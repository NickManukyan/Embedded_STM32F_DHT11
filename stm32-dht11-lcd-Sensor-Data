#include <Wire.h>                   // I2C communication
#include <LiquidCrystal_I2C.h>       // I2C LCD library
#include <DHT.h>                     // DHT sensor library

#define SENSOR_PIN PA1
#define SENSOR_TYPE DHT11

LiquidCrystal_I2C display(0x27, 16, 2);  // Create an LCD object with I2C address 0x27 for 
DHT dhtSensor(SENSOR_PIN, SENSOR_TYPE);  // Create a DHT sensor object

void initializeLCD() {
  display.begin();
  display.backlight();
  display.setCursor(0, 0);
  display.print("STM32 WEATHER");
  display.setCursor(0, 1);
  display.print("Initializing...");
  delay(2000);
  display.clear();
}

void setup() {
  dhtSensor.begin();
  initializeLCD();
}

void loop() {
  float humidity = dhtSensor.readHumidity();
  float temperature = dhtSensor.readTemperature();

  display.setCursor(0, 0);
  display.print("Temp: ");
  display.print(temperature, 1);   // 1 decimal place
  display.print(" C");

  display.setCursor(0, 1);
  display.print("Humidity: ");
  display.print(humidity, 0);      // No decimal place
  display.print("%");

  delay(1000);  // Small delay for readability
}
