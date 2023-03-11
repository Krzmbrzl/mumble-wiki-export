To set up a channel viewer for Mumble, the officially supported method is the  [[[Ice]](http://www.zeroc.com/ ZeroC Ice (Internet communication engine)] interface. Using) requires a setup like this:

[[Image:Murmur_ICE_channel_viewer_diagram.png|none|thumb|300px|Communication method for Murmur]]

The details of setting up and using the interface are documented on the [[Ice]] page. The interface provided by Murmur is described in the  [documentation](http://mumble.sourceforge.net/slice/?title=slice generated). Server information is provided in the [[Channel Viewer Protocol]] format as JSON or XML.

= Reading the Database Directly =
{{Warning
|message=Interacting with the database for any reason but recovering from a corrupt database is ''highly discouraged!'' Doing so may lead to undesired results. In the best case (only reading from the file), you may get outdated or inconsistent data.
}}
{{Warning
|message=Do ''not'' make your database file accessible over the internet. It contains sensitive user information.
}}

* First check to see if your server has the SQLite3 PHP library installed.  You can do this by putting a ''<?php phpinfo();'' in a php file and loading it on the server and searching for "SQLite3".
* Get the " [Mod_murmur.php](http://www.fsxtools.de/j/downloadslink)" PHP script and if you are like most, you will want to setup a stand alone install and the instructions below are copied from  [here](http://www.fsxtools.de/j/component/kunena/14-coding/11261-murmur-channel-viewer-installation-faq?Itemid=0#11261):

Then you only need the mod_murmur.php file (unzip the .zip). Edit it and replace this manually (note the ending slashes!):

 $whatpath = "<nowiki>http://path.to/unzippedimages/</nowiki>";<
 $whatname = "MyServer";
 $dbhost = "/path/to/murmur"; // This is the path where it will look for the murmur.sqlite db!

* Mod_murmur has been tested against v1.2.3 of Murmur



