{{Notice
|message=Some of the software mentioned here is outdated and that is not always labeled, so take a closer look at the software and check for the last update date, features and compatibility.
}}

'''If you created or found an application you think should be included or find out that some software does not work anymore, edit this page, open a discussion or report an issue on GitHub instead: https://github.com/mumble-voip/mumble-www/issues.'''

= Clients =

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable" width="100%"
! Name
! Platform
! Programming language
! Comment
! License
! Weblink

|-bgcolor="#f8f8ff"
| '''Mumla'''
| Android
| Java
| Fork (aka continuation) of Plumble.
|  [GPLv3](https://gitlab.com/quite/mumla/-/raw/master/LICENSE)
|  [GitLab](https://gitlab.com/quite/mumla)

|-bgcolor="#f8f8ff"
| '''mumble-web'''
| Web
| HTML5 and JavaScript
| Quite a few features are still missing, most noticeably voice activity detection and all administrative functionality.
|  [ISC](https://opensource.org/licenses/ISC)
|  [GitHub](https://github.com/Johni0702/mumble-web)

|-bgcolor="#f8f8ff"
| '''talKKonnect'''
| Linux
| Go
| talKKonnect is a Linux CLI Headless Self Contained Mumble Client For Raspberry Pi with LCD, Channel Control and Granular XML Config. Using GPIOs you can interface with RF radios or other network radio technologies.  
|  [MPL](https://opensource.org/licenses/MPL-2.0)
|  [talkkonnect](https://talkkonnect.com/)

|-bgcolor="#f8f8ff"
| '''Wahay'''
| Linux
| Go
| Wahay is an easy-to-use, secure and decentralized conference call application that provides private and autonomous digital communications to everyone. It combines Grumble, Mumble and Tor Onion services.
|  [GPLv3](https://github.com/digitalautonomy/wahay/blob/master/LICENSE)
|  [Wahay](https://www.wahay.org)

|-bgcolor="#f8f8ff"
| '''Pymumble'''
| Linux
| Python
| A mumble client written in python. 
Offers some special features (like a Musicbot (that supports stereo transmission)), but also lacks some features.
See the Github repo for details.
|  [GPLv3](https://github.com/azlux/pymumble/blob/pymumble_py3/LICENSE)
|  [GitHub](https://github.com/azlux/pymumble)

|-bgcolor="#f8f8ff"
| '''barnard'''
| Linux
| Go
| barnard is a terminal-based client with a curses-like UI. Built on the Gumble library.
Note: barnard was last updated 2018.
|  [GPLv2](https://raw.githubusercontent.com/layeh/barnard/master/LICENSE)
|  [GitHub](https://github.com/layeh/barnard)

|-bgcolor="#f8f8ff"
| '''WiMic'''
| Android
| Java / NDK
| Fork of Plumble. (WiMic has many features added like echo canceller, performance enabled for 8 Khz and 8k bitrates at 10 ms latency, performed vox gain control, battery optimization and new native NEON preprocessing audio libraries, mainly focused on OPUS codec performance).

WiMic Android client can work with WiMic Server/Client too.
|  [GPLv3](https://github.com/hiro2233/wimic_android/blob/master/LICENSE)
|  [Github](https://github.com/hiro2233/wimic_android)

|}

= Servers =
Note: These servers might not have all recent features and functionality.

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! Status
! Source-Language
! License
! Comment
! Weblink

|-bgcolor="#f8f8ff"
| Grumble
| Experimental
|  [Go](http://golang.org)
| # BSD3
| Alternative Mumble server written in Go
|  [github.com](https://github.com/mumble-voip/grumble Project page and source on)

|-bgcolor="#f8f8ff"
| uMurmur
| Stable (outdated)
| C
| # BSD3
| uMurmur is a minimalistic Mumble server primarily targeted to run on routers with an open OS like OpenWRT. The server part of Mumble is called Murmur, hence the name uMurmur.
Note: uMurmur was last updated 2017, so it is outdated.
|  [github.com](https://github.com/fatbob313/umurmur Project page and sources on)

|-bgcolor="#f8f8ff"
| WiMic Server/Client (with GUI Manager)
| Stable
| C/C++
|  [GPLv3](https://github.com/hiro2233/wimic/blob/master/LICENSE)
| Hybrid server, based on uMurmur and Mumlib. WiMic Server/Client can run on GNU/Linux and Windows (MSYS2) platforms, focused to work with WiMic Android performance.
|  [Github](https://github.com/hiro2233/wimic)

|}

= Libraries =

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable" width="100%"
! Name
! Technology
! Comment
! License
! Weblink

|-bgcolor="#f8f8ff"
| '''gumble'''
| Go
| -
| MPL 2.0
| [https://github.com/layeh/gumble/]

|-bgcolor="#f8f8ff"
| '''lua-mumble'''
| Lua (Linux)
| -
| MIT
| [https://github.com/bkacjios/lua-mumble]

|-bgcolor="#f8f8ff"
| '''MumbleKit'''
| Objective-C
| -
| BSD3
| [https://github.com/mumble-voip/mumblekit]

|-bgcolor="#f8f8ff"
| '''MumbleSharp'''
| C#
| -
| MIT
| [https://github.com/martindevans/MumbleSharp]

|-bgcolor="#f8f8ff"
| '''node-mumble'''
| JavaScript (Node.js)
| -
| MIT
| [https://github.com/Rantanen/node-mumble]

|-bgcolor="#f8f8ff"
| '''pymumble'''
| Python
| -
| GNU
| [https://github.com/azlux/pymumble]
|

|-bgcolor="#f8f8ff"
| '''Mumble-Unity'''
| C# (Unity3D)
| -
| MIT
| [https://github.com/BananaHemic/Mumble-Unity]
|

|-bgcolor="#f8f8ff"
| '''NoodleJS'''
| JavaScript (Node.js)
| -
| MIT
| [https://github.com/Gielert/NoodleJS]
|

|-bgcolor="#f8f8ff"
| '''gomble'''
| Go
| youtube, UDP, for music bots
| MIT
| [https://github.com/CodingVoid/gomble/]

|-bgcolor="#f8f8ff"
| '''Humla'''
| Java (Android)
| Used for [[Mumla]]. Fork of Jumble.
| GPLv3
| [https://gitlab.com/quite/humla]

|-bgcolor="#f8f8ff"
| '''mumlib'''
| C++, boost::asio
| Note: Outdated (last update: 2018).
Provides basic functionality, no ACL
| LGPLv3
| [https://github.com/slomkowski/mumlib]

|}

= Web-Interfaces =

There are several browser based interfaces which can be used to administrate the Murmur server. If you need something very basic or want to create your own interface you should take a look at Murmur's  [[[Ice]](https://github.com/mumble-voip/mumble/tree/master/scripts/server script folder] which contains some basic web-interface examples which use) or [[DBus]] (we recommend using Ice, as DBus is kept for backwards compatibility, and is not being extended for quite some time).
Additionally the following table contains a collection of more elaborate Web-Interfaces:

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! Technology
! License
! Current Version
! Last Release
! [[DBus]]
! [[Ice]]
! 1.2.x
! Comment
! Weblink

|-bgcolor="#f8f8ff"
| [[Mumble-Django]]
|  [Python](http://www.python.org) +  [Django](http://www.djangoproject.com)
| # GPLv3
| V2.7
| 2012-03-31
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
| Channel viewer (internal and support for others), admin panel, IPv6, [[Channel Viewer Protocol]], Munin plugin, CLI, supports multiple servers and instances, user registration, textures, gravatar, translated to English, German, French, Italian and Japanese
| [https://mumble-django.readthedocs.io]

|-bgcolor="#f8f8ff"
| [MumPI](Mumble PHP Interface.md)
|  [PHP](http://php.net/)
| # LGPLv3
| V2.2.6
| 2015-12-09
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
| Admin and User functionality; multiserver (start, stop, add, remove, edit virtual servers), registration & online user management, interface admin, admin-group and permission system, serverviewer
| [http://github.com/Kissaki/MumPI/wiki]

|-bgcolor="#f8f8ff"
| PHP Mumble Admin
|  [PHP](http://php.net/)
| # GPLv3
| V0.4.3
| 2013-02-07
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
| Complete administration control panel for Murmur designed for multiple virtual server.  [Website](http://sourceforge.net/projects/phpmumbleadmin/)
| [http://sourceforge.net/projects/phpmumbleadmin/]

|-bgcolor="#f8f8ff"
| Mumbled Webinterface
|  [PHP](http://php.net/)
| # GPLv3
| V0.2
| 2010-01-22 (Inactive)
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
|
| [http://sourceforge.net/projects/mumbled/]
|

|-bgcolor="#f8f8ff"
| MyMumb-Panel
|  [PHP](http://php.net/)
| # GPLv3
| V0.1
| 2014-09-18
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
| Multi-server management, Users Managment and soon channel viewer.
| [https://github.com/dieonar/MyMumb-Panel/]
|}


<small>Note: We recommend using a preferably [[Ice]] or at least [[DBus]] capable interface.</small>

= # anchor|Standalone ApplicationsDesktop Applications (GUI) =
{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! OS
! [[DBus]]
! [[Ice]]
! Comment
! Weblink

|-bgcolor="#f8f8ff"
| Murmur Admin Console
|  [Windows](http://de.wikipedia.org/wiki/Microsoft_Windows)
| bgcolor=#ddffdd | Yes
| bgcolor=#ffdddd | No
| Add, edit and delete users over SSH
| [http://bograt.com/Murmur/]

|-bgcolor="#f8f8ff"
|  [Mur](http://yulli.cleanvoice.ru/ Yulli)
|  [Windows](http://de.wikipedia.org/wiki/Microsoft_Windows)
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| Add, remove and control virtual servers remotely (supports SSH)
| [http://yulli.cleanvoice.ru]
|}

= Commandline-Interfaces =
Note: gRPC is experimental and not yet implemented by default, but will likely be implemented in near future (Status from June 2020). <br>
Dbus is deprecated. 

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! OS
! [[DBus]]
! [[Ice]]
! [[gRPC]]
! Comment
! Weblink

|-bgcolor="#f8f8ff"
| murmur-cli
| Linux
| bgcolor=#ffdddd | No
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| CLI for gRPC protocol
| https://github.com/layeh/murmur-cli

|-bgcolor="#f8f8ff"
| [[mice]]
| multi-platform
| bgcolor=#ffdddd | No
| bgcolor=#ddffdd | Yes
| bgcolor=#ffdddd | No
| Helper script written in  [Python](http://www.python.org)
Note: Potentially outdated
| [https://github.com/mumble-voip/mumble-scripts/raw/master/Helpers/mice.py]

|-bgcolor="#f8f8ff"
| RegMum
|  [Windows](http://de.wikipedia.org/wiki/Microsoft_Windows)
| bgcolor=#ddffdd | Yes
| bgcolor=#ffdddd | No
| bgcolor=#ffdddd | No
| Bat script
Note: Potentially outdated
| [DBus_scripts](DBus_scripts#Windows.md)

|-bgcolor="#f8f8ff"
| mmctl
|  [Python](http://www.python.org)
| bgcolor=#ddffdd | Yes
| bgcolor=#ffdddd | No
| bgcolor=#ffdddd | No
| 1.1.8 - Easy to use script for managing servers and adding users locally
Note: Potentially outdated (last update 2013)
| [http://github.com/mbr/mmctl]

|-bgcolor="#f8f8ff"
| [[Murmur-manager]]
| Ruby
| bgcolor=#ddffdd | Yes
| bgcolor=#ddffdd | Yes
| bgcolor=#ffdddd | No
| 1.2.1
Note: Potentially outdated (last update 2013)
|  [GitHub](http://github.com/cheald/Murmur-manager/)

|}

= Bots =
{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! Description
! Programming language
! Comment
! License
! Weblink

|-bgcolor="#f8f8ff"
| '''Stumble'''
| A fully extensible, SQLite enhanced bot, that ships with a standard extension library, including audio file saving and playback using FFmpeg.
| JavaScript (Node.js)
| -
| MIT
| [https://github.com/Okahyphen/stumble]

|-bgcolor="#f8f8ff"
| '''Jeanne'''
| Jeanne is meant to be a powerful Music bot for Mumble, with voice recognition. She can stream youtube video and (web)radio, with features like on-the-fly playlist and auto-playing.
| JavaScript (Node.js)
| -
| MIT
| [https://github.com/TinyMan/node-jeanne]
|-bgcolor="#f8f8ff"

| '''Calico'''
| A Mumble bot that connects to an SQL server and responds to text commands with audio / text responses. Built with [[piepan]].
| Lua
| -
| MIT
| [https://github.com/Okahyphen/calico]

|-bgcolor="#f8f8ff"
| '''Eve-Bot'''
| From the website: This bot is written for online multiplayer communities playing games like TF2 or CSS, where the spectator's view of the game is sometimes delayed to prevent collusion.
| Python
| -
| # BSD3
| [http://frymaster.127001.org/mumble/]

|-bgcolor="#f8f8ff"
| '''mumble-bots'''
| Several bot scripts based on [[Mumble Ruby]].
| Ruby
| -
|
| [https://github.com/SuperTux88/mumble-bots]

|-bgcolor="#f8f8ff"
| '''mumble-dicebot'''
| Connects as a user to a [[Mumble Server]] and listens for dice commands.
| Ruby
| -
|  [WTF](https://en.wikipedia.org/wiki/WTFPL)
| [https://github.com/vaxr/mumble-dicebot/]

|-bgcolor="#f8f8ff"
| '''mumble-ruby'''
| A headless [here](Mumble client]] which can send audio from a named pipe into a [[Mumble server]]. Further information is available [[Mumble Ruby.md).
| Ruby
| -
| MIT License
| [https://github.com/perrym5/mumble-ruby]

|-bgcolor="#f8f8ff"
| '''mumblebot'''
| Connects as a user to a server and listens for text commands. Among others it has a soundboard. Based on [[Mumble Ruby]]
| Ruby
| -
|
| [https://github.com/erulabs/mumblebot/]

|-bgcolor="#f8f8ff"
| '''mumblebot'''
| Connects as a user to a [[Mumble Server]] and can run local scripts to interact with the server.
| Python
| -
| # BSD3
| [http://code.google.com/p/mumblebot/wiki/About]

|-bgcolor="#f8f8ff"
| '''mumblecop'''
| Connects to a [[Mumble Server]] and listens for commands which trigger plugins. Several plugins included already, including ones for streaming youtube audio, rolling dice, and displaying a countdown. More plugins can easily be added. Uses [[Mumble Ruby]]
| Ruby
| -
| MIT
| [https://bitbucket.org/Flandoo/mumblecop]

|-bgcolor="#f8f8ff"
| '''mumblerecbot'''
| Connects as a user to a server and records the audio stream as a file. Is based on [[PyMumble]].
| Python
| -
| # GPLv3
| [https://github.com/Robert904/mumblerecbot]

|-bgcolor="#f8f8ff"
| '''piepan'''
| An easy to use framework for writing Mumble bots using Lua
| Lua
| -
| MPL 2.0
| [https://github.com/layeh/piepan]

|-bgcolor="#f8f8ff"
| '''sftmumblebot'''
| A chat bridge between IRC and a [[Mumble Server]].
| Python
| -
| # GPLv3
| [https://github.com/SFTtech/sftmumblebot]

|-bgcolor="#f8f8ff"
|'''Mumble-Ruby-Pluginbot'''
| Mumble-Ruby-Pluginbot is an audio bot that can be controlled through text messages in the Mumble client, can download music from Youtube and other online sources. It offers many commands to control the MPD session which feeds the bot, for example to change the volume, display and load playlis(s), and many more.
| Ruby
| -
| -
| [https://wiki.natenom.de/en/mumble/clienten_und_projekte/bots/mumble-ruby-pluginbot]

|-bgcolor="#f8f8ff"
|'''Ultros'''
| Extensible, multi-protocol, general-purpose bot. 
| Python
| -
|  [Artistic-2.0](http://opensource.org/licenses/Artistic-2.0)
| [https://github.com/UltrosBot/Ultros]

|-bgcolor="#f8f8ff"
|'''Mumsi'''
| SIP to Mumble gateway based on PJSIP stack and Mumlib library. Enables the user to participate in Mumble conference using SIP client or perhaps ordinary telephone, by VoIP provider.
| C++
| -
|  [Apache-2.0](http://opensource.org/licenses/Apache-2.0)
| [https://github.com/slomkowski/mumsi]

|-bgcolor="#f8f8ff"
|'''Botamusique'''
| Bot to play YouTube / SoundCloud / radio / local music on Mumble (using pymumble).
| Python
| -
|  [2.0](http://choosealicense.com/licenses/mpl-2.0/ MPL)
| [https://github.com/azlux/botamusique]

|-bgcolor="#f8f8ff"
|'''JJMumbleBot'''
| A plugin-based Python 3 Mumble bot with extensive features.
| Python
| -
|  [3.0](https://choosealicense.com/licenses/gpl-3.0 GPL)
| [https://github.com/DuckBoss/JJMumbleBot]

|-bgcolor="#f8f8ff"
|'''Rena Mumble'''
| A music bot for Mumble.
| JavaScript
| -
|  [MIT](https://choosealicense.com/licenses/mit/)
| [https://git.lolcat.ca/lolcat/rena_mumble]

|}

= Channel Viewers =

We encourage anyone developing a viewer to use the open and documented [[Channel Viewer Protocol]] to ensure inter-operability and compatibility.

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! Type
! Platform
! Provides CVP
! Reads CVP
! Proprietary (Non-CVP)
! Comment
! Weblink

|-bgcolor="#f8f8f8"
| Mumble.com
| Web
| Javascript
| No
| '''Yes'''
| No
| Enter the URL to the JSON encoded Channel Viewer Protocol provided by your Mumble host to create a unique channel viewer. Requires a CVP provider to query the Mumble server and generate the JSON.
|  [Tool](http://www.mumble.com/mumble-server-status.php Mumble.com Status)


|-bgcolor="#f8f8f8"
| FlaskCVP
| Web
| Python,  [Flask](http://flask.pocoo.org/)
| '''Yes'''
| No
| No
| A minimalistic CVP provider written using Mumble-Django's connection library and the Flask framework.
|  [flaskcvp.py](https://bitbucket.org/Svedrin/mumble-django/src/tip/pyweb/flaskcvp.py)

|-bgcolor="#f8f8ff"
| GTMurmur
| Web
| Binary
| '''Yes'''
| No
| '''Yes'''
| Server-side binary for Murmur which adds support for GameTracker.com queries. Also provides CVP via socket which can be used by other channel viewers. 
|  [GameTracker.com](http://www.gametracker.com/downloads/gtmurmurplugin.php)

|-bgcolor="#f8f8ff"
| MurmurQuery
| Web
| PHP
| No
| '''Yes'''
| No
| PHP class that reads CVP JSON data from the GTMurmur Plugin and displays users and channels in HTML.
|  [GitHub](http://github.com/edmundask/MurmurQuery)

|-bgcolor="#f8f8f8"
| [[Murmur-manager]]
| Web
| Ruby
| No
| No
| '''Yes'''
| 
|  [GitHub](http://github.com/cheald/Murmur-manager/)

|-bgcolor="#f8f8ff"
| [[Mumble reader]]
| Web
| PHP/Javascript
| '''Yes'''
| '''Yes'''
| No
| JS Viewer which uses PHP with Ice 3.3 to query a Mumble server. Does not support the latest version of Ice (3.4) but the clean JS front-end can be used with other CVP providers.
|  [Webpage](http://mumble.rko.nu/)
 [Github](https://github.com/Pimmetje/mumblereader)

|-bgcolor="#f8f8f8"
| [MumPI](Mumble PHP Interface.md)
| Web
| PHP/Javascript
| '''Yes'''
| '''Yes'''
| '''Yes'''
| JS-Viewer uses own protocoll/calls to MumPI.
MumPI provides JSON-Channel Viewer Protocol-webservice for other viewers.
|  [@Github](http://github.com/Kissaki/MumPI/wiki)

|-bgcolor="#f8f8f8"
| MView
| Web
| Javascript
| No
| '''Yes'''
| No
| JS-Viewer injecting HTML (no evil iframes etc necessary!).
|  [@Github](https://github.com/Kissaki/MView MView)

|-bgcolor="#f8f8ff"
| Mumble Watcher
| Desktop
| QT/KDE
| No
| '''Yes'''
| No
| Useful if you want to see who's online in a Desktop app without actually connecting, e.g. because you're on a PC without a proper headset.
|  [BitBucket](http://bitbucket.org/Svedrin/mumble-watcher/)

|-bgcolor="#f8f8f8"
| [[Mumble-Django]]
| Web
| JavaScript
| No
| '''Yes'''
| No
| An ExtJS component that inherits Ext.tree.TreeView to build a channel viewer.
|  [BitBucket](http://mumble-django.org/bb/src/tip/pyweb/mumble/media/js/channelviewer.js)  [Documentation](http://mumble-django.org/docs/api/channelviewer.html)

|-bgcolor="#f8f8f8"
| Mumble-widget
| Web
| JavaScript
| No
| '''Yes'''
| No
| A CVP compatible web-based channel viewer widget to display active users on your Mumble server. Easy setup, just copy and paste snippet of code to your website.
|  [Website](http://mumble-widget.guildbit.com/)  [Github](https://github.com/alfg/mumble-widget)  [Example](http://jsfiddle.net/alfg/3m86purL/ JSFiddle)

|-bgcolor="#f8f8f8"
| Command Channel
| Web
| PHP/JavaScript/EQdkp-Plus/Joomla!/WordPress
| No
| '''Yes'''
| No
| A robust channel viewer that has been packaged into several different formats for popular Content Management Systems. You can easily change the icons and colors used.
|  [EQdkp-Plus](http://commandchannel.com/Downloads/eqdkp-plus/mumbleviewer.zip Module for)

 [Joomla!](http://extensions.joomla.org/extensions/sports-a-games/game-servers/16358 Extension for)

 [WordPress](http://wordpress.org/extend/plugins/mumble-channel-viewer/ Plugin for)

 [only](http://commandchannel.com/Downloads/mumble-channel-viewer-php.zip PHP)

 [only](http://commandchannel.com/Downloads/mumble-channel-viewer-javascript.zip JavaScript)

 [Documentation](http://github.com/CommandChannel/Mumble-Channel-Viewer/wiki JavaScript)

 [code](http://github.com/CommandChannel/Mumble-Channel-Viewer Source)

 [above)](http://github.com/ClusterFCK/Drupal-Mumble-Viewer Module for Drupal 7 (Based on the)

|-bgcolor="#f8f8f8"
| PHP Mumble Viewer
| Web
| PHP
| '''Yes'''
| '''Yes'''
| No
| Project abandoned.
|  [phpmumbleviewer.coolcow.org](http://phpmumbleviewer.coolcow.org/)

|-bgcolor="#f8f8f8"
| [[Voice Comms Viewer]]
| Web
| JavaScript
| No
| '''Yes'''
| No
| A site that creates Channel Viewers for Mumble, Teamspeak & Ventrilo using the Channel Viewer Protocol
|  [commsviewer.com](http://commsviewer.com/)

|-bgcolor="#f8f8f8"
| Mumble Channel Viewer
| Web
| JavaScript
| No
| '''Yes'''
| No
| Chrome extension that reads CVP JSON or XML data and displays channels and users.
|  [Store](https://chrome.google.com/webstore/detail/mumble-channel-viewer/delalapmnpndmfopplmjegencdnddfcc Chrome Web)
 [GitHub](https://github.com/nunof07/chrome-mumble)
|-bgcolor="#f8f8f8"
| MumbleCVP
| Web
| Docker
| '''Yes'''
| No
| No
| A fastAPI version of FlaskCVP using python 3 in a dockerized container.
|  [Dockerhub](https://hub.docker.com/r/ajmandourah/mumblecvp)



|}

= Authenticators =

<div style="float:right; border:1px solid #ccc;">
![Image](mumble_authenticator_introduction.png)
</div>
Authenticators allow server administrators to adjust the login back-end of Mumble servers. This allows users to log in with their account information of an existing database, for example logging in with their data from a forum.

{| class="wikitable sortable"
|-
! Account Source !! License !! Weblink
|-
| phpBB3 || 3-clause BSD ||  [phpBB3](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/phpBB3 mumble-voip/mumble-scripts)
|-
| SMF 2.0 || 3-clause BSD ||  [2.0](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/SMF/2.0 mumble-voip/mumble-scripts SMF)
|-
| SMF 1.x || 3-clause BSD ||  [1.x](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/SMF/1.x mumble-voip/mumble-scripts SMF)
|-
| LDAP || 3-clause BSD ||  [LDAP](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/LDAP mumble-voip/mumble-scripts)
|-
| Eve-Online || GPL ||  [public-api2.2.py](http://bawki.de/mumble/public-api2.2.py)
|-
| Drupal || 3-clause BSD ||  [mumble-drupal-auth](https://github.com/dsnopek/mumble-drupal-auth)
|}

= Miscellaneous Scripts =

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! Type
! Platform
! Protocol
! Comment
! Weblink

|-bgcolor="#f8f8ff"
| Evebot
| Bot
| Python
| Mumble client
| Relays comms from one channel to another with a delay (to synchronise comms for time-delayed game spectators, for example)
|  [Evebot](http://frymaster.127001.org/mumble/)

|-bgcolor="#f8f8ff"
| [[Mumo]]
| Bot
| Python
| ICE
| Highly extensible script that can use external events (such as gamestate changes) to dynamically shuffle users into channels and groups. Support for various user states and the game "Battlefield 2".
|  [mumo](https://github.com/mumble-voip/mumo)

|-bgcolor="#f8f8ff"
| Murmur-Munin
| Statistics
| Python
| ICE
| A plugin for Munin to create statistics for your Mumble-Server.
|  [Murmur-Munin](https://github.com/Natenom/munin-plugins/blob/master/murmur-munin.py)

|-bgcolor="#f8f8ff"
| Murmur-REST
| RESTful API
| Python
| ICE
| A RESTful API for administering virtual Mumble servers. Built with Flask and Ice.
|  [Murmur-REST](https://github.com/alfg/murmur-rest)

|}

= Server Deployment and Management =

These tools will help you deploy and manage Murmur servers.

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Name
! State
! Source-Language
! License
! Comment
! Weblink

|-bgcolor="#f8f8ff"
|  [ajmandourah/mumble-docker](https://www.github.com/ajmandourah/Mumble-docker)
| Stable
| Shell/Dockerfile
| MIT
| A container which includes a mumble-server. Easy deployment with access to conf files, logs and databases for easy backups.
|  [GitHub](https://www.github.com/ajmandourah/mumble-docker)
 [DockerHub](https://hub.docker.com/r/ajmandourah/mumble)

|-bgcolor="#f8f8ff"
|  [sudoforge/mumble-server](https://github.com/sudoforge/docker-images/tree/master/mumble-server)
| Stable
| Shell/Dockerfile
| MIT
| Run mumble-server in a docker container - built for easy deployment and management at scale.
|  [GitHub](https://github.com/sudoforge/docker-images/tree/master/mumble-server)
 [DockerHub](https://hub.docker.com/r/sudoforge/mumble-server)

|}


