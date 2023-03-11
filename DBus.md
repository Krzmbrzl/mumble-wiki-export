**WARNING:** The DBus interface for the server is deprecated and will
not be extended any more (and thus is already missing features). Use the
[Ice](Ice "wikilink") interface instead.

# What is DBus for Murmur

`D-Bus is a free software project which offers a simple way for applications to communicate with one another.`
`It is developed by Red Hat as part of the freedesktop.org project. - `[`Wikipedia`](http://en.wikipedia.org/wiki/D-BUS)

DBus can be used as an RPC method for controlling murmur from another
application.

# Configuring DBus for Murmur

Since point-to-point DBus connections don't work in Qt yet, you have two
options to configure Murmur for dbus use.

## A Windows machine

Since Murmur can't run without an active desktop on windows, you can
safely ignore this setup. Just make sure your
[murmur.ini](murmur.ini#dbus "wikilink") says

    dbus=session

## DBus on Linux/OSX

### Your own machine with root access

If you own the box you're running murmur on, and you have only one
murmur process, you'll want to use the system dbus. The first step is
creating a new file called */etc/dbus-1/system.d/murmurd.conf*

    <!DOCTYPE busconfig PUBLIC
     "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
     "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
    <busconfig>

      <policy user="mumble">
        <allow own="net.sourceforge.mumble.murmur"/>
      </policy>
      <policy user="root">
        <allow own="net.sourceforge.mumble.murmur"/>
      </policy>

      <policy context="default">
        <allow send_destination="net.sourceforge.mumble.murmur"/>
        <allow receive_sender="net.sourceforge.mumble.murmur"/>
      </policy>
    </busconfig>

Then restart the system dbus daemon. Please note that this configuration
allows anyone with a user on your machine to control the murmur process,
so you might want to tighten security slightly.

In your [murmur.ini](murmur.ini#dbus "wikilink"), make sure it says

    dbus=system

### A shared machine

First, we'll have to start a dbus daemon and place the session info
somewhere. For DBus we need an isolated daemon, different from the one
running under, say, a X11 session, so we specifically spawn our own. The
following small shell script will ensure a deamon is ready (copied from
*murmur-user-wrapper*):

    #! /bin/bash
    DIR=$HOME/murmur
    DBUSFILE=$DIR/.dbus.sh
    DBUS_SESSION_BUS_ADDRESS=invalid:/
    [ -f $DBUSFILE ] && . $DBUSFILE
    if ! dbus-send --print-reply --dest=org.freedesktop.DBus --type=method_call / org.freedesktop.DBus.GetId 2> /dev/null > /dev/null; then
      echo "Launching D-Bus session"
      dbus-launch --sh-syntax > $DBUSFILE
      . $DBUSFILE
      if ! dbus-send --print-reply --dest=org.freedesktop.DBus --type=method_call / org.freedesktop.DBus.GetId 2> /dev/null > /dev/null; then
        echo "Failed to launch session DBUS, bailing out."
      fi
    fi

Before running this for the first time, make sure \~/murmur exists

`mkdir $HOME/murmur`

    dbus-launch --sh-syntax > ~/.dbus.sh
    source ~/.dbus.sh

Make sure your [murmur.ini](murmur.ini#dbus "wikilink") has

    dbus=session

Since there can be many session busses on a system, you'll always need
to specify which one to use. So for every new shell you open, you should
always source this script before starting murmur, and you also need to
run it before using any DBus commands.

    source ~/.dbus.sh

You should not put the above into your *.bashrc* or similar, as most X
sessions will have their own and separate session dbus.

When using the session bus, only the userid who created the bus can use
it. Hence, you have to make sure that any scripts you write run with the
same user ID.

### A Docker container

If your host runs [Docker](https://www.docker.com/), you can use
[RabidFX's Dockerfile](https://hub.docker.com/r/rabidfx/murmur-dbus/) to
create a SSL-capable, fully-autonomous Murmur server in minutes, with
DBus capabilities (through the host's system bus).

# Making sure it works

Start murmur with the options *-fg -v*, which will run it in the
foreground with full debugging. You should see the line "DBus
registration succeeded".

If your distribution includes the full Qt4 tools package, you'll have a
program called *qdbus* which can be used to inspect the dbus system. Try
running

    qdbus --system net.sourceforge.mumble.murmur /

or if you're using the session bus:

    qdbus --session net.sourceforge.mumble.murmur /

You should see a long list of function names. You can actually use the
simpler functions directly from qdbus. For example, you can set a new
superuser password with

    qdbus --system net.sourceforge.mumble.murmur / net.sourceforge.mumble.Meta.setSuperUserPassword 1 supahsecret

If you don't have *qdbus*, try this

    dbus-send --system --dest=net.sourceforge.mumble.murmur --type=method_call --print-reply / org.freedesktop.DBus.Introspectable.Introspect

# Documentation

You can use the Introspect method for receiving a list of all available
commands. A simple script to create an output can look like this:

    #!/usr/bin/python
    import dbus

    dbus_base = 'net.sourceforge.mumble.murmur'
    bus = dbus.SystemBus()
    proxy = bus.get_object(dbus_base, '/')
    murmur = dbus.Interface(proxy, 'net.sourceforge.mumble.Meta')
    print murmur.Introspect(dbus_interface='org.freedesktop.DBus.Introspectable')

For a documentation of all dbus methods have a look at [DBus
Methods](DBus_Methods "wikilink").

# Using DBus

## Showing the list of users on a webpage

There is a small perl example called *scripts/weblist.pl* in the mumble
distribution. It works as a CGI for most systems.

## Manual configuration using DBus

If you are not able to use an additional application for administrating
Murmur there is still the possibility of manually communicating with the
server using [DBus](DBus "wikilink").

### Showing the default configuration

This is just to verify we have contact with DBus, and to print out the
default configuration.

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.getDefaultConf`

(if you're running a system DBus based configuration, add *--system*
before all the other parameters)

This should print out the default configuration.

### Virtual Servers

Listing the servers:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.getAllServers`

Adding a server:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.newServer`

Removing a server:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.deleteServer int32:`**<serverid>**

Starting a server:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.start int32:`**<serverid>**

Stopping a server:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.stop int32:`**<serverid>**

### Server configuration

Each virtual server has it's server-specific configuration. If a
particular confiuration item is empty, it will fall back to the default
configuration, which is specified in the ini file.

Listing the configuration:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.getDefaultConf`
`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.getAllConf int32:`**<serverid>**

Setting a configuration item:

`dbus-send --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call / net.sourceforge.mumble.Meta.setConf int32:`**<serverid>**` string:"`**<key>**`" string:"`**<value>**`"`

### User management

If you can run CGI scripts from your user account, the murmur.pl script
contains user self-management. Just copy it to your webserver and make
it executable (you might need to rename it to murmur.cgi), and it should
contain everything needed. If not, this is what you'll need:

Adding a new registration:

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /`**<serverid>**` net.sourceforge.mumble.Murmur.registerPlayer string:"`**<username>**`"`

Fetching an existing registration:

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /`**<serverid>**` net.sourceforge.mumble.Murmur.getRegistration int32:`**<userid>**

or

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /`**<serverid>**` net.sourceforge.mumble.Murmur.getRegisteredPlayers string:"`**<username>**`"`

Updating a registration:

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /`**<serverid>**` net.sourceforge.mumble.Murmur.setRegistration int32:`**<userid>**` string:"`**<username>**`" string:"`**<email>**`" string:"`**<password>**`"`

### Detailed explanation of user management

  - Note you must be running \> 1.1.5 Murmur Stable for these commands
    to work.
  - If you are running Murmur from a session DBus, then remove the
    *--system* from the *dbus-send* commands

<serverid> is a digit number of the server you have. For instance if you
had fifty Murmur servers running, the first server you started would be
1, and the fiftieth server you started would be 50.

<userid> is also a digit number such as 4 or 30, depending on how many
people are registered in the database. For instance when you run

` dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.registerPlayer string:"Name"`

you will see after you run this command "int32" and some other text.
There will be a number to the right of "int32". This number is the
user's UserID.

So for instance you want to register a user, that user's name was
*Name*, his password was *passwrd*, and you have one server running.

On Linux you would run

` dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.registerPlayer string:"Name"`

You will then see some text. In it you will see "int32". Let's say you
already had 5 users registered^. The number next to "int32" in the
terminal would be 6. Remember this number.

Now run

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.setRegistration int32:6 string:"Name" string:"<user's email address>" string:"passwrd"`

On Windows you would run

`"C:\Program Files\Mumble\dbus-send.exe" --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.registerPlayer string:"Name"`

You will then see some text. In it you will see "int32". Let's say you
already had 5 users registered^. The number next to "int32" in the
command prompt would be 6. Remember this number.

Now run

`"C:\Program Files\Mumble\dbus-send.exe" --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.setRegistration int32:6 string:"Name" string:"<user's email address>" string:"passwrd" `

You now have a registered user. "Name" can now login with the username
*Name* and the password *passwrd*.

If you want to change Name's registration, do the following command:
(let's change Name's name to "Unnamed" and his password to "nopasswrd")

For Linux do

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.setRegistration int32:6 string:"Unnamed" string:"<user's email address>" string:"nopasswrd"`

For Windows do

`"C:\Program Files\Mumble\dbus-send.exe" --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.setRegistration int32:6 string:"Unnamed" string:"<user's email address>" string:"nopasswrd"`

If you cannot remember the int32 of a user, simply run this command

Linux

`dbus-send --system --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.getRegisteredPlayers string:"`<username>`"`

Windows

`"C:\Program Files\Mumble\dbus-send.exe" --print-reply --dest=net.sourceforge.mumble.murmur --type=method_call /1 net.sourceforge.mumble.Murmur.getRegisteredPlayers string:"`<username>`"`

If you have just started a new Murmur server, the first user you create
will have a UserID of 1. The first UserID, 0, is the SuperUser.

# DBus in the Mumble client

The Mumble client itself can also be controlled over DBus. At the moment
the following functionality is exposed:

  - Direct the client to a [Mumble URL](Mumble_URL "wikilink")
  - Get the current [Mumble URL](Mumble_URL "wikilink")
  - Focus the Mumble window
  - Mute/Deafen self
  - Fetch self mute/deafen state

[Category:Documentation
English](Category:Documentation_English "wikilink")