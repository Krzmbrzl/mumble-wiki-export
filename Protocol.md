The Mumble Protocol is Open Source, just like Mumble itself. The source
code for the current version can be found in the Git repository in the
file
[Mumble.proto](https://github.com/mumble-voip/mumble/blob/master/src/Mumble.proto).

# Protocol documentation

A complete documentation about the protocol can be found at
[readthedocs.org](https://mumble-protocol.readthedocs.org/en/latest/).

# UDP Ping packet

Mumble supports querying the following data by sending a ping packet to
the target server. Both the request and the response packets are
formatted in Big Endian.

The ping request packet contains the following data:

| Width   | Data type | Value | Comment                       |
| ------- | --------- | ----- | ----------------------------- |
| 4 bytes | int       | 0     | Denotes the request type      |
| 8 bytes | long long | ident | Used to identify the reponse. |

The response will then contain the following data:

| Width   | Data type | Value                           | Comment                                                                                      |
| ------- | --------- | ------------------------------- | -------------------------------------------------------------------------------------------- |
| 4 bytes | int       | Version                         | e.g., \\x0\\x1\\x2\\x3 for 1.2.3. Can be interpreted as one single int or four signed chars. |
| 8 bytes | long long | ident                           | the ident value sent with the request                                                        |
| 4 bytes | int       | Currently connected users count |                                                                                              |
| 4 bytes | int       | Maximum users (slot count)      |                                                                                              |
| 4 bytes | int       | Allowed bandwidth               |                                                                                              |

Example implementations of pinging:

  - The official python script
    [mumble-ping.py](https://raw.githubusercontent.com/mumble-voip/mumble-scripts/master/Non-RPC/mumble-ping.py)
  - The IRC bot [K-10](K-10 "wikilink")’s [extension of that
    script](https://bitbucket.org/Svedrin/k10-plugins/src/tip/BwCalc/plugin.py#cl-120)
    that adds IPv6 support
  - The C\#/.NET Core [mumble-ping
    application](https://github.com/Kissaki/mumble-ping)
  - [PHP implementation](https://git.lolcat.ca/lolcat/mumble-ping)

[Category:Development](Category:Development "wikilink")