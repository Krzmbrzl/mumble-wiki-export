# Включение редактора Групп и ACL

Редактор Групп и Списков Контроля Доступа включается опцией "Экспертные
настройки" в окне "Настройки Mumble" (Настройки → Настройки). После
этого появятся закладки "Группы" и "Списки контроля доступа" при
выборе "Редактировать" на канале.

# Groups

Для редактирования или создания группы используйте правую клавишу мыши
на корневом разделе и выберите "Редактировать". Обычно создают группы
в корневом разделе для простоты управления. Перейдите в закладку
"Группы". Теперь можно выбрать существующую либо создать новую.

You can now either select a group or add another one by clicking in the
blank box called "Group", typing the group name and pressing enter. Now
that the group is selected, add the users to the group by typing their
registered name in the bottom left box and clicking "Add."

Groups are tied to a specific channel, but can also be inherited by
subchannels, when the flag "Inheritable" is set in the parent channel
and "Inherit" is set in the subchannel (usually you want these flags to
be set). This opens a convenient way to administer channels and their
ACLs; set up the ACLs on the top of the channel tree that should have a
similar privilege structure, and just change the group memberships on
subchannels.

For each channel, a group has 3 pieces of data:
1\. "Members": the list of players to add to the group (i.e. because
they are not members of the same group in the parent channel already),
2\. "Inherited members": the list of members inherited from the same
group in the parent channel and
3\. "Excluded members": the list of inherited members to remove from the
group.

**Note: Only registered players can be added to groups.**

## Example

Let's take a practical example, the *admin* group. Every time a player
makes a channel, he is automatically added to its admin group. This
doesn't automatically give him any privileges, it just marks him as a
member of that group, however Murmur's default installation installs an
ACL that grants the *admin* group the *Write ACL* (all access)
permission.

In a structure like this:

  - Root
      - A
          - B
      - C
          - D

player "Big Boss" is the only *Member* of the *admin* group in Root. In
channel A, player "BossA" and in channel B, "BossB" are added to the
*Members* of *admin*,

In the channels Root, A and B the flags *Inherit* and *Inheritable* are
set for the *admin* group (default setting in Murmur). A player being a
member of that group in any of these channels thus is an *inherited
member* in a subchannel. So the total list of members in channel B is
"Big Boss, BossA, BossB". The convenience of this system is that if we
later add "Super Boss" to admin in Root, he'll automatically be in the
admin group of the channels A and B.

Let's move on, and say that player "BossC" is in the Members list in
channel C, but here admin is not marked as *inherit*. This means that
"Big Boss" is not in the admin group and any changes for admin in Root
will not be seen here. Channel D will inherit the list from C, unless C
also marks admin as not inheritable.

# ACL

ACL (Access Control Lists) are all attached to a specific channel. A
channel can specify if it wants to inherit the ACL on the parent, but it
cannot specify which; it's a all or nothing deal. ACL are evaluated in
order, from top to bottom along the chain of channels. To add or remove
an ACL, right click on the channel you wish to change ACL's on and click
"Edit ACL." Once you add an ACL, you set the group the ACL defines by
typing it's name in the bottom left box labeled "Group." If you just
want to set an ACL for a specific user, leave the Group box blank and
type the name of the user in the box labeled "User ID."

For each entry, either a user or a group will match. A user must be a
specific, registered user, while a group can be any group valid in the
channel the ACL is defined on. Note that group membership is evaluated
in the channel the ACL is executed in, which is important for inherited
ACLs. If a group begins with a *\!*, it's membership is inverted, and if
it begins with a *\~*, it is evaluated in the context of the channel the
ACL is defined on (and not the active channel).

  -
    all

Everyone

  -
    auth

All authenticated users

  -
    in

All users inside current channel

  -
    out

All users outside current channel

For each entry, permissions are either allowed or denied; in case of a
conflict the last entry takes precedence. Remember that all entries are
evaluated in order, so if you have the following set of entries:

  - @all deny speak
  - @all allow speak

Then everyone will be allowed to speak. On the other hand

  - @all allow speak
  - @all deny speak

Will deny speak from everyone.

Each entry can be marked as either applying in the current channel, in
subchannels or both. Most of the time you want both. Remember that for
an entry to be applied on a subchannel, you have to apply it to
subchannels **and** allow inheritance in the subchannels.

## The @sub group

There is a special group called *sub*, which just like *all* has a
special meaning. Sub is used as *sub,a,b,c*, where *a* is the minimum
number of common parents, and *b* and *c* restrain the path depth:

  - b is the minimum and c the maximum path length, measured from the
    channel referred by a.
  - If any of those parameter is missing, then there will be no
    minimum/maximum path length.

It's somewhat complex, but also rather powerful. For example, assume the
following tree:

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

Let's deny enter to all on *Root* to start with. Then, on *A*, we define

1.  @\~sub,0,1 +enter

First of all, this ACL will be evaluated in the context of the defining
channel, since the group starts with \~.

The **first parameter** (0) indicates how many additional elements of
the path name must match. A zero means we require a match up to this
point. This means that any player in a channel under the path Root.A
will match (so in all sub-channels).

If this first parameter had been 1 the evaluation would start one level
below Root.A, where the ACL was defined. The second parameter with value
1 indicates all sub-channels (thus now of Root.A.\*) are allowed to
enter. So we would be allowed to enter Sub1 and Sub2.

Setting this to positive values only makes sense for pinned groups (with
the \~).

The **second parameter** requires the path of the evaluated channel to
be at least one element longer than the path of the channel of the ACL.
So this rule will match in anything that starts with Root.A and has at
least one more element.

To sum it up; this rule allows anyone in one of A's descendants (but no
A itself) to join A or any of its descendants (we assume subchannels
inherit the rule).

If we don't use the \~, then it will allow people in any of A
descendants to go up (ie, from Sub1 to A1 or A but not the other way)
or, in other words, allow people in the descendant of a channel (any
depth) to enter it.

Let's add a new rule to *A1*:

1.  @sub,-1,0 +link

This allows anyone that's in the parent (equal path up to -1 elements
(the first parameter)) or any of the siblings (path length equal (the 0
parameter)) to link to this channel.

And finally, just to show how messed up it can get, let's add this on B:

1.  @\~sub,-1,2,2 +enter

This lets anyone that's currently in a descendant of Root (B's parent)
and has a path length of exactly 2 (length of Root.B -1 + 2) join, so
this rule would match someone in A1, but not A or Sub1.

## Channel Passwords and Access Tokens

Beginning with Mumble 1.2, it is now possible to set access on channels
based on "tokens" or "passwords". Passwords are stored in a tokens list
in the client for each server, with the client using them as needed.
From this point forward, we will refer to channel passwords as "tokens"
instead, for clarity.

### Configuring an Access Token

Access Tokens are configured by creating special groups, which consist
of the token prefixed by a pound symbol. For example a token called
"letmein" corresponds to a group called \#letmein.

The Channel Editor dialog box contains a field called "password".
Entering "letmein" in the password field will automatically create a
token group called \#letmein, then by default will deny "Enter" access
to @all and allow "Enter" access to users in the group \#letmein, which
will consist of any user who has that token in their token list.

To create token groups manually, first enable the Advanced Channel
Editor. Then Edit a channel and go to the ACL tab. On the bottom of the
ACL list, select the @all entry and check the "Deny Enter" permissions
box. Now click "Add", and in the "Group" combobox at the bottom write
\#letmein and press enter. Now check the "Allow Enter" permissions box,
and click OK to dismiss the editor.

### Using an Access Token

You may add access tokens to your client by selecting "Access Tokens"
from the "Server" menu. Click add, type the token (e.g. "letmein") and
click "OK". It should take effect immediately, granting you whatever
permissions are associated with that token group. Remember that tokens
are passwords, so treat them as such; pick a token name that is unique
and hard to guess.

# Permission Definitions

## Write

This gives total control over the channel, including the ability to edit
ACLs. This privilege implies all other privileges.

## Traverse

Without this privlege, a player will be unable to access the channel or
any subchannels in any way, regardless of privileges in the subchannel.
Don't deny this unless you really know what you're doing; you can
probably achieve the effect you want by denying a player the Enter
privlege.

## Enter

Allows player to enter channel. Even without this privilege, a player
can be moved into the channel by a player with Move/Kick.

## Speak

Allows player to speak in channel. For linked channels, only players
with Speak privilege in the destination channels will be heard. This can
be used to set up a hierarchy of linked channels where all players can
hear all the leader of each group, but normal players will not be
propageated outside their channel. This way, players will hear someone
else is talkig to the group leader and (hopefully) stop talking for a
short while.

If a player joins a channel he does not have Speak privilege in, he will
be suppressed by the server, and will be unable to speak until someone
unmutes him.

## Mute / Deafen

Allows a player to mute or deafen another player. Note that mute status
will follow a player until he is either manually unmuted or reconnects
to the server.

## Move / Kick

Allows a player to move another player to another channel or kick them
off the server. Unless the target player has Enter privileges in the
channel he's being moved to, Move privileges is required in both
channels.

## Make Channel

Allows a player to make a subchannel in the current channel. The player
will automatically be added to the *admin* group in the new channel, so
make the inheritable ACLs give the privileges you desire.

## Make Temporary Channel

Allows a player to make a temporary subchannel in the current channel,
which will automatically be deleted when the last user leaves it. The
creator will automatically be moved into the channel after creating it.

## Link Channel

Allows a player to link or unlink, as well as push-to-link a channel.
Unlinking requires Link privilege in either channel, and linking
requires Link privilege in both.

## AltSpeak

Allows a player to speak in channel if he is holding the Alt
Push-To-Talk key (can be configured in the Shortcuts tab of the options
window). It works as Speak for linked channels, etc. This may be used to
broadcast to a hierarchy of channels without having to link to them.

# Примеры

## Сервера для FPS игр

Пример 1. Публичный сервер для игры двух противоборствующих сторон.
Каждая сторона состоит из подразделений. Попытаемся создать такую
структуру:

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

Утилитой qstat игроки распределяются в каналы своих сторон. Теперь мы
хотим дать им возможность менять и связывать каналы подразделений. У
игроков не должно быть возможности заходить и связывать каналы другой
стороны.

Вот как просто это реализуется. На канале "Servers" создайте пустую
группу "players". Теперь добавьте следующие ACL:

1.  @all Запретить Вход
2.  @\~sub,2,2 Разрешить Вход, Разрешить Связывать Канал

Первое правило закрывает вход всем. Второе правило разрешает любому из
уровня 2 и ниже от "Servers" ходить и связывать каналы. На практике
это позволяет игроку одной стороны свободно ходить и связывать
каналы, но не позволяет ему переходить и связывать каналы другой
стороны и остальные подканалы сервера.

## MMORPG Рейд

Предполагаем такую структуру:

  - Root
      - Raid
          - Healers
          - Tanks
          - Damage Dealers
          - Wussards and other pets

Хотим назначить командиров каждого подразделения и всего рейда.

Делаем так: При редактировании канала Raid создаем группу
"groupleaders". Добавляем лидера каждого подразделения в эту группу. В
этом же канале создаем группу "raidleaders" и добавляем в неё лидеров
всего рейда.

Настройки ACL канала Raid:

1.  @all Запретить Вход, Запретить Говорить \[Применить к этому каналу\]
2.  @raidleaders Разрешить Вход, Разрешить Говорить, Разрешить Связывать
    канал, Разрешить Глушить, Разрешить Доступ \[Применить к подканалам
    и Применить к этому каналу\]
3.  @groupleaders Разрешить Говорить, Разрешить Связывать канал
    \[Применить к этому каналу\]
4.  @groupleaders Разрешить Связывать канал, Разрешить Глушить,
    Разрешить Доступ \[Применить к подканалам\]

Первое правило закрывает всем возможность говорить и заходить на канал
Raid. Второе правило снимает эти запреты для группы "raidleaders" и дает
им расширенные полномочия. Третье правило позволяет группе
"groupleaders" заходить и связывать канал Raid. Четвёртое правило даёт
группе "groupleaders" возможность связывать подканалы, а также
избавляться от проблемных игроков.

Обычные игроки не смогут зайти на канал Raid, но они могут заходить на
любые подканалы. Все будут слышать командиров подразделений и рейда
после связывания каналов. Лидеры рейда будут слышать командиров групп
и не будут слышать обычных игроков. Таким образом все игроки будут
слышать лидеров рейда (командирам групп не придётся повторять
команды) и не будут мешать остальному рейду.

[Category:Documentation
Russian](Category:Documentation_Russian "wikilink") [Category:Needs
Update for 1.2.0](Category:Needs_Update_for_1.2.0 "wikilink")