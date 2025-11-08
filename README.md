# StairLight System - ESP8266 Project

## Overview

Complete intelligent stair lighting system with motion detection, web-based configuration, and beautiful lighting effects.

## Features

- ✅ Direction-aware motion detection (walk-up/walk-down)
- ✅ 4 customizable lighting effects
- ✅ Web-based configuration interface (mobile-friendly)
- ✅ OTA (Over-The-Air) firmware updates
- ✅ Time-based scheduling (auto-disable during daylight)
- ✅ Real-time sensor monitoring in debug mode
- ✅ EEPROM persistent configuration storage
- ✅ WiFi with AP fallback mode
- ✅ Knight Rider startup animation

## Hardware Requirements

- ESP8266 NodeMCU (ESP-12E)
- PCA9685 16-channel PWM driver
- MPU6050 accelerometer (I2C)
- Retroreflective sensor (bottom detection)
- LED strips (up to 10 channels)
- 12V/24V power supply

## Pin Configuration

```
I2C Bus:
  SDA: D2 (GPIO4)
  SCL: D1 (GPIO5)

Digital Inputs:
  Bottom Sensor: D5 (GPIO14)

PWM Outputs:
  LED Channels 0-9 via PCA9685 (I2C address 0x40)
```

## Getting Started

### 1. Build and Upload Firmware

```bash
# Build project
pio run

# Upload via USB
pio run --target upload

# Upload filesystem (web interface)
pio run --target uploadfs
```

### 2. Initial Setup

1. Power on the device
2. Connect to WiFi network: `StairLight_Setup`
3. Password: `stairlight123`
4. Open browser to: `http://192.168.4.1`
5. Configure your home WiFi in Settings
6. Device will restart and connect to your network

### 3. Configuration

Access the web interface at the device's IP address:

- **Effects Page (/)**: Configure lighting effects
- **Settings (/settings.html)**: WiFi, sensors, scheduling
- **Info (/info.html)**: System information, factory reset

## Web API

### GET /api/status
Returns current system status and sensor readings.

### GET /api/config
Returns complete configuration.

### POST /api/config
Update configuration (JSON body).

### POST /api/test
Manually trigger an effect for testing.

### POST /api/reset
Factory reset (erases all settings).

## Effect Types

1. **Walk-Up**: Lights turn on from bottom to top
2. **Walk-Down**: Lights turn on from top to bottom
3. **Walk-Up-Out**: Lights turn off from bottom to top
4. **Walk-Down-Out**: Lights turn off from top to bottom

Each effect can be independently configured:
- Step delay (50-2000ms)
- Fade duration (100-2000ms)
- Brightness (10-100%)
- Overlap (1-5 steps)
- Enable/disable

## OTA Updates

After initial setup, upload new firmware wirelessly:

```bash
# Configure upload_port in platformio.ini
upload_protocol = espota
upload_port = stairlight.local

# Upload via OTA
pio run --target upload
```

## Debug Mode

Enable debug mode in Settings to see:
- Real-time sensor readings
- Motion detection status
- System logs
- Effect states

Serial monitor (115200 baud) also provides detailed debugging output.

## Troubleshooting

### Device not responding
- Check power supply (sufficient amperage for LEDs)
- Verify I2C connections (SDA, SCL)
- Reset to factory defaults via Info page

### WiFi connection issues
- Ensure 2.4GHz network (ESP8266 doesn't support 5GHz)
- Check SSID and password are correct
- Device will fall back to AP mode after 30 seconds

### Motion detection too sensitive/insensitive
- Adjust "Sensitivity" in Settings page
- Lower values = more sensitive
- Calibration happens automatically on boot

### LEDs flickering
- Check power supply capacity
- Reduce global brightness
- Verify PCA9685 connections

## Code Structure

```
include/
  config.h          - Pin definitions and constants
  storage.h         - EEPROM configuration management
  sensors.h         - Motion detection interface
  leds.h            - LED control and effects
  webserver.h       - Web server and API

src/
  main.cpp          - Setup and main loop
  storage.cpp       - Configuration persistence
  sensors.cpp       - MPU6050 and sensor logic
  leds.cpp          - PCA9685 and lighting effects
  webserver.cpp     - WiFi and HTTP server

data/
  index.html        - Effects configuration page
  settings.html     - Settings page
  info.html         - System information page
  style.css         - Responsive styling
  main.js           - Effects page JavaScript
  settings.js       - Settings page JavaScript
  info.js           - Info page JavaScript
```

## Development

This project follows clean coding practices:
- Modular architecture
- Non-blocking, event-driven design
- Extensive inline documentation
- Better Comments style (🔵 INFO, 🟠 WARNING, etc.)
- Beginner-friendly code

See `.copilot-instructions.md` for detailed coding standards.

## License

This project is provided as-is for educational and personal use.

## Credits

Built with:
- PlatformIO
- Arduino framework for ESP8266
- Adafruit PWM Servo Driver Library
- I2Cdevlib MPU6050
- ESPAsyncWebServer
- ArduinoJson
- NTPClient

---

**Made with ❤️ for beautiful stair lighting**
