# ESP32_BLE_WiFi_Project
Project to broadcast temperature and humidity data over BLE and transfer WiFi credentials to connect to a network
# ESP32 BLE WiFi Project

This project demonstrates how to use an ESP32 to broadcast Bluetooth Low Energy (BLE) services for temperature and humidity measurements and transfer WiFi credentials over BLE to connect to a WiFi network.

## Features

- BLE service for temperature measurement
- BLE service for humidity measurement
- BLE service for WiFi credentials transfer
- Connects to WiFi using received credentials

## Requirements

- ESP32 development board
- Arduino IDE with ESP32 support
- BLE-enabled smartphone (for sending WiFi credentials)

## Setup

1. **Install ESP32 Board in Arduino IDE**:
    - Go to `File` > `Preferences`.
    - Add `https://dl.espressif.com/dl/package_esp32_index.json` to the Additional Board Manager URLs.
    - Go to `Tools` > `Board` > `Board Manager` and install `esp32` by Espressif Systems.

2. **Install Required Libraries**:
    - `WiFi` (comes with ESP32 package)
    - `BLEDevice` (comes with ESP32 package)

3. **Upload the Code**:
    - Open `main.cpp` in Arduino IDE.
    - Select the correct board and port.
    - Upload the sketch to the ESP32.

## Usage

1. Power the ESP32.
2. Use a BLE-enabled smartphone app (e.g., nRF Connect) to connect to the ESP32.
3. Send WiFi credentials in the format `SSID:Password` to the ESP32.
4. The ESP32 will connect to the specified WiFi network and print the IP address on the Serial Monitor.

## Additional Documentation

- [Setup Instructions](docs/setup_instructions.md)
- [Troubleshooting](docs/troubleshooting.md)

## Screenshots

![Screenshot1](screenshots/screenshot1.png)
![Screenshot2](screenshots/screenshot2.png)

## Demonstration Video

[Link to Demonstration Video](video/demonstration_video.mp4)
