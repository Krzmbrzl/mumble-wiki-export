'''If you find anything incorrect or missing in this article feel free to add it yourself. After you register, you must wait three days before you can edit a page.'''
= Introduction =
{{Notice
|message=For a step-by-step guide to setting up a Murmur server, read '''[Murmur Guide](Murmurguide.md)'''.

}}
Murmur is the server component for Mumble. This article is meant to give you the necessary information to configure and run your own server.

= Distribution-Specific Murmur =

By default, Murmur is configured to run from a regular user account, and on Windows and OSX this is the only way it works. 

However, on distributions with prepackaged Murmur (Debian/Ubuntu), Murmur is configured to run as a system service, just like your webserver, mailserver and whatever else you have running. This "global" installation is a ready, turn-key solution, most of the information here does not apply to you. Most packages also include the 'murmur-user-wrapper' script, which does all of the below for you if you want to run as a regular user (including starting DBus).

So, on these systems, you can still run Murmur manually, but you will then not benefit from the extensive care that has gone into preparing those packages.

If you need to register users externally, or change the settings of a virtual server, read the section on Advanced Configuration.

= Basic Configuration =

## Settings, Ports, and Authentication 
The default settings for a Murmur server are configured in ''[[murmur.ini]]''. Here, you can configure the welcome text, port number and other settings. However, these are just default settings and can be overwritten via the [[Ice]] RPC without changing the .ini; if you're running multiple virtual servers, each virtual server has its own configuration, which is maintained internally by Murmur (see below).

The default port for a Murmur server is UDP and TCP 64738.
<br> 
Have a look at [ SRV Record configuration](Mumble URL]] to see how to publish links to your server, and [[SRV_Record .md).

Adding an authenticated user can be done through various means. Unless you need automated registration of users or authentication against an external database using the functionality built into the client is the easiest method. If you need more control you can use [[Ice]] or [[DBus]].

## Setting the SuperUser Password 
{{Notice
|message=Note this command can be run seperately while the server is running to change the password without restarting.  Also note that in 1.2.2 at least, you must run the server normally at least once before trying to set this.
}}

{{Notice
|message=For older versions the SuperUser account is disabled until you setup the password. You don't need the SuperUser account to run a simple server, but you do need it if you want to give your regular user account any privileges. 
}}

In version >=1.2.4 the SuperUser password is generated automatically on the first server start. You can find it in the logfile. Search for an entry like <code><W>2013-09-03 11:23:44.516 1 => Password for 'SuperUser' set to 'supersecretpassword'</code>. You can of course change this password.

To set/change the password on the Linux static server, run
 murmur.x86 -ini <path to configuration file> -supw <password> [srv]
To set the password on Debian-based systems, run
<pre>
 # EITHER use the dpkg management facilities
 sudo dpkg-reconfigure mumble-server

 # OR run the server binary manually
 sudo -i murmurd -ini /etc/mumble-server.ini -supw <password> [srv]
</pre>
To set the password on Windows systems, run
 <path to murmur.exe> -ini <path to configuration file> -supw <password> [srv]

Make sure the <tt>-ini</tt> parameter is the same as for running the server normally to make sure the password gets set in the right database file. If the command does not seem to work, double-check that you are supplying the right path.

The <tt>[srv]</tt> parameter is the ID of the virtual Mumble-Server you want to change password for. If omitted, ID 1 is used (for the first virtual server).

This will only set the password and then terminate, it will not start the server. To run the server, start it without the <tt>-supw</tt> parameter.

## Starting Murmur 

To start Murmur, 

On a static Linux build, cd to the directory where you extracted the files and do
 murmur.x86
On Debian-based,
 sudo dpkg-reconfigure mumble-server
On Windows,
 <path to murmur.exe> (usually C:\Program Files\Mumble\Murmur.exe)

For debugging or real time logging, you might want to add ''-fg -v'' to the command line, which will stop the program from running in the background.

By default, Murmur opens its configuration file, database file and logfile in your current directory. The configuration file can be overridden with the ''-ini'' parameter, and the database and logfile can be set from the ini file, using their respective parameters.

= Advanced Configuration and Administration=

To make use of a strong server certificate the users will not have to manually accept, please see [[Obtaining a Let's Encrypt Murmur Certificate]] and [[Obtaining a Comodo Murmur certificate]].

{{Notice
|message=Most of these interfaces are created and maintained by third parties and the Mumble developers have no influence on the stability and/or security of these projects. 

Also, nearly all of the basic administration tasks can be completed '''through the client''' when using > Mumble 1.2.x.
}}
## Compatibility With RPC-Interfaces 

For full functionality with an RPC interface, Murmur requires either a working [[DBus]] daemon or [[Ice]] installation that is enabled. We recommend using the [[Ice]] interface; [[DBus]] is considered deprecated and although it will not be removed in the near future, it is not receiving any new functionality. Once you have Murmur working with the RPC interface, you can install a compatible web interface; see below for possible options.

## Authenticating With an External Database/Forum 

###Ice
For phpBB3, there is  [phpBB3auth](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/phpBB3). You must point the python script to the ini file; read the in-source documentation for more infomation.

For SMF (Simple Machines Forum), there is  [smfauth](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/SMF). You must point the python script to the ini file; read the in-source documentation for more infomation.

###DBus

There is an extended example of how to use the authenticator called ''scripts/dbusauth.pl''. You'll need to configure where your phpBB3 database resides, but once that is done you'll simply have to run the script after starting murmur to allow authentication to be done through the phpBB3 database.

Any group associations the user has on phpBB3 is copied to a temporary group on a root channel (and by default inherited to all subchannels). Please note that this is a temporary group membership and as such will not show up in the Edit ACL dialogs.

## 3rd Party Applications 

If you are planning to administrate your Murmur server with an external 3rd Party Application, see the following pages for further information.

* '''[Web-Interfaces](3rd_Party_Applications#Web-Interfaces.md)'''
* '''[Standalone Applications](3rd_Party_Applications#Standalone Applications.md)'''
* '''[Commandline-Interfaces](3rd_Party_Applications#Commandline-Interfaces.md)'''

{{Notice
|message=The aforementioned categories have been moved to the page '''[3rd Party Applications](3rd_Party_Applications.md)'''.
}}

## Manual Configuration Using DBus 

If you are not able to use an additional application for administrating Murmur there is still the possibility of manually communicating with the server using [DBus article](DBus]]. You can find detailed information on this in our [[DBus.md).

= Alternative Mumble Servers =
There are multiple alternative Mumble Servers which support the Mumble protocol. <br>
Everyone is free to implement their own Mumble server software and add it to this list.

{{Notice
|message=It is recommended to use the Standard Mumble Server. <br>
These Servers vary in functionality, so check for features and compatibility before use.
}}
 
## Grumble 
Grumble is a Mumble Server based on Go (programming language). <br>
It is in active development by the official Mumble team. <br>
Take a look at the Github Repo: https://github.com/mumble-voip/grumble

{{Notice
|message=For now Grumble lacks support for some features (e.g. remote control, config system). <br>  
See https://github.com/mumble-voip/grumble#project-status for more details.
}}

## uMurmur 
{{Notice
|message=uMurmur is outdated (last updated: 2017). So it is not recommended for use and might not be compatible with recent versions of Mumble.
}}

uMurmur is a minimalistic Murmur implementation without dependency on QT-core. It lacks features of the Mumble server, but aims at working well on embedded devices like routers. 

Read more at  [page](http://umurmur.net the uMurmur project).



