__TOC__

# Debugging Mumble & Murmur

If you have a problem with Mumble and wish to help the developers in
fixing it, it usually helps to give Mumble developers a debug log of
exactly what Mumble is doing when it crashes.

Note that the methods presented here only help with debugging crashes or
freezes, they do not help for debugging UI glitches, sound artifacts or
network problems.

## Submitting a Debug Log

The fastest way to submit a bug report is to hop on
[IRC](irc://irc.freenode.org/mumble). Put your bug report in a pastebin,
and put the link to the pastebin along with your Mumble version, OS, OS
version, sound card etc in the channel. Then sit back and wait. Sooner
or later, a developer will look through the bug, and ask followup
questions.

If you can't sit around on IRC all day, [submit a bug
report](https://github.com/mumble-voip/mumble/issues/new), including
your debug log.

Remember that along with submitting the log, you need to clearly
describe the method of reproducing the bug. Example: "If the
Server|Information tab originally shows Maximum 180 kbit/s, Current 120
kbit/s, and I then go into settings and set audio bitrate to 8kbit/s,
the Server|Information still shows 180 and 120 kbit/s."

## Windows: WinDbg

First, make sure that the bug still occurs in the last released
snapshot. Doing a debug report is a bit of work, and it would all be
wasted if the bug has already been fixed.

### Downloading WinDbg

Download the [Debugging Tools for
Windows](http://msdn.microsoft.com/en-US/windows/hardware/gg454513)
which includes WinDbg. (It is not available as a stand-alone.)

### Running Windbg

Run WinDbg x86. Even if you may have a 64-bit processor and OS, Mumble
is a 32-bit application, so the 32-bit debugger works much better.

Once WinDbg is open, press Ctrl+E and in the window that pops up
navigate to "mumble.exe", click it, then click "Open". If you have
problems attaching to mumble you may need to run WinDbg as
administrator.

Mumble should now start to load. Whenever you see a line containing "int
3" just keep pressing F5 until Mumble completely starts and is
functional (providing that it actually starts without crashing).

For extra info you can use the online debugging symbols for mumble.
Press Ctrl+S and add
`"srv**https://dl.mumble.info/symbols/;srv**http://msdl.microsoft.com/download/symbols"`
(without quotes) to the text box.

At this point, wait for Mumble to hang or crash. If it's a hang, use
"Break" from the "Debug" menu of Windbg. Note that breaking Mumble will
probably freeze your mouse and keyboard for a few seconds, as this also
pauses Mumble's hotkey handling.

In the log window, write

`~* kp `

or

`!uniqstack`

Then, from the "Edit" menu, choose "Copy Window Text to Clipboard". You
now have the debug log on the clipboard, proceed to submit your debug
log.

## Windows: DebugView

### Getting a Console Log

If you just need to read the output that would normally go to a console,
you can use [DebugView
(32bit)](http://technet.microsoft.com/en-us/sysinternals/bb896647.aspx).
Just run the executable and you will see output from Mumble and some
other applications.

### Enabling More Verbose Logging in the Overlay

If you want to get more output from the Windows overlay, put a file
called "*debugoverlay*" next to the .exe file for game you want debug.
The file must not have an extension, and can be empty, the overlay just
checks if it exists. You can then see some more messages in DebugView.

## Linux: Using gdb

If you compiled Mumble and Murmur yourself, recompile with symbols
enabled. To do this:

`qmake CONFIG+=symbols -recursive`
`make clean`
`make release`

Alternately, if you are on Ubuntu or Debian, just install the
*mumble-dbg* package.

This will give you a release build with debugging symbols. Note that
unlike *make debug*, which makes a debug build, this is still a fully
optimized binary, it's just a lot larger.

Start gdb with logged output

`script -c "gdb /path/to/mumble" mumble_debug.txt`

This starts gdb, but also copies all output to mumble_debug.txt

When the prompt comes up

`gdb> run`

Mumble will now proceed running as usual. If Mumble crashes, control
will return to gdb. If Mumble hangs, type "Ctrl-C" in the gdb window to
break it.

`gdb> thread apply all bt full`

At this point, simply quit gdb

`gdb> quit`

One you exit gdb, the file *mumble_debug.txt* will contain your debug
data.

[Category:Documentation
English](Category:Documentation_English "wikilink")
[Category:Development](Category:Development "wikilink")