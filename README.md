from machine import Pin
import time

sensor = Pin(4, Pin.IN)
led = Pin(2, Pin.OUT)

def blink_led(interval, blink_count):
    for _ in range(blink_count):
        led.value(1)
        time.sleep(0.1)
        led.value(0)
        time.sleep(0.1)
    time.sleep(interval)

while True:
    if sensor.value() == 0:
        led.value(1)
        time.sleep(60)
        led.value(0)
    else:
        liquid_level = 100

        if liquid_level >= 100:
            blink_led(0.2, 5)
        elif liquid_level >= 95:
            blink_led(0.5, 2)
        elif liquid_level >= 90:
            blink_led(1, 1)
        elif liquid_level >= 80:
            blink_led(3, 1)
        elif liquid_level >= 70:
            blink_led(5, 1)
        elif liquid_level >= 60:
            blink_led(8, 1)
        elif liquid_level >= 50:
            blink_led(10, 1)
        elif liquid_level >= 40:
            blink_led(15, 1)
        elif liquid_level >= 30:
            blink_led(30, 1)
        elif liquid_level >= 20:
            blink_led(60, 1)

    time.sleep(1)
