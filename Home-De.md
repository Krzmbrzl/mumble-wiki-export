__NOTOC____NOEDITSECTION__
<div style="border: 1px solid #C9C9C9; padding: .7em; background-color:#F8F8F8; margin-top: 0;">
<center>
'''Kommuniziere mit Mumble in Kristallklaren Sound und niedriger Verzögerung'''</center>
</div>

<div id="mum-intro-userroles">
{|class="mum-intro-userrole" style="width:33%; min-width:280px; float:left; margin:0px; padding:8px 8px 0px 0px; border-spacing:0px; background-color:transparent;"
|style="border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|
{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:150%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Für User</h2>
|-
|style="color:#000000;"|
<ul>
<li>Niedrige Latenz - Optimal zum Sprechen und Spielen</li>
<li>Bleib Privat und Sicher
<ul>
  <li>Verschlüsselte Kommunikation</li>
  <li> [authentication](https://en.wikipedia.org/wiki/Public-key_cryptography Public/private-key) Standardmäßig</li>
</ul></li>
<li>[Optimiert für Spiele](Features#Persistency.md)</li>
<li>Für Spieler:
<ul>
 <li>[In-game Overlay](Overlay.md) - sehe wer Spricht</li>
 <li>[Positional audio](Positional-Audio.md) - hör die Spieler, vo da wo sie sich befinden</li>
</ul></li>
<li>[Wizards](Features#Wizards.md), welche dir helfen z.b. dein Mikrofon zu Konfigurieren</li>
</ul>
|-
|}
|}

{|class="mum-intro-userrole" style="width:33%; min-width:280px; float:left; margin:0px; padding:8px 8px 0px 0px; border-spacing:0px; background-color:transparent;"
|style="border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|
{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:150%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Für Admins</h2>
|-
|style="color:#000000;"|
<ul>
<li> [Software](https://github.com/mumble-voip/mumble/blob/master/LICENSE Kostenlose) - kein Lizenzaufwand</li>
<li> [Source](https://github.com/mumble-voip/mumble Open) - open in security and technology, and open to extendibility</li>
<li>[Extensive user permission system (ACL)](Features#Access_Control_Groups.md)</li>
<li>Erweiterbar dank [Ice middleware](Ice.md)
<ul>
<li>[Web interfaces](3rd_Party_Applications#Web-Interfaces.md) - freie Auswahl an Bestehender Software</li>
<li>[Channel viewers](3rd_Party_Applications#Channel_Viewers.md) - ohne direkten Zugriff auf die Ice schnitstelle, falls der Hoster [CVP](Channel Viewer Protocol.md) unterstützt.</li>
<li>[[Authenticators]] - Damit können sich user ihren Nutzernamen schützen. </li>
<li>Eigene Chat Befehle und Kontext Menüs</li>
</ul>
</li>
</ul>
|-
|}
|}

{|class="mum-intro-userrole" style="width:34%; min-width:280px; float:left; margin:0px; padding:8px 0px 0px 0px; border-spacing:0px; background-color:transparent;"
|style="border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|
{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:150%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Für Hoster</h2>
|-
|style="color:#000000;"|
<ul>
<li> [software](https://github.com/mumble-voip/mumble/blob/master/LICENSE Free) - Keine Lizenzgebühren</li>
<li>Automatisierte Administration dank der [[Ice]] Software</li>
<li>[Verbraucht kaum Ressourcen](Commercial Hosting.md)</li>
<li>Sehr Stabile Server Software</li>
<li>Freie auswahl der [server software](3rd_Party_Applications#Server_Software.md)</li>
<li>Eigene Weboberflächen für die User dank Ice
<ul><li>Oder verwende einfach eins der Bestehenden [web interfaces](3rd_Party_Applications#Web-Interfaces.md)</li></ul>
</li>
<li>Stellen sie usern channel viewer data ([CVP](Channel Viewer Protocol.md)) bereit, ohne die Kontrolle zu verlieren
<ul>
<li>Oder geben sie ihren Kunden die Kontrolle dank des Ice Interfaces.</li>
</ul>
</li>
</ul>
|-
|}
|}
</div>

{| style="border: 0; margin: 0; padding: 0; width: 100%; background: transparent;"
|-
|style="vertical-align:top; padding-right: .6em;"|

{|style="border-spacing:0px; margin:8px 8px 8px 0px; width:100%;"
|style="width:55%; border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|
{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:200%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Download Mumble</h2>
|-
|style="color:#000;"|
<mumblelatest></mumblelatest>
|-
|}
|}

{|style="border-spacing:0px; margin:8px 8px 8px 0px; width:100%;"
|style="width:55%; border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|
{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:200%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Third Party Applications</h2>
|-
|style="color:#000;padding-left:30px;"|

### Alternative Clients 

Falls du ein Betriebsystem nutzt, welches nicht offiziell unterstützt wird, oder falls du nach einer alterative zu den offiziellen Clients suchst, findest du hier eine Übersicht der empfohlenen Clients:

{| class="wikitable" style="min-width:450px;"
|-
!style="text-align:left;"| Name
!style="text-align:left;"| OS
!style="text-align:left;"| Links
|-
| Mumla  || Android ||  [F-Droid](https://f-droid.org/packages/se.lublin.mumla/)
|-
| Plumble || Android ||  [Play](https://play.google.com/store/apps/details?id=com.morlunk.mumbleclient.free Google),  [F-Droid](https://f-droid.org/repository/browse/?fdid=com.morlunk.mumbleclient)
|-
| Mumblefy || iOS ||  [Store](https://itunes.apple.com/dk/app/mumblefy/id858752232?mt=8 App)
|}

### Other Third Party Software 
Zusatzsoftware für Mumble wie beispielsweise Musikbots, findest du hier: [Third Party Applications](3rd Party Applications.md)

|-
|}
|}

{|style="border-spacing:0px; margin:8px 8px 8px 0px; width:100%;"
|style="width:55%; border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|

{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:150%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Mach mit!</h2>
|-
|style="color:#000;"|<big style="width:50%; min-width:300px; float:left;">
* <span class="plainlinks"> [Forums](http://forums.mumble.info/ Discussion)</span>
* <span class="plainlinks"> [freenode](irc://irc.freenode.org/mumble #mumble on)</span>
</big><div style="width:50%; float:left;">
# Socialnetworks
</div>
|-
|}

|}

{|style="border-spacing:0px; margin:8px 8px 8px 0px; width:100%;"
|style="width:55%; border:1px solid #C9C9C9; background:#F8F8F8; vertical-align:top; color:#000;"|
{|width="100%" cellpadding="2" cellspacing="5" style="vertical-align:top; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:150%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; color:#000; padding:0.2em 0.4em;">Neuigkeiten & Blog</h2>
|-
|style="color:#000;"|
<mumbleblog num="4"></mumbleblog>
|-
|}
|}

|style="vertical-align:top; width: 320px;"|

{|width="100%" cellpadding="2" style="width:100%; border-spacing:5px; margin:8px 8px 8px 0px; vertical-align:top; border:1px solid #C9C9C9; color:#000; background:#F8F8F8;"
! <h2 style="margin:0; background:#F0F0F0; font-size:150%; font-weight:bold; border:1px solid #A4A4A4; text-align:left; 

color:#000; padding:0.2em 0.4em;">Documentation</h2>
|-
|style="color:#000;"|<big>
:* [Installation](Installing Mumble.md)
:* [[FAQ]]
:* [[Features]]
:* [Geplante features](Upcoming.md)
:* [[Contributing]]
:* [[Development]]
: &nbsp;
:'''Client'''
:* [Positional audio plugins](Games.md)
:* [[Skins]]
:* <span class="plainlinks"> [Statistics](http://stats.mumble.info Usage)</span>
: &nbsp;
:'''Server'''
:* [Murmur einrichten](Running Murmur.md)
:* [ACL & Groups](ACL and Groups.md)
:* [[Commercial Hosting]]
:* [[DBus]] and [[Ice]]
</big>
|-
|}

|}

