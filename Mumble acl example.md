
This example shows you howto create a channel where all users will be redirected after joining the server, authenticated users will be able to move around but others (guests) can only speak in this channel and are not allowed to move around

Info:
If this is a fresh mumble install you have to set the SuperUser password first:
murmur -ini /path/to/murmur.ini -supw somepassword



1. Setting the defaultchannel

Connect as Admin or SuperUser.
Create a channel that will serve as the "first channel", for example: Entrance
Take a look at murmur.log, you will find a line looking like this one:

<W>2010-02-02 22:30:34.873 1 => <26:SuperUser(0)> Added channel Entrance [Root[0:-1](4:0] under)

4 is the channel ID in this case that we want.

Add defaultchannel=4 to [[murmur.ini]] and restart the server.



2. Permissions

Now every user is redirected to the Entrance channel but everyone can still move around. Lets change that.
Right click on Root, choose Edit -> Permissions and add a new rule called all.
After you moved @all to the position below you will see:

@''all''

@all   <----------- New

@admin

@auth


change @all to disallow: enter, register. dont set any other permissions for this rule. This denys users to enter the root channel and to register themselves, because if they could register themselves they could move around freely (You can still register other users as admin).
Set "Applies to sub-channels".
Keep the other rules as they are.

Now lets change the permission for Entrance, below permissions you will see all rules that are inherited:
@''all''

@''all''

@''admin''

@''auth''

Add a new rule called all and allow traverse, enter, speak (im not sure about traverse, works if its enabled). disallow all other options.
Add a new rule called auth and allow traverse, enter, speak, move. dont allow/disallow anything else.
And your done :)



