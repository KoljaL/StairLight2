# StairLight System


## Project Description

StairLight is an intelligent stair lighting system built on the ESP8266 NodeMCU platform. The system automatically detects motion at the top of stairs using an MPU6050 accelerometer and creates beautiful lighting effects that follow users up or down the stairs.

## Key Features

### Hardware Integration
- **ESP8266 NodeMCU**: Main microcontroller with WiFi capabilities
- **PCA9685**: 16-channel PWM driver for precise LED control
- **MPU6050**: Motion detection via accelerometer
- **Retroreflective Sensor**: Bottom position detection
- **LED Strips**: Up to 10 individually controlled lighting channels

### Smart Motion Detection
- Direction-aware lighting (walk-up vs walk-down effects)
- Calibrated motion sensing with adjustable sensitivity on the top step, to trigger walk-down effect
- Retroreflective sensor at the bottom step triggers walk-up effect
- Configurable detection thresholds and timeouts
- if a light effect is active, a new triggerting will be ignored until the effect is finished
- 4 cases: walk-up, walk-down, walk-up-out, walk-down-out, each can be independently configured

### Web-Based Configuration
- Mobile-friendly responsive interface, all data received and send in JSON format
- PWA like, but no service worker implemented, allows easy access from Iphone home screen
- Comprehensive settings management
- Real-time effect preview
- Real-time status monitoring aka debug mode to see sensor readings and effect states on the setting page
- OTA (Over-The-Air) firmware updates
- WiFi network setup and management
- Factory reset option

#### Pages
- **/** - Main status and  Lighting Effects configuration
- **/settings** - OTA, WiFi, Scheduling, Sensors Sensitivity, and other configurations
- **/info** - System information, Factory reset and logs, if config mode enabled, auto refresh every 5 seconds, and concatenate log entries


### Lighting Effects
- **Walk-Up Effect**: Sequential lighting from bottom to top until all steps are lit
- **Walk-Down Effect**: Sequential lighting from top to bottom until all steps are lit
- **Walk-Up-Out Effect**: Sequential dimming from bottom to top
- **Walk-Down-Out Effect**: Sequential dimming from top to bottom
- **Fade-Out Effect**: Smooth dimming after timeout
- **Knight Rider Effect**: Back-and-forth sweeping light after power on
- Customizable timing, brightness, and overlap parameters

### Network Connectivity
- Access Point mode for initial setup
- Home WiFi integration with fallback to AP mode
- NTP time synchronization for scheduling
- JSON API for status and configuration

### Power Management & Scheduling
- Automatic lighting disable during daylight hours
- Configurable auto-off timing
- Energy-efficient PWM control with gamma correction
- Persistent configuration storage in EEPROM

## Technical Specifications

### Microcontroller
- **Platform**: ESP8266 NodeMCU (ESP-12E)
- **Framework**: Arduino
- **Flash Memory**: LittleFS for web files
- **EEPROM**: 512 bytes for configuration storage

### I/O Configuration
- **I2C Bus**: SDA=D2 (GPIO4), SCL=D1 (GPIO5)
- **Digital Input**: D5 (GPIO14) for bottom sensor
- **PWM Channels**: 0-9 via PCA9685
- **Communication**: 115200 baud serial, WiFi 802.11n

### Performance
- **Response Time**: <200ms motion detection
- **Effect Speed**: 50-2000ms per step (configurable)
- **PWM Frequency**: 1.6kHz for flicker-free operation
- **WiFi Range**: Standard ESP8266 range (~50m indoor)

## Installation Environment

### Development Tools
- **PlatformIO Core**: Cross-platform build system
- **Libraries**: Adafruit PCA9685, I2Cdevlib MPU6050, ESPAsyncWebServer
- **Upload Method**: USB serial or OTA via WiFi
- **Debugging**: Serial monitor at 115200 baud

### Network Requirements
- **WiFi**: 2.4GHz network (WPA/WPA2 security)
- **Internet**: Optional (for NTP time sync and OTA updates)
- **Local Access**: HTTP web interface on port 80

## Use Cases

### Residential Applications
- Home stair lighting with motion activation
- Energy-efficient automatic lighting
- Accessibility enhancement for elderly or mobility-impaired users
- Decorative accent lighting with programmable effects

### Commercial Applications
- Office building stairwell lighting
- Hotel and hospitality accent lighting
- Retail environment mood lighting
- Exhibition and display lighting control

## Customization Options

### Hardware Scalability
- Support for 1-10 LED strips (easily expandable to 16)
- Multiple sensor types (retroreflective, ultrasonic, PIR)
- Different LED strip types (12V, 24V, RGB, single-color)
- Power supply options (12V/24V external supplies)

### Software Flexibility
- Modular code architecture for easy modifications
- JSON-based configuration for integration with home automation
- RESTful API for external control systems
- Expandable effect library

### Integration Capabilities
- Home Assistant integration potential
- MQTT support (can be added)
- Smartphone app development ready
- Voice control integration possibility

---
