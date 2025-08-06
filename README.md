🌡️ ClimateBox – Smart ESP32 Climate & Light Control System
This project uses an ESP32, DHT11 sensor, relays, and Blynk to control lights and a fan based on timers and humidity data.

📦 Hardware Requirements
 ESP32 board

 DHT11 Temperature & Humidity sensor

 4-channel relay module

 Fan (connected to a relay)

 3 Lights (each connected to a relay)

 Jumper wires

 Breadboard or soldered PCB (optional)

 USB cable for programming ESP32

🔌 Relay Pin Mapping
Device	GPIO
Light 1	5
Light 2	18
Light 3	19
Fan	23
DHT11	4

🧰 Software Requirements
Arduino IDE (https://www.arduino.cc/en/software)

Libraries:

Blynk: Install from Library Manager → "Blynk"

DHT sensor library: "DHT sensor library" by Adafruit

Adafruit Unified Sensor (dependency for DHT)

🔧 Blynk Setup
Go to https://blynk.cloud

Create a new Template:

Template ID: TMPL3uleSHwL4

Template Name: ClimateBox

Add Datastreams for the following virtual pins:

Pin	Type	Purpose
V0	Switch	Manual Light 1
V1	Switch	Manual Light 2
V2	Switch	Manual Light 3
V3	Gauge	Humidity (%)
V4	Gauge	Temperature (°C)
V5	LED	Fan ON Indicator
V6–V8	Button	Light 1 timers (180, 360, 720 mins)
V9–V11	Button	Light 2 timers
V12–V14	Button	Light 3 timers
V15	Button	All lights 180 mins
V16	Button	All lights 360 mins
V17	Button	All lights 720 mins

Copy your Blynk Auth Token and paste it in the code here:

cpp
Copy
Edit
#define BLYNK_AUTH_TOKEN "YOUR_AUTH_TOKEN"
🖥️ Arduino IDE Setup
Install ESP32 board support:

File > Preferences > Add this URL to Additional Board URLs:

bash
Copy
Edit
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
Then go to Tools > Board > Board Manager and search/install esp32

Select your board:

Tools > Board: Choose ESP32 Dev Module

Set Wi-Fi Credentials in the code:

cpp
Copy
Edit
char ssid[] = "YOUR_WIFI_SSID";
char pass[] = "YOUR_WIFI_PASSWORD";
Upload Code:

Connect your ESP32 via USB

Select the correct COM Port (Tools > Port)

Click Upload (Right Arrow)

✅ How It Works
1. Manual Light Control
Use switches (V0–V2) to manually turn ON/OFF Light 1, 2, 3.

2. Timed Light Operation
Tap buttons (V6–V14) to start timer-controlled lighting cycles (3h, 6h, 12h).

Use buttons V15–V17 to start all lights together.

3. Humidity-based Fan Control
If humidity drops below 50%, fan turns ON (relay = LOW).

If humidity goes above 60%, fan turns OFF (relay = HIGH).

Virtual LED on V5 reflects fan status.

📈 Monitoring
Temperature is shown on V4

Humidity is shown on V3

Fan LED on V5

📋 Notes
DHT11 is not highly accurate; consider DHT22 for better precision.

Ensure your relay board logic is compatible with ESP32 (3.3V or 5V).

Always use proper safety measures if connecting high-voltage appliances.

📞 Troubleshooting
Sensor not responding?

Check DHT11 wiring and pin definition.

Fan always ON?

Double-check logic level (LOW = ON for relay).

Blynk not connecting?

Confirm Wi-Fi credentials and check your BLYNK_AUTH_TOKEN.
