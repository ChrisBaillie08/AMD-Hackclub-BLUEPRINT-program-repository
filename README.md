# AMD-Hackclub-BLUEPRINT-program-repository

This project is a DIY analog synthesiser that I have designed from scratch as an EPQ project. It is a dual oscillator monophonic synthesiser with entirely analog signal processing.
A RP Pico and DAC is used to convert MIDI data into control voltages for velocity and pitch.

The synthesiser includes an analog velocity sensitive envelope, using mathematical models of how real world piano tones behave to model the relationship between note velocity and max amplitude, attack time, decay time and release time.

Additional features include a LFO with sineshaper, two oscillators, a powerful 4 pole VCF and a digital transposition section, which allows each oscillator to be tuned up and down in semitone increments.

