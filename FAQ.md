# Languages|FAQ


= About Mumble =
## What is Mumble? 
Mumble is a voice chat application for groups. While it can be used for any kind of activity, it is primarily intended for gaming. It can be compared to programs like Ventrilo or TeamSpeak.
People tend to simplify things, so when they talk about Mumble they either talk about "Mumble" the client application or about "Mumble & Murmur" the whole voice chat application suite.

## What is Murmur? 
"[[Murmur]]", also called "Mumble-Server", is the name of the server application. In any case, if anyone talks about Murmur it is for sure the server part.

## What platforms does it run on? 
The client, Mumble, runs on Windows, Mac OS X and Linux.

There is also a client for iOS, named [[Mumble for iOS]] and an unofficial Android client named [[Mumla]].

The server component, [[Murmur]], should run on anything you can compile Qt 4 on.

## What are the system requirements? 
The client runs on any Windows, Linux or Mac OS X machine. You also need a microphone. The server is mostly bandwidth bound, so as long as your network hardware is sufficient it should run on pretty much anything.

Please note that the Windows binaries distributed from SourceForge are compiled for SSE (Pentium 3 or Athlon-XP). Mumble is a VoIP solution for gaming, and as most modern games require at least that good a CPU it makes little sense for us not to optimize for it.

## Can I use Mumble to connect to Ventrilo/Teamspeak/Skype/... 
No. Mumble only supports its own [protocol](Protocol.md) which has been specifically designed to give you the best user experience.

If you need to use Ventrilo on Linux take a look at  [Mangler](http://www.mangler.org/).

## Installing Mumble 

Please see the entire page devoted to [[installing Mumble]].

## Compiling Mumble 

We currently maintain pages with instructions on building Mumble from source on [Linux](BuildingLinux.md), [Windows](BuildingWindows.md), [MacOS X](BuildingMacOSX.md), and [FreeBSD](BuildingFreeBSD.md).

## What makes Mumble better? 

Mumble has very low latency combined with good sound quality; it uses  [OPUS](http://opus-codec.org/),  [CELT](http://www.celt-codec.org/) and  [Speex](http://www.speex.org/), not just the voice compression technology, but also the voice pre-processing to remove noise and improve clarity. Mumble also has [positional audio](Positional-Audio.md) for [supported games](Games.md), meaning the other players' voice will come from the direction their character is in game.

## What are the bandwidth requirements? 
From 0.9.1, this is highly variable, and mostly up to the user. With top quality, minimum latency and positional information sent, it is 144.0 kbit/s including the IP and UDP overhead. With 60 ms transmission delay, the lowest quality speech and no positional information, it is 15.8 kbit/s (again with IP and UDP overhead). The default quality setting uses 58.8 kbit/s. When comparing with other products, remember to compare the total bandwidth use and not just the bitrate of the audio encoding.

There are two parts to tuning the bandwidth; the audio bitrate per audio frame (e.g. 10ms) and the amount of frames to put in each packet. Each transmitted packet has an overhead of 28 bytes from IP and UDP alone, so at the highest transmission rate (100 packets per second), that is 2800 bytes of data for raw network overhead alone. You should try to find a balance that works well for you, but we generally recommend sacrificing high audio bitrate for lower latency; Mumble sounds quite good even on the lowest quality setting.

There is no way to adjust the amount of incoming bandwidth; you will have to have enough to sustain the total amount of speaking players. This should be a minor issue; most players these days are on asymmetric lines and hence it is only upload that is a bottleneck.

## Is Mumble encrypted? 
Your whole communication to and from the server is always encrypted. This encryption is mandatory and cannot be disabled. The so-called control channel, which transports your chat messages and other non-time critical information, is encrypted with  [TLS](http://en.wikipedia.org/wiki/Transport_Layer_Security) using 256 bit  [AES](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)-SHA. The voice channel carrying speech and positional audio is encrypted with  [OCB-AES](http://www.cs.ucdavis.edu/~rogaway/ocb/) 128 bit. You and the server authenticate to each other using digital certificates like they are used for secured connections in Web-browsers.

## What tools did you use to make this? 

See [[Development Tools]].

## Do you sell mumble servers? Do you run mumble.com?  
No. We do not sell, rent or run any mumble servers. Neither do we run or own mumble.com.

If you do not want to run your own server you can take a look at [ this list of Hosters](Hosters.md) (note that we do not vouch for or vet any hosters on that list) for inspiration.

## How can I help or contact you? 
A good start would be just using Mumble. If you like it, tell all your friends. If you like it so much you want to donate see our [donation page]]. If you do not like it, tell us what is wrong so we can fix it. You can do so via the  [[[IRC]](http://forums.mumble.info/ forums] or meet us on) at irc://irc.freenode.org/mumble . If you have a bug or error that you need help with it also helps to read over [[Debugging](Donate.md) to learn how to give the developers the information needed to help fix the bug. If you want to get involved with the project yourself take a look at our [contribution page](Contributing.md) or directly talk to us.

= Audio Features = 

## How does the positional sound work? 

Your position in-game is transmitted along with every audio packet, and Mumble uses standard DirectSound 3D to position the audio on the receiver side. Only games which have been [adjusted](Link.md) to be used with mumble, or for which a plug-in has been written get positional audio. All other games will work as well, you just will not get 3D sound. You can find a list of supported games in the [Games article](Games#Positional_audio.md).

## Why does Mumble sound so much better than other voice products? 

One word: De-noising. This is a standard part of Speex 1.1 and above, and any voice product already implementing speex should be able to trivially include the same filtering. 
Removing the noise from the input means that the audio will be clearer and that the needed bitrate will decrease. It takes fewer bits to model clear voice than it does to accurately represent the noise, so in any noisy transmission a large share of the bits will be noise modelling.

## The text-to-speech quality is horrible! 

We use the standard MS Speech API, and the included voices are not all that good. If you have installed either MS Office or the Speech SDK, you will get more voices which can be configured from the Speech control panel. You can also buy a commercial Text-To-Speech engine; as long as it's SAPI5 compatible it can be used by Mumble. The main developers are currently using NeoSpeech Kate (buyable standalone from  [NextUp](http://www.nextup.com)).

## Why do some voices sound metallic/robotic? 

Mumble is optimized for low latency so when your connection has a lot of variance ping wise some audio packets will arrive too late for mumble to consider them. A bad connection might even lose packets completely. If that happens the codec tries to "cover up" the fact it misses data. Before version 1.2.1 our new codec CELT was not as good at this as Speex (the old codec) so make sure you use a recent version. Mumble also has a so-called "jitter buffer" that tries to counteract the ping variance issues but it is not perfect, we are currently collecting usage data to improve it.

You can usually reduce the artifacts by increasing buffer sizes, but a (ping wise) stable connection is the best solution. Be aware that the ping has to be stable from the sender to the server and back to the receiving end.

The issues mentioned before are the most common ones. Some people might hear metallic sounding voices even with a stable ping on both ends. This might be a result of noise filtering by Mumble. If the environment of the sender is especially noisy, some parts of the voice will be filtered as well. The alternative would be noisy sound, meaning precious bandwidth would be used to encode noise and the clarity of the voice would also decrease.

## With Mumble my microphone only picks up noise and static, voice is barely audible 
This can have many reasons. A few of them being bad hardware, bad electrical connections or a very electromagnetically noisy environment. Such hardware problems can only be solved by replacing the components at fault. In very many cases the problem is in, or is amplified by, software though.

One possibility is a too high or low input volume. To fix this simply redo the audio wizard and pay special attention to the "Volume tuning" page. You might have to enable/disable microphone boost and/or lower/raise the microphone volume in your operating system to get the input volume into the ideal range. Enabling the audio cards noise reduction, if available, also can be very effective.

In a lot of situations there is a less obvious cause. A bad driver. Updating the audio driver to the newest version available can fix bugs Mumble's low latency access to the audio hardware might trigger.

##I see I can use sound notifications, what formats are supported?

Mumble support many common formats like .ogg, .wav (uncompressed) or .flac. A complete list of supported formats can be found  [here](http://www.mega-nerd.com/libsndfile/#Features).

## Why doesn't the voice activity detect my voice any more? 

If you change your audio environment suddenly and drastically, by for example disconnecting and reconnecting your microphone or dragging a piece of paper directly over the microphone, you will throw the voice pre-processor off balance. It will recover, but it will take time. 

To reset the pre-processor, choose 'Reset' from the 'Audio' menu.

## What is this weird echo I hear of myself from other users? 

Unfortunately, a lot of popular headsets produce tiny traces of echo. In other VoIP products, you will not notice it because the echo is lower than the noise level, but as Mumble dutifully removes all noise, the echo suddenly becomes clear. There is little the person hearing the echo can do, but there are a few things the person producing the echo can do. On Vista, we support echo cancellation for any sound card. On Linux, we support echo cancellation when using PulseAudio, and on Windows XP we support echo cancellation using ASIO (which unfortunately requires a very high quality soundcard with ASIO drivers).

If you are really dealing with "remote echo"–make sure it's really someone else lighting up when you hear echo–, and the remote user is using a headset, the cause is likely crosstalk between the headphone and microphone cables. The headphones have a rather high signal level, while most computer headset microphones have very weak signals that get amplified a ''lot,'' so badly shielded cables will cause issues. Sometimes, it helps to plug the headset into the onboard audio connectors instead of connectors on the front of the case and possibly unplug the front panel cable from the mainboard.

## Can I change the volume of a specific user? 

Yes, since Version 1.3.0. The user context menu (right click) has a “Local Volume Adjustment…” action that opens a dialog where you can do so.

Mumble takes two approaches that should make the need to do so unnecessary. But sometimes it is still reasonable or necessary.

Mumble primarily intends a user-prepares-their-settings approach. The Audio Wizard helps end users in doing so with a guided setup, volume visualizations and description of the voice activation levels.

Mumble employs Automatic Gain Control (AGC) to normalize the volumes of all participants automatically. AGC is powerful but if there is not enough signal to begin with (e.g. Mic volume turned way down) it will not be able to operate correctly.

Still, users may not follow this approach or their configuration may change or break unnoticed. Hence you can adjust the volume for each user for yourself (locally) individually. This does not transfer to other users. It is a personal, local setting.

## Where is the Alt-Speak key in 1.2.x? 

Alt-Speak was replaced by the Whisper functionality. Add a whisper shortcut with the target "Current Channel" and check "Whisper to linked channels" to do what alt-speak did in 1.1.x.

= Server =

## How can I run Murmur as a service? 

https://sourceforge.net/tracker/index.php?func=detail&aid=2951513&group_id=147372&atid=768008

## What sort of bandwidth will I need for the server? 
Worst case scenario: Number of users &times; Number of talking users &times; 133,6 kbit/s. With less aggressive quality settings, it's ~60 kbit/s, and the bare minimum is 17.4kbit/s. Note that Mumble is geared towards social gaming; its quality enables people to talk naturally to each other instead of just barking short commands, so the amount of "users talking at the same time" can be somewhat higher than expected.

This means that a server with 20 players and 2 players talking at once requires 1-3 Mbit/s, depending on quality settings. In the server's [.ini](murmur.ini.md) file, you can specify the maximum allowed bitrate for users as well as the maximum number of clients to allow.

Additional information / community-provided examples can be found [on the Commercial Hosting page](Commercial_Hosting#Murmur_technical_requirements.md).

## Where do I configure the welcome message, listen port and so on? 
[[murmur.ini]], it is self-documenting.

murmur.ini is located in your Mumble Program Files folder on Windows, and in /etc/mumble-server.ini on Ubuntu.

## What is the default server port for Murmur? 

The default server port for Murmur is UDP and TCP 64738.

## Can I run multiple servers on one host? 

Yes, Murmur supports virtual servers. See [[Running_Murmur]]

## How do the ACLs work? 

See [[ACL and Groups]]

## Where is the administrator account? 

The topmost user in the Mumble hierarchy is the useraccount "SuperUser", which bypasses all permission checks and is always allowed to do anything. SuperUser can't be used as a normal user account (it can't talk) and should only be used for initial configuration or to recover from misconfiguration.

See [here](Running_Murmur#Setting_the_SuperUser_Password.md) on how to set the password for the SuperUser.

## How can I reset the database? 

Delete the murmur.sqlite file then reset the SuperUser password as described [here](Running_Murmur#Setting_the_SuperUser_Password.md). This will also create a new database.

## How can I add a user? 

See [[Running_Murmur]]

And [[Murmurguide]]

## How can I change a user's password? 

See [[Running_Murmur]]

And [[Murmurguide]]

## How can I edit the database? 

Editing of the database directly is no longer supported. We realize that [[Ice]] can be a pain, but once you get past the initial teething problems with it, it simplifies administration and provides a lot less headaches than constantly ensuring the sanity of the database.

However, if you wish to go it alone, the most frequently asked questions: 

* Passwords are stored in SHA1 hashes.

## How do I backup the database? 

Shut down the server (kill the process), and make a copy of murmur.sqlite. That file is the database.

## How do I run Murmur as a Linux/Unix Sys V service? 
There's an example in ''scripts/murmur.init'', see [[Murmur Init Script]] for details.

## I get the error "Meta: Failed to load qWave.dll, no QoS available" in the Murmur log when I start Murmur 

qWave is network QoS for Vista. You don't have qWave, so it's proceeding without it. You can disregard this message if you are NOT on Vista/Server 2008. If you are, you should try to stop the error.

## How can I verify that there is nobody wiretapping my connection (MITM)? 

You can verify that the certificate on the client and server are really the same the following way:

# Iconbox begin|type=infoPlease note: It depends on your distribution whether the database file is named murmur.sqlite or mumble-server.sqlite.# Iconbox end

<b>On server (Linux):</b>

# Connect to your server using SSH or similar.
# Run
 sqlite3 -batch murmur.sqlite 'select value from config where key="certificate" and server_id="1"' | openssl x509 -fingerprint -sha1 -noout

NOTE: On Windows, you can use https://sourceforge.net/projects/sqlitebrowser/ to open the <tt>murmur.sqlite</tt> database.

<b>On client:</b>
# Connect to server
# Select menu "Server" - "Information".
# Scroll down to the "Digest (SHA-1)".
# Verify that this is the same as the SHA-1 fingerprint on the server.

NOTE: The Mumble client also stores the server certificate fingerprint in its <tt>mumble.sqlite</tt> (see [where the clients store their information](Client_Settings.md)) in the table <tt>cert</tt>.

## I used to get a ping display in the server list for my server. I re-installed the server and it is now gone. How to get it back? 
Open the [[murmur.ini]] server configuration file and set an explicit address to listen on using the <tt>host=</tt> setting. Save the config file and restart the server. You should now have the useful ping display again in your connection dialog / server list.

## How do I force usage of the Opus codec (opusthreshold)? 

From [[1.2.4]] onwards the server and clients support opus. The server configuration was extended with the field *opusthreshold* to allow enforcing the usage of Opus. Note: Clients without opus support (clients prior to 1.2.4) will not be able to hear and talk in that case, will however receive a message from the server noting their incompatibility.

To enforce Opus usage only, set *opusthreshold* to *0*.

Also see [[Murmur.ini#opusthreshold]]

## Why does Murmur require a GUI / Qt on Linux? 
Murmur does not require nor have a graphical user interface on *nix. It does use parts of the Qt-Framework which is well known for building GUI applications. However Qt is much more than a library for making user interfaces and if your distribution asks you to install desktop components for the parts we use in murmur they have packaged it or Qt incorrectly.

## How many slots and servers can I host for free? 
As Mumble is true  [(FOSS)](https://en.wikipedia.org/wiki/Free_and_open-source_software Free and Open Source Software) you can host an unlimited number of slots on an unlimited amount of servers (virtual and/or physical) without having to ask us for any kind of permission. This is regardless of whether you plan on hosting a private server or plan on offering [[Commercial Hosting]].

## Can I call in a mumble server using a regular phone or VoIP service? 

Mumble itself does not support SIP or VoIP or telephone use directly, and  [will](https://sourceforge.net/p/mumble/feature-requests/931/ probably never). That said, it's possible to create a plugin that would enable this functionality.

There's a server called  [mumsi](https://github.com/slomkowski/mumsi) which can connect mumble with a SIP server.

= Common Problems and Resolutions =
## Mumble starts and turns into white window with no response ( Windows 7 64bit) 
Run task manager and kill the process, then run Mumble again, should start normally. This issue is under investigation.

## Can't hear other users/users can't hear me 

First check that you can hear yourself in the Audio Wizard. If you can't, then there's something wrong with your local audio configuration.

Next, turn on the Expert Config options, and turn the Loopback Mode to "Server" under "Audio Output". If you can hear yourself talk while connected to the server, your network settings are fine; the problem is other users.

If you can hear yourself in the audio wizard, but not when using server loopback mode, something between you and the server is blocking the data.

Some users of Windows Vista have reported that if you have this problem: (1) set compatibility mode on the shortcut for "Windows XP (Service Pack 2)"; (2) start Mumble; (3) close Mumble; (4) turn off compatibility mode; (5) start Mumble and see if the problem is solved.

## My server has multiple IP addresses. How can I make Murmur listen on a specific address? 

The [host= option in murmur.ini](murmur.ini#host.md) lets you do this. If the option is blank (the default), it will listen on all addresses.

## Server connection rejected: Invalid Password. 
This simply means the server password was incorrect, next time make sure you type in the password in the password box on the connect window.

## Server connection failed: Host not found. 
This means that there is no computer at that ip address, double check this is the right IP

## Server connection failed: Connection refused. 
This means there is a computer there but that is the incorrect port, double check the IP to make sure that this is the right computer, if it is then check what port you are supposed to connect on and put that in the port box on the connect screen.

## I get disconnected from the server as soon as I connect. 
This can be due to a version mismatch between the server and the client. Ask the server owner about the version that its being used, and get that version.

This can also occur with some home routers if they are unable to handle QoS (Quality Of Service) being set on the packets.  This can be disabled in mumble in the  "Network" tab; you will need to check the "[Advanced](Advanced_client_configuration.md)" checkbox to see this.

## I've Tried the above but it will not connect 
Are you on a Network make sure the port is open and the same if the host is on a network.

## I tried but the port is open and it still will not connect 
Then you should enable port forwarding on your router to your computer for the port. To get your LAN IP address:
*Windows: press run then type "cmd" (no quotes) and type in "ipconfig" and it will display your IP address next to IP Address.
*Linux and other unixes: On a console, type ''ifconfig''. Your IP is next to ''inet addr:''

## Mumble G15 keyboard won't show up in Mumble! What's the deal? 
You need the latest G15 keyboard software. Go  [here](http://www.logitech.com/index.cfm/434/180&hub=1&cl=us,en).

## Mumble gives me a BSOD / crashes my PC when I try to start it. 
Mumble has no kernel components, and as such cannot cause a Blue screen of death or crash your computer. A BSOD/crash is an indication of faulty drivers or faulty hardware. Run several stress tests such as  [Prime95](http://www.mersenne.org/freesoft/) to ensure that your system is stable, and also check all other components of your system. A few runs with Memtest86+ are also recommended. Besides this, install the latest drivers, firmware, and BIOS's for your computer.

## The Mumble client does not start, or crashes when connecting (Windows) 
If you are using Outpost Firewall please update to a recent Mumble Snapshot client which should resolve this issue.

## For some reason my game will crash when I'm running Mumble 
The Mumble Overlay is a nice feature that many people use, but because of the rendering methods it uses to display the overlay while you're in a game, it can sometimes make the game crash or not work properly. You can find a list of games that are known to have issues with the overlay and how to solve problems experienced in these games in the [Games article](Games#Overlay.md). You can also find an application incompatibility list on this page as well.

## When I run Mumble the volumes of other applications drop 
If you are running Vista or later this is a feature. Mumble is able to lower the volume of other applications while someone is talking to you. This is very handy in loud games, when listening to music, or watching movies. We understand that some user might not like this feature, to disable it enable Advanced mode in the configuration and pull the "Other applications volume slider" to 100% in the Audio Output tab.

Note: If you are running 1.1.8 on a windows 7 system you will see a similar behaviour which is not caused by this feature. Windows 7 introduced functionality which is supposed to trigger all kind of actions when there is an incoming VoIP call, such as halting video playback and lowering the volume of other applications. Unfortunately this also triggers on Mumble 1.1.8 which was released well before we had access to Windows 7. To solve this issue either disable the feature in Windows 7 (Rightclick the audio icon in the taskbar, select recording devices, go to the Communications tab and disable it) or use the 1.1.X backwards compatible client which comes with recent 1.2.0 snapshots. 1.1.X supports Windows 7 without additional configuration.

## I'm running many virtual servers or have many users connected, and the server becomes unstable 

A phenomenon experienced mostly by commercial hosters who have a lot of virtual servers running. To fix the issues, you need to make sure you use a Qt with glib support.

Second, you need to make sure your per-process file limit is high enough. For most distros, this is done by editing /etc/security/limits.conf. Add the following:
 *       hard    nofile  8192
 *       soft    nofile  8192

	
Make sure the UsePAM in sshd_config is set to yes.
Restart your sshd, log back in and recheck the limit is now 8192 by checking 'ulimit -n'.
If you run murmurd as
 murmurd -limits
It will perform a file descriptor test

## "unable to open database file" in Murmur log  

This ''could'' mean your sqlite database is corrupt, but is likely a symptom of the above file limit issue with virtual servers.
Assuming you've gone through the above troubleshooting, to test for database corruption, run
 echo "pragma integrity_check;" | sqlite3 your-database-name-here.sqlite
To possibly recover from database corruption, the best solution is to restore from your backup. If no backup is available, run
 echo ".dump" | sqlite3 old.db | sqlite3 new.db
'''Make sure you run this on a copy of your database''' as it is not guaranteed to work.


## "A referral was returned from the server." error while starting Mumble on Windows 

''' See: http://blog.mumble.info/important-update-to-mumble-1-2-3a/ '''

Otherwise:
Check your system time. Windows certificate check will fail if your clock is some years ahead/behind.

For Window XP: Install the latest Root Certificate update through Windows Update (it's an optional update) to fix this problem.

For Windows Vista/7: Right-click the Mumble executable, select "Properties", select the "Digital Signature" tab, click "Details" and click "Install certificate".

If you compiled Mumble yourself either sign the binary or disable signing.

## Mumble has high CPU usage 

The two most CPU intensive tasks Mumble performs are resampling and echo cancellation. The first of the two, resampling, is entirely avoidable on most audio hardware in existence today. Mumble operates on a native 48Khz sampling rate and if your audio device is configured to take/provide exactly that sample rate no resampling needs to be performed by Mumble. You can change the native sample rate of your audio devices in your operating systems audio device configuration.

Echo cancellation is used to prevent feedback from speakers or poorly shielded headsets into your microphone. If you do not use speakers you can usually disable echo cancellation without any quality penalty. You can do so via the Mumble audio wizard or the Settings menu.

Note: Mumble can also have a performance impact on games it displays its overlay in. This will not show up as CPU usage for Mumble but for the game it is displaying the overlay in. If you notice an unreasonable performance drop in a game you can either disable the overlay completely or blacklist that particular game in the Settings menu to solve the problem.

## ServerDB: Database driver QSQLITE not available 
If you try to use our current static server binaries and on starting it get the error

 ServerDB: Database driver QSQLITE not available

you will have to install the SQLite driver manually. (Anybody fixed it? Which driver did you install/how?)

This is an issue with our currently generated static binaries and will be resolved in the future.

## Where does the Mumble client store its settings? 
See [here](Client_Settings.md).

## How can I undo audio attenuation applied by Mumble? 
Mumble's sets the application specific volume (on the system's side) and if it doesn't reset it for some reason (e.g. a crash) these settings may persist. To remove them, you'll have to manually raise the volume of that application in the audio settings again. For Windows see https://github.com/mumble-voip/mumble/issues/2606#issuecomment-257071855

= Compilation / installation problems =

## mumble.pri:8: Unknown test function: CONFIG 

Mumble requires Qt version 4.3 or better; you are running qmake from Qt 3

## Error message in murmur.cgi line 118 

You need an MTA on localhost unless you have defined a different SMTP server.

= Language Translation =

If you want to get more information about Mumble Translations or want to help out translating Mumble, take a look at the [Language Translation Page](Language Translation.md).

= Recording =

Many people use Mumble for podcasting/radio because of its high quality and low latency, and we realize that some people want to record their conversation on Mumble for these types of purposes. In release 1.2.3 or later you are able to record with the clients recording feature ( [here](http://blog.mumble.info/for-the-record/ see)). For older releases this feature is not available.

On Windows however, there are many different programs that can capture audio.  [Audacity](http://audacity.sourceforge.net/) is a good program for doing this.

If you are using PulseAudio, read  [guide](http://files.kral.ws/Tobias/Gentoo/mumble-conference_record_with_pulseaudio_and_gstreamer.txt this) on how to record Mumble conversations. The guide is written for Gentoo Linux, but users of other operating systems should be able to adapt this guide to their computer.

= Mac OS X =

## Help! Mumble won't run on my 10.4 installation! 

We no longer officially support 10.4 for our official builds, since none of the developers can test builds for it. However, unofficial snapshots (and release builds) are available at  [http://www.scorpius-project.org/mumble-osx-10.4/](http://www.scorpius-project.org/mumble-osx-10.4/). Note however that we cannot guarantee that they work, or even run.

## How does the overlay work on the Mac? 

Currently, the overlay on Mac OS X is a bit of a hassle. Programs you want to load with the overlay enabled have to be bootstrapped by a launcher executable. What this means is that the program has to be launched via the overlay launcher by passing the path to the program to it. For example:

  /Applications/Mumble.app/Contents/MacOS/Overlay/mumble-overlay ''/path/to/Game.app''

= Windows =

## How do I disable the launching of dbus-daemon.exe? 

The process will only listen to input, thus not produce any CPU load and is really low on memory footprint.

If you still want to disable it, remove the dbus-daemon.exe file from you Mumble installation folder and create a new, empty file and name it dbus-daemon.exe.

## Can I set Mumble to auto-connect to my server when Windows starts? 

The easiest way to make Mumble automatically connect to your server is using the Autostart feature Windows offers in the Start menu. Simply
create a new Shortcut in the Autostart directory in your start menu, that points to a ["mumble://" URL](Mumble URL.md) for your server.

## The overlay does not work in game X 

The overlay currently only works with OpenGL and DirectX9/10 in 32bit applications. This means if your game uses DirectX 11 the overlay will not display. Same goes for 64bit applications (be aware that if you run a Java game like Minecraft in a 64bit Java Runtime Environment it is a 64bit application).

We are working on resolving these issues. For now the only option to get overlay in these applications is to switch them to DirectX 10 (where possible) or respectively to run them in a 32bit Java Runtime Environment.

= Central services =
## Services used by the client 
See [[MumbleServices]].

= Known Issues =
## No Echo Cancellation on Mac OS 
There is currently no Echo Cancellation in the MacOS client.

It might be included in the future though.


