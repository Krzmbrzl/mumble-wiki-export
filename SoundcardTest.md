# Testing soundcard impulse response

In theory, soundcards have a perfectly flat frequency response, without
any distortion. In practice, they have a slightly uneven frequency
response and quite a bit of distortion. This is a (very) simple test to
figure out if your soundcard is a high quality one or not.

## You need

  - A soundcard with line out and line in (microphone in may do, but
    your results might be off).
  - A PC running Windows
  - [Audacity](http://audacity.sourceforge.net/)
  - A short, quality 3.5mm to 3.5mm cable.
  - A bit of patience.

## Prep

  - Hook the 3.5mm cable from line out to line in. Make sure the cable
    isn't lying over or next to any power cables or unshielded signal
    cables.
  - If you are on Vista/Win7, rightclick the volume icon, click Playback
    devices, Properties on your device, Advanced, and make sure it's
    48000hz (16 or 24 bit). If it can't do 48khz, this test is useless.
    If there is an enhancements or vendor specific tab, make sure all
    enhancements are disabled.
  - Repeat the above for recording device.

## Recording

  - Start Audacity
  - Set the project rate to 48000 Hz (lower left corner)
  - Check Edit|Preferences and make sure the datarate is 48000 32bit
    float
  - Download [sweep.pcm](http://mumble.hive.no/sweep.pcm).
  - File|Import|Raw sweep.pcm, which is a 48000hz 32bit float 1channel.
  - Click the big red record button. You should see the waveform being
    recorded. Adjust the *playback* volume until the amplitude of the
    recording doesn't fill up more than 80% of the available vertical
    space. If it's already below 80%, great :)
  - Delete the recorded track.
  - Repeat the recording, and this time yank out your cable halfway
    through. Verify that the signal goes to zero and that you aren't
    just recording the internal loopback.
  - Delete the recorded track.
  - At the bottom, set start to 0sec, length to 50sec.
  - Record
  - Select your new track. Click the name of the track and rename it to
    your sound card.
  - Select your track (click where it says Stereo 48000hz), then select
    'Stereo to Mono' from the 'Track' menu.
  - If the shape of the two tracks are identical, great :)

[Category:Documentation
English](Category:Documentation_English "wikilink")