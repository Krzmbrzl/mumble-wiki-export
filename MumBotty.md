# MumBotty

MumBotty is a bot that sits in the \#mumble and \#mumble.de IRC channels
and features a couple of commands concerning the Mumble infrastructure.
Note that recently, it has been renamed to K-10.

## Wiki

MumBotty allows searching for Wiki entries by using the \`\`w\`\` or
\`\`wiki\`\` commands:

<Svedrin>` help w`
<MumBotty>` (w [@`<nickname>`] `<search string>` [...]) -- Returns a list of wiki page`
`titles that contain `<search string>`. If the search string is prefixed with @`<nickname>`,`
`the plugin will highlight the given nickname instead of the user of the command.`

Running this command with the keyword "Building" will yield the
following results:

<Svedrin>` !w Building`
<MumBotty>` `<http://mumble.sf.net/BuildingFreeBSD>` -- BuildingFreeBSD`
<MumBotty>` `<http://mumble.sf.net/BuildingLinux>`   -- BuildingLinux  `
<MumBotty>` `<http://mumble.sf.net/BuildingMacOSX>`  -- BuildingMacOSX `
<MumBotty>` `<http://mumble.sf.net/BuildingWindows>` -- BuildingWindows`

## Ice method introspection

MumBotty can introspect Ice methods through the \`\`i\`\` or \`\`ice\`\`
commands:

<Svedrin>` !help ice`
<MumBotty>` (ice [@`<nickname>`] [`<object>` [`<method>`]]) -- Introspect the given object and/or method.`

Running this command for Server::getTree, you would get:

<Svedrin>` !ice Server getTree`
<MumBotty>` Server::getTree() - see `<http://mumble.sourceforge.net/slice/Murmur/Server.html#getTree>

If you don't specify any arguments at all, you will receive a list of
objects. If you only specify an object, you will receive a list of
methods this object provides.

## FAQ Search

You can use MumBotty to search and display FAQ entries by using the
\`\`f\`\` or \`\`faq\`\` commands:

<Svedrin>` !f qwave`
<MumBotty>` Svedrin: Q: I get the error "Meta: Failed to load qWave.dll, no QoS available" in the Murmur log when I start Murmur`
<MumBotty>` Svedrin: A: qWave is network QoS for Vista. You don't have qWave, so it's proceeding without it. You can disregard this message if you are NOT on Vista/Server 2008. If you are, you should try to stop the error.`

The result will only be displayed if MumBotty found exactly one FAQ
Question that matched. Otherwise you will get error messages like these:

`* MumBotty didn't see any questions that looked promising.`
`* MumBotty found 8 questions that match your query.`

Note that this is not a fulltext search. If you specify more than one
keyword, they will be matched as a sentence.

## Announcements

MumBotty will announce a set of events, most notably:

  - Commits
  - Updates to forum threads
  - Updates to tracker artifacts
  - The wiki change history

# Command syntax

There are multiple possible ways of addressing the bot:

  - For messages only useful to yourself, you should /query it and talk
    to it in private to prevent spamming the channel. It will accept the
    same commands which you can use in the channel.
  - To use it from within a channel, prefix your messages with an \! to
    directly address the bot.
  - You can also use inline commands by using the ,, prefix:
      - Commands consisting of a single word -- like ,,uptime -- can be
        used without any special syntax.
      - In order to use multi-word commands, you need to enclose the
        command in parentheses, for example if you wanted to see the
        ,,(wiki building) page.

The bot will always respond to messages in the way you contacted it to
begin with.

# Owner

This bot is being run by Svedrin.

# Source code, Wishlist, Bugs

The source code for all the mumble specific plugins can be found at
[BitBucket](https://bitbucket.org/Svedrin/k10-plugins). If MumBotty
doesn't behave and even slapping it around a bit won't help, please
submit an issue at [the issue
tracker](https://bitbucket.org/Svedrin/k10-plugins/issues?status=new&status=open).

[Category:Documentation
English](Category:Documentation_English "wikilink") [Category:3rd
Party](Category:3rd_Party "wikilink")