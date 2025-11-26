## 🚀 Sensy-One S1 Pro Multi Sense

The all-in-one open-source sensor designed for Home Assistant, refined through real-world user feedback.

![Sensy-One Banner](https://github.com/sensy-one/S1-Pro-Multi-Sense/blob/main/assets/images/S1_Pro_Multi_Sense.jpg)

The Sensy-One S1 Pro Multi Sense is an open-source presence and environmental sensor, built from the ground up with Home Assistant in mind. After extensive prototyping, firmware tuning, and valuable input from users and smart home enthusiasts, the S1 Pro brings together reliable presence detection, real-time air quality monitoring, and ambient light sensing — all in one compact, Home Assistant-ready device. [Explore on YouTube](https://www.youtube.com/watch?v=s2bCj49uFjw)

## ✨ Standout Specs

**Seamless Home Assistant integration**

The S1 Pro is automatically discovered in Home Assistant via BLE Improv when Bluetooth is available. If not, it starts a wireless access point for quick setup — no additional tools required.

> Note: BLE Improv is temporarily disabled due to performance issues.

**Powered by ESP32-C3**

At its core, the S1 Pro uses the ESP32-C3-MINI-1-N4 module — offering reliable Wi-Fi and Bluetooth Low Energy, low power consumption, and full support for ESPHome and Home Assistant integrations.

**Flexible USB-C power configuration (add-on)**

The S1 Pro includes a built-in, downward-facing USB-C port for standard mounting.
For added flexibility, two optional modules connect via the rear Mezzanine connector:
a male USB-C plug for direct connection to a wall adapter without cables, and a female USB-C port for placing the sensor upright, where bottom access isn't practical.

**Modular mounting options**

The S1 Pro supports two optional mounting adapters for flexible placement:
a ball mount for precise positioning in 90-degree corners, and a standard ball mount for clean, low-profile installation on any surface.

**Precision-engineered enclosure**

The custom case is optimized for minimal interference with mmWave signals and maximum airflow across the sensors — ensuring accurate environmental readings and efficient cooling to extend component lifespan. Printed on a Formlabs Form 4 resin printer, the enclosure features a smooth, professional finish with no visible layer lines, and measures just 50 mm high, 35 mm wide, and 25 mm deep.

**Advanced mmWave presence sensing**

Powered by the Hi-Link LD2450 radar module, the S1 Pro tracks up to three targets simultaneously, including their position, speed, and movement in real time.
It features a 120° field of view, 70° vertical coverage, and up to 6 meters range, with updates every 30 ms for smooth, accurate presence detection.

**BLE Presence & Proximity**

The S1 Pro supports Bluetooth-based presence and proximity detection, with seamless integration into platforms like Bermuda. This enables accurate room-level tracking of smartphones, wearables, and tags!

> Note: This feature is temporarily disabled due to performance issues. We’re actively working on stabilizing it.

**Customizable detection zones**

Define up to 3 detection zones, plus 1 exclusion zone to ignore movement from devices like fans or 3D printers.
Each zone includes adjustable presence delay and motion threshold settings, and reports zone-specific data such as target count, occupancy status, and movement activity.

**Full-color status LED**

A bright WS2812B RGB LED on the back of the PCB projects light onto the wall, ideal for alerts, presence indication, or ambient effects.

**Built-in buzzer**

The integrated Huaneng MLT-8530 buzzer delivers clear audio alerts at 80–90 dB and 2.7 kHz, perfect for notifications, warnings, or presence feedback.

**Comprehensive environmental monitoring**

Equipped with the advanced Bosch BME688 sensor, the S1 Pro delivers real-time insights into your indoor environment. It measures CO₂ equivalent, gas resistance, IAQ (Indoor Air Quality), VOC equivalent, humidity, temperature, and air pressure — giving you a complete picture of air quality and comfort in your space.

**High-precision CO₂ sensing (add-on)**

For even more accurate measurements, the S1 Pro supports an optional Sensirion SCD40 module.
This add-on measures CO₂, humidity, and temperature with higher precision, and connects directly to the main PCB via a Molex Mezzanine connector — no soldering required.

**Ambient light and UV sensing**

The integrated Lite-On LTR-390UV sensor measures both illuminance (Lux) and UV index (UVI), enabling smart lighting control and sun exposure awareness based on real-time ambient conditions.

## 📍 Best Placement Practices

To get the most accurate presence and environmental readings, it's important to place the S1 Pro correctly.

**Recommended mounting height:**
- 1.25 to 1.50 meters from the floor (typical seated/standing person height).
- Higher is possible — just tilt the sensor downward to cover the detection area.

**Placement tips:**
- Ensure a clear line of sight to the monitored area — walls, plants, or furniture can reduce accuracy.
- Avoid placing near large metal objects (like fridges, pipes, or servers), as they can reflect mmWave signals.
- Avoid direct airflow from HVAC vents or fans to keep air quality readings stable
- Mount away from heat sources to prevent temperature distortion

## ⚡ From Power On to Home Assistant

Power the S1 Pro using any standard 5V USB-C power source.
Once powered, it automatically begins looking for your Home Assistant system.

**If your Home Assistant setup supports Bluetooth (BLE):**
- The S1 Pro will be automatically discovered under Devices & Services.
- Click Add, enter your Wi-Fi credentials, and you're done.

> Note: BLE Improv is temporarily disabled due to performance issues.

**If your system does not support Bluetooth:**
- The sensor will start a Wi-Fi access point named I am Sensy!.
- Connect to it and open `http://192.168.4.1` in your browser.
- Enter your Wi-Fi details, click Save, and it will connect to your network.
- The sensor will then show up in Home Assistant as a Discovered device.

> Tip: Make sure your Wi-Fi is 2.4 GHz — 5 GHz is not supported.  
For best results, use a dedicated IoT network to improve stability, make discovery easier, and enhance security.

## 🎛 Adjusting Sensor Offsets

The S1 Pro allows you to fine-tune sensor readings directly from Home Assistant.

**Offsets are available for:**
- Temperature (BME688 / SCD40)
- Lux & UV index (LTR-390UV)

**To calibrate:** 
- Compare readings with a trusted external device.
- Adjust the offset entities exposed by the S1 Pro in Home Assistant.
- Changes apply instantly — no restart or YAML needed.

> Tip: Let the sensor run for a few minutes before calibrating for the most stable results.

## 🌬 CO₂ Calibration (SCD40 Add-on)

For faster or more precise calibration, you can use the Forced Calibration button in Home Assistant.

**To calibrate manually:**
- Place the sensor in fresh outdoor air.
- In Home Assistant, click Forced Calibration on the S1 Pro.
- The sensor will set a new baseline of 425 ppm (current global outdoor CO₂ level).

> Tip: Only perform this when you're confident the air is clean and stable. (The BME688 calibrates itself automatically — no user action required.)

## 📊 Real-Time Visualization with Plotly Graph Card

Visualize live presence data from the S1 Pro directly in your Home Assistant dashboard.  
The Plotly Graph Card shows an interactive view of target positions, movement speed, and your defined zones — giving you instant insight into room activity.

**Install HACS and the Plotly Graph Card**
- If you haven’t already installed HACS, follow the [Official instructions](https://www.hacs.xyz/docs/use/download/download/).
- Once installed, open HACS from the sidebar in Home Assistant.  
- Go to Frontend, search for Plotly Graph Card, and click Download. 
- Refresh your browser after installation.

**Add a Custom Plotly Graph Card**
- Go to your Home Assistant dashboard and click Edit Dashboard.
- Select Add Card, then choose Plotly Graph Card. 
- Click Show Code Editor to open the YAML editor.
- Copy and paste the custom configuration from the [Git repository](https://github.com/sensy-one/S1-Pro-Multi-Sense/blob/main/assets/config/plotly_chart.yaml) into the editor.

**Replace the Placeholder IDs**
- In the YAML config, look for any replace_me placeholders.
- Replace them with your device name, for example: s1_pro_multi_sense_4048c4.
- If you renamed the device (for example to living_room), use that instead.

> Tip: Use Ctrl+F (Windows) or Cmd+F (Mac) to quickly find and replace all instances.
> Note: Seeing "Visual editor not supported"? That’s normal for custom cards — you can safely ignore it.

## 🧭 Get in the Zone

The S1 Pro now supports up to 3 detection zones and 1 exclusion zone — all configurable as custom polygons with up to 8 points each.
Instead of adjusting multiple number entities, you can now set zones visually using the Zone Editor tool:

> Note: A new and improved Zone Editor Add-on for Home Assistant is now available!
You can find it [here](https://github.com/sensy-one/home-assistant-addons) and follow the installation guide. The steps below describe the manual (legacy) method, which you can still use if you prefer.

**How to use the Zone Editor**
- Download the [zone_editor.html](https://github.com/sensy-one/S1-Pro-Multi-Sense/tree/main/assets/config) file.
- Open the Zone Editor on a desktop computer using any modern browser (Chrome, Edge, Firefox, Safari).
- In the Zone Editor, enter the IP address of your S1 Pro sensor (the same one you see in Home Assistant).
- Select which zone you want to configure (Zone 1, Zone 2, Zone 3, or Exclusion).
- Click directly on the radar canvas to place up to 8 points and draw the shape of your zone.
- Save your configuration — it will be applied immediately to your device.

> Note: Make sure your desktop is connected to the same network as your Home Assistant / Sensor.

> Tip: If you run into trouble, you can always have a look at the [YouTube video](https://www.youtube.com/watch?v=raLACrPG8EM) for guidance.

## 🔄 Firmware on the Fly

Keep your S1 Pro up to date with regular OTA updates.  
We continuously improve performance and add new features to keep your device reliable and future-ready.

**Install OTA Updates**
- Download the latest OTA firmware from the [releases](https://github.com/sensy-one/S1-Pro-Multi-Sense/releases).
- In Home Assistant, go to Devices and Services, ESPHome.
- Select your S1 Pro and click Visit under Device Info to open the web interface. 
- Scroll down to OTA Update, choose the firmware file, and click Update.

> Tip: If the page times out during upload, just refresh the page or try again.

## 🔧 Troubleshooting

If your sensor isn’t behaving as expected, a factory reset can help you start fresh.

**Install Factory Firmware**
- Download the latest factory firmware from the [releases](https://github.com/sensy-one/S1-Pro-Multi-Sense/releases).
- Connect the sensor to your computer using a USB-C cable. 
- Open the [ESPHome web wizard](https://web.esphome.io/?dashboard_wizard).
- Click Connect and select the correct COM port.  
- Choose Install, select the firmware file you downloaded, and click Install again.

> Note: Only the bottom-facing USB-C port supports data transfer.

## 💬 Let's Connect

Your feedback helps us improve. Whether you’ve found a bug, need help, or want to suggest a feature — we’re listening.

**Discord:**
- Join the community and get support on our [Discord server](https://discord.gg/TB78Wprn66).

**GitHub Issues:**  
- Found a bug or have a suggestion? Report it on our [GitHub issues page](https://github.com/sensy-one/S1-Pro-Multi-Sense/issues).