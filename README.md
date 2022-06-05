# Profiling firmware for ESP32

## Requirements

### Hardware

* [ESP-EYE](https://www.espressif.com/en/products/devkits/esp-eye/overview).

While the script is mainly tested with ESP-EYE, other ESP32-based development boards will work too.

### Software

* [ESP IDF 4.4](https://docs.espressif.com/projects/esp-idf/en/v4.4/esp32/get-started/index.html).


## Building the application

### Compile

1. Initialize ESP IDF:
   ```bash
   get_idf
   ```
2. Switch to ESP32-C3:
```
idf.py set-target esp32c3 
```
3. Compile:
   ```bash
   idf.py build
   ```

### Flash

Connect the ESP32 board to your computer.

Run:
   ```bash
   idf.py -p /dev/ttyUSB0 flash monitor
   ```

Where ```/dev/ttyUSB0``` needs to be changed to actual port where ESP32 is connected on your system.

### Serial connection

Use screen, minicom or Serial monitor in Arduino IDE to set up a serial connection over USB. The following UART settings are used: 115200 baud, 8N1.


Results without ESP-NN:
```
Starting...
Test: gestures-large-i8
Iterations: 10
Total time: 10 ms.
Time per inference: 1048 us.

Test: image-32-32-mobilenet-i8
Iterations: 10
Total time: 1316 ms.
Time per inference: 131657 us.

Test: keywords-2d-i8
Iterations: 10
Total time: 577 ms.
Time per inference: 57746 us.

DSP MIPS is 10

{
    "gestures-large-i8": 1.048000,
    "image-32-32-mobilenet-i8": 131.656998,
    "keywords-2d-i8": 57.745998
}
```