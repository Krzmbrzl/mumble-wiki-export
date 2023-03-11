To migrate a [Mumble-Server](Murmur "wikilink") the following files are
needed (on Debian in this example):

  - Database: /var/lib/mumble-server/mumble-server.sqlite
  - [Configuration file](Murmur.ini "wikilink"): /etc/mumble-server.ini
  - Certificate related files: Check the following entries in your
    mumble-server.ini file and save those files:
      - [sslca](Murmur.ini#sslCA "wikilink")
      - [sslcert](Murmur.ini#sslcert "wikilink")
      - [sslkey](Murmur.ini#sslcert "wikilink")

[Category:Documentation
English](Category:Documentation_English "wikilink") [Category:Mumble
Server](Category:Mumble_Server "wikilink")