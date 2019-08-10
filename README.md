# micropython-si1132
Micropython I2C driver for Silabs Si1132 - UV index and ambient light sensor

### how to use this library
I'm using it with ESP8266 µC, to read values I need to connect sensor over I2C to the ESP's GPIO.
I connected SDA to GPIO13 and SCL to GPIO12 (you may use any other I2C capable GPIOs) then used this code to read values:

``` python
import machine
import si1132

i2c = machine.I2C(scl=machine.Pin(12), sda=machine.Pin(13))
si = si1132.SI1132(i2c)

print("Visible light:", si.read_visible())
print("UV index:", si.read_UV())
print("IR:", si.read_IR())

```

Visible light seems to be expressed in LUXes, UV index is just an UV index and I've not tested unit of IR.
