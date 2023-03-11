Murmur's configuration file (**murmur.ini**) consists of single line
configuration settings, in the format of `key=value`. Empty lines and
anything after **\#** to the end of a line are ignored.

Some settings are process-wide (`database`, etc) while others are used
as defaults on a per-server basis. `registername` for example will be
used as the default "title" for all virtual servers, unless it's
overridden via RPC.

A unique example is `port` - the first server will attempt to bind to
this port, with each subsequent server incrementing the port by one for
its own port.

## Database Configuration

There are other options not listed below, namely: `dbUsername`,
`dbPassword`, `dbHost`, `dbPrefix`, `dbOpts`, and `dbPort`. These
options have different meanings depending on the [database engine
used](http://qt-project.org/doc/qt-4.8/sql-driver.html), and explaining
them is outside the scope of this document.

### database

If `dbDriver` is **`QSQLITE`** (the default), this setting will specify
the path to the database file. Other database drivers will use this
setting for their own purposes -with **`QMYSQL`** it will set the
database name.

`database=/var/run/murmur.sqlite`

### dbDriver

The database backend that Murmur will use for storage of persistent
data. The default is **`QSQLITE`**, which is the
[SQLite](http://en.wikipedia.org/wiki/SQLite) database driver. Murmur
does its best to speak sensible, standards-compliant SQL - so you may
have luck with [any of the other database drivers supported by
QSql](http://qt-project.org/doc/qt-4.8/sql-driver.html) - but note that
SQLite is the most tested configuration followed very distantly behind
by MySQL.

## RPC Configuration

### dbus

Murmur has deprecated support for control via D-Bus. It's poorly
documented, new features aren't added to it, and it's possible it could
be removed at some point in the future. To activate it simply uncomment
the following line:

`dbus=session`

### dbusservice

This setting allows you to configure a distinct service name for this
Murmur process on the D-Bus. It's really only useful if you have
multiple Murmur processes that share the same D-Bus.

`dbusservice=net.sourceforge.mumble.murmur`

### ice

Murmur supports extensive RPC via ZeroC [Ice](Ice "wikilink"), and the
`ice` setting specifies the "endpoint". More information on [configuring
Ice Endpoints can be found in the ZeroC Ice
documentation](http://www.zeroc.com/doc/Ice-3.4.1-IceTouch/manual/ProxyEndpointRef.51.2.html).

Note that all virtual servers share an Ice service, and without secrets
configured anyone with access to the Ice port has full administrative
access to every virtual server on the Murmur process. It's not
recommended it's exposed to the world for that reason, it's recommended
you protect the service via a firewall and configure Ice Secrets below.

The default will cause Ice to listen on TCP port 6502 on the loopback
interface:

`ice="tcp -h 127.0.0.1 -p 6502"`

#### icesecretread and icesecretwrite <span id="icesecret"></span><span id="icesecretread"></span><span id="icesecretwrite"></span>

The default Ice configuration listens on a local TCP socket, which means
that anyone with access to the local machine can access it. Murmur
supports setting plaintext "secrets" on the service, so that any script
or program accessing the service must also possess the secret.

Access is split into two levels: "read" (look only) and "write"
(modify). "write" access implies "read" access. We'll work on tracking
down examples of setting "secret" in the context for your Ice scripts at
some point.

To configure secrets:

`icesecretread=letmelook`
`icesecretwrite=letmechangestuff`

Note that if either of these entries is uncommented and empty, access
will be denied. To disable secrets, comment these settings out.

#### Ice Configuration Section

The Ice configuration section begins with the line **\[Ice\]** and must
be the last configuration section in murmur.ini. This section allows you
to set additional Ice options.

If you are using Ice through a NAT device, you will need to setup
[Published
Endpoint](http://doc.zeroc.com/display/Ice/Object+Adapter+Endpoints#ObjectAdapterEndpoints-published)
for Ice. More information on [configuring Ice for NAT traversal can be
found in the ZeroC Ice
documentation](http://doc.zeroc.com/pages/viewpage.action?pageId=3900838).
You can set a published endpoint by using the following line in the Ice
configuration section:

`Murmur.PublishedEndpoints=tcp -h 123.4.1.1 -p 7000`

## Security Stuff

### autobanAttempts, autobanTimeframe and autobanTime <span id="autobanattempts"></span><span id="autobantimeframe"></span><span id="autobantime"></span>

In order to prevent misconfigured, impolite or malicious clients from
affecting the low-latency of other users, Murmur has a rudimentary
global-ban system. It's configured using the `autobanAttempts`,
`autobanTimeframe` and `autobanTime` settings.

If a client attempts `autobanAttempts` connections in `autobanTimeframe`
seconds, they will be banned for `autobanTime` seconds. This is a global
ban, from all virtual servers on the Murmur process. It will not show up
in any of the ban-lists on the server, and they can't be removed without
restarting the Murmur process - just let them expire. A single, properly
functioning client should not trip these bans.

To disable, set `autobanAttempts` or `autobanTimeframe` to 0. Commenting
these settings out will cause Murmur to use the defaults:

`#autobanAttempts = 10`
`#autobanTimeframe = 120`
`#autobanTime = 300`
`#autobanSuccessfulConnections=true`

To avoid autobanning successful connection attempts from the same IP
address, set `autobanSuccessfulConnections=false`. Note though that this
is only available since 1.4.0

### serverpassword

This setting configures the default password for unregistered users -
registered users will not be prompted for this password (they will
either have their own, or be authenticated by their certificate). This
setting is usually configured on a per-virtual-server basis, via RPC.

`password=letmein`

### uname

On Unix-like OSes, you can start Murmur as root and have it drop
privileges to another account such as "mumble" or "murmur". The username
must already exist on your system, and have write access to the Murmur
database, logfiles, etc.

This option is ignored if Murmur is not started as root.

`uname=murmur`

### obfuscate

By default, in log files and in the user status window for privileged
users, Mumble will show IP addresses - in some situations you may find
this unwanted behavior. If `obfuscate` is set to **true**, Murmur will
randomize the IP addresses of connecting users.

Note that this setting currently only applies to IPv4 addresses, and
that it is currently just a simple XOR with a random value - it is
probably trivially broken if a user knows their IP address and can
compare it with the obfuscated one assigned to them. As tested on 1.2.3
the obfuscate function only affects the log file and DOES NOT effect the
*user information* section in the client window.

`obfuscate=true`

### sendversion

In the UDP ping response, Murmur will include its version as well.
Adjusting this setting to **false** disables that behavior.

`sendversion=false`

### legacyPasswordHash

This sets password hash storage to legacy mode (1.2.4 and before). Note
that setting this to true is insecure and should not be used unless
absolutely necessary.

`legacyPasswordHash=false`

### kdfIterations

Set a specific number of iterations for PBKDF2 password storage in the
Mumble database. By default a strong amount of PBKDF2 iterations are
chosen automatically. If \>0 this setting overrides the automatic
benchmark and forces a specific number of iterations.

Note that you should only change this value if you know what you are
doing.

`kdfIterations=-1`

### allowping

Setting this to **false** disables responses to the UDP ping sweep that
clients will make when the connection dialog is open. Note that on
publicly listed servers, and on some configured clients, this will
prevent the server from showing up in the list.

`allowping=false`

## Process Administrivia

### logfile

By default, murmur will log to murmur.log in the current working
directory. You can change this file by specifying it in the `logfile`
setting, including a full path if necessary.

You can set this setting blank, and Murmur will log only via message
boxes (Win32 systems) and to the console (non-Win32 systems).

`logfile=murmur.log`

### logdays

Murmur also stores logs in the database, which are accessible via RPC.
The default is 31 days of months, but you can set this setting to 0 to
keep logs forever, or -1 to disable logging to the database.

`logdays=31`

### pidfile

If this setting is set to a filename, Murmur will write its PID to this
file when it forks. This enables service checkers to ensure the process
is still running, and restart it if it's not. The file will be removed
if Murmur shuts down cleanly.

Note that Murmur on Windows systems will not write a PID file.

`pidfile=murmur.pid`

### welcometext

This setting configures a "message of the day" which is displayed to all
users who connect to the server. You can use a subset of HTML and CSS in
the welcometext, see [here](Usage_of_HTML_and_CSS_in_Mumble "wikilink").
Encase in quotes to spread it out on multiple lines.

`welcometext="`
`Welcome to this server running `<b>`Murmur`</b>`.`
`Enjoy your stay!`
`"`

### welcometextfile

Allows to read the welcometext from an external file which might be
useful if you want to specify a rather lengthy text. If a value for
`welcometext` is set, the `welcometextfile` will not be read. This
option was introduced with 1.4.0.

`welcometextfile=welcome_text.txt`

## Connectivity

### port

This setting configures the TCP and UDP ports that Murmur will listen on
- the default is 64738. If the Murmur process is running multiple
virtual servers, then this port will be incremented for each virtual
server by default. You can specify, via RPC, a specific port for each
virtual server if you wish to override the defaults.

`port=64738`

### host

The `host` setting configures the default interface which each virtual
server will listen on. You can override this setting for each virtual
server if you want them on different IPs - the default is "all
interfaces", but note that on multi-homed servers this will sometimes
break UDP so specifying an interface is sometimes useful.

If you want to listen on multiple distinct interfaces, specify them in a
space-seperated list.

`# Listen on made up IPv4 address 333.333.333.333`
`# and on made up IPv6 address HEHE::HEHE`
`host=333.333.333.333 HEHE::HEHE`

`# Listen on all interfaces`
`host=0.0.0.0`
`# or:`
`host=`

### sslCert and sslKey <span id="sslcert"></span><span id="sslkey"></span>

If you have your own certificate and wish to use it instead of the
certificate that Murmur automatically generates, you can enter the
filenames here. If your key and cert are seperate files, point the
respective settings at each file. If your key and cert are in one file,
set it in `sslKey`

`sslCert=cert.pem`
`sslKey=key.pem`

**These settings are simply called "`certificate`" and "`key`" when
being set via RPC.**

### sslPassPhrase

If the keyfile specified above is encrypted with a passphrase, you can
enter it in this setting. It must be plaintext, so you may wish to
adjust the permissions on your murmur.ini file accordingly.

`sslpassphrase=supersecretkey`

### sslCA

If your certificate is signed by an authority that uses a sub-signed or
"intermediate" certificate, you probably need to bundle it with your
certificate in order to get Murmur to accept it. You can either
concatenate the two certificates into one file, or you can put it in a
file by itself and put the path to that file in `sslCA`.

`sslCA=class1.intermediate.pem`

### sslCiphers

The sslCiphers option chooses the cipher suites to make available for
use in SSL/TLS. This option is server-wide, and cannot be set on a
per-virtual-server basis.

This option is specified using OpenSSL cipher list notation (see
<https://www.openssl.org/docs/apps/ciphers.html#CIPHER-LIST-FORMAT>).

It is recommended that you try your cipher string using 'openssl ciphers
<string>' before setting it here, to get a feel for which cipher suites
you will get.

After setting this option, it is recommend that you inspect your Murmur
log to ensure that Murmur is using the cipher suites that you expected
it to.

Note: Changing this option may impact the backwards compatibility of
your Murmur server, and can remove the ability for older Mumble clients
to be able to connect to it.

`sslCiphers=EECDH+AESGCM:EDH+aRSA+AESGCM:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:AES256-SHA:AES128-SHA`

### sslDHParams

The sslDHParams option allows you to specify a PEM-encoded file with
Diffie-Hellman parameters, which will be used as the default
Diffie-Hellman parameters for all virtual servers. If a file is not
specified, each Murmur virtual server will auto-generate its own unique
set of 2048-bit Diffie-Hellman parameters on first launch.

`sslDHParams=dh.pem`

### bonjour

[Bonjour](http://developer.apple.com/networking/bonjour/index.html) is
an auto-discovery service that allows other people on the same LAN as
you to find the server without needing the address to it. It only really
makes sense to enable this on a LAN-based server. The default is false.

`bonjour=true`

### bandwidth

You can configure a per-user upper bandwidth limit, in bits per second.
This allows you to clamp your users down to a sensible setting if you
are limited in bandwidth. This does not set a minimum bandwidth - the
Murmur client will check its own bandwidth setting and the server's
bandwidth settings, and choose the lower of the two.

The default is 72000, which is 72Kbps. Setting this over about 130000
doesn't really do anything. Note that this is per user.

`bandwidth=72000`

### timeout

Murmur and Mumble are usually pretty good about cleaning up hung
clients, but occasionally one will get stuck on the server. The
`timeout` setting will cause a periodic check of all clients who haven't
communicated with the server in this many seconds - causing zombie
clients to be disconnected.

Note that this has no effect on idle clients or people who are AFK. It
will only affect people who are already disconnected, and just haven't
told the server.

`timeout=30`

## Users and Channels

### users

The `users` setting configures a limit on the maximum number of users
per virtual server.

`users=100`

### usersperchannel

Where `users` sets a blanket limit on the number of clients per virtual
server, `usersperchannel` sets a limit on the number per channel. The
default is 0, for no limit.

`usersperchannel=10`

### channelname and username <span id="channelname"></span><span id="username"></span>

These two settings allow you to configure a regular expression ([Qt
regular
expressions](http://doc.qt.io/qt-4.8/qregexp.html#characters-and-abbreviations-for-sets-of-characters))
of acceptable names for users and channels. This allows you very
powerful control over names of objects on your servers - things like
maximum and minimum username lengths, etc.

Note that you must double-escape things like backslashes in the .ini,
and that the .ini parser does weird things with things like curly braces
unless you enclose the regular expression in quotes:

`channelname=[ \\-=\\w\\#\`\[\\]`\\{\\}\`\(\\)`\\@\\|]+`
`username=[-=\\w\`\[\\]`\\{\\}\`\(\\)`\\@\\|\\.]+`
`username="[A-Z]{2,9}" # Allow only capital ASCII letters, between two and nine characters (inclusively).`

### channelnestinglimit

This setting allows you to specify how many levels of children the root
channel can have, useful for avoiding trigger errors when using
non-SQLite database backends.

The default value is 10.

### certrequired

Mumble supports strong authentication via client certificates, and
providing you have an RPC mechanism in place to set them, weak
authentication via passwords. By default, users without certificates are
still allowed on a server if they know the `serverpassword`, or if there
isn't one set - however they cannot self-register, even if the server
allows it (as there's no certificate to register).

Setting `certrequired` to true ensures that only clients who possess a
certificate of some kind are allowed on the server. This is mostly safe,
as recent Mumble versions will automatically generate a certificate if
the certificate wizard is closed prematurely.

`certrequired=false`

### defaultchannel

If a user has no stored channel (they've never been connected to the
server before, or `rememberchannel` is set to **false**) and the client
hasn't been given a URL that includes a channel path, the default
behavior is that they will end up in the root channel.

You can set this setting to a channel ID, and the user will
automatically be moved into that channel instead. Note that this is the
numeric ID of the channel, which can be a little tricky to get (you'll
either need to use an RPC mechanism, watch the console of a debug
client, or root around through the Murmur Database to get it).

`# AFK channel`
`defaultchannel=4`

### rememberchannel

When a user connects to a server they've already been on, by default the
server will remember the last channel they were in and move them to it
automatically. Toggling this setting to **false** will disable that
feature.

`rememberchannel=false`

### rememberchannelduration

How many seconds should the server remember the last channel of a user.
Set to **0** (default) to remember forever. This option has no effect if
`rememberchannel` is set to false.

This option has been introduced with 1.4.0.

`rememberchannelduration=0`

### textmessagelength

The `textmessagelength` setting configures the maximum length of each
message sent via the server in bytes. Set to 0 for no limit. Note that
on older versions of Murmur, if users want to paste images to each other
inline, a fairly sizable limit is required. On newer versions, the
imagemessagelength setting controls the size of these messages.

`textmessagelength=5000`

### imagemessagelength

Like `textmessagelength`, this setting configures the maximum length in
bytes of messages passing through the server - but it only applies to
messages that include inline image blobs. Set to 0 for no limit.

`imagemessagelength=131072`

**WARNING**: Raising this much above the default is a really bad idea at
the moment, due to the way QT parses inline image blobs. Clients up to
at least 1.2.3 will also disregard this setting, and enforce a limit of
64kB regardless when sending messages, for this very reason. Sending 3MB
high-res images across a VOIP client might seem like a good idea, but
it's really not, and you open your server up to a whole mess of abuse
with high values, so tread carefully with this setting.

### allowhtml

Set to **true** to allow some HTML to be used in text messages between
clients, user comments and channel descriptions.

`allowhtml=true`

### opusthreshold

`opusthreshold` is a number between 0 and 100, which specifies a
percentage of users on the server supporting the Opus codec before the
entire server mandates Opus is used. *It defaults to 100*, so that any
non-Opus supporting client connecting will cause the entire server to
fall back to CELT. This is a safe default, to avoid users not being able
to hear other users.

`opusthreshold=100`

Setting this to 50 will mean that if 50% or more users on the server
support Opus, the server will switch to Opus and any non-supporting
users will be unable to hear conversations.

**Note**: Opus is only implemented on 1.2.4 and above, and so this
setting will have no effect on servers earlier than 1.2.4.

### listenersperchannel

The amount of allowed listener proxies in a single channel. It defaults
to -1 meaning that there is no limit. Set to 0 to disable Channel
Listeners altogether. This option has been introduced with 1.4.0.

`listenersperchannel=5`

### listenersperuser

The amount of listener proxies a single user may have. It defaults to -1
meaning that there is no limit. Set to 0 to disable Channel Listeners
altogether. This option has been introduced with 1.4.0.

`listenersperuser=2`

### messagelimit and messageburst

These two settings allow to configure the per-user rate limiter for some
command messages sent from the client to the server. The `messageburst`
setting specifies an amount of messages which are allowed in short
bursts. The `messagelimit` setting specifies the number of messages per
second allowed over a longer period. If a user hits the rate limit,
their packages are then ignored for some time. Both of these settings
have a minimum of `1` as setting either to `0` could render the server
unusable.

## Server Registration

Mumble supports a public server registry, which your Murmur can
automatically configure itself to register with if you choose. The
server must be public (no `serverpassword`), it must be accessible
worldwide, and it must have a Murmur-generated certificate or a 3rd
party strong certificate with the TLS bit enabled.

`serverpassword` must be empty, and all the other `register*` settings
must be filled in. `registerHostname` **must** be valid and resolve.

### registerName

**This setting is also used as the "Root" channel name, so you probably
want to set it even if you don't want to register your server.**

The registerName setting also specifies the "name" of your server in the
public server list. The list is no longer sorted alphabetically, so
please, in the interests of being user-friendly, don't set it to
something silly trying to arbitrarily "rank" your server.

`registerName=Super Awesome Mumble Server`

### registerPassword

`registerPassword` is a simple, plain-text secret between your server
and the registration server. Its sole purpose is to prevent other
servers from impersonating your server in the public server list.

Set this setting empty to disable registration with the public server
list.

`registerPassword=secret`

### registerUrl

This points to a URL to the website for the server. Put your group's
website, your sponsor's website, or the website where users can
self-administrate with the server. They can right-click on your server
in the registration list to access this URL.

`registerUrl=http://mumble.sourceforge.net/`

### registerHostname

This setting is the DNS hostname where your server can be reached. It
only needs to be set if you want your server to be addressed in the
server list by its hostname instead of by IP, but if it's set it must
resolve on the internet or registration will fail.

`registerHostname=mumble.some.host`

### registerLocation

This sets the location (country) for the server, so it will be shown in
this country (and the corresponding continent) on the public server
list.
It is set by using the two-letter TLD style country code (ISO 3166-1
alpha-2 country code), for example *US* for the United States of America
(mostly the same as the country domain, in this case *.us*).
A list of the country codes can be found on wikipedia:
[ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Example:
registerLocation=US

## Miscellany

### suggestVersion

You can set a recommended minimum version for your server, and clients
will be notified in their log when they connect if their client does not
meet the minimum requirements. `suggestVersion` expects the version in
the format X.X.X.

`suggestVersion=1.2.5`

Note that the `suggest*` options appeared after 1.2.3 and will have no
effect on client versions 1.2.3 and earlier.

### suggestPositional

Setting this to "true" will alert any user who does not have positional
audio enabled that the server administrators recommend enabling it.
Setting it to "false" will have the opposite effect - if you do not care
whether the user enables positional audio or not, set it to blank. The
message will appear in the log window upon connection, but only if the
user's settings do not match what the server requests.

`suggestPositional=true`

Note that the `suggest*` options appeared after 1.2.3 and will have no
effect on client versions 1.2.3 and earlier.

### suggestPushToTalk

Setting this to "true" will alert any user who does not have
Push-To-Talk enabled that the server administrators recommend enabling
it. Setting it to "false" will have the opposite effect - if you do not
care whether the user enables PTT or not, set it to blank. The message
will appear in the log window upon connection, but only if the user's
settings do not match what the server requests.

`suggestPushToTalk=true`

Note that the `suggest*` options appeared after 1.2.3 and will have no
effect on client versions 1.2.3 and earlier.

## Logging & Debugging

Log related options that are not listed here are
[logfile](#logfile "wikilink") and [logdays](#logdays "wikilink").

### loggroupchanges

Enables logging of group changes. This means that every time a group in
a channel changes, the server will log all groups and their members from
before the change and after the change. Deault is `false`. This option
was introduced with Murmur 1.4.0.

` loggroupchanges=true`

### logaclchanges

Enables logging of ACL changes. This means that every time the ACL in a
channel changes, the server will log all ACLs from before the change and
after the change. Default is `false`. This option was introduced with
Murmur 1.4.0.

` logaclchanges=true`

[Category:Documentation_English](Category:Documentation_English "wikilink")