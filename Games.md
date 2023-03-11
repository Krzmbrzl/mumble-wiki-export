**NOTE: Please go to [the new documentation on our
website](https://www.mumble.info/documentation/user/positional-audio/)
instead. The documentation here is now obsolete.**

\---

# Overlay

Our overlay is not technically game-specific but
rendering-engine-specific. Thus it works for all games using supported
rendering APIs.

For more information on the overlay, see [the respective page about the
Overlay](Overlay "wikilink").

# Positional audio

![Positional_Audio.gif](Positional_Audio.gif "Positional_Audio.gif")
Please note that Mumble works with all games as a regular voice chat
application. Those listed on this page are the games for which we are
providing [positional sound](Positional-Audio "wikilink") support, so
that the voice of your teammates comes from their direction in game.

This feature **can be enabled as follows**:

  - 1.) Check "[Advanced](Advanced_client_configuration "wikilink")" in
    the *Configure|Settings* menu
  - 2.) Go to *Plugins* and check "Link to Game and Transmit Position"

If you deselected *Enable positional audio* during setup you have to
re-enable it in the wizard.

**Just because your game says it is a different version from the plugin
does not necessarily mean that the plugin will not work.**

It is possible that some plugins are outdated in the current release; in
that case please check the lists below.

If there is no update for the plugin, please report it
[here](https://github.com/mumble-voip/mumble/issues).

For additional info on what positional audio is and how it works in
Mumble, see [here](Positional-Audio "wikilink").

If you want to add support for a game and you are able to modify the
source of this game you can use the [Link](Link "wikilink") plugin. If
you cannot modify the source of the game you want to add, [this
guide](Pluginguide "wikilink") should help. For an overall look at
retrieving positional data from a game, see
[here](HackPositionalAudio "wikilink").

<div style="clear:left;">

</div>

## Supported games

The following table displays which games positional audio is available
for, from which game version on (/for which version), for what platform
and if extended support is available.

Games that provide native positional data via the Link plugin are marked
in <span style="background-color:#e8e8ff">blue</span> (that means they
won’t get outdated). Outdated plugins are marked in
<span style="background-color:#FFFFC0">yellow</span>.
*No* means that the games don't use the extended positional audio
features that were introduced with Mumble 1.2. Move the pointer over to
see more info about the extended support for a specific plugin (if
available).

**Note:** Windows plugins work on Wine\!

<table>
<thead>
<tr class="header">
<th><p>Game</p></th>
<th><p>Version</p></th>
<th><p>Action required</p></th>
<th><p>Platform</p></th>
<th><p>Extended support (Context, identity)</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/17510">Age of Chivalry</a></p></td>
<td><p>Build 4104</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.arma2.com">ArmA 2</a></p></td>
<td><p><a href="http://steamcommunity.com/games/arma2/announcements/detail/1027014441254296137">1.08</a> while the latest is <a href="http://steamcommunity.com/games/arma2/announcements/detail/1370438673676192803">1.10</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.arma2.com">ArmA 2: Operation Arrowhead</a></p></td>
<td><p>&gt;= 1.60</p></td>
<td><p>Install the <a href="https://dev.withsix.com/projects/mumblelink">dedicated mod</a></p></td>
<td><p>Windows</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://arma3.com">Arma 3</a></p></td>
<td><p>&gt;= 0.5</p></td>
<td><p>Install the <a href="https://dev.withsix.com/projects/mumblelink">dedicated mod</a></p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://www.assettocorsa.it/home-ac/">Assetto Corsa</a></p></td>
<td><p>CSP &gt;= 0.1.77</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.battlefield.com">Battlefield 1</a></p></td>
<td><p><a href="https://www.battlefield.com/news/update-notes/spring-update">1.0.49.52296</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on server name. Identity: Team, Squad and Squad leader">Yes</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.battlefield.com/battlefield-1942">Battlefield 1942</a></p></td>
<td><p>1.61b</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.battlefield.com/battlefield-2">Battlefield 2</a></p></td>
<td><p>1.50</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on host IP address and port. Identity: Host IP address and port, Commander, Squad Leader, Squad, Team, On VoIP, On VoIP com, Target squad ID">Yes</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.battlefield.com/battlefield-2142">Battlefield 2142</a></p></td>
<td><p><a href="http://largedownloads.ea.com/pub/patches/BF2142/">1.51</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on host IP address and port. Identity: Host IP address and port, Team ID, Squad ID, Commander, Squad Leader, Target squad ID, On VoIP, On VoIP com, Player">Yes</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.battlefield.com/battlefield3">Battlefield 3</a></p></td>
<td><p>Build 1147186 - End Game DLC</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on host IP address and port. Identity: Team, Squad, Squad Leader">Yes</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.battlefield.com/battlefield4">Battlefield 4</a></p></td>
<td><p>1.8.2.48475</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on Server ID. Identity: Host IP address and port, Team, Squad, Squad Leader, Squad State">Yes</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.battlefield.com/battlefield-bad-company-2-vietnam">Battlefield Bad Company 2</a></p></td>
<td><p>Build 795745</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.battlefieldheroes.com">Battlefield Heroes</a></p></td>
<td><p>?</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/362890">Black Mesa</a></p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p><a href="#Source_Engine" title="wikilink"><span title='See "Source Engine"'>Yes</span></a></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://borderlandsthegame.com">Borderlands</a></p></td>
<td><p><a href="http://borderlands.wikia.com/wiki/Patch_1.4.0">1.4.0</a> while the latest is <a href="http://borderlands.wikia.com/wiki/Patch_1.4.1">1.4.1</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/49520">Borderlands 2</a></p></td>
<td><p><a href="http://borderlands.wikia.com/wiki/Patch_1.8.X_(Borderlands_2)">1.8.3</a> while the latest is <a href="http://borderlands.wikia.com/wiki/Patch_1.8.X_(Borderlands_2)">1.8.4</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Character name">Identity only</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://breachgame.com">Breach</a></p></td>
<td><p>1.1.0</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/2630">Call of Duty 2</a></p></td>
<td><p>1.3</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/7940">Call of Duty 4: Modern Warfare</a></p></td>
<td><p>1.7.568</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="https://steamcommunity.com/app/10190">Call of Duty: Modern Warfare 2 Multiplayer</a></p></td>
<td><p>1.2.208</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/10180">Call of Duty: Modern Warfare 2 Special Ops</a></p></td>
<td><p>1.1</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/10090">Call of Duty: World at War</a></p></td>
<td><p>1.7.1263</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/10">Counter-Strike 1.6</a></p></td>
<td><p>1.6</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/730">Counter-Strike: Global Offensive</a></p></td>
<td><p>&gt;= <a href="http://blog.counter-strike.net/index.php/2014/08/10222">Aug 27 2014</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p><a href="#Source_Engine" title="wikilink"><span title='See "Source Engine"'>Yes</span></a></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/240">Counter-Strike: Source</a></p></td>
<td><p>&gt;= <a href="http://store.steampowered.com/news/9893">Feb 5 2013</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p><a href="#Source_Engine" title="wikilink"><span title='See "Source Engine"'>Yes</span></a></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.dayofdefeat.com">Day of Defeat: Source</a></p></td>
<td><p>&gt;= <a href="http://store.steampowered.com/news/9221">1.0.0.46 (01:24:57 Oct 26 2012 (5101))</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p><a href="#Source_Engine" title="wikilink"><span title='See "Source Engine"'>Yes</span></a></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.dystopia-game.com">Dystopia</a></p></td>
<td><p>Build 4104</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://steamcommunity.com/app/10000">Enemy Territory: Quake Wars</a></p></td>
<td><p>1.50</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://ezquake.sf.net">ezQuake</a></p></td>
<td><p>&gt;= 2.0 alpha</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.finalfantasyxiv.com">Final Fantasy XIV</a></p></td>
<td><p>2016.11.11.0000.0000</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on Map. Identity: Map and Player">Yes</span></p></td>
</tr>
<tr class="odd">
<td><p>Garry's Mod 11</p></td>
<td><p>Build 5692</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.rockstargames.com/IV">Grand Theft Auto IV</a></p></td>
<td><p><a href="https://support.rockstargames.com/hc/en-us/articles/200145406--May-28-2010-Grand-Theft-Auto-IV-Patch-7-Title-Update-v-1-0-7-0-English-1-0-6-1-Russian-1-0-5-2-Japanese">1.0.7.0</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://www.rockstargames.com/sanandreas">Grand Theft Auto: San Andreas</a></p></td>
<td><p>1.0</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.rockstargames.com/GTAOnline">Grand Theft Auto V</a></p></td>
<td><p>1.50 (Steam) <a href="https://support.rockstargames.com/hc/en-us/articles/115004482908">1.38</a> (Retail)</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Player nickname, vehicle, location and street">Identity only</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="https://www.guildwars.com">Guild Wars</a></p></td>
<td><p>Build 36001</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on location + area">Partial context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.guildwars2.com/">Guild Wars 2</a></p></td>
<td><p>&gt;= <a href="https://forum-en.guildwars2.com/forum/info/news/Game-Update-Notes-February-26-2013">Build 2/26/13</a> <sub><a href="http://wiki.guildwars2.com/wiki/Mumble">Official Wiki page</a></sub></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/320/">Half-Life 2: Deathmatch</a></p></td>
<td><p>&gt;= <a href="http://store.steampowered.com/news/9221">1.0.0.37 (01:24:57 Oct 26 2012 (5101))</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p><a href="#Source_Engine" title="wikilink"><span title='See "Source Engine"'>Yes</span></a></p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/222880/">Insurgency</a></p></td>
<td><p>?</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/17700">Insurgency: Modern Infantry Combat</a></p></td>
<td><p>Build 4044</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/8190">Just Cause 2</a></p></td>
<td><p>1.0.0.2</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://leagueoflegends.com">League of Legends</a></p></td>
<td><p>1.0.0.145</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address and port">Context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.l4d.com">Left 4 Dead</a></p></td>
<td><p><a href="http://www.l4d.com/blog/post.php?id=20984">1.0.3.1</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on Server ID. Identity: Host IP address and port, map name and player SteamID">Yes</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.l4d.com">Left 4 Dead 2</a></p></td>
<td><p><a href="http://www.l4d.com/blog/post.php?id=22240">2.1.4.6</a></p></td>
<td><p>No</p></td>
<td><p>Windows, Linux</p></td>
<td><p><span title="Context based on Server ID. Identity: Host IP address and port, server name, map name, player nickname and player SteamID">Yes</span></p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.lotro.com">Lord of the Rings Online</a></p></td>
<td><p><a href="https://lotro-wiki.com/index.php/Patches">Update 4</a> while the latest is <a href="https://lotro-wiki.com/index.php/Patches">Update 18</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on region and instance">Partial context only</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="https://minecraft.net">Minecraft</a></p></td>
<td><p>&gt;= Beta 1.3</p></td>
<td><p>Install the mod for <a href="https://github.com/zsawyer/MumbleLink">Forge</a> or <a href="https://github.com/magneticflux-/fabric-mumblelink-mod">Fabric.</a></p></td>
<td><p>Any</p></td>
<td><p>Yes (<a href="http://www.minecraftforum.net/topic/217587-164-mod-mumblelink-forge-smp-lan-mumble-realism-directional-voip/#developmentAddons">moddable</a>)</p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.minetest.net/">Minetest</a></p></td>
<td><p>Any</p></td>
<td><p>Install the <a href="https://forum.minetest.net/viewtopic.php?f=53&amp;t=21586">dedicated mod</a></p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/299740">Miscreated</a></p></td>
<td><p>&gt;= Patch <a href="http://miscreatedgame.com/news/patch-34">#34</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.gameconnect.net/projects/nucleardawn">Nuclear Dawn</a></p></td>
<td><p>&gt;= <a href="http://store.steampowered.com/news/9647">6.9</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.openarena.ws">Open Arena</a></p></td>
<td><p>&gt;= <a href="https://github.com/OpenArena/engine/commit/0ee3960225">commit 0ee3960225</a></p></td>
<td><p>Set <em>cl_useMumble</em> to <em>1</em></p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.quakelive.com">Quake Live</a></p></td>
<td><p><a href="http://steamcommunity.com/games/282440/announcements/detail/876328108049672536">1069</a></p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on host IP address and port. Identity: Map and team">Yes</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://redeclipse.net/">Red Eclipse</a></p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.championsofregnum.com">Regnum-Online</a></p></td>
<td><p>?</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://rq3.com/">Reaction</a></p></td>
<td><p>Any</p></td>
<td><p>Set <em>cl_useMumble</em> to <em>1</em></p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="http://ethernet.wasted.ch">Revenge of the Cats: Ethernet</a></p></td>
<td><p>&gt;= prototype 1.6</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.rigsofrods.com">Rigs of Rods</a></p></td>
<td><p>&gt;= 0.38.20</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.rocketleaguegame.com/">Rocket League</a></p></td>
<td><p><a href="https://rocketleaguegame.com/news/patch-notes-v1-42">1.42</a></p></td>
<td><p>No</p></td>
<td><p>Windows, Linux</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://sauerbraten.org/">Sauerbraten</a></p></td>
<td><p>&gt;= <a href="http://sauerbraten.org/docs/history.html#_2008_06_17_ctf_edition">2008_06_17_ctf_edition</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://playstaxel.com/">Staxel</a></p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://subrosagame.com">Sub Rosa</a></p></td>
<td><p>0.07b</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="http://www.teamfortress.com/">Team Fortress 2</a></p></td>
<td><p>&gt;= <a href="http://store.steampowered.com/news/9221">1.2.3.5 (01:24:57 Oct 26 2012 (5101))</a></p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p><a href="#Source_Engine" title="wikilink"><span title='See "Source Engine"'>Yes</span></a></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://tesseract.gg">Tesseract</a></p></td>
<td><p>&gt;= First Edition</p></td>
<td><p>No</p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="even">
<td><p><a href="https://ufoai.org">UFO: Alien Invasion</a></p></td>
<td><p>&gt;= <a href="https://ufoai.org/wiki/Changelog/2.5">2.5</a></p></td>
<td><p>Set <em>snd_mumble</em> to <em>1</em></p></td>
<td><p>Any</p></td>
<td><p><a href="https://github.com/ufoai/ufoai/blob/136e4441b489643d378357fbff5666d60bc916ed/src/client/sound/s_mumble.cpp#L86">Context only</a></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/13240">Unreal Tournament (UT99)</a></p></td>
<td><p>436</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on server name">Partial context only</span></p></td>
</tr>
<tr class="even">
<td><p><a href="http://store.steampowered.com/app/13230">Unreal Tournament 2004</a></p></td>
<td><p>Build 3369</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://store.steampowered.com/app/13210">Unreal Tournament 3</a></p></td>
<td><p>2.1</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.unvanquished.net/">Unvanquished</a></p></td>
<td><p>Any</p></td>
<td><p>Set <em>cl_useMumble</em> to <em>1</em></p></td>
<td><p>Any</p></td>
<td><p>Yes</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://www.warsow.net/">Warsow</a></p></td>
<td><p>&gt;= <a href="http://www.warsow.net/forum/thread/t/191271#post-191271">0.6</a><br />
Improved &gt;= <a href="http://www.warsow.net/forum/thread/t/206086#post-206086">1.0</a></p></td>
<td><p>Set <em>cl_mumble</em> to <em>1</em></p></td>
<td><p>Any</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p><a href="https://www.etlegacy.com/">Wolfenstein: Enemy Territory</a></p></td>
<td><p>2.60b</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Based on host IP address, map and team">Context only</span></p></td>
</tr>
<tr class="odd">
<td><p><a href="http://blizzard.com/games/wow">World of Warcraft</a></p></td>
<td><p>7.0.3.22810</p></td>
<td><p>No</p></td>
<td><p>Windows</p></td>
<td><p><span title="Context based on Realm's name. Identity: Player's nickname">Yes</span></p></td>
</tr>
</tbody>
</table>

### Supported engines

| Engine                                                                         | Version                                                                    | Action required            | Platform | Extended support (Context, identity)                                                                                    |
| ------------------------------------------------------------------------------ | -------------------------------------------------------------------------- | -------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------- |
| [ioquake3](https://ioquake3.org)                                               | \>= [commit 0ee3960225](https://github.com/ioquake/ioq3/commit/0ee3960225) | Set *cl_useMumble* to *1* | Any      | No                                                                                                                      |
| [Source Engine](http://source.valvesoftware.com)                               | \>= [?](http://store.steampowered.com/news/9221)                           | No                         | Any      | <span title="Context based on Server ID. Identity: Universe, Account type, Account steam3ID, Instance, Team">Yes</span> |
| [YEngine Next Generation](https://github.com/yEngine/YEng) (if using Y.mumble) | \>= [commit b4011706e7](https://github.com/yEngine/YEng/commit/b4011706e7) | No                         | Linux    | Yes                                                                                                                     |

## Manual positional audio plugin

![POS-Audio-plugin.jpg](POS-Audio-plugin.jpg "POS-Audio-plugin.jpg") In
addition to the mentioned plugins, there is a special plugin called
*manual placement plugin*. It does not require a game, instead you can
configure the plugin itself to set your own position from which other
people in the same channel can hear you.

**1** Set yourself on the canvas from where others should hear you.
**Make sure to choose a position other than 0, 0, 0** or you won't hear
or send positionally.

**2** Set your own orientation where you want your virtual avatar to
look at on a 360° Scale.

**3** Set your own azimuth (if you look up or down while you talk).

**4** Set the context of your avatar. Only the people with the same
context will hear you positionally.

**5** Set the identity.

**6** Link or unlink the plugin to transfer the settings to the server
for processing.

**7** Enable or disable the plugin.

**8** Separate the plugin settings window. This is useful to change the
positional audio settings without keeping the Mumble settings window
opened.

**9** Reset values for all settings.

**10** Close the window.

[Category:Documentation
English](Category:Documentation_English "wikilink")