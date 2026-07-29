# Portable Vital Signs Logger
An Arduino-based embedded systems project that measures heart rate and blood oxygen using a MAX30102 sensor, displays the data on an OLED display, logs readings to an SD card, and analyzes the data using Python.

### Hardware
- ✅ Arduino Nano
- ✅ SSD1306 OLED Display
- ✅ MAX30102 Pulse Oximeter
- ✅ Shared I²C Bus Configured

### Software
- ✅ Custom startup interface
- ✅ Multi-screen OLED interface
- ✅ Live sensor communication
- ✅ Real-time Red, IR, and Green values displayed

## Current Prototype
The current prototype integrates an Arduino Nano, SSD1306 OLED display, and MAX30102 optical sensor over a shared I²C bus. The system initializes through a custom startup interface before displaying live Red, IR, and Green sensor readings in real time
![OLED Live Sensor](images/fullrun1_wiring.jpg)

### In Progress
- ⏳ Heart rate (BPM) calculation
- ⏳ SpO₂ calculation

### Future Features
- ⬜ SD card logging
- ⬜ Python data visualization
- ⬜ Wearable enclosure