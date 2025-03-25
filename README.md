# Environmental Monitoring Station

**YouTube Channel:** https://www.youtube.com/playlist?list=PLrZbkNpNVSwxEoAMTovuAd9RmLn4Sj5hn  
**GitHub Repository:** https://github.com/HorizonHnk/Environmental-Monitoring-Station.git

![Environmental Monitoring System](https://via.placeholder.com/800x400?text=Environmental+Monitoring+System)

## Project Overview

This repository contains all code and documentation for an Environmental Monitoring Station built with ESP32 microcontrollers. The system monitors air quality, temperature, and humidity with a master-slave architecture using ESP-NOW wireless communication. The master unit features a web interface for remote monitoring, data visualization, and export capabilities.

**Time to complete:** 2 weeks (intensive development)

## Features

- **Real-time environmental monitoring** of:
  - Air quality (CO2/VOCs) via MQ135 sensor
  - Temperature (-40°C to 80°C) via DHT22 sensor
  - Humidity (0-100%) via DHT22 sensor
- **Master-slave architecture** with wireless communication
  - Master unit with air quality monitoring and data aggregation
  - Slave unit with temperature and humidity sensors
- **Multi-modal visualization**:
  - LCD display with real-time readings
  - LED threshold indicators (10 for temperature/humidity, 5 for air quality)
  - Buzzer alerts for critical air quality levels
  - Web interface for remote monitoring
- **Data logging and analysis**:
  - 24-hour data storage at 1-minute intervals
  - CSV export functionality
  - Real-time and historical data visualization

## System Architecture

The system consists of two ESP32 units communicating wirelessly:

### Master Unit
- ESP32 microcontroller with built-in Wi-Fi
- MQ135 air quality sensor
- 20x4 LCD display (I2C)
- 5 LEDs for air quality level indication
- Buzzer for alert notifications
- Web server for remote monitoring

### Slave Unit
- ESP32 microcontroller
- DHT22 temperature and humidity sensor
- 10 LEDs for threshold indicators (5 temp, 5 humidity)
- Wireless communication with master unit

## Technology Selection

### Microcontroller Comparison

| **Feature** | **ESP32** | **Arduino UNO** | **ESP8266** | **Raspberry Pi Zero W** | **STM32 (F4)** |
|-------------|-----------|-----------------|-------------|-------------------------|----------------|
| CPU | Dual-core 240MHz | Single-core 16MHz | Single-core 80MHz | Single-core 1GHz | Single-core 84MHz |
| RAM | 520KB | 2KB | 80KB | 512MB | 128KB |
| Flash | 4MB | 32KB | 4MB | External SD | 512KB |
| WiFi | Built-in | None | Built-in | Built-in | None |
| Bluetooth | Built-in | None | None | Built-in | None |
| GPIO Pins | 36 | 14 | 17 | 40 | 51 |
| ADC Channels | 18 | 6 | 1 | 0 (needs HAT) | 16 |
| Power Consumption | 160-260mA | 50mA | 80mA | 150-250mA | 20-100mA |
| Cost | $8-10 | $5-8 | $3-5 | $10-15 | $10-15 |
| Ease of Use | Moderate | High | Moderate | Low | Low |

**Selected: ESP32** - Best balance of processing power, connectivity, GPIO availability, and cost. Built-in WiFi enables IoT functionality without additional components.

### Development Environment

Arduino IDE was selected for its extensive library support and ease of use, enabling rapid development despite the project's complexity.

## Project Goals and Benefits

### Primary Goals

1. **Create an Affordable Environmental Monitoring Solution**
   - Target cost under $100 total (compared to $150-500 for commercial options)
   - Use readily available components for easier reproduction and maintenance

2. **Monitor Key Environmental Parameters**
   - Air Quality (VOCs/CO2) using MQ135 sensor
   - Temperature (-40°C to 80°C) using DHT22 sensor
   - Humidity (0-100%) using DHT22 sensor

3. **Provide Multiple Visualization Methods**
   - Local Display: 20x4 LCD showing current readings and status
   - Visual Indicators: LED arrays showing threshold status for each parameter
   - Audible Alerts: Buzzer with different patterns for air quality warnings
   - Remote Access: Web interface accessible via WiFi for monitoring from any device

4. **Create Flexible and Expandable System**
   - Master-slave architecture allowing separation of sensor units
   - Wireless communication for flexible placement
   - Modular code design for easier future enhancement

5. **Implement Data Logging for Trend Analysis**
   - Store 24 hours of readings at 1-minute intervals
   - Provide data export in CSV format for further analysis
   - Display basic trend visualization in web interface

### Benefits and Applications

1. **Health and Comfort Monitoring**
   - Track indoor air quality for health impact awareness
   - Monitor temperature and humidity for optimal comfort
   - Receive alerts when parameters exceed healthy thresholds

2. **Energy Efficiency**
   - Identify optimal temperature and humidity settings
   - Monitor environmental changes to optimize HVAC usage
   - Collect data for analyzing environmental patterns

3. **Educational Value**
   - Demonstrate microcontroller capabilities and IoT concepts
   - Provide real-world data for environmental science education
   - Serve as platform for learning about sensors, wireless communication, and web interfaces

## Development Timeline

The project was completed in an intensive 2-week development sprint:

### Week 1: Research, Design, and Simulation
- Days 1-2: Research and component selection
  - Evaluated microcontrollers, sensors, and communication protocols
  - Selected ESP32, DHT22, and MQ135 as primary components
  - Designed system architecture with master-slave configuration
- Days 3-4: Circuit design and simulation
  - Created wiring diagrams for both units
  - Set up Wokwi simulation environments
  - Validated sensor reading algorithms virtually
- Days 5-7: Core functionality implementation
  - Simulated temperature/humidity monitoring unit
  - Simulated air quality monitoring unit
  - Tested LED threshold indicators and display formatting
  - Implemented basic web interface in simulation

### Week 2: Hardware Implementation and Integration
- Days 1-2: Hardware assembly
  - Set up both ESP32 units on breadboards
  - Connected sensors, LEDs, LCD displays
  - Verified basic hardware functionality
- Days 3-4: Sensor integration and calibration
  - Implemented sensor reading algorithms on hardware
  - Calibrated sensors for accuracy
  - Created threshold-based alert systems
- Days 5-6: Wireless communication and integration
  - Implemented ESP-NOW communication between units
  - Integrated all sensor data at master unit
  - Created unified data visualization system
- Day 7: Web interface and final testing
  - Enhanced web interface with interactive dashboard
  - Implemented data logging and export functionality
  - Conducted comprehensive testing and debugging

## Final System Technical Specifications

### Master Unit

- **Microcontroller**: ESP32 Development Board
- **Air Quality Sensor**: MQ135 (ADC Pin 34)
- **Display**: 20x4 LCD via I2C (Address 0x27)
- **Alert System**: Buzzer on GPIO 19 with three pattern modes
- **Indicators**: 5 LEDs for air quality levels (GPIOs 26, 27, 13, 12, 14)
- **Network**: WiFi AP+STA mode with ESP-NOW on channel 6
- **Web Interface**: Responsive dashboard with real-time updates
- **Data Logging**: Circular buffer with 1440 data points (24 hours at 1-minute intervals)
- **Export Options**: CSV data export and local storage

### Slave Unit

- **Microcontroller**: ESP32 Development Board
- **Sensors**: DHT22 Temperature & Humidity (GPIO 5)
- **Indicators**: 
  - 5 LEDs for temperature thresholds (GPIOs 15, 2, 4, 25, 26)
  - 5 LEDs for humidity thresholds (GPIOs 13, 14, 33, 32, 27)
- **Network**: ESP-NOW communication with master on channel 6
- **Features**: Connection status indication, automatic reconnection

## Software Features

- Non-blocking code design for responsive operation
- Sensor data averaging for improved stability
- LED threshold visualization for intuitive monitoring
- Web-based dashboard with interactive controls
- CSV data export functionality for analysis
- Captive portal for easy web interface access
- Multi-pattern buzzer alerts based on air quality levels
- Master-slave wireless communication with timeout detection
- Comprehensive error handling and recovery mechanisms
- NTP time synchronization when internet-connected
- Configurable logging intervals and alert thresholds

## Code Structure

### Master Unit Code Organization

```
master/
├── master.ino                 # Main program entry point
├── config.h                   # Configuration parameters and pin definitions
├── sensors/
│   ├── mq135.h                # MQ135 air quality sensor functions
│   └── mq135.cpp              # Implementation of air quality monitoring
├── display/
│   ├── lcd_manager.h          # LCD display management functions
│   └── lcd_manager.cpp        # Implementation of display formatting
├── communication/
│   ├── espnow_manager.h       # ESP-NOW communication functions
│   └── espnow_manager.cpp     # Implementation of wireless communication
├── indicators/
│   ├── led_controller.h       # LED control functions
│   └── buzzer_controller.h    # Buzzer alert pattern functions
├── webserver/
│   ├── server_manager.h       # Web server and API functions
│   ├── html_content.h         # Web page HTML content
│   └── js_content.h           # JavaScript for web interface
└── data/
    ├── data_logger.h          # Data logging functions
    └── data_logger.cpp        # Implementation of data storage and export
```

### Slave Unit Code Organization

```
slave/
├── slave.ino                  # Main program entry point
├── config.h                   # Configuration parameters and pin definitions
├── sensors/
│   ├── dht22.h                # DHT22 temperature/humidity functions
│   └── dht22.cpp              # Implementation of temperature/humidity monitoring
├── display/
│   ├── lcd_manager.h          # LCD display management functions
│   └── lcd_manager.cpp        # Implementation of display formatting
├── communication/
│   ├── espnow_manager.h       # ESP-NOW communication functions
│   └── espnow_manager.cpp     # Implementation of wireless communication
└── indicators/
    └── led_controller.h       # LED threshold indicator functions
```

## Bill of Materials

| Component | Quantity | Unit Cost | Total Cost |
|-----------|----------|-----------|------------|
| ESP32 Development Board | 2 | $8 | $16 |
| DHT22 Temperature & Humidity Sensor | 1 | $3 | $3 |
| MQ135 Air Quality Sensor | 1 | $5 | $5 |
| 20x4 I2C LCD Display | 2 | $7 | $14 |
| 5mm LEDs (assorted colors) | 20 | $0.10 | $2 |
| Passive Buzzer | 1 | $1 | $1 |
| Breadboards | 2 | $5 | $10 |
| Jumper Wires (pack) | 1 | $5 | $5 |
| Resistors (220Ω, pack of 100) | 1 | $2 | $2 |
| 10kΩ Resistor | 1 | $0.50 | $0.50 |
| Micro USB Cables | 2 | $3 | $6 |
| USB Power Adapters | 2 | $5 | $10 |
| **TOTAL** | | | **$74.50** |

## Testing Protocol

### Functional Testing
- Sensor calibration and accuracy verification
- LED threshold indicator testing
- Alert system verification with different patterns
- Wireless communication reliability testing
- Web interface compatibility testing

### Environmental Testing
- Temperature range testing (0°C to 40°C)
- Humidity range testing (20% to 90% RH)
- Air quality response testing with controlled variations

### Reliability Testing
- Continuous operation testing (24+ hours)
- Error recovery testing (sensor failures, communication disruptions)
- Power consumption analysis

## Future Enhancements

1. **Extended Sensing Capabilities**
   - Add particulate matter (PM2.5/PM10) sensing
   - Include CO and ozone detection

2. **Cloud Connectivity**
   - Implement cloud storage for long-term data retention
   - Create cloud-based analytics dashboard

3. **Mobile Application**
   - Develop dedicated mobile app for monitoring
   - Add push notifications for alerts

4. **Machine Learning Integration**
   - Implement predictive analytics for air quality trends
   - Create anomaly detection for unusual environmental conditions

5. **Energy Optimization**
   - Add sleep modes for lower power consumption
   - Implement solar power option for remote deployment

## Installation and Usage

### Hardware Setup

1. **Assemble the master unit:**
   - Connect MQ135 sensor to ESP32 (ADC pin 34)
   - Connect I2C LCD display (SDA to pin 21, SCL to pin 22)
   - Connect 5 LEDs with 220Ω resistors to pins 26, 27, 13, 12, 14
   - Connect buzzer to pin 19

2. **Assemble the slave unit:**
   - Connect DHT22 sensor to ESP32 (pin 5)
   - Connect 10 LEDs with 220Ω resistors to pins 15, 2, 4, 25, 26, 13, 14, 33, 32, 27

### Software Setup

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/environmental-monitoring-station.git
   ```

2. Install required libraries in Arduino IDE:
   - ESP32 board support
   - Adafruit DHT Sensor library
   - LiquidCrystal_I2C library
   - ESP-NOW library

3. Open `master/master.ino` and `slave/slave.ino` in Arduino IDE

4. Update the MAC addresses in the configuration:
   - Find the slave's MAC address using the `GetMacAddress` example
   - Update `SLAVE_MAC_ADDRESS` in `master/config.h`

5. Upload code to both units and power them on

### Accessing the Web Interface

1. Connect to the WiFi network "ESP32_EnvMonitor" (password: "monitoring")
2. Navigate to http://192.168.4.1 in your web browser
3. View real-time environmental data and historical trends
4. Export data as CSV using the "Download Data" button

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Libraries used:
  - [Adafruit DHT Sensor Library](https://github.com/adafruit/DHT-sensor-library)
  - [LiquidCrystal_I2C](https://github.com/johnrickman/LiquidCrystal_I2C)
  - ESP32 Core libraries

## Contact

For questions or collaboration, please open an issue on this repository.
