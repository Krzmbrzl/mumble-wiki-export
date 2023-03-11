## Mumble Universal Binaries for Mac OS X 

Since the 1.2.3 release of Mumble, the default packaging for Mac OS X only includes 64-bit Intel (X86-64) binaries for Mumble and Murmur.
The reason behind this move was that the majority Macs sold since the switch to Intel processors (that is, except the first generation of the
various Mac families and the Mac Mini) have X86-64 support.

Universal binaries that are built to run on 32-bit Intel (i386) and PowerPC (ppc) are still provided, but don't include all extra "nice-to-have" features
such as the overlay.


## Requirements 

* Mac OS X 10.4 or greater
* 32-bit Intel or 32-bit PowerPC CPU


If you find that they do not work for you given the above requirements, *please* file a bug on the  [tracker](https://sourceforge.net/tracker/?group_id=147372&atid=768005 bug) or talk to us on  [IRC](irc://irc.freenode.org/mumble).


## Downloads 

The latest universal binary release of Mumble is 1.2.3:

http://mumble.info/snapshot/Mumble-Universal-1.2.3.dmg

Snapshots are also regularly made available, though perhaps not as rapidly as the 64-bit versions are. They can be found in the snapshot folder of mumble.info:

http://mumble.info/snapshot/

All universal snapshots follow the naming scheme Mumble-Universal-Snapshot-VERSION.dmg, where VERSION is an internal description of the version of the snapshot.
(It is the output of 'git describe' at build-time.)



