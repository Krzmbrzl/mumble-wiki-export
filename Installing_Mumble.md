__TOC__

=Download and Install Mumble and Mumble-Server (aka Murmur)=

##Windows
'''Mumble:'''<br>   
Download the latest stable version of Mumble from the  [Website](https://www.mumble.info/downloads/ Official).<br>   
The installer will guide you through the installation and configuration of Mumble.    

Alternatively you can download and run the latest MSI installer (mumble-1.x.x.msi; "winx64" for the 64-bit version) from the  [page](https://github.com/mumble-voip/mumble/releases GitHub releases).<br>    
''Note:'' Releases that include the term "RC" are '''R'''elease''' C'''andidates and therefore Test Versions.

'''Mumble-Server (aka Murmur):'''<br>   
The Mumble-Installer includes an option to install the Mumble-Server.

##Mac OS X
'''Mumble:'''<br> 
Download the latest stable version of Mumble from the  [Website](https://www.mumble.info/downloads/ Official).<br>

Alternatively you can download the latest version from the:  [page](https://github.com/mumble-voip/mumble/releases GitHub releases). <br>    
''Note:'' Releases that include the term "RC" are '''R'''elease''' C'''andidates and therefore Test Versions.

In order to be able to use the '''[[Overlay]]''' it has to be installed separately. <br>
To install it: launch Mumble, go into ''Mumble's settings'' -> Overlay section and you should see an ''option to install it''.<br>
The reason for the separate installation is that Mumble itself does not need administrative rights to install, but the overlay does.

'''Mumble-Server (aka Murmur):'''<br> 
You can download a static version of the Mumble-Server from the  [Website](https://www.mumble.info/downloads/ Official).<br>

##Linux
On the most popular Linux distributions, Mumble should be available in the official repositories or third-party repositories. <br>
For Details, take a look at the distribution-sections below. <br>
If no package is available, take a look at the [Snap](Installing Mumble#Snap_Package_.28for_various_Distributions.29.md)- and [Flatpak](Installing_Mumble#Flatpak_Package_.28for_various_Distributions.29.md)-packages below (which will run on various distributions) or you can try to compile Mumble, see Section: [Building-Mumble](Installing_Mumble#Building_Mumble.md).

###= Debian =

To install Mumble from the Debian Repository, run:

 apt-get install mumble

For the Mumble-Server, run:
 apt-get install mumble-server

{{Notice
|message=The ''mumble-server''-Package on Debian and Debian-based distributions (i.a. Ubuntu) will start automatically on system-start.<br>
You can disable the autostart with systemd.
You find details in the file "README.Debian".
}}

###= Ubuntu =

The Ubuntu Repositories include a Mumble version from the time when the Ubuntu Version was released, thus it might be outdated. <br>
We also maintain a  [PPA](https://launchpad.net/~mumble/+archive/release) ( [stable](https://launchpad.net/~mumble/+archive/release)) with
the recent versions of Mumble.<br>
If you want to try the latest development version, you can use the: ( [snapshots](https://launchpad.net/~mumble/+archive/snapshot dev))

To add the PPA use:

 sudo add-apt-repository ppa:mumble/release
 sudo apt-get update

To install the client you can use:

 sudo apt-get install mumble

to install and configure the server use:

 sudo apt-get install mumble-server
 sudo dpkg-reconfigure mumble-server

{{Notice
|message=The ''mumble-server''-Package in Ubuntu will start automatically on system-start.<br>
You can disable the autostart with systemd.
You find details in the file "README.Debian".
}}

### RHEL (and its derivatives, such as CentOS) 

Please see the [[Install CentOS5]] page for both packaged and manual murmur installation instructions. Mumble is not easily built on this platform at this time, and there are no official packages (yet?).

For CentOS 6 see the [[Install CentOS6]] page.

For CentOS 7 see the [[Install CentOS7]] page.

### Fedora 

Install from Fedora Repositories:

To install mumble, run:
  dnf install mumble

For the Mumble-Server, run:
  dnf install murmur

There are additional packages available for the [[Overlay]] and Plugins:
* mumble-overlay
* mumble-plugins

### SUSE 

Mumble packages are available from  [software.opensuse.org](http://software.opensuse.org/package/mumble).

You can follow these steps while running openSUSE:
# Open a web browser and go to  [software.opensuse.org/package/mumble](http://software.opensuse.org/package/mumble)
# Assuming you're running 32bit, click on '''1-Click Install''' located at the first result
# When asked to download a file, tell your browser you want to open the file
# Once YaST is opened, click ''Next'' (leave defaults), then ''Next'' again, and again
# Enter your root password if asked; Mumble will now download
# Click '''Finish'''
# To run Mumble:
## Open the Kickoff application launcher and type '''mumble''', then --> '''Run mumble'''
## Or: open a terminal and type '''mumble''' and press enter


''Note: If you are asked to accept a certificate just press '''OK'''''

''Note: Latest mumble version can usually be found at  [opensuse.org](http://software.opensuse.org/package/mumble) under "Show other versions" either at "openSUSE Factory" or under "Show unstable packages" of your openSUSE version.''

Some packages can also be found in the  [Service](http://download.opensuse.org/repositories/home:/lnussel:/mumble:/unstable/ Build).

### Arch Linux 
To install Mumble from the Arch Repositories, run:
 pacman -S mumble

For the Mumble Server (aka Murmur):
 pacman -S murmur

There are also unstable packages available in the  [AUR](https://wiki.archlinux.org/index.php/Arch_User_Repository):
* Mumble Unstable (updated directly from Git): https://aur.archlinux.org/packages/mumble-git/
* Mumble-Server Unstable (updated directly from Git): https://aur.archlinux.org/packages/murmur-git/

### Mandriva/ROSA/Unity 

Mumble is available since 2010.0.

 urpmi mumble

It's best to install the package from Cooker - it has many fixes.

### Snap Package (for various Distributions) 

An Snap Package is available: https://snapcraft.io/mumble<br>

It is maintained by a third-party: the Snapcrafters.

### Flatpak Package (for various Distributions) 

A Flatpak Package is available: https://www.flathub.org/apps/details/info.mumble.Mumble

### Building Mumble 

If all of the above options fail to work, you can always try to [compile Mumble from source](BuildingLinux.md), however installing a package is considered "best practice".

## BSD 
### FreeBSD  
To install Mumble:

 pkg install mumble

To install Murmur:

 pkg install murmur

To enable Murmur:

 sysrc murmur_enable="YES"

### OpenBSD 
To install Mumble:

 pkg_add mumble

To install the Mumble-Server (Murmur):

 pkg_add murmur

To enable Mumble-Server:

 rcctl enable murmurd

# Notice|message=The murmur package became available with the release of OpenBSD 6.7 and doesn't exist in OpenBSD 6.6 and previous releases.

## Smartphones 

### Android 
[[Mumla]] is an unofficial client (by Quite), it's the successor of deprecated Plumble.

It has many features in addition to the Mumble's ones, such as: bluetooth headset support, proximity sensor utilizing "Voice Call" mode and hardware push-to-talk key support.

You can download Mumla on  [F-Droid](https://f-droid.org/packages/se.lublin.mumla/) and on the  [Playstore](https://play.google.com/store/apps/details?id=se.lublin.mumla Google).

### iPhone 
# Notice|message=The iOS client is outdated!

The Mumble iOS client is available  [Store](https://itunes.apple.com/us/app/mumble/id443472808?mt=8 on the App).

You can find more information about the iOS client from the  [repo](https://github.com/mumble-voip/mumble-iphoneos mumble-iphoneos GitHub). Any help with the project is always appreciated.


