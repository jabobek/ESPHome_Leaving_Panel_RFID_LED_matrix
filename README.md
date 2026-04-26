# ESPHome RFID Leaving Panel with 8x16 LED Matrix

A comprehensive ESPHome-based smart panel for your home entrance. This project features an RFID reader for security/presence, an 8x16 LED matrix for status and weather display, and integration with Home Assistant for advanced automation logic.

## Features
- **RFID Presence:** Tag scanning for arrival/departure logic.
- **8x16 LED Matrix:** Custom animations for weather, countdowns, and status icons.
- **Weather Display:** Syncs with Home Assistant to show current weather conditions and temperature.
- **Countdown Timer:** Visual feedback when leaving the house.
- **Environmental Sensing:** Built-in AHT10 sensor for indoor temperature and humidity.
- **BLE Tracking:** Integrated BLE tracker for presence detection.
- **Home Assistant Integration:** Full control via HA services and entities.

## Hardware Requirements
- **Microcontroller:** ESP32 (e.g., ESP32-DevKitC)
- **Display:** 8x16 WS2812B (NeoPixel) LED Matrix
- **RFID Reader:** RC522 (SPI)
- **Sensor:** AHT10 (I2C)
- **Other:** Push button, Door sensor (magnetic), optional Relays.

## Wiring Guide

| Component | ESP32 Pin | Note |
|-----------|-----------|------|
| **RC522 (SPI)** | | |
| SCK | GPIO 18 | |
| MOSI | GPIO 23 | |
| MISO | GPIO 19 | |
| SDA (CS) | GPIO 5 | |
| RST | GPIO 4 | |
| **AHT10 (I2C)** | | |
| SDA | GPIO 21 | |
| SCL | GPIO 22 | |
| **LED Matrix** | GPIO 13 | Data Pin |
| **Buttons/Sensors**| | |
| Panel Button | GPIO 14 | Input Pullup |
| Door Sensor | GPIO 27 | Input Pullup |
| **Relay Outputs** | | |
| Relay 1-4 | GPIO 32, 33, 25, 26 | |

## Installation
1.  **ESPHome:** Use `rfid_leaving_panel.yaml` as your main configuration. Update the `wifi` section and any `substitutions` if needed.
2.  **Home Assistant:**
    - Import the provided Blueprints/YAMLs for logic:
        - `ha_leaving_panel_leavinglogic.yaml`: Handles RFID scans and light control.
        - `ha_leaving_panel_weather_sync.yaml`: Synchronizes weather data from HA to the panel.
        - `ha_leaving_panel_weather_1h.yaml`: Automation for temporary weather display.
    - Make sure to replace placeholder entity IDs (like `sensor.outdoor_temperature`) with your actual entities in the Home Assistant automations.
	- Additional automation can be done via HA interface with used sensors or outputs

## Usage
- **Leaving:** Press the panel button to start the countdown. The matrix will show the remaining time.
- **Arriving:** Scan your RFID tag. If recognized, it triggers your "Welcome" automation (e.g., turning on lights).
- **Idle:** Displays weather, temperature, or custom text/icons as configured in Home Assistant.

## License & Attribution
This project is free to use, modify, and distribute. 
**Attribution is required:** Please mention the original author when using or sharing this project.
