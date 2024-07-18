# Setup Instructions

## Hardware Setup

1. Connect your ESP32 to your computer using a USB cable.
2. Ensure that the ESP32 is properly powered and connected.

## Software Setup

1. **Install Arduino IDE**: Download and install the Arduino IDE from the [official website](https://www.arduino.cc/en/software).

2. **Install ESP32 Board**:
    - Open Arduino IDE.
    - Go to `File` > `Preferences`.
    - Add `https://dl.espressif.com/dl/package_esp32_index.json` to the Additional Board Manager URLs.
    - Go to `Tools` > `Board` > `Board Manager`.
    - Search for `esp32` and install the `esp32` package by Espressif Systems.

3. **Install Required Libraries**:
    - The `WiFi` and `BLEDevice` libraries come with the ESP32 package.
    - No additional libraries need to be installed manually.

4. **Upload the Sketch**:
    - Open `main.cpp` in the Arduino IDE.
    - Select the correct ESP32 board and port from the `Tools` menu.
    - Click on the upload button to upload the sketch to the ESP32.

## Connecting to WiFi

1. Open a BLE-enabled smartphone app (e.g., nRF Connect).
2. Scan for BLE devices and connect to `ESP32_BLE`.
3. Send the WiFi credentials in the format `SSID:Password` to the ESP32.
4. The ESP32 will connect to the specified WiFi network and print the IP address on the Serial Monitor.
