**If you find anything incorrect or missing in this article feel free to
add it yourself. After you register, you must wait three days before you
can edit a page.**

# Introduction

Murmur is the server component for Mumble. This article is meant to give
you the necessary information to configure and run your own server.

# Distribution-Specific Murmur

By default, Murmur is configured to run from a regular user account, and
on Windows and OSX this is the only way it works.

However, on distributions with prepackaged Murmur (Debian/Ubuntu),
Murmur is configured to run as a system service, just like your
webserver, mailserver and whatever else you have running. This "global"
installation is a ready, turn-key solution, most of the information here
does not apply to you. Most packages also include the
'murmur-user-wrapper' script, which does all of the below for you if you
want to run as a regular user (including starting DBus).

So, on these systems, you can still run Murmur manually, but you will
then not benefit from the extensive care that has gone into preparing
those packages.

If you need to register users externally, or change the settings of a
virtual server, read the section on Advanced Configuration.

# Basic Configuration

## Settings, Ports, and Authentication

The default settings for a Murmur server are configured in
*[murmur.ini](murmur.ini "wikilink")*. Here, you can configure the
welcome text, port number and other settings. However, these are just
default settings and can be overwritten via the [Ice](Ice "wikilink")
RPC without changing the .ini; if you're running multiple virtual
servers, each virtual server has its own configuration, which is
maintained internally by Murmur (see below).

The default port for a Murmur server is UDP and TCP 64738.
Have a look at [Mumble URL](Mumble_URL "wikilink") to see how to publish
links to your server, and [SRV Record
configuration](SRV_Record "wikilink").

Adding an authenticated user can be done through various means. Unless
you need automated registration of users or authentication against an
external database using the functionality built into the client is the
easiest method. If you need more control you can use
[Ice](Ice "wikilink") or [DBus](DBus "wikilink").

## Setting the SuperUser Password

In version \>=1.2.4 the SuperUser password is generated automatically on
the first server start. You can find it in the logfile. Search for an
entry like <W>`2013-09-03 11:23:44.516 1 => Password for 'SuperUser' set
to 'supersecretpassword'`. You can of course change this password.

To set/change the password on the Linux static server, run

`murmur.x86 -ini `<path to configuration file>` -supw `<password>` [srv]`

To set the password on Debian-based systems, run

```
 # EITHER use the dpkg management facilities
 sudo dpkg-reconfigure mumble-server

 # OR run the server binary manually
 sudo -i murmurd -ini /etc/mumble-server.ini -supw <password> [srv]
```

To set the password on Windows systems, run

`<path to murmur.exe> -ini `<path to configuration file>` -supw `<password>` [srv]`

Make sure the `-ini` parameter is the same as for running the server
normally to make sure the password gets set in the right database file.
If the command does not seem to work, double-check that you are
supplying the right path.

The `[srv]` parameter is the ID of the virtual Mumble-Server you want to
change password for. If omitted, ID 1 is used (for the first virtual
server).

This will only set the password and then terminate, it will not start
the server. To run the server, start it without the `-supw` parameter.

## Starting Murmur

To start Murmur,

On a static Linux build, cd to the directory where you extracted the
files and do

`murmur.x86`

On Debian-based,

`sudo dpkg-reconfigure mumble-server`

On Windows,

`<path to murmur.exe> (usually C:\Program Files\Mumble\Murmur.exe)`

For debugging or real time logging, you might want to add *-fg -v* to
the command line, which will stop the program from running in the
background.

By default, Murmur opens its configuration file, database file and
logfile in your current directory. The configuration file can be
overridden with the *-ini* parameter, and the database and logfile can
be set from the ini file, using their respective parameters.

# Advanced Configuration and Administration

To make use of a strong server certificate the users will not have to
manually accept, please see [Obtaining a Let's Encrypt Murmur
Certificate](Obtaining_a_Let's_Encrypt_Murmur_Certificate "wikilink")
and [Obtaining a Comodo Murmur
certificate](Obtaining_a_Comodo_Murmur_certificate "wikilink").

## Compatibility With RPC-Interfaces

For full functionality with an RPC interface, Murmur requires either a
working [DBus](DBus "wikilink") daemon or [Ice](Ice "wikilink")
installation that is enabled. We recommend using the
[Ice](Ice "wikilink") interface; [DBus](DBus "wikilink") is considered
deprecated and although it will not be removed in the near future, it is
not receiving any new functionality. Once you have Murmur working with
the RPC interface, you can install a compatible web interface; see below
for possible options.

## Authenticating With an External Database/Forum

### Ice

For phpBB3, there is
[phpBB3auth](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/phpBB3).
You must point the python script to the ini file; read the in-source
documentation for more infomation.

For SMF (Simple Machines Forum), there is
[smfauth](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/SMF).
You must point the python script to the ini file; read the in-source
documentation for more infomation.

### DBus

There is an extended example of how to use the authenticator called
*scripts/dbusauth.pl*. You'll need to configure where your phpBB3
database resides, but once that is done you'll simply have to run the
script after starting murmur to allow authentication to be done through
the phpBB3 database.

Any group associations the user has on phpBB3 is copied to a temporary
group on a root channel (and by default inherited to all subchannels).
Please note that this is a temporary group membership and as such will
not show up in the Edit ACL dialogs.

## 3rd Party Applications

If you are planning to administrate your Murmur server with an external
3rd Party Application, see the following pages for further information.

  - **[Web-Interfaces](3rd_Party_Applications#Web-Interfaces "wikilink")**
  - **[Standalone
    Applications](3rd_Party_Applications#Standalone_Applications "wikilink")**
  - **[Commandline-Interfaces](3rd_Party_Applications#Commandline-Interfaces "wikilink")**

## Manual Configuration Using DBus

If you are not able to use an additional application for administrating
Murmur there is still the possibility of manually communicating with the
server using [DBus](DBus "wikilink"). You can find detailed information
on this in our [DBus article](DBus "wikilink").

# Alternative Mumble Servers

There are multiple alternative Mumble Servers which support the Mumble
protocol.
Everyone is free to implement their own Mumble server software and add
it to this list.

## Grumble

Grumble is a Mumble Server based on Go (programming language).
It is in active development by the official Mumble team.
Take a look at the Github Repo: <https://github.com/mumble-voip/grumble>

## uMurmur

uMurmur is a minimalistic Murmur implementation without dependency on
QT-core. It lacks features of the Mumble server, but aims at working
well on embedded devices like routers.

Read more at [the uMurmur project page](http://umurmur.net).

[Category:Documentation
English](Category:Documentation_English "wikilink")