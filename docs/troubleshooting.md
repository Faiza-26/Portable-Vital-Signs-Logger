# Troubleshooting
## Problem
MAX30102 not detected

## Tool Used
I²C Scanner

## Result
Initially: No I²C devices found.
After applying pressure: Device detected at address 0x57.

## Lesson
Always isolate hardware problems before assuming software is incorrect.


## July 29
### Problem
Needed to use the OLED and MAX30102 simultaneously
### Solution
Connected both devices to the same SDA and SCL lines
Verified communication using the I²C scanner
Detected:
- OLED: 0x3C
- MAX30102: 0x57

Successfully displayed live sensor values on the OLED