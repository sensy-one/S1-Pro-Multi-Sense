## 🚀 Sensy-One S1 Pro Multi Sense

The all-in-one presence and environmental sensor for Homey Pro and Home Assistant.

![Sensy-One Banner](https://github.com/sensy-one/S1-Pro-Multi-Sense/blob/main/assets/images/S1_Pro_Multi_Sense.jpg)

S1 Pro combines presence detection, air-quality monitoring and ambient light sensing in one compact device. It connects locally to Homey Pro or Home Assistant through ESPHome. [Explore on YouTube](https://www.youtube.com/watch?v=s2bCj49uFjw)

## ✨ Standout Specs

**Local smart home integration**

Connect S1 Pro to Homey Pro or Home Assistant over your local network using ESPHome. Follow [Getting Started](#-getting-started) to set up your connection and add the sensor.

**Powered by ESP32-C3**

At its core, the S1 Pro uses the ESP32-C3-MINI-1-N4 module — offering reliable Wi-Fi and Bluetooth Low Energy, low power consumption, and support for ESPHome, Homey Pro and Home Assistant.

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

In Homey, use the sensor's LED Flow cards to set power, colour and brightness. In Home Assistant, use its light entity.

**Built-in buzzer**

The integrated Huaneng MLT-8530 buzzer delivers clear audio alerts at 80–90 dB and 2.7 kHz, perfect for notifications, warnings, or presence feedback. In Homey, use the buzzer Flow cards; in Home Assistant, use its switch.

**Comprehensive environmental monitoring**

Equipped with the advanced Bosch BME688 sensor, the S1 Pro delivers real-time insights into your indoor environment. It measures CO₂ equivalent, gas resistance, IAQ (Indoor Air Quality), VOC equivalent, humidity, temperature, and air pressure — giving you a complete picture of air quality and comfort in your space.

**High-precision CO₂ sensing (add-on)**

For even more accurate measurements, the S1 Pro supports an optional Sensirion SCD40 module.
This add-on measures CO₂, humidity, and temperature with higher precision, and connects directly to the main PCB via a Molex Mezzanine connector — no soldering required.

The SCD40 add-on entities are disabled by default in Home Assistant, including the calibration buttons and temperature offset. If the add-on is installed, enable its entities on the S1 Pro device page. Home Assistant preserves existing enabled/disabled settings and may restore them after a device is removed and added again, so disable unused SCD40 entities manually if needed. The built-in BME688 entities remain enabled; IAQ Classification reports `unknown` until a valid IAQ measurement is available.

**Ambient light and UV sensing**

Earlier S1 Pro units use the Lite-On LTR-390UV with illuminance (Lux) and UV index (UVI); newer units use the LTR-F216A with illuminance only. At startup, the firmware reads the sensor's full PART_ID at I²C address 0x53, register 0x06. UVI is exposed only for the documented LTR390 ID (0xB2); the LTR-F216A (0xB1), an unrecognized ID, or a failed read hides UVI and disables UV sampling. The existing lux calculation, calibration, entity names, and IDs are preserved. The UV-offset control is unchanged.

If Home Assistant already registered a UVI entity on a unit without UV hardware, that old entry may remain unavailable after updating. Disable that entry once in Home Assistant; newly discovered units without UV hardware will not offer a UVI entity.

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

## ⚡ Getting Started

### Connect to your network

Power S1 Pro with a 5 V USB-C supply. On first setup, connect to its **I am Sensy!** Wi-Fi access point, open `http://192.168.4.1`, and save your 2.4 GHz Wi-Fi credentials.

BLE Improv is currently disabled; use the access point for setup.

### Add to Homey Pro

1. Install the [SENSY-ONE app](https://homey.app/en-nl/app/com.sensy-one/SENSY-ONE/test/).
2. Make sure S1 Pro and Homey Pro are on the same local network.
3. In Homey, select **Devices → + → SENSY-ONE → S1 Pro**, then choose your sensor.

Measurements are available in Flows and Insights. Home Assistant is not required. The app is under review and can already be installed through the test link above.

### Add to Home Assistant

Once connected to your network, S1 Pro appears under **Settings → Devices & services**. Select the discovered ESPHome device and complete the setup.

## 🎛 Adjusting Sensor Offsets

Compare readings with a trusted reference after the sensor has warmed up.

- **Homey Pro:** open the sensor's advanced settings to adjust BME688/SCD40 temperature offsets and lux correction.
- **Home Assistant:** adjust the temperature, lux or UV-index offset entities on the device page. UV index is not exposed in Homey.

## 🌬 CO₂ Calibration (SCD40 Add-on)

In Homey, use the SCD40 calibration control in the sensor's advanced settings and follow its instructions.

**In Home Assistant:**
- Place the sensor in fresh outdoor air.
- In Home Assistant, click Forced Calibration on the S1 Pro.
- The sensor will set a new baseline of 425 ppm (current global outdoor CO₂ level).

> Tip: Only perform this when you're confident the air is clean and stable. (The BME688 calibrates itself automatically — no user action required.)

## 🧭 Get in the Zone

The S1 Pro now supports up to 3 detection zones and 1 exclusion zone — all configurable as custom polygons with up to 8 points each.

### Homey Pro

Open **Settings → Apps → SENSY-ONE → App settings** in Homey. Select your sensor, draw the zones and save. Presence and target-count readings appear for each configured detection zone.

### Home Assistant

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

## 📊 Home Assistant: Plotly Graph Card

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

## 🔄 Firmware on the Fly

Keep your S1 Pro up to date with regular OTA updates.  
We continuously improve performance and add new features to keep your device reliable and future-ready.

**Install OTA Updates**
- Download the latest OTA firmware from the [releases](https://github.com/sensy-one/S1-Pro-Multi-Sense/releases).
- Open the sensor's local IP address in your browser. In Home Assistant, you can also use **Visit** on its ESPHome device page.
- Scroll down to OTA Update, choose the firmware file, and click Update.

> Tip: If the page times out during upload, just refresh the page or try again.

## 🔧 Troubleshooting

**Not found in Homey?** Check that the sensor and Homey Pro are on the same local network and that mDNS discovery is allowed.

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
