# AMD-Hackclub-BLUEPRINT-program-repository
**Description**
This project is a DIY analog synthesiser that I have designed from scratch as an EPQ project. It is a dual oscillator monophonic synthesiser with entirely analog signal processing.
A RP Pico and DAC is used to convert MIDI data into control voltages for velocity and pitch.

The synthesiser includes an analog velocity sensitive envelope, using mathematical models of how real world piano tones behave to model the relationship between note velocity and max amplitude, attack time, decay time and release time.

Additional features include a LFO with sineshaper, two oscillators, a powerful 4 pole VCF and a digital transposition section, which allows each oscillator to be tuned up and down in semitone increments.

**How do I use this synthesiser?**
If anyone is, for whatever reason, keen to emulate this project and try it out, you will find that it functions mostly like any analog synth you might have used before. The signal chain starts with an oscillator, which produces selectable saw/triangle/pulse waves at a frequency defined by a control voltage. This control voltage comes from a DAC, driven by my RP Pico running MIDI - CV conversion. Next, this waveform, rich in harmonics, runs through a mixer, where the level of each waveform, as well as those on the duplicate 2nd oscillator, can be adjusted. These waveforms are summed and sent into a VCF, or voltage controlled filter. This uses a 4 pole filter, meaning essentially 4 filters in series, to suppress higher harmonics. The frequency at which harmonics are cut off, called the cutoff frequency, can be adjusted on the panel, or by a control voltage. This control voltage comes from and envelope, which I will explain in a bit. The VCF also does some other things like boost the frequency at cutoff (resonance), and then we get to the VCA, or Voltage Controlled Amplifier. One channel of this is used to attenuate the signal, again with both a master output volume and a voltage control from an envelope. Furthermore, there is a LFO, or low frequency oscillator, operating at sub audio frequencies, whose output can be used to modulate the frequency of the oscillator, creating a vibrato like effect. This has a cool sine shaper, used to derive a sinosuidal profile wave from a triangle wave using the non linear distortion of a LM13700 dual transconductance op amp. Now, to the envelopes. In my synthesiser, unlike most, there are two ways to operate the envelopes: Manual and Velocity sensitive. In manual, user controlled levels of attack, decay and release time as well as sustain level define the profile of an ADSR envelope. To help understand this, here is a little graphic of the profile of the control voltage this produces, which can be sent to the VCA or VCF to cause the cutoff/amplitude to rise then fall over the course of a note being pressed:
https://www.google.com/url?sa=t&source=web&rct=j&url=https%3A%2F%2Fthewolfsound.com%2Fenvelopes%2F&ved=0CBYQjRxqFwoTCICbkcravpMDFQAAAAAdAAAAABBv&opi=89978449<img width="800" height="399" alt="image" src="https://github.com/user-attachments/assets/b75de6e1-1f53-4f79-bb56-94cbcb69cd54" />
In Velocity Senstive mode, things get a little bit more interesting. My RP Pico is running a parallel process of outputting a Velocity CV, which is proportional to the note velocity MIDI Value. This Velocity CV is sent to a series of logarithmic amplifiers and inverting amplifiers in what I call the piano-ifier. The purpose of this section is to emulate how real piano tones' decay, attack and release times relate to note velocity. For example, decay time follows a linear relationship, whilst release time is a logarithmic one. In addition, one of the channels of the VCA is used as a master max amplitude attenuator, where the loudness/amplitude of the signal is controlled proportional to note velocity, as seen on real pianos. 
The form of the casing of the synthesiser is roughly modelled of a MiniMoog, a classic 1970s synthesiser. This will be updated and iterated on in the future as my EPQ research dives into retrofuturism after the deadline of Hackclub.

W**hy did I decide to do this project?**
This is for an EPQ qualification, where I design an artefact whilst documenting my research, design and prototyping in detail. I chose this specific artefact as it stems from a curiosity into electronic music, and vintage synthesisers which I never really looked into before. My research has taken me across several different technical areas, as this is no ordinary synthesiser. In addition, I have always wanted to get to grips with designing electronic schematics, which I know is a good skill to have. This led me to choose an analog synthesiser, which uses mostly analog circuitry in creative ways to result in the synthesis of sound, with a digital MIDI-CV converter, which on its own cannot be understated.

**N.B.** Please bear in mind that this repo will be updated with future development/prototyping. If this project looks incomplete or not sufficiently designed, please know that for something of this complexity, the timescales don't perfectly align with Hackclub deadlines, but for my EPQ project I still have time left in my research phase. Furthermore, the nature of DIY analog synthesisers is that no matter how much time you spend on a schematic, there will always be an element of just seeing what works on a physical prototype, so much revision and iteration will be needed. That being said, I am confident in my design as it stands right now. The most important thing is that I know get to building things to start testing which modules work. 

**Schematic**
Here is a screenshot of my current KiCad schematic. There are no PCBs required at this stage as I need to test everything on breadboards first, and I will probably just use protoboards in the end.
<img width="2173" height="1328" alt="image" src="https://github.com/user-attachments/assets/26b769ff-3d5c-474a-889f-753632b297c8" />

**3D Model**
Here are some screenshots of my current 3D model, designed in Fusion 360. 
<img width="1093" height="1187" alt="image" src="https://github.com/user-attachments/assets/87804885-43f5-4de7-a762-33fc71c14d2a" />
<img width="620" height="760" alt="image" src="https://github.com/user-attachments/assets/4d3b9568-d659-4c9c-8307-a306cf84fae9" />
<img width="921" height="920" alt="image" src="https://github.com/user-attachments/assets/42378cfe-ed59-4fa0-9f8c-8ba9d9d0718d" />
<img width="1153" height="1109" alt="image" src="https://github.com/user-attachments/assets/c5a275cc-0ff1-4e64-8c7a-bc0d187ea13d" />
<img width="1237" height="1118" alt="image" src="https://github.com/user-attachments/assets/22e2f0e7-1ab3-4253-b3ca-5731e32a25e2" />
<img width="838" height="893" alt="image" src="https://github.com/user-attachments/assets/83d68acd-0f31-4d73-9ed4-5a18abea2ac4" />
<img width="834" height="1030" alt="image" src="https://github.com/user-attachments/assets/69fa1e3e-f030-40c2-8b48-0faef1518399" />

**BOM**
Here is my BOM, in table format. If you 
[EPQ BOM.csv](https://github.com/user-attachments/files/26290612/EPQ.BOM.csv)

