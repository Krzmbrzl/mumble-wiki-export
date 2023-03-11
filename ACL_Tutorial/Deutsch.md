# ACL Tutorial

In diesem Tutorial wird euch erklärt wie die Rechteverwaltung in Mumble
funktioniert. Details hierüber findet ihr auch in der [ACL
FAQ](ACL_FAQ/Deutsch "wikilink"), in welcher unter anderem einige
Beispiele und Erklärungen von speziellen Gruppen zu finden sind.

## Wie wir vorgehen

Wir setzen einen Server mit einem *General chat* Kanal auf, in welchem
jeder sprechen kann. Desweiteren erstellen wir einen *Custom channels*
Kanal, in welchem jeder registrierte Benutzer seinen eigenen Kanal
erstellen und administrieren kann. Anschließend werden wir als normaler,
registrierter Benutzer einige Kanäle für ein FPS Spiel erstellen, in
welchen Leute entweder zu ihrem Team oder zu jedem anderen sprechen
können und das per Tastendruck.

Genug geredet, lasst uns anfangen\!

## Rechte setzen für den gesamten Server

Zuerst brauchen wir ein Passwort für den SuperUser. Hat dieser noch kein
Passwort, dann kannst Du ihm jetzt eines geben. Gib einfach an der
Konsole bzw. am Befehlsprompt folgendes ein:

`murmur -ini /path/to/murmur.ini -supw meinganztollesgeheimespasswort`

Dann öffnen wir Mumble und verbinden uns mit dem Server. Login:
SuperUser und das Passwort welches wir ihm gegeben haben. Dann schaut
das in etwa so aus:

(Bild fehlt)

Lasst uns anfangen mit den Berechtigungen. Öffne den ACL Editor, Du
kannst das mit einem Rechtsklick machen. Wenn geschehen, dann siehst Du
ein Fenster mit zwei Tabs. Der erste dient der Gruppenadministration, wo
man Benutzer Gruppen zuordnen kann, etc. Der zweite ordnet
Berechtigungen den Gruppen zu.

In eben jenem ACL Tab (wo die Berechtigungen den Gruppen zugeordnet
werden) sollen zwei Regeln gesetzt werden:

Die erste erlaubt registrierten Benutzern (allen in der @auth Gruppe),
Kanäle im Root Channel zu erstellen sowie deren Unterkanäle. Die zweite
erlaubt allen Benutzern in der @admin Gruppe, Berechtigungen zu
schreiben / zu setzen.

Jetzt erstmal löschen wir die Regel die mit der @auth Gruppe verbunden
ist, indem wir diese selektieren und auf "Entfernen" klicken. Wir sagen,
dass wir niemanden im Root Kanal (Allerersten Kanal) wollen. Wir wollen
einen *General Chat* Kanal dafür. Wir fügen also eine Regel hinzu, um
die User aus dem Root Kanal rauszuhalten. Um dies zu tun, klicke auf
Hinzufügen und klick jede Checkbox in der Spalte "Ablehnen" an, ausser
Traverse.

Warum nicht Traverse anklicken: Ganz einfach, dies würde Leuten
verbieten, den Root Kanal UND alle Unterkanäle zu betreten. Da jeder
andere Kanal ein Unterkanal von ROOT ist, kann dann kein User
irgendeinen Kanal betreten. Also lassen wir Traverse ohne Haken. Ihr
müsst bei TRAVERSE nicht erlaubt anklicken, da TRAVERSE standardmässig
erlaubt ist. Standardeinstellungen sind:

  - Erlaubt: TRAVERSE, BETRETEN, SPRECHEN und ALTERNATIV SPRECHEN
  - ABLEHNEN: SCHREIBEN, STUMM/TAUBSTELLEN, VERSCHIEBEN/KICK, CHANNEL
    ERSTELLEN und CHANNEL VERBINDEN.

Falls Du dich wunderst, ja wir haben Schreiben, Stumm/Taubstellen,
Verschieben/Kick, Channel erstellen und Channel verbinden nicht markiert
und sie sind verboten. Man muss diese Rechte nicht auf ablehnen stellen,
da diese per Standard abgelehnt sind (wenn wir diese nicht explizit
erlauben). Jetzt schaut euer Bildschirm aus wie dieser hier (ausgenommen
ihr habt einige nutzlose Checks deaktiviert):

(Bild fehlt)

Regeln werden in Mumble von oben nach unten ausgeführt. Das bedeutet,
die

`@admins allow write`

Regel ist nutzlos, sie wird überschrieben durch die

`@all deny write ...`

Also müssen wir das reparieren. Wähle einfach die Regel welche @all
regelt und klicke auf "Hoch". Das bringt diese Regel ganz nach oben. Du
hast nun einige Standardeinstellungen für den gesamten Server etabliert.

(Bild fehlt)

## Erstellung des *General Chat* Kanal und die Einstellung seiner Berechtigungen

Dieser Kanal soll als Chatraum für jeden der unseren Kanal betritt, zur
Verfügung stehen. Solange wir ihnen nicht das sprechen im Root Kanal
erlauben und sie müssen diesen Kanal *General Chat* betreten wenn sie
chatten (sprechen) wollen, dann sollten wir eine Willkommensnachricht
einrichten auf dem Server, die darauf hinweist. Ok weiter gehts. Zuerst
erstelle den Kanal. Das ist ganz einfach, klick Channel-\>Add (oder
Rechtsklick in den Channel den du möchtest, und klick Add um einen
Unterkanal zu erstellen, aber du weisst, der Root Kanal wird nicht
angezeigt, so benutzen wir das Menü). In der Box welche erscheint, gib
den Kanal Name *General Chat* ein und klicke "Ok", das wars.

Jetzt wollen wir jedem das Recht einräumen, in diesem Kanal zu sprechen.
Also gehen wir zu "ACL editieren" (vergiss nicht, vorher den neuen Kanal
auszuwählen). Du siehst die Regeln des Root Kanals im *General Chat*
Kanal, aber wenn du diese anwählst, dann siehst du dass diese ausgegraut
sind. Warum? Diese Regeln wurden vom übergeordneten Kanal (in diesem
Fall dem *Root Kanal* vererbt. Wenn Du die Checkbox ACLs erben
deaktivierst, dann verschwinden sie, aber wir wollen das nicht. Füge
einfach nur eine neue Regel hinzu welche jedem (Gruppe = @all) erlaubt,
den Raum zu betreten, zu sprechen oder AltSpeak zu nutzen und klicke
"Ok" um das zu speichern. Wir sind fertig mit diesem Kanal. Einfach,
oder nicht?

(Bild fehlt)

## Erstellen des *Custom channels* Kanal und dessen Konfiguration

So wie wir sagten, wir wollen jeden, der registriert ist, hier seine
eigenen Kanäle erstellen lassen. Der erste Schritt ist einfach, erstelle
den Kanal wie zuvor den anderen. Du solltest etwas in der Art wie hier
gezeigt vor der Nase haben:

(Bild fehlt)

Nun wollen wir das Recht *Channel erstellen* jedem registrierten (@auth)
Benutzer geben. Geh einfach in den ACL Editor für diesen Kanal
(auswählen des Kanals nicht vergessen), füge eine neue Regel ein, in
der Gruppenliste wähle oder schreibe auth und wähle die Channel
Erstellen Checkbox in der Spalte Erlauben. **Warnung:** Wenn Du den
Gruppennamen eingibst, stelle sicher dass Du "ENTER" drückst wenn du
fertig bist mit dem eingeben. Das aktualisiert die Regelgruppe. Du
kannst sehen, wenn Du kein "ENTER" drückst, dann wird in der Anzeige
oben der Name der Gruppe nicht geändert (in unserem Fall in @auth, da
steht dann immer noch @all).

(Bild fehlt) (Bild fehlt)

Und nun haben wir einen hübschen Kanal wo Leute ihre eigenen Kanäle
kreieren können. Beachte das sie den *Custom Channels* Kanal nicht
betreten können. Aber sie können ihre Unterkanäle kreieren. Ist das
nicht Cool?

# Registrierte Benutzer

Hier wollen wir einen registrierten und authentifizierten Spieler
spielen mit einem seeeeeehr originellen Namen: AuthedPlayer. Er möchte
seine eigenen Kanäle kreieren, um ein paar öffentliche Kanäle und zwei
private Unterkanäle anzubieten, einen für jedes Team eines FPS Spiels.
Er möchte dass sie zu ihrem Team oder zu beiden Teams sprechen können.
Wir schauen wie wir das mit AltSpeak machen können, Kanäle verbinden und
mehr.

## Erstellen des Hauptkanals

Nach dem Einloggen, spielen wir ein bisschen in Mumble um zu prüfen dass
wir den Root Kanal nicht betreten können nachdem wir ihn verlassen haben
(wenn du den Server das erste mal connectest, dann landest Du im Root
Kanal), weiterhin auch um zu prüfen, dass wir den *Custom channels*
Kanal nicht betreten können, etc. Wenn wir uns überzeugt haben, dass
dies funktioniert wie wir es uns vorgestellt haben, erstellen wir
unseren ersten Kanal. Einfach Rechtsklick in *Custom channels* (Vergiss
nicht, du kannst auch das Menü verwenden, nachdem der Kanal markiert
wurde) und klicke "Hinzufügen", um einen neuen Kanal unter *Custom
channels* zu erstellen. Da ich (Javitonino) sehr kreativ bin, nenne ich
ihn *My Private Channel*. Wir wurden in diesem Kanal automatisch der
@admin Gruppe hinzugefügt, so können wir auf ihm schreiben (die ACLs)
(Vergiss nicht die Regeln im *Root Kanal?*Sie sind vererbt komplett
runter bis in unseren Kanal). Aber das bedeutet auch, das wir das
*Channel erstellen* Recht vererbt bekommen haben, so kann jeder
registrierte Benutzer in UNSEREM Kanal Kanäle erstellen. Das wollen wir
so nicht haben.

(Bild fehlt)

Unsere Regel überschreibt die vererbte, weil vererbte Regeln oben stehen
(werden durch darunter folgende Regeln überschrieben). So wenn wir
UNSEREN Kanal gesichert haben, dann geben wir die Erlaubnis, diesen zu
betreten und darin zu sprechen:

(Bild fehlt)

Beachte, dass wir *Betrifft Unterkanäle* deaktiviert haben. Genauso wie
Unterkanäle nicht öffentlich sind, wollen wir auch nicht dass diese das
*Betreten* Recht gewähren. Wenn wir diese Option nicht deaktiviert
haben, dann müssen wir eine andere Regel erstellen um das *Betreten*
Recht abzulehnen. Dies ist der einfachere Weg. Und nun haben wir diesen
Kanal bereit. Lasst uns mit den Unterkanälen fortfahren.

## Erstellen der Team Unterkanäle

Erst erstellen wir zwei Unterkanäle unseres eigenen Kanals. Weil
nützlich, benenne ich sie sehr kreativ .... Team1 und Team2. Wir können
Regel definieren für jeden der beiden, aber es ist schneller, diese im
übergeordneten Kanal (My Private Channel) zu definieren und lassen die
Unterkanäle diese Regeln erben. Erst wollen wir, das die Leute in einem
Teamkanal auch reden können, also machen wir das so wie hier:

(Bild fehlt)

Beachte, dass wir *Betrifft diesen Kanal* demarkiert haben, weil wir die
Regel NUR für die Unterkanäle definieren. Interessanter ist die Nutzung
der speziellen Gruppe *in*. Diese Gruppe umfasst die Leute welche sich
IN dem Kanal befinden, auf den sich die Regel bezieht. Es schaut so aus,
als ob das dasselbe ist wie @all aber es ist recht unterschiedlich:

Wir verbinden beide Kanäle. Das bedeutet, dass Leute in verschiedenen
Kanälen jeden im anderen verbundenen Kanal hört. Aber wir wollen, dass
Leute nur ihre Teamkollegen hören können. So benutzen wir *in* um das
Recht *Sprechen* den Leuten im selben Kanal zu geben. Das bedeutet, dass
Leute in Team2 nicht die Leute in Team1 hören können, weil die Leute in
Team1 nicht das Sprachrecht in Team2 haben weil die *in* Gruppe ihnen
die Rechte nur im eigenen Kanal gibt. Am Anfang ist es ein bisschen
kompliziert, das zu verstehen, aber es ist sehr nützlich. Um es zu
verstehen, verstehe erst, dass jeder Kanal seine eigenen *in*-Gruppen
hat. Das bedeutet dass die *in* Gruppe in Team1 nicht dieselbe ist wie
die *in* Gruppe in Team2.

Um das besser zu erklären benutze ich einige Namen...

  - Jack ist in Team1
  - John ist in Team2

Beide Kanäle sind verbunden, so dass die Stimme von einem Kanal in den
anderen übertragen wird so die Sprecher im Zielkanal (wo die Stimme
hinübertragen wird) Sprachrechte haben. Jack spricht aber John hört ihn
nicht, weil Jack kein Recht hat, in Team2 zu sprechen da er nicht in
Team2's *in* Gruppe ist. So wird seine Stimme nicht über den Kanallink
übertragen und John hört Jack nicht. Hätten wir *all* anstelle von *in*
für die Regel benutzt, dann würden Jack und John sich gegenseitig ohne
Probleme hören, weil beide in der *@all* Gruppe sind.

Ok lasst uns weitermachen. Wir wollen, dass die Leute zum anderen Team
sprechen können. Da ist dann AltSpeak praktisch. Wir fügen eine Regel
ein wie diese:

(Bild fehlt)

Dies erlaubt jedem (beiden Teams) zum jeweils anderen Team zu sprechen
wenn AltSpeak gedrückt wird. AltSpeak wird aktiviert solange eine Taste
gedrückt wird, welche in den Shortcuts definiert wurde (In Mumble
Konfiguration-\>Einstellungen-\>Shortcuts). Solange wir diese Taste
drücken, wird die Stimme durch die AltSpeak Rechte übertragen. Wenn wir
jedem das Recht *AltSpeak* erlaubt haben und beide Kanäle sind verbunden
bedeutet das, dass wenn jemand spricht solang er diese Taste drückt,
wird er von beiden Teams gehört.

Und wir sind fertig ;-)

## Wie schaut es aus für unregistrierte Spieler

Erst lädst du sie in deine Teamkanäle ein (Du kannst sie von deinem
öffentlichen Kanal in deinen Teamkanal ziehen mittels drag-and-drop).
Sie müssen dazu in Deinem öffentlichen Kanal sein, da du das *Move/Kick*
Recht in beiden, dem Original und Zielkanal brauchst. Wenn kein
AltSpeaking...

(Bild fehlt) (Bild fehlt)

Wenn AltSpeaking:

(Bild fehlt) (Bild fehlt)

# Abschliessende Hinweise

Dies ist ein Schnelltutorial und es wurden bei weitem nicht Alles
angesprochen. Zum Beispiel *Benutzerdefinierte Gruppen*. Hier eine kurze
Beschreibung:

  - Du definierst Rechte für diese Gruppe ganz simpel. Schreibe den
    gewünschten Gruppennamen (z.B. *Freunde*) in die Gruppenbox
    (Vergiss nicht, ENTER ist Dein Freund) und markiere die
    entsprechenden Checkboxen.
  - Um eine Person dieser Gruppe hinzuzufügen, gehe zum unteren Button
    Hinzufügen im ACL Editor, wähle den Gruppenname in der Gruppenbox
    (oder schreibe die Gruppe rein + ENTER), dann schreib den Namen den
    Du in der Box haben möchtest unten an der *Hinzufügen* Liste und
    drücke den zugehörigen "Hinzufügen" Knopf. Du kannst nur
    registrierte Nicknamen der Liste hinzufügen.

Gruppen sind pro Kanal und vererbar. Wenn du einige Gruppenmitglieder
beerben möchtest, dann kannst du "vererben" markieren und die Mitglieder
welche du in der Gruppe nicht haben möchtest, in die *Entfernen* Liste
aufnehmen (da ist ein Knopf am Ende der Vererbungsliste um es einfach zu
machen).

Ich hab also noch einige Möglichkeiten übrig vor der Benutzung der
*@sub* Gruppe. Mehr Infos darüber in [ACL und
Gruppen](ACL_FAQ_DEUTSCH "wikilink")

Es gibt viele Regeln welche einfacher gemacht werden könnten. Als
Beispiel, im letzten Abschnitt des Tutorials, du kannst das *Ablehnen
Channel erstellen* und das *Erlauben AltSpeak* in der selben Regel
festmachen und das für beide Kanäle und Unterkanäle. Das hier ist nur
ein Beispiel was man machen kann, ohne zu sehr in die Tiefe zu gehen,
fühl Dich frei deine eigenen unmöglich zu verstehenden Entwürfe zu
kreieren und füge sie der Beispielsektion in [ACL und
Gruppen](ACL_FAQ_DEUTSCH "wikilink") dazu.

[Category:Documentation
German](Category:Documentation_German "wikilink")