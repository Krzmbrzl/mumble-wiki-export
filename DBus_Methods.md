This is a documentation of the DBus interface. Mostly useful for
creating scripts for interacting with Murmur.

# net.sourceforge.mumble.Meta

  - **start**

<!-- end list -->

  -
    Starts a virtual server
    input parameters:
      - \[int\] server_id The specific server

<!-- end list -->

  - **stop**

<!-- end list -->

  -
    Stops a virtual server
    input parameters:
      - \[int\] server_id The specific server

<!-- end list -->

  - **newServer**

<!-- end list -->

  -
    Creates a new virtual server
    output parameters:
      - \[int\] server_id The id of the new created server

<!-- end list -->

  - **deleteServer**

<!-- end list -->

  -
    deletes a virtual server
    input parameters:
      - \[int\] server_id The specific server

<!-- end list -->

  - **getBootedServers**

<!-- end list -->

  -
    Returns a list of all active servers
    output parameters:
      - \[int\]\* server_id

<!-- end list -->

  - **getAllServers**

<!-- end list -->

  -
    Returns a list of all servers
    output parameters:
      - \[int\]\* server_id

<!-- end list -->

  - **isBooted**

<!-- end list -->

  -
    check, whether a server is booted
    input parameters:
      - \[int\] server_id
    output parameters:
      - \[boolean\] is_booted

<!-- end list -->

  - **getConf**

<!-- end list -->

  -
    receive the configuration of a server by key
    input parameters:
      - \[int\] server_id
      - \[string\] key
    output parameters:
      - \[string\] value

<!-- end list -->

  - **getAllConf**

<!-- end list -->

  -
    receive the whole configuration of a server
    input parameters:
      - \[int\] server_id
    output parameters:
      - \[string|string\]\* key-\>value map

<!-- end list -->

  - **getDefaultConf**

<!-- end list -->

  -
    receive the default configuration
    output parameters:
      - \[string|string\]\* key-\>value map

<!-- end list -->

  - **setConf**

<!-- end list -->

  -
    set the value of a specific key on a specific server
    input parameters:
      - \[int\] server_id
      - \[string\] key
      - \[string\] value

<!-- end list -->

  - **setSuperUserPassword**

<!-- end list -->

  -
    set the superuser password on a specific server
    input parameters:
      - \[int\] server_id
      - \[string\] password

<!-- end list -->

  - **rotateLogs**

<!-- end list -->

  -
    rotate the logs

<!-- end list -->

  - **getLog**

<!-- end list -->

  -
    get the log of a specific server in a specific time frame
    input parameters:
      - \[int\] server_id
      - \[int\] min_seconds
      - \[int\] max_seconds

<!-- end list -->

  - **quit**

<!-- end list -->

  -
    shutdown the server

# Server-specific methods

## getPlayers

  - input:nothing
  - returns a list of PlayerInfoExtended(see below)

## getChannels

  - input:nothing
  - returns a list of ChannelInfo(idem)

## getACL

  - input:chan identifier(int)
  - returns a list containing \[a list of ACLInfo, a list of GroupInfo,
    a boolean for inherit\]

## setACL (todo)

  -
  -
## getBans

  - nothing
  - list of BanInfo

## setBans

  - list of BanInfo
  - nothing

## getPlayerState

  - player session id(unsigned int) (warning, unsigned ints are special,
    see below)
  - PlayerInfo

## setPlayerState

  - PlayerInfo
  - nothing

## getPlayerNames

  - list of session id(unsigned ints) (warning, same as above)
  - list of names(unicode strings)

## getPlayerIds

  - list of names(strs on unicode strs)
  - list of IDs(ints(regular ones))

## addChannel

  - name(str or unicode str) , parent's id(int)
  - id of the new chan(int)

## removeChannel

  - chan id(int)
  - nothing

## setChannelState

  - ChannelInfo
  - nothing

## kickPlayer

  - session id(unsigned int) , reason(str or unicode str)
  - nothing

# Warning

unsigned ints are a bit strange. They look like longs when Python reads
them (1786L for instance) but Python must transform them before sending
them ot dbus.)

    >>>import dbus
    >>>egg=178L
    >>>spam = dbus.UInt32(egg)  #may vary depending on your plateform
    and now, spam is a dBus unsigned int and is ready to be sent

# Structures (e.g. omagad, what is PlayerInfo ???)

  - **PlayerInfo** is a tuple (static list) containing (dont forget to
    transform session before sending it):

<!-- end list -->

  -
    (session:long, mute:bool, deaf:bool, suppressed:bool, selfMute:bool,
    selfDeaf:bool, channel:int)

<!-- end list -->

  - **PlayerInfoExtended** is a tuple (static list) containing (you just
    receive it with getPlayerState, you never have to send one)(notice
    that the 7 first are exactly the same as PlayerInfo: (session:long,
    mute:bool, deaf:bool, suppressed:bool, selfMute:bool, selfDeaf:bool,
    channel:int, id:int, name:unicode str, onlinesecs:int,
    bytespersecond:int))

<!-- end list -->

  -

<!-- end list -->

  - **ChannelInfo** is a tuple containing:

<!-- end list -->

  -
    (id:int, name:str, parent:int, links:list of ints)

<!-- end list -->

  - **GroupInfo**:

<!-- end list -->

  -
    (name:str, inherited:bool, inherit:bool, inheritable:bool, add:list,
    remove:list, members:list)

<!-- end list -->

  - **ACLInfo**:

<!-- end list -->

  -
    (applyThere:bool, applySubs:bool, inherited:bool, id:int, group:str,
    allow:long, deny:long)

<!-- end list -->

  - **BanInfo**:

<!-- end list -->

  -
    (address:long, bits:int)

# Implementation

To access the server interface, proceed as following:

    >>>import dbus
    >>>bus = dbus.SystemBus() # assuming that you are using a system bus
    >>>server = bus.get_object('net.sourceforge.mumble.murmur', '/1') # assuming that you want to control the server number 1
    >>> # to use methods, do:
    >>>server.method(args)

[Category:Development](Category:Development "wikilink")
[Category:Documentation
English](Category:Documentation_English "wikilink")