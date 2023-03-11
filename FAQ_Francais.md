# A propos de Mumble

Mumble est une application de chat vocal multi-utilisateurs. Bien qu'il
puisse être utilisé pour n'importe quel type d'activité, il est
principalement dédié aux jeux. Il est comparable à des programmes comme
Ventrilo ou Teamspeak. Lorsque vous entendez parler de Mumble, cela peut
avoir deux signifcations, "Mumble", l'application cliente, ou "Mumble et
Murmur", la suite applicative de chat vocal complète.

## Qu'est ce que Murmur ?

"Murmur" est le nom de l'application seveur. Dans tous les cas, si
quelqu'un parle de Murmur, c'est sans aucun doute la partie serveur de
la suite applicative.

## Sous quelles plate-formes peut-il être exécuté ?

L'application cliente, Mumble, peut être exécutée sous Windows, Mac OS X
et Linux.

L'application serveur, Murmur, devrait fonctionner sous n'importe quelle
plate-forme autorisant la compilation de Qt 4.

## Quels sont les pré-requis ?

L'application cliente s'exécute sur n'importe quelle machine possédant
Windows, Linux ou Mac OS X. VOus aurez également besoin d'un microphone.
L'application serveur est principalement consommatrice de
bande-passante, donc à partir du moment où votre matériel réseau est
suffisant, l'application devrait fonctionner sans problème particulier.
Veuillez noter toutefois que les binaires windows distribués via
sourceforge sont compilés pour des processeurs possédants les
instructions SSE (Pentium III / Athlon XP et plus récents) : Mumble
étant avant tout une solution de chat vocal pour le jeu, et les jeux
modernes demandant au minimum ce type de processeur, il nous a paru
naturel d'optimiser le logiciel pour ce type de processeur.

## Puis-je utiliser Mumble pour me connecter à un serveur Ventrilo/Teamspeak/Skype/...

Non. Mumble ne prend en charge que son propre protocole, qui a été
spécialement conçu pour vour procurer la meilleure expérience
utilisateur.

Si vous souhaitez utiliser Ventrilo sous linux, vous pouvez allez voir
du côté de [Mangler](http://www.mangler.org/).

## Installer Mumble

Veuillez vous référer la page dédiée : [installing
Mumble](installing_Mumble "wikilink") (en anglais).

## Compiler Mumble

Nous maintenons actuellement plusieurs pages pour compiler Mumble depuis
les sources sous [Linux](BuildingLinux "wikilink") (en anglais),
[Windows](BuildingWindows "wikilink") (en anglais), et
[FreeBSD](BuildingFreeBSD "wikilink") (en anglais).

## Pourquoi choisir Mumble ?

Mumble présente une latence très faible, associée à une grande qualité
sonore ; il utilise [CELT](http://www.celt-codec.org/) et
[Speex](http://www.speex.org/), non pas simplement pour la technologie
de compression de la voix, mais aussi les filtres permettant de
supprimer le bruit, et améliorer la clarté. Mumble possède également une
fonctionnalité de [positionnement
audio](Games#Positional_audio "wikilink") (page en anglais) pour les
jeux pris en charge, ce qui signifie que la voix des autres joueurs
semblera provenir de la position dans laquelle se trouve leur personnage
dans le jeu.

## Quels sont les besoins en bande passante ?

Depuis la version 0.9.1, c'est très variable, et surtout lié à
l'utilisateur : Avec la qualité maximale, la latence minimale et les
informations de positionnement audio envoyées, la bande passante
nécessaire est de 133,6 kbit/s (en prenant en compte les entêtes IP et
UDP). Avec 60ms de latence, la qualité la plus faible, et sans
information de positionnement audio, la bande passante nécessaire est de
17,4 kbit/s (là encore avec les entêtes IP et UDP). La qualité est
réglée par défaut à 58,8 kbit/s. Lors d'une comparaison avec un autre
produit, pensez à comparer la bande passante totale nécessaire, et pas
seulement le débit de l'encodage audio.

Il y a deux facteurs à prendre en compte pour affiner la bande passante
: le débit audio pour chaque trame audio (pas exemple 10ms) et le nombre
de trames dans chaque paquet. Chaque paquet transmis possède un entête
de 28 octets pour les informations IP et UDP, ce qui signifie qu'au plus
haut débit de transmission (100 paquets/s), il y a 2800 octets
simplement pour les informations brutes de transmission réseau. L'idéal
est de trouver un compromis qui fonctionne bien pour soi, mais nous
recommandons généralement de sacrifier la qualité audio au profit de la
latence, Mumble possédant une très bonne qualité audio même aux réglages
audio les plus faibles.

Il n'y a pas d'ajustement possible de la bande passante descendante
nécessaire : vous devez avoir assez de débit pour recevoir les données
de tous les autres utilisateurs. Cependant, ceci ne devrait pas poser de
problème majeur, la plupart des utilisateurs aujourd'hui possèdent une
connexion asymétrique, et seulement la bande passante remontante
(upload) présente des limites.

## Quels outils ont été utilisés pour réaliser tout cela ?

Voir [Development Tools](Development_Tools "wikilink") (en anglais).

## Comment puis-je apporter mon aide / contacter l'équipe ?

Un bon début est tout simplement d'utiliser Mumble \! Si vous
l'appréciez, dites le à vos amis. Si vous ne l'aimez pas, dites nous ce
qui ne vous convient pas, afin que nous puissions y remédier. Vous
pouvez réaliser cela grâce aux [forums](http://forums.mumble.info/) (en
anglais) ou nous rencontrer sur [IRC](IRC "wikilink") à l'adresse
<irc://irc.freenode.org/mumble> (en anglais). Si vous rencontrez un bug
ou une erreur avec laquelle vous avez besoin d'aide, lisez également la
page [Debugging](Debugging "wikilink") (en anglais), pour savoir comment
donner aux développeurs les informations nécessaires pour les aider à
résoudre les problèmes.

# Fonctionnalités audio

## Comment fonctionne le positionnement audio ?

Votre position dans le jeu est transmise dans chaque paquet audio, et
Mumble utilise DirectSound 3D pour positionner le son du coté du client.
Seuls les jeux qui ont été [liés](Link "wikilink") (en anglais) pour
être utilisé avec Mumble, ou pour lesquels un plugin a été écrit
bénéficient du positionnement audio. Tous les autres jeux
fonctionneront également, vous ne bénéficierez simplement pas du son 3D.
Vous pourrez trouver une liste des jeux supportés dans [cet
article](Games#Positional_audio "wikilink") (en anglais).

## Pourquoi Mumble est-il a ce point meilleur face à ses concurrents ?

Un mot : filtrage. Ceci fait partie intégrante de Speex depuis sa
version 1.1, et n'importe quel produit de transmission vocale utilisant
Speex devrait être capable de proposer facilement ce genre de filtrage.
Supprimer le bruit de l'entrée audio permet non seulement d'augmenter la
clarté du son, mais également de réduire la bande passante nécessaire.
Modéliser une voix claire demande moins de bits que le bruit, ce qui
signifie qu'une transmission bruitée sera en grande partie dédiée au
bruit.

## La qualité du synthétiseur vocal est horrible \!

Nous utilisons le synthétiseur standard de Microsoft, et les voix
disponibles ne sont pas forcément terribles. Si vous avez installé MS
Office ou le SDK Speech, vous disposez de voix supplémentaires,
configurables via le panneau de contrôle de Speech. Vous pouvez
également acheter un synthétiseur commercial ; du moment qu'il est
compatible avec SAPI5, il pourra être utilisé avec Mumble. Les
développeurs principaux utilisent [NeoSpeech](http://www.nextup.com).

## Pourquoi certaines voix produisent un son métallique/robotique ?

Mumble est optimisé pour les faibles latences, si votre connexion
présente de grandes variations de ping, certains paquets audio
arriveront trop tard pour être pris en charge par Mumble. Une mauvaise
connexion peut même engendrer une perte complète des paquets : si cela
se produit, le codec va essayer de "compenser" la perte de paquets.
Avant la version 1.2.1, notre nouveau codec CELT n'étais pas aussi
performant que Speex (l'ancien codec), assurez vous donc d'utiliser une
version récente. Mumble utilise également un buffer pour pour essayer
d'effacer les variations de ping, mais ce n'est pas parfait, nous
collectons actuellement des statistiques d'utilisation pour l'améliorer.

Généralement, augmenter ce buffer permet de réduire les artefacts, mais
une connexion stable (en terme de ping) est la meilleure solution.
gardez à l'esprit que le ping doit être stable du client vers le
serveur, mais également du serveur jusqu'au client final.

Les solutions évoquées ci-dessus sont les plus courantes. Certains
utilisateurs peuvent entendre des sons "métalliques", même avec un ping
stable dans tous les échanges : ceci peut être le résultat du filtrage
de Mumble. Si l'environnement de l'orateur est particulièrement bruité,
certaines parties de la voix seront également supprimées. Une
alternative serait une voix bruitée, ce qui signifie une précieuse bande
passante gaspillée, et une clarté de voix inférieure.

## Avec Mumble, mon microphone ne capte que les bruits ambiants, ma voix est difficilement audible

Ceci peut avoir de nombreuses raisons. Dans une minorité de cas, cela
peut être du à un mauvais matériel, de mauvaises connexions électriques,
ou un environnement particulièrement exposé aux perturbations
électromagnétiques. Ce genre de problème matériel peut seulement être
résolu en remplaçant l'élément défaillant. Dans la plupart des cas, le
problème est du au (ou est amplifié par le) logiciel.

Une possibilité pour résoudre ce genre de problème est d'augmenter ou
baisser le volume d'entrée. Vous pouvez relancer l'assistant audio et
porter une attention particulière à la page permettant de régler le
volume. Il se peut que vous ayez besoin d'activer / désactiver le
"boost" microphone et/ou d'augmenter/baisser le volume du microphone
dans les paramètres du système d'exploitation pour obtenir un volume
d'entrée situé dans la plage idéale. Activer la réduction du bruit de la
carte son (si cette fonctionnalité est disponible), peut également être
très efficace.

Dans beaucoup de situations, il peut y avoir une solution moins évidente
: un problème de driver. Installer la version du driver la plus récente
pour votre carte son peut résoudre certains problèmes rencontrés par
Mumble pour accéder de manière rapide à votre matériel audio.

## Je vois que je peux utiliser des notifications sonores, quels sont les formats supportés ?

Mumble supporte de nombreux formats classiques comme .ogg, .wav (non
compressé) ou .flac. Une liste complète des formats supportés peut être
consultée [ici](http://www.mega-nerd.com/libsndfile/#Features) (en
anglais).

## Pourquoi la détection d'activité vocale ne détecte plus ma voix ?

Si vous avez changé votre environnement audio soudainement et de manière
très marquée, par exemple en débranchant et rebranchant votre
microphone, ou en posant une feuille de papier directement sur le
microphone, vous mettrez en défaut le pré-filtrage de la voix. Il
re-fonctionnera, mais il lui faudra un peu de temps.

Pour effectuer une remise à zéro du pré-filtrage, vous pouvez utiliser
le reset situé dans le menu audio.

## Quel est cet écho bizarre me faisant entendre ma voix en provenance des autres utilisateurs ?

Malheureusement, de nombreux casques populaires produisent un petit
écho. Dans les autres produits de chat vocal, vous n'entendez pas cet
écho parce qu'il est plus faible que le bruit, mais Mumble supprimant
quasi intégralement les bruits, l'écho devient tout de suite audible.
Dans ce cas, la meilleure chose à faire est d'activer la suppression de
l'écho, aussi bien du coté de la personne produisant l'écho, que celui
de la personne l'entendant. Sous Vista, Mumble permet de réaliser une
suppression de l'écho avec n'importe quelle carte son, sous XP, cette
suppression de l'écho en sera disponible que pour les cartes son
possédant un driver compatible ASIO (disponible seulement pour les
cartes son de meilleure qualité). Sous Linux, Mumble permet d'utiliser
la suppression de l'écho lorsque PulseAudio est utilisé.

## Puis-je changer le volume d'un utilisateur en particulier ?

Non, vous ne pouvez pas. Mumble utilise un CAG (**C**ontrôle
**A**utomatique du **G**ain) pour normaliser les volumes de tous les
utilisateurs automatiquement, ce qui signifie que l'ajustement du volume
d'un seul utilisateur n'est pas nécessaire, voire même non souhaitable.
Nous pensons que cela n'a pas de sens que chaque utilisateur d'un
serveur règle le volume d'un autre utilisateur manuellement, alors que
le problème pourrait être réglé par la personne concernée directement.
la plupart des questions que nous recevons à ce sujet proviennent du
fait que l'utilisateur n'a pas exécuté l'assistant audio : le CAG est un
outil très puissant, mais s'il n'y a pas assez de signal pour
l'initialiser (par exemple un volume de microphone trop bas), il ne sera
pas en mesure de fonctionner correctement.

## Où est le "Alt-speak" dans les version 1.2.x ?

Le "Alt-speak" a été remplacée par la fonctionnalité de chuchotement. Il
vous suffit d'ajouter un raccourci de chuchotement avec comme cible le
canal courant et de cocher "Chuchoter aux canaux liés" pour réaliser la
même chose que ce que faisait le "Alt-speak" dans les version 1.1.x.

[Category:Documentation
Francais](Category:Documentation_Francais "wikilink")