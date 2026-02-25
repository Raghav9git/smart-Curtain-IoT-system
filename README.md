# Smart Curtain IoT System using Arduino, Sensors and Bluetooth

## Overview

This project implements a Smart Curtain Automation System using Arduino. The curtain is controlled automatically based on environmental conditions and can also be manually controlled using a mobile application via Bluetooth.

The system integrates multiple sensors including a photoresistor (LDR), infrared sensor, and DHT11 temperature-humidity sensors to make intelligent decisions for opening and closing the curtain.

---

## Features

- Automatic curtain control based on light intensity
- Motion-based curtain opening using IR sensor
- Temperature and humidity-based environmental control
- Manual control via Bluetooth mobile application
- Servo motor-based curtain actuation
- Real-time temperature and humidity transmission to mobile device
- Multi-sensor decision logic using unified control flag

---

## Technologies Used

- Arduino Uno
- Servo Motor
- DHT11 Temperature and Humidity Sensors (Indoor & Outdoor)
- Photoresistor (LDR)
- Infrared Motion Sensor
- HC-05 / HC-06 Bluetooth Module
- Arduino IDE (C++)
- SoftwareSerial Library

---

## Hardware Components

- Arduino Uno
- Servo Motor (connected to pin 4)
- IR Sensor (connected to pin 7)
- Photoresistor (connected to A0)
- DHT11 Sensor (Indoor - pin 9)
- DHT11 Sensor (Outdoor - pin 11)
- Bluetooth Module (RX - pin 10, TX - pin 11)
- External Power Supply (if required)

---

## Working Principle

The system evaluates multiple sensor inputs and determines whether the curtain should be opened or closed.

A boolean variable `openCurtain` is used to avoid conflicting sensor outputs and ensure clean decision logic.

1. Light Detection (Photoresistor)
   - If light intensity > threshold (bright environment), curtain opens.
   - If light intensity < threshold (dark environment), curtain closes.

2. Motion Detection (IR Sensor)
   - If motion is detected, curtain opens.

3. Indoor Temperature and Humidity
   - If temperature > 26°C, curtain opens.
   - If humidity < 30% (dry conditions), curtain opens.
   - If temperature > 26°C and humidity > 60%, curtain opens.

4. Manual Control via Bluetooth
   - Send "o" to open curtain.
   - Send "c" to close curtain.
   - Send angle value (0–180) to set servo position manually.

5. Outdoor Temperature and Humidity Monitoring
   - Outdoor DHT11 sensor data is transmitted to the mobile device via Bluetooth.

---

## System Logic Flow

- Read all sensor values
- Evaluate conditions
- Set boolean flag `openCurtain`
- Apply final decision to servo motor
- Transmit environmental data via Bluetooth

This structure prevents chaotic servo behavior caused by multiple sensors triggering simultaneously.

---

## Pin Configuration

- Servo Motor → Pin 4
- IR Sensor → Pin 7
- Photoresistor → A0
- DHT11 (Indoor) → Pin 9
- DHT11 (Outdoor) → Pin 11
- Bluetooth RX → Pin 10
- Bluetooth TX → Pin 11

---

## How to Run

1. Install required libraries in Arduino IDE:
   - Servo.h
   - DHT.h
   - SoftwareSerial.h

2. Connect hardware according to pin configuration.

3. Upload the code to Arduino.

4. Connect Bluetooth module to mobile device.

5. Use mobile app to:
   - Open curtain (send "o")
   - Close curtain (send "c")
   - Set custom servo angle (0–180)

---

## Output

- Curtain automatically opens/closes based on environment.
- Real-time outdoor temperature and humidity data sent to mobile.
- Manual override via Bluetooth.
- Servo motor position adjusted accordingly.

---

## Applications

- Smart Home Automation
- Energy-efficient room lighting control
- Climate-based curtain control
- IoT-based environmental monitoring

---

## Future Improvements

- Integration with WiFi (ESP8266/ESP32) for cloud monitoring
- Mobile app dashboard with real-time graph visualization
- Machine learning-based adaptive curtain behavior
- Integration with home automation platforms

---

