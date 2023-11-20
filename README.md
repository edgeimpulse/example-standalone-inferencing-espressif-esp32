# Edge Impulse Example: standalone inferencing (Espressif ESP32)

This repository runs an exported impulse on the Espressif ESP32. See the documentation at [Running your impulse locally](https://docs.edgeimpulse.com/docs/running-your-impulse-locally-1).

## Requirements

### Hardware

* [ESP-EYE](https://www.espressif.com/en/products/devkits/esp-eye/overview).

While the script is mainly tested with ESP-EYE, other ESP32-based development boards will work too.

### Software

* [Edge Impulse CLI](https://docs.edgeimpulse.com/docs/cli-installation).

* [ESP IDF 5.1.1](https://docs.espressif.com/projects/esp-idf/en/v5.1.1/esp32/get-started/index.html).


## Building the application

### Get the Edge Impulse SDK

Unzip the deployed `C++ library` from your Edge Impulse project and copy only the folders to the root directory of this repository:

   ```
   example-standalone-inferencing-espressif-esp32/
   ├─ edge-impulse-sdk
   ├─ model-parameters
   ├─ main
   ├─ tflite-model
   ├─ .gitignore
   ├─ CMakeLists.txt
   ├─ LICENSE
   ├─ README.md
   ├─ sdkconfig
   ├─ sdkconfig.old
   └─ partitions.csv
   ```

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

### Troubleshooting and optimization

When switching boards or upgrading to newer version of SDK, the `sdkconfig` file in the project folder gets overwritten. Run `idf.py menuconfig` to enter configuration menu and make sure that all the relevant performance settings (e.g. Flash SPI speed (80 MHz), CPU Frequency (240 MHz), CONFIG_COMPILER_OPTIMIZATION_PERF=y) are set.
