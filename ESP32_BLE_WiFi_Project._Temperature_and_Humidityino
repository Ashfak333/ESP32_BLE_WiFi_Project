#include <BLEDevice.h>
#include <BLEUtils.h>
#include <BLEServer.h>
#include <WiFi.h>

// BLE UUIDs
#define SERVICE_UUID            "00000002-0000-0000-FDFD-FDFDFDFDFDFD"
#define CHARACTERISTIC_TEMP     "00002A1C-0000-1000-8000-00805F9B34FB" // Example UUID for Temperature
#define CHARACTERISTIC_HUM      "00002A6F-0000-1000-8000-00805F9B34FB" // Example UUID for Humidity
#define WIFI_SERVICE_UUID       "00000003-0000-0000-FDFD-FDFDFDFDFDFD"
#define WIFI_CRED_CHARACTERISTIC "00003A01-0000-1000-8000-00805F9B34FB" // Custom UUID for WiFi credentials

// Global variables
BLECharacteristic *pCharacteristicTemp;
BLECharacteristic *pCharacteristicHum;
BLECharacteristic *pWiFiCredCharacteristic;
bool newCredentials = false;
String ssid;
String password;

// Callback to handle received WiFi credentials
class WiFiCredsCallbacks: public BLECharacteristicCallbacks {
  void onWrite(BLECharacteristic *pCharacteristic) {
    std::string value = pCharacteristic->getValue();
    size_t separator = value.find(":");
    if (separator != std::string::npos) {
      ssid = value.substr(0, separator).c_str();
      password = value.substr(separator + 1).c_str();
      newCredentials = true;
      Serial.println("Received new WiFi credentials:");
      Serial.println("SSID: " + ssid);
      Serial.println("Password: " + password);
    }
  }
};

void setup() {
  Serial.begin(115200);
  BLEDevice::init("ESP32_BLE");

  BLEServer *pServer = BLEDevice::createServer();

  // Temperature and Humidity Service
  BLEService *pService = pServer->createService(SERVICE_UUID);

  pCharacteristicTemp = pService->createCharacteristic(
                          CHARACTERISTIC_TEMP,
                          BLECharacteristic::PROPERTY_READ |
                          BLECharacteristic::PROPERTY_NOTIFY
                        );

  pCharacteristicHum = pService->createCharacteristic(
                         CHARACTERISTIC_HUM,
                         BLECharacteristic::PROPERTY_READ |
                         BLECharacteristic::PROPERTY_NOTIFY
                       );

  pService->start();

  // WiFi Credentials Service
  BLEService *pWiFiService = pServer->createService(WIFI_SERVICE_UUID);
  pWiFiCredCharacteristic = pWiFiService->createCharacteristic(
                             WIFI_CRED_CHARACTERISTIC,
                             BLECharacteristic::PROPERTY_WRITE
                           );
  pWiFiCredCharacteristic->setCallbacks(new WiFiCredsCallbacks());
  pWiFiService->start();

  // Start advertising
  BLEAdvertising *pAdvertising = BLEDevice::getAdvertising();
  pAdvertising->addServiceUUID(SERVICE_UUID);
  pAdvertising->addServiceUUID(WIFI_SERVICE_UUID);
  pAdvertising->start();
}

void loop() {
  // Simulate sensor data
  float temperature = 25.0 + random(-500, 500) / 100.0;
  float humidity = 50.0 + random(-200, 200) / 100.0;

  // Convert to string
  char tempStr[8];
  dtostrf(temperature, 1, 2, tempStr);
  char humStr[8];
  dtostrf(humidity, 1, 2, humStr);

  // Set value and notify
  pCharacteristicTemp->setValue(tempStr);
  pCharacteristicTemp->notify();

  pCharacteristicHum->setValue(humStr);
  pCharacteristicHum->notify();

  delay(10000); // Update every 10 seconds

  // Check for new WiFi credentials
  if (newCredentials) {
    newCredentials = false;
    Serial.println("Connecting to WiFi...");
    WiFi.begin(ssid.c_str(), password.c_str());

    while (WiFi.status() != WL_CONNECTED) {
      delay(1000);
      Serial.println("Connecting...");
    }
    Serial.println("Connected to WiFi");
    Serial.println("IP address: ");
    Serial.println(WiFi.localIP());
  }
}

