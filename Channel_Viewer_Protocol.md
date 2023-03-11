People often wish to have a view on their Mumble servers without needing to actually
run the client. This is mostly accomplished using a web based channel viewer which
retrieves channel and user data from a web server, which in turn queries it from
Murmur, and then using techniques like JavaScript to render that data into a nice
tree structure.

As multiple channel viewers started to arise, developers found the consensus that
using a standardized format for data retrieval yields multiple advantages, the most
important of which is interoperability: The need for using a specific server and
viewer does not arise when all servers and viewers use a shared data format, thus
allowing for both parts to be exchanged easily and independent from one another.

A good example implementation is [[Mumble reader]], written in PHP and JQuery. It uses IcePHP to query Murmur via [[Ice]] and generate the Channel Viewer Protocol JSON data, which the JQuery front-end reads and formats into the channel viewer itself. The Ice query code only works with IcePHP versions earlier than 3.4, although other query services can be read by its JQuery front-end.

## General notes 

### Data integrity 

The data format should generally be aimed towards delivering information retrieved
from Murmur unaltered. That means that any field that exists in Murmur should be
exposed by the server (unless there is a really good reason not to do so, like for
passwords and the like), and it should not alter any fields that exist in Murmur
to prevent confusion.

### Custom data fields 

If the implementer of the protocol chooses to add extra information that does not
originate from Murmur itself, these fields should be prefixed with "x_" in order
to prevent name clashes (so for example, a custom field named "coolstuff" should
be named "x_coolstuff" instead).

If a client encounters a field which it does not understand, it must ignore that
field.

### Empty fields 

In general, empty fields should be treated as if they would not have been set at
all. This means that a client should not rely on that a field that exists actually
has a usable value.

### Encoding 

The documents, be it JSON or XML, should be encoded in UTF-8 in order to be as
easily usable as possible. Servers must set their encoding headers correctly to
prevent encoding issues.

### The Address field 

The address field in the user records requires special attention for multiple reasons.

* To respect users' privacy, user records should generally not contain the address if the request does not provide any means of authentication. What kind of authentication the client needs to provide is a bit hard to say; a compromise between security and ease of implementation (both client- and server side) is to accept both...
** the standard authentication means of the platform the server is implemented in; that means if your server implementation uses a web framework, its built-in authentication (e.g. through cookies) should be accepted. This way, web based clients will support authentication without any further modification.
** HTTP Basic auth if no other authentication data has been provided, to enable non-web-based clients to retrieve the address information if they need to.
* To ease client implementation, the server should set the "x_addrstr" field to a string that contains either...
** a fully qualified domain name: "somewhere.example.com".
** an IPv4 address in dotted quad notation: "192.168.0.1".
** an IPv6 address in colon notation: "2001:6f8:108f:1:21f:3cff:wx:yz".

Note however that in most cases, the users' addresses will not even be needed by the
client, so most of this shouldn't even apply to most clients.

If a server does not support delivering users' addresses at all, it should just ignore
any authentication data the client may have sent.


## Example Channel tree 

All examples are based on the following channel structure:

* test server
** newtesting
** testing
*** htmlsubtesting - This channel has HTML elements in its description
**** subsubtesting
*** plainsubtesting - This channel has HTML elements in its description which are escaped and should NOT be evaluated
**** subsubtesting


## JSON 

To expose the full channel tree using JSON, start with the root channel and
recursively add the users and data to it.

In order to make cross-site requests easier, the server must implement
 [JSONP](http://bob.pythonmac.org/archives/2005/12/05/remote-json-jsonp/).
The name for the request parameter that holds the callback name must be
"callback". If this parameter is not specified, the server must not wrap
the JSON in parenthesis to ensure compatibility with e.g. Python's
simplejson.

### Server format 

The root object of the tree must always be the server itself, which has
the following properties:

 'id': 1,             // The ID of this server instance
 'name': 'some name', // The server's name
 'root': {...},       // The root channel object

And may optionally have:

 'x_connecturl': 'mumble://somewhere/'
 'x_uptime': 7156     // The number of seconds this server has been running

### Channel format 

A Channel entry must at least contain the following fields:

 'description': '',
 'id': 0,
 'links': [],         // A list of IDs that name linked channels
 'name': 'Root',
 'parent': -1,
 'users': [],         // A list of users in this channel
 'position': 0,
 'channels': [],      // A list of subchannels
 'temporary': false

And may optionally contain:

 'x_connecturl': 'mumble://somewhere/somechannel'

### User format 

A User entry must at least contain the following fields:

 'channel': 40,
 'deaf': false,
 'mute': false,
 'name': 'Yps0',
 'selfDeaf': false,
 'selfMute': false,
 'session': 143,
 'suppress': false,
 'userid': 4,

And may optionally contain:

 'address': (0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 255, 255, 192, 168, 0, 10),
 'x_addrstring': '192.168.0.10',           // A nicely formatted version of the IP address (hostname, dotted quad, IPv6 notation)
 'recording': false,
 'bytespersec': 6580,
 'comment': '',
 'context': '',
 'identity': '',
 'idlesecs': 0,
 'onlinesecs': 161,
 'os': 'Win',
 'osversion': '5.1.2600.1',
 'prioritySpeaker': false,
 'release': '02071e',
 'tcponly': false,
 'x_texture': 'http://shotgunfun.de/mumble/1/4/texture.png',   // A URL to retrieve the texture/avatar from
 'version': 66051

Which fields to expose may depend on the user of the channel viewer, e.g. the IP adress
may be shown to certain logged-in users only.

### Full Example: JSON 

Serializing the aforementioned channel structure as JSON, we will get:
 {
    "x_connecturl": "mumble://kuunavang.funzt-halt.net?version=1.2.2", 
    "x_uptime": 53289, 
    "root": {
        "channels": [
            {
                "channels": [], 
                "x_connecturl": "mumble://kuunavang.funzt-halt.net/newtesting?version=1.2.2", 
                "temporary": false, 
                "description": "", 
                "parent": 0, 
                "position": 0, 
                "users": [], 
                "name": "newtesting", 
                "links": [], 
                "id": 6
            }, 
            {
                "channels": [
                    {
                        "channels": [
                            {
                                "channels": [], 
                                "x_connecturl": "mumble://kuunavang.funzt-halt.net/testing/htmlsubtesting%20%C3%B6%C3%A4%C3%BC/subsubtesting?version=1.2.2", 
                                "temporary": false, 
                                "description": "", 
                                "parent": 4, 
                                "position": 0, 
                                "users": [], 
                                "name": "subsubtesting", 
                                "links": [], 
                                "id": 5
                            }
                        ], 
                        "x_connecturl": "mumble://kuunavang.funzt-halt.net/testing/htmlsubtesting%20%C3%B6%C3%A4%C3%BC?version=1.2.2", 
                        "temporary": false, 
                        "description": "This channel has <i>HTML</i> elements in its description that are evaluated as <span style=\"color:#ff0000\">red </span><b><span style=\"color:#ff0000\">bold</span></b> Fonts!", 
                        "parent": 1, 
                        "position": 0, 
                        "users": [
                            {
                                "comment": "", 
                                "mute": false, 
                                "suppress": false, 
                                "selfDeaf": false, 
                                "x_addrstring": "2001:6f8:108f:1:21f:3cff:wx:yz", 
                                "deaf": false, 
                                "selfMute": true, 
                                "bytespersec": 0, 
                                "session": 1, 
                                "tcponly": false, 
                                "address": [ 32, 1, 6, 248, 16, 143, 0, 1, 2, 31, 60, 255, w, x, y, z ], 
                                "idlesecs": 33, 
                                "identity": "", 
                                "name": "svedrin", 
                                "userid": 1, 
                                "version": 66050, 
                                "context": "", 
                                "release": "1.2.2-2", 
                                "osversion": "Debian GNU/Linux unstable (sid)", 
                                "os": "X11", 
                                "onlinesecs": 35, 
                                "channel": 4
                            }
                        ], 
                        "name": "htmlsubtesting \u00f6\u00e4\u00fc", 
                        "links": [
                            2
                        ], 
                        "id": 4
                    }, 
                    {
                        "channels": [
                            {
                                "channels": [], 
                                "x_connecturl": "mumble://kuunavang.funzt-halt.net/testing/plainsubtesting/subsubtesting?version=1.2.2", 
                                "temporary": false, 
                                "description": "", 
                                "parent": 2, 
                                "position": 0, 
                                "users": [], 
                                "name": "subsubtesting", 
                                "links": [], 
                                "id": 3
                            }
                        ], 
                        "x_connecturl": "mumble://kuunavang.funzt-halt.net/testing/plainsubtesting?version=1.2.2", 
                        "temporary": false, 
                        "description": "This channel has &lt;i&gt;HTML&lt;/i&gt; elements in its description that are not evaluated as &lt;span style=&quot;color: red&quot;&gt;red &lt;b&gt;bold&lt;/b&gt;&lt;/span&gt; Fonts!", 
                        "parent": 1, 
                        "position": 0, 
                        "users": [], 
                        "name": "plainsubtesting", 
                        "links": [
                            4
                        ], 
                        "id": 2
                    }
                ], 
                "x_connecturl": "mumble://kuunavang.funzt-halt.net/testing?version=1.2.2", 
                "temporary": false, 
                "description": "", 
                "parent": 0, 
                "position": 0, 
                "users": [], 
                "name": "testing", 
                "links": [], 
                "id": 1
            }
        ], 
        "x_connecturl": "mumble://kuunavang.funzt-halt.net?version=1.2.2", 
        "temporary": false, 
        "description": "", 
        "parent": -1, 
        "position": 0, 
        "users": [], 
        "name": "Root", 
        "links": [], 
        "id": 0
    }, 
    "name": "test server", 
    "id": 1
 }

## XML 

For XML, the same principles apply as for JSON, along with the following encoding principles:

* Boolean values are represented as "true" or "false"
* Lists (e.g. for the players' IP addresses or the channel links) are space-separated numbers

The root element (<tt><server></tt>) should set the following namespace attributes:

* xmlns="http://mumble.sourceforge.net/Channel_Viewer_Protocol"
* xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance
* xsi:schemaLocation="http://bitbucket.org/Svedrin/mumble-django/wiki/channel-viewer-protocol_murmur-X-Y-Z.xsd" with X.Y.Z being the version of Murmur that the data in this document originates from.

As XML Schema Definitions need to be adapted to match the fields returned by Murmur,
including the correct Murmur version in the URL is important to enable a correct
validation. Currently, the following XSD documents are available:

{| border="1" cellspacing="0" cellpadding="5" align="center"
! Murmur Version
! XSD URL
|- 
| 1.2.2
| http://bitbucket.org/Svedrin/mumble-django/wiki/channel-viewer-protocol_murmur-1-2-2.xsd
|- 
| 1.2.3
| http://bitbucket.org/Svedrin/mumble-django/wiki/channel-viewer-protocol_murmur-1-2-3.xsd
|}



### Server Format 

A server is represented using the <tt><server /></tt> tag.

### Channel Format 

A channel is represented using the <tt><channel /></tt> tag.

### User Format 

A user is represented using the <tt><user /></tt> tag.

'''Warning''': Mumble includes NULL bytes in the ''context'' field, so the context field - if not empty - must be base64 encoded.

### Full Example: XML 

 <?xml version="1.0" encoding="UTF-8" ?>
 <server
  xmlns="http://mumble.sourceforge.net/Channel_Viewer_Protocol"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance
  xsi:schemaLocation="http://bitbucket.org/Svedrin/mumble-django/wiki/channel-viewer-protocol_murmur-1-2-3.xsd"
  id="1"
  name="test server"
  x_connecturl="mumble://kuunavang.funzt-halt.net?version=1.2.2">
   <channel
    description=""
    id="0"
    links=""
    name="Root"
    parent="-1"
    position="0"
    temporary="false"
    x_connecturl="mumble://kuunavang.funzt-halt.net?version=1.2.2">
     <channel
      description=""
      id="6"
      links=""
      name="newtesting"
      parent="0"
      position="0"
      temporary="false"
      x_connecturl="mumble://kuunavang.funzt-halt.net/newtesting?version=1.2.2" />
     <channel
      description=""
      id="1"
      links=""
      name="testing"
      parent="0"
      position="0"
      temporary="false"
      x_connecturl="mumble://kuunavang.funzt-halt.net/testing?version=1.2.2">
       <channel
        description="This channel has &lt;i&gt;HTML&lt;/i&gt; elements in its description that are evaluated as &lt;span style=&amp;quot;color:#ff0000&amp;quot;&gt;red &lt;/span&gt;&lt;b&gt;&lt;span style=&amp;quot;color:#ff0000&amp;quot;&gt;bold&lt;/span&gt;&lt;/b&gt; Fonts!"
        id="4"
        links="2"
        name="htmlsubtesting"
        parent="1"
        position="0"
        temporary="false"
        x_connecturl="mumble://kuunavang.funzt-halt.net/testing/htmlsubtesting?version=1.2.2">
         <channel
          description=""
          id="5"
          links=""
          name="subsubtesting"
          parent="4"
          position="0"
          temporary="false"
          x_connecturl="mumble://kuunavang.funzt-halt.net/testing/htmlsubtesting/subsubtesting?version=1.2.2" />
         <user
          address="32 1 6 248 16 143 0 1 2 31 60 255 w x y z"
          bytespersec="0"
          channel="4"
          comment=""
          context="QmF0dGxlZmllbGQgQmFkIENvbXBhbnkgMgA= "
          deaf="false"
          identity=""
          idlesecs="1693"
          mute="false"
          name="svedrin"
          onlinesecs="2943"
          os="X11"
          osversion="Debian GNU/Linux unstable (sid)"
          release="1.2.2-2"
          selfDeaf="false"
          selfMute="false"
          session="7"
          suppress="false"
          tcponly="false"
          userid="1"
          version="66050"
          x_addrstring="2001:6f8:108f:1:21f:3cff:wx:yz" />
       </channel>
       <channel
        description="This channel has &amp;lt;i&amp;gt;HTML&amp;lt;/i&amp;gt; elements in its description that are not evaluated as &amp;lt;span style=&amp;quot;color: red&amp;quot;&amp;gt;red &amp;lt;b&amp;gt;bold&amp;lt;/b&amp;gt;&amp;lt;/span&amp;gt; Fonts!"
        id="2"
        links="4"
        name="plainsubtesting"
        parent="1"
        position="0"
        temporary="false"
        x_connecturl="mumble://kuunavang.funzt-halt.net/testing/plainsubtesting?version=1.2.2">
         <channel
          description=""
          id="3"
          links=""
          name="subsubtesting"
          parent="2"
          position="0"
          temporary="false"
          x_connecturl="mumble://kuunavang.funzt-halt.net/testing/plainsubtesting/subsubtesting?version=1.2.2" />
       </channel>
     </channel>
   </channel>
 </server>

## Existing Implementations 

A number of implementations exist already, which one you choose depends mostly on your needs. If you only want a channel viewer and no administration capabilities, you might want to go with  [MumPI]([Mumble-Django]](http://code.google.com/p/mumblereader/ MumbleReader]. For a full-featured web administration interface that also features CVP, check out) or [[Mumble_PHP_Interface.md).

More information is to be found on the [3rd Party Applications](3rd Party Applications#Channel_Viewers.md) page.

## Authors and Contact 

This standard has been written based on the consensus made on [[IRC]]: #mumble on irc.freenode.net.

Main authors:
* Michael "Svedrin" Ziegler <diese-addy@funzt-halt.net>
* Pimmetje
* S_Roach

If you wish to discuss parts of this standard or help maintaining it, you should join the [[IRC]]
channel or send a mail to Svedrin.


