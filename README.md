# PixelBoard

### 16×16 WS2812B RGB LED Matrix powered by WLED

PixelBoard is a 16×16 RGB LED matrix project using 256 individually addressable WS2812B LEDs and an **Adafruit Sparkle Motion** controller.

The project uses **WLED** for wireless LED control, allowing the matrix to display animations, colors, effects, 2D patterns, and audio-reactive effects.

<img width="442" height="450" alt="Case 3" src="https://github.com/user-attachments/assets/381929b5-9279-4d8e-8dac-2df6f49779e4" />
<img width="441" height="450" alt="Case 2" src="https://github.com/user-attachments/assets/50226794-ca15-45fd-bbbc-da8f7523ade6" />
<img width="473" height="464" alt="case 1" src="https://github.com/user-attachments/assets/1f50d265-5a9c-4a0f-b1c7-f884694fb817" />
<img width="659" height="476" alt="led display pcb" src="https://github.com/user-attachments/assets/3d85f37c-c577-437f-a25a-8abca300495b" />
<img width="615" height="236" alt="LED DISpLAY schematic" src="https://github.com/user-attachments/assets/e30acd1d-adce-4b2a-bc37-2bb84700e153" />


## Features

* 16×16 LED matrix
* 256 individually addressable WS2812B LEDs
* Adafruit Sparkle Motion controller
* WLED firmware
* Wi-Fi control
* 2D matrix effects
* Audio-reactive effects
* Serpentine LED layout
* Custom enclosure and diffuser

## Hardware

| Component                              | Quantity |
| -------------------------------------- | -------: |
| Flexible 16×16 NeoPixel RGB LED Matrix |        1 |
| Adafruit Sparkle Motion                |        1 |
| LED Diffusion Acrylic                  |        1 |
| JST PH 3-Pin Cables                    |       2+ |
| M2.5 Screws & Standoffs                |    1 set |
| 5V Power Supply                        |        1 |
| USB-C Cable                            |        1 |
| Right-Angle USB-C Adapter              |        1 |

See [`bom.csv`](bom.csv) for the complete Bill of Materials, part numbers, prices, and product links.

## Wiring

The LED matrix is connected to the Adafruit Sparkle Motion as follows:

```text
Sparkle Motion
     |
     | GPIO 21
     v
  LED Matrix DIN

5V  ------------> LED Matrix 5V
GND ------------> LED Matrix GND
```

The LEDs are connected in a chain from the first LED to the last LED.

## Firmware

PixelBoard uses **WLED** rather than custom firmware.

WLED provides:

* Wireless control
* Color and brightness control
* LED effects
* 2D matrix effects
* Presets and playlists
* Audio-reactive effects

WLED can be installed using the official installer:

https://install.wled.me/

For complete installation instructions and PixelBoard-specific settings, see:

**[Firmware Documentation](Firmware/README.md)**

Detailed LED and 2D matrix configuration is available in:

**[WLED Configuration](Firmware/WLED Configuration.md)**

### Main WLED Settings

| Setting     | Value                   |
| ----------- | ----------------------- |
| Controller  | Adafruit Sparkle Motion |
| LED Type    | WS281x / WS2812B        |
| LED Count   | 256                     |
| Color Order | GRB                     |
| Data GPIO   | 21                      |
| Matrix      | 16 × 16                 |
| First LED   | Bottom Left             |
| Orientation | Horizontal              |
| Serpentine  | ON                      |

## 2D Matrix

The matrix uses a serpentine layout with the first LED positioned at the bottom-left.

```text
→ → → → → → → → → → → → → → → →
← ← ← ← ← ← ← ← ← ← ← ← ← ← ← ←
→ → → → → → → → → → → → → → → →
← ← ← ← ← ← ← ← ← ← ← ← ← ← ← ←
```

This configuration allows WLED's 2D effects to display correctly across the entire matrix.

## Power

The 256 LEDs can draw significant current at high brightness. Use a suitable 5V power supply and avoid powering the entire matrix directly through the controller or USB connection.

For testing, keep the brightness and current limit at a reasonable level.

## Repository Structure

```text
PixelBoard/
├── README.md
├── bom.csv
├── hardware/
│   ├── schematic/
│   ├── pcb/
│   └── gerbers/
├── firmware/
│   ├── README.md
│   └── wled_config.md
├── enclosure/
└── images/
```

## Resources

* [WLED Installer](https://install.wled.me/)
* [WLED Documentation](https://kno.wled.ge/)
* [Adafruit Sparkle Motion](https://www.adafruit.com/product/6100)
* [16×16 NeoPixel Matrix](https://www.adafruit.com/product/2547)

## License

This project is open-source. See the `LICENSE` file for details.

---

**PixelBoard — 16×16 pixels, 256 LEDs, powered by WLED.**
