'''NOTE: Please go to  [website](https://www.mumble.info/documentation/user/in-game-overlay/ the new documentation on our) instead. The documentation here is now obsolete.'''

---


![Image](overlay123_s.png)

Mumble provides overlay support for Games using Direct3D 9/10/11 or OpenGL on Windows and OpenGL using games on Linux/OSX.
<div style="clear:left;"></div>

## Incompatible games 
Games that are known to have '''issues''' with the Mumble overlay:
{|class="sortable" style="margin:4px; background-color:#eeeeee; border:1px;"
!style="width:120px; text-align:left;"|Game
!style="width:50px; text-align:left;"|API
!style="text-align:left;"|Comments
!style="width:65px;"|Fixed in
|- style="background-color:#dddddd;"
|| Warcraft 3
|| any
|| Fixed in the latest 1.3.0 snapshot builds
|| <div style="font-weight:bold;color:#338833;">1.3.0</div>
|- style="background-color:#dddddd;"
|| Combat Arms
|| unknown
|| overlay causes CA to crash after map changes;<br/> overlay will not display unless one joins a server and then leaves it
|| unknown
|- style="background-color:#dddddd;"
|| Vanguard
|| n/a
|| crashes to desktop when overlay is enabled
|| unknown
|- style="background-color:#dddddd;"
|| Call of Duty 4
|| n/a
|| PunkBuster kick playing online
|| unknown
|- style="background-color:#dddddd;"
|| Call of Duty 2
|| n/a
|| PunkBuster kick playing online
|| unknown
|- style="background-color:#dddddd;"
|| Killing Floor
|| n/a
|| the game will crash when changing resolutions or going into fullscreen mode
|| unknown
|- style="background-color:#dddddd;"
|| Red Orchestra
|| n/a
|| the game will crash when changing resolutions or going into fullscreen mode
|| unknown
|- style="background-color:#dddddd;"
|| H1Z1
|| n/a
|| game crashes at startup
|| unknown
|- style="background-color:#dddddd;"
|}

Overlay availability by API, OS and CPU-architecture:

{|class="sortable" style="margin:4px; background-color:#eeeeee;"
!style="width:150px; text-align:left;"|API
!style="width:150px; text-align:left;"|CPU-Architecture
!style="width:150px; text-align:left;"|Platform
!style="text-align:left;"|Status
|- style="background-color:#dddddd;"
| rowspan="2" | OpenGL
|| x86
| rowspan="2" | Windows, Linux, Mac
|| <div style="color:#338833;">fully works in 1.2.5</div>
|-
| x64
|| <div style="color:#338833;">fully works</div>
|- style="background-color:#dddddd;"
| rowspan="2" | Vulkan|| x86
| rowspan="2" | Windows, Linux, Mac
|| <div style="color:#338833;">fully works in 1.3.0</div>
|-
| x64
|| <div style="color:#338833;">fully works in 1.3.0</div>
|- style="background-color:#dddddd;"
| rowspan="2" | Direct3D 9
|| x86
| rowspan="2" | Windows
|| <div style="color:#338833;">fully works in 1.2.5</div>
|-
| x64
|| <div style="color:#338833;">fully works in 1.3.0</div>
|- style="background-color:#dddddd;"
| rowspan="2" | Direct3D 9ex
|| x86
| rowspan="2" | Windows
|| <div style="color:#338833;">fully works in 1.2.5</div>
|-
|| x64
|| <div style="color:#338833;">fully works in 1.3.0</div>
|- style="background-color:#dddddd;"
| rowspan="2" | Direct3D 10
|| x86
| rowspan="2" | Windows
|| <div style="color:#338833;">fully works in 1.2.5</div>
|-
|| x64
|| <div style="color:#338833;">fully works in 1.3.0</div>
|- style="background-color:#dddddd;"
| rowspan="2" | Direct3D 11
|| x86
| rowspan="2" | Windows
|| <div style="color:#226622;">fully works in 1.3.0</div>
|-
|| x64
|| <div style="color:#226622;">fully works in 1.3.0</div>
|- style="background-color:#dddddd;"
| rowspan="2" | Direct3D 12
|| x86
| rowspan="2" | Windows
|| <div style="color:#883333;">does not display</div>
|-
|| x64
|| <div style="color:#883333;">does not display</div>
|-
|}

## Disabling the overlay for a particular game 
If you would like to disable the overlay for a certain game (because you do not want it in that particular game, or that game has issues with the overlay), and do not want to disable the overlay altogether, put a file named ''nooverlay'' (without any extensions) in the same folder as the game executable is located. This will tell Mumble that you do not want the overlay in this particular game. Current releases of Mumble also support black-/whitelisting from the client itself (Settings->Overlay, make sure [advanced](Advanced client configuration.md) is checked).

![Image](mumble_overlay_blacklist_win7.png)

## Overlay on GNU/Linux 

As described in  [README](https://github.com/mumble-voip/mumble/blob/master/README.Linux our linux) to use the Overlay in an application you start hat appliaction through the mumble-overlay binary:

 mumble-overlay gamename

### Manual approach 

Using this preload command should only be necessary if you did not install a binary package (and thus do not have ''mumble-overlay'' available):

As described in  [README](https://github.com/mumble-voip/mumble/blob/master/README.md our) to use the Overlay in an application you preload it.

 LD_PRELOAD=/path/to/libmumble.so.1.1 gamename


