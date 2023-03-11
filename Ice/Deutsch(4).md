Mumur unterstützt Remote scripting mit [ZeroC
ICE](http://www.zeroc.com/), einem RPC Mechanismus.

Es gibt C++, Java, .NET, Python, PHP and Ruby Unterstützungen für alle
Platformen (Win32, Linux and OSX).

Ice kann auch über ein Netzwerk betrieben werden, somit kann eine
Webapplikation mit dem laufenden Murmur Prozess komunizieren.

# debian Webserver und Murmur für ZeroC-Ice konfigurieren

Dies sind Beispiele nutze sie auf eigene Gefahr\!

**Dieser Leitfaden ist für debian 5.0 (lenny)**

Ich gehe davon aus das du bereits einen funktionierenden apache2 mit PHP
Unterstützung hast.

**Voraussetzungen**

Als erstes installieren wir einige benötigte Packete, dies machen wir in
einem root-shell.

`apt-get update`

`apt-get install mumble-server icecpp libzeroc-ice32 php-zeroc-ice lzma`

Diese sind namentlich der Mumble-Server selbst (mumble-server), ZeroC
Ice selbst (icecpp), die ZeroC-Ice C++ Laufzeitbibliothek
(libzeroc-ice32), das IcePHP Modul (php-zeroc-ice) und der lzma
Extraktor. Sei dir bewusst darüber das wir vorerst eine älterer
Serverversion OHNE Ice Unterstützung installieren. Das werden wir später
korrigieren.

Zusätzlich benötigen wir den aktuellen Server (Murmur).

Man kann ihn über die Adresse <http://www.mumble.info> beziehen. "Stable
Static Linux Server". Ich empfehle dafür das Heim-Verzeichnis.

`cd ~`
`wget `<http://switch.dl.sourceforge.net/sourceforge/mumble/murmur-static_x86-1.1.8.tar.lzma>
`unlzma -v murmur-static_x86-1.1.8.tar.lzma`
`tar xfv murmur-static_x86-1.1.8.tar`

*' Schritt 1 - Murmur konfigurieren*'

OPTIONAL: Um Murmur mit jedem Systemstart automatisch zu starten
bearbeite die Datei /etc/default/mumble-server entsprechend mit einem
Editior deiner Wahl.

Nun öffne die Datei /etc/mumble-server.ini

`vim /etc/mumble-server.ini`

OR

`nano -w /etc/mumble-server.ini `

Kommentiere die Zeile die mit dbus= beginnt aus

`#dbus=system`

Erstelle eine neue Zeile und füge folgendes in diese ein

`ice="tcp -h 127.0.0.1 -p 6502"`

Murmur weiß damit das er auf Ice Anfragen achten soll.

''' Schritt 2 - Murmur manuell aktualisieren '''

Sicherlich kamm schon die Frage auf warum wir eine "veraltete" Version
installiert haben.

Die Antwort ist denkbar einfach, damit wir erniger Arbeit haben.
Allerdings gibt es einen kleinen Nachteil.

Wenn das Packet im Repository eine Aktualisierung erhält kann das unsere
Ice Unterstützung wieder rückgängig machen. Aber ich behaupte dennoch
das dies der beste Weg ist und man kann dieses Problem leicht wieder
beheben in dem man die murmurd einfach nochmal manuel aktualisiert.

Die statische Linux Binärdatei wurde bereits in das Heimverzeichnis
entpackt und nun benötigen wir einige Dateien von dort.

Al erstes ersetzen wir die ältere Version durch die Neuere.

`cd ~/murmur-static_x86-1.1.8`
`chmod +x ./murmur.x86`
`cp murmur.x86 /usr/sbin/murmurd`

Nun kopiere die zugehörige Ice Spezifikation.

`cp Murmur.ice /var/lib/mumble-server/Murmur.ice`

''' Schritt 3 - PHP Einstellungen ''' Nun müssen wir der PHP-Ice
Erweiterung noch mitteilen wo sie die Ice Spezifikation für Murmur
findet. Es sollte bereits eine Datei /etc/php5/conf.d/IcePHP.ini von der
Installation existieren. Öffne diese in einem Editor.

`vim /etc/php5/conf.d/IcePHP.ini`

ODER

`nano -w /etc/php5/conf.d/IcePHP.ini`

Am Ende der Datei füge folgende Zeile hinzu:

`ice.slice = /var/lib/mumble-server/Murmur.ice`

''' Schritt 4 - Reload '''

Alles nötige sollte nun getan sein und wir wollen unsere neuen
Eisntellungen testen.

Neustart von apache2.

`/etc/init.d/apache2 restart`

Murmur starten.

`/etc/init.d/mumble-server start`

Nun wollen wir einen prüfenden Blick in die Log-Datei werfen ob alles
wie erwartet funktioniert.

`tail -n10 /var/log/mumble-server/mumble-server.log`

Wenn du eine ähnliche Zeile wie die folgende findest:

`...`
<W>`2009-04-06 13:37:11.316 MurmurIce: Endpoint "tcp -h 127.0.0.1 -p 6502" running`
`...`

sollte alles funktionieren und du kannst nun mit Murmur über die IcePHP
Erweiterung kommunizieren.

''' Nochmals, denke darann das die Ice Unterstützung evtl. zerstört wird
wenn das Packet über die Packetverwaltung aktualisiert wird\! '''

[Category:Documentation
German](Category:Documentation_German "wikilink")