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
2. Compile:
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
Test: gestures-large-f32
Iterations: 10
Total time: 53 ms.
Time per inference: 5389 us.
Test: gestures-large-i8
Iterations: 10
Total time: 29 ms.
Time per inference: 2972 us.
Test: image-32-32-mobilenet-f32
Iterations: 10
Total time: 3685 ms.
Time per inference: 368516 us.
Test: image-32-32-mobilenet-i8
Iterations: 10
Total time: 4220 ms.
Time per inference: 422011 us.
Test: keywords-2d-f32
Iterations: 10
Total time: 1704 ms.
Time per inference: 170413 us.
Test: keywords-2d-i8
Iterations: 10
Total time: 1932 ms.
Time per inference: 193244 us.
DSP MIPS is 33
{
    "gestures-large-f32": 5.389000,
    "gestures-large-i8": 2.972000,
    "image-32-32-mobilenet-f32": 368.515991,
    "image-32-32-mobilenet-i8": 422.010986,
    "keywords-2d-f32": 170.412994,
    "keywords-2d-i8": 193.244003
}
```
Did not run:
MOBILENET_96_96_F32
MOBILENET_96_96_I8
MOBILENET_320_320_F32 