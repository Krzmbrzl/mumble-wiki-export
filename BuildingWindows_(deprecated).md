# Introduction

Mumble has quite a few dependencies for building on Windows, and as the
feature set grows, so does the list of dependencies. This page will try
to detail the steps required to set up a Win32 build environment
suitable for compiling the current code found in our repository. Be
aware that these steps might not work for older revisions of Mumble as
dependencies might have been removed or updated to an incompatible
version in the meantime. **Note that you must follow each step in order,
or you will have problems.**

The paths used here equal the defaults assumed in the Mumble build
files. You are free to change them, but you might need to [adjust the
build files](#Custom_Dependency_Paths "wikilink") themselves. If you
find any problems or incorrect steps in this article please either
correct them or contact us and we will try our best to resolve the
issue.

Also note, that if you are submitting a bug report for a self-built
executable, we expect you to either

  - Follow these instructions to the letter

or

  - Report any deviations from these instructions

Deviations means anything, from "I installed to the D: drive" to "I
changed the gcc build options for Qt" or "I used another version of
Speex".

**A note to those following this guide**: When you extract compressed
files, sometimes they will have container folders and sometimes they
will not. Please ensure (for example) that when you extract a compressed
file like protobuf-2.2.0.zip, you see "bin" "include" and such folders
as that directly inside of the folder named "protobuf-2.2.0". If you
just see one folder and no other files, then you need to open that
folder, and use the folder that is inside of it.

**Also remember that this guide may not be updated every single time a
build dependency gets updated. It's up to you to make sure that you have
the latest versions on the various dependencies; it would also be
appreciated if you would update this wiki to reflect any changes you run
into.**

# Software which you will need

Tools: [Visual Studio 2010
Express](http://go.microsoft.com/?linkid=9709949), [Git for
Windows](http://code.google.com/p/msysgit/downloads/list),
[ActivePerl](http://www.activestate.com/activeperl/downloads),
[NASM](http://www.nasm.us/)

Optional Tools:
[TortoiseGIT](http://code.google.com/p/tortoisegit/downloads/list),
[Notepad++](http://notepad-plus-plus.org/download/),
[7-Zip](http://7-zip.org/download.html)

Dependencies: [Protocol
Buffers](http://code.google.com/p/protobuf/downloads/list),
[Boost](http://www.boost.org/users/download/),
[OpenSSL](http://www.openssl.org/source/), [zlib](http://www.zlib.net/),
[libsndfile](http://www.mega-nerd.com/libsndfile/#Download), [Microsoft
Windows
SDK](http://www.microsoft.com/downloads/dlx/en-us/listdetailsview.aspx?FamilyID=6b6c21d2-2006-4afa-9702-529fa782d63b),
[Microsoft DirectX
SDK](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6812)

Optional:, [Bonjur (requires
account)](https://developer.apple.com/bonjour/),
[G15SDK](http://www.logitech.com/en-gb/support/3498?bit=64&crid=404&osid=14)
(included in the Gaming Software),
[MySQL](http://dev.mysql.com/downloads/mysql/), ([Visual Leak
Detector](http://sites.google.com/site/dmoulding/vld)), [ZeroC
Ice](http://www.zeroc.com/download.html) , [ASIO SDK (requires
Account)](http://www.steinberg.net/nc/en/company/developer/sdk_download_portal.html)

**Dependency-Tree:**

`Mumble <- boost`
`       <- protobuf`
`       <- openssl   <- zlib`
`                    <- perl`
`       <- libsndfile`

`       // optional:`
`       <- ice`
`       <- (vld)`
`       <- bonjour`
`       <- asio`
`       <- g15sdk`
`       <- mysql`

# Preparations

## Tools Used in Compiling

### Visual Studio

You'll need Visual Studio 2010 (or Visual C++ Express Edition) with SP1
or later.

Visual Studio 2010 trials:
<http://www.microsoft.com/visualstudio/en-us/try>

Visual C++ 2010 Express Edition:
<http://www.microsoft.com/visualstudio/en-us/products/2010-editions/visual-cpp-express>

### Git

Download the most recent Git from
<http://code.google.com/p/msysgit/downloads/list> and install it. Make
sure you select "Run Git from the Windows Command Prompt."

**After you install Git, start a command prompt and run**

`git config --global core.autocrlf true`

### TortoiseGit

[TortoiseGit](http://code.google.com/p/tortoisegit/downloads/list) is a
GUI frontend for Git. You can install this along with the one above for
realtime information about changes to the Git code.

### ActivePerl and NASM

Download and install ActivePerl from here:
<http://www.activestate.com/activeperl/>
Download and install NASM from here: <http://www.nasm.us/>

### 7-Zip and Notepad++

Get 7-Zip [here](http://7-zip.org/). After you install it, start the
7-Zip File Manager, go to Tools -\> Options, and select the file
associations you want. We recommend selecting .zip and .7z file
extensions.

[Notepad++](http://notepad-plus-plus.org/download/). After you install
Notepad++, start it, go to Preferences -\> New Document/Default
Directory, and check "Unix" in the Format box.

## Libraries and Depedencies

### Bonjour

Download the Bonjour SDK from [Apple
site](http://developer.apple.com/opensource/) *(Apple account is
required)* and install it to its default install location.

### G15SDK

Download the G15 software from here:
[http://www.logitech.com/en-us/434/3498?section=downloads\&WT.ac=sc|downloads](http://www.logitech.com/en-us/434/3498?section=downloads&WT.ac=sc%7Cdownloads)||dd
and install it.

Now go to *C:\\Program Files\\Logitech Gaming Software\\LCDSDK* and
extract "LCDSDK_3.06.109.zip". Take the folder that has been extracted
and rename it to *G15SDK*. Put this folder into *c:\\dev*.

### libsndfile

Download the **32-bit** Windows installer from
<http://www.mega-nerd.com/libsndfile/#Download> and install it to its
default install location.

### Microsoft Windows SDK

At the time of writing this, the latest version is the "Microsoft
Windows SDK for Windows 7 and .NET Framework 4". Download it from
<http://msdn.microsoft.com/en-us/windows/bb980924.aspx> .

Install it to a location of your choice. The “Documentation” and
“Samples” in the SDK are not required for Mumble and can be left out
to speed up the installation.

After installing the Windows SDK you must make sure Visual Studio uses
it. Start the WindowsSdkVer.exe utility in the SDK's setup folder and
change the used version to 7.X. If you get an error that says you don't
have VS2005 or VS2008 installed see [on how to fix
it](http://blogs.msdn.com/b/windowssdk/archive/2009/08/21/windows-sdk-configuration-tool-may-report-an-error-when-os-display-format-is-not-english.aspx).

### Microsoft DirectX SDK

Download the DirectX SDK from
<http://www.microsoft.com/en-us/download/details.aspx?id=6812>. Install
it to the default location.

### MySQL

Download the latest release of MySQL Server (x86, 32-bit). It can be
found here: <http://dev.mysql.com/downloads/mysql/> (select "Without
installer (unzip in C:\\)"). Unzip it to *c:\\dev\\MySQL*.

### Protocol Buffers

  - Download [Protocol Buffers from
    Google](http://code.google.com/p/protobuf/) (*protobuf-x.y.z.zip*)
  - unpack it to *c:\\dev\\protobuf-x.y.z*.

<!-- end list -->

  - Open protobuf-x.y.z\\vsprojects\\protobuf.sln
  - Find a dropdown box at the top right of VS2010 that says "Debug" on
    it. Change that to "Release"
  - Right click the "Solution 'protobuf' (9 projects)" at the top left
    of VS2010 and select "Batch Build..." Click "Select All," then click
    "Build".

Now run the file
*C:\\dev\\protobuf-x.y.z\\vsprojects\\extract_includes.bat*.

### Visual Leak Detector (optional)

[Download](http://dmoulding.googlepages.com/vld) VLD and install it to
its default install location.

If you're using Visual C++ Express Edition, you will need to manually
extract the files using a tool like [7-zip](http://7-zip.org/). Extract
it to *C:\\dev\\* and adjust [the
VLD_PATH](BuildingWindows#Custom_Dependency_Paths "wikilink") to point
to it.

### ZeroC Ice

Download Ice version 3.4.2 of ZeroC Ice from
<http://www.zeroc.com/download.html>. Install to the default install
location.

# Create Prep

Create *C:\\dev*, and inside that directory create a file *prep.cmd*
containing:

`@echo off`
`SET DIR=c:\dev`
`SET VSVER=10.0`
`SET LIB=`
`SET QT_DIR=%DIR%\QtMumble`
`SET MUMBLE_DIR=%DIR%\mumble`
`SET VLD_DIR=%DIR%\vld`
`SET MYSQL_DIR=%DIR%\mysql`
`SET NASM_DIR=%DIR%\nasm`
`SET ICE_DIR=%DIR%\Ice`

`IF DEFINED %PROGRAMFILES(X86)% (`
`  GOTO amd64`
`) ELSE (`
`  GOTO x86`
`)`

`:amd64`
`SET PROGPATH=%PROGRAMFILES(X86)%`
`GOTO Common`

`:x86`
`SET PROGPATH=%PROGRAMFILES%`
`GOTO Common`

`:Common`
`CALL "%PROGPATH%\Microsoft Visual Studio %VSVER%\VC\vcvarsall.bat" x86`
`CALL "%DXSDK_DIR%\Utilities\bin\dx_setenv.cmd" x86`
`SET PATH=%QT_DIR%\bin;%DIR%\OpenSSL\bin;%PROGPATH%\Mega-Nerd\libsndfile\bin;%MYSQL_DIR%\lib;%ICE_DIR%\bin\vc100;%DIR%\protobuf-2.4.0a\vsprojects\Release;%NASM_DIR%;%VLD_DIR%\bin;%PATH%`
`TITLE Mumble Development Environment`

`if "%1"=="" (`
`  cmd /V:ON`
`  exit /b`
`)`

Now create a shortcut to *C:\\Windows\\System32\\cmd.exe /K
"..\\prep.cmd"* on your desktop. Edit its properties to make it Start in
*C:\\dev\\mumble*.

Alternatively, you can use the advanced script
[BuildingWindows/mde.cmd](BuildingWindows/mde.cmd "wikilink")
([download](http://luki.net.pl/dl/mumble/mde.cmd)) which allows you to
set it up in its head (vs-ver and paths of your environment), and
additionally to preparing your environment provides some git and
building commands.

# Custom Dependency Paths

The build files were modified to support custom dependency paths a while
ago. This is for the people who have **the dependencies installed in
some other place than the C:\\dev directory structure**. To specify the
custom paths you need to **create a *winpaths_custom.pri* file** to the
root of your Mumble project. In this file you can override all paths
found in *winpaths_default.pri*. For example:

` OPENSSL_PATH = /dev/MyOpenSSLIsSomewhereElse`
` ICE_PATH = C:\\Program Files (x86)\\ZeroC\\Ice-3.4.1`

Would make the build process search its OpenSSL and Ice dependencies in
the specified folders and use defaults for everything else. Note that
you should only override the variables for dependencies you actually
installed in non-default locations to prevent clashes with possible
future updates.

**Note:** If you copied *winpaths_default.pri* to create your
*winpaths_custom.pri* make sure to delete the following lines from your
*winpaths_custom.pri* file:

`# Include custom file if it exists`
`exists(winpaths_custom.pri) {`
`   include(winpaths_custom.pri)`
`}`

# Commandline Instructions

Whenever something appears

`like this`

you're supposed to enter it in that command shell (or copy it from this
webpage and right click in the command window and select *Paste*).

Note that *each line* is a separate command. So, if you wanted to do the
following,

`cd mumble`
`prep`

you would type "cd mumble" in your command prompt, and press enter, and
then you would type "prep", and press enter.

Ok. So you're ready to start compiling.

Start a new command shell (run *cmd.exe*)

`cd \dev`
`prep`

After you run prep make sure a message similar to "Setting environment
for using Microsoft Visual Studio 2010 x86 tools" appears.

***When you later want to compile a dependency or program, always
remember to call prep.bat first to set paths correctly.***

# Compile Mumble Dependencies

### Boost

Download the most recent Windows version of the [Boost C++
libraries](http://www.boost.org/) and unzip it to *c:\\dev*

`cd \dev `
`prep`
`cd boost_*`
`bootstrap.bat`
`b2 --toolset=msvc-10.0 --prefix=C:\dev\Boost install`

This might take a while (like hour), but when done you'll have Boost
installed.

### OpenSSL

Download [zlib](http://www.zlib.net/) source and unpack it to *C:\\dev*
and rename the *zlib-x.y.z* folder to *zlib*

[Download the OpenSSL source](http://www.openssl.org/source/) named
"openssl-1.0.0d.tar.gz" and unpack it to *c:\\dev* (it will create a
directory called openssl-x.y.z)

`cd c:\dev\openssl`<press tab>
`perl Configure VC-WIN32 --prefix=c:\dev\OpenSSL zlib-dynamic --with-zlib-include=c:\\dev\\zlib`
`ms\do_nasm`
`nmake -f ms\ntdll.mak`
`nmake -f ms\ntdll.mak test`

Make sure all the tests passed, then run:

`nmake -f ms\ntdll.mak install`

### Qt

Checkout the Mumble Qt git repo to `C:\dev\QtMumble`:

`cd c:\dev`
`git clone `<git://gitorious.org/+mumble-developers/qt/mumble-developers-qt.git>` QtMumble`

Switch to the *4.8-mumble* branch:

`cd QtMumble`
`git checkout --track -b 4.8-mumble origin/4.8-mumble`

Now for compilation configuration and compilation itself execute

`configure -debug-and-release -qt-sql-sqlite -qt-sql-mysql -no-qt3support -no-exceptions -qt-zlib -qt-libpng -qt-libjpeg -openssl -I c:\dev\OpenSSL\include -L c:\dev\OpenSSL\lib -I c:\dev\MySQL\include -L c:\dev\MySQL\lib -platform win32-msvc2010 -no-dbus -nomake demos -nomake examples -no-webkit -ltcg -mp`
`nmake`

# Download, Compile and Run Mumble

### Download Mumble and Submodules

To clone the repositories you must open [Mumble Development
Environment](#Create_Prep "wikilink") console and type:

`git clone `<git://github.com/mumble-voip/mumble.git>` mumble && cd mumble && git submodule init && git submodule update`

### Compile Mumble and Murmur

Once all of the above is done we can get to compiling Mumble itself.

If you want to have ASIO support you have to install an additional,
proprietary, ASIO SDK.

There are three dependencies that most people who make their own
compiles will not need:

1.  g15
2.  asio
3.  bonjour

The bonjour dependency is useful if you want to browse servers across a
local network, but you can disable it if this feature is not needed.

To compile Mumble without ASIO, G15, Bonjour, and with disabled
privilege elevation (would require a valid code signing certificate)
replace the qmake command below with this one:

`qmake CONFIG-=sse2 CONFIG+=no-asio CONFIG+=no-g15 CONFIG+=no-bonjour CONFIG+=no-elevation -recursive`

If you get errors about qt_\*.ts files, then go to
*C:\\dev\\QtMumble\\translations* and copy and rename any qt_\*.qm's to
qt_\*.ts.

To compile Mumble:

`cd c:\dev\mumble`
`..\prep`
`qmake`
`nmake clean`
`nmake`

Note that this builds the debug versions, which is what we strongly
recommend to use while developing. If you want to send the binary to
someone else, use

`nmake release`

instead of the last *nmake* command listed above. This will result in a
much smaller binary with fewer dependencies.

### Run Mumble and Murmur

Once compiled, you can go into *c:\\dev\\mumble\\release* or (*\\debug*
if you compiled the debug version) and can execute mumble.exe or
murmur.exe. Before executing Mumble or Murmur you need to open a command
prompt and do

`cd \dev`
`prep`
`cd mumble\debug (or release)`

Then execute either Mumble or Murmur *from the command prompt* with

`mumble.exe`

or

`murmur.exe`

If you want to run the release build directly from Windows Explorer, you
will need to collect all the library files into one folder, along with
the executables you built when you compiled Mumble. Have a look at the
files the official Mumble installer creates in *Program Files\\Mumble*.

# Build a Mumble installer package

If you want to create an installable .msi package from your
self-compiled Mumble some additional steps are needed.

Download and install the latest WIX stable Version (currently 3.8) from
[here](http://wixtoolset.org/releases/).

Set the following environment variables as needed (see defaults in
installer/Settings.wxi):

` MumbleSourceDir  default: \dev\mumble`
` MumbleQtDir  default: \dev\QtMumble`
` MumbleDebugToolsDir  default: C:\Program Files (x86)\Debugging Tools for Windows (x86)`
` MumbleSndFileDir  default: \Program Files (x86)\Mega-Nerd\libsndfile\bin`
`   Define MumbleNoSndFile to exclude  libsndfile`
` MumbleMySQLDir  default: \dev\MySQL`
`   Define MumbleNoMySQL to exclude  MySQL`
` MumbleIceDir  default: \Program Files (x86)\ZeroC\Ice-3.4.2\bin\vc100`
`   Define MumbleNoIce to exclude Ice`
` MumbleOpenSslDir  default: \dev\openssl`
` MumbleZlibDir  default: \dev\zlib`
` MumbleMergeModuleDir  default: C:\Program Files (x86)\Common Files\Merge Modules`
` Define MumbleSSE to include SSE`
` Define MumbleNoSSE2 to exclude SSE2`
` Define MumbleNoG15 to exclude G15`

Open installer/MumbleInstall.sln, switch to release and build the
installer.

Once this completed successfully run the *build_installer.pl* script to
include all translations into your installer.

You should now have a working .msi installer.

# Static Build

Since [1.2.5](1.2.5 "wikilink") we are distributing Mumble as a static
build where the main Mumble app logic is provided in a DLL rather than
the exe.

The static environment and builds should not be necessary for normal
development and playing around.

## Scripted Build

For our static build scripts see [mumble-releng (Release Engineering)
buildenv/win32-static](https://github.com/mumble-voip/mumble-releng/tree/master/buildenv/win32-static).

In contrary to the environment setup in the above section(s) releng will
use its own build environment in your home directory. For the build you
can follow the README. If you have cygwin installed it should be a
matter of starting a mumble buildenv cygwin console and running
`./build-all.bash`. Dependencies will be downloaded an compiled - this
will take quite some time (especially Qt compilation).

## Manual Build

This section describes the necessary flags and steps - be aware though
that our releng scripts will apply source patches on the fly when
compiling, which you will have to apply yourself. **With the below
instructions alone your build will not succeed yet.**

The **Qt** library (dependency) will have to be built with the
\*static\* flag. Pass \`static\` to the \`configure\` call before
building Qt.

To build **Mumble** statically add the `static` config property to the
call to `qmake`.

`CONFIG+=static`

[Category:Development](Category:Development "wikilink")