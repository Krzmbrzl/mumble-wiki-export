**If you created or found an application you think should be included or
find out that some software does not work anymore, edit this page, open
a discussion or report an issue on GitHub instead:
<https://github.com/mumble-voip/mumble-www/issues>.**

# Clients

<table>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Platform</p></th>
<th><p>Programming language</p></th>
<th><p>Comment</p></th>
<th><p>License</p></th>
<th><p>Weblink</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Mumla</strong></p></td>
<td><p>Android</p></td>
<td><p>Java</p></td>
<td><p>Fork (aka continuation) of Plumble.</p></td>
<td><p><a href="https://gitlab.com/quite/mumla/-/raw/master/LICENSE">GPLv3</a></p></td>
<td><p><a href="https://gitlab.com/quite/mumla">GitLab</a></p></td>
</tr>
<tr class="even">
<td><p><strong>mumble-web</strong></p></td>
<td><p>Web</p></td>
<td><p>HTML5 and JavaScript</p></td>
<td><p>Quite a few features are still missing, most noticeably voice activity detection and all administrative functionality.</p></td>
<td><p><a href="https://opensource.org/licenses/ISC">ISC</a></p></td>
<td><p><a href="https://github.com/Johni0702/mumble-web">GitHub</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>talKKonnect</strong></p></td>
<td><p>Linux</p></td>
<td><p>Go</p></td>
<td><p>talKKonnect is a Linux CLI Headless Self Contained Mumble Client For Raspberry Pi with LCD, Channel Control and Granular XML Config. Using GPIOs you can interface with RF radios or other network radio technologies.</p></td>
<td><p><a href="https://opensource.org/licenses/MPL-2.0">MPL</a></p></td>
<td><p><a href="https://talkkonnect.com/">talkkonnect</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Wahay</strong></p></td>
<td><p>Linux</p></td>
<td><p>Go</p></td>
<td><p>Wahay is an easy-to-use, secure and decentralized conference call application that provides private and autonomous digital communications to everyone. It combines Grumble, Mumble and Tor Onion services.</p></td>
<td><p><a href="https://github.com/digitalautonomy/wahay/blob/master/LICENSE">GPLv3</a></p></td>
<td><p><a href="https://www.wahay.org">Wahay</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Pymumble</strong></p></td>
<td><p>Linux</p></td>
<td><p>Python</p></td>
<td><p>A mumble client written in python. Offers some special features (like a Musicbot (that supports stereo transmission)), but also lacks some features. See the Github repo for details.</p></td>
<td><p><a href="https://github.com/azlux/pymumble/blob/pymumble_py3/LICENSE">GPLv3</a></p></td>
<td><p><a href="https://github.com/azlux/pymumble">GitHub</a></p></td>
</tr>
<tr class="even">
<td><p><strong>barnard</strong></p></td>
<td><p>Linux</p></td>
<td><p>Go</p></td>
<td><p>barnard is a terminal-based client with a curses-like UI. Built on the Gumble library. Note: barnard was last updated 2018.</p></td>
<td><p><a href="https://raw.githubusercontent.com/layeh/barnard/master/LICENSE">GPLv2</a></p></td>
<td><p><a href="https://github.com/layeh/barnard">GitHub</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>WiMic</strong></p></td>
<td><p>Android</p></td>
<td><p>Java / NDK</p></td>
<td><p>Fork of Plumble. (WiMic has many features added like echo canceller, performance enabled for 8 Khz and 8k bitrates at 10 ms latency, performed vox gain control, battery optimization and new native NEON preprocessing audio libraries, mainly focused on OPUS codec performance).</p>
<p>WiMic Android client can work with WiMic Server/Client too.</p></td>
<td><p><a href="https://github.com/hiro2233/wimic_android/blob/master/LICENSE">GPLv3</a></p></td>
<td><p><a href="https://github.com/hiro2233/wimic_android">Github</a></p></td>
</tr>
</tbody>
</table>

# Servers

Note: These servers might not have all recent features and
functionality.

<table>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Status</p></th>
<th><p>Source-Language</p></th>
<th><p>License</p></th>
<th><p>Comment</p></th>
<th><p>Weblink</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Grumble</p></td>
<td><p>Experimental</p></td>
<td><p><a href="http://golang.org">Go</a></p></td>
<td></td>
<td><p>Alternative Mumble server written in Go</p></td>
<td><p><a href="https://github.com/mumble-voip/grumble">Project page and source on github.com</a></p></td>
</tr>
<tr class="even">
<td><p>uMurmur</p></td>
<td><p>Stable (outdated)</p></td>
<td><p>C</p></td>
<td></td>
<td><p>uMurmur is a minimalistic Mumble server primarily targeted to run on routers with an open OS like OpenWRT. The server part of Mumble is called Murmur, hence the name uMurmur. Note: uMurmur was last updated 2017, so it is outdated.</p></td>
<td><p><a href="https://github.com/fatbob313/umurmur">Project page and sources on github.com</a></p></td>
</tr>
<tr class="odd">
<td><p>WiMic Server/Client (with GUI Manager)</p></td>
<td><p>Stable</p></td>
<td><p>C/C++</p></td>
<td><p><a href="https://github.com/hiro2233/wimic/blob/master/LICENSE">GPLv3</a></p></td>
<td><p>Hybrid server, based on uMurmur and Mumlib. WiMic Server/Client can run on GNU/Linux and Windows (MSYS2) platforms, focused to work with WiMic Android performance.</p></td>
<td><p><a href="https://github.com/hiro2233/wimic">Github</a></p></td>
</tr>
</tbody>
</table>

# Libraries

| Name             | Technology           | Comment                                                                  | License | Weblink                                          |
| ---------------- | -------------------- | ------------------------------------------------------------------------ | ------- | ------------------------------------------------ |
| **gumble**       | Go                   | \-                                                                       | MPL 2.0 | [1](https://github.com/layeh/gumble/)            |
| **lua-mumble**   | Lua (Linux)          | \-                                                                       | MIT     | [2](https://github.com/bkacjios/lua-mumble)      |
| **MumbleKit**    | Objective-C          | \-                                                                       | BSD3    | [3](https://github.com/mumble-voip/mumblekit)    |
| **MumbleSharp**  | C\#                  | \-                                                                       | MIT     | [4](https://github.com/martindevans/MumbleSharp) |
| **node-mumble**  | JavaScript (Node.js) | \-                                                                       | MIT     | [5](https://github.com/Rantanen/node-mumble)     |
| **pymumble**     | Python               | \-                                                                       | GNU     | [6](https://github.com/azlux/pymumble)           |
| **Mumble-Unity** | C\# (Unity3D)        | \-                                                                       | MIT     | [7](https://github.com/BananaHemic/Mumble-Unity) |
| **NoodleJS**     | JavaScript (Node.js) | \-                                                                       | MIT     | [8](https://github.com/Gielert/NoodleJS)         |
| **gomble**       | Go                   | youtube, UDP, for music bots                                             | MIT     | [9](https://github.com/CodingVoid/gomble/)       |
| **Humla**        | Java (Android)       | Used for [Mumla](Mumla "wikilink"). Fork of Jumble.                      | GPLv3   | [10](https://gitlab.com/quite/humla)             |
| **mumlib**       | C++, boost::asio     | Note: Outdated (last update: 2018). Provides basic functionality, no ACL | LGPLv3  | [11](https://github.com/slomkowski/mumlib)       |

# Web-Interfaces

There are several browser based interfaces which can be used to
administrate the Murmur server. If you need something very basic or want
to create your own interface you should take a look at Murmur's [script
folder](https://github.com/mumble-voip/mumble/tree/master/scripts/server)
which contains some basic web-interface examples which use
[Ice](Ice "wikilink") or [DBus](DBus "wikilink") (we recommend using
Ice, as DBus is kept for backwards compatibility, and is not being
extended for quite some time). Additionally the following table contains
a collection of more elaborate Web-Interfaces:

<table>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Technology</p></th>
<th><p>License</p></th>
<th><p>Current Version</p></th>
<th><p>Last Release</p></th>
<th><p><a href="DBus" title="wikilink">DBus</a></p></th>
<th><p><a href="Ice" title="wikilink">Ice</a></p></th>
<th><p>1.2.x</p></th>
<th><p>Comment</p></th>
<th><p>Weblink</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="Mumble-Django" title="wikilink">Mumble-Django</a></p></td>
<td><p><a href="http://www.python.org">Python</a> + <a href="http://www.djangoproject.com">Django</a></p></td>
<td></td>
<td><p>V2.7</p></td>
<td><p>2012-03-31</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Channel viewer (internal and support for others), admin panel, IPv6, <a href="Channel_Viewer_Protocol" title="wikilink">Channel Viewer Protocol</a>, Munin plugin, CLI, supports multiple servers and instances, user registration, textures, gravatar, translated to English, German, French, Italian and Japanese</p></td>
<td><p><a href="https://mumble-django.readthedocs.io">12</a></p></td>
</tr>
<tr class="even">
<td><p><a href="Mumble_PHP_Interface" title="wikilink">MumPI</a></p></td>
<td><p><a href="http://php.net/">PHP</a></p></td>
<td></td>
<td><p>V2.2.6</p></td>
<td><p>2015-12-09</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Admin and User functionality; multiserver (start, stop, add, remove, edit virtual servers), registration &amp; online user management, interface admin, admin-group and permission system, serverviewer</p></td>
<td><p><a href="http://github.com/Kissaki/MumPI/wiki">13</a></p></td>
</tr>
<tr class="odd">
<td><p>PHP Mumble Admin</p></td>
<td><p><a href="http://php.net/">PHP</a></p></td>
<td></td>
<td><p>V0.4.3</p></td>
<td><p>2013-02-07</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Complete administration control panel for Murmur designed for multiple virtual server. <a href="http://sourceforge.net/projects/phpmumbleadmin/">Website</a></p></td>
<td><p><a href="http://sourceforge.net/projects/phpmumbleadmin/">14</a></p></td>
</tr>
<tr class="even">
<td><p>Mumbled Webinterface</p></td>
<td><p><a href="http://php.net/">PHP</a></p></td>
<td></td>
<td><p>V0.2</p></td>
<td><p>2010-01-22 (Inactive)</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td></td>
<td><p><a href="http://sourceforge.net/projects/mumbled/">15</a></p></td>
</tr>
<tr class="odd">
<td><p>MyMumb-Panel</p></td>
<td><p><a href="http://php.net/">PHP</a></p></td>
<td></td>
<td><p>V0.1</p></td>
<td><p>2014-09-18</p></td>
<td><p>No</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Multi-server management, Users Managment and soon channel viewer.</p></td>
<td><p><a href="https://github.com/dieonar/MyMumb-Panel/">16</a></p></td>
</tr>
</tbody>
</table>

<small>Note: We recommend using a preferably [Ice](Ice "wikilink") or at
least [DBus](DBus "wikilink") capable interface.</small>

# Desktop Applications (GUI)

| Name                                     | OS                                                        | [DBus](DBus "wikilink") | [Ice](Ice "wikilink") | Comment                                                         | Weblink                          |
| ---------------------------------------- | --------------------------------------------------------- | ----------------------- | --------------------- | --------------------------------------------------------------- | -------------------------------- |
| Murmur Admin Console                     | [Windows](http://de.wikipedia.org/wiki/Microsoft_Windows) | Yes                     | No                    | Add, edit and delete users over SSH                             | [17](http://bograt.com/Murmur/)  |
| [Yulli Mur](http://yulli.cleanvoice.ru/) | [Windows](http://de.wikipedia.org/wiki/Microsoft_Windows) | No                      | Yes                   | Add, remove and control virtual servers remotely (supports SSH) | [18](http://yulli.cleanvoice.ru) |

# Commandline-Interfaces

Note: gRPC is experimental and not yet implemented by default, but will
likely be implemented in near future (Status from June 2020).
Dbus is deprecated.

| Name                                        | OS                                                        | [DBus](DBus "wikilink") | [Ice](Ice "wikilink") | [gRPC](gRPC "wikilink") | Comment                                                                                                                | Weblink                                                                        |
| ------------------------------------------- | --------------------------------------------------------- | ----------------------- | --------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| murmur-cli                                  | Linux                                                     | No                      | No                    | Yes                     | CLI for gRPC protocol                                                                                                  | <https://github.com/layeh/murmur-cli>                                          |
| [mice](mice "wikilink")                     | multi-platform                                            | No                      | Yes                   | No                      | Helper script written in [Python](http://www.python.org) Note: Potentially outdated                                    | [19](https://github.com/mumble-voip/mumble-scripts/raw/master/Helpers/mice.py) |
| RegMum                                      | [Windows](http://de.wikipedia.org/wiki/Microsoft_Windows) | Yes                     | No                    | No                      | Bat script Note: Potentially outdated                                                                                  | [DBus_scripts](DBus_scripts#Windows "wikilink")                               |
| mmctl                                       | [Python](http://www.python.org)                           | Yes                     | No                    | No                      | 1.1.8 - Easy to use script for managing servers and adding users locally Note: Potentially outdated (last update 2013) | [20](http://github.com/mbr/mmctl)                                              |
| [Murmur-manager](Murmur-manager "wikilink") | Ruby                                                      | Yes                     | Yes                   | No                      | 1.2.1 Note: Potentially outdated (last update 2013)                                                                    | [GitHub](http://github.com/cheald/Murmur-manager/)                             |

# Bots

<table>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Description</p></th>
<th><p>Programming language</p></th>
<th><p>Comment</p></th>
<th><p>License</p></th>
<th><p>Weblink</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Stumble</strong></p></td>
<td><p>A fully extensible, SQLite enhanced bot, that ships with a standard extension library, including audio file saving and playback using FFmpeg.</p></td>
<td><p>JavaScript (Node.js)</p></td>
<td><p>-</p></td>
<td><p>MIT</p></td>
<td><p><a href="https://github.com/Okahyphen/stumble">21</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Jeanne</strong></p></td>
<td><p>Jeanne is meant to be a powerful Music bot for Mumble, with voice recognition. She can stream youtube video and (web)radio, with features like on-the-fly playlist and auto-playing.</p></td>
<td><p>JavaScript (Node.js)</p></td>
<td><p>-</p></td>
<td><p>MIT</p></td>
<td><p><a href="https://github.com/TinyMan/node-jeanne">22</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Calico</strong></p></td>
<td><p>A Mumble bot that connects to an SQL server and responds to text commands with audio / text responses. Built with <a href="piepan" title="wikilink">piepan</a>.</p></td>
<td><p>Lua</p></td>
<td><p>-</p></td>
<td><p>MIT</p></td>
<td><p><a href="https://github.com/Okahyphen/calico">23</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Eve-Bot</strong></p></td>
<td><p>From the website: This bot is written for online multiplayer communities playing games like TF2 or CSS, where the spectator's view of the game is sometimes delayed to prevent collusion.</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td></td>
<td><p><a href="http://frymaster.127001.org/mumble/">24</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>mumble-bots</strong></p></td>
<td><p>Several bot scripts based on <a href="Mumble_Ruby" title="wikilink">Mumble Ruby</a>.</p></td>
<td><p>Ruby</p></td>
<td><p>-</p></td>
<td></td>
<td><p><a href="https://github.com/SuperTux88/mumble-bots">25</a></p></td>
</tr>
<tr class="even">
<td><p><strong>mumble-dicebot</strong></p></td>
<td><p>Connects as a user to a <a href="Mumble_Server" title="wikilink">Mumble Server</a> and listens for dice commands.</p></td>
<td><p>Ruby</p></td>
<td><p>-</p></td>
<td><p><a href="https://en.wikipedia.org/wiki/WTFPL">WTF</a></p></td>
<td><p><a href="https://github.com/vaxr/mumble-dicebot/">26</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>mumble-ruby</strong></p></td>
<td><p>A headless <a href="Mumble_client" title="wikilink">Mumble client</a> which can send audio from a named pipe into a <a href="Mumble_server" title="wikilink">Mumble server</a>. Further information is available <a href="Mumble_Ruby" title="wikilink">here</a>.</p></td>
<td><p>Ruby</p></td>
<td><p>-</p></td>
<td><p>MIT License</p></td>
<td><p><a href="https://github.com/perrym5/mumble-ruby">27</a></p></td>
</tr>
<tr class="even">
<td><p><strong>mumblebot</strong></p></td>
<td><p>Connects as a user to a server and listens for text commands. Among others it has a soundboard. Based on <a href="Mumble_Ruby" title="wikilink">Mumble Ruby</a></p></td>
<td><p>Ruby</p></td>
<td><p>-</p></td>
<td></td>
<td><p><a href="https://github.com/erulabs/mumblebot/">28</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>mumblebot</strong></p></td>
<td><p>Connects as a user to a <a href="Mumble_Server" title="wikilink">Mumble Server</a> and can run local scripts to interact with the server.</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td></td>
<td><p><a href="http://code.google.com/p/mumblebot/wiki/About">29</a></p></td>
</tr>
<tr class="even">
<td><p><strong>mumblecop</strong></p></td>
<td><p>Connects to a <a href="Mumble_Server" title="wikilink">Mumble Server</a> and listens for commands which trigger plugins. Several plugins included already, including ones for streaming youtube audio, rolling dice, and displaying a countdown. More plugins can easily be added. Uses <a href="Mumble_Ruby" title="wikilink">Mumble Ruby</a></p></td>
<td><p>Ruby</p></td>
<td><p>-</p></td>
<td><p>MIT</p></td>
<td><p><a href="https://bitbucket.org/Flandoo/mumblecop">30</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>mumblerecbot</strong></p></td>
<td><p>Connects as a user to a server and records the audio stream as a file. Is based on <a href="PyMumble" title="wikilink">PyMumble</a>.</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td></td>
<td><p><a href="https://github.com/Robert904/mumblerecbot">31</a></p></td>
</tr>
<tr class="even">
<td><p><strong>piepan</strong></p></td>
<td><p>An easy to use framework for writing Mumble bots using Lua</p></td>
<td><p>Lua</p></td>
<td><p>-</p></td>
<td><p>MPL 2.0</p></td>
<td><p><a href="https://github.com/layeh/piepan">32</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>sftmumblebot</strong></p></td>
<td><p>A chat bridge between IRC and a <a href="Mumble_Server" title="wikilink">Mumble Server</a>.</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td></td>
<td><p><a href="https://github.com/SFTtech/sftmumblebot">33</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Mumble-Ruby-Pluginbot</strong></p></td>
<td><p>Mumble-Ruby-Pluginbot is an audio bot that can be controlled through text messages in the Mumble client, can download music from Youtube and other online sources. It offers many commands to control the MPD session which feeds the bot, for example to change the volume, display and load playlis(s), and many more.</p></td>
<td><p>Ruby</p></td>
<td><p>-</p></td>
<td><p>-</p></td>
<td><p><a href="https://wiki.natenom.de/en/mumble/clienten_und_projekte/bots/mumble-ruby-pluginbot">34</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Ultros</strong></p></td>
<td><p>Extensible, multi-protocol, general-purpose bot.</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td><p><a href="http://opensource.org/licenses/Artistic-2.0">Artistic-2.0</a></p></td>
<td><p><a href="https://github.com/UltrosBot/Ultros">35</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Mumsi</strong></p></td>
<td><p>SIP to Mumble gateway based on PJSIP stack and Mumlib library. Enables the user to participate in Mumble conference using SIP client or perhaps ordinary telephone, by VoIP provider.</p></td>
<td><p>C++</p></td>
<td><p>-</p></td>
<td><p><a href="http://opensource.org/licenses/Apache-2.0">Apache-2.0</a></p></td>
<td><p><a href="https://github.com/slomkowski/mumsi">36</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Botamusique</strong></p></td>
<td><p>Bot to play YouTube / SoundCloud / radio / local music on Mumble (using pymumble).</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td><p><a href="http://choosealicense.com/licenses/mpl-2.0/">MPL 2.0</a></p></td>
<td><p><a href="https://github.com/azlux/botamusique">37</a></p></td>
</tr>
<tr class="even">
<td><p><strong>JJMumbleBot</strong></p></td>
<td><p>A plugin-based Python 3 Mumble bot with extensive features.</p></td>
<td><p>Python</p></td>
<td><p>-</p></td>
<td><p><a href="https://choosealicense.com/licenses/gpl-3.0">GPL 3.0</a></p></td>
<td><p><a href="https://github.com/DuckBoss/JJMumbleBot">38</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Rena Mumble</strong></p></td>
<td><p>A music bot for Mumble.</p></td>
<td><p>JavaScript</p></td>
<td><p>-</p></td>
<td><p><a href="https://choosealicense.com/licenses/mit/">MIT</a></p></td>
<td><p><a href="https://git.lolcat.ca/lolcat/rena_mumble">39</a></p></td>
</tr>
</tbody>
</table>

# Channel Viewers

We encourage anyone developing a viewer to use the open and documented
[Channel Viewer Protocol](Channel_Viewer_Protocol "wikilink") to ensure
inter-operability and compatibility.

<table>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Type</p></th>
<th><p>Platform</p></th>
<th><p>Provides CVP</p></th>
<th><p>Reads CVP</p></th>
<th><p>Proprietary (Non-CVP)</p></th>
<th><p>Comment</p></th>
<th><p>Weblink</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mumble.com</p></td>
<td><p>Web</p></td>
<td><p>Javascript</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>Enter the URL to the JSON encoded Channel Viewer Protocol provided by your Mumble host to create a unique channel viewer. Requires a CVP provider to query the Mumble server and generate the JSON.</p></td>
<td><p><a href="http://www.mumble.com/mumble-server-status.php">Mumble.com Status Tool</a></p></td>
</tr>
<tr class="even">
<td><p>FlaskCVP</p></td>
<td><p>Web</p></td>
<td><p>Python, <a href="http://flask.pocoo.org/">Flask</a></p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>A minimalistic CVP provider written using Mumble-Django's connection library and the Flask framework.</p></td>
<td><p><a href="https://bitbucket.org/Svedrin/mumble-django/src/tip/pyweb/flaskcvp.py">flaskcvp.py</a></p></td>
</tr>
<tr class="odd">
<td><p>GTMurmur</p></td>
<td><p>Web</p></td>
<td><p>Binary</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>Server-side binary for Murmur which adds support for GameTracker.com queries. Also provides CVP via socket which can be used by other channel viewers.</p></td>
<td><p><a href="http://www.gametracker.com/downloads/gtmurmurplugin.php">GameTracker.com</a></p></td>
</tr>
<tr class="even">
<td><p>MurmurQuery</p></td>
<td><p>Web</p></td>
<td><p>PHP</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>PHP class that reads CVP JSON data from the GTMurmur Plugin and displays users and channels in HTML.</p></td>
<td><p><a href="http://github.com/edmundask/MurmurQuery">GitHub</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="Murmur-manager" title="wikilink">Murmur-manager</a></p></td>
<td><p>Web</p></td>
<td><p>Ruby</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td></td>
<td><p><a href="http://github.com/cheald/Murmur-manager/">GitHub</a></p></td>
</tr>
<tr class="even">
<td><p><a href="Mumble_reader" title="wikilink">Mumble reader</a></p></td>
<td><p>Web</p></td>
<td><p>PHP/Javascript</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>JS Viewer which uses PHP with Ice 3.3 to query a Mumble server. Does not support the latest version of Ice (3.4) but the clean JS front-end can be used with other CVP providers.</p></td>
<td><p><a href="http://mumble.rko.nu/">Webpage</a> <a href="https://github.com/Pimmetje/mumblereader">Github</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="Mumble_PHP_Interface" title="wikilink">MumPI</a></p></td>
<td><p>Web</p></td>
<td><p>PHP/Javascript</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p><strong>Yes</strong></p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>JS-Viewer uses own protocoll/calls to MumPI. MumPI provides JSON-Channel Viewer Protocol-webservice for other viewers.</p></td>
<td><p><a href="http://github.com/Kissaki/MumPI/wiki">@Github</a></p></td>
</tr>
<tr class="even">
<td><p>MView</p></td>
<td><p>Web</p></td>
<td><p>Javascript</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>JS-Viewer injecting HTML (no evil iframes etc necessary!).</p></td>
<td><p><a href="https://github.com/Kissaki/MView">MView @Github</a></p></td>
</tr>
<tr class="odd">
<td><p>Mumble Watcher</p></td>
<td><p>Desktop</p></td>
<td><p>QT/KDE</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>Useful if you want to see who's online in a Desktop app without actually connecting, e.g. because you're on a PC without a proper headset.</p></td>
<td><p><a href="http://bitbucket.org/Svedrin/mumble-watcher/">BitBucket</a></p></td>
</tr>
<tr class="even">
<td><p><a href="Mumble-Django" title="wikilink">Mumble-Django</a></p></td>
<td><p>Web</p></td>
<td><p>JavaScript</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>An ExtJS component that inherits Ext.tree.TreeView to build a channel viewer.</p></td>
<td><p><a href="http://mumble-django.org/bb/src/tip/pyweb/mumble/media/js/channelviewer.js">BitBucket</a> <a href="http://mumble-django.org/docs/api/channelviewer.html">Documentation</a></p></td>
</tr>
<tr class="odd">
<td><p>Mumble-widget</p></td>
<td><p>Web</p></td>
<td><p>JavaScript</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>A CVP compatible web-based channel viewer widget to display active users on your Mumble server. Easy setup, just copy and paste snippet of code to your website.</p></td>
<td><p><a href="http://mumble-widget.guildbit.com/">Website</a> <a href="https://github.com/alfg/mumble-widget">Github</a> <a href="http://jsfiddle.net/alfg/3m86purL/">JSFiddle Example</a></p></td>
</tr>
<tr class="even">
<td><p>Command Channel</p></td>
<td><p>Web</p></td>
<td><p>PHP/JavaScript/EQdkp-Plus/Joomla!/WordPress</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>A robust channel viewer that has been packaged into several different formats for popular Content Management Systems. You can easily change the icons and colors used.</p></td>
<td><p><a href="http://commandchannel.com/Downloads/eqdkp-plus/mumbleviewer.zip">Module for EQdkp-Plus</a></p>
<p><a href="http://extensions.joomla.org/extensions/sports-a-games/game-servers/16358">Extension for Joomla!</a></p>
<p><a href="http://wordpress.org/extend/plugins/mumble-channel-viewer/">Plugin for WordPress</a></p>
<p><a href="http://commandchannel.com/Downloads/mumble-channel-viewer-php.zip">PHP only</a></p>
<p><a href="http://commandchannel.com/Downloads/mumble-channel-viewer-javascript.zip">JavaScript only</a></p>
<p><a href="http://github.com/CommandChannel/Mumble-Channel-Viewer/wiki">JavaScript Documentation</a></p>
<p><a href="http://github.com/CommandChannel/Mumble-Channel-Viewer">Source code</a></p>
<p><a href="http://github.com/ClusterFCK/Drupal-Mumble-Viewer">Module for Drupal 7 (Based on the above)</a></p></td>
</tr>
<tr class="odd">
<td><p>PHP Mumble Viewer</p></td>
<td><p>Web</p></td>
<td><p>PHP</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>Project abandoned.</p></td>
<td><p><a href="http://phpmumbleviewer.coolcow.org/">phpmumbleviewer.coolcow.org</a></p></td>
</tr>
<tr class="even">
<td><p><a href="Voice_Comms_Viewer" title="wikilink">Voice Comms Viewer</a></p></td>
<td><p>Web</p></td>
<td><p>JavaScript</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>A site that creates Channel Viewers for Mumble, Teamspeak &amp; Ventrilo using the Channel Viewer Protocol</p></td>
<td><p><a href="http://commsviewer.com/">commsviewer.com</a></p></td>
</tr>
<tr class="odd">
<td><p>Mumble Channel Viewer</p></td>
<td><p>Web</p></td>
<td><p>JavaScript</p></td>
<td><p>No</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>Chrome extension that reads CVP JSON or XML data and displays channels and users.</p></td>
<td><p><a href="https://chrome.google.com/webstore/detail/mumble-channel-viewer/delalapmnpndmfopplmjegencdnddfcc">Chrome Web Store</a> <a href="https://github.com/nunof07/chrome-mumble">GitHub</a></p></td>
</tr>
<tr class="even">
<td><p>MumbleCVP</p></td>
<td><p>Web</p></td>
<td><p>Docker</p></td>
<td><p><strong>Yes</strong></p></td>
<td><p>No</p></td>
<td><p>No</p></td>
<td><p>A fastAPI version of FlaskCVP using python 3 in a dockerized container.</p></td>
<td><p><a href="https://hub.docker.com/r/ajmandourah/mumblecvp">Dockerhub</a></p></td>
</tr>
</tbody>
</table>

# Authenticators

<div style="float:right; border:1px solid #ccc;">

![<File:Mumble_Authenticator_Introduction.png>](Mumble_Authenticator_Introduction.png
"File:Mumble_Authenticator_Introduction.png")

</div>

Authenticators allow server administrators to adjust the login back-end
of Mumble servers. This allows users to log in with their account
information of an existing database, for example logging in with their
data from a forum.

| Account Source | License      | Weblink                                                                                                                |
| -------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------- |
| phpBB3         | 3-clause BSD | [mumble-voip/mumble-scripts phpBB3](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/phpBB3)   |
| SMF 2.0        | 3-clause BSD | [mumble-voip/mumble-scripts SMF 2.0](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/SMF/2.0) |
| SMF 1.x        | 3-clause BSD | [mumble-voip/mumble-scripts SMF 1.x](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/SMF/1.x) |
| LDAP           | 3-clause BSD | [mumble-voip/mumble-scripts LDAP](https://github.com/mumble-voip/mumble-scripts/tree/master/Authenticators/LDAP)       |
| Eve-Online     | GPL          | [public-api2.2.py](http://bawki.de/mumble/public-api2.2.py)                                                            |
| Drupal         | 3-clause BSD | [mumble-drupal-auth](https://github.com/dsnopek/mumble-drupal-auth)                                                    |

# Miscellaneous Scripts

| Name                    | Type        | Platform | Protocol      | Comment                                                                                                                                                                                                | Weblink                                                                              |
| ----------------------- | ----------- | -------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| Evebot                  | Bot         | Python   | Mumble client | Relays comms from one channel to another with a delay (to synchronise comms for time-delayed game spectators, for example)                                                                             | [Evebot](http://frymaster.127001.org/mumble/)                                        |
| [Mumo](Mumo "wikilink") | Bot         | Python   | ICE           | Highly extensible script that can use external events (such as gamestate changes) to dynamically shuffle users into channels and groups. Support for various user states and the game "Battlefield 2". | [mumo](https://github.com/mumble-voip/mumo)                                          |
| Murmur-Munin            | Statistics  | Python   | ICE           | A plugin for Munin to create statistics for your Mumble-Server.                                                                                                                                        | [Murmur-Munin](https://github.com/Natenom/munin-plugins/blob/master/murmur-munin.py) |
| Murmur-REST             | RESTful API | Python   | ICE           | A RESTful API for administering virtual Mumble servers. Built with Flask and Ice.                                                                                                                      | [Murmur-REST](https://github.com/alfg/murmur-rest)                                   |

# Server Deployment and Management

These tools will help you deploy and manage Murmur servers.

| Name                                                                                            | State  | Source-Language  | License | Comment                                                                                                                     | Weblink                                                                                                                                      |
| ----------------------------------------------------------------------------------------------- | ------ | ---------------- | ------- | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| [ajmandourah/mumble-docker](https://www.github.com/ajmandourah/Mumble-docker)                   | Stable | Shell/Dockerfile | MIT     | A container which includes a mumble-server. Easy deployment with access to conf files, logs and databases for easy backups. | [GitHub](https://www.github.com/ajmandourah/mumble-docker) [DockerHub](https://hub.docker.com/r/ajmandourah/mumble)                          |
| [sudoforge/mumble-server](https://github.com/sudoforge/docker-images/tree/master/mumble-server) | Stable | Shell/Dockerfile | MIT     | Run mumble-server in a docker container - built for easy deployment and management at scale.                                | [GitHub](https://github.com/sudoforge/docker-images/tree/master/mumble-server) [DockerHub](https://hub.docker.com/r/sudoforge/mumble-server) |

[Category:3rd Party](Category:3rd_Party "wikilink")