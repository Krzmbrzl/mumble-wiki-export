Murmur supports remote scripting using [ZeroC
Ice](http://www.zeroc.com/), a RPC mechanism. There are bindings for
C++, Java, .NET, Python, PHP and Ruby, and this is supported on all our
platforms (Win32, Linux and OSX). Ice works locally and also over a
network, meaning you can create a web application that interfaces with a
Murmur process running on another machine.

# Getting ready to use Ice

To enable the Ice interface in your *murmur.ini* configuration file for
*localhost* on port *6502* add or uncomment:

`ice="tcp -h 127.0.0.1 -p 6502"`

Now restart Murmur so the change takes effect.

To check if Ice in fact does listen, on UNIX type:

`netstat -apn | grep 6502`

and on Windows type:

`netstat -an `

and look for the process listening on port *6502*.

If the port is not being listened on, check Murmurs log. It should state
enabling ice on startup. If it does not, something of your configuration
went wrong.

`MurmurIce: Endpoint "tcp -h 127.0.0.1 -p 6502" running`

# End User Howtos

Note that after you have ICE set up on your machine, you can install a
[web interface](3rd_Party_Applications#Web-Interfaces "wikilink").

How to convert Murmur.ice to Murmur.php for Ice \>= 3.4.0 :
<http://doc.zeroc.com/display/Ice/slice2php+Command-Line+Options>

## How to setup Ice 3.4 for PHP with Apache on Linux (general)

If your Linux distribution offers a binary packet for Ice with PHP
(usually the name contains Ice and php) you can skip everything but
naming the Murmur.ice slice file in the php.ini (see below). If there is
no prepared package you'll have to try to find binaries for your system
or [compile](Ice#Compiling_Ice "wikilink") Ice yourself and add the
extension to PHP and tell PHP where to find the Murmur.ice file.

To add the IcePHP extension to PHP, first check that the file IcePHP.so
for linux is in your php extensions folder specified in your php.ini as

`extension_dir = /usr/lib/php5/extensions`

If it is not, get the corresponding files from [ZeroC's downloads
page](http://www.zeroc.com/download.html).

Then either in your php.ini file or in your /etc/php.d or
/etc/php5/conf.d folder in ice.ini, add the line

`extension=IcePHP.so`

At least the Linux RPMs will do this automatically, so check that you're
not doing it a second time.

Second, you have to tell the PHP parser where to find the slice
(**S**pecification **L**anguage for **Ice**) file. Add

`ice.slice = /path/to/Murmur.ice`

to your php.ini or other config file (e.g. ice.ini).

### Troubleshooting

If you encounter problems, check your Apache log.

If it tells you the PHP extension was compiled on an older api, you have
to compile the IcePHP.so from source.

Download Ice-3.4.2.tar.gz from [ZeroCs downloads
page](http://www.zeroc.com/download.html), untar, cd into PHP, as
written in the INSTALL file export ICE_HOME environment variable
pointing to your Ice install dir. If you installed it with an RPM, type

`export ICE_HOME=/usr`

then make, and in the lib folder, there'll be your IcePHP.so file.

One common error is

`PHP Warning:  PHP Startup: skipping dictionary ::Murmur::UserInfoMap - unsupported key type in Unknown on line 0`

This is caused because the .ice is slightly incompatible with older
versions of php-ice - edit the Murmur.ice file and find the following
lines

`/** User information map.`
`* Older versions of ice-php can't handle enums as keys. If you are using one of these, replace 'UserInfo' with 'byte'.`
`*/`

and perform the substitution mentioned.

## How to Setup Ice for PHP with Apache on Debian/Ubuntu

**Note:** For the **PHP Ice**, there are major differences between the
Ice versions 3.3 and 3.4. In more detail: 3.3 uses *.ice* definition
files while 3.4 uses compiled/converted PHP files.

Thus, depending on the version you are installing, you will have to
follow different configuration steps.

At the moment \[2012.05.06\], the current Debian stable is *squeeze*,
for which the official repositories provide version the *Ice 3.3*. For
Ubuntu on the other hand, the current stable version *12.04* (LTS)
provides *Ice 3.4* in its repositories. So **make sure you follow the
matching instructions**.

**Short, expert version**:

  - If php-zeroc-ice version \>= 3.4: *`apt-get install php-zeroc-ice`*,
    then add `/usr/share/Ice-3.4.2/php/lib` to your PHPs *include path*.
  - If php-zeroc-ice version \<= 3.3: *`apt-get install php-zeroc-ice`*,
    then add the `ice.slice` parameter to with value
    <pathto>`/murmur.ice` to your PHPs configuration.

For the following guide, a set up Apache2 and PHP environment, and a
working install of Murmur is assumed.

*' Step 1 - PHP Ice extension*'

First we need to install the Ice library for PHP. Execute the following
in a root shell:

`apt-get update`

`apt-get install php-zeroc-ice`

''' Step 2 - PHP Setup '''

Now we need to tell PHP to load the IcePHP extension. Open the file
*/etc/php5/apache2/php.ini* for editing:

`vim /etc/php5/apache2/php.ini`

OR:

`nano -w /etc/php5/apache2/php.ini`

Paste the folowing in the dynamic extensions section of the file:

`extension=IcePHP.so `

''' Step 3 - Reload and Check '''

Everything should be set up so let's restart the servers so they load
the updated config files.

Restart your Apache2 daemon:

`/etc/init.d/apache2 restart`

Make a file named phpinfo.php in your web root and paste the following:

<?php phpinfo(); ?>

Open the page in your browser, you should be greeted with PHP's
information page. Search the page for "Ice version" to verify that the
IcePHP extension has loaded. If you don't see IcePHP's version and
config info on this page, verify that the file IcePHP.so exists in PHP's
*extension_dir* (this will also be in your PHP info page). Once you're
sure that the IcePHP extension has loaded, delete the phpinfo.php file
for security reasons.

Now we will take a look in the mumble-server log to see if Murmur's Ice
interface is listening:

`tail -n10 /var/log/mumble-server/mumble-server.log`

If you find a line similar to the following everything is fine and you
can now communicate to Murmur via its Ice interface.

`...`
<W>`2012-03-24 13:37:11.316 MurmurIce: Endpoint "tcp -h 127.0.0.1 -p 6502" running`
`...`

''' Step 4 - Setting up Murmur to provide Ice interface '''

Now open the file */etc/mumble-server.ini* for editing:

`vim /etc/mumble-server.ini`

OR:

`nano -w /etc/mumble-server.ini `

Comment the following line to disable [DBus](DBus "wikilink"):

`#dbus=system`

Uncomment or paste the following line to enable the Ice interface:

`ice="tcp -h 127.0.0.1 -p 6502"`

Restart your Mumble server:

`/etc/init.d/mumble-server restart`

After restarting the daemon Murmur will now listen for Ice requests.

Now you can install and use any of the PHP based [3rd Party
Applications](3rd_Party_Applications "wikilink") compatible with IcePHP
version 3.4.

## How to setup Ice for PHP with Apache on Windows

These are example scripts. Use at your own risk. These scripts are not
intended for production machines. These are examples of what Ice can do.
Note that if you already have a web server installed on the server you
can adapt this guide to use it instead of installing Apache.

First install
[Apache](http://apache.mirror.facebook.com/httpd/binaries/win32/apache_2.2.11-win32-x86-openssl-0.9.8i.msi).
Install it to *C:\\apache\\*.

Now install
[PHP](http://www.php.net/get/php-5.2.8-win32-installer.msi/from/us.php.net/mirror).
Tell PHP to install to *C:\\PHP5\\*. In the installer on the "Web Server
Setup" window select Apache 2.2.x Module. When you get to "Select Apache
Configuration Directory" put *C:\\apache\\conf\\*. Proceed through the
installer. Install the defaults, you do not need to install the
extensions for PHP.

Now [download](https://zeroc.com/downloads/ice) and install
Ice-*x.x.x*-VC60.msi. Go to *C:\\Ice-3.3.1-VC60\\bin\\* and copy

`bzip2.dll `
`ice33.dll `
`iceutil33.dll `
`msvcp60.dll `
`msvcrt.dll `
`php_ice.dll `
`slice33.dll `
`stlport_vc646.dll `

to *C:\\apache\\bin* . Now open *C:\\PHP5\\php.ini* and add the
following two lines to the bottom of the file:

`extension=php_ice.dll`
`ice.slice=C:\PHP5\Murmur.ice`

Now save and exit php.ini.

After you have done all that, download
[Murmur.ice](mumblegithub:/mumble/raw/1.2.8/src/murmur/Murmur.ice "wikilink"),
[icedemo.php](mumblegithub:/mumble/raw/1.2.8/scripts/icedemo.php "wikilink"),
and
[weblist.php](mumblegithub:/mumble/raw/1.2.8/scripts/weblist.php "wikilink")
(Click the links, and on the Sourceforge page right click on
"(download)" and select "Save Link As...".) Put Murmur.ice in
*C:\\PHP5*. Put icedemo.php and weblist.php in *C:\\apache\\htdocs*.

Double click the Apache icon in the system tray and select "Restart".

You now need at least one running Murmur server. Go to C:\\Program
Files\\Mumble and double click murmur.exe and the server will start.

You should now be able to go to <http://><your IP or Domain>/icedemo.php
(or weblist.php). Make SURE that you have icedemo.php protected so that
only YOU can access it. If you do not want to use icedemo.php,
[here](3rd_Party_Applications#Web-Interfaces "wikilink") is a list of
other web interfaces you can use.

## How to setup Ice for PHP with XAMPP on Windows

### pre Setup

Download and install the following packages:

  - XAMPP for Windows <http://www.apachefriends.org>
  - ZeroC Ice <https://zeroc.com/downloads/ice>

Now configure and start XAMMP.

### Create developer environment for Windows

  - Open System in Control Panel ( On Windows VISTA/7 Systems select
    advanced )
  - On the Advanced tab, click Environment Variables
  - Add the Ice Path to %PATH%

Select the name PATH on user variables and edit. If the name PATH does
not exist, select new. Enter now the PATH to your Ice installation dir.

Sample for 32Bit:

`%PROGRAMFILES%\ZeroC\Ice-3.4.0\bin;%PATH%`

Sample for Windows x64:

`%PROGRAMFILES(x86)%\ZeroC\Ice-3.4.0\bin;%PATH%`

Now logout from Windows or restart. After reboot check if included Ice
in our environment. Open the CMD and try

`slice2php`

The Output return the slice2php help. If not check
<http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/environment_variables.mspx?mfr=true>

### Configure XAMPP/PHP

Copy the File php_ice.dll from <your path>\\ZeroC\\Ice-3.4.0\\bin to
<your_path>\\xampplite\\php\\ext Edit the php.ini in
<your_path>\\xampplite\\php and add

`extension=php_ice.dll`
`ice.slice=`<mumble_path>`\Murmur.ice`

Now start XAMMP and check the phpinfo().

## Using different ice.slice on same host

Sometimes you run two servers of mumble on the same host and you cannot
load two slices with different mumble versions on the same time. The
solution is to use ICE profiles, that will require extra files and
unfortunately modification of scripts that run the default profile.
Description on Debian etch with apache2, PHP as fcgid and cli.

### Creating profiles

  - Lets create profile directory (as root/superuser user), I have
    created mine at

`/etc/php5/ice/`

  - Then create directories per profile (it will make life easier later)

`/etc/php5/ice/murmur.1.1.x`
`/etc/php5/ice/murmur.1.2.x`

  - To each of the corresponding directory I have placed the Murmur.ice
    file provided with the installs. You will notice that later upgrades
    will just consist of copying new files (instead of renaming).
  - time to make profiles.ini file that ICE will use:

`vi /etc/php5/ice/profiles.ini`

  - Insert there below code:

<code>

    [Murmur11x]
    slice=/etc/php5/ice/murmur.1.1.x/Murmur.ice

    [Murmur12x]
    slice=/etc/php5/ice/murmur.1.2.x/Murmur.ice

</code>

  - This way you got two profiles, first (Murmur11x) is loading slice
    file for older murmur setups, and the other (Murmurm12x) loads newer
    slices. Below example of directory structure:

`/etc/php5/ice`
`|-- murmur.1.1.x`
``|   `-- Murmur.ice``
`|-- murmur.1.2.x`
``|   `-- Murmur.ice``
`` `-- profiles.ini ``

### IcePHP.ini

  - Now time to alter /etc/php5/cgi/conf.d/IcePHP.ini, so it will look
    like this

<code>

    extension = IcePHP.so
    ice.profiles=/etc/php5/ice/profiles.ini

</code>

  - Notice that we are adding ice.profile setting, so that ice knows
    where to search for profiles.
  - Default profile is named __default__ and you better avoid to
    make it.
  - I got no idea about setting up default ice.slice entry (experience
    told me to force editing php files anyway, read below)

#### Changing PHP scripts

  - Next alter the source code of the php scripts you use. It consists
    of just altering the one function that tells ICE to load profile. By
    default the function is ran without parameter, and it looks like
    below:

`Ice_loadProfile();`

  - Now we will tell that function to load specific profile that it was
    designed for. Below example modifications to load different profiles
    for given ice profile:

for older mumble:

`Ice_loadProfile('Murmur11x'); // load profile for scripts that talk with murmur 1.1.x`

or for new mumble:

`Ice_loadProfile('Murmur12x'); // load profile for scripts that talk with murmur 1.2.x`

  - Notice that single quotes are required.

### Checking out if it works

  - Remember to restart apache (your configuration may require it)
  - See php/apache error logs when something goes wrong.
  - If you get error like *unknown operation getUsers invoked on proxy
    of type ::Murmur::Server* then it means you use old Murmur.ice file.
    This happens when you try to connect using Murmur.ice from version
    1.1.x to Murmur server 1.2.x, which require Murmur.ice 1.2.x. Update
    Murmur.ice on web server and restart it and then it should work.

### Further steps

  - I suggest you do the same with /etc/php5/cli/conf.d file and scripts
    that you run from console (crontab)
  - Altering php.ini error_reporting is advised to disable generating
    massive amount of warning messages:

`error_reporting = E_ALL & ~E_NOTICE & ~E_WARNING`

  - You can also set up config files for those profile - more info at
    <http://www.zeroc.com/doc/Ice-3.3.1/manual/IcePHP.29.3.html>

# Developing for the Murmur Ice interface

How to use Ice differs from language to language. The parameters and
method names will remain the same, but the syntax will naturally be
different. Murmur will, by default, open up an adapter on port 6502 (or
10000 for homedir installs), which has a single accessible object named
"Meta". This is the Meta server, and from it you can retrieve adapters
for any configured server.

The ice interface is fully documented, and you can browse the [generated
documentation](http://mumble.sourceforge.net/slice).

## PHP

With *IcePHP* establishing the connection to the interface **differs**
between the Ice versions 3.3 and prior and 3.4 and later.

\=== Ice \<= 3.3 === There's an example script using the **Ice 3.3**
approach (defining the ice.slice directive in the PHP settings) included
in the source; have a look at
[mumblegithub:/mumble/blob/1.2.4/scripts/icedemo.php](mumblegithub:/mumble/blob/1.2.4/scripts/icedemo.php "wikilink").

The establishing, minimum code, is:

`Ice_loadProfile();`
`// initialize ice connection`
`global $ICE;`
`$base = $ICE->stringToProxy('Meta:tcp -h 127.0.0.1 -p 6502');`
`$meta = $base->ice_checkedCast("::Murmur::Meta");`

\=== Ice \>= 3.4 === For **Ice 3.4** and later you’ll have to do a
different approach.

First, you’ll have to **generate PHP code** from the slice definitions
.ice file. \>=Ice 3.4 installed, use the **slice2php executable** to
generate it.

For your PHP code, you’ll have to have the Ice.php and other libs
(scripts provided by zeroc) in your PHPs include path to include them.

`require_once 'Ice.php';`
`require_once 'Murmur.php';`
`$ICE = Ice_initialize();`
`$meta = Murmur_MetaPrxHelper::checkedCast($ICE->stringToProxy('Meta:tcp -h 127.0.0.1 -p 6502'));`

Where *Murmur.php* is the generated file.

## Python

To use the ICE interface with a Python client, you'll have to have the
`zeroc-ice` package installed (can be installed using pip:
<https://doc.zeroc.com/ice/latest/release-notes/using-the-python-distribution>).
Be aware that Python2 and Python3 require different packages of
zeroc-ice.

In the first step, you'll have to compile the slice file to generate the
backend Python code. To do this, you have to use the **slice2py
executable** on the `Murmur.ice` slice file. At least on Linux, you'll
also have to provide some include directories:

`slice2py --checksum -I/usr/local/share/Ice -I/usr/share/Ice/slice -I/usr/share/ice/slice -I/usr/share/slice Murmur.ice`

After that you can write a small ICE client like so (assuming you have
used the standard `ice="tcp -h 127.0.0.1 -p 6502"` config in
`murmur.ini`):

`import sys, Ice`
`import Murmur`

`with Ice.initialize(sys.argv) as communicator:`
`    base = communicator.stringToProxy("Meta:tcp -h 127.0.0.1 -p 6502")`

`    meta = Murmur.MetaPrx.checkedCast(base)`
`    if not meta:`
`        raise RuntimeError("Invalid proxy")`

`    servers = meta.getAllServers()`
`    `
`    if len(servers) == 0:`
`        print("No servers found")`

`    for currentServer in servers:`
`        if currentServer.isRunning():`
`            print("Found server (id=%d):\tOnline since %d seconds" % (currentServer.id(), currentServer.getUptime()))`
`        else:`
`            print("Found server (id=%d):\tOffline" % currentServer.id())`

This code will use ICE to get a list of all configured virtual servers
and prints them and their status to the console.

If you're using Python3 you might run into a bug that prints out `double
free or corruption (out)` once the program is terminated. Apparently
this is a bug that only shows in combination with gcc7 (and Pyhton3).
More on that can be found at
<https://forums.zeroc.com/discussion/46580/python-3-6-3-ice-3-5-1-crash-on-exit>.
The bug might be solved by simply using Python2 instead and/or by
installing a more recent version of the `zeroc-ice` package.

# Using Glacier2

Glacier2 is a Ice **routing and firewall utility**, and allows you to
securely run the server on one machine and murmur on another. Note that
if both server and client are on a secure LAN, you can just use iptables
to protect the Ice port, which is a lot easier than setting up Glacier2.
Also, **since Mumble 1.2.2 you can set an icesecret** in your murmur.ini
and use it as a password. **This is a lot easier to set up** and use
than Glacier2.

The examples here assume that 1.2.3.4 is the public IP address of the
server running Murmur. We're going to use the username "magic" with the
password "pink".

## Configuring Glacier2

Create a config file called config.glacier2 and put the following in it:

` Glacier2.Client.Endpoints=tcp -h 1.2.3.4 -p 4063`
` Glacier2.SessionTimeout=60`
` Glacier2.CryptPasswords=passwords.txt`

Your endpoint host should be the public IP that you are running Glacier
on. If you don't specify a client via -h, then Glacier will bind to all
listening interfaces.

Then, create a password hash using the OpenSSL utility.

` openssl passwd pink`

this will spit out a hash, which looks something like CTThafhdv9Lz2

Create a file called passwords.txt containing:

` magic CTThafhdv9Lz2`

Start glacier2 as this:

` glacier2router --Ice.Config=config.glacier2`

You will need to have Ice installed - <https://zeroc.com/downloads/ice>
glacier2router is a binary that is located in
*<location_of_Ice_installation>/bin/glacier2router.exe.*

## Configuring Murmur

There's nothing to do in murmur. Seriously. Leave the default setting of
binding to 127.0.0.1 alone.

## Configuring Client (PHP)

This is where it starts getting slightly ugly. Note that this requires
Ice \>= 3.3.1, as Ice 3.3.0 has a bug in it which prevents this from
working. The following is the adaptation necessary to weblist.php to get
it to work:

    try {
      $router = $ICE->stringToProxy("Glacier2/router:tcp -p 4063 -h 1.2.3.4");
      $router = $router->ice_uncheckedCast("::Glacier2::Router")->ice_router(null);
      $session = $router->createSession("magic", "pink");
      $base = $ICE->stringToProxy("Meta:tcp -h 127.0.0.1 -p 6502")->ice_router($router);
      $meta = $base->ice_checkedCast("::Murmur::Meta")->ice_router($router);

      ...

For each object you get a proxy to (including the return from
$meta-\>getServer), you need to add -\>ice_router($router)

## Configuring Client (Ruby)

There is a set of classes for easily working with Ice directly and
through Glacier available at
[GitHub](https://github.com/cheald/murmur-manager/tree/master/interfaces/).
However, if you want to do it manually, it's not too hard.

    glacierHost = "yourhost.com"
    glacierPort = 1234
    user = "glacieruser"
    pass = "glacierpass"
    server_id = 1

    prx = ic.stringToProxy("Glacier2/router:tcp -h #{glacierHost} -p #{glacierPort}")
    router = ::Glacier2::RouterPrx::uncheckedCast(prx).ice_router(nil)
    router.createSession(user, pass)
    meta = Murmur::MetaPrx::checkedCast(ic.stringToProxy("Meta:tcp -h #{host} -p #{port}")).ice_router(router)
    server = meta.getServer(server_id).ice_router(router)

For each object you get a proxy to (including the return from
Murmur::MetaPrx::getServer), you need to add \#ice_router(router)

# Compiling Ice

On some platforms there are no officially supported binaries available.
In that case you will either have to change your platform or compile Ice
yourself.

## Building Ice on Redhat/CentOS machines

**Note:** 3.3.1 is no longer the current version of Ice. Feel free to
try this guide with the new version and update it if it works, or fix it
if it does not.

1\. Download and unpack ICE

` wget `<http://www.zeroc.com/download/Ice/3.3/Ice-3.3.1.tar.gz>
` tar -xzf Ice-3.3.1.tar.gz`

2\. Compile the ICE CPP bindings (these are required for all other
bindings) You will need mcpp-devel from the Zeroc website installed to
compile. <https://zeroc.com/downloads/ice> - Ctrl-F and look for
"mcpp-devel". There is a big package of various Ice RPMs to download.
You will install a few dependencies, along with the mcpp-devel package.

` cd Ice-3.3.1/cpp`
` make`

(wait 20 minutes)

` sudo make install`

3\. Compile and install the Ice bindings for your preferred language.
For example, to install Ruby bindings:

` cd ../rb`
` make`
` sudo make install`

4\. Export the paths for your newly-installed libraries. These will be
different for each language - check the INSTALL or README files in each
language's subdirectory for exact instructions.

For Ruby:

` export RUBYLIB=/opt/Ice-3.3.1/ruby:$RUBYLIB`
` export LD_LIBRARY_PATH=/opt/Ice-3.3.1/lib:LD_LIBRARY_PATH`

If you don't want to always have to keep running those export lines,
also add them to your \~/.bashrc:

` export RUBYLIB=/opt/Ice-3.3.1/ruby:$RUBYLIB`
` export LD_LIBRARY_PATH=/opt/Ice-3.3.1/lib:LD_LIBRARY_PATH`

4\. At this point, Ice should be available to your language (in this
case, Ruby):

` $ irb`
` irb(main):001:0> require 'Ice'`
` => true`

5\. Generate the Slice file for your language.

To generate it for ruby, we use the slice2rb program, which is in the
Ice/cpp/bin directory. Similar binaries for your language of choice will
be there, too.

` wget -O Murmur.ice "`<https://raw.github.com/mumble-voip/mumble/master/src/murmur/Murmur.ice>`"`
` ../cpp/bin/slice2rb Murmur.ice`

` cp Murmur.rb #{MANAGER_ROOT}/vendor/ice`

Congrats\! Ice should be set up and fully functional.

[Category:Documentation
English](Category:Documentation_English "wikilink")