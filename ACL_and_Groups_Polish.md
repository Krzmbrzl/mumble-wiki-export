# Wstęp

ACL czyli Access Control List jest sposobem przyznawania praw dla
użytkowników na kanałach. Kilka zasad :

  - tworzyć grupę, dodawać ludzi do grupy, następnie grupie przydzielać
    prawa.
  - prawa są sprawdzane od góry do dołu
  - prawo Zabroń ma wyższy priorytet niż Zezwól
  - najpierw odbieraj prawa (grupy na gorze) a potem przyznawaj prawa
    (grupy na dole) - dzięki temu, co nie jest zezwolone to jest
    zabronione i nie ma nadużyć :)

# Aktywacja zakładki edycji ACL

Najpierw sprawdź **Opcje** -\> **Konfiguracja**, na dole po lewej masz
checkbox **Zaawansowane** - zaznacz go. Dzięki temu jak klikniesz prawym
myszy na kanale i wybierzesz **Edytuj** to zobaczysz zakładkę ACL.

# Grupy

Z początku chcesz najpierw stworzyć grupy w kanale głównym aby być w
stanie łatwiej zarządzać pozostałymi kanałami. Aby zedytować albo
stworzyć nową grupę, kliknij prawym myszy na głównym kanale i kliknij
**Edycja** (Edit). Następnie kliknij w zakładkę **Grupy** (Groups) -
możesz teraz wybrać grupy, albo dodać nowe (wpisujesz nazwę w pole i
wciskasz Dodaj).

W chwili jak wybierzesz grupę, w dolnych okienkach pokaże się lista
użytkowników należąca do grupy. Oczywiście jeśli grupa jest nowa to
lista jest pusta, i wtedy trzeba z listy na dole wybrać osobę będącą na
serwerze, ewentualnie trzeba wpisać jej dokładny nick z palca i wcisnąć
**Dodaj** (Add). Dodawać do grup można tylko zarejestrowanych
użytkowników na mumble.

Grupy są przypisane do specyficznego kanału, ale mogą być także
dziedziczone przez subkanały ( podkanały ), jeśli jest zaznaczona opcja
**Dziedziczny** (Inheritable) w kanale **nadrzędnym** (parent) oraz
jeśli jest zaznaczona opcja **Dziedzicz** (Inherit) w **podkanale**.

Dzięki tej opcji możesz ustawić jedną albo więcej grup w kanale
nadrzędnym i dziedziczyć po nim grupy i prawa dostępu dla tych grup.
Dodatkowo można ustawić na każdy podkanał specyficzne prawa dla danych
grup.

Dla każdego kanału grupa zawiera trzy składowe informacje:

1.  Członkowie (Members): lista osób dodanych do grupy (np gdyż nie są
    członkami takiej samej grupy dziedziczonej z nadrzędnego kanału)
2.  Odziedziczeni członkowie (Inherited members): lista osób
    dziedziczonych z tej samej grupy z kanału nadrzędnego
3.  Wykluczeni członkowie (Excluded members): lista osób która ma być
    usunięta z grupy - użyteczne jak danej osobie mamy zabrać prawa z
    pewnej grupy w pewnym specyficznym podkanale.

## Przykład

Praktyczny przykład z grupą *admin*. Za każdym razem, jak osoba tworzy
kanał, wtedy jest on dodawany do grupy admin danego kanału, jednakże nie
daje to jeszcze żadnych praw na kanale, a jedynie zaznacza, iż należy on
do tej grupy. Jednakże Mumrur domyślnie tworzy grupę w kanale z prawami
Edycję ACL (Write ACL) Zezwól.

Przy strukturze jak poniżej

  - Root
      - A
          - B
      - C
          - D

Osoba "Big Boss" jest jedynie członkiem grupy admin w kanale Root. W
kanale A, osoba "BoosA" oraz w kanale "BossB" są dodawani do grup admin
na tych kanałach.

W kanale Root, A oraz B, ustawiamy flagę Dziedzicz (Inherit) oraz
Dziedziczny (Inheritable) na grupie admin - jest to domyślne ustawienie
w Murmurze.

Osoba będąca członkiem tej grupy w jakimkolwiek kanale będzie
dziedziczona (inherited member) w podkanałach. Tak więc całkowita lista
osób na kanale B będzie "Big Boss, BossA, BossB". Dzięki temu jeśli
dodamy nową osobę "SuperBoss" do grupy admin w kanale Root, to
automatycznie pojawi się ona w grupie admin w kanałach podrzędnych A
oraz B

Teraz w kanale C mamy grupę admin, ale oznaczamy w nim aby nie było
opcji Dziedzicz (Inherit). Dodatkowo dodajemy do niej osobę BossC. Jak
teraz się przyjrzymy grupie admin, to zauważymy, że na kanale C nie ma
adminów z kanału Root, więc lista zawiera tylko jedną osobę BossC.
Wszelkie zmiany w grupach nie dziedziczonych w kanale Root nie będą
wtedy widoczne w kanale C.

Natomiast w kanale D będziemy widzieć tylko admina z kanału C (bo jest
nadrzędny), chyba że ustawimy aby nie dziedziczyć grupy admin.

# ACL

ACL (Access Control Lists) są przypisane do specyficznego kanału. Kanał
może mieć zaznaczenie czy dziedziczy (inherit) inne ACL z kanału
nadrzędnego czy też nie, jednakże nie można wybrać które ma dziedziczyć
- po prostu dziedziczy wszystkie albo żadne. ACL są przetwarzane w
kolejności w jakiej zostały wpisane, od góry do dołu zgodnie z
kierunkiem dziedziczenia kanałów.

Aby edytować ACL trzeba kliknąć prawym myszy na kanale, wybieramy
**Edytuj** (Edit), a następnie wybieramy zakładkę **ACL**. Dodawanie
grup polega na wybraniu na dole danej grupy, oraz wtedy przypisania jej
praw w prawej części zakładki (Zezwól i Zaroń/Allow Deny).

## Uprawnienia

  - Edycja ACL (Write ACL) - pozwala na kompletną kontrolę kanału -
    edycję opisu, dodawanie osób do grup, edycję ACL, nie dawać tego
    nikomu, kto nie powinen mieć prawa dministracyjnych
  - Wejście na pod-kanał (Traverse) - zejście do podkanałów tego kanału
    - czyli np z ominięciem skoku na kanał nadrzędny.
  - Wejście (Enter) - wejście na ten kanał
  - Mowa (Speak/Talk) - pozwolenie na gadanie
  - Wyciszanie/Ogłuszanie (Mute/Deafen) - wyłączanie mikrofonu i
    słuchawek innym
  - Przenoszenie użytkowników (Move) - łapiesz kogoś z tego kanału i
    gdzieś wrzucasz.
  - Tworzenie kanałów (Make channel) - jasne
  - Łączenie kanałów (Link) - dzięki temu ludzie mogą połączyć kanały i
    gadać ze sobą bez łażenia po kanałach. Tym się robi podsłuch :)
  - Szept(Whisper) - **dawniej Alt Speak** - daje możliwość wysyłania
    komunikatu głosowego alternatywną metodą (taki drugi bind)
  - Wysyłanie wiadomości tekstowych (Message) - wysyłane tekstu do osoby
    czy kanału
  - Tworzenie kanałów Tymczasowych (Temporary) - kanały tymczasowe
    istnieją do czasu, aż ktoś na nich siedzi

## Przypisywanie grup

Zamiast przypisywać prawa grupie, można przypisywać prawa poszczególnym
osobom - wtedy nie dotykamy pola Grupy tylko wybieramy osobę z ID
Użytkownika. Jednak jest to nie zalecane rozwiązanie.

W ACL użytkowników można rozróżnić od grup tym, że grupy mają przed
nazwą znaczek @.

## Specjalne znaki przed nazwami grup oraz grupy specjalne

Nazwy grup można poprzedzać specjalnymi znakami:

  - \! (wykrzyknik) odwraca przynależność do grupy (czyli \!admin
    oznacza wszystkich nie będących w grupie admin)
  - \~ (tylda) grupa określona w miejscu na którym jest zdefiniowany ACL
    a nie na aktywnym kanale.
  - all - wszyscy użytkownicy zarejestrowani i niezarejestrowani
  - auth - wszyscy zarejestrowani użytkownicy
  - in - wszyscy użytkownicy na aktualnym kanale
  - out - wszyscy użytkownicy nie będący na aktualnym kanale
  - sub - dotyczy tylko podkanałów tego kanału, o tym niżej

Dla każdego wpisu prawa mogą być Zezwól (Allow) albo Zabroń (Deny). W
razie konfliktu, ostatni wpis ma najważniejsze znaczenie. Pamiętaj, że
każdy wpis jest przetwarzany w kolejności w jakiej się znajduje na
liście (od góry do dołu). Przykład 1:

`@all deny speak`
`@all allow speak`

Wynik: wszyscy użytkownicy mogą rozmawiać

Przykład 2:

`@all allow speak`
`@all deny speak`

Wynik: wszyscy użytkownicy NIE MOGĄ rozmawiać.

Każdy wpis ACL posiada specjalne flagi definiujące jego właściwości
oddziaływania - czyli kontekst w jakim się znajduje. **Stostuj do
podkanału** (subchannels) - prawa dostępu wpływają na grupy w danych
podkanałach. **Stosuj do tego kanału** (this channel) - prawa dostępu
wpływają na grupy w aktualnym kanale. Oczywiście można wybrać żaden,
jeden albo oba na raz. W większości przypadków chcesz mieć wybrane obie
opcje. Pamiętaj, że jeśli chcesz aby wpis działał na podkanały, to
musisz ustawić na wpisie aby był stosowany na podkanały oraz żeby
podkanały dziedziczyły ACL z kanału nadrzędnego.

## Grupa @sub

Specjalna grupa **sub** działa podonie jak *all* ale posiada specjalne
znaczenie i parametry. Stosuje się wpis:

`sub,a,b,c`

gdzie

  - a jest minimalną liczbą wspólnych kanałów nadrzędnych (parents)
  - b oraz c ograniczają głębokość zejścia po podkanałach.
      - b ustawia minimalną głębokość ścieżki liczoną od kanału a
      - c ustawia maksymalną głębokość ścieżki liczona od kanału a

Jeśli któregokolwiek parametru brakuje, wtedy nie istnieje minimalna ani
maksymalna głęokość ścieżki.

Z początku wydaje się to zagmatwane, ale jest również bardzo potężnym
narzędziem. Przykład:

  - Root
      - A
          - A1
              - Sub1
              - Sub2
          - A2
          - A3
      - B
          - B1
          - B2

Zakładamy odmowę wejścia (all deny) na kanał Root. Następnie na A
definujemy:

` @~sub,0,1 +enter`

Po pierwsze, ten wpis ACL będzie przetwarzany w kontekście
zdefiniowanego kanału, gdyż jego grupa zaczyna się od \~.

Pierwszy parametr (0) wskazuje ile dodatkowych elementów ścieżki musi
pasować. Zero oznacza, że pasują wszystkie do danego miejsca. To
oznacza, że każdy użytkownik w kanale będącym w ścieżce **Root.A**
będzie pasował. Gdyby parametr wynosił 1, a my byśmy byli w ścieżce
Sub2, wtedy ścieżka by musiała pasować do Root.A.Sub1. Ustawienie tego
parametru ma sens tylko do grup doczepionych (z \~).

Drugi parametr oznacza, że ścieżka musi być o co najmniej jeden kanał
dłuższa niż ścieżka kanału w którym zdefiniowano wpis ACL. Tak więc ten
wpis pasuje w tym przypadku do każdego kanału zaczynającego się od
Root.A i posiadającego przynajmniej jeden dodatkowy element (podkanał).

**Sumując** - ten wpis ACL pozwala każdej osobie będącej w
_podkanałach_ A (ale nie będącej bezpośrednio na A), wejść na kanał A
albo jakikolwiek z jego podkanałów (zakładamy, że podkanały A dziedziczą
ACL z kanału A).

Gdybyśmy nie użyli znaku \~, wtedy każdy użytkownik w jakimkolwiek
podkanale A wejść na kanał wyżej (np z Sub1 na A1 albo A, ale nie
inaczej), albo innymi słowy - każdy byłby w stanie wejść do kanału
nadrzędnego jeśli byłby w kanale podrzędnym.

Dodajmy nowy wpis ACL do A1:

`@sub,-1,0 Zezwól Łączenie kanału.`

To pozwoli każdemu, kto jest w katalogu nadrzędnym (ścieżka w górę do -1
elementu (pierwszy parametr)) oraz wszelkich podkanałów (drugi parametr
0) aby zlinkować się do tego kanału.

Ostatecznie ostatni wpis, pokazujący jak można to namieszać:

`@~sub,-1,2,2 +enter`

To pozwala każdej osobie w podkanale Root (czyli parent dla B) i
mającego ścieżkę wynoszącą dokładnie 2 (długość Root.B -1 + 2) wejść na
kanał, tak więc ta zasada będzie oddziałwywać na osoby w A1, ale już nie
w A czy Sub1.

## Hasła na kanały i żetony (Tokens)

Mumble 1.2 wprowadza funckję aby dostać się do kanału używając haseł lub
żetonów. Hasła są trzymane w liście Hasła Dostępu (Token List) po
stronie klienta, dla każdego serwera. Są one używane jak użytkownik musi
go użyć.

  - klient - hasło na grupę.
  - serwer, kanał - hasło na kanał + prawa dostępu dla grupy zgodnej z
    hasłem kanału

### Konfiguracja żetonów dostępu (Access Tokens)

Żetony dostępu są konfigurowane poprzez tworzenie specjalnych grup,
które składają się z nazwy żetonu poprzedzonego znakiem \# (hash). Na
przykład żeton o nazwie "letmein" oddziałuje na grupę nazwaną \#letmein.

Edytor kanałów zawiera na dole opcję o nazwie "hasło" (password).

Wpisując tam tekst "letmein" (bez cudzysłowów) tworzymy automatycznie
żeton dostępu (grupę) o nazwie \#letmein. Następnie domyślnie ustawiamy
Zabroń Wejście (Deny Enter) na kanał dla @all oraz dajemy Zezwól na
Wejście (Allow Enter) do użytkowników w grupie \#letmein, która będzie
zawierała osoby które posiadają po swojej stronie poprawny wpis w liście
Hasła Dostępu (Tokens).

### Używanie haseł dostępu

Po stronie klienta można dodac żetony poprzez menu Serwer \> Hasła
dostępu (Server, Access Tokens). Klikamy w Dodaj (Add), wpisujemy
żeton, np "letmein" oraz klikamy OK. Zmany powinny odnosić
natychmiastowy skutek, pozwalając odobie na wejście na kanały związane z
tym żetonem. Pamiętaj, że są to hasła więc traktuj je jak hasła - używaj
unikalnych nazw oraz drudnych do dogadnięcia ciągów znaków.

# Prawa dostępu

## Edycja ACL

(Edit ACL) Daje to **absolutną** kontrolę nad kanale oraz edycje wpisów
ACL czyli grup dostępu. To prawo dostępu wymusza, że wszystkie pozostałe
prawa są przydzielone automatycznie. Dlatego też to prawo powinny mieć
osoby którym można ufać, np administratorzy, właściciele kanałów.

## Wejście na podkanał

(Traverse) Bez tego prawa osoba nie będzie w stanie wejść do kanału albo
jakiegokolwiek podkanału, niezależnie od innych praw w kanałach poniżej.
Nie odmawiaj tego prawa, chyba że bardzo dobrze wiesz co robisz. Lepiej
jest niektórym osobom odmówić wejścia na kanał niż zaronić wejścia na
podkanał.

## Wejście

(Enter) Pozwala osobie wejść na kanał. Jak ktoś nie ma prawa wejść na
kanał, to zawsze może byc na niego przeniesiona przez osobę, która ma na
kanale docelowym prawa Przenoszenie użytkowników.

## Mowa

(Speak) Pozwala osobie rozmawiać na kanale przez mikrofon. Przy kanałach
połączonych, aby było słychać osobę na innym kanale, to musi ona mieć
prawa Mowa na kanale docelowym. Dzięki temu można ustanowić hierarchię
linkowanych kanałów gdzie wszyscy gracze będą słyszeć tylko liderów
grup, ale za to grupy nie będą się na wzajem zagłuszać (głosy zwykłych
ludzi nie będą słyszane poza lokalnym kanałem).

Jeśli osoba dołącza do kanału i nie posiada ona praw Mowa na kanale,
wtedy zostanie ona automatycznie uciszona (tylko mikrofon), inie będzie
ona w stanie cokolwiek powiedzieć dopóki ktoś jej nie cofnie wyciszenia.

## Wycisz

(Mute) Pozwala danej osobie wyciszyć mikrofon innych osób. Pamiętaj, że
status wyciszenia podąża za osobą poruszającą się po kanałach. Tak więc
będzie się ona musiała sama odciszyć (jeśli może), albo ktoś jej cofnie
wyciszenie, albo musi się podłączyć do serwera jeszcze raz.

## Ogłusz

(Deafen) Podobnie jak z mikrofonem, ale dodatkowo wycisza głośniki, więc
dana osoba kompletnie nie może się komunikować głosowo, ani nie ędzie
odbierać komunikatów głosowych. Użyteczne na kanału Away.

## Przenieś

(Move) Pozwala danej osobie przenosić inne osoby na inne kanały. Jeśli
osoba przenoszona nie ma praw Wejście na kanale docelowym, to wtedy
osoba przenosząca musi mieć prawa Przenieś na obu kanałach (źródłowym i
docelowym).

## Kopanie użytkowników

(Kick) Dotyczy tylko kanału głównego (root) i propagowane jest w dół po
wszystkich kanałach. Pozwala danej osobie wykopać inną osobę z serwera,
np za nie przestrzeganie zasad.

## Banowanie użytkowników

(Ban) Dotyczy tylko kanału głównego (root) i propagowane jest w dół po
wszystkich kanałach. Działa tak jak Kopanie ale dana osoba juz nie wróci
na serwer - bany na numer IP z maską CIDR. Dawać tylko bardzo zaufanym
osobom, administratorom.

## Tworzenie kanałów

(Make Channel) Pozwala osobie na tworzenie podkanałów w danym kanale.
Osoba taka automatycznie będzie dodana do grupy *admin* w nowo
stworzonym kanale. Dlatego też sugerowane jest korzystanie z
dziedziczonych grup w ACL.

## Tworzenie kanałów tymczasowych

(Make Temporary Channel) Pozwala osobie na tworzenie tymczasowych
kanałów w aktualnym kanale. Kanały takie są automatycznie kasowane,
kiedy wyjdzie z nich ostatnia osoba. Przy stworzeniu, twórca będzie
automatycznie przeniesiony do tego podkanału.

## Połącz kanały

(Link Channel) Pozwala osobie połączyć albo rozłączyć kanały, a także
używać opcji push-to-link channels. Aby połączyć kanały, osoba musi
posiadać prawo Połącz kanały na obu kanałach - źródłowym i jednocześnie
docelowym. Aby rozłączyć kanały, trzeba posiadać prawa Połącz kanały na
jednym z kanałów - źródłowym lu docelowym.

## Szept

(AltSpeak or Whisper) Pozwala osobie na wysyłanie komunikatów głosowych
kiedy trzyma ona klawisz do Szeptu (Alt Push To Talk). Klawisz ten
konfiguruje się w opcjach w Skrótach (Shortcuts) - wybieramy akcję Szept
(Whisper), wybieramy do kogo (osoby albo kanału), oraz jaki klawisz.
Tego rodzaju komunikaty są dobre jak chcemy rozmawiać przez chwilę tylko
z wybrana osobą, grupą osób, kanałem, czy też jak wybierzemy jako cel
kanał główny z podkanałami - aby przesyłać ogłoszenia na serwerze.
Dzięki temu można nadawać komunikaty bez łączenia się z kanałami.

## Wysyłanie komunikatów tekstowych

(Send text messages) Pozwala osobie wysyłać komunikaty tekstowe do
innych osób na kanale.

## Rejestracja

(Register users) Dotyczy tylko kanału głównego (root) i propagowane jest
w dół po wszystkich kanałach. Pozwala danej osobie rejestrować inne
osoby na serwerze - osoba do zarejestrowania musi mieć wygenerowany
certyfikat. Osoba bez rejestracji nie może być przypisana do grupy.
Dzięki temu można się odseparować od niechcianych osób na serwerze.

## Rejestracja samego siebie

(Register self) Dotyczy tylko kanału głównego (root) i propagowane jest
w dół po wszystkich kanałach. Pozwala osobie aby się sama mogła
zarejestrować, aby administrator nie musiał robić to za nią. Wtedy musi
cierpliwie czekać na przypisanie do innych grup ACL jeśli istnieją.
Użyteczne na serwerach publicznych.

# Examples

## Group of servers with FPS game

In this example, we assume we have a group of public servers running FPS
games. Each game has 2 competing sides, and each side consists of one or
more squads. We want a hierarchy such as this:

  - Servers
      - "Servername"
          - Team 1
              - Squad 1
              - Squad 2
              - ...
          - Team 2
              - Squad 1
              - ...
          - ...
      - ...

Let's assume we have a small script linked with qstat that puts the
player in the channel of the right side, and once in there we want to
give them the ability to switch between squad channels and link at will.
However, we do not want them to gain access to the channels of the other
side.

This is actually a very straightforward implementation; on the "Servers"
channel, define an empty group called players. Then, add the following
acls:

1.  @all deny enter
2.  @\~sub,2,2 allow enter, allow link

The first rule denies enter privilege to all players, and the second
rule allows anyone within a hierarchy at least 2 elements down from
"Servers" to move and link at will. In practice, this means that once a
player is inside "Team 1", he can move freely about in there but can't
switch to the other team or another server subchannel.

## MMORPG Raid

Assume this setup:

  - Root
      - Raid
          - Healers
          - Tanks
          - Damage Dealers
          - Wussards and other pets

The desire is to have one leader of each group, plus a few people as
raid leaders.

Set this up as follows: In "Raid", create a group called "groupleaders".
Put the leader of each group in this group. In the same channel define
"raidleaders", and put the raidleaders in this group.

In the Raid channel, define the following ACLS:

1.  @all deny enter, deny speak \[Apply Here only\]
2.  @raidleaders allow enter, allow speak, allow link, allow mute, allow
    kick \[Apply Here and Apply Subs\]
3.  @groupleaders allow speak, allow link \[Apply Here only\]
4.  @groupleaders allow link, allow mute, allow kick \[Apply Subs only\]

The first rule makes sure nobody can speak or enter the Raid channel.
The second rule lifts this restriction from anyone in the raidleaders
group as well as giving them broad permissions. The third rule makes
sure groupleaders can link and speak to the raid channel, and the fourth
gives them permission to link from the subchannel as well as get rid of
troublesome players.

Normal players will not be able to join the raid channel, but as that
denial only applied in the raid channel they can join any subchannel
they wish. When the channels are linked, everyone in the linked channels
will hear raid leaders and group leaders. However, raid leaders will
only hear group leaders, they will not hear normal players. This way,
players can stay quiet when they hear a command coming down (and also
hear the command direct without the groupleader having to repeat it),
and if they don't that won't bother the rest of the raid.

[Category:Documentation
Polish](Category:Documentation_Polish "wikilink") [Category:Needs Update
for 1.2.0](Category:Needs_Update_for_1.2.0 "wikilink")