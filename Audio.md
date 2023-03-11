# Introduction

Mumble features various Audio Options and Features, this wiki page will
describe them and tell you which settings are best for your setup.

# Audio Input - Options

## Interface

### Echo Cancellation

If enabled, this will filter echo from the audio you send to others.
You should enable it in the following cases:
1\. You use conventional loudspeakers and no headset:
This Setup will usually create echo, so you will need echo cancellation.

2\. Headset transmits echo, though it shouldn't:
Some Headsets tend to transmit echo, the reasons for this include: bad
cable and noise isolation or the microphone is to close to the
loudspeakers of the headset.

Two options are implemented (you can choose one of them):
{| class="wikitable" |- \! Option: \!\! Description: \!\! Usecase: |- |
1. Mixed echo cancellation || This is the basic Option: It will process
all loudspeaker outputs bundled together.
This is less accurate than the Multichannel option, but will also use
less CPU. || Sufficient for setups with loudspeakers near to the
microphone.

|- | 2. Multichannel echo cancellation || Extended option: It will
process all audio channels seperately, this is more accurate, but will
result in higher CPU usage. || For setups with (multiple) loudspeakers
farther away from the microphone. |}

In case of doubt:
1\. Try *Mixed echo cancellation* first.
2\. If *Mixed echo cancellation* does not filter the echo correctly, try
*Multichannel echo cancellation*.

**Alternatives:**
You can also use external echo filters.

Examples for external echo filters:
\* Pulseaudio Module: [Documentation (options
only)](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#index45h3)

  - Pulseeffects: [pulseeffects on
    Github](https://github.com/wwmm/pulseeffects)

## Audio Processing

### RNNoise

RNNoise is a noise suppression library.
It is intended to filter background noises from the audio that is sent
to other users.
RNNoise uses a deep learning algorithm so it should work better than
most regular filters.

More information can be found on various websites:

  - <https://github.com/xiph/rnnoise>
  - <https://hacks.mozilla.org/2017/09/rnnoise-deep-learning-noise-suppression/>

# Audio Output - Options

# Technology

In this section we take a short look at the technology behind the
scenes.