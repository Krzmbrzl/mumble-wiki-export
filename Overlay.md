**NOTE: Please go to [the new documentation on our
website](https://www.mumble.info/documentation/user/in-game-overlay/)
instead. The documentation here is now obsolete.**

\---

![overlay123_s.png](overlay123_s.png "overlay123_s.png") The overlay is
a feature that will overlay the nicknames of users in the channel or
users talking over your currently running game. That means you will be
able to see who's listening and talking ingame.

Mumble provides overlay support for Games using Direct3D 9/10/11 or
OpenGL on Windows and OpenGL using games on Linux/OSX.

<div style="clear:left;">

</div>

## Incompatible games

Games that are known to have **issues** with the Mumble overlay:

<table>
<thead>
<tr class="header">
<th><p>Game</p></th>
<th><p>API</p></th>
<th><p>Comments</p></th>
<th><p>Fixed in</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Warcraft 3</p></td>
<td><p>any</p></td>
<td><p> Fixed in the latest 1.3.0 snapshot builds</p></td>
<td><div style="font-weight:bold;color:#338833;">
<p>1.3.0</p>
</div></td>
</tr>
<tr class="even">
<td><p>Combat Arms</p></td>
<td><p>unknown</p></td>
<td><p> overlay causes CA to crash after map changes;<br />
overlay will not display unless one joins a server and then leaves it</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="odd">
<td><p>Vanguard</p></td>
<td><p>n/a</p></td>
<td><p> crashes to desktop when overlay is enabled</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="even">
<td><p>Call of Duty 4</p></td>
<td><p>n/a</p></td>
<td><p> PunkBuster kick playing online</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="odd">
<td><p>Call of Duty 2</p></td>
<td><p>n/a</p></td>
<td><p> PunkBuster kick playing online</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="even">
<td><p>Killing Floor</p></td>
<td><p>n/a</p></td>
<td><p> the game will crash when changing resolutions or going into fullscreen mode</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="odd">
<td><p>Red Orchestra</p></td>
<td><p>n/a</p></td>
<td><p> the game will crash when changing resolutions or going into fullscreen mode</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="even">
<td><p>H1Z1</p></td>
<td><p>n/a</p></td>
<td><p> game crashes at startup</p></td>
<td><p>unknown</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Overlay availability by API, OS and CPU-architecture:

<table>
<thead>
<tr class="header">
<th><p>API</p></th>
<th><p>CPU-Architecture</p></th>
<th><p>Platform</p></th>
<th><p>Status</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OpenGL</p></td>
<td><p>x86</p></td>
<td><p>Windows, Linux, Mac</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.2.5</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#338833;">
<p>fully works</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Vulkan</p></td>
<td><p>x86</p></td>
<td><p>Windows, Linux, Mac</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.3.0</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.3.0</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Direct3D 9</p></td>
<td><p>x86</p></td>
<td><p>Windows</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.2.5</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.3.0</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Direct3D 9ex</p></td>
<td><p>x86</p></td>
<td><p>Windows</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.2.5</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.3.0</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Direct3D 10</p></td>
<td><p>x86</p></td>
<td><p>Windows</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.2.5</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#338833;">
<p>fully works in 1.3.0</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Direct3D 11</p></td>
<td><p>x86</p></td>
<td><p>Windows</p></td>
<td><div style="color:#226622;">
<p>fully works in 1.3.0</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#226622;">
<p>fully works in 1.3.0</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Direct3D 12</p></td>
<td><p>x86</p></td>
<td><p>Windows</p></td>
<td><div style="color:#883333;">
<p>does not display</p>
</div></td>
</tr>
<tr class="even">
<td><p>x64</p></td>
<td><div style="color:#883333;">
<p>does not display</p>
</div></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Disabling the overlay for a particular game

If you would like to disable the overlay for a certain game (because you
do not want it in that particular game, or that game has issues with the
overlay), and do not want to disable the overlay altogether, put a file
named *nooverlay* (without any extensions) in the same folder as the
game executable is located. This will tell Mumble that you do not want
the overlay in this particular game. Current releases of Mumble also
support black-/whitelisting from the client itself (Settings-\>Overlay,
make sure [advanced](Advanced_client_configuration "wikilink") is
checked).

![<File:Mumble_Overlay_Blacklist_Win7.png>](Mumble_Overlay_Blacklist_Win7.png
"File:Mumble_Overlay_Blacklist_Win7.png")

## Overlay on GNU/Linux

As described in [our linux
README](https://github.com/mumble-voip/mumble/blob/master/README.Linux)
to use the Overlay in an application you start hat appliaction through
the mumble-overlay binary:

`mumble-overlay gamename`

### Manual approach

Using this preload command should only be necessary if you did not
install a binary package (and thus do not have *mumble-overlay*
available):

As described in [our
README](https://github.com/mumble-voip/mumble/blob/master/README.md) to
use the Overlay in an application you preload it.

`LD_PRELOAD=/path/to/libmumble.so.1.1 gamename`

[Category:Documentation
English](Category:Documentation_English "wikilink")