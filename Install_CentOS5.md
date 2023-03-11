= Installation of murmur server on CentOS 5 =

It is currently very difficult to build Mumble and Murmur on RHEL 5 and its derivatives, such as CentOS 5. For these systems, it is recommended to use the current static binary, linked from the [Mumble home page](Main_Page.md).

Unfortunately, if you use the static binary, you will have to manually start the server each boot or write your own initialization scripts (see [[#Manual Installation]], below). For this reason, there is now a third-party package available, which configures murmur as if it were provided by the operating system.

## Package Installation 

There is an unofficial, unsupported, third-party package of (the statically linked) Murmur available for installation via yum. It has only been tested on CentOS 5.6 (i386) at this time, but should work on other RHEL 5.x versions and derivatives. If you have any problems or feedback (such as results on other distros besides Centos 5.6 i386), please find [lewellyn]] on [[IRC](User:lewellyn.md). The package is not officially supported by anyone, but the package definition and configuration scripts derive from the Fedora 15-Alpha and Mandriva packages and the binary is the official static tarball from mumble.sf.net, the various pieces of which are known to work reliably.

''(As of April 2011, the third-party GBS repository is providing Murmur 1.2.3.)''

The steps are as follows:

# As root (such as via sudo), run: <code><nowiki>rpm -ivh http://pkg.geekbakery.net/RedHat/5/stable/noarch/gbs-release-1.0-1.gbs.noarch.rpm</nowiki></code>
##'''Optional:''' Configure your new repository, for example using the  [priorities](http://wiki.centos.org/PackageManagement/Yum/Priorities) plugin.
# Install murmur from the new  [repository](http://pkg.geekbakery.net/ GBS) you just added: ''(run the commands as root or via sudo)''
## If you want to just install murmur and don't care about ensuring you have the proper dependencies for the web functions or dbus: <code>yum install murmur</code>
## Instead, if you want to make sure you have all the proper dependencies for running with dbus and the included web scripts (this package depends on murmur): <code>yum install murmur-suggests</code>
## '''''NOTE:''''' The first time you install a package from the GBS repository, you may/should get a prompt to accept the key. The proper ID for this key is <tt>98b3c52e</tt>. If this matches what is on your screen, enter '<tt>y</tt>' at the confirmation prompt.

That's it! Now you can <code>service murmur start</code> to start your new server. Or, if you wish, you can [customize your configuration](murmur.ini.md) first.

Note that installing from the GBS repository indicates acceptance of the  [agreement](http://pkg.geekbakery.net/GEEKBAKERY-SRA.txt repository's). Summary of the agreement is: ''No support nor warranty is offered, and if it breaks, you get to do what you will with the pieces.''


## Manual Installation 

Here's the process for manually installing on CentOS 5.4, using the init script and config from a mandriva rpm and the 1.2.2 static binary release: ''(You can use this as the starting point for your own manual installation of the latest version.)''

<pre>
yum install lzma

cd ~/downloads
wget http://sourceforge.net/projects/mumble/files%2FMumble%2F1.2.2%2Fmurmur-static_x86-1.2.2.tar.lzma/download
wget ftp://rpmfind.net/linux/Mandriva/devel/cooker/x86_64/media/contrib/release/mumble-server-1.2.2-3mdv2011.0.x86_64.rpm
cd ~/install

lzcat ../downloads/murmur-static_x86-1.2.2.tar.lzma | tar -xf -
cp murmur-static_x86-1.2.2/murmur.x86 /usr/sbin/murmurd

rpm2cpio ../downloads/mumble-server-1.2.2-1mdv2010.1.x86_64.rpm > file.lzma
lzma -d file.lzma
mkdir mumble-rpm
cd mumble-rpm
cpio -imv --make-directories < ../file
rm ../file

cp etc/mumble-server.ini /etc
cp etc/rc.d/init.d/mumble-server /etc/rc.d/init.d
chmod a+x /etc/rc.d/init.d/mumble-server

groupadd -g 4000 mumble-server
useradd -g 4000 -G mumble-server -s /sbin/nologin -d / -M mumble-server
mkdir /var/lib/mumble-server
chown mumble-server:mumble-server /var/lib/mumble-server
mkdir /var/log/mumble-server
chown mumble-server:mumble-server /var/log/mumble-server
vim /etc/rc.d/init.d/mumble-server
</pre>

Change all occurrences of 'gprintf' to 'printf'

<pre>
service mumble-server start
chkconfig --add mumble-server
chkconfig --level 3 mumble-server on
</pre>

(thanks to dominicc on the mumble forum)



