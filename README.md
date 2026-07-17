# Doppler Radar-Based Vital Sign Monitoring System

## Overview
A contactless heart rate (BPM) monitoring system using a Doppler radar sensor, 
combining embedded signal acquisition, FPGA-based real-time indication, and 
offline DSP analysis to extract vital sign data without physical contact 
with the subject.

## Key Features
- Contactless detection of heart rate using microwave Doppler radar
- Real-time signal acquisition via Arduino
- FPGA-based real-time visual feedback (LED) using Tang Nano 9K, reflecting 
  live heartbeat signal activity
- FFT-based frequency analysis in Python to extract BPM from raw radar signal

## Hardware/Components Used
- HB100 Doppler Radar Module (10.525 GHz microwave motion sensor)
- Arduino Uno (signal acquisition/preprocessing)
- Tang Nano 9K FPGA (Gowin GW1NR-9) — drives an LED indicator in real time, 
  giving instant visual feedback of detected heartbeat signal alongside the 
  offline BPM calculation

## How It Works
1. The HB100 radar emits a continuous microwave signal and detects the 
   Doppler shift caused by chest wall movement from heartbeat
2. The raw analog signal is captured by the Arduino
3. The Tang Nano 9K FPGA processes the live signal and drives an LED to 
   blink/light up in sync with detected heartbeat activity — giving real-time 
   visual confirmation the system is sensing a pulse
4. In parallel, the signal is logged and passed to a Python script for 
   offline analysis
5. FFT (Fast Fourier Transform) is applied to isolate the frequency 
   component corresponding to heart rate
6. The dominant frequency peak in the BPM range is converted to beats-per-minute

## Challenges & Solutions
- **False peaks**: The raw radar signal occasionally produced false peaks 
  in the FFT output, likely from minor body movement or ambient noise. 
  Addressed by narrowing the frequency band of interest to the 
  physiologically expected BPM range before picking the peak.
- **Calibration**: Sensor sensitivity and positioning required manual 
  calibration to get a usable signal — subject distance and radar alignment 
  significantly affected signal quality, so a consistent test setup was 
  needed for reliable readings.

## Results/Demo
See `/media` folder for photos and video of the working system.
BPM detection validated against manual pulse count.

## Future Improvements
- Add automated peak-detection thresholding to reduce false positives
- Extend to breathing rate detection alongside heart rate
- Move more signal processing on-chip (FPGA) for full real-time output
- Formal accuracy validation against a pulse oximeter

## Tech Stack
- Hardware: HB100 Radar, Arduino Uno, Tang Nano 9K FPGA
- Languages: Arduino C/C++, Verilog (FPGA LED logic), Python (FFT/signal analysis)
- Libraries: NumPy/SciPy (FFT), matplotlib (visualization)

## Note
Original source code from this project was lost due to a system reset. 
Photos and video documentation of the working system are included below.
