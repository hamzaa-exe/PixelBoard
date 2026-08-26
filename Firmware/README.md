
# PixelBoard Firmware

PixelBoard uses **WLED** running on the **Adafruit Sparkle Motion** to control a 16×16 WS2812B LED matrix.

WLED provides wireless control of the PixelBoard, including colors, animations, effects, brightness, presets, and playlists.

## Hardware

* **Controller:** Adafruit Sparkle Motion
* **Firmware:** WLED
* **LED type:** WS2812B
* **LED count:** 256
* **Matrix:** 16 × 16
* **Wi-Fi:** 2.4 GHz

## Install WLED

WLED can be installed directly from a compatible desktop web browser.

### Requirements

* Adafruit Sparkle Motion
* USB data cable
* Computer
* Google Chrome, Microsoft Edge, Opera, or another Web Serial-compatible browser
* 2.4 GHz Wi-Fi network

### Installation

1. Connect the Adafruit Sparkle Motion to your computer using a USB data cable.

2. Open the official WLED installer:

   [https://install.wled.me/](https://install.wled.me/)

3. Click **Install**.

4. Select the serial port for the Sparkle Motion.

5. Wait for WLED to finish installing.

6. Configure the Wi-Fi network when prompted.

> **Important:** WLED uses 2.4 GHz Wi-Fi. A 5 GHz-only network will not work.

## Wi-Fi Setup

After installation, WLED will attempt to connect to your Wi-Fi network.

If the Wi-Fi setup does not appear or the board cannot connect, WLED can create its own access point.

1. Open your device's Wi-Fi settings.

2. Connect to:

   `WLED-AP`

3. Use the default password:

   `wled1234`

4. Open the WLED interface.

5. Go to **Config → WiFi Setup**.

6. Enter your normal 2.4 GHz Wi-Fi credentials.

7. Set the mDNS name to:

   `pixelboard`

After connecting to the same Wi-Fi network, PixelBoard can be accessed through:

`http://pixelboard.local`

## LED Configuration

After connecting to WLED, open:

**Config → LED Preferences**

Configure the LED hardware for PixelBoard.

| Setting     | Value                    |
| ----------- | ------------------------ |
| Controller  | Adafruit Sparkle Motion  |
| LED Type    | WS281x / WS2812B         |
| LED Count   | 256                      |
| Matrix      | 16 × 16                  |
| Color Order | GRB                      |
| Data GPIO   | See PixelBoard schematic |

### LED Data Connection

The Sparkle Motion data output is connected to the **DIN** input of the first WS2812B LED.

The LEDs are connected in a continuous chain:

`Sparkle Motion → LED 1 → LED 2 → ... → LED 256`

The exact GPIO used for the data connection should match the GPIO configured in WLED.

## 16×16 Matrix

PixelBoard contains:

**16 × 16 = 256 WS2812B LEDs**

The physical arrangement of the LEDs and the direction of the data path must match the matrix configuration in WLED.

If animations appear:

* Upside down
* Mirrored
* Reversed
* In the wrong sequence

check the LED mapping and matrix settings in WLED.

## Using PixelBoard

Once WLED is configured, connect your phone or computer to the same Wi-Fi network.

Open:

`http://pixelboard.local`

WLED allows you to:

* Change LED colors
* Adjust brightness
* Select animations
* Change animation speed
* Select color palettes
* Create presets
* Create playlists
* Control PixelBoard wirelessly

## Power

The 256 WS2812B LEDs can draw a significant amount of current, especially at high brightness and when displaying white.

The LED matrix should be powered from the dedicated power supply designed for PixelBoard rather than attempting to power all 256 LEDs directly from the Sparkle Motion or USB connection.

For initial testing, keep the brightness/current limit low.

## Firmware Updates

PixelBoard does not use custom firmware.

**WLED is the firmware used by the Adafruit Sparkle Motion.**

When updating WLED, check the PixelBoard configuration afterward, especially:

* LED count
* Data GPIO
* Color order
* Matrix/LED mapping
* Brightness/current limits

## Resources

* WLED Installer: [https://install.wled.me/](https://install.wled.me/)
* WLED Documentation: [https://kno.wled.ge/](https://kno.wled.ge/)
* Adafruit Sparkle Motion documentation: [https://learn.adafruit.com/adafruit-sparkle-motion](https://learn.adafruit.com/adafruit-sparkle-motion)
* WLED GitHub: [https://github.com/Aircoookie/WLED](https://github.com/Aircoookie/WLED)

