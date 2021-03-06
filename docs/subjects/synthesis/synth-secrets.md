# Synth Secrets
## Intro
It's winter. We're in lockdown. I've just released an EP. I only ever have a brief couple of hours in the evening, when I'm so tired from the day, just thinking about being radical, free and creative makes me want to sleep. So, how should I spend my winter? 

For a while now, I've identified that my basic knowledge of synthesis is lacking. Now that I've got a good process for organising events algorithmically (Tidal), I think it would be fruitful to back this up with an extended repertoire of synthesis techniques. Whilst I'm there, I may as well write up what I learn and share them online. These notes, therefore, could be redrafted to create a course of sorts.

I'm going to base this on Sound On Sound's legendary Synth Secrets series which can be found [here](https://www.soundonsound.com/series/synth-secrets).

## Techniques to try
Keep a running list of techniques that arise over the course of the series that you want to explore in more depth.
* Resonant filter sweeps (see [section](pages/synth-secrets?id=of-responses-amp-resonance))
* Resonance self-oscillation (see [section](pages/synth-secrets?id=of-responses-amp-resonance))
* Using vibrato to modulate a self-oscillating filter (see [section](pages/synth-secrets?id=of-responses-amp-resonance))
* Using a CV to control the Q of a sound (see [section](pages/synth-secrets?id=of-responses-amp-resonance))
* Pulse width modulation (PWM) (see [section](pages/synth-secrets?id=modulation))
* Additive synthesis with each component modulating in some way

## 1 - What's in a sound?
[Link](https://www.soundonsound.com/techniques/whats-sound)

Overview of mathematical principles of waveforms - fundamental frequency, harmonics etc. Introduces concept of subtractive synthesis - filtering complex waveforms.

## 2 - The physics of percussion
[Link](https://www.soundonsound.com/techniques/physics-percussion)

Discussion of complexity of vibrating membranes - can't be so easily expressed as the 'one-dimensional' vibrations of string. Can be reduced to the idea that, whereas 'one dimensional' vibrating bodies have mathematically related harmonics - and therefore are experienced as tonal - 'two dimensional' vibrating membranes create complex, mathematically unrelated harmonics/overtones - experienced as noise. These can be synthesised using a noise generator - white noise, for example, producing all frequencies simultaneously. Filtered noise is the basis of the most popular drum synthesizers of the 1990s - Roland CR78, TR808 etc.

Also, alludes to metal percussion such as gongs and bells. Despite looking very different, these are governed by the same rules as the stretched membrane as they are still 'two dimensional'. Even bells can be through of as bent sheets.

Mentions the use of the ring modulator to create metallic sounds. Ring modulators "produces the dense cluster of non-harmonic overtones that are characteristic of metal sheets."

## 3 - Modifiers and controllers
[Link](https://www.soundonsound.com/techniques/modifiers-controllers)

Discussing harmonic content of a sound is insufficient for an understanding of synthesis. Need to understand how sounds change over time.

### Modifying a sound
Most obvious aspect of a sound that changes over time is the loudness - since it must have a beginning and end. In synthesis, this contour of the volume is achieved by adding a `controller` to the amplifier. Since this controller is another fluctuating form of voltage, this is called a `control voltage` or `CV`. Since this controller is applied, in this case, to the amplifier, we call it a `voltage controlled amplifier` or `VCA`.

### Envelopes
Discusses `ADSR` envelopes. Envelope Generators `EG` are simply a form a of controller connected to the VCA that can be triggered and control the value of the amplified over time.

### LFOs and Tremelo
Tremelo is simply a CV applied to the amplifier. This CV can be an oscillator. 

### Summary
Desribes three fundamental types of module available to all synths:
* Signal generator - for example, a Tone generator: produces the basic audio tone
* Modifier - for example, a VCA: changes the audio signal in some way
* Controller - for example, an LFO: directs the behaviour of a modifier

There's is ambiguity over the definition of modules, as all of them will create fluctuating amplitudes. So, therefore, it is not the source that determines whether a module is a signal generator, modifier or controller, but it's destination - can we hear it directly, or are we hearing it's influence in other words.

## 4 - Of Filters & Phase Relationships
[Link](https://www.soundonsound.com/techniques/filters-phase-relationships)

Filters are the crowning glory of subtractive synthesis. However, they are much misunderstood - "even the most basic belief surrounding them (that they just make parts of the signal quieter) is wrong". A filter does far more than just attenuate. To really understand what they do, it's necessary to understand phase relationships.

### Phase 
Adding together two sines that are 180deg out of phase produces silence. Adding together two sines that are 360deg out of phase produces doubles the frequency. Adding together sines using phase relationships that are less symmetrical will produce results somewhere between complete attenuation and doubling of the amplitude.

This idea applied to more complex waveforms creates more complex results, with some harmonics attenuated and some applified.

"Combining complex 'out of phase' signals does not necessarily lead to complete cancellation. In fact, in the real world, it rarely, if ever, does so."

This is because, taking two identical signals and offsetting them, the different harmonics will be phase-shifted by different amounts (as they have different wave lengths). When viewed as on a spectral analyser, this looks like a comb with cancellations occuring creating teeth. This is indeed called a `Comb Filter`.

### Phasing & Filtering
Looks at an `LPF`. 

"Filters not only change a waveform by attenuation, but distort it by individually phase-shifting the harmonics within it."

## 5 - Further With Filters
[Link](https://www.soundonsound.com/techniques/further-filters)

The relationship between the input and output of a filter is called a `Transfer Function`. A 6dB/octave describes a filter where, for every octave, we attenuated by 6dB. Discusses the misconception that the cutoff is the point in the frequency spectrum where we apply our filter. In fact, attentuation happens well before this.

6dB/octave filters are used as tone controls in hifis, but they are not generally used in synthesis as they don't modify the signal enough to change the tone dramatically. A more powerful filter is required if new timbres are to be created.

Whereas a 6dB/octave filter can be created with a single passive component, steeper curves require a different approach. Cascading passive components doesn't work so we have to use `2-pole` and `4-pole` filters. There's some pretty complex maths involved but, in general, these filters use a Laplace Transform. A single 6dB/oct filter has 1 pole, a double 12dB/oct filter has 2 poles and a 24dB/oct filters have 4 poles. Again, the effect of these is far from the ideal, with a 4 pole, 24dB/oct filter actually having numerous legs, as opposed to being a straight line. Each of these legs has slopes nearer to 6db and 12db, and are curved. So, expecting a 24dB filter to actually attenuate a signal by 24dB per octave is false. There is also some discussion of how these filters affect the signal in the pass band - with distortion present...

## 6 - Of Responses & Resonance
[Link](https://www.soundonsound.com/techniques/responses-resonance)

### Varying the cutoff filter
Discusses circuitry of high pass and low pass filters.

### More types of filter
Discusses combining LPF and HPFs to create band pass and band reject filters. Also highlights that phase shifts introduced by two separate filters can cause all manner of side effects.

### Sweeping the filter
Obvious at this point that we could replace the potentiometer used to control the cutoff frequency with a CV of some sort.

### Resonance
Discusses resonant frequencies - for example, a string place before a speaker playing music will vibrate in sympathy when frequencies proportionate to 
the string play in the music - ie. frequencies at the strings resonant frequency.

When you combine resistors and capacitors with an inductor you can create a circuit that has a a large peak in the response at a certain frequency. In a filter, the frequencies that are resonant are those near the cutoff. If you use a voltage controller to sweep the cutoff of a resonant filter up and down you end up with one of the most desirable of all analogue filter sounds.

### Self Oscillation
If you continue to increase the Q, the resonance becomes so pronounced that high and low frequencies disappear from the signal and another effect occurs - the filter begins to oscillate at its cutoff frequency. A filter on the edge of self oscillation 

## 7 - Envelopes, Gates & Triggers
[Link](soundonsound.com/techniques/envelopes-gates-triggers)
## 10 - Modulation
[Link](https://www.soundonsound.com/techniques/modulation)

### 1. Three simple modulations
* Vibrato - modulation of pitch
* Tremolo - modulation of loudness
* Modulating the cutoff on the filter - from slow filter sweep to a growl when modulated at higher frequencies

In all cases, the frequency of modulation is, of course, controlled by the frequency of the LFO. The depth is controlled by the level of the VCA that the LFO passes through.

### 2. Another simple modulation
Discusses pulse waves. Square wave has a duty cycle of 50% or a ratio of 1:2 (spends 1 out of 2 periods of time 'at the top'). Duty cycle has great affect on the timbre of the sound. Waveforms with a duty cycle of 5 - 10% are thin and nasal. At 50% becomes hollow and woody. 

These ratios/percentages have a pleasing relationsip with the harmonics. A waveform with a 50% / 1:2 duty cycle (square wave) has every other harmonic missing (comprised of 1st, 3rd, 5th, 7th...). A waveform with 33.3...% / 1:3 duty cycle with have every third harmonic missing (comprised of 1st, 2nd, 4th, 5th, 7th, 8th etc.). Where the duty cycle is not an integer, the two harmonics between where the percentages lies with be attenuated, but not completely removed.

#### Pulse width modulation
See paragraph above for outline of pulse waves. In PWM, a CV is used to modulate the duty cycle, or pulse width of the tone generator. PWM is ideal for creating string sounds as well as lush lead sounds.

## 11 - Amplitude Modulation
[Link](https://www.soundonsound.com/techniques/amplitude-modulation)
Previous discussion of modulation was all based around LFOs - modulation using frequencies that are below the range of human hearing. But what happens when we use audio frequency signals? This opens up a whole range of timbral possibilities as, rather counter intuitively, rather than these higher frequencies creating a more intense, but essentially the same, type of modulation (for example a quicker, more intense tremelo), they actually introduce frequencies that weren't previously there...

### Maths...

## 12 - Introduction to frequency modulation
[Link](https://www.soundonsound.com/techniques/introduction-frequency-modulation)

John Chowning discovered this form of synthesis when experimenting with vibrato, discovering that when the modulating waveform goes beyond a particular frequency, vibrato disappears and a new complex waveform emerges. 

FM is simply very fast vibrato. It can be visualised in our schematics as an audio rate oscillator, being modulated by a control rate oscillator. FM, like AM, generates sidebands - additional components, not necessarily harmonically related to the freq of the Carrier or Modulator. Whereas AM produces just two, FM produces many sidebands. The modulator's frequency determines where these sidebands will lie. The modulator's amplitude will determine the shape, or amplitudes, of this spectrum. However, this is not constant, and the modulator amplitude must increase proportionally with the pitch to keep the spectra constant. It must, in fact, double with the frequency.

### Filters
In accord with the Making a Noise book on FM, there is no need to use filters here as controlling the Modulation Index (Carrier / Modulator) determines the bandwidth of the waveform (by determining the shape of the spectra). Using envelopes to control this spectra creates much more rich audio effects than the simple pass and block of spectra achieved using filters.

### Summary
we can say the following two things about the relationship between the Modulator and the output signal:

* The number of significant spectral components and their amplitudes are determined by the Modulation Index, which is proportional to the Modulator's amplitude; but inversely proportional to the Modulator's frequency...
* For any given Carrier frequency, the position of the spectral components is determined by the Modulator's frequency alone.

## 13 - More on frequency modulation
[Link](https://www.soundonsound.com/techniques/more-frequency-modulation)

### Introducing Carrier:Modulator (C:M) Ratios
In an example where the C:M ratio is 1:1 (the carrier frequency and the modulator frequency are equal) the frequencies of the upper sidebands are C+M, C+2M, C+3M, C+4M etc... The frequencies of the lower sidebands are -C+M, -C+2M, -C+3M, -C+4M etc. What are negative frequencies? Turns out they are the same as the upper frequencies but with their phases inverted. Wouldn't this create phase cancellation? No, because the amplitudes of these upper and lower sidebands are not the same. 

So, in the above example, if the Carrier was 100Hz, the sidebands would be 200Hz, 300Hz, 400Hz, 500Hz etc. A perfect harmonic series.

### Creating Recognisable Harmonic Series
In the above example of 1:1, not only do we get all of the frequencies of the harmonic series, due to some complex maths that we'll skim over, these have amplitudes of 1n - which is a filtered sawtooth wave.

For a C:M of 1:2, the sidebands are 3C, 5C, 7C... just the odd harmonics are present - which is a filtered square wave.

For 1:3, upper sidebands are 4C, 7C, 10C... with reflected lower sidebands 2C, 5C, 8C... - creating a pulse wave.

The results are relatively simple for integer ratios, creating harmonic sounds with the carrier as the fundamental. This becomes much more complex when the C and M are not integers - often with carrier no longer being the lowest frequency in the spectrum.

Discusses operators and various schematics for creating sounds.

Some directions for drum synthesis using FM:
* https://www.musicradar.com/how-to/how-to-make-electronic-drum-sounds-using-alternative-synthesis-methods

## 14 - An introduction to additive synthesis
[Link](https://www.soundonsound.com/techniques/introduction-additive-synthesis)

Additive synthesis usually only associated with digital synthesis.

### Principles
Refers back to the first in the series - discusses harmonic series and that the harmonic content of a sound determines the waveform. Just as we can break a wavefrom down into its harmonic components, so we can build sounds up from sine waves. Gives this summary: "at any given moment, you can describe any waveform in terms of the frequencies and amplitudes of its components, you can take the appropriate number of sine waves and mix them together at the appropriate frequencies and in the appropriate quantities to regenerate the waveform."

Now, given that this type of sythesis in the analogue domain would require a large bank of VCOs, all connected to VCAs, with a mixer and some kind of gate, this is hopelessly inefficient. However, the Hammond Organ does precisely that. The tonewheel organ has 91 discs on an axle, running the length of the instrument, that, when rotated infront of a pickup, create a pretty close approximation of a sine wave. Each register has 9 drawbars which, when extended, mix in the sound of one of these oscillators at an amplitude dictated by how far out the drawbar is extended.

Whilst the above configuration can create a seemingly infinite array of timbres, what is missing from this being a truly powerful synthesizer is that the Hammond does not have a means of shaping the harmonics over time. Sounds are therefore static. This works for a Hammond because, by their very nature, organs are simple waveform generators which create tones that do not shift over time. Put another way, regardless of the method of synthesis, any timbre will sound static and 'organ-like' if it does not change over time.

If we consider a plucked string sound, with a bright attack that gives way to a darker sustain, we could be tempted to introduce a filter to our additive synthesiser. However, considering that the brightness is determined by harmonic content, why not achieve the same effect by controlling the amplitude envelopes of our harmonics? being able to individually control the amplitude envelopes of your harmonics allows you to achieve timbres that would be impossible with a single signal path.

### Fourier analysis

Discusses Fourier. There's also nothing to stop you from using more complex waveforms, rather than sinewaves, as the basis for your additive synthesis.

### Noise
Even though a flute can be broken down into its constituent, sinusoidal parts, there is still the missing aspect of noise. So, a complete setup would require a white or pink noise generator, with some sort of filter and envelope. 
## Part ? - Creative synthesis with delays
[Link](https://www.soundonsound.com/techniques/creative-synthesis-delays)

### Analogue vs digital delay
Conceptually, these are very similar - an input signal arrives at the delay, is then held for a period of time before joining the output. The difference in sound occurs due to the degradation introduced in the analogue process. In the digital output, the signal we end up with will be identical - delays to oneside - as the input. However, in an analogue circuit will be affected by the limitations of the capacitors and by electronic noise. These errors are culumative. If the effects are random this will result in white noise being added to the system. However, often as not, these errors will be systematic, and so a certain effect will be introduced.

### Analogue, Digital & Tape Delays
Discusses usual circuitry for delays line.

* Multiple delays lines - where multiple play heads are arranged after the record head.
* Feedback, caused by using a tape loop rather than an infinitely long piece of tape. Delay lines are sent back to the start of the circuit. An erase head is placed before the record head. How much the looped signal is erased is a pleasing effect.

