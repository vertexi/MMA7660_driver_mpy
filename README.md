# MMA7660 Accelerometer Driver for Micropython

This is a driver for MicroPython to handle cheap and very low power 3-Axis Orientation/Motion
Detection Sensor based on MMA7660 chip.

This library supports:

- get 3-Axis row accelerometer data
- get 3-Axis acceleration converted by row data
- get 3-Axis angle converted by row data

## Example

```python
from machine import Pin, I2C
import mma7660
import utime

i2c = I2C(1, scl=Pin(11), sda=Pin(10), freq=400000)
print(i2c)
accel = mma7660.Accelerometer(i2c)
while True:
    print(accel.getXYZ(), accel.get_x(), accel.get_y(), accel.get_z())
    print(accel.getAcceleration(),
          accel.getAcceleration_x(),
          accel.getAcceleration_y(),
          accel.getAcceleration_z())
    print(accel.getAngle())
    utime.sleep_ms(500)
```

The above code uses `pin 11` as SCL pin and `pin 10` as SDA pin, to communicate
with MMA7660 chip, and then get the 3-Axis data by I2C.

## Todo

- [ ] Tap detection
- [ ] Interrupts
- [ ] Auto sleep/wake mode settings

