Installation of murmur server on CentOS 6 with standard settings

-----

# General configuration

Regardless of murmur version, you need to create iptables rules for
murmur. Below is an example of how to do that using the standard port
64738.

## Configuration iptables

    service iptables stop

    iptables -A INPUT -p udp -m udp --dport 64738 -j ACCEPT
    iptables -A INPUT -p tcp -m tcp --dport 64738 -j ACCEPT

    service iptables save
    service iptables start

# Murmur 1.2.4

## The binary package and the source

    https://www.dropbox.com/s/wla29wnabsz53nq/mumble-server-1.2.4-1.el6.x86_64.rpm
    https://www.dropbox.com/s/hs0ztzrdy4unn75/mumble-server-1.2.4-1.el6.i686.rpm
    https://www.dropbox.com/s/nc0odvada3u6hc4/mumble-server-1.2.4-1.el6.src.rpm

You need the epel and the ZeroC repository for Ice 3.5. (ZeroC™ is the
Home of Ice™)

For x64

    rpm -ivh http://ftp-stud.hs-esslingen.de/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
    wget --directory-prefix=/etc/yum.repos.d/ http://zeroc.com/download/Ice/3.5/el6/zeroc-ice-el6.repo
    yum install avahi-compat-libdns_sd qt qt-sqlite ice-libs protobuf
    rpm -ivh https://www.dropbox.com/s/wla29wnabsz53nq/mumble-server-1.2.4-1.el6.x86_64.rpm

For x86

    rpm -ivh http://ftp-stud.hs-esslingen.de/pub/epel/6/i386/epel-release-6-8.noarch.rpm
    wget --directory-prefix=/etc/yum.repos.d/ http://zeroc.com/download/Ice/3.5/el6/zeroc-ice-el6.repo
    yum install avahi-compat-libdns_sd qt qt-sqlite ice-libs protobuf
    rpm -ivh https://www.dropbox.com/s/hs0ztzrdy4unn75/mumble-server-1.2.4-1.el6.i686.rpm

## Set the password of murmur

    /usr/sbin/murmurd -ini /etc/mumble-server/mumble-server.ini -supw yourpassword

## The service

    service mumble-server start
    chkconfig mumble-server on

Don't forget the iptables settings\!

# Murmur 1.2.3

If for some reason you want to install the older 1.2.3 version of Murmur
use the following instructions. Do not try to install both packages at
the same time.

## The binary package and the source

    https://www.dropbox.com/s/8tx3t75lscnycf2/murmur-1.2.3-1.el6.i686.rpm
    https://www.dropbox.com/s/cp9amj5f9glae11/murmur-1.2.3-1.el6.x86_64.rpm
    https://www.dropbox.com/s/9ywof04f320kowm/murmur-1.2.3-1.el6.src.rpm

You need the epel and the ZeroC repository for Ice 3.4. (ZeroC™ is the
Home of Ice™)

For x86

    rpm -ivh http://ftp-stud.hs-esslingen.de/pub/epel/6/i386/epel-release-6-8.noarch.rpm
    wget --directory-prefix=/etc/yum.repos.d/ http://zeroc.com/download/Ice/3.4/rhel6/zeroc-ice-rhel6.repo
    yum install avahi-compat-libdns_sd qt qt-sqlite ice-libs protobuf
    rpm -ivh https://www.dropbox.com/s/8tx3t75lscnycf2/murmur-1.2.3-1.el6.i686.rpm

For x64

    rpm -ivh http://ftp-stud.hs-esslingen.de/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
    wget --directory-prefix=/etc/yum.repos.d/ http://zeroc.com/download/Ice/3.4/rhel6/zeroc-ice-rhel6.repo
    yum install avahi-compat-libdns_sd qt qt-sqlite ice-libs protobuf
    rpm -ivh https://www.dropbox.com/s/cp9amj5f9glae11/murmur-1.2.3-1.el6.x86_64.rpm

## Set the password of murmur

    /usr/sbin/murmurd -ini /etc/mumble-server.ini -supw yourpassword

## The service

    service murmur start
    chkconfig murmur on

Don't forget the iptables settings\!

[Category:Documentation
English](Category:Documentation_English "wikilink")