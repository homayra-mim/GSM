Arduino Nano + SIM800A GSM Module to ThingSpeak
This project demonstrates how to send sensor data from an Arduino Nano to the ThingSpeak IoT platform using a SIM800A GSM module over HTTP.
It’s designed for locations without Wi-Fi, using the cellular network to transmit data.

🛠 Features
Collect sensor readings (e.g., temperature, humidity) from Arduino.
Send data to ThingSpeak via GSM (SIM800A).
Works in areas without internet access via Wi-Fi.
Can be adapted for multiple fields (up to 8 ThingSpeak fields).

📋 Hardware Required
Arduino Nano
SIM800A GSM/GPRS module
Jumper wires
Breadboard
External 5V–9V power supply (recommended for SIM800A, as Arduino’s 5V pin may not supply enough current)
(Optional) Sensors such as DHT11/DHT22 for temperature & humidity.

🔌 Wiring Diagram
Arduino Nano Pin	SIM800A Pin
D2	TXD
D3	RXD
GND	GND
5V / External	VCC (5–9V)

⚠ Important: SIM800A requires 2A peak current during transmission.
Use an external regulated power supply if possible.

📄 Code Overview
The code:
Initializes a SoftwareSerial connection with the GSM module.
Configures the SIM800A to connect to the mobile network.
Opens a TCP connection to api.thingspeak.com.
Sends data using a GET request to your ThingSpeak API key.
Closes the connection.

Replace:
cpp
Copy
Edit
String str = "GET https://api.thingspeak.com/update?api_key=O13AOCHYYNU2LQ19&field1=" + String(t) + "&field2=" + String(h);
with your own ThingSpeak API key and variables.

🖥 ThingSpeak Setup
Create an account at ThingSpeak.
Create a New Channel with your desired fields (e.g., field1 = Temperature, field2 = Humidity).
Copy your Write API Key from the channel settings.
Paste it into the Arduino code where O13AOCHYYNU2LQ19 is.

📡 APN Configuration
Change the APN in:
cpp
Copy
Edit
gprsSerial.println("AT+CSTT=\"airtelgprs.com\"");
to your SIM card provider’s APN (e.g., for Grameenphone: "internet", for Robi: "internet").

---->Usage
Upload the code to your Arduino Nano.
Power the SIM800A with a stable supply.
Open Serial Monitor (9600 baud) to see connection logs.
Check your ThingSpeak channel for live updates.

