The RPC subcommand allows users to more easily issue SocketRPC requests
to a running Mumble client in version 1.3.0 or higher.

Currently, only commands for muting/deafning are supported.

Supported commands are currently:

  - 'mute' - Unmute self
  - 'unmute' - Unmute self
  - 'togglemute' - Toggle self-mute status
  - 'deaf' - Deafen self
  - 'undeaf' - Undeafen self
  - 'toggledeaf' - Toggle self-deafen status

(You can also see them via 'mumble rpc --help')

Example: <code>

` $ mumble rpc mute    # Mute a running Mumble client`
` $ mumble rpc unmute  # Unmute a running Mumble client`
` [...]`

</code>

## See also

An alternative to this subcommand is the usage of [DBus methodes for the
client](DBus#DBus_in_the_Mumble_client "wikilink").

[Category:Documentation
English](Category:Documentation_English "wikilink") [Category:Mumble
Client](Category:Mumble_Client "wikilink")
[Category:1.3.0](Category:1.3.0 "wikilink")