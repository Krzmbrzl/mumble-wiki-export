**NOTE: Please go to [the new documentation on our
website](https://www.mumble.info/documentation/user/positional-audio/)
instead. The documentation here is now obsolete.**

\---

# Positional Audio

This article describes how Positional Audio (PA) works. For a list of
games with PA support, see [Games](Games "wikilink").

## What is Positional Audio

Positional Audio is a feature of Mumble that places the people talking
to you in a certain position relative to your own depending on their
actual position in the game you are playing. This way you can hear the
person as if their actual avatar in-game was talking to you.

If someone is NOT using Positional Audio, you would hear that audio
source always from the same spot, equally loud from each of your stereo
speakers.

![StationaryAudio.gif](StationaryAudio.gif "StationaryAudio.gif")

If someone uses Positional Audio, and is in the same context
[(game)](Games "wikilink") you will hear them louder from one speaker
than from the other in such a way that correctly represents their angle
and distance to you.

![Positional_Audio.gif](Positional_Audio.gif "Positional_Audio.gif")

## How does Mumble get informations about the virtual positions of the clients

There are two different approaches for Mumble to get this information.

  - One: The [Game](Games#Supported_Games "wikilink") itself has a
    routine that transmits this data from within the program to the
    mumble client.
  - Two: The Mumble client can use a specially crafted plugin to peek
    into the memory of a game to get the needed information. This
    approach is done from outside of the program. If a program gets
    updated and stores the position on a different memory offset the
    plugin has to be updated as well to work again.

Either way Mumble tries to gain the following information:

  - Position/Heading of your avatar
    [in-game](Games#Supported_Games "wikilink")
  - Position/Heading of the [in-game](Games#Supported_Games "wikilink")
    camera
  - A so called "context" uniquely identifying the game (as in
    server/realm and so on) you are playing on
  - A so called "identity" uniquely identifying the client amongst other
    clients with the same "context". It is also used to store additional
    information like team or class depending on the game.

The server will only transmit positional audio data to client with
matching context information. That means if you play a game on two
different servers you will not hear each other positionally. The context
and identity information are not forwarded to the other clients though.
They can be used by server side applications which could, for example,
place players in different channels/groups depending on the server/team
they are currently playing on/in.

## How to activate Positional Audio

![Audio-Output.jpg](Audio-Output.jpg "Audio-Output.jpg") Postional Audio
is activated by default. If you wish to configure it you will have to
open settings pages of Mumble and check the

(1) Advanced Config settings

on the Audio Output is a check box (2) to General enable or disable
Positional Audio for your client.

<div style="clear:right;">

</div>

-----

![Plugin.jpg](Plugin.jpg "Plugin.jpg")

On this Page you are able to generally allow Mumble to see if you run a
program that matches one of the plugins in Box (2) The check box in the
plug-in list (2) enables or disables the plug-in. This way you can
decide if you want positonal audio for a certain program or not. The
Button (3) "reload Plugins" tells the client to reload the .dll's from
the filesystem and check if there is a new Plugin in the plugin folder
on your local drive.

Mumble does this lookup on startup and futher more checks on the
internet for updated versions of the plugins. If there is a newer
version the client downloads it automatic and places it into the right
folder. Be aware that if there is an old .dll it gets replaced. (4)
shows you addtional Infos about the selected plugin in (2) the main box.

If the Plugin can be configured you can use Button (5) Configure to get
into the options of the selected Plugin.

Currently the only Plugin that has such a page is the *"Manual Positonal
Audio"* Plugin (see --\> Games
[Games\#Special_Plugins](Games#Special_Plugins "wikilink"))

<div style="clear:left;">

</div>

## What Programs/Games does Mumble Support with Positional Audio

see --\> [Games](Games "wikilink")

## How do I create Positional Audio for an unsupported Game

See [Pluginguide](Pluginguide "wikilink") for a step-by-step explanation
on how to create plugins and
[HackPositionalAudio](HackPositionalAudio "wikilink") for a more
abstract explanation with more methods for retrieving the data.

If you can mod the game you might be able to use
[Link](Link "wikilink"). Check in advance if the game's modding API
allows you access to the relevant data\!

[Category:Documentation
English](Category:Documentation_English "wikilink")