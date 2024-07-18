# Troubleshooting

## Common Issues

### Unable to Connect to BLE

- Ensure that your smartphone's Bluetooth is enabled.
- Make sure the ESP32 is powered and the sketch is running.
- Restart the ESP32 and try connecting again.

### WiFi Connection Failed

- Double-check the format of the WiFi credentials: `SSID:Password`.
- Ensure that the SSID and password are correct.
- Check if the WiFi network is in range.
- Verify that the ESP32 is within the WiFi network's range.

### Serial Monitor Not Displaying Output

- Ensure that the correct port is selected in the Arduino IDE.
- Check the baud rate setting in the Serial Monitor (should be 115200).
- Ensure that the ESP32 is properly connected to the computer.

## Debugging Tips

- Add more `Serial.println` statements in the code to track the program flow.
- Use the Serial Monitor to view the debug output and identify where the problem occurs.
