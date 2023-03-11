Mumble (and Murmur) are open source, and therefore completely free of
charge. However, to fully experience the quality of Mumble, a quality
server with good network connection is needed. Home-based DSL or Cable
servers are far from optimal, and do not scale to much more than 5-6
users.

We are therefore interested in facilitating commercial hosting of
Murmur, to enable users who lack either the server hardware and network
connection or the skill to compile and maintain Murmur to use Mumble.

This page is specifically targeted at commercial hosting providers. This
is where we'll present a short summary of Murmur's expected resource
requirements, and where you can edit it to provide us with information
on what you need to make your job easier.

If you aren't looking to start a host yourself, and are just looking for
a commercial host, the Mumble Wiki maintains a non-exhaustive [list of
hosts](Hosters "wikilink").

# Murmur technical requirements

Murmur runs on any operating system where Qt can compile. At the moment,
that is "most" UNIXes, Windows and MacOSX. Our internal testserver runs
on Linux, and a binary version for Windows is included in the mumble
installer.

Based on data from our testserver, murmur will use about 40 MB of
virtual memory, of which about 4 MB are resident in physical memory.

Since only minimal processing, as required for cryptography and
"visibility checks" between users, is done serverside, we were not able
to push even 1% of actual CPU usage with 4 users on a Xeon 3.4Ghz. We do
see quite a few context switches though, so quality network cards and
infrastructure capable of handling high packet load are recommended on
servers hosting a big number of clients.

Mumble uses CELT, and using the highest quality and lowest latency, the
peak bandwidth is 134kbit/s per speaker per listener (with IP and UDP
overhead). However, this is the *max* bandwidth, and the recommended
bandwidth (that has a very unnoticeable quality reduction for normal
speech) is 63kbit/s. In other words, a server with 10 users and 1 user
speaking will need to replicate the datastream 9 times, for a total of
63\*9=567kbit/s outgoing bandwidth. If all 10 users speak at once, each
stream has to be replicated 9 times, for a total of 63kbit/s\*9\*10=5.67
Mbit/s. Note that these are *absolute* worst-case scenarios, and the
average bandwidth use is around 20-30 kbit/s during speech, multiplied
by the number of listeners; it is only possibly in a real world scenario
for at most two people to be talking at the same time and still
understand what they are saying.

As one data point you can take a look at silencerru's post about the
resource usage for a \~800 user server [in the
forum](http://forums.mumble.info/viewtopic.php?f=2&t=597).

# Licensing

Murmur and Mumble is BSD and GPL licensed, which means that much like
the Linux kernel, you are free to use it in commercial hosting without
royalties. You are selling a service, not a program.

If you want to repackage and rebrand the client without also
distributing its source code, the Mumble source code is BSD licensed,
which allows you to do this. You will also need commercial licenses for
the packages Mumble uses, namely Qt and Ice, as well as a patent license
for [OCB](http://www.cs.ucdavis.edu/~rogaway/ocb/). The owners of these
packages and patents have all kindly granted Mumble a license, but that
only covers open source distribution. Note that if you just use our
binaries from sourceforge, you don't need to worry about any of this.

# Requirements for Murmur for adoption by commercial providers

I'll note down what I can imagine commercial hosting providers would
like to see implemented in Murmur before they start offering it as a
service. If you are a commercial provider, please comment in the
discussion section (even if you agree, it helps to know we're on the
right track), or add new sections.

## Ability to limit number of users

Set the "[users](Murmur.ini#users "wikilink")" parameter in murmur.ini

## Ability to limit audio quality

Set the "[bandwidth](Murmur.ini#bandwidth "wikilink")" parameter in
murmur.ini, which limits the per-user incoming bandwidth. Multiply this
by the number of users in a channel to find the used outgoing bandwidth
per active speaker.

## No frills ACLs and Groups

The multi-channel [ACL and Groups](ACL_and_Groups "wikilink") system in
Mumble enables easy setup of linked channels that can match most any
scenario. On the downside, it's also easy to mess up, especially if
you're an inexperienced user. While this might ultimately be up to the
hosting providers, we should probably provide a small example of how to
use a webpage to "configure" a very basic access system, and give no
users the actual "Write" bit, even the admin. This would allow those
users who feel they are competent enough to log in with superuser and
foul things up as much as they want, and will also allow for simple
management for less sophisticated users.

If anyone wishes to do so, this can be done through the
[Ice](Ice "wikilink") RPC interface of Murmur.

## SQL-Server

The default and recommended SQL engine for Murmur is SQLite, since it is
faster than all the other alternatives and requires less resources. From
0.9.5 onwards, Murmur also supports MySQL.

## Multiserver support

From version 1.1.0 onwards, Murmur fully supports multiple independent
virtual servers per process.

Additional servers can be added either with the [Ice](Ice "wikilink") or
[DBus](DBus "wikilink") RPC interface. You can use the newServer() call
which returns a server id, then use start(id) or stop(id) to stop the
server. Before you start it, you probably want to configure it, which is
done through setConf(serverid, key, value).

Known configuration keys are:

  - [host](Murmur.ini#host "wikilink") - IP bound to
  - [password](Murmur.ini#password "wikilink") - server PW
  - [port](Murmur.ini#port "wikilink") - server port
  - [timeout](Murmur.ini#timeout "wikilink") - client inactivity timeout
  - [bandwidth](Murmur.ini#bandwidth "wikilink") - bandwidth restriction
  - [users](Murmur.ini#users "wikilink") - max \# of users
  - [welcometext](Murmur.ini#welcometext "wikilink") - the blurb sent by
    the server on connect
  - [registername](Murmur.ini#registername "wikilink"),
    [registerpassword](Murmur.ini#registerpassword "wikilink"),
    [registerhostname](Murmur.ini#registerhostname "wikilink"),
    [registerurl](Murmur.ini#registerurl "wikilink") - The data for
    registration in the public server list
  - [certificate](Murmur.ini#certificate "wikilink") - x509 certificate
    in PEM form
  - [sslkey](Murmur.ini#sslkey "wikilink") - x509 private key in PEM
    form

If a config key is not present, the default is to take the value from
the .ini file (except port, which defaults to inifile+server_id-1)

## RPC

Murmur supports [Ice](Ice "wikilink") RPC calls, which allow querying
all information of the server in real time, and also allow management.
Hence, it's fairly easy to write scripts to query and display server
status, and also to create web frontends for server administration.

[Here](3rd_Party_Applications "wikilink") is a list of the
web-interfaces available.

[Ice](Ice "wikilink") has all but replaced [DBus](DBus "wikilink"),
given its multi-platform features and usability.

[Category:Documentation
English](Category:Documentation_English "wikilink")