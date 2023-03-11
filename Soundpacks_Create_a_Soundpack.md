A [soundpack](Soundpacks "wikilink") in Mumble consists of one audio
file per notification class.

## How to create a Soundpack for Mumble

Record one audio file for every "notification class". See below for a
list of these classes.

**Important:** You cannot create one notification per message string but
only per notification class.

Zip all files into an archive, upload it somewhere and add it to
[soundpack](Soundpacks "wikilink").

## Notification classes and what could be said

A list of notification classes and what a speaker could say...

| Notification Class | Say as                           |
| ------------------ | -------------------------------- |
| ChannelJoin        | User joined channel.             |
| ChannelLeave       | User left channel.               |
| CriticalError      | Critical error occured.          |
| DebugInfo          | Debug information logged.        |
| Information        | Information logged.              |
| OtherMutedOther    | ?.                               |
| OtherSelfMute      | User state changed.              |
| PermissionDenied   | Permission denied.               |
| Recording          | Recording state changed.         |
| SelfMute           | You muted yourself.              |
| ServerConnected    | Connected.                       |
| ServerDisconnected | Disconnected.                    |
| TextMessage        | Incoming Message.                |
| UserJoin           | User connected.                  |
| UserKicked         | User was kicked.                 |
| UserLeave          | User disconnected.               |
| Warning            | Warning logged.                  |
| YouKicked          | You were kicked from the server. |
| YouMuted           | You were muted.                  |
| YouMutedOther      | You changed a user's state.      |

## Message Strings of all Notification Classes in Mumble

| String                                                                                             | Notification Class |
| -------------------------------------------------------------------------------------------------- | ------------------ |
| Server connection rejected: %1.                                                                    | ServerDisconnected |
| Welcome message: %1                                                                                | Information        |
| Welcome message: %1                                                                                | Information        |
| You were denied %1 privileges in %2.                                                               | PermissionDenied   |
| %3 was denied %1 privileges in %2.                                                                 | PermissionDenied   |
| Denied: Cannot modify SuperUser.                                                                   | PermissionDenied   |
| Denied: Invalid channel name.                                                                      | PermissionDenied   |
| Denied: Text message too long.                                                                     | PermissionDenied   |
| Denied: Operation not permitted in temporary channel.                                              | PermissionDenied   |
| You need a certificate to perform this operation.                                                  | PermissionDenied   |
| %1 does not have a certificate.                                                                    | PermissionDenied   |
| Invalid username: %1.                                                                              | PermissionDenied   |
| Invalid username.                                                                                  | PermissionDenied   |
| Channel is full.                                                                                   | PermissionDenied   |
| Channel nesting limit reached.                                                                     | PermissionDenied   |
| Denied: %1.                                                                                        | PermissionDenied   |
| Permission denied.                                                                                 | PermissionDenied   |
| %1 connected.                                                                                      | UserJoin           |
| %1 is now muted and deafened.                                                                      | OtherSelfMute      |
| %1 is now muted.                                                                                   | OtherSelfMute      |
| %1 is now unmuted.                                                                                 | OtherSelfMute      |
| Recording started                                                                                  | Recording          |
| Recording stopped                                                                                  | Recording          |
| %1 started recording.                                                                              | Recording          |
| %1 stopped recording.                                                                              | Recording          |
| You were muted and deafened by %1.                                                                 | YouMuted           |
| You were unmuted and undeafened by %1.                                                             | YouMuted           |
| You were muted by %1.                                                                              | YouMuted           |
| You were unmuted by %1.                                                                            | YouMuted           |
| You were undeafened by %1.                                                                         | YouMuted           |
| You were suppressed.                                                                               | YouMuted           |
| You were unsuppressed.                                                                             | YouMuted           |
| You were unsuppressed by %1.                                                                       | YouMuted           |
| You muted and deafened %1.                                                                         | YouMutedOther      |
| You unmuted and undeafened %1.                                                                     | YouMutedOther      |
| You muted %1.                                                                                      | YouMutedOther      |
| You unmuted %1.                                                                                    | YouMutedOther      |
| You undeafened %1.                                                                                 | YouMutedOther      |
| You suppressed %1.                                                                                 | YouMutedOther      |
| You unsuppressed %1.                                                                               | YouMutedOther      |
| %1 muted and deafened by %2.                                                                       | OtherMutedOther    |
| %1 unmuted and undeafened by %2.                                                                   | OtherMutedOther    |
| %1 muted by %2.                                                                                    | OtherMutedOther    |
| %1 unmuted by %2.                                                                                  | OtherMutedOther    |
| %1 undeafened by %2.                                                                               | OtherMutedOther    |
| %1 suppressed by %2.                                                                               | OtherMutedOther    |
| %1 unsuppressed by %2.                                                                             | OtherMutedOther    |
| You were moved to %1 by %2.                                                                        | ChannelJoin        |
| %1 moved to %2.                                                                                    | ChannelLeave       |
| %1 moved to %2 by %3.                                                                              | ChannelLeave       |
| %1 entered channel.                                                                                | ChannelJoin        |
| %1 moved in from %2 by %3.                                                                         | ChannelJoin        |
| %1 is recording                                                                                    | Recording          |
| You were kicked and banned from the server by %1: %2.                                              | YouKicked          |
| You were kicked from the server by %1: %2.                                                         | YouKicked          |
| %3 was kicked and banned from the server by %1: %2.                                                | UserKicked         |
| %3 was kicked from the server by %1: %2.                                                           | UserKicked         |
| %1 left channel.                                                                                   | ChannelLeave       |
| %1 disconnected.                                                                                   | UserLeave          |
| Server", "message from                                                                             | Source             |
| %2%1: %3                                                                                           | TextMessage        |
| Unable to find matching CELT codecs with other clients. You will not be able to talk to all users. | CriticalError      |
| The server requests minimum client version %1                                                      | Warning            |
| The server requests positional audio be enabled.                                                   | Warning            |
| The server requests positional audio be disabled.                                                  | Warning            |
| The server requests Push-to-Talk be enabled.                                                       | Warning            |
| The server requests Push-to-Talk be disabled.                                                      | Warning            |

[Category:Documentation
English](Category:Documentation_English "wikilink")