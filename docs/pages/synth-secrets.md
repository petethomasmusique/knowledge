# Synth Secrets
## Intro
It's winter. We're in lockdown. I've just released an EP. I only ever have a brief couple of hours in the evening, when I'm so tired from the day, just thinking about being radical, free and creative makes me want to sleep. So, how should I spend my winter? 

For a while now, I've identified that my basic knowledge of synthesis is lacking. Now that I've got a good process for organising events algorithmically (Tidal), I think it would be fruitful to back this up with an extended repertoire of synthesis techniques. Whilst I'm there, I may as well write up what I learn and share them online. These notes, therefore, could be redrafted to create a course of sorts.

I'm going to base this on Sound On Sound's legendary Synth Secrets series which can be found [here](https://www.soundonsound.com/series/synth-secrets).

## Part 1 - What's in a sound?
[Link](https://www.soundonsound.com/techniques/whats-sound)

Overview of mathematical principles of waveforms - fundamental frequency, harmonics etc. Introduces concept of subtractive synthesis - filtering complex waveforms.

## Part 2 - The physics of percussion
[Link](https://www.soundonsound.com/techniques/physics-percussion)

Discussion of complexity of vibrating membranes - can't be so easily expressed as the 'one-dimensional' vibrations of string. Can be reduced to the idea that, whereas 'one dimensional' vibrating bodies have mathematically related harmonics - and therefore are experienced as tonal - 'two dimensional' vibrating membranes create complex, mathematically unrelated harmonics/overtones - experienced as noise. These can be synthesised using a noise generator - white noise, for example, producing all frequencies simultaneously. Filtered noise is the basis of the most popular drum synthesizers of the 1990s - Roland CR78, TR808 etc.

Also, alludes to metal percussion such as gongs and bells. Despite looking very different, these are governed by the same rules as the stretched membrane as they are still 'two dimensional'. Even bells can be through of as bent sheets.

Mentions the use of the ring modulator to create metallic sounds. Ring modulators "produces the dense cluster of non-harmonic overtones that are characteristic of metal sheets."

## Part 3 - Modifiers and controllers
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

## Part 4 - Of Filters & Phase Relationships
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

## Further With Filters
[Link](https://www.soundonsound.com/techniques/further-filters)

The relationship between the input and output of a filter is called a `Transfer Function`. A 6dB/octave describes a filter where, for every octave, we attenuated by 6dB. Discusses the misconception that the cutoff is the point in the frequency spectrum where we apply our filter. In fact, attentuation happens well before this.

6dB/octave filters are used as tone controls in hifis, but they are not generally used in synthesis as they don't modify the signal enough to change the tone dramatically. A more powerful filter is required if new timbres are to be created.

Whereas a 6dB/octave filter can be created with a single passive component, steeper curves require a different approach. Cascading passive components doesn't work so we have to use `2-pole` and `4-pole` filters. There's some pretty complex maths involved but, in general, these filters use a Laplace Transform. A single 6dB/oct filter has 1 pole, a double 12dB/oct filter has 2 poles and a 24dB/oct filters have 4 poles. Again, the effect of these is far from the ideal, with a 4 pole, 24dB/oct filter actually having numerous legs, as opposed to being a straight line. Each of these legs has slopes nearer to 6db and 12db, and are curved. So, expecting a 24dB filter to actually attenuate a signal by 24dB per octave is false. There is also some discussion of how these filters affect the signal in the pass band - with distortion present...



