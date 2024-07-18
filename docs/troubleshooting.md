# Troubleshooting

## Common Issues

### Unable to Connect to BLE

- **Check Bluetooth Settings**:
  - Ensure your smartphone's Bluetooth is turned on.
  - Confirm that the ESP32 is powered and running the sketch.

- **Restart Devices**:
  - Restart the ESP32 and your smartphone, then try connecting again.

### WiFi Connection Failed

- **Verify Credentials**:
  - Double-check the WiFi credentials format: `SSID:Password`.
  - Ensure that both SSID and password are correct and match your network settings.

- **Check Network Availability**:
  - Make sure the WiFi network is in range and broadcasting.
  - Verify that the ESP32 is within the WiFi network's range.

### Serial Monitor Issues

- **Check Port and Baud Rate**:
  - Ensure the correct port is selected in the Arduino IDE.
  - Set the Serial Monitor to the correct baud rate (115200).

- **Connection Issues**:
  - Confirm that the ESP32 is properly connected to your computer.
  - Ensure that the USB cable is working and properly connected.

## Debugging Tips

- **Add Debugging Statements**:
  - Insert additional `Serial.println` statements in your code to track the execution flow and identify issues.

- **Monitor Serial Output**:
  - Use the Serial Monitor to view real-time debug information and determine where the problem might be occurring.
