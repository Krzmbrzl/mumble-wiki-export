**Hinweis: Um die Reiter *Gruppen* und *Berechtigungen* beim
*Bearbeiten* eines Kanals sehen zu können, muss in *Konfiguration -\>
Einstellungen* der Haken bei *Erweitert* gesetzt sein.**

# Gruppen

Um eine Gruppe zu bearbeiten oder hinzuzufügen, klicken Sie mit der
rechten Maustaste auf den Hauptkanal und dann "Bearbeiten". Zwecks
einfacherer Verwaltung ist es empfehlenswert Gruppen zum Hauptkanal
hinzuzufügen. Nun klicken Sie auf den Reiter "Gruppen". Dort können Sie
entweder eine Gruppe auswählen oder eine neue erstellen, indem Sie im
leeren Feld "Gruppe" den Namen eintippen und die Eingabetaste drücken.
Nachdem die Gruppe ausgewählt ist, fügen Sie ihr Benutzer hinzu, indem
Sie deren registrierten Namen im unteren linken Feld ("Mitglieder")
eingeben und auf "Hinzufügen" klicken.

Gruppen sind an einen bestimmten Kanal gebunden, können aber auch von
Unterkanälen geerbt (übernommen) werden, dafür müssen die Attribute
"Vererbbar" im übergeordneten Kanal (Elternkanal) und "Erben" im
Unterkanal gesetzt sein. So ergibt sich eine bequeme Möglichkeit, Kanäle
und deren Berechtigungen zu verwalten; konfigurieren Sie die
Berechtigungen an der Spitze des Kanalbaums, welcher gleichartige
Rechtestrukturen haben soll, und ändern Sie einfach nur die
Gruppenzugehörigkeiten in den Unterkanälen.

Eine Gruppe hat für jeden Kanal 3 Datenteile:
1\. "Mitglieder": Spieler, die zur Gruppe hinzugefügt werden sollen,
z.B. weil sie im übergeordneten Kanal (Elternkanal) nicht dieser
angehören,
2\. "Geerbte Mitglieder": Mitglieder, die von der gleichnamigen Gruppe
des übergeordneten Kanals (Elternkanal) geerbt wurden und
3\. "Ausgeschlossene Mitglieder": geerbete Mitglieder, welche aus der
Gruppe entfernt werden sollen.

## Beispiele


Nehmen wir ein praktisches Beispiel, die *admin*-Gruppe. Immer wenn ein
Spieler einen Kanal erstellt, wird er automatisch dessen *admin*-Gruppe
hinzugefügt. Das gibt ihm nicht automatisch irgendwelche Rechte, es
markiert ihn lediglich als *Mitglied* dieser Gruppe, allerdings wird in
Murmurs Standardinstallation der Gruppe *admin* das Recht zum
*Berechtigungen bearbeiten* (voller Zugriff) zugewiesen.

In einer Struktur wie dieser:
\* Hauptkanal

  -   - A
          - B
      - C
          - D

ist Spieler "BigBoss" im Hauptkanal alleiniges Mitglied der Gruppe
*admin*. In Kanal A steht Spieler "Boss A" in der *Mitglieder*-Liste der
Gruppe *admin*, für "Boss B" gilt das gleiche in Kanal B.

Im Hauptkanal und in den Kanälen A und B sind für die Gruppe *admin* die
Attribute *Erben* und *Vererbbar* gesetzt (Standardeinstellung in
Murmur). Ein Spieler, der *Mitglied* der Gruppe in einem dieser Kanäle
ist, ist ein *geerbtes Mitglied* in einem untergeordneten Kanal, für den
das Gruppenattribut *Erben* gesetzt ist. Somit ist die Gesamtliste der
*Mitglieder* von *admin* in Kanal B folgende: Big Boss, Boss A und Boss
B. Der Nutzen dieses Systems ist, dass, wenn wir später den Spieler
"Super Boss" zur *admin*-Gruppe im Hauptkanal hinzufügen, dann wird er
automatisch Admin in den untergeordneten Kanälen A und B.

Fahren wir fort und nehmen an, dass Spieler "Boss C" *Mitglied* von
*admin* in Kanal C ist, nur hier ist für *admin* das Attribut *Erben*
**nicht** gesetzt. Das bedeutet, dass "Big Boss" hier in Kanal C
**nicht** in der *admin*-Gruppe und jede Änderung für *admin* im
Hauptkanal nicht wirksam ist. Kanal D erbt die Liste von C, außer wenn
in C für *admin* *Vererbbar* ebenfalls nicht gesetzt ist.

# Berechtigungen (ACL)

Die Liste der *Berechtigungen* ist einem bestimmten Kanal zugeordnet.
Ein Kanal kann bestimmen, ob er die Berechtigungen seines Elternkanals
erbt, aber nicht welche; es heißt alle oder keine. Berechtigungen werden
der Reihe nach, von oben nach unten entlang der Kette von Kanälen,
ausgewertet. Um Berechtigungen hinzuzufügen oder zu entfernen, klickt
man mit der rechten Maustaste auf den Kanal, für den man diese
Änderungen durchführen möchte, dann auf *Bearbeiten* und wechselt zum
Reiter *Berechtigungen*. Nach einem Klick auf *Hinzufügen* wird der Name
der *Gruppe*, für die die Berechtigungen gelten sollen, im unteren
linken Feld (*Gruppe*) eingegeben bzw. ausgewählt. Will man nur die
Berechtigungen für einen einzelnen Benutzer festlegen, gibt man dessen
Namen bei *Benutzer ID* ein und lässt das Feld *Gruppe* frei.

Jeder Eintrag in der Liste trifft entweder auf einen Benutzer oder eine
Gruppe zu. Ein Benutzer muss ein bestimmter
<u>[registrierter](Mumbleguide_Deutsch#Registrieren "wikilink")</u>
Benutzer sein, während eine Gruppe irgendeine sein kann, die gültig ist,
in dem Kanal für den die Berechtigungen definiert werden. Es ist zu
beachten, dass die Gruppenzugehörigkeit in dem Kanal überprüft wird, in
dem die Berechtigungen <u>angewendet</u> werden, was für vererbte
Berechtigungen wichtig ist, beginnt der Gruppenname hingegen mit "\~",
erfolgt diese Auswertung im Kontext des Kanals in dem die Berechtigungen
<u>definiert</u> sind. Für eine Gruppe, die mit "\!" beginnt, wird die
Mitgliedschaft umgekehrt, d.h. eine solche Regel betrifft alle
<u>nicht</u> der Gruppe angehörenden Benutzer.

<b> all (Alle/Jeder)

auth (Alle registrierte User)

in (Alle User in dem aktuellen Kanal)

out (Alle User ausserhalb des aktuellen Kanals) </b>

Für jeden Eintrag sind die Rechte entweder erlaubt oder verboten; Für
den Fall eines Konfliktes hat der letzte Eintrag Vorrang. (Anmerkung von
BarefeetXanadu: Daher wird beim Sperren eines Kanals erst für @all das
Betreten verboten und dann für einige User oder alle registrierten @auth
das Betreten erlaubt. Wenn man erst erlaubt für einige und dann z.B:
@all verbietet, dann wirkt eben das letzte, das verboten für @all und
die ACL funktioniert dann nicht wie gewünscht.). Erinnere Dich daran,
dass alle Einträge der Reihe nach ausgewertet werden, hast Du also
folgende Reihenfolge:

<b> @all deny speak (@all verbiete sprechen)
@all allow speak (@all erlaube sprechen)
</b> Dann kann jeder sprechen.

<b> @all allow speak
@all deny speak

</b> wird jedem das Sprechen verbieten.
(siehe auch meine Anmerkung bzgl. Raum betreten oder nicht).

Jeder Eintrag kann markiert werden, ob er sich auf den aktuellen Kanal,
den Unterkanal oder auf beide bezieht. In der Regel willst Du dass der
Eintrag sich auf beide bezieht. Erinnere Dich, wenn ein Eintrag sich auf
einen Unterkanal beziehen soll, dass Du den Eintrag auf den Unterkanal
anwendest <b>und</b> die Vererbung in den Unterkanälen erlaubst.



\== Die @sub Gruppe ==

Es gibt eine spezielle Gruppe namens *sub*, welche genau wie *all* eine
spezielle Bedeutung hat. Sub wird in der Form *sub,a,b,c* verwendet,
wobei *a* die minimale Anzahl gemeinsamer Eltern ist, während *b* und
*c* die Pfadtiefe beschränken:

  - b ist die minimale und c die maximale Pfadlänge, gemessen von dem
    Kanal auf den a sich bezieht.
  - Fehlt irgendeiner dieser Parameter, dann gibt es keine
    minimale/maximale Pfadlänge.

Es ist etwas komplex, aber auch ziemlich mächtig. Nehmen wir
beispielsweise folgende Baumstruktur:

  - Hauptkanal
      - A
          - A1
              - Sub1
              - Sub2
          - A2
          - A3
      - B
          - B1
          - B2

Für den Anfang verbieten wir *all* das Betreten des *Hauptkanals*. Dann
defineren wir in A:

`@~sub,0,1 +enter`

Diese Berechtigung (ACL) wird zu allererst im Kontext des definierenden
Kanals ausgewertet, weil die Gruppe mit \~ beginnt.

Der erste Parameter (a=0) zeigt an, wieviele weitere Elemente des
Pfadnamens übereinstimmen müssen. Eine 0 bedeutet, wir benötigen eine
Übereinstimmung bis an diesen Punkt. Dies bedeutet, dass irgendein
Spieler in einem Kanal unter dem Pfad *Hauptkanal.A* als übereinstimmend
(zutreffend) gewertet wird. Wäre der Parameter 1, und wir befänden uns
im Kanal Sub2, dann müsste der Pfad des Spielers mit Hauptkanal.A.Sub1
übereinstimmen. Positive Werte machen nur für festgenagelte/gepinnte
(pinned) Gruppen (die mit \~) Sinn.

Der zweite Parameter fordert, dass der Pfad des zu bewertenden Kanals um
mindestens ein Element länger sein muss als der Pfad des Kanals, in dem
diese Berechtigung (ACL) definiert ist. Also wird diese Regel in allem,
was mit Hauptkanal.A beginnt, und zumindest ein Element mehr hat,
zutreffen.

Zusammenfassend ist festzustellen: Diese Regel erlaubt jedem in einem
von A nachkommenden Kanal (nicht in A selber), den Kanal A oder
irgendeinen A nachkommenden Kanal zu betreten. (Wir unterstellen, dass
die Unterkanäle diese Regel vererben).

Wenn wir die Tilde \~ nicht benutzen, dann ist es Leuten in den von A
nachkommenden Kanälen erlaubt, nach oben zu gehen (z.B: von Sub1 nach A1
oder nach A aber nicht die andere Richtung, also nicht A1 nach Sub1)
oder in anderen Worten: "Erlaube den Spielern in den Nachkommen eines
Kanals (irgendeine Tiefe), den Kanal zu betreten (z.B. erlaube den
Spielern in A1, den A zu betreten.)

Lasst uns dem Kanal A1 eine neue Regel geben.

`@sub,-1,0 +link`

Dies erlaubt jedem im Ursprungskanal (gleiche Pfade bis auf -1 Elemente
(der erste Parameter) oder irgendeiner der Geschwister (Pfadlänge gleich
(der 0 Parameter)), zu diesem Kanal zu linken.

Zum Abschluss einfach um zu zeigen wie derangiert es gehen kann, lasst
uns zu Kanal B folgende Regel hinzufügen:

`@~sub,-1,2,2 +enter`

Dies lässt jeden, der in einem nachkommenden Kanal des Hauptkanals
(Ursprung von B) ist, und eine Pfadlänge von exakt 2 hat (Länge von
Hauptkanal.B -1+2) den Hauptkanal betreten. Diese Regel würde
übereinstimmen mit jemandem in A1, aber nicht A oder Sub1.

## Kanalpasswörter und Zugriffscodes (Access Tokens)

### Zugriffscodes konfigurieren

### Zugriffscodes benutzen

# Die Rechte

## Write (Schreiben)


Dies gibt totale Kontrolle über den Kanal, inkl. der Fähigkeit, die ACL
zu editieren. Dieses Privileg schliesst alle anderen Privilegien mit
ein.

\== Traverse (Durchqueren) ==
Ohne dieses Privileg kann ein Spieler auf den Kanal oder irgendeinen
Unterkanal nicht zugreifen, egal auf welchem Weg, ohne Rücksicht auf
Privilegien in Unterkanälen. Verweigere dieses Privileg nicht, ausser Du
weisst genau was du tust. Du kannst den Effekt den du möchtest, besser
erreichen wenn du das Recht des Betretens (Enter) verbietest (Deny).


## Enter (Betreten)


Erlaubt Spielern, den Kanal zu betreten. Ohne das Privileg kann ein
Spieler dennoch in den Kanal gemoved werden (vom Admin der Spieler moven
kann).

\== Speak (Sprechen) ==
Erlaubt Spielern, im Kanal zu sprechen. Für verlinkte Kanäle, nur die
Spieler mit Sprechprivileg in den Zielkanälen (Wo der Link hinzielt)
können gehört werden. Dies kann genutzt werden um eine Hierarchie
aufzubauen, in der alle Spieler alle Leader jeder Gruppe hören können,
aber normal wird die Sprache der Spieler nicht ausserhalb deren Kanals
übertragen.
Auf diese Weise hören Spieler irgendeinen anderen zum Gruppenführer
sprechen und hören mit Sprechen (hoffentlich) auf für kurze Zeit.
Wenn ein Spieler einen Kanal betritt in dem er kein Recht auf Sprechen
hat, dann wird er vom Server "unterdrückt", und ist unfähig zu sprechen
bis ihn irgendjemand "unmuted" also das "Stumm" entfernt.


\== Mute/Deafen (Stumm/Taub) ==
Erlaubt einem Spieler andere Spieler stumm oder taub zu stellen. Der
Spieler bleibt solange stumm bis der Status entweder manuell rückgängig
gemacht wird, oder er sich neu auf den Server verbindet.



## Move (Spieler ziehen)


Erlaubt einem Spieler, einen anderen Spieler in einen anderen Raum zu
ziehen. (Need Correction: Ausser der angezielte Spieler hat ENTER Rechte
in den Kanälen in die er gezogen wurde, Move Rechte werden in beiden
Kanälen benötigt.)


\== Make Channel (Erstelle Kanal)== Erlaubt einem Spieler einen
Unterkanal in einem Kanal zu erstellen. Der Spieler wird automatisch der
<i>admin</i> Gruppe des neuen Kanals hinzugefügt, sodass er in diesem
Kanal und dessen Unterkanälen die Berechtigungen beliebig setzen kann.



## Link Channel (Verbinde Kanäle)


Erlaubt einem Spieler, Kanäle zu verbinden oder die Verbindungen zu
lösen. Um Verbindungen zu lösen braucht man Linkrechte in einem von den
beiden Kanälen, zum Verbinden benötigt man Linkrechte in BEIDEN
Kanälen.



## AltSpeak or Whisper (Alternativ Sprechen oder Flüstern)

Erlaubt einem Spieler, in einem Kanal mittels der ALT-PTT Taste zu
sprechen. (Kann im Shortcuts Menü konfiguriert werden). Es arbeitet als
Sprechmöglichkeit für verbundene Kanäle etc. AltSpeak erkennt ihr am
grünen Mund.

In der 1.2.x Serie wurde die ALT-PTT durch Flüstern ersezt. Um Flüstern
auf die ALT-PTT Funktion zu schalten, muss auf Daten auf den "..." Knopf
gedrückt werden, und folgende Punkte aktiviert werden:

  - An den Kanal Flüstern
  - Aktueller Kanal
  - An verbundene Kanäle flüstern



## Text Message (Textnachricht)

Erlaubt oder verweigert die Textnachrichten der Benutzer.


## Add Temporary Channel (Temporären Kanal erstellen)

Mit dieser Funktion können von Benutzer oder Gruppen Kanäle erstellt
werden, welche automatisch gelöscht werden, wenn der letzte Benutzer den
Kanal verlässt. (Hinweis: es können keine Unterkanäle erstellt werden)


## Kick (Kicken)

Hiermit lassen sich Benutzer vom Server werfen. Diese Funktion erscheint
nur im Hauptkanal.


## Ban (Bannen)

Mit Bannen kickt und schließt man Benutzer aus dem Server aus, die auf
dem Server nicht Willkommen sind. Diese Funktion erscheint nur im
Hauptkanal.


## Register User (Benutzer registrieren)

Erforderlich um andere Benutzer zu registrieren. Der Benutzer, der
registriert werden soll, muss ein Zertifikat haben.


## Self Register (Selber registrieren)

Standardmäßig allen Benutzern erlaubt. Notwendig um sich selbst mit den
eigenen Zertifikat auf den Server zu registrieren.

# Beispiele

## Gruppen von FPS Game Servern


\=== Methode 1 === In dem ersten Beispiel nehmen wir an, wir haben eine
Gruppe von FPS Public Game Server. Jedes Spiel hat zwei konkurrierende
Seiten, und jede Seite besteht aus einem oder mehreren Squads. Wir
wollen eine Hierarchie wie diese hier:

\* Servers
\*\* "Servername"
\*\*\* Team 1
\*\*\*\* Squad 1
\*\*\*\* Squad 2
\*\*\*\* ............
\*\*\* Team 2
\*\*\*\* Squad 1
\*\*\*\* Squad 2
\*\*\*\* ............
\*\*\*\* .............
\*\*\*\* ..................


Lasst uns annehmen, wir haben ein kleines Skript mit qstat gelinkt,
welches die Spieler in den Kanal auf der rechten Seite steckt und eines
in dem wir ihnen die Fähigkeit geben wollen zwischen den Squad Kanälen
zu wechseln und beliebig zu linken (verbinden). Aber wir wollen nicht,
dass sie Zugriff auf die andere Seite erhalten.

Aktuell ist das eine sehr eindeutige Implementation; Auf den "Server"
Kanälen definieren wir eine leere Gruppe welche sich "Spieler" nennt.
Dann fügen wir der Gruppe folgende ACL hinzu.

1\. @all deny enter
2\. @\~sub,2,2 allow enter, allow link

Die erste Regel verbietet den Spielern das Betreten, die zweite Regel
erlaubt jedem innerhalb einer Hierarchie mindestens zwei Elemente von
"Server" abwärts, nach eigenem Wunsch zu linken und zu "moven".
Praktisch heisst dass wenn ein Spieler im Team 1 ist, kann er in Team 1
sich frei bewegen aber er kann nicht zum anderen Team oder zu einem
anderen Server Unterkanal wechseln.


\=== Methode 2 === In dem zweiten Beispiel nehmen wir an, wir haben eine
Gruppe von FPS Public Game Server. Jedes Spiel hat auch hier zwei
konkurrierende Seiten, und jede Seite besteht aus einem oder mehreren
Squads. Wir wollen hier ebenfalls eine Hierarchie wie diese hier:

\* Servers
\*\* "Servername"
\*\*\* Team 1
\*\*\*\* Squad 1
\*\*\*\* Squad 2
\*\*\*\* ............
\*\*\* Team 2
\*\*\*\* Squad 1
\*\*\*\* Squad 2
\*\*\*\* ............
\*\*\*\* .............
\*\*\*\* ..................

Nun werden die Team und Squad Kanläle miteinander verknüpft.

Die Kanäle Team 1 und Team 2 muss in **Berechtigungen** müssen folgende
ACLs eingetragen werden.
1\. **@out** "**Sprechen**" "**Flüstern ak. AltSpeak**" verweigern.
2\. **@sub** "**Flüstern ak. AltSpeak**" erlauben und bei **Betrifft
Unterkanäle** häckchen entfernen
3\. **@\~sub** fügt **,-1,1,1** mit Enter ein **@\~sub,-1,1,1** ,
**Betrifft Unterkanäle** häckchen entfernen und erlaubt **Flüstern ak.
AltSpeak** Die Squad Kanäle müssen nun Bearbeitet werden

`1. `**`@~sub,-1,0`**` erlaubt `**`Sprechen`**` `
` 2. `**`@~sub,-1,1,1`**` verweigert `**`Sprechen`**` `
` 3. `**`@~sub,-1,0,1`**` erlaubt `**`Flüstern``   ``ak.``
 ``AltSpeak`**` `
` 4. `**`@in`**` erlaubt `**`Sprechen`**


Die Alt-Speak Taste muss bei jeden Spieler festgelegt werden. [In 1.2.x
heist es jetzt
Flüstern](FAQ_Deutsch#Wo_ist_die_Alt-Speak_Funktion_in_1.2.x_hin.3F "wikilink").

Nun kann die Team Leitung in die Team Kanäle und die Spieler sich in die
Squad kanäle begeben. Die Team Leitung kann mit den Squads Sprechen,
jedoch müssen die Squads die Flüstern bzw. AltSpeak Taste drücken um mit
der Team Leitung bzw. anderen Squads des Teams zu Sprechen.
Die Team Leiter können mit der Flüstern bzw. AltSpeak Taste miteinander
Sprechen.

Es ist empfehlenswert die Methode 1 mit Methode 2 zu kombinieren.
Allerdings ohne die "allow link" rechte

## MMORPG Raid

Folgend zwei Beispiel-Einrichtungen bei denen Raid- und Gruppen-Führer
von den Teilnehmern nicht gestört werden, und man damit ein 3-leveliges
Rechtesystem verwendet.

### 2-stufige Kanäle

Eine Möglichkeit ist für den Raid Unterkanäle für die verschiedenen
Typen an Teilnehmern zu erstellen, und den Führern einen übergeordneten
Kanal zuzuweisen.

Die Kanalstruktur sieht hierzu folgendermaßen aus:

`Root`
`  Raid`
`    Healers`
`    Tanks`
`    Damage Dealers`
`    Wussards and other Pets`

Hierbei ist Root ein beliebiger Eltern-Kanal, der für unser konkretes
Beispiel nicht von Relevanz ist.

Unser Wunsch ist es, einen Führer pro Gruppe zu haben, plus ein paar
Leute als Raidführer.

Dies wird wie folgt erreicht: Erstelle in *Raid* eine Gruppe welche sich
*Gruppenführer* nennt. Stecke den Führer von jeder Gruppe in diese
Gruppe. Im selben Kanal definiere die Gruppe *Raidführer* und füge sie
die Raidführer dieser Gruppe hinzu.

Im *Raid*-Kanal definiere folgende ACL:

`  1. @all deny enter, deny speak [Apply Here only]`
`  2. @raidleaders allow enter, allow speak, allow link, allow mute, allow kick [Apply Here and Apply Subs]`
`  3. @groupleaders allow speak, allow link [Apply Here only]`
`  4. @groupleaders allow link, allow mute, allow kick [Apply Subs only]`

Die erste Regel stellt sicher, dass niemand sprechen kann oder den
"Raid" Kanal betreten kann. Die zweite Regel hebt die erste Regel für
jeden Raidführer auf und gibt weitergehende Rechte. Die dritte Regel
stellt sicher, dass Gruppenführer zum "Raid" Kanal verbinden sowie
dorthin sprechen können, und die vierte Regel gibt den Gruppenführern
die Erlaubnis, vom Unterkanal zu verbinden ebenso wie lästige Leute
loszuwerden.

Normale Spieler sind nicht in der Lage, den "Raid" Kanal zu betreten
aber da diese Weigerung nur im "Raid" Kanal gilt, können sie alle
Unterkanäle betreten, welche sie wollen. Wenn die Kanäle verbunden sind,
kann jeder in den verbundenen Kanälen die Raidführer hören sowie die
Gruppenführer. Dennoch hören Raidführer nur die Gruppenführer, nicht die
anderen Spieler. Auf diesem Weg bleiben Spieler ruhig wenn sie ein
Kommando bekommen von den Führern (und hören das Kommando direkt ohne
das der Gruppenführer es wiederholen muss), und wenn nicht, dann stört
es nicht den Rest des Raid.

### Methode 2

Methode 2 wird wie Folgt aufgebaut:

  - Root
      - ***Raid***
          - ***Healers***
              - ***Unter Gruppe 1***
              - ***Unter Gruppe 2***
              - ... (Unendlich)
          - ***Tanks***
              - ***Unter Gruppe 1***
              - ***Unter Gruppe 2***
              - ...
          - ***Damage Dealers***
              - ***Unter Gruppe 1***
              - ***Unter Gruppe 2***
              - ...
          - ***Wuzzard***
              - ***Unter Gruppe 1***
              - ***Unter Gruppe 2***
              - ...
          - ... (Unendlich)

Die Kanäle müssen miteinander Verknüpft werden.

Die ACL vom **Raid** Kanal Bearbeiten

`1. `**`@out`**` "`**`Sprechen`**`" und "`**`Alt-Speak`**`" Verweigern.`
`2. `**`@sub`**` "`**`Alt-Speak`**`" Erlauben. Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`
`3. `**`@sub,0,2`**` "`**`Alt-Speak`**`" Verweigern. Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`

Nun die ACL von allen Gruppen Führern (Healers, Tanks)

`1. `**`@~sub,-1,0`**` "`**`Alt-Speak`**`" Erlauben (oder "`**`Sprechen`**`" Erlauben). Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`
`2. `**`@~sub,-1,1,2`**` "`**`Sprechen`**`" und "`**`Alt-Speak`**`" Verweigern. Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`
`3. `**`@~sub,-1,0,1`**` "`**`Alt-Speak`**`" Erlauben. Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`
`4. `**`@in`**` "`**`Sprechen`**`" Erlauben. Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`
`5. `**`@sub`**` "`**`Alt-Speak`**`" Erlauben.  Kontext `**`Betrifft``
 ``Unterkanäle`**` entfernen.`

Zum Schluss noch die Unter Gruppen Bearbeiten

`1. `**`@~sub,-1,0`**` "`**`Sprechen`**`" Erlauben`
`2. `**`@~sub,-1,1,1`**` "`**`Sprechen`**`" Verweigern`
`3. `**`@~sub,-1,0,1`**` "`**`Alt-Speak`**`" Erlauben`
`4. `**`@in`**` "`**`Sprechen`**`" Erlauben`
`5. Optional `**`@~sub,-2,0`**` "`**`AltSpeak`**`" Erlauben`

#### Erläuterung:

Der Raid Führer sollte sich in den ***Raid*** begeben, so wie die
Gruppen Führer sich in Healers, Tanks,... begeben sollten. Der rest geht
in die **Unter Gruppen**. Der Raid Führer kann mit **Alt-Speak** zu den
Gruppen Führern Sprechen und andersrum, und Gruppen Führer können sich
auch untereinander hören. Unter Gruppen können mit ihren Gruppen Führer
mit **Alt-Speak** Sprechen, alerdings können Gruppen Führer *ohne*
Alt-Speak mit ihren Unter Gruppen Sprechen. Wenn bei Gruppen Führer die
erste ACL statt Alt-Speak **Sprechen** Erlaubt wird, können die Raid
Führer mit den Gruppen ohne Taste Drücken Sprechen. Wenn bei Unter
Gruppen die Fünfte ACL hinzufügt, können die Unter Gruppen den Raid
Führer mit der **Alt-Speak** Taste hören.

Die Alt-Speak Taste muss bei jeden Spieler festgelegt werden. [In 1.2.x
heist es jetzt
Flüstern](FAQ_Deutsch#Wo_ist_die_Alt-Speak_Funktion_in_1.2.x_hin.3F "wikilink").

Damit lassen sich Gilden bis ca. 500 Benutzern gut auf einmal
Befehligen, jenachdem wieviele Benutzer es sind sollten auch
dementsprechend viele Kanäle angelegt werden.
Das ist viel arbeit, aber es lohnt sich.

Bei Fragen zur Methode 2, schreibt Chris2000SP in irc an. [\#mumble.de
auf Freenode](irc://irc.freenode.org/mumble.de)

[Category:Documentation
German](Category:Documentation_German "wikilink")