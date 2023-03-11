To set up a channel viewer for Mumble, the officially supported method
is the [ZeroC Ice (Internet communication
engine)](http://www.zeroc.com/) interface. Using [Ice](Ice "wikilink")
requires a setup like this:

![Murmur_ICE_channel_viewer_diagram.png](Murmur_ICE_channel_viewer_diagram.png
"Murmur_ICE_channel_viewer_diagram.png")

The details of setting up and using the interface are documented on the
[Ice](Ice "wikilink") page. The interface provided by Murmur is
described in the [generated
documentation](http://mumble.sourceforge.net/slice/?title=slice). Server
information is provided in the [Channel Viewer
Protocol](Channel_Viewer_Protocol "wikilink") format as JSON or XML.

# Reading the Database Directly

  - First check to see if your server has the SQLite3 PHP library
    installed. You can do this by putting a *\<?php phpinfo();* in a php
    file and loading it on the server and searching for "SQLite3".
  - Get the "[Mod_murmur.php](http://www.fsxtools.de/j/downloadslink)"
    PHP script and if you are like most, you will want to setup a stand
    alone install and the instructions below are copied from
    [here](http://www.fsxtools.de/j/component/kunena/14-coding/11261-murmur-channel-viewer-installation-faq?Itemid=0#11261):

Then you only need the mod_murmur.php file (unzip the .zip). Edit it
and replace this manually (note the ending slashes\!):

`$whatpath = "http://path.to/unzippedimages/";<`
`$whatname = "MyServer";`
`$dbhost = "/path/to/murmur"; // This is the path where it will look for the murmur.sqlite db!`

  - Mod_murmur has been tested against v1.2.3 of Murmur

[Category:3rd Party](Category:3rd_Party "wikilink")