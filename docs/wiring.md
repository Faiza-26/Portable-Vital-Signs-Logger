## I²C Connections

| Arduino Nano | OLED | MAX30102 |
|--------------|------|----------|
| 5V | VCC | VIN |
| GND | GND | GND |
| A4 (SDA) | SDA | SDA |
| A5 (SCL) | SCL | SCL |

Both peripherals share the same I²C bus.

OLED Address: 0x3C

MAX30102 Address: 0x57