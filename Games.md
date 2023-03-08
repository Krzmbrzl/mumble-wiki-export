'''NOTE: Please go to  [website](https://www.mumble.info/documentation/user/positional-audio/ the new documentation on our) instead. The documentation here is now obsolete.'''

---

= Overlay =
Our overlay is not technically game-specific but rendering-engine-specific. Thus it works for all games using supported rendering APIs.

For more information on the overlay, see [the respective page about the Overlay](Overlay.md).

= Positional audio =
![Image](positional_audio.gif)
Please note that Mumble works with all games as a regular voice chat application. Those listed on this page are the games for which we are providing [positional sound](Positional-Audio.md) support, so that the voice of your teammates comes from their direction in game.

This feature '''can be enabled as follows''':
* 1.) Check "[Advanced](Advanced client configuration.md)" in the ''Configure|Settings'' menu
* 2.) Go to ''Plugins'' and check "Link to Game and Transmit Position"

If you deselected ''Enable positional audio'' during setup you have to re-enable it in the wizard.

'''Just because your game says it is a different version from the plugin does not necessarily mean that the plugin will not work.'''

It is possible that some plugins are outdated in the current release; in that case please check the lists below.

If there is no update for the plugin, please report it  [here](https://github.com/mumble-voip/mumble/issues).

For additional info on what positional audio is and how it works in Mumble, see [here](Positional-Audio.md).

If you want to add support for a game and you are able to modify the source of this game you can use the [ this guide](Link]] plugin. If you cannot modify the source of the game you want to add, [[Pluginguide .md) should help. For an overall look at retrieving positional data from a game, see [ here](HackPositionalAudio .md).
<div style="clear:left;"></div>

## Supported games 

The following table displays which games positional audio is available for, from which game version on (/for which version), for what platform and if extended support is available.

Games that provide native positional data via the Link plugin are marked in <span style="background-color:#e8e8ff">blue</span> (that means they won’t get outdated). Outdated plugins are marked in <span style="background-color:#FFFFC0">yellow</span>.<br>
''No'' means that the games don't use the extended positional audio features that were introduced with Mumble 1.2. Move the pointer over to see more info about the extended support for a specific plugin (if available).

'''Note:''' Windows plugins work on Wine!

{{Warning
|message=Plugins for 64-bit games only work with Mumble x64!
}}
{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Game
! Version
! Action required
! Platform
! Extended support (Context, identity)

|-style="background-color:#f8f8ff"
|  [Chivalry](http://store.steampowered.com/app/17510 Age of)
| Build 4104
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#FFFFC0"
|  [2](http://www.arma2.com ArmA)
|  [1.08](http://steamcommunity.com/games/arma2/announcements/detail/1027014441254296137) while the latest is  [1.10](http://steamcommunity.com/games/arma2/announcements/detail/1370438673676192803)
| No
| Windows
| No

|-style="background-color:#e8e8ff"
|  [Arrowhead](http://www.arma2.com ArmA 2: Operation)
| >= 1.60
| Install the  [mod](https://dev.withsix.com/projects/mumblelink dedicated)
| Windows
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [3](https://arma3.com Arma)
| >= 0.5
| Install the  [mod](https://dev.withsix.com/projects/mumblelink dedicated)
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Corsa](https://www.assettocorsa.it/home-ac/ Assetto)
| CSP >= 0.1.77
| No
| Windows
| style="background-color:#abf8a1" | Yes

|-style="background-color:#f8f8ff"
|  [1](https://www.battlefield.com Battlefield)
|  [1.0.49.52296](https://www.battlefield.com/news/update-notes/spring-update)
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on server name. Identity: Team, Squad and Squad leader">Yes</span>

|-style="background-color:#f8f8ff"
|  [1942](http://www.battlefield.com/battlefield-1942 Battlefield)
| 1.61b
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [2](http://www.battlefield.com/battlefield-2 Battlefield)
| 1.50
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on host IP address and port. Identity: Host IP address and port, Commander, Squad Leader, Squad, Team, On VoIP, On VoIP com, Target squad ID">Yes</span>

|-style="background-color:#f8f8ff"
|  [2142](http://www.battlefield.com/battlefield-2142 Battlefield)
|  [1.51](http://largedownloads.ea.com/pub/patches/BF2142/)
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on host IP address and port. Identity: Host IP address and port, Team ID, Squad ID, Commander, Squad Leader, Target squad ID, On VoIP, On VoIP com, Player">Yes</span>

|-style="background-color:#f8f8ff"
|  [3](http://www.battlefield.com/battlefield3 Battlefield)
| Build 1147186 - End Game DLC
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on host IP address and port. Identity: Team, Squad, Squad Leader">Yes</span>

|-style="background-color:#f8f8ff"
|  [4](http://www.battlefield.com/battlefield4 Battlefield)
| 1.8.2.48475
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on Server ID. Identity: Host IP address and port, Team, Squad, Squad Leader, Squad State">Yes</span>

|-style="background-color:#f8f8ff"
|  [2](http://www.battlefield.com/battlefield-bad-company-2-vietnam Battlefield Bad Company)
| Build 795745
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [Heroes](http://www.battlefieldheroes.com Battlefield)
| ?
| No
| Windows
| No

|-style="background-color:#e8e8ff"
|  [Mesa](http://store.steampowered.com/app/362890 Black)
| Any
| No
| Any
| style="background-color:#abf8a1" | [<span title='See "Source Engine"'>Yes</span>](#Source_Engine.md)

|-style="background-color:#FFFFC0"
|  [Borderlands](http://borderlandsthegame.com)
|  [1.4.0](http://borderlands.wikia.com/wiki/Patch_1.4.0) while the latest is  [1.4.1](http://borderlands.wikia.com/wiki/Patch_1.4.1)
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#FFFFC0"
|  [2](http://store.steampowered.com/app/49520 Borderlands)
|  [1.8.3](http://borderlands.wikia.com/wiki/Patch_1.8.X_(Borderlands_2)) while the latest is  [1.8.4](http://borderlands.wikia.com/wiki/Patch_1.8.X_(Borderlands_2))
| No
| Windows
| style="background-color:#ddffdd" | <span title="Character name">Identity only</span>

|-style="background-color:#f8f8ff"
|  [Breach](http://breachgame.com)
| 1.1.0
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [2](http://store.steampowered.com/app/2630 Call of Duty)
| 1.3
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [Warfare](http://store.steampowered.com/app/7940 Call of Duty 4: Modern)
| 1.7.568
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#f8f8ff"
|  [Multiplayer](https://steamcommunity.com/app/10190 Call of Duty: Modern Warfare 2)
| 1.2.208
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [Ops](http://store.steampowered.com/app/10180 Call of Duty: Modern Warfare 2 Special)
| 1.1
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [War](http://store.steampowered.com/app/10090 Call of Duty: World at)
| 1.7.1263
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [1.6](http://store.steampowered.com/app/10 Counter-Strike)
| 1.6
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#e8e8ff"
|  [Offensive](http://store.steampowered.com/app/730 Counter-Strike: Global)
| >=  [2014](http://blog.counter-strike.net/index.php/2014/08/10222 Aug 27)
| No
| Any
| style="background-color:#abf8a1" | [<span title='See "Source Engine"'>Yes</span>](#Source_Engine.md)

|-style="background-color:#e8e8ff"
|  [Source](http://store.steampowered.com/app/240 Counter-Strike:)
| >=  [2013](http://store.steampowered.com/news/9893 Feb 5)
| No
| Any
| style="background-color:#abf8a1" | [<span title='See "Source Engine"'>Yes</span>](#Source_Engine.md)

|-style="background-color:#e8e8ff"
|  [Source](http://www.dayofdefeat.com Day of Defeat:)
| >=  [(5101))](http://store.steampowered.com/news/9221 1.0.0.46 (01:24:57 Oct 26 2012)
| No
| Any
| style="background-color:#abf8a1" | [<span title='See "Source Engine"'>Yes</span>](#Source_Engine.md)

|-style="background-color:#f8f8ff"
|  [Dystopia](http://www.dystopia-game.com)
| Build 4104
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#f8f8ff"
|  [Wars](http://steamcommunity.com/app/10000 Enemy Territory: Quake)
| 1.50
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#e8e8ff"
|  [ezQuake](http://ezquake.sf.net)
| >= 2.0 alpha
| No
| Any
| No

|-style="background-color:#f8f8ff"
|  [XIV](http://www.finalfantasyxiv.com Final Fantasy)
| 2016.11.11.0000.0000
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on Map. Identity: Map and Player">Yes</span>

|-style="background-color:#FFFFC0"
| Garry's Mod 11
| Build 5692
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#f8f8ff"
|  [IV](http://www.rockstargames.com/IV Grand Theft Auto)
|  [1.0.7.0](https://support.rockstargames.com/hc/en-us/articles/200145406--May-28-2010-Grand-Theft-Auto-IV-Patch-7-Title-Update-v-1-0-7-0-English-1-0-6-1-Russian-1-0-5-2-Japanese)
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [Andreas](https://www.rockstargames.com/sanandreas Grand Theft Auto: San)
| 1.0
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [V](http://www.rockstargames.com/GTAOnline Grand Theft Auto)
| 1.50 (Steam)  [1.38](https://support.rockstargames.com/hc/en-us/articles/115004482908) (Retail)
| No
| Windows
| style="background-color:#ddffdd" | <span title="Player nickname, vehicle, location and street">Identity only</span>

|-style="background-color:#f8f8ff"
|  [Wars](https://www.guildwars.com Guild)
| Build 36001
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on location + area">Partial context only</span>

|-style="background-color:#e8e8ff"
|  [2](https://www.guildwars2.com/ Guild Wars)
| >=  [2/26/13](https://forum-en.guildwars2.com/forum/info/news/Game-Update-Notes-February-26-2013 Build) <sub> [page](http://wiki.guildwars2.com/wiki/Mumble Official Wiki)</sub>
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Deathmatch](http://store.steampowered.com/app/320/ Half-Life 2:)
| >=  [(5101))](http://store.steampowered.com/news/9221 1.0.0.37 (01:24:57 Oct 26 2012)
| No
| Any
| style="background-color:#abf8a1" | [<span title='See "Source Engine"'>Yes</span>](#Source_Engine.md)

|-style="background-color:#e8e8ff"
|  [Insurgency](http://store.steampowered.com/app/222880/)
| ?
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#f8f8ff"
|  [Combat](http://store.steampowered.com/app/17700 Insurgency: Modern Infantry)
| Build 4044
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#f8f8ff"
|  [2](http://store.steampowered.com/app/8190 Just Cause)
| 1.0.0.2
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [Legends](http://leagueoflegends.com League of)
| 1.0.0.145
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address and port">Context only</span>

|-style="background-color:#f8f8ff"
|  [Dead](http://www.l4d.com Left 4)
|  [1.0.3.1](http://www.l4d.com/blog/post.php?id=20984)
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on Server ID. Identity: Host IP address and port, map name and player SteamID">Yes</span>

|-style="background-color:#f8f8ff"
|  [2](http://www.l4d.com Left 4 Dead)
|  [2.1.4.6](http://www.l4d.com/blog/post.php?id=22240)
| No
| Windows, Linux
| style="background-color:#abf8a1" | <span title="Context based on Server ID. Identity: Host IP address and port, server name, map name, player nickname and player SteamID">Yes</span>

|-style="background-color:#FFFFC0"
|  [Online](https://www.lotro.com Lord of the Rings)
|  [4](https://lotro-wiki.com/index.php/Patches Update) while the latest is  [18](https://lotro-wiki.com/index.php/Patches Update)
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on region and instance">Partial context only</span>

|-style="background-color:#e8e8ff"
|  [Minecraft](https://minecraft.net)
| >=  Beta 1.3
| Install the mod for  [Forge](https://github.com/zsawyer/MumbleLink) or  [Fabric.](https://github.com/magneticflux-/fabric-mumblelink-mod)
| Any
| style="background-color:#abf8a1" | Yes ( [moddable](http://www.minecraftforum.net/topic/217587-164-mod-mumblelink-forge-smp-lan-mumble-realism-directional-voip/#developmentAddons))

|-style="background-color:#e8e8ff"
|  [Minetest](http://www.minetest.net/)
| Any
| Install the  [mod](https://forum.minetest.net/viewtopic.php?f=53&t=21586 dedicated)
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Miscreated](http://store.steampowered.com/app/299740)
| >= Patch  [#34](http://miscreatedgame.com/news/patch-34)
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Dawn](https://www.gameconnect.net/projects/nucleardawn Nuclear)
| >=  [6.9](http://store.steampowered.com/news/9647)
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Arena](http://www.openarena.ws Open)
| >=  [0ee3960225](https://github.com/OpenArena/engine/commit/0ee3960225 commit)
| Set ''cl_useMumble'' to ''1''
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#f8f8ff"
|  [Live](https://www.quakelive.com Quake)
|  [1069](http://steamcommunity.com/games/282440/announcements/detail/876328108049672536)
| No
| Windows
| style="background-color:#abf8a1" | <span title="Context based on host IP address and port. Identity: Map and team">Yes</span>

|-style="background-color:#e8e8ff"
|  [Eclipse](http://redeclipse.net/ Red)
| Any
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Regnum-Online](https://www.championsofregnum.com)
| ?
| No
| Any
| No

|-style="background-color:#e8e8ff"
|  [Reaction](http://rq3.com/)
| Any
| Set ''cl_useMumble'' to ''1''
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Ethernet](http://ethernet.wasted.ch Revenge of the Cats:)
| >= prototype 1.6
| No
| Any
| No

|-style="background-color:#e8e8ff"
|  [Rods](http://www.rigsofrods.com Rigs of)
| >= 0.38.20
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#f8f8ff"
|  [League](https://www.rocketleaguegame.com/ Rocket)
|  [1.42](https://rocketleaguegame.com/news/patch-notes-v1-42)
| No
| Windows, Linux
| No

|-style="background-color:#e8e8ff"
|  [Sauerbraten](http://sauerbraten.org/)
| >=  [2008_06_17_ctf_edition](http://sauerbraten.org/docs/history.html#_2008_06_17_ctf_edition)
| No
| Any
| No

|-style="background-color:#f8f8ff"
|  [Staxel](http://playstaxel.com/)
| Any
| No
| Windows
| style="background-color:#abf8a1" | Yes

|-style="background-color:#f8f8ff"
|  [Rosa](http://subrosagame.com Sub)
| 0.07b
| No
| Windows
| No

|-style="background-color:#e8e8ff"
|  [2](http://www.teamfortress.com/ Team Fortress)
| >=  [(5101))](http://store.steampowered.com/news/9221 1.2.3.5 (01:24:57 Oct 26 2012)
| No
| Any
| style="background-color:#abf8a1" | [<span title='See "Source Engine"'>Yes</span>](#Source_Engine.md)

|-style="background-color:#e8e8ff"
|  [Tesseract](http://tesseract.gg)
| >= First Edition
| No
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Invasion](https://ufoai.org UFO: Alien)
| >=  [2.5](https://ufoai.org/wiki/Changelog/2.5)
| Set ''snd_mumble'' to ''1''
| Any
| style="background-color:#ddffdd" |  [only](https://github.com/ufoai/ufoai/blob/136e4441b489643d378357fbff5666d60bc916ed/src/client/sound/s_mumble.cpp#L86 Context)

|-style="background-color:#f8f8ff"
|  [(UT99)](http://store.steampowered.com/app/13240 Unreal Tournament)
| 436
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on server name">Partial context only</span>

|-style="background-color:#f8f8ff"
|  [2004](http://store.steampowered.com/app/13230 Unreal Tournament)
| Build 3369
| No
| Windows
| No

|-style="background-color:#f8f8ff"
|  [3](http://store.steampowered.com/app/13210 Unreal Tournament)
| 2.1
| No
| Windows
| No

|-style="background-color:#e8e8ff"
|  [Unvanquished](https://www.unvanquished.net/)
| Any
| Set ''cl_useMumble'' to ''1''
| Any
| style="background-color:#abf8a1" | Yes

|-style="background-color:#e8e8ff"
|  [Warsow](http://www.warsow.net/)
| >=  [0.6](http://www.warsow.net/forum/thread/t/191271#post-191271)<br>Improved >=  [1.0](http://www.warsow.net/forum/thread/t/206086#post-206086)
| Set ''cl_mumble'' to ''1''
| Any
| No

|-style="background-color:#f8f8ff"
|  [Territory](https://www.etlegacy.com/ Wolfenstein: Enemy)
| 2.60b
| No
| Windows
| style="background-color:#ddffdd" | <span title="Based on host IP address, map and team">Context only</span>

|-style="background-color:#f8f8ff"
|  [Warcraft](http://blizzard.com/games/wow World of)
| 7.0.3.22810
| No
| Windows
| style="background-color:#abf8a1"| <span title="Context based on Realm's name. Identity: Player's nickname">Yes</span>
|}

### Supported engines 

{|border="0" cellpadding="2" cellspacing="1" style="background:#e2e2e2;" class="sortable"
! Engine
! Version
! Action required
! Platform
! Extended support (Context, identity)

|-style="background-color:#e8e8ff"
|  [ioquake3](https://ioquake3.org)
| >=  [0ee3960225](https://github.com/ioquake/ioq3/commit/0ee3960225 commit)
| Set ''cl_useMumble'' to ''1''
| Any
| No

|-id="Source_Engine" style="background-color:#e8e8ff"
|  [Engine](http://source.valvesoftware.com Source)
| >=  [?](http://store.steampowered.com/news/9221)
| No
| Any
| style="background-color:#abf8a1" | <span title="Context based on Server ID. Identity: Universe, Account type, Account steam3ID, Instance, Team">Yes</span>

|-style="background-color:#e8e8ff"
|  [Generation](https://github.com/yEngine/YEng YEngine Next) (if using Y.mumble)
| >=  [b4011706e7](https://github.com/yEngine/YEng/commit/b4011706e7 commit)
| No
| Linux
| style="background-color:#abf8a1" | Yes
|}

## Manual positional audio plugin 

![Image](pos-audio-plugin.jpg)
In addition to the mentioned plugins, there is a special plugin called ''manual placement plugin''. It does not require a game, instead you can configure the plugin itself to set your own position from which other people in the same channel can hear you.

'''1''' Set yourself on the canvas from where others should hear you. '''Make sure to choose a position other than 0, 0, 0''' or you won't hear or send positionally.

'''2''' Set your own orientation where you want your virtual avatar to look at on a 360° Scale.

'''3''' Set your own azimuth (if you look up or down while you talk).

'''4''' Set the context of your avatar. Only the people with the same context will hear you positionally.

'''5''' Set the identity.

'''6''' Link or unlink the plugin to transfer the settings to the server for processing.

'''7''' Enable or disable the plugin.

'''8''' Separate the plugin settings window. This is useful to change the positional audio settings without keeping the Mumble settings window opened.

'''9''' Reset values for all settings.

'''10''' Close the window.


