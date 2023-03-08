# Languages|FAQ

##FAQ: Über Mumble

###Was ist Mumble?
Mumble ist eine universell einsetzbare Voice-Chat-Anwendung ähnlich Ventrilo oder TeamSpeak, die sich in erster Linie auf die Kommunikation in Computerspielen konzentiert. Oftmals wird der Begriff "Mumble" sowohl für den Client als auch den Server verwendet, der Server heißt jedoch "Murmur", und das komplette Paket "Mumble & Murmur".

###Auf welchen Plattformen läuft Mumble?
Der Mumble Client läuft unter allen aktuellen Windows-Versionen, sowie unter Apple OSX und unter Linux. Ebenso sind Clients für Apple iOS und Android erhältlich.

Der Server "Murmur" läuft auf allen Systemen, auf denen Du QT4 kompilieren kannst.

Aktuelle Links zu Client- und Server-Paketen findest Du auf unserer [Website](Main Page.md).

###Systemanforderungen
Client: Linux oder Windows, ein Mikrofon. Der Server bzw. die Anzahl der Server hängt von der Bandbreite Deines Servers ab. Solange Deine Netzwerkhardware über ausreichende Kapazitäten verfügt, läuft der Server [Murmur](Running_Murmur.md) auf allen Betriebssystemen, welche Qt4 kompilieren können.

Bitte beachte, dass die Mumble-Binarys für SSE-Prozessoren (Pentium 3 oder Athlon XP) kompiliert wurden.
Mumble ist eine VoIP-Lösung für Computerspiele. Da die meisten modernen Computerspiele eine relativ gute CPU benötigen, war es für das Entwicklerteam von Mumble nicht notwendig, Mumble für ältere Hardware zu optimieren.

###Mumble Installieren
Vorkompilierte Programmpakete könnt ihr von Sourceforge downloaden, wenn ihr Windows oder ein i386-Linux mit installiertem Debian Paket Manager habt. Installationsquellen:
* Windows: [http://sourceforge.net/project/showfiles.php?group_id=147372|Sourceforge]
* Linux
* Debian, Ubuntu, etc.  [[2](http://3v1n0.tuxfamily.org/.md)(http://sourceforge.net/project/showfiles.php?group_id=147372|Sourceforge] (.deb) oder das Trevino Repository)
* Distros welche RPM benutzen: Du kannst ein RPM nutzen  [wurde](http://sourceforge.net/forum/forum.php?thread_id=1782689&forum_id=492606|welches im Forum gefunden)
* Gentoo: ''emerge mumble'' funktioniert. Ihr müsst aber die sqlite oder sqlite3 Flags aktiviert haben und müsst,
falls ihr QT4 ohne die Flags emerged habt, QT4 erneut emergen.
* Archlinux: Ihr findet ein PKGBUILD im AUR: [http://aur.archlinux.org/packages.php?do_Details=1&ID=10221|[3]]

Ausschlussklausel: Nur die Dateien von Sourceforge sind offiziell. Seit vorsichtig im Umgang mit Dateien von anderen Quellen.
Für diejenigen, die es wollen: Hier findet ihr zwei gute Tutorials wo erklärt wird, wie ihr Mumble/Murmur auf eurem System kompilieren könnt.

* Linux: [Kompilierung](BuildingLinux.md)
* Windows: [Kompilierung auf Windows Systemen](BuildingWindows.md)

###Was macht Mumble besser?
Mumble hat eine niedrige Latenzzeit, kombiniert mit einer guten Soundqualität. Es nutzt Speex extensiv, nicht nur die Sprachkompression selbst, sondern auch die Sprachvorverarbeitung um ungewollte Geräusche zu entfernen und die Deutlichkeit der Sprache zu erhöhen. Mumble nutzt die "Positional Audio" Technik für Spiele welche dies unterstützen. Das bedeutet, dass die Stimmen der anderen Spieler aus der Richtung kommen, wo deren Charaktere sich im Spiel befinden.

###Welche Bandbreite benötige ich?
Seit 0.9.1 ist dies sehr variabel und hängt stark vom Spieler ab. Mit Top-Qualität, kleinster Latenzzeit und Positional Audio beträgt die Bandbreite 64,6 kbit/s inkl. dem IP und UDP Overhead. Mit 80ms Übertragungsverzögerung, der geringsten Sprachqualität und ohne Positional Audio sind es 11.0 kbit/s (wieder mit IP und UDP Overhead). Standard sind 45.4 kbit/s; das Entwicklerteam hat noch keine Verschlechterung herausgehört gegenüber den 20 kbit/s mehr bei 65.4 kbit/s. Wenn Ihr mit anderen Produkten vergleicht, dann vergesst nicht, die komplette Bandbreite zu vergleichen und nicht nur die Bitrate der Audioentschlüsselung.

Es gibt 2 Möglichkeiten, um die Bandbreite zu tunen. Die Audio Bitrate per Audio Frame (20 ms) und die Anzahl von Frames pro Paket. Jedes gesendete Paket hat einen Overhead von 28 Byte nur IP und UDP alleine, so dass bei der höchsten Übermittlungsrate (50 Pakete pro Sekunde) 1400 Byte nackte Daten nur für die Übermittlung des Netzwerk Overheads anfallen.
Probiere es aus und finde ein Gleichgewicht zwischen den beiden Parametern, welche für dich gut sind. Die Entwickler empfehlen, auf eine hohe Audiobitrate zugunsten geringerer Latenz zu verzichten. Mumble klingt auch auf der niedrigsten Audio Qualitätsstufe noch ganz gut.

Es gibt keine Möglichkeit, die Menge der hereinkommenden Bandbreite einzustellen; du musst die Daten welche durch die anderen sprechenden Spieler anfallen, "ertragen" können. Das ist eine geringfügige Angelegenheit, denn aktuell sind die meisten Spieler auf ADSL so dass der meiste Upload der anderen Spieler nur einen "Flaschenhals" darstellt, also eher gering ist.

###Welche Werkzeuge wurden für die Entwicklung von Mumble verwendet
Siehe auch [ Entwicklungswerkzeuge (Englisch)](Development Tools.md).

###Wie kann ich helfen oder Kontakt mit euch aufnehmen?
Ein guter Start ist, Mumble zu nutzen. Wenn es Dir gefällt, zeig es deinen Freunden. Wenn Dir etwas nicht gefällt, dann teile uns die Gründe mit, damit wir es verbessern können. Du kannst dies über die Foren oder in IRC in irc://irc.freenode.org/mumble

##FAQ: Audio Funktionen

###Wie funktioniert "Positional Audio"?
Deine Position im Spiel wird mit jedem Audio Paket übermittelt und Mumble benutzt Standard DirectSound 3D, um die Audioausgabe entsprechend zu positionieren auf der Empfängerseite. Nur Spiele mit entsprechendem PlugIn können "Positional Audio" nutzen. Alle anderen Spiele laufen normal, aber ohne 3D Sound resp. "Positional Audio".

###Warum klingt Mumble so viel besser als andere VoIP Programme?
Ein Wort: Geräuschverminderung. Standard bei Speex 1.1 aufwärts und alle VoIP Anwendungen, welche Speex implementieren, haben die Möglichkeit, ganz trivial die selben Filter zu verwenden.

Die Geräusche vom Eingang zu entfernen bedeutet, dass die Audioqualität klarer und die benötigte Bitrate kleiner wird. Es braucht weniger Bits um eine klare Stimme zu erzeugen, als um akkurat Geräusche darzustellen. So wird in allen Geräuschübermittlungen ein großer Anteil Bits Nebengeräusche formen.

###Wo ist die Lautstärkenkontrolle?
Grundsätzlich verwendet Mumble die Audio-Schnittstellen des jeweiligen Betriebssystems. Folglich ändert man die Lautstärke im Mixer, welcher vom Betriebssystem bereitgestellt wird.

Ab Windows VISTA kann die Lautstärke separat für jedes Programm (und somit für Mumble) im Mixer geregelt werden. Linux Anwender können verschiedene Soundserver benutzen, welche wiederum einige Möglichkeiten bieten, um die Lautstärke separat zu regeln.

Sollten z.B. Spielgeräusche zu laut und Mumble zu leise sein, so kann man im Spiel selber die Lautstärke etwas reduzieren.

Es gibt keine Funktion für die Verstärkung hereinkommender Sprache, und wird es auch nicht geben, da dies die Audioqualität verschlechtern wird, und die Entwickler dies nicht wollen. Verständlich.

###Die Qualität von Text to Speech ist entsetzlich
Die Entwickler nutzen die Standard MS-Speech API, welche qualitativ nicht unbedingt hochwertig ist. Wenn Ihr MS Office oder die "Speech SDK" installiert habt, dann habt ihr mehr Stimmen, welche ihr im Speech Control Panel konfigurieren könnt. Ihr könnt auch eine kommerzielle Text-to-Speech Engine kaufen; Solange diese SAPI5 kompatibel ist, kann diese auch in Mumble verwendet werden. Die Hauptentwickler benutzen derzeit NeoSpeech Kate (kann eigenständig von NextUp bezogen werden).

###Warum klingen manche Klänge metallisch?
Mumble benutzt den Speex Geräuschfilter und wenn beim Sprecher ein starker Geräuschhintergrund besteht, dann werden auch Teile der Stimme gefiltert. Die Alternative wären laute Geräusche; das heisst, kostbare Bandbreite wird verschwendet um die Geräusche zu entschlüsseln und die klare Wiedergabe der Stimme wird ebenfalls schlechter.

###Warum erkennt die "Voice Activity" meine Stimme nicht mehr?
Wenn Du deine Audioaustattung schnell und plötzlich änderst wie z.B. ziehen und neu einstöpseln des Mikrofons oder ziehen eines Blattes direkt über dem Mikrofon bringt den Stimmpräprozessor aus dem Gleichgewicht. Er wird sich zwar wieder erholen, dies kann jedoch einige Zeit dauern.

Um den Präprozessor zu resetten, wähle "Reset" aus dem "Audio"menü.

###Was ist dieses eigenartige Echo in dem ich mich selbst von den anderen Usern wieder höre?
Bedauerlicherweise produzieren eine Menge bekannter Headsets Spuren von Echo. In anderen VoIP-Produkten bemerkst Du diese nicht, weil das Echo geringer ist als der Geräuschpegel, aber Mumble entfernt alle Geräusche und so wird das Echo klar. Da kann man nur wenig machen. Aber es gibt doch einige Dinge, die derjenige der das Echo produziert, tun kann.
Die einfachste Lösung ist, ASIO zu benutzen und Echo Entfernung einzuschalten. Das erfordert ein Analoges Headset (kein USB Typ) und eine Soundkarte von hoher Qualität.
Die beschwerlichere Lösung ist, das Headset zu bearbeiten. Wenn es möglich ist, den Arm des Headsets etwas herauszubrechen, so dass das Mikrofon weiter weg vom Ohrhörer ist, dann tu es und kleb' den Arm mit einem dicken Isolierband wieder hin. Das isoliert das Headset von Vibrationen. Wenn Dein Headset offen ist, (keine grossen Ohrhörer), dann gibt es einen Weg des Klanges durch die Luft von den Ohrhörern zum Mikrofon, der Echo erzeugen kann. Du kannst dies lösen, indem du Schaumstoffartige Dinge an die Ohrhörervorderseite anhängst, um den Sound der nach außen hörbar wird, einzudämmen. Dies zerstört meist die Ergonomie des Headsets und weiter schaut es etwas befremdlich aus.

###Wo ist die Alt-Speak Funktion in 1.2.x hin?
Diese wurde in einer neuen Flüstern-Funktion eingebaut und damit ersetzt. Erstellen sie ein neuen Tastenkürzel "Flüstern/Rufen" und wählen bei Daten "Aktueller Kanal" bei "An Kanal Rufen" inklusive "An Verknüpfte Kanäle Rufen" aus, um die Alt-Speak Funktion von 1.1.x in 1.2.x zu nutzen.

##FAQ: Server

###Welche Bandbreite brauche ich?
Im schlimmsten Fall: Anzahl User X Anzahl sprechender User X 60 kbit/s. Mit nicht ganz so aggressiven Einstellungen etwas bei 20 kbit/s und Minimum bei 12 kbit/s.

Beachte, dass Mumble mit der sozialen Spielcommunity verzahnt ist, jeder kann zu jedem in klarer Sprache sprechen, anstelle nur Befehle zu bellen. Der Anteil sprechender User kann also höher sein als erwartet.
Das bedeutet auch, dass ein Server mit 20 Spielern, wo zwei gleichzeitig sprechen, 0.8-2.4 Mbit/s benötigt, abhängig von den Qualitätseinstellungen. In der INI des Servers kannst Du angeben, welche Bitrate maximal für User erlaubt ist und ebenso auch die maximale erlaubte Anzahl von Usern, die online sein können (Slots).


###Wo stelle ich die Willkommensnachricht, den "Listen Port" und weiteres ein?
Dazu passt man die Variable [welcometext in der murmur.ini](murmur.ini#welcometext.md) an.

###Wie administriert man die ACL?

Siehe [ACL FAQ](ACL_FAQ_(Deutsch).md)


###mumble.pri:8: Unbekannte test Funktion: CONFIG
Mumble benötigt QT 4.2 (Bei Mumble-Funk.de läuft 4.2.2).

Wenn Ihr QT kompiliert dann macht am Anfang

<code>
./configure -qt-sql-sqlite
</code>


um das MakeFile zu erstellen.


###Wie kann ich die Datenbank resetten?
Bei sqlite (Standard):

Lösche die Datei murmur.sqlite und führe den Befehl
murmur -supw erneut aus.

Bei MySQL: TRUNCATE DATABASENAME (kein Delete)


###Wie ändere ich das Passwort eines Users?
Konsole (BASh):

 -bash-3.00$ sqlite3 murmur.sqlite
 sqlite> UPDATE players SET pw
 'newpassword' WHERE name
 'playername';
 sqlite>


Weitere Möglichkeit: SQLiteBrowser verwenden.


###Wie kann ich die Datenbank sichern (Backup)?
Fahre den Murmur runter und kopiere die murmur.sqlite. Dies ist die Datenbank.

MySQL: Exportiere die Datenbank an der Konsole (man mysql) oder mit PHPMyAdmin.


###Wie kann ich Murmur als SyS V Dienst laufen lassen (selbständig starten nach Serverstart)?
Benutze dieses Skript.

 #!/bin/bash
 #
 # chkconfig: 35 90 12
 # description: Murmur Service
 # Idologic Jun 27, 2007  
 
 # Get function from functions library
 . /etc/init.d/functions 
 
 # Start the service Murmur
 start() {
 initlog -c "echo -n Starting Murmur server: "
 daemon /usr/bin/murmur -ini /etc/murmur/murmur.ini
 ### Creating the lock file ###
 touch /var/lock/subsys/murmur
 success $"Murmur server startup"
 echo
 }  
 
 # Restart the service Murmur
 stop() {
 initlog -c "echo -n Stopping Murmur server: "
 killproc murmur
 ### Deleting the lock file ###
 rm -f /var/lock/subsys/murmur
 echo
 }
 
 ### main logic ###
 case "$1″ in
 start)
 start
 ;;
 stop)
 stop
 ;;
 status)
 status murmur
 ;;
 restart|reload|condrestart)
 stop
 start
 ;;
 *)
 echo $"Usage: $0 {start|stop|restart|reload|status}"
 exit 1
 esac 
 
 exit 0

##FAQ: Bekannte Probleme und Lösungen

###Fehler: failure to load mumble_ol.dll

Wenn bei Dir Windows XP mit SP2 läuft, dann ist dein DirectX vielleicht veraltet. Es gibt wohl so ziemlich jeden Monat ein Update von DirectX, daher updatet auch so ziemlich jedes Spiel Dein DirectX. Derzeit ist 9.0c aktuell. Schaue auf das Erscheinungsdatum Deines DirectX.

Aktuelle DirectX Versionen gibt es direkt von Microsoft.
 [upzudaten.](http://www.microsoft.com/windows/directx/default.mspx|Klicke hier um DirectX)

Runtergeladen, entpackt und installiert wurde dieses Problem für mich gelöst:  [Runtimes](http://www.microsoft.com/downloads/details.aspx?FamilyID=b406cf67-d926-463b-99e8-27199d6626b5&DisplayLang=en|DirectX End-User)


###Ich kann andere nicht hören, andere hören mich nicht ;-(

Abhilfe schafft hier ein Häkchen in der Checkbox "Use TCP Mode" in Konfiguration -> Einstellungen -> Grundeinstellungen.


###Webserver kann Datenbank nicht beschreiben, wenn murmur.cgi benutzt wird

Schau nach, ob die DB beschreibbar ist vom Webserverbenutzer, genauso auch das Directory in dem die DB liegt.


###Fehlermeldungen in murmur.cgi Zeile 118

Sofern Du keinen anderen SMTP Server (Mailausgang) definiert hast, benötigst Du einen MTA auf dem localhost.


###Ich kann zwar auf den Server drauf, aber Channels anlegen / joinen geht nicht

Du kannst nicht den 0.9.1 Client mit dem 0.9.2 Server nutzen. Genausowenig den 0.9.4 Client mit dem neuen 1.0.0 Server.


###Wo ist der PTT Knopf (Push to Talk)?

Wenn in Konfiguration -> Einstellungen -> Grundeinstellungen Push-To-Talk aktiv ist, dann muss mit Konfiguration -> Einstellungen -> Shortcuts auch eine Taste als PTT Taste definiert werden.


###Shortcuts wie z.B: PTT gehen nicht unter Linux

Bitte aktiviert die Xevie Erweiterung damit die Shortcuts funktionieren.

Bitte fügt folgende Zeilen in die Xorg.conf ein:

 Option         "XEVIE" "Enable"

Das schaut dann in etwa so aus:
 Section "Extensions"
 ...
 Option "XEVIE" "Enable"
 EndSection

Dann noch den X-Server neustarten (STRG+ALT+Backspace) und Mumble neu starten.


###Die Tasten scheinen gesperrt zu sein, wenn ich Shortcuts unter Linux benutze

Zeitweise sind Tasten "gesperrt", wenn Xevie verwendet wird. Beispiel: Du drückst zwei Tasten gleichzeitig und wenn du die Tasten loslässt, dann wird nur eine Taste als gelöst erkannt. Das sieht man am besten in Spielen, wenn du anfängst, diagonal zu laufen. Wenn du dann stoppst, wird die Bewegung beibehalten. Dies kann mit den Tastenwiederholungseinstellungen behoben werden, welche hier zu finden sind:


Gnome: System->Einstellungen->Tastatur

KDE: K Menü->Kontrollzentrum->Peripherie->Tastatur

Du kannst auch ausprobieren, den Geschwindigkeits/Anteil Regler zu verändern sowie die Tastenwiederholung auszuschalten (die erste Checkbox).

###Das Display der Logitech G15 wird nicht erkannt

Mumble LCD Display der Logitech G15 Tastatur. Vorausgesetzt wird dafür ist ein aktueller Treiber.

Leider informiert ein Treiber der 2.x Serie nicht über ein Update auf die 3.x Serie. Dieser muss manuell über den Kundendienst von Logitech bezogen werden.

## Windows 

### Kann Mumble automatisch zum Server verbinden, wenn Windows startet? 

Die einfachste Möglichkeit dies zu erreichen, ist über das Autostart-Feature das Windows im Startmenü anbietet. Erstelle dazu einfach eine neue
Verknüpfung im Autostart-Verzeichnis deines Startmenüs, die auf eine "mumble://"-URL zu deinem Server verweist. Dann wird Windows beim Start automatisch Mumble starten.



