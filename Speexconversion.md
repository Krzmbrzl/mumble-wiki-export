# How to convert a sound file to speex

Mumble now supports playing triggered events using a speex sound file.
This guide will show you how to convert almost any non-DRM sound file to
a speex file that you can use in Mumble.

## Files

First you will need a sound file. Find the file you want to convert and
remember where it is located. For the purposes of this guide all sound
files (for the Windows based instructions) will be called
"sound.<extension>".

Now install MediaCoder: <http://mediacoder.sourceforge.net/download.htm>
(Please note that if you already have a wav file, you can use it. It
must be a 16 Khz, Mono WAV or PCM file however.) You can also use your
encoder of choice to convert it to 16 Khz mono if you wish. MediaCoder
is used here as an example.

Once MediaCoder is installed, start it and drag your sound file into the
top left box that has the "Name" field at the top of it. Now click the
"Audio" tab near the bottom of the MediaCoder window. For the Encoder
select "Waveform", for Resample select "16000 Hz" and for Channel select
"Mono (Left)". Output should be set to "Waveform file". Now press F5 and
the encoding process should begin. Once it is done you should have a wav
file in the same location as the input file. Please note, in future
versions of Mumble, different sound files will be used so make sure to
keep your original sound files.

It is now time to install the Speex convertor. Download and unzip this
<http://downloads.xiph.org/releases/speex/speex-1.2beta3-win32.zip> to
*C:*. Rename the folder *speex-1.2beta3-win32* to just *speex*. There
have been issues running this version of speexenc with Windows Vista for
certain people. If speexenc crashes when you try to encode, please post
on the forums to let us know.

## Windows Commands

Start your command prompt (press the Windows key, hold it down, then
press the R key, type cmd and press enter). Type

`cd \speex\bin`

and press enter. Now in Windows Explorer find your transcoded wav file,
and put it in *C:\\speex\\bin*.

Now copy this command, and in the command prompt, right click and select
"Paste".

`speexenc.exe --quality 10 --comp 10 --nframes 10 sound.wav sound.spx`

Press enter and it should encode the wav file into a speex file.

Take the speex file from the *C:\\speex\\bin* folder using Windows
Explorer, and put it in *C:\\Program Files\\Mumble\\spx* (this step is
not necessary but it makes managing your sound files a bit easier).

## Linux Commands

Tools:

sox [1](http://sox.sourceforge.net)

speexenc

Convert your wave File to 16 kHz (wideband)

`sox record.wav record-wideband.wav rate 16000`

Convert your wave File to Speex ogg

`speexenc --quality 10 --comp 10 --nframes 10 record-wideband.wav record.spx`

## Enabling the Sound File

In Mumble, go to Configure -\> Settings -\> Messages and select a
message you would like the sound file to play when the message triggers.
Once selected, click the radio box for "Soundfile" then click Browse.
You should see the spx folder you created. Open this, select your speex
file, and click Open. You can also test the file here by clicking it
once. Doubleclick it to change the file.