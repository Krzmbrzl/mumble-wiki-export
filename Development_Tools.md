Since we get asked a lot, here's the tools we use for software
development:

# Backtrace

![Backtrace_Logo.png](Backtrace_Logo.png "Backtrace_Logo.png")

We have recently started to use Backtrace to analyse crash reports from
Mumble clients. Backtrace was easy to integrate into our existing
[minidump](https://docs.microsoft.com/en-us/windows/desktop/debug/minidump-files)
based reporting infrastructure and gives us a much clearer view on what
crashes affect the most users compared to what we had before. Backtrace
is graciously providing their service to us and other [Open Source
projects for
free](https://help.backtrace.io/pricing-data-protection-privacy-and-terms/pricing-and-tiers/backtrace-for-open-source).

# Ermine

![url=<http://www.magicermine.com/>](Ermine-logo.png
"url=http://www.magicermine.com/")

The static binary distribution of Murmur was made portable to different
Linux distributions with Magic Ermine.

# Ice

![url=<http://www.zeroc.com/>](Zeroc-logo.png
"url=http://www.zeroc.com/")

The Mumble server software uses ZeroC [Ice](Ice "wikilink") as a RPC
framework, enabling flexible remote control.

# Opus

![url=<http://opus-codec.org/>](opus-logo.png
"url=http://opus-codec.org/")

As of Version [1.2.4](1.2.4 "wikilink") [Mumble](Mumble "wikilink") uses
[Opus](http://www.opus-codec.org/) as the primary audio codec.

# Speex

![url=<http://www.speex.org/>](speex-logo.png
"url=http://www.speex.org/")

We are using the Speex DSP library for echo cancellation and denoising.

# Klocwork

![url=<http://www.klocwork.com/>](Klocwork-logo.png
"url=http://www.klocwork.com/")

Mumble has been analyzed with Klocwork source code analysis, the most
accurate and comprehensive tool for finding critical programming errors
and security vulnerabilities.

I must say I really love Klocwork. For opensource applications, they'll
do the analysis for free (providing you're the main author). It's found
some really obscure bugs in Mumble and Murmur, bugs that would have
caused crashes had they not been fixed before release. While my QA
department (aka: My guild who is running the test builds) will find all
bugs from normal use, Klocwork finds bugs that occur only under
circumstances no sane user would ever attempt. It also ensures server
and client input is sanitized, as it easily catches all those "what if
that value is really invalid" instances.

# Visual Studio 2008

It's a necessity for compiling programs on Windows using modern
interfaces such as WASAPI. We only use the compilers though; editing is
still done in Textpad.

# Qt

Mumble uses Qt, the Cross-Platform Rich Client Development Framework. Qt
is used for cross-platform GUI, network and database functions.
[Qt](http://qt-project.org/) is both a widget toolkit and a set of very
handy utility templates like container classes, network handling. It's
all crossplatform, meaning that Murmur runs on pretty much any modern
architecture, including the qmake files. I have a few projects that
doesn't use Qt at all, but uses Qmake :)

# Valgrind

"[Valgrind](http://valgrind.org/) is an award-winning suite of tools for
debugging and profiling Linux programs." We use this to make sure the
server has no memory leaks.

# Intel VTune

VTune is Intel's performance analyzer, which through a convoluted
process gives more or less accurate benchmarking results. While valgrind
will tell you exactly how many times each instruction is executed, it
can't tell you how long it takes to execute that instruction. Hopefully
someday VTune's output will be as detailed and easy to use as valgrind's
kcachegrind.

# MSDN

[MSDN](http://msdn.microsoft.com/) is Microsoft's developer website, and
contains an updated decription for each and every function available on
windows. I find the website easier to use than the MSDN helpfiles, as
the website has all the files searchable as one, instead of having one
file for the DirectX SDK, one for the Platform and so on.

# SourceForge

[SourceForge](http://www.sourceforge.net/) is not only a website, it's a
very handy tool. It comes with Git, which we use extensively, as well as
forums, wikis and mailing lists. In the past, we used it for all of this
- but since have partly migrated away. Nowadays, it’s used mainly for
file hosting.

# NSIS

[Nullsoft Scriptable Install System](http://nsis.sourceforge.net/) is
the installer made famous by WinAmp. It's an easy-to-use, efficient and
userfriendly install system; it took us less than 15 minutes to make the
first installer for Mumble.

*Note:* Since 1.2.3, we no longer use NSIS for our windows installers.

[Category:Development](Category:Development "wikilink")