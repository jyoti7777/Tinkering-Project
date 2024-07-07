# Indoor Air Quality Monitor

## Overview

This project aims to design an Indoor Air Quality Monitoring System. The primary features of the system are:

- Utilizing MQ sensors and DTH11 to detect various air parameters, temperature, and humidity.
- Maintaining a record of the values in an Excel sheet, accessible remotely via OneDrive.
- Integrating ESP32's Wi-Fi capabilities for mobile connectivity to send instant alerts to mobile devices based on our indoor air quality sensor readings.

## Team Members

- Patel Ayush (2022CSB1101)
- Pranav Menon (2022CSB1329)
- Hartik Arora (2022CSB1314)
- Jyoti (2022CSB1319)
- Aniket Kumar Sahil (2022CSB1067)

## Components and Parts

- **Twilio:** A cloud-based communication platform providing APIs for SMS integration from ESP32 to a smartphone.
- **MQ Sensors:** Used to detect gases via resistance changes, utilizing metal oxide semiconductor coatings. The MQ-2 sensor is pivotal for gauging smoke concentration and detecting gases like LPG, butane, propane, methane, alcohol, smoke, and hydrogen.
- **DHT11 Sensor:** Measures temperature and humidity.
- **ESP32:** A microcontroller with Wi-Fi capabilities.
- **Arduino UNO:** Central processing unit for sensor data.

## Design Parameters

### Sensor Integration and Compatibility
- **Communication:** Establish protocols to ensure seamless communication between MQ sensors, DHT11, Arduino UNO, and ESP32 for synchronized data collection.
- **Mapping Values:** Map sensor values within the appropriate range of the processing unit to derive correct ppm values for gas detection.

### Data Transmission and Notification System
- **Twilio Integration:** ESP32 integrates with Twilio's API to enable SMS or other notifications.
- **ESP32 Integration:** Configured to connect to the internet via Wi-Fi, handling sensor data, triggering notifications, and communicating with Twilio's API.

### Power Consumption
- **Power Supply:** Using a laptop USB port to provide 5V to MQ and DHT11 sensors, Arduino UNO, and 3.3V for ESP32.


## Challenges Faced

### Hardware
- **Power Management:** Managing power between Arduino UNO (5V), ESP32 (3.3V), and gas sensors (5V) due to voltage differences.
- **Pin Selection:** Identifying suitable ESP32 pins for specific purposes.
- **Sensor Heating Time:** Sensors require significant heat-up time to detect values efficiently.

### Software
- **Updated Apps:** Outdated tutorials increased confusion during the integration process.
- **Libraries:** Managing multiple sensor libraries and identifying the correct ones to include.
- **Critical Values:** Determining critical gas sensor values due to varying analog ranges for different boards.

## Applications in Industries
- Industrial Safety Monitoring
- Smart Agriculture
- Environmental Monitoring
- Research and Education
- Smart Cities
- Greenhouse Monitoring
- Safety in sensitive chambers like nuclear power plants and submarines

## Future Enhancements
- Custom sensor integration as per application needs.
- Improved user interface for better communication.
- Additional alert mechanisms such as email and push notifications.
- Geolocation/geofencing and mapping.
- Enhanced power efficiency and sustainability.
- Integration with external systems (e.g., AI).
- Advanced data analysis, research, and visualization.


=
