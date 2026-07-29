# July 15, 2026
## Objective
Connect the MAX30102 pulse oximeter to the Arduino Nano and verify I²C communication.
---
## Hardware Used
- Arduino Nano V3
- MAX30102 (HW-605) Pulse Oximeter
- Breadboard
- Jumper Wires
---
## Wiring
VIN  → 5V
GND → GND
SDA → A4
SCL → A5
---
## Progress
- Successfully wired the MAX30102.
- Uploaded the SparkFun Basic Readings example.
- The sensor initially could not be detected.
- Used an I²C scanner to diagnose the issue.
- Initially received:
    No I2C devices found.
- After improving the mechanical connection between the sensor and breadboard:
    I2C device found at address 0x57
- Successfully confirmed communication with the sensor.
---
## Problems Encountered
The sensor made inconsistent contact with the breadboard.
---
## Solution
Pressed the breakout board firmly into the breadboard and verified communication using an I²C scanner before testing higher-level code.
---
## Lessons Learned
Debug hardware one layer at a time.
1. Verify power.
2. Verify communication.
3. Verify software.
4. Verify functionality.
The I²C scanner is one of the most useful debugging tools for embedded systems.
---
## Next Session
- Improve sensor contact.
- Run HeartRate example.
- Measure BPM.
- Understand signal quality.



# July 16, 2026
## Objective
Obtain live heart rate readings from the MAX30102 sensor.
## Completed
- Successfully wired the MAX30102 to the Arduino Nano.
- Uploaded SparkFun HeartRate example.
- Verified the sensor appears on the I²C bus at address 0x57.
- Successfully used an I²C scanner to diagnose communication.
- Confirmed the scanner only detects the sensor when physical pressure is applied to the breakout board.
## Debugging
Observed:
- "MAX30105 was not found."
- I²C scanner initially detected no devices.
- Applying pressure to the sensor caused the scanner to detect address 0x57.
- HeartRate example produced IR = 0 and "No finger?" indicating unreliable sensor communication.
Conclusion:
The issue appears to be a mechanical connection between the sensor breakout board and the breadboard rather than software or wiring.
## Next Steps
- Purchase female-to-female jumper wires.
- Eliminate the breadboard as a failure point.
- Verify stable I²C communication.
- Continue HeartRate example.



# July 20, 2026
## Objective
Connect and verify operation of the SSD1306 OLED display
---
## Hardware
- Arduino Nano
- SSD1306 OLED (128x64)
---
## Wiring
OLED GND → Nano GND
OLED VCC → Nano 5V
OLED SDA → Nano A4
OLED SCL → Nano A5
---
## Debugging
Initially the OLED remained blank
Used an I²C scanner
Scanner detected: 0x3C
The Adafruit example expected: 0x3D
Changed
#define SCREEN_ADDRESS 0x3D
to
#define SCREEN_ADDRESS 0x3C
Re-uploaded
OLED successfully displayed the graphics demo
---
## Lessons Learned
Do not assume the example code uses the correct I²C address
Always verify addresses using an I²C scanner



## July 27
### Objective:
Reconnect with the project after a short break
### Completed:
- Reviewed repository structure
- Reviewed previous debugging notes
- Began replacing the OLED demo with a custom startup screen
### Next:
Write custom OLED code and return to debugging the MAX30102



## July 28
### Objective
Create a custom startup interface for the OLED display
### Completed
- Modified the Adafruit SSD1306 example
- Created a custom startup screen
- Learned how to create and call custom functions
- Added multiple startup screens using delays
- Successfully displayed:
    - Portable Vitals Logger
    - ASU Electrical Engineering
### Lessons Learned
- Functions help organize embedded software
- I2C scanner confirmed OLED address was 0x3C
- Embedded systems often display information as a sequence of screens
### Next Steps
- Add an initialization screen
- Connect the MAX30102
- Display live sensor values



# July 29, 2026
## Objective
Integrate the MAX30102 pulse oximeter and OLED display into a single embedded system capable of displaying live sensor data
---
## Completed
- Connected the MAX30102 and OLED to the same I²C bus
- Verified both devices using the I²C scanner
  - OLED detected at address **0x3C**
  - MAX30102 detected at address **0x57**
- Combined the OLED display code with the MAX30102 Basic Readings example
- Initialized both peripherals in the same Arduino sketch
- Successfully read live Red, IR, and Green sensor values
- Displayed the live sensor values on the OLED in real time
---
## Challenges
- Learned how multiple I²C devices share the same SDA and SCL lines
- Worked through integrating two separate example programs into one sketch while keeping the code organized
---
## Lessons Learned
- Multiple I²C devices can communicate on the same bus as long as each has a unique address
- Initializing hardware in `setup()` and updating live data in `loop()` creates a clean software structure
- Separating the display logic into its own function makes the program easier to expand and maintain
---
## Next Steps
- Replace raw Red, IR, and Green values with calculated heart rate (BPM)
- Display live BPM on the OLED
- Begin integrating SpO₂ calculations into the project