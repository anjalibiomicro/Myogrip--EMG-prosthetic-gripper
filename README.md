# EMG-Controlled Servo Prosthetic Hand

An Arduino-based EMG (Electromyography) signal processing system designed to control a servo motor (e.g., for a prosthetic hand or robotic gripper) using muscle activity.

This project reads raw muscle signals from an analog EMG sensor, passes them through a digital bandpass/notch filter chain, extracts the signal envelope, and uses hysteresis-thresholding to actuate a servo motor smoothly without flicker.

## Features

- **Sampling Rate:** Precise 500 Hz sampling loop using `micros()`.
- **Digital Signal Processing:** 4-stage IIR Biquad filter chain to remove noise and powerline interference from raw EMG data.
- **Envelope Detection:** Moving average circular buffer filter for smooth signal rectifying and envelope calculation.
- **Hysteresis Thresholding:** Dual-threshold control logic (`CLOSE_THRESHOLD` vs `OPEN_THRESHOLD`) to prevent servo jittering/flicker at transition points.
- **Serial Telemetry:** Outputs raw processed envelope and state data for real-time visualization via Arduino Serial Plotter.

## Hardware Requirements

| Component | Quantity | Description / Pin Assignment |
| :--- | :---: | :--- |
| **Arduino Board** | 1 | UNO, Nano, or Mega |
| **EMG Sensor Kit** | 1 | MyoWare, BioAmp, or similar analog EMG sensor on **A0** |
| **Servo Motor** | 1 | Standard/Micro Servo (e.g., SG90, MG996R) on **Pin 10** |
| **External Power Supply** | 1 | 5V DC supply for the servo motor (shared ground with Arduino) |
| **Surface Electrodes** | 3 | Ag/AgCl Gel Electrodes for muscle signal acquisition |

## Hardware Connections

| Component Pin | Arduino Pin | Notes |
| :--- | :--- | :--- |
| **EMG Signal Out** | `A0` | Analog Input Pin |
| **Servo Signal Wire** | `Pin 10` | Digital PWM Output |
| **GND (Shared)** | `GND` | Common Ground for Sensor
