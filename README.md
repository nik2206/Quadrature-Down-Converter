# Quadrature Down Converter - RF Signal Processing

## Overview

A Quadrature Down Converter (QDC) circuit that converts high-frequency RF signals to low-frequency baseband signals using I/Q demodulation. This project demonstrates analog circuit design, RF signal processing, and wireless communication fundamentals with complete LTSpice simulations and hardware validation.

Key Highlights:
- I/Q signal decomposition with 95.36% phase accuracy
- Three-stage system: oscillator, mixer, and low-pass filter
- TSMC 180nm and UA741 op-amp models
- Simulation and hardware validation

## Team Members

| Name | Roll Number | Email |
|------|-------------|-------|
| Nagamalla Sai Abhinav | 2024102037 | saiabhinav.nagamalla@students.iiit.ac.in |
| Abhinav Venkata Kota | 2024102059 | abhinav.kota@students.iiit.ac.in |
| Nikhil Venkat Atkuru | 2024102039 | nikhil.atkuru@students.iiit.ac.in |

## System Architecture

### Three Main Components

1. Quadrature Oscillator (100 kHz)
   - Three-stage op-amp circuit with automatic gain control (AGC)
   - Generates I and Q signals with 90-degree phase difference
   - Achieved frequency: 100 kHz, phase accuracy: 95.36 degrees
   - Components: UA741 op-amp (±15V), RC networks (1.3 kOhm, 1 nF), diodes for AGC

2. NMOS Mixer
   - NMOS transistor operating in linear region for signal multiplication
   - Multiplies input RF signal with oscillator signals
   - Coupling capacitor: 100 pF, Load resistance: 1 kOhm
   - Threshold voltage: 0.57 V (from TSMC 180nm models)
   - Produces difference frequency (desired) and sum frequency (filtered out)

3. Low-Pass Filter (2 kHz cutoff)
   - Simple RC passive filter (R = 1.3 kOhm, C = 61 nF)
   - Removes high-frequency noise and sum frequency components
   - Passband flatness: ±0.5 dB (DC to 1.5 kHz)
   - Stopband attenuation: -40 dB/decade rolloff

### System Function

The circuit processes RF signals through:
- Input RF signal multiplied by quadrature oscillator outputs
- Mixer produces sum and difference frequency components
- LPF attenuates sum frequencies, passes difference frequency
- Output: Clean I and Q baseband signals for further processing

## Technology & Models

TSMC 180nm Process:
- NMOS and PMOS transistor models with detailed parameters
- Threshold voltage: 0.38 V (NMOS), -0.39 V (PMOS)
- Operating temperature: 27 degrees Celsius

UA741 Op-Amp:
- Legacy op-amp for educational purposes
- Gain-bandwidth product: 1 MHz
- Complete SPICE macromodel implementation

## Key Results

Oscillator Performance:
- Frequency: 100 kHz with 0.1% accuracy
- Phase difference: 95.36 degrees (close to ideal 90 degrees)
- Output amplitude: 1 Vp-p
- Stable sinusoidal outputs verified

Mixer Performance:
- Tested input frequencies: 95 kHz to 105 kHz
- Successful frequency down-conversion confirmed
- Image rejection: >40 dB

Filter Performance:
- Cutoff frequency: 2 kHz (-3dB point)
- Passband flatness: ±0.5 dB
- Stopband attenuation: -40 dB/decade rolloff

## Applications

This design applies to:
- Software-defined radio (SDR) systems
- Bluetooth and Wi-Fi receivers
- Phase measurement and signal detection
- Frequency estimation and lock-in amplifiers

## Repository Structure

```
Quadrature-Down-Converter/
├── LTSpice Schematics/           # Circuit designs and simulations
│   ├── Quadrature_Oscillator.asc # 100 kHz oscillator with AGC
│   ├── MIXER_AEC_PROJECT.asc     # NMOS mixer implementation
│   ├── MIXER+LPF_AEC_PROJECT.asc # Integrated mixer + filter
│   └── FINAL.asc                 # Complete QDC system
│
├── Resources/                    # Reference documentation and papers
│   ├── 1_Direct-conversion_radio_transceivers_for_digital_communications.pdf
│   ├── 2_TI_opamp_osc.pdf
│   ├── 3_A_simple_wide-band_sine_wave_quadrature_oscillator.pdf
│   └── ua741.pdf
│
├── TSMC_180nm.txt               # TSMC 180nm MOSFET models (NMOS/PMOS)
├── UA741.301                    # UA741 op-amp SPICE macromodel
├── Problem Statement.pdf        # Design specifications and requirements
├── Report.pdf                   # Comprehensive technical report
├── Mid Eval PPT.pdf             # Project progress presentation
└── README.md                    # This file
```

Description of Files and Directories:

LTSpice Schematics/:
Contains all circuit designs in LTSpice native format (.asc files). Start with individual component schematics, then progress to the integrated FINAL design for the complete system.

TSMC_180nm.txt:
SPICE model definitions for NMOS (CMOSN) and PMOS (CMOSP) transistors based on TSMC 180nm process. Includes device parameters like threshold voltage, mobility, and parasitic capacitances essential for accurate transistor-level simulation.

UA741.301:
Historical op-amp design with complete SPICE subcircuit implementation. Defines the three-stage operational amplifier including input differential pair, gain stage, and output buffer.

Resources/:
Academic and industry references covering:
- RF receiver architectures and I/Q demodulation theory
- Op-amp oscillator design and compensation
- Practical quadrature oscillator implementations
- Op-amp datasheets and application notes

Documentation Files:
- Report.pdf: Full technical report with design details and results
- Problem Statement.pdf: Original design specifications
- Mid Eval PPT.pdf: Design progress and methodology presentation

This project demonstrates proficiency in analog circuit design, RF signal processing fundamentals, SPICE simulation methodology, and practical implementation of advanced wireless communication techniques.
