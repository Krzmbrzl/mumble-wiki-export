MurmurCL is a basic console interface to some of the functionality the murmur server exposes via the [[Ice]] RPC mechanism.

'''Note:''' As MurmurCL was mainly written for testing purposes it has some limits and usability issues.

## Features 
Following is a list of the features included in the script as of writing this:

'''Add servers'''

Adds a virtual server to a mumble instance

'''Delete servers'''

Deletes a virtual server from a mumble instance

'''List servers'''

Lists virtual servers on a mumble instance

'''Configure servers'''
Sets a config variable on a virtual server



'''Add players'''

Adds a player to a virtual server

'''Delete players'''

Deletes a player from a virtual server

'''List players'''

Lists players registered on a virtual server

'''Configure players'''

Sets a config variable of a user on a virtual server



'''List channels'''

List channels on a virtual server

'''Add channels'''

Adds a channel to a virtual server

'''Delete Channels'''

Deletes a channel from a virtual server



'''Help'''

Help about the commands with short description and syntax explanation

## Examples 
### The help command 
If you want to get information about a command the help function is very useful. It can be called with one or zero parameters. If you call it without any parameters it looks like this:
   console> ./murmurcl.py help
   
       Displays this help
       usage: help [command]
   
   
   Available commands: ['addchannel', 'listplayers', 'addserver', 'cfgserver', 'listservers', 'listchannels', 'startserver'
   , 'addplayer', 'cfgplayer', 'delchannel', 'delplayer', 'stopserver', 'delserver']
If you want information about a specific command just use it's name as the paramter for help.
   console> ./murmurcl.py help addserver
   
       Add a new virtual server to the murmur instance
       usage: addserver [port]


### Setting a default channel 
Mumble has some features which are not accessible via the default graphical user interface. One of them is setting a default channels players will join when they connect to the server. This can be done by setting the defaultchannel paramter for a server.

To do this we first have to find out the port of our server, you usually know this but let's say you don't.   
   console> ./murmurcl.py listservers
   ###==
   Id              Port            Running
   ###==
   1               64738           True

After that we have to find out the id of the channel you want to set as default.
   console> ./murmurcl.py listchannels 64738
   ###==
   Id      Parent  Name
   ###==
   0       -1      Root
   1       0       A channel
Ok, now we have the id of "A channel", let's make it the new default:
   console> ./murmurcl.py cfgserver defaultchannel 1 on 64738
   'defaultchannel' set to '1' on server 64738

Now new players will always join "A channel" instead of "Root". Be aware that this doesn't work on clients which choose their default channels themselves.



