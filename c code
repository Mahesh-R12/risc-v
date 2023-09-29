#include <Arduino.h>
#include <DHT.h>
#include <Wire.h>
#include <Adafruit_BMP085.h>

// Sensor pins
#define DHTPIN 2           // Pin for DHT22 sensor
#define RAINPIN A0         // Rain sensor analog pin
#define BMP085_ADDRESS 0x77 // I2C address for BMP085 pressure sensor

// DHT sensor configuration
DHT dht(DHTPIN, DHT22);

// Create BMP085 sensor object
Adafruit_BMP085 bmp;

void setup() {
  Serial.begin(9600);
  delay(1000);

  // Initialize sensors
  dht.begin();
  Wire.begin();
  if (!bmp.begin(BMP085_ADDRESS)) {
    Serial.println("Could not find a valid BMP085 sensor, check wiring!");
    while (1);
  }
}

void loop() {
  // Read sensor data
  float temperature = dht.readTemperature();
  float humidity = dht.readHumidity();
  int rainValue = analogRead(RAINPIN);
  float pressure = bmp.readPressure() / 100.0; // hPa

  // Print sensor data
  Serial.print("Temperature (°C): ");
  Serial.println(temperature);
  Serial.print("Humidity (%): ");
  Serial.println(humidity);
  Serial.print("Rain Value: ");
  Serial.println(rainValue);
  Serial.print("Pressure (hPa): ");
  Serial.println(pressure);

  // Add code here to send data to a server, display it on an OLED screen, or store it as needed

  delay(60000); // Delay for 1 minute before taking the next reading
}
