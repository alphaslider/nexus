NEXUS: Web-Based Modular Sequencer and Acid Engine
Overview
NEXUS is a high-performance, zero-dependency step sequencer and synthesizer built entirely with the Web Audio API. It integrates subtractive synthesis, physical modeling for percussion, and a dedicated Acid emulation engine within a unified 16-step grid architecture. By utilizing vanilla JavaScript for both the audio graph and the sequencing logic, NEXUS provides a low-latency environment for real-time electronic music production directly in the browser.

Core Technical Specifications
1. Synthesis Engines
Beep Engine: A monophonic voltage-controlled oscillator (VCO) supporting Sine, Sawtooth, Square, and Triangle waveforms. It features an exponential decay envelope and adjustable portamento (glide) for melodic sequencing.

Acid Engine (303 Emulation): A specialized signal path consisting of a resonant 24dB/octave-style low-pass filter and a dedicated WaveShaper distortion node. The filter features a synchronized envelope sweep triggered on every note event.

Percussion Engine: * Kick: Frequency-swept sine wave with a Rotterdam-style distortion toggle.

Snare/Snap: Combined oscillator body with a high-pass filtered white noise burst.

Hi-Hats: Noise-based generators with high-pass filtering and variable ratcheting logic.

Sampler: Multi-slot sampler with per-step low-pass filtering, pitch-shifting via playback rate manipulation, and choke-group logic.

2. Sequencer Architecture
Grid: 16-step resolution with multi-bank support (8 banks total).

Timing: High-precision scheduling using the Web Audio API clock to prevent drift associated with standard JavaScript timers.

Arranger Mode: A song-mode interface allowing for the chaining of patterns into structured compositions.

Generative Logic: Per-track "Auto" modes that utilize weighted randomization algorithms to evolve patterns in real-time.

3. Signal Processing and FX Rack
Tape Echo: A feedback delay line with an integrated band-pass filter to simulate vintage magnetic tape saturation and frequency loss.

Impulse Response Reverb: Dual convolver nodes providing spatial depth for both the synth engine and sampler tracks.

Master Dynamics: A final-stage WaveShaper for global harmonic saturation and an AnalyserNode for real-time peak monitoring.

Installation and Usage
Prerequisites
A modern web browser with Web Audio API support (Chrome 70+, Firefox 75+, or Safari 14.1+).

Deployment
Clone the repository.

Open index.html in a web browser.

Click the Power button to initialize the AudioContext.

Project Structure
Audio Engine: Handles the creation of oscillators, gain stages, and the routing of the master FX chain.

Scheduler: Manages the tick() function, calculating step timing based on the user-defined BPM.

UI/UX: A hardware-inspired dark interface optimized for high-contrast visibility and low CPU overhead.

Technical Challenges Solved
Sample-Accurate Timing: Overcoming the limitations of setTimeout by scheduling audio events ahead of time using AudioContext.currentTime.

Efficient Waveform Generation: Generating percussion transients through math-based noise buffers rather than external audio files to reduce initial load times.

Dynamic Routing: Implementing a cross-fading reverb send system that maintains signal phase and gain staging across multiple tracks.
