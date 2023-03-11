# murmur-manager

murmur-manager is a set of Ruby classes for managing Murmur servers. It
comes packaged with a handy dandy command-line script, so you can easily
manage your servers.

## Getting It

1\. Clone the Github repo

` git clone `<http://github.com/cheald/murmur-manager/>

2\. Make sure you have Ice set up for your Ruby install

` $ irb`
` irb(main):001:0> require 'Ice'`
` => true`

If this doesn't succeed, you need to [set up Ice and/or Ice Ruby
bindings](Ice "wikilink").

## Commands

You can get help at any time by just running the script with no
arguments.

` Usage: manager.rb [opts]`
` Args                                    Effect`
` ----                                    ------`
` [server-id] config                      List a server's config`
` [server-id] set [key] [val]             Set a server's config value`
` [server-id] start                       Start a server`
` [server-id] stop                        Stop a server`
` [server-id] destroy                     Permanently destroy a server`
` [server-id] supw [password]             Set superuser password for this server`
` new                                     Create a new server`
` list                                    List existing servers`

## List all your current servers

` [chris@polaris manager]$ ./manage-ice.rb list`
` Server ID       Running`
` ---------       ------`
` 1               true`
` 2               true`
` 3               true`
` 4               true`
` 5               true`
` 8               false`
` 12              false`
` 13              true`
` 14              true`

## Get a server's configuration

` [chris@polaris manager]$ ./manage-ice.rb 1`
` allowhtml                               true`
` obfuscate                               false`
` registerhostname`
` certificate                             -----BEGIN CERTIFICATE-----`
` port                                    50001`
` registerurl`
` timeout                                 30`
` defaultchannel                          0`
` textmessagelength                       5000`
` username                                [-=\w`\[\]`\{\}`\(\)`\@\|\.]+`
` welcometext                             Welcome to my Mumble server`
` bonjour                                 true`
` certrequired                            false`
` channelname                             [ \-=\w\#`\[\]`\{\}`\(\)`\@\|]+`
` registername`
` bandwidth                               72000`
` host                                    0:0:0:0:0:0:0:0`
` registerpassword`
` users                                   150`
` key                                     -----BEGIN RSA PRIVATE KEY-----`
` password`

## Update a configuration option

` ./manage-ice.rb 1 set port users 175`

## Spawning a new virtual server

` [chris@polaris manager]$ ./manage-ice.rb new`
` New server: ID 17 added`
` [chris@polaris manager]$ ./manage-ice.rb 17 set port 64049`
` [chris@polaris manager]$ ./manage-ice.rb 17 restart`

You get the idea. Not too hard\!

[Category:3rd Party](Category:3rd_Party "wikilink")