# Languages|ACL Tutorial
[[category:Documentation English]]

=ACL tutorial=
This tutorial will help you understand how permissions work on Mumble. Details about this topic can be found in [[ACL and Groups]], where there are some examples, descriptions of special groups, etc.

##What we are going to do
We are going to set a server, with a ''General chat'' channel where everyone can talk. We are also creating a ''Custom channels'' channel where anyone who is authed can create and administrate his own channel.
Then, as a normal authed user, we will create a couple of channels for a FPS game where people can talk either to their team or to everyone just by pressing one key.

Enough talking, let's get to work.

##Setting permission for the whole server
First, we will need to set up a password for the SuperUser. If you haven't done that yet, you can do it by typing this at a console/command prompt:
 murmur -ini /path/to/murmur.ini -supw somepassword

Then, we open Mumble and connect to the server using SuperUser and the password we have just set. You should be looking at something like this now:

(image missing)

Let's start with the permissions. Open the ACL editor, you can do this by selecting "Edit ACL" from the Channel menu. Once we are there, you can see a window with two tabs. The first one is for defining people who are in a group, etc. The second one is used to assign permissions to groups. 
Right now, in that tab, you should have two rules set: 
*The first one allows people on the auth group to create channels in the root channel and its subchannels.
*The second one allows people in the group admins to ''Write'', that means edit permissions.

For now, we will delete the rule related with the auth group by selecting it and clicking remove. We said that we don't want anyone in the root channel, as we will make a ''General chat'' channel for that. So we will add a rule to keep them out. To do that, click add, and click every checkbox in the deny column except the ''Traverse'' one.

The reason to leave traverse unchecked is because it will forbid people to enter this channel '''and''' subchannels. Since every other channel is a subchannel of root, this will effectively forbid people from entering any channel. So we leave it unchecked. It is not neccesary to mark the allow check, because ''Traverse'' is allowed by default. Default settings are:
*Allow: Traverse, Enter, Speak and AltSpeak
*Deny: Write, Mute/Deafen, Move/Kick, Make Channel and Link channel

If you are wondering, yes, we could have left Write, Mute/Deafen, Move/Kick, Make Channel and Link channel unchecked and they will still be forbidden. There is no reason to leave those rights denied as they will be by default. Now your screen should be looking like this (except that you have disabled some useless checks):

(image missing)

In Mumble, rules are applied from top to bottom. Right now, the:
 @admins allow write
rule is useless as it will get over written by the
 @all deny write ...
So we will have to fix it. Simply select the rule referring to all and click up. That should put that on top. You have now established some default settings for the whole server :)

(image missing)

##Creating the ''General chat'' channel and setting its permissions
This channel will serve as a chat room for everyone that gets to join our channel. Since we don't allow them to speak in the root channel, and they must join this channel if they want to chat, maybe we should put a welcome message to the server that warns about that. Anyways, here we go.
First, create the channel. This is as easy as clicking Channel->Add (or right-clicking in the channel you want and click add to create a subchannel, but you know, root isn't shown, so we will use the menu one). In the box that appears type the channel name, click ''OK'' and we are done.

Now, we want to give the right for everyone to speak here. So we head to ''Edit ACL'' (remember to select the new channel before). You will see the rules of the root channel, but if you select them, you will see that all the options are grayed out. That's because they are inherited from the parent channel (in this case, ''Root''). If you uncheck the  ''Inherit ACL's'' option, they will disappear, but we don't want that. Just add a new rule that allow everyone (group=all) to Speak or AltSpeak and click ok to save it. We are now done with this channel. Easy, no?.

(image missing)

##Creating the ''Custom channels'' channel and configuring it
As we said, we will let anyone who is registered to create his own channel here. The first step is easy, create the channel just as we did before. You should have something like this just in front of your nose:

(image missing)

Now we'll be giving ''Make channel'' rights to authed people. Just go to ACL editor, add a new rule, in the group list select or write auth and select the allow make channel checkbox.
'''Warning:''' If you type the group name, make sure you press enter when you've finished. This will update the rule group. You can see that if you type and don't press enter, it will not change the group in the top listing.

(image missing) (image missing)

And now we have a pretty channel where people can create their own channel. Note that they cannot even enter ''Custom channels'' channel but they still can create subchannels. Isn't it cool?

=Registered user=
In this part, we will be playing a registered and authed player with a veeeeery original name: AuthedPlayer. He will be creating his own channels to host a little public channel and two private subchannels, one for each team of a FPS game. He would like that they can talk to their team or to both teams. We are seeing how to do this with the AltSpeak right, linking channels and more.

##Creating the main channel
After logging in, we may play a little to check that we can't enter the root channel once we leave it (the first time you connect you will land here), that we cannot enter the ''Custom channels'' channel, etc. Once we have checked that permissions are working as expected we start creating our first channel. We simply right click in ''Custom channels'' (remember that you can still use the menu) and click add to create a new channel. As I am very creative I called it ''My Private Channel''. Automatically we are added to the admins group in that channel, so we can ''Write'' on it (remember the rules in the root channel? they are inherited all the way down to our channel). But that also mean that we get the ''Make channel'' permission inherited, so everyone who is authed can make a channel inside ours. We don't like that so...

(image missing)

Our rule will overwrite the inherited one, because inherited rules are always put at top. So now that we have our channel secured, we will give permission to enter and speak:

(image missing)

Note that we have disabled ''Applies to sub-channels''. As subchannels will not be public, we don't want them to have the ''Enter'' permission granted. If we haven't disabled this option, we have to create yet another rule just to deny the ''Enter'' permission. This way is easier. And now, we have this channel ready for service. Let's continue with the subchannels.

##Creating the team subchannels
First, we create two subchannels of our own channel. As usual I called them in a very creative way... Team1 and Team2. We could define rules for each one, but it is quicker to define them in the parent channel (My Private Channel) and make the subchannels inherit the rules. First, we want people in one team channel to be able to speak so we do it like that:

(image missing)

Notice that we have unchecked the ''Apply to this channel'' option, as we are defining this rule only for  the subchannels. More interesting is the use of the speacial group ''in''. This group refers to the people that are inside the channel the rules refers to. It appears it is the same as all, but it is quite different: 
We are going to link both channels. That means that people in different channels will hear each other. But we want that people only can hear teammates. So we use ''in'' to give Speak privileges to people in the same channel. This means, people in Team2 can't hear people in Team1 because the people in Team1 don't have rights to speak in Team2 because the ''in'' group only gives them permission in his own channel. It is a little complicated to understand at first, but it is very useful. To understand it, you have first to understand that each channel has its separate groups. That means that ''in'' group in Team1 is no the same group that ''in'' group in Team2.

To explain it better I'm going to use some names...
*Jack is in Team1
*John is in Team2
Both channels are linked, so the voice will be transmitted from one to the other as long as the speaker have rights in the destination channel. Jack speaks but John will not be able to hear it. That is because Jack has no rights to speak in Team2 as it is not in the Team2's ''in'' group. So voice will not be transmitted across the channel link and John will not be able to hear Jack.
If we have used ''all'' instead of ''in'' for the rule, Jack and John will hear each other without a problem, as everyone is in ''all'' group.

Well, let's continue. We wanted to people talk to the other team. This is when AltSpeak comes handy. We add a rule like this:

(image missing)

This will allow everyone (both teams) to talk to each other when AltSpeaking. AltSpeak is enabled while pressing a key defined in Shortcuts (in the Mumble options). While holding down that key, voice will be transmitted using the AltSpeak rights. As we allowed anyone to AltSpeak and both channels are linked, that means that if someone talks while pressing the key, it will be heard by both teams.

And we are done.

##How it looks like for some anonymous players
First you "invite" them to your team channels (you can move them from your public channel to your team channels by drag-and-drop). They have to be in your public channel to do that, as you will need Move permissions in both the origin and destination channels. If not AltSpeaking...

(image missing) (image missing)

If AltSpeaking:

(image missing) (image missing)

=Final notes=
This is a quick tutorial and I have not explained a lot of things. For example custom groups. They should be easy to figure out but here goes a quick explanation:
*You define rights for that group by simply writing the group name in the group box (remember, ENTER is your friend;)) and marking the appropriate checkboxes. 
*To add a person to the group you go to the other tab in the ACL editor, select the group name in the group box (or write it+enter), write the name you want to add in the box at the botton of the added list and press the corresponding add button. You can only add registered nicks to that list.
*Groups are per-channel and are inheritable. If you want to inherit some group members, you can mark inherit and add the members you don't want to be part of the group in the specific channel to the remove list (there is a button at the end of the inherited list to make this easy).
I have also left behind the use of the sub group. You can find more info about that in [[ACL and Groups]]

There are a lot of rules that could have been made easier. For example, in the last part of the tutorial, you could stick the ''deny Make Channel'' and the ''allow AltSpeak'' in the same rule applied to both channel and subchannels. This is just an example of which can be made without going too deep, feel free to create your own impossible-to-understand layouts and add them to the examples section in [[ACL and Groups]]

And last but not least, please leave a comment in the discussion page of this article if you feel like that. Thanks :)

= Further Information =
Further documentation on [ACL and Groups is available](ACL and Groups.md).

External links:  [(Video)](https://www.youtube.com/watch?v=VOeMsMjQRoM Setting Channel Permissions in your Mumble Server)

