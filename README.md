# ASIC-Binary-Phase-Shift-Key-Decoder

Project Overview

This repository contains the implementation of an ASIC Binary Phase Shift Key (BPSK) Decoder, developed as part of a group project. The decoder is designed to process incoming BPSK modulated signals and decode them into binary data. My primary contribution to this project was designing the Costas Loop for phase correction and the Match Filter for synchronization detection.

Key Components

1. Costas Loop Implementation

The Costas Loop is used to demodulate the incoming BPSK signal by performing phase error correction. My specific contributions to this part include:

Implemented two FIR filters using shift registers, with coefficients provided by the professor.
Developed a Numerically Controlled Oscillator (NCO) using an accumulator to produce sine and cosine waveforms.
The incoming BPSK signal is multiplied by the NCO output (sine and cosine waveforms) to correct phase errors.

2. Match Filter Design for Synchronization
After the Costas Loop, the Match Filter detects synchronization by continuously monitoring the cosine filter output. Key features include:

Continuously sums the cosine filter output over 500 samples.
The sum is compared against a predefined threshold value to detect the synchronization signal.
Upon synchronization, 250 samples are collected (at a rate of 2.5 bits/cycle).
Concatenates 10 bits from the 250 collected samples and sends them to the decoder for final processing.

Workflow

Incoming BPSK signal is processed through the Costas Loop for phase correction.
The Match Filter detects synchronization and prepares the data for decoding.
The system concatenates and forwards the decoded bits for further processing.
