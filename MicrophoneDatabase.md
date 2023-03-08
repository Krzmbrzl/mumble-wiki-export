# Notice|message=This is probably outdated (last edit 2009). Needs review.

= Frequency response database =

Right now, the audio quality in Mumble is "really good". Noise filtering, echo cancellation and automatic gain means most people sound good, or at least as good as their headset. A problem with consumer grade headsets is that, while cheap, their audio quality leaves a lot to be desired. The headphones are bad, the microphone is usually much worse.

We therefore intend to compile a datbase of common headsets, measuring the frequency response of the microphones so that the shortcomings of the headset can be countered.

## From the users point of view 

The user will simply pick their headset from a long list of alternatives, and magically sound better to others.

= Test methodology =

Assuming the current plan is successfull, we'll have access to an anechoic chamber with a artificial head. For each headset, we'll then:

* Put the headset on the artifical head.
* Place a reference microphone (hereafter called just 'reference') as close to the microphone from the headset (hereafter called just 'microphone') as possible.
* Play a 60 second logarithmic sweep from 15hz to 23khz (generated with the tools from drc) through the mouth of the head. Repeat several times with the microphone arm in different positions.
* Play a 20 second long speech sample through the mouth of the head.
* Play the same logarithmic sweep through the headset itself.
* Record both the reference mic and the headset.
* (If we can find the microphones for it; record with the head as well)

All of the above will be done at 48khz, 24bit, or as close to it as equipment will allow.

## Post processing 

* Convolve both reference and microphone recording with the inverse filter of the sweep.
* FFT both, smooth the curve, compute power, piecewise divide.
* Resample resulting umpty-sample inverse frequency response down to 480 elements.

## Realtime processing (what we intend to do in Mumble) 

Per frame, in the preprocessor:
* FFT with windowed overlap-add (which is already done)
* Piecewise multiply with 480-element result from post processing.

So in short, we can get realtime frequency response correction for the runtime cost of one multiply per FFT element, and there is no additional latency added.

= Help Wanted =

I am not a signal processing guru. So some questions remain:

* I'll simply assume that either immediately or some time in the future, improvements can be found to my post processing, so I intend to publish the reference and microphone recordings as raw data (along with my postprocessing programs). This way people can use this data for their own processing. If anyone can think of any additional measurements that should be made, please say so now.
* The artificial head may not be available to us; how relevant would the measurements be if we simply used one or more speakers?
* Unless the microphone sensitivity happens to be perfectly matched to the reference, we'll need to scale. Are there any sane ways of calculating a scaling factor? RMS in the 0.1-4khz range?
* The point of playing the sweep through the headset itself is that quite a lot of headsets generate echo by the audio mechanically travelling down the arm to the microphone. However, we can, in the future, also use this to do output correction.
* The point of the 20 second speech sample is to provide end users (and hardware reviewers and manufacturers) with examples of reference, raw and corrected recordings. Hopefully this will encourage people to send us headsets. Any suggestions for a good sample that covers as wide a frequency range as possible?
* Quite a lot of headsets these days come with a built-in USB soundcard, and they are often integrated so you can't plug out the headset. These headsets usually pick up a lot of electrical noise from the computer over the USB cabling; any suggestions on how to provide a noise-free USB signal, power and ground?
* ... and are there any suggestions on how to handle the clock desynchronization that will occur with lousy USB soundcards? They will not be sample synchronous to my reference recording any more.
* This whole idea is based on headset microphones having unit consistency. I happen to have a few identical cheap headsets, and their frequency response was pretty identical when measured in my living room (hardly perfect circumstances). Does anyone have counter-examples to this?



