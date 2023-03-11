The Mumble client uses two different locations for its data:

  - A database which contains the serverlist, server certificates,
    favorites, friends, access tokens, comments, etc.
  - Settings storage for the configuration

Here is a list of these locations for different operating systems.

## Windows

|          |                                                                            |
| -------- | -------------------------------------------------------------------------- |
| Database | `%APPDATA%\Mumble\mumble.sqlite`                                           |
| Settings | In the Windows registry (Path: `HKEY_CURRENT_USER\Software\Mumble\Mumble`) |

## Mac OS X

|          |                                                                  |
| -------- | ---------------------------------------------------------------- |
| Database | `$HOME/Library/Application Support/Mumble/Mumble/.mumble.sqlite` |
| Settings | `$HOME/Library/Preferences/net.sourceforge.mumble.Mumble.plist`  |

## Linux

|                       |                                                        |
| --------------------- | ------------------------------------------------------ |
| Database              | `$HOME/.local/share/data/Mumble/Mumble/.mumble.sqlite` |
| Database version 1.3+ | `$HOME/.local/share/Mumble/Mumble/mumble.sqlite`       |
| Settings              | `$HOME/.config/Mumble/Mumble.conf`                     |

[Category:Documentation
English](Category:Documentation_English "wikilink") [Category:Mumble
Client](Category:Mumble_Client "wikilink")