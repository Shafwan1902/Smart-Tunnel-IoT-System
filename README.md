# 🌊 Smart Tunnel Flood Monitoring System (IoT)

A real-time IoT solution designed to detect flash floods in tunnels and automate safety barriers. This system leverages **ESP32**, **MQTT**, and a **Time-Series Database (InfluxDB)** to provide sub-second latency alerts and visualization.

![Dashboard Preview](PLACEHOLDER_LINK_TO_YOUR_DASHBOARD_IMAGE_HERE)
*(Add your Grafana Dashboard screenshot here)*

## 🚀 Project Overview
Flash floods in urban tunnels pose a significant risk to safety. This project simulates a "Smart Tunnel" that autonomously:
1.  **Monitors** river water levels and rainfall intensity.
2.  **Detects** critical overflow events inside the tunnel.
3.  **Triggers** an automated barrier (Servo Motor) to close the tunnel.
4.  **Alerts** operators via a Real-Time Grafana Dashboard and Telegram Bot.

## 🏗️ System Architecture

The system follows a 4-Layer IoT Architecture:
* **Perception Layer:** ESP32 DevKit V1 + Ultrasonic (HC-SR04) + Rain Sensor.
* **Network Layer:** Wi-Fi (IEEE 802.11 b/g/n) transmits telemetry via **MQTT** to HiveMQ Cloud.
* **Middleware:** A Python Gateway script bridges MQTT data to **InfluxDB** (Time-Series Database).
* **Application Layer:** **Grafana** visualizes data trends, while Telegram APIs handle emergency push notifications.

## 🛠️ Tech Stack

### Hardware
* **Microcontroller:** ESP32 DevKit V1 (Wi-Fi + Bluetooth)
* **Sensors:** HC-SR04 Ultrasonic (Distance), Analog Rain Sensor, Water Level Module
* **Actuators:** SG90 Servo Motor (Gate Control), Status LEDs (Red/Green)

### Software & Protocols
* **Language:** Python 3.9 (Gateway), MicroPython/C++ (ESP32 Firmware)
* **Communication:** MQTT (Message Queuing Telemetry Transport)
* **Database:** InfluxDB v2 (Optimized for high-speed time-series data)
* **Visualization:** Grafana (Industry-standard observability)
* **Alerting:** Telegram Bot API (HTTPS)

## 📊 Key Features
* **Real-Time Latency:** Achieved ~1.2s end-to-end latency from Sensor to Dashboard.
* **Resilience:** "Keep-Alive" MQTT sessions ensure connection stability.
* **Data Integrity:** InfluxDB handles high-write throughput for continuous sensor logging.
* **Safety Logic:** Local edge processing on ESP32 + Cloud verification in Python.

## ⚙️ How to Run

### 1. Hardware Setup
* Connect the sensors to the ESP32 pins as defined in `esp32_code.py`.
* Ensure the ESP32 is connected to a 2.4GHz Wi-Fi network.

### 2. Software Prerequisites
Install the required Python libraries:
```bash
pip install paho-mqtt influxdb-client requests
