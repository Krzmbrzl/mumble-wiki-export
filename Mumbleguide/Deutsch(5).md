**Bitte bearbeite diese Seite wenn Du eine Funktion oder einen
Arbeitsschritt findest, welche/r Deiner Meinung nach hier aufgelistet
sein sollte. Dies ist nicht umsonst eine Wiki\!**

# Mumble Funktionen und Grundeinstellungen

Gut, Du hast Mumble nun installiert und fragst Dich möglicherweise, was
es alles einzustellen gibt. Hier findest Du deswegen eine Auflistung der
Grundlegenden Einstellungsmöglichkeiten von Mumble.

Die Standard Konfigurationsansicht von Mumble deckt die meisten
Grundeinstellungen ab, blendet allerdings auch einige der möglichen
Einstellungen aus. Wenn Du alle möglichen Eigenschaften von Mumble frei
verändern willst klicke oben in Mumble auf Konfiguration dann auf
Einstellungen und setzte unten links in der Ecke im
Konfigurations-Fenster bei Erweitert einen Haken, ansonsten besitzt du
nur die Möglichkeit an den einfachen Einstellungen herum zu spielen.
Wenn Du bei einem der unten aufgeführten Punkten ein **Erweiterte
Konfiguration** wie dieses hier siehst, dann benötigst Du für diesen
Schritt den haken im Erweitert-Feld.

Wenn wir in diesem Leitfaden von **der Konfiguration** reden meinen wir
im Normalfall das Konfigurationsfenster unter: Konfiguration -\>
Einstellungen.

Wenn Du irgendwelche fragen hast schau bitte zuerst einmal in die
[deutschen FAQ](FAQ/Deutsch "wikilink") oder in die aktuelleren
[englischen FAQ](FAQ "wikilink"). Oder besuche den [offiziellen Mumble
IRC-Channel](irc://irc.freenode.org/mumble) bzw. den [deutschen Mumble
IRC-Channel](irc://irc.freenode.org/mumble.de).

## Oberfläche

### Assistenten

Wenn Du Mumble das erste mal startest, bittet es Dich den
Audio-Assistent und Zertifikats-Assistent zu starten und ordentlich
abzuarbeiten. *Das solltest Du auch*. Klick Dich nicht einfach durch,
sondern lese dir jeden Schritt genau durch und versuche zu verstehen was
für Einstellungen der Assistent von Dir erwartet. Besondere
Aufmerksamkeit solltest du der Seite zum Thema Audio-Eingabe schenken,
schließlich willst du nicht, dass niemand dich wirklich hört oder das
die Anderen *zu viel* hören.

Ein Zertifikat ermöglicht es Dir, Dich auf einem Server zu registrieren,
ohne dafür ein externes Programm, eine Webseite oder ein Passwort zu
benötigen. Wenn Du zum Ersten mal Mumble startest, nach dem du den
Audio-Assistenten beendet hast, erscheint automatisch der
Zertifikats-Assistent. Hier importierst Du entweder ein Zertifikat, dass
Du schon einmal angelegt hast, oder erstellst ein neues. Sobald Du im
Zertifikats-Assistenten den Punkt zum Thema Back-up erstellen
(exportieren) erreichst, sichere es auf einem Flash-Speicher (USB-Stick
etc.) oder anderem Externen Speichermedium (Externe Festplatte, DVD,
Diskette etc.), aber **speichere es nicht auf deiner Festplatte\!** Ab
Mumble 1.2.1 wird für dich automatisch ein Zertifikat angelegt, sofern
du den Assistenten abgebrochen hast (dieses Zertifikat ist allerdings
nicht zu empfehlen). Dieses automatisch erstellte Zertifikat findest du
unter \[Meine\] Dokumente/MumbleAutomaticCertificateBackup.p12. Wenn du
dieses Zertifikat wirklich nutzten willst, anstatt ein eigenes
Zertifikat zu erzeugen, sparst du dir viel Ärger, wenn du diese Datei
frühzeitig auf einen Externen Datenträger kopierst, oder über den
Zertifikats Assistenten (Konfiguration -\> Zertifikats-Assistent)
manuell exportierst.

### Methoden zur Tonübertragung

**Erweiterte Konfiguration**

In Mumble gibt es mehrere Methoden zur Tonübertragung: Kontinuierlich,
Stimmaktivierung und Push-To-Talk.

Kontinuierlich macht genau das, wonach es klingt: Mumble überträgt
kontinuierlich alles was Dein Mikrophon aufnimmt. Dies kann Sinn machen
bei Podcasts oder Gesprächen die eine möglichst geringe Latenz erfordern
oder die höchst Mögliche Tonqualität, ungeachtet von
Hintergrundgeräuschen und der genutzten Bandbreite.

Stimmaktivierung macht auch genau das wonach es klingt: Wenn Du laut
genug redest wird Dein Signal übertragen. Du kannst genau einstellen
wann und wie lange dies jeweils passiert indem Du in den Audio-Eingabe
Bereich der Konfiguration gehst. '''Wenn Du kein brauchbares Signal
durch *Signal zu Rauschen* bekommst, probiere es mit Rohamplitude. Schau
Dir einfach kurz an wie sich der Balken im jeweiligen Zustand verhält
und Du *dürftest* erkennen wie die jeweilige Einstellung zu optimieren
ist.

Push-To-Talk bedeutet, dass Du eine Taste/eine Tastenkombination
definierst (im Menüpunkt "Tastenkombinationen"), bei deren drücken dein
Signal übertragen wird. Du kannst hierfür auch extra Signale einstellen
um selber zu hören ob Du aus versehen gerade ein Signal sendest, oder ob
Du vielleicht die falsche Taste drückst und Dich somit niemand hört.

### GUI

Du kannst dauerhaft die Teilfenster von Mumble verändern. Gehe dazu in
den Benutzter-Interface Bereich der Konfiguration und such Dir eine
vordefinierte Anzeigeart aus.

Gesetzt dem Falle, dass Du die einzelnen Felder noch präziser einstellen
willst, bewege deine Maus an den oberen Rand eines Teilfensters und
warte knapp eine halbe Sekunde. Darauf hin dürfte ein kleiner Bereich
ausfahren, mit dem man über Drag and Drop das Teilfenster vollkommen
frei positionieren kann. Wenn man mit der Maus auf die Übergänge geht,
bekommt man die Möglichkeit außerdem die Höhe und die Breite jedes
dieser Elemente manuell anzupassen.

### Zu einem Server verbinden

Öffne den Verbindungs-Dialog (Server -\> Verbinden). Hier kannst Du
einen Favoriten hinzufügen über "Server hinzufügen..." oder in dem Du in
die Öffentliche Serverliste gehst, Rechtsklick auf einen Server Deiner
Wahl machst und auf "Zu Favoriten hinzufügen..." klickst. Beim Verbinden
zum Server kannst Du Dir einen Namen deiner Wahl nehmen, allerdings
kannst Du den Namen den du besitzt, wenn Du Dich mit dem Server
registrierst, selber nicht mehr ändern, es sei denn ein
Server-Administrator ändert ihn in der Server-Datenbank oder löst Deine
Registrierung auf.

### Registrieren

Sobald Du auf einen Server Connectet bist dürftest Du Dich auf dem
Server Registrieren dürfen, in dem Du auf Deinen Namen rechts-klickst
und auf "Registrieren" klickst. Standart gemäß funktioniert dies, da es
sich dabei um eine Standardeinstellung des Servers handelt, auf manchen
Servern kann man sich allerdings als Gast nicht selber registrieren, in
dem Fall musst Du Dich von einem registrierten User oder vom Admin
registrieren lassen.

**Als Admin kannst du alle registrierten Benutzter managen in dem du auf
"Server -\> Registrierte Benutzer" klickst.**

## Öfter auftretende Probleme

### Audio

**Erweiterte Konfiguration**

## Konfiguration

**Hinweis: Mumble wurde bewusst so entwickelt, dass einige Änderungen
erst nach erneutem Start verfügbar sind. Für diese Maßnahme gibt es
natürlich Gründe, dies ist hoffentlich Verständlich. Daher, wenn Du
viele Konfigurationen auf einmal tätigst, wäre es zu empfehlen, Mumble
neu zu starten, dies hat auch den positiven Nebeneffekt, dass diese
Einstellungen auch nach einem unerwarteten Mumble/Betriebssystem Absturz
diese Einstellungen nicht verloren gehen.**

### Nachrichten

**Erweiterte Konfiguration**

Wie vorhin angedeutet können manche Nachrichten auf Dauer ein bisschen
stören. Wenn Du bestimmte Nachrichten im Log (das Fenster in dem alle
Texte angezeigt werden, welches in Mumble als "Konsole" geführt ist)
oder bestimmte "Benachrichtigungen" (die kleinen Nachrichten die unten
rechts in Windows auftauchen wenn Mumble sich nicht im Vordergrund
befindet) (de-)aktivieren möchtest, gehe einfach zu Konfiguration -\>
Nachrichten und entferne bzw. setzte die entsprechenden Haken.

### Overlay

**Erweiterte Konfiguration**

Mumble besitzt ein Overlay, dass in Spielen und unter anderem in DirectX
gerenderten Videos erscheint (VLC, MPC etc.). Dieses Overlay wird Dir
oben rechts angezeigt wenn Du Ingame bist. Du kannst es unter
Konfiguration -\> Overlay einstellen.

Wenn Du das Overlay deaktivieren willst, entferne einfach den Haken bei
"Overlay aktivieren".

Wenn Dir das Overlay gefällt, kannst Du deinen Namen mit einem 600x60
Pixel großen PNG Bild ersetzt (am besten mit Alpha-Transparenz um es an
einigen Stellen Durchsichtig zu halten). Um eine Textur zu nutzten oder
zu entfernen gehe Server -\> Texture ändern oder Server -\> Textur
entfernen.

Wenn das Overlay mit einem Deiner Spiele oder Programm Probleme hat oder
es Dich explizit in einer Anwendung stört, deaktiviere es für diese
Anwendung in dem Du in den Ordner der Ausführenden Datei eine Datei
Namens "nooverlay" (ohne eine Datei-Endung) positionierst.

#### Mac

Wenn Du einen Mac nutzt ist das Overlay nicht ganz so
Benutzerfreundlich, hier musst Du das Spiel mit dem
Mumble-Overlay-Kommando starten. Zum Beispiel:

`/Applications/Mumble.app/Contents/Overlay/mumble-overlay /Applications/World\ of\ Warcraft/World\ of\ Warcraft.app`

### Positionsabhängiges Audio

**Erweiterte Konfiguration**

Mumble unterstützt in [einigen Spielen](Games "wikilink")
positionsabhängiges Audio. Dies bedeutet, dass, sofern diese Funktion
aktiviert ist, das Signal innerhalb Mumbles sich an den Charakteren im
Spiel orientiert. Wenn Dein Freund also Ingame rechts von Dir steht
kommt seine Stimme in Mumble auch von rechts, ist er weiter weg, wird
auch seine Stimme leiser. Dieses Feature wird durch Plug-Ins in Form von
DLL-Dateien ermöglicht.

Wenn Du Spiele von [dieser Liste](Games "wikilink") besitzt und auch
"Positionsabhängiges Audio" nutzten möchtest gehe zu Konfiguration -\>
Plugins und setzte einen Haken bei "Mit Spiel verbinden und Position
übertragen" und im "Audio Ausgabe" Bereich einen weiteren Haken bei
"Positionsabhängiges Audio". Wenn Du Kopfhörer besitzt setzte darüber
hinaus noch einen Haken bei "Kopfhörer". Des weiteren empfehle ich
"Minimale Lautstärke" am besten auf 80% und maximal auf 95% zu setzten,
da somit Deine Mitspieler, egal wie weit sie Ingame weg stehen, immer in
einer ordentlichen Lautstärke mit Dir kommunizieren.

#### Manual placement plugin

Wenn Du ohne Spiel diese Funktion nutzten möchtest gehe wie folgt vor:

Konfiguration -\> Plugins -\> klicke auf "Manual placement plugin" -\>
klicke auf Konfigurieren -\> im nun erscheinenden Fenster auf "Unhing"
-\> im Konfigurationsdialog daraufhin auf OK -\> hohle das Fenster des
"Manual placement plugin" in den Vordergrund -\> Aktiviere "Activated"
und "Linked" -\> setzte Deine Positionseinstellungen.

Hinweis: Um das Ergebnis zu hören benötigst Du noch eine weitere Person
die dieses Plugin auch nutzt.

#### Plugin Updates

Plugin Updates sind relativ oft nötig, denn wann immer ein Spiel
gepatcht wird ändern sich auch die Speicheradressen die benötigt werden,
um die Positionen zu ermitteln. Deswegen müssen die Plugins neu
kompiliert und die alten durch die neuen ersetzt werden. In Mumble 1.2.0
werden die geupdateten Plugins daraufhin automatisch heruntergeladen.

### Skins

Wenn Du Dein Mumble optisch etwas aufpäppeln möchtest gibt es dazu
mehrere Möglichkeiten. [Hier](Skins "wikilink") findest du z.B. eine
Seite mit Links zu vielen tollen Skins und einer Anleitung, wie du diese
installierst. Wenn Du Dir ein Skin erstellen lassen möchtest, dass
optisch genau deinen Farbwünschen entspricht probier mal
[Juicer](http://zavaboy.com/phpbox/juicer/) aus. **Hinweis: noch sind
nicht viele Skins auf die 1.2.0 geupdatet. Generell wird das keine
Probleme verursachen, außer höchstens kleinere Schönheitsfehler, wir
empfehlen aber trotzdem auf die Versionsnummer zu achten.**

**Um einen Skin zu installieren:**

1.  Gehe in deinen Mumble-Ordner (Standard unter Windows 32 bit:
    C:\\Programme\\Mumble\\ ) und erstelle dort den Ordner *skins*
2.  Downloade und entpacke einen Skin. Achte darauf, dass dessen Ordner
    (nicht einer seiner möglichen Unterordner) die Bilder und die
    Skindatei (eine Datei im .qss-Format) beinhaltet.
3.  Platziere diesen Ordner im Ordner *skins*
4.  Gehe zu Konfiguration -\> Benutzerinterface und klicke rechts neben
    der "Skin"-Box auf "**...**". Ein neues Fenster sollte auftauchen
    und automatisch den *skins*-Ordner anzeigen, wenn nicht wechsle
    manuell in diesen. Öffne hier drinnen den Ordner mit dem Skin,
    welches du nutzten willst. Wähle jetzt QSS-Datei deren Name dem des
    Skinnes ähneln sollte.

**Einen Skin modifizieren:**

Wenn Du willst, dass ein Skin besser zu Deiner Mumble-Einstellung passt,
ihn optisch an Deinen Geschmack anpassen willst, oder Du ein paar Farben
ändern möchtest öffne die <skinname>.qss im Ordner des Skins mit einem
Texteditor. Wenn Du jemals mit CSS gearbeitet hast, dürftest Du mit QSS
keinerlei Probleme haben, da QSS CSS mit eigenen Klassen entspricht.
Allerdings auch ohne CSS Kenntnisse dürftest Du Dich schnell eingelesen
haben und finden was du suchst.

**Einen eigenen Skin erstellen:** Wenn du einen eigenen Skin erstellen
willst findest du [hier](Skinning "wikilink") genauere Hinweise zu
diesem Thema.

### Text-zu-Sprache

**Erweiterte Konfiguration**

Dies ist ein eigentlich ganz gutes Feature das viele deutsche
Mumble-User meist allerdings als störend betrachten sofern es nicht von
ihnen manuell auf deutsche Nutzung angepasst wurde. (De-)Aktivieren
kannst du es ganz einfach und schnell über Audio -\> Text-zu-Sprache.

Da die originale Text-to-speech Stimme eines Betriebssystems meist
Englisch spricht klingt diese meist störend. Wenn man dieses Feature in
einer deutschen Stimme mit guter Qualität haben möchte muss man sich
entweder teure Software kaufen, oder man handelt [das Tutorial von
Mumble-Tower
ab](http://mumble-tower.de/tutorial/alternative-Sprecher-mit-MBROLA-und-espeak),
welches erklärt wie man dies mit knapp 5 Minuten Arbeit gratis hin
bekommt.

Unter Konfiguration -\> Einstellungen kannst Du für Text-zu-Sprache die
Punkte auswählen, welche Du "vorgelesen" bekommen möchtest, wie laut die
Stimme Dir vor liest und ab Welcher Textlänge diese Funktion nicht
startet, damit du nicht 5 Minuten lang einem 1000 Zeichen-Text lauschen
musst.

### Lautstärke

**Erweiterte Konfiguration**

Mumble passt automatisch die Ausgabelautstärke der einzelnen User an, so
dass deren Lautstärke nahe zu identisch ist. Du kannst allerdings
trotzdem gewisse Änderungen im Bezug auf die Lautstärkeregelung
vornehmen unter Konfiguration -\> Audio-Ausgabe.

Hier kannst Du die "Lautstärke" von Mumble generell höher und niedriger
stellen, oder das Verhalten "Andere Anwendungen" steuern. Letzteres
reduziert die Lautstärke aller anderen Anwendungen während Du von Mumble
ein Audiosignal erhältst, wodurch Du sogar bei lauten spielen oder Musik
alle Ansagen verstehen dürftest. Im Normalfall werden andere Anwendungen
in diesem Fall auf 50% ihrer aktuellen Lautstärke reduziert. Je nach
Geschmack lässt sich dieser Wert Variieren wodurch Du z.B. alle anderen
Anwendungen komplett ausblenden kannst (0%), oder diese Funktion, wenn
sie Dich irritieren sollte, deaktivieren kannst (100%).

### Flüstern

Seit Mumble 1.2.0 gibt es ein besonders interessantes Feature: Die
Fähigkeit zu einem Bestimmten Channel oder User zu Flüstern. Hierfür
musst du eine Tastenkombination einrichten: Konfiguration -\>
Tastenkürzel und klicke auf "Hinzufügen". In der Tabelle müsste ein
neuer, leerer Eintrag erscheinen. Un der Funktion Spalte klicke doppelt
um im Drop-Down-Menü "Flüstern" auszuwählen. Klicke nun doppelt auf das
Datenfeld und dann auf "**...**".

Es wird sich ein Fenster öffnen in dem Du auswählen kannst ob Du zu
einem User oder an Channel Flüstern willst.

Wenn Du an User Flüstern willst klicke in der Drop-Down-Liste auf einen
Namen und klicke auf "Hinzufügen". Diesen Vorgang kannst Du für mehrere
User wiederholen wodurch Du mit einer Taste zu mehreren Usern Flüstern
kannst. Wenn Du einen Haken bei "Ignoriere positionsabhängiges Audio"
setzt wird Deine Stimme immer zentriert Übertragen, egal ob Ihr euch in
einem Spiel befindet und dort an unterschiedlichen Stellen steht, oder
nicht. **Hinweis: Die User die Du zu deiner Flüsterliste hinzufügen
willst, müssen entweder auf dem aktuellen Server sein, oder sich in
Deiner "Freundesliste" befinden.**

"An den Kanal flüstern" dürfte selbsterklärend sein.

### Sounddateien

**Erweiterte Konfiguration**

Ab Mumble 1.2.0 kannst Du Events mit Sounddateien, wie z.B. .ogg und
unkomprimierte .wav (für eine Gesamtliste der unterstützten Formate
schau [hier](http://www.mega-nerd.com/libsndfile/#Features)),
hervorheben.

Gehe dafür Konfiguration -\> Nachrichten und schaue in die Sounddatei
und Pfad Spalten

Klicke doppelt auf die "Pfad" Spalte und ein Explorer-Fenster wird sich
öffnen. Suche Dir eine unterstützte Sounddatei und klicke doppelt auf
sie, somit weist Du dem Event diese Sounddatei zu. Wenn Du diese
Sounddatei auch aktivieren willst musst Du nur einen Haken in der
richtigen Zeile der "Sounddatei" Spalte setzen. **Merke: Es gibt
Standard-Sounds zu einigen Events. Um diese zu aktivieren setzte einfach
den dazugehörigen Haken.**

## Nutzerberechtigungen

**Erweiterte Konfiguration**

### ACL/Gruppen

Wenn Du ein Server-Admin bist oder aus anderen Gründen wissen willst wie
man einen Channel einrichtet, lies bitte [dies
hier](Murmurguide#Becoming_Administrator_and_Registering_a_User "wikilink").
Lese diesbezüglich bitte "Becoming Administrator and Registering a
User", "ACLs" und "Access Tokens".

### Zugriffscodes

Ein weiteres tolles Feature von 1.2.0 sind die Zugriffscodes. Man kann
sie am Besten als eine Art Passwort betrachten. Wenn Du einen
Zugriffscode hast der mit der Zugriffscode Gruppe im ACL des Channels
übereinstimmt, kannst Du diesen Channel betreten. Stell Dir dies am
Besten wie eine Gruppe mit den nötigen Zugriffsrechten vor, zu der Du
Dich selber hinzufügen kannst in dem Du das Nötige Passwort kennst, oder
in dem Dich jemand dieser Gruppe hinzufügt.

Sobald Du den Namen eines Zugriffscodes herausgefunden hast gehe zu
Server -\> Zugriffscodes und füge ihn für den Channel dem Du beitreten
willst hinzu. Merke: Zugriffscodes sind immer auf einen Server bezogen,
dadurch kannst Du sie nicht auf einem anderen Server, als den für den Du
sie eingerichtet hast, verwenden.

### Zertifikats- und Passwort-Speicherung unterdrücken

Manchmal kann es vorkommen, dass Du z.B. aus Testzwecken als
unregistrierter User auf Deinen Server connecten willst/musst. Um das zu
bewerkstelligen gehe Konfiguration -\> Netzwerk und setzte einen Haken
bei "Zertifikats- und Passwort-Speicherung unterdrücken". Dies bringt
alle Server dazu sich nicht an Dein Passwort und Zertifikat zu erinnern.
Wenn Du allerdings den Server in deinen Favoriten hast musst Du auch
deinen Benutzernamen ändern, sonst wird Mumble Dich weiterhin nach einem
Passwort fragen.

## Alles Weitere

Wenn Du weiterhin ein Problem hast, dass Du nicht gelöst bekommst, komm
doch in den [Mumble IRC channel](irc://irc.freenode.org/mumble), dort
wird man bemüht sein, Dir zu helfen.

[Category:Documentation
German](Category:Documentation_German "wikilink")