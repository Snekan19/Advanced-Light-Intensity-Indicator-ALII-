# Advanced Light Intensity Indicator (ALII)

## 📌 Project Overview
The Advanced Light Intensity Indicator (ALII) is a hardware-only, analog and digital mixed-signal system designed to measure and indicate ambient light intensity.  
The system is implemented **without using any microcontroller or embedded software**.

---

## 🎯 Objectives
- Measure ambient light intensity using an LDR    
- Suppress 50 Hz mains interference using filters
- Indicate light intensity levels
- Indicate average light intensity for certain period of time 

---

## 🧩 System Architecture
The ALII system consists of the following functional stages:

1. Signal Conditioning (Active Filtering)
To mitigate 50 Hz mains interference affecting the LDR sensor, we designed a 2nd-order Sallen-Key low-pass filter with a 10 Hz cutoff frequency. This stage effectively attenuated noise by approximately 28 dB, providing a clean and reliable analog signal.

2. Quantization (Flash ADC)
We implemented a custom 3-bit Flash ADC using a parallel comparator ladder. This enabled instant conversion of the analog voltage into a digital thermometer code, mapping light intensity into 8 discrete levels (0–7) with zero conversion latency.

3. Digital Stability Logic
To eliminate display flicker caused by transient shadows, we developed a stability timer using discrete logic gates and counters. The display updates only after the light level remains stable for a predefined duration, ensuring robust and user-friendly operation.

4. Digital Averaging Logic
To obtain an average over a given time period, a timer at a specific configuration is used along with a counter, some flip-flops and 4 bit adders. 

