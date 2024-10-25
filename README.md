
# Temperature and Humidity Monitoring with Arduino and Telegram Bot

This project uses a **DHT11** sensor to monitor temperature and humidity, displaying real-time data on an **OLED** display and allowing remote access to the readings via a **Telegram** bot.

## Features

- Measurement of temperature and humidity with DHT11 sensor.
- Displaying data on the OLED SSD1306 display.
- Integration with a Telegram bot for remote readings.
- Wi-Fi connection management for easy internet access.
- Support for Telegram command `/state` to view current temperature and humidity, and `/start` for instructions.

## Required Components

- **Arduino with WiFi support** (e.g., ESP32)
- **DHT11** (temperature and humidity sensor)
- **SSD1306 OLED display**
- **WiFi Connection**
- **Telegram Account** and a bot created via BotFather to receive notifications (include the bot token in the code).

## Hardware Connections

1. Connect the **DHT11** sensor to the **DHTPIN** defined in the code (e.g., pin `2`).
2. Connect the **SSD1306** display to the ESP32 using the **SDA** and **SCL** pins for I2C.

## Library Installation

To run this project, make sure to have the following libraries installed in **Arduino IDE**:

- `WiFi.h` and `WiFiClientSecure.h` (included in the base ESP32 library).
- `UniversalTelegramBot.h` for handling Telegram bot requests.
- `ArduinoJson.h` for JSON parsing.
- `Adafruit_Sensor.h`, `DHT.h` for the DHT11 sensor.
- `Adafruit_GFX.h` and `Adafruit_SSD1306.h` for the OLED display.

## Code Configuration

Before uploading the code, configure the following variables in the `.ino` file:

- **WiFi**:
  ```cpp
  #define WIFI_SSID "YOUR_WIFI_SSID"
  #define WIFI_PASSWORD "YOUR_WIFI_PASSWORD"
  ```

- **Telegram Bot**:
  ```cpp
  #define BOT_TOKEN "YOUR_BOT_TOKEN"
  ```

## Usage

1. **WiFi Connection**: After the device starts, the ESP32 will attempt to connect to the configured WiFi network.
2. **OLED Display**: Temperature and humidity data will be shown in real-time on the OLED display.
3. **Telegram Bot**: Use the following commands to interact with the bot:
   - `/start`: You will receive a welcome message and usage guide.
   - `/state`: You will receive the current temperature and humidity.

## Screens

The OLED display shows:
- A status icon to indicate connection attempts.
- **Temperature** and **Humidity** in large characters for easy reading.

## Main Code Functions

- **WiFi Connection**: Managed in the `setup()` phase; the connection is monitored with messages on the serial monitor.
- **DHT11 Reading**: The sensor measures temperature and humidity; the readings are sent both to the OLED display and to the Telegram bot.
- **Telegram Update**: The `handleNewMessages()` function checks for new messages every second and handles the `/start` and `/state` commands.
