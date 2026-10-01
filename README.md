# Smart Workshop Sensor

A compact, modern environmental monitoring device built around an ESP32.

The Smart Workshop Sensor is designed to monitor the environmental conditions of a workshop, garage, room, or workspace. It combines multiple sensors with an OLED display and provides a simple status system for quickly understanding the current environment.

> Project Status: In Development

---

## Features

### Current

- Temperature measurement
- Relative humidity measurement
- Atmospheric pressure measurement
- Ambient light measurement
- 128×64 OLED display
- Physical navigation buttons
- Environmental status indicator
- Custom 3D-printed enclosure
- USB-C powered
- Modular firmware architecture

### Planned

- CO₂ measurement
- Wi-Fi connectivity
- Web dashboard
- Historical data graphs
- Local data logging
- Environmental warnings
- Mobile-friendly interface
- OTA firmware updates
- Optional battery operation
- Automatic environmental analysis
- Custom PCB

---

## Hardware

The first version uses the following components:

| Component | Purpose |
|---|---|
| ESP32 DevKit | Main microcontroller |
| BME280 | Temperature, humidity and pressure |
| 0.96" OLED 128×64 | User interface |
| BH1750 | Ambient light measurement |
| Push buttons | Menu navigation |
| Green LED | Normal status |
| Yellow LED | Warning status |
| Red LED | Critical status |
| USB-C | Power |
| 3D-printed enclosure | Housing |

A CO₂ sensor such as the SCD40/SCD41 is planned for a future version.

---

## Main Display

The main screen is designed to provide the most important information at a glance.

```text
┌────────────────────────┐
│    SMART WORKSHOP      │
│                        │
│       22.6 °C          │
│       47 % RH          │
│      1012 hPa          │
│                        │
│       643 lux          │
│                        │
│    STATUS: NORMAL      │
└────────────────────────┘
```

The display will automatically update the sensor values.

---

## User Interface

The device uses three physical buttons.

### Main Menu

```text
Dashboard
Temperature
Humidity
Pressure
Light
History
Settings
Device Info
```

The interface should remain simple and readable so the device can be operated without a computer or phone.

---

## Environmental Status

The device uses three status levels:

| Status | Meaning |
|---|---|
| NORMAL | Environmental values are within the configured range |
| WARNING | One or more values require attention |
| CRITICAL | One or more values are outside the critical range |

The thresholds are configurable in the project configuration.

---

## Software

The firmware is written in C++ and developed using:

- Visual Studio Code
- PlatformIO
- ESP32 Arduino Framework

### Libraries

The project uses or plans to use:

- `Adafruit BME280`
- `Adafruit Unified Sensor`
- `Adafruit GFX`
- `Adafruit SSD1306`
- `BH1750`
- `Wire`

---

## Project Structure

```text
SmartWorkshopSensor/
│
├── platformio.ini
│
├── src/
│   └── main.cpp
│
├── include/
│   ├── config.h
│   ├── sensors.h
│   ├── display.h
│   └── buttons.h
│
├── lib/
│
├── data/
│
└── README.md
```

The project is intentionally modular so new sensors and features can be added without rewriting the entire firmware.

---

## I2C Architecture

The environmental sensors and OLED display communicate with the ESP32 using the I2C bus.

```text
                    ┌──────────────┐
                    │     ESP32    │
                    │              │
                    │ SDA → GPIO21 │
                    │ SCL → GPIO22 │
                    └───────┬──────┘
                            │
             ┌──────────────┼──────────────┐
             │              │              │
             ▼              ▼              ▼
          BME280          OLED           BH1750
       Temperature      Display          Light
       Humidity
       Pressure
```

---

## Enclosure

The planned enclosure dimensions are approximately:

**100 × 60 × 30 mm**

The enclosure will be 3D printed.

Design goals:

- Compact
- Modern
- Easy to print
- Easy to assemble
- Replaceable components
- Good sensor airflow
- Accessible USB-C port
- Clean cable management

The sensors should have ventilation openings to prevent inaccurate readings caused by heat trapped inside the enclosure.

---

## Future Web Dashboard

A future version will provide a web interface through the ESP32.

Example:

```text
SMART WORKSHOP
────────────────────────

Temperature
22.6 °C

Humidity
47 %

Pressure
1012 hPa

CO₂
643 ppm

Light
643 lux

────────────────────────
ENVIRONMENT: NORMAL
```

Historical measurements will eventually be displayed as graphs.

---

## Development Roadmap

### Version 0.1 — Prototype

- <img width="1000" height="750" alt="image" src="https://github.com/user-attachments/assets/babe45be-b277-4cd8-9aff-e63aaf8400a1" />

