**Please edit this page if you find a feature or step you think should
be included; it's a wiki for a reason\! Note you must register and wait
about 3 days in order to be able to edit.**

# Setting Up a Murmur Server

Note that the instructions of this guide are Windows based, but all of
the instructions should be adaptable to Linux. Once your IP is made
static, and you get Murmur started, its ini configured, and its port is
cleared through whatever firewalls are present, the setup is mostly
client-side.

Always remember that there are professional Mumble server hosters.
Simply Googling "mumble server hosting" will come up with many
excellent, reliable hosts that offer servers at a very cheap price. We
also have a list of hosters [here](Hosters "wikilink").

If you have any questions, that you cannot find answers to on this page,
check the [FAQ](FAQ "wikilink").

## Preparations

### Configure OS

#### Windows

Before you can have Murmur completely working, you need to make a few
changes to your network on Windows.

First, make your IP static. Unless you're just going to run this server
a few times, or it is a LAN server only to be found via
[Bonjour](Bonjour "wikilink"), you need to make your IP static so that a
person outside of your network can dependably connect to your Murmur
server. If you have no idea how to make your IP static, read [this
guide](http://portforward.com/networking/static-xp.htm) for doing in on
Windows XP, and [this
guide](http://portforward.com/networking/static-vista.htm) for doing it
on Windows Vista.

#### Linux

Generally, the config file for setting a static IP involves either using
your distro's GUI network tool or editing configuration files (for
example, */etc/network/interfaces*). It is recommended that you
[Google](http://www.google.com/) for instructions to set a static IP for
your specific distribution. Generally something like "Ubuntu static IP"
will get what you need.

### Configure Network

Now you need to open a port on your computer and/or networking
equipment. This port will be the port that Murmur runs on, and the
default is 64738 (using the TCP and UDP protocols). If you wish to use a
port different than this one, use it instead of port 64738 used in this
example. If you are just using Windows' built-in firewall then when you
start Murmur it should ask whether or not to allow it. If you are using
a third-party software firewall you will need to find the instructions
for opening a port on it on your own. To learn how to open the port on
your network equipment, we recommend you go to
[Portforward](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)
and select your specific devices from the list. Though Murmur is not
currently on the Portforward website, just use some other program in
place of it (for instance read the instructions for opening the ports
for Call of Duty) but **only open the port you want to use for
*Murmur***, ensuring that you are using both TCP and UDP for the port.
Remember that ANY device with a firewall between you and the internet
*must* allow the port you are going to use for Murmur on both the TCP
and UDP protocols. That means your \[wireless\] router, Cable or DSL
modem, and anything else that has a firewall.

After you have forwarded the port, you can check to make sure it is open
by going to <http://www.canyouseeme.org/> from the computer that has the
port forwarded.

**Note that if your network seems to have the port forwarded completely,
and you *still* cannot connect, you may still have some hidden software
firewall blocking the port on your server. Check *very* carefully to
make sure you do not.**

### Install Murmur

#### Windows

Now you need to install Murmur. Download the latest stable Win32 release
[here](http://wiki.mumble.info/wiki/Main_Page). Start the installation,
and when you come to the installation selection, select at least the
Murmur server. You can choose to install Mumble and Bonjour if you want,
but it is not a requirement. Once you have it installed, it is
recommended that you make a shortcut to it in order to easily start it.
Go to *C:\\Program Files\\Mumble* (or wherever you installed Murmur to),
right click on *murmur.exe* and click "Create Shortcut." Find the
shortcut (it will be in the same folder as *murmur.exe*), right click
it, and click "Rename." Type "Murmur" (without the quotes) and press
enter. Now drag the Murmur icon onto your desktop.

**Windows Server users note:** you may have an old murmur.sqlite
database if you are upgrading to 1.2.x. Mumble may not remove this
database on installation, so unless you want to keep it, you can delete
it at *C:\\Users\\<username>\\murmur.sqlite*.

#### Linux

For nearly all Linux distributions, you can simply use the [static
binary](http://dl.mumble.info). However, if your specific distribution
supports Murmur (such as Ubuntu), you should look into using the
specific packages for it. These are listed on the [Linux section of the
Installing Mumble](Installing_Mumble#Linux "wikilink") page.

## Set Up Server

### Configuring ini File

First, you need to locate the path of your
[Murmur.ini](Murmur.ini "wikilink"). This file contains all the basic
settings for Murmur.

  - Windows: In *C:\\Program Files\\Mumble* (or wherever you installed
    Mumble to) there is a file called *murmur.ini*.
  - Linux: If you are running the command *murmurd* as root (e.g. when
    running Murmur as a system service) */etc/mumble-server.ini* is
    used, when run as a normal user *\~/.murmurd/murmur.ini* is sourced.
    On some distributions you can also use the easy wrapper command
    *murmur-user-wrapper*, per default it will look at
    *\~/murmur/murmur.ini*. To generate a sample configuration file at
    this location, run *murmur-user-wrapper -i*.

If you change any of the settings in this ini file, you have to restart
Murmur for the changes to apply. It is suggested that you look over
and/or configure the lines that start with the following:

`welcometext=`
`port=`
`serverpassword=`
`bandwidth=`
`users=`
`registerName=`

You do not need to change any of these fields for your server to work,
but you should change them if you *need* to. For instance if you do
*not* want your server to be public (that is, any user of Mumble has the
potential to enter it) you should set

`serverpassword=`

to

`serverpassword=Password_of_your_choice`

(*Password_of_your_choice* being whatever you want your server
password to be.) Uncomment

`#registerName=`

(change it to)

`registerName= `

and set it. This line sets the name of the Root channel of your Murmur
server. It is the top channel of the server and if you do not set it, it
will have a name of "Root." For instance if you wanted to name the
server "FPS Fun" you would set the line to

`registerName=FPS Fun`

*Do not* fill out the other

`#register* `

fields or uncomment them if you are going to have a server password set.
If you *want* it to be public you *must* leave

`serverpassword= `

blank and you must set the following lines with the proper information
and remove the \# from them. (\# at the beginning of a line comments the
entire line, telling the program that reads it to completely ingore the
line.) The lines below register the server with the central Mumble
server list and make it so that one who browses the servers on the
"Server Browser" tab of the connect window can see your server. Read the
commented lines in the ini for specific information about these three
lines.

`#registerName=`
`#registerPassword=`
`#registerUrl=`

The

`#registerHostname=`

line is optional and only set it if you have an external static IP. If
you are on a home-based DSL or Cable network, you probably should not
set this field.

Carefully read the commented text in the ini file for explanations of
each of the ini settings you wish to change or set.

### Regular Expressions

If you want to use a character that the server does not allow, you need
to use regular expressions - specifically, [Qt regular
expressions](http://qt-project.org/doc/qt-4.8/qregexp.html#characters-and-abbreviations-for-sets-of-characters).
These are, in themselves, rather complex, but for Mumble, you don't need
to learn them. Here's a quick guide to regular expressions:

If you want to use the character "%" in a channel name, then uncomment
this line in Murmur.ini:

`#channelname=[ \\-=\\w\\#\`\[\\]`\\{\\}\`\(\\)`\\@\\|]+ `

so that it is

`channelname=[ \\-=\\w\\#\`\[\\]`\\{\\}\`\(\\)`\\@\\|]+`

then add the character, which will make it look like this:

`channelname=[ \\-=\\w\\#\`\[\\]`\\{\\}\`\(\\)`\\@\\|\\%]+`

See? It's easy. You just add each character that you want, putting
*\\\\* between each character.

If you want to add the ability for users to use spaces in their
username, then uncomment this line

`#username=[-=\\w\`\[\\]`\\{\\}\`\(\\)`\\@\\|\\.]+`

so that it is

`username=[-=\\w\`\[\\]`\\{\\}\`\(\\)`\\@\\|\\.]+`

then make it look like this:

`username=[ \\-=\\w\`\[\\]`\\{\\}\`\(\\)`\\@\\|\\.]+`

(See the space at the very beginning, right after the *\[* ?)

### Starting Murmur

**In server versions up to 1.2.2, the server must have been run normally
at least once, to generate the database properly. Also, if you are using
a custom config file location, you must remember to specify it on the
command line using the *-ini <path>* flag while setting the password.**

#### Windows

Once you have configured the .ini file to your liking and are ready to
start Murmur, start it by double clicking the Murmur icon you put on
your desktop. The server should start and you should see a little icon
similar to Mumble's in your system tray (the little icons in the bottom
right corner of your screen). You can right click this icon and select
either "Show Log" to view the log that Murmur generates (users that
connect, settings initialized, etc.) or "Quit Murmur" to shut down the
Murmur server.

If you want Murmur to automatically start with Windows, select the
Murmur icon, right click it, and click "Copy." Now right click on your
start button, select "Open All Users" and open "Programs\\Startup."
Right click in an empty space and select "Paste." Now Murmur should
start with Windows.

##### Running as a Windows Service

Download latest version of NSSM from <https://nssm.cc/download> ,
extract the files, in a command prompt navigate to the NSSM folder then
navigate to the win32 or win64 folder depending on your system. Run the
following command "nssm install <servicename>" without quotes and NSSM
will display a prompt for you to navigate to the murmur folder to select
the murmur.exe, click Install service after selecting murmur.exe. You
will need to go and manually start the service as NSSM doesnt start it
after creation. Working on Server 2012 R2 as of 3/18/2016.

<https://sourceforge.net/p/mumble/feature-requests/650/>

#### Linux

If you are using the static binary, simply CD to wherever you extracted
it, chmod it, and then do

`./murmur.x86 [-ini `<path>`]`

If you are using a package for your distribution, the command is usually

`murmurd`

This command will be run if you use Murmur as a system service on Linux.
As described in
[Running_Murmur\#Distribution-Specific_Murmur](Running_Murmur#Distribution-Specific_Murmur "wikilink")
on some distributions you can also use the following wrapper-command if
you intend to run Murmur from a normal user environment:

`murmur-user-wrapper`

Refer to the corresponding manual pages for options etc.

Most packages will automatically start from init.d; you should check to
make sure yours does not before manually starting it. For Installation,
look at [the installation section](Murmurguide#Linux_2 "wikilink"). For
the path of the configuration file at [this
section](Murmurguide#Configuring_ini_File "wikilink").

### Setting SuperUser Password

Now you will need to set the SuperUser Password. The server should be
running at this point.

#### Windows

To set the SuperUser password, press the Windows key and hold it down
(it's the key typically located between the left CTRL and left Alt
buttons) and then press the R key.

In the input box of the window that pops up, type *cmd* and press Enter.

Now type

`cd %ProgramFiles%\Mumble`

and press Enter. If that does not work try "cd
%ProgramFiles(x86)%\\Mumble". If you installed Murmur to a different
folder than those, you need to cd to the correct install directory.

After you have done that, type

`murmur.exe -supw Password_of_your_choice`

(*Password_of_your_choice* being whatever password you want to give
SuperUser) and press Enter. If you are not using the murmur.ini located
in the install folder you can pass your own using "-ini
<full path to ini>".

Note: **This does not start the Murmur server**, it only sets the
SuperUser password. A window should pop up that displays the current
date and time followed by "Superuser password set on server1."

![This is a visual reference of what should be seen after entering the
command correctly and pressing Enter. Your install directory may differ
from the one displayed.](Set_Mumble_SU_pwd_16.05.2015_145519.png
"This is a visual reference of what should be seen after entering the command correctly and pressing Enter. Your install directory may differ from the one displayed.")

#### Linux

If you're using the static binary, CD to where you extracted it, and run

`./murmur.x86 [-ini `<path>`] -supw Password_of_your_choice`

If you're using Murmur as a system service or with *murmurd*, run

`murmurd -supw Password_of_your_choice`

If you're using the wrapper command *murmur-user-wrapper*, then run

`murmur-user-wrapper -p Password_of_your_choice`

*Password_of_your_choice* being your chosen SuperUser password, of
course.

### Connecting to Murmur Server

Now that Murmur is started, start Mumble. When it is started, click the
*Add New...* button. Then fill the fields with your servers information.

The *Servername* field contains the name that will be displayed in your
server list.

The *Address* field is the external IP of your server; if you do not
know the external IP, go here (from the computer hosting Murmur):
<http://whatismyipaddress.com/> ; or your servers bonjour name (prefixed
with @). **Your external IP is *never* 192.168.x.x**

The *Username* field takes your users Name. Be aware that names are case
sensitive. If you want to connect as SuperUser mind the capitalization.
Since you are going to want to add your user as an admin, put in that
username for now.

Note that in contrast to 1.1.8 there is no password field. This is
because 1.2.x relies on certificate authentication. If for some reason a
password is needed the client will present you with a prompt.

### Becoming Administrator and Registering a User

In 1.2.x you don't need any 3rd party scripts, servers, or programs to
add a user. First, you probably want to become a member of the
administrator group.

**Note that as an administrator, you can manage the registered users by
going to Server -\> Registered Users.**

Becoming an admin:

1.  Start the Mumble client.
2.  Go through the Certificate Wizard and either import or create a
    certificate. You can skip the Audio Wizard if you want, although you
    will need to run through it in order to set up your mic properly, so
    you might want to do that anyway.
3.  Open Configure -\> Settings and check
    "[Advanced](Advanced_client_configuration "wikilink")" at the bottom
    left.
4.  Join your server following the [previous
    step](Murmurguide#Connecting_to_Murmur_Server "wikilink")
5.  When you are connected to the server, right click on your username,
    and then click "Register" - if you do not see this option, ensure
    that you have an @all ACL that has "Register Self" set to Allow,
    Applies to sub-channels unchecked.
6.  Reconnect as the SuperUser - Go back to your server list, and on the
    main Mumble window click Server -\> Connect. You will see the server
    you added in the previous step. Right click it and select "Edit..."
    Change *Username* to SuperUser, click OK, then click Connect.
7.  Right click the "Root" Channel (it will be above your username; it
    will be whatever you named it if you set the registerName in
    Murmur.ini) and click *Edit*.
8.  Go to the Groups tab
9.  In the drop-down box at the top select the "admin" group
10. In the "Members" drop-down box at the bottom left, type your
    username and press enter
11. Click OK
12. Follow step 3 to change your username back to the user you added
    with SuperUser
13. Connect back to the server
14. Test your administration ability by right clicking the root channel,
    clicking *Add*, and adding a new channel

The default settings allow users to register themselves. This can be
disabled within the ACLs. Members of the admin group can always *right
click-\>Register* a user to register them manually. Note that this only
works if the user provided a certificate (meaning that they have
completed the certificate wizard).

***Make sure that you instruct everyone on your server to back up their
certificate. The certificate wizard forces you to do this, but you
should always back it up to a secure storage medium like a flash drive,
your email inbox, or any external storage medium. If you ever lose your
certificate, you will have to re-register and be manually added back
into all your various ACLs\!***

If you want to learn more about ACLs see [this
guide](ACL_and_Groups "wikilink").

For a quick overview of what a certificate is, and how they are used to
identify people, see [this page](Authentication "wikilink").

### Permissions

Note that you **must** have **[Advanced
config](Advanced_client_configuration "wikilink")** checked at Configure
-\> Settings in order to see the ACL tab for a channel.

#### ACLs

Many people have complained about the complexity of ACLs - that they are
complicated, hard, and cumbersome. *They are none of these if used
correctly.* You see, the ACLs *can* be as complicated as you want. It is
basically a full permissions suite similar to what you would deal with
on an Apache server. But it doesn't *have* to be that complicated\!

Do you know what ACL means? Access Control List. That is all. An ACL
simply defines where and what a "Group" can do. A Group is simply a
bunch of users defined by a name. That is all.

Here is a basic guide that you can use to create the most essential
permissions for your server:

Ok. You have made one admin so far. If you want to add *another* admin,
the other person you know must register themselves. After that, you can
open the ACL editor and add them in the same way that you used SuperUser
to add yourself.

But now you want to make a channel that only certain people can get in.
Very simple.

1.  Make sure that everyone you want to add is registered with the
    server
2.  Make the channel for the people who want it (for this example, make
    an MMO channel)
3.  Right click on the root channel, click "Edit", then go to the Groups
    tab
4.  Click, in the empty box at the top, and type the name of the group
    you want to add. For example, if you wanted to make a channel for
    MMO players, you might name your group "MMOplayers." Type that into
    the box and press enter. A new group has been made.
5.  Now you need to add members to this group. In the box at the bottom
    left, type a member name and press enter after each name. The names
    that you add should appear in the box above the input box.

Finally, you need to create an ACL for the channel. Close the current
window, and then right click on the MMO channel and select Edit. Click
the ACL tab.

1.  Here is where it *appears* to become complicated, when in fact it is
    not at all. What you first see is inherited ACLs. All inherited
    means is that the permissions of the above channel are automatically
    applied to this one. Since we don't want that, uncheck "Inherit
    ACLs."
2.  Now if you just left it like it is now, then the @all permissions
    would be in effect for this channel. Anyone who went into this
    channel (except for those in the admin group; they override this)
    would have the permissions you see at the right.
3.  But we want to make some ACLs. Start off by adding an "@all." Just
    click "Add" and it will be created. By default, the Group will be
    *all*. All the *@* means is "apply to." For this group, you probably
    just want to set "Deny" for all the permissions. However, you don't
    have to manually click "Deny" on everything. The group that is
    defined before it, the "@all" in italics, already has set
    permissions. For example, it defaults to deny "Write ACL." So, in
    the "@all" ACL below it, if you don't check either "Deny" or "Allow"
    and it will default to "Deny." **Also note that lower ACLs take
    priority over ones above them. For instance, you can make an @all
    that denies permissions for everything, and make an @all below that
    one, that allows permissions for everything, and everyone in the
    server will be given administrator-level access to the server.**
4.  Now click "Add" again. However, this time you need to click the
    "Group" box at the bottom left. Delete the "all" text from there and
    type *MMOplayers*, then press enter.
5.  Now you need to define what exactly *MMOPlayers* can do. The
    recommended settings would probably be "Allow" on all the
    permissions except for "Write ACL" and "Make channel"; those two
    permissions should be set to "Deny".
6.  Now only people in the *MMOplayers* group should be able to join the
    channel (and those in the admin group, of course).

#### Access Tokens

Another nice feature of Mumble 1.2.x is Access Tokens. These are what
you could call passwords; basically, if you have a token that is the
same name as the channel's ACL Access Token group, you can enter the
channel. Think of Access Tokens as groups where you can add yourself to
the group if you know the "password" (token).

1.  Go to Server -\> Access Tokens and add a token.
2.  Add an ACL for a channel you want to give permissions to. Do exactly
    the same as you would with a normal ACL, but when you assign a group
    for the ACL, type *\#TOKEN_NAME* (TOKEN_NAME being the name of the
    token that you added in the above step).
3.  Now each individual user can click themselves, click Server -\>
    Access Tokens, and add the tokens for the channels they want to
    enter. Remember, channel owners should only give out the token name
    to those they want to enter their channel, and it is best to pick a
    unique, hard-to-guess name for your token.

## Server Configuration Methods

As of Mumble 1.2.x, nearly all administration tasks can be handled
directly through the client. However, if you are a dedicated server
hoster, you will probably want to start virtual servers, and have some
way of configuring and applying the **murmur.ini** parameters without
having to shut down Murmur. See below for more information.

### Remote Controlling the Server

For a 3rd party application there are two methods, [Ice](Ice "wikilink")
and [DBus](DBus "wikilink"), to interact with the server. These can be
used from a variety of programming languages and give you low-level
access to a lot of functionality.

The easiest way to set up a remote interface is to use Mumble-Django or
[MumPI](https://sourceforge.net/projects/mumpi/).

If you are using a Debian-based distribution, you can install
Mumble-Django with

`sudo apt-get install mumble-django`

and follow the included documentation.

You can find a list of all the various web-interfaces
[3rd_Party_Applications](3rd_Party_Applications "wikilink").

**This is not a required step in this guide.**

[Category:Documentation
English](Category:Documentation_English "wikilink")