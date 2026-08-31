# PixelBoard

### 16×16 WS2812B RGB LED Matrix powered by WLED

PixelBoard is a custom 16×16 RGB LED matrix project using **256 individually addressable WS2812B LEDs** and a custom-designed PCB.

The custom PCB is designed specifically for PixelBoard and provides the ESP32-based controller, USB-C programming, 5V LED power distribution, level-shifted LED data, and a single 3-pin JST output for connecting the LED matrix.

The project uses **WLED** for wireless LED control, allowing the matrix to display animations, colors, effects, 2D patterns, and audio-reactive effects.

<img width="442" height="450" alt="Case 3" src="https://github.com/user-attachments/assets/381929b5-9279-4d8e-8dac-2df6f49779e4" />
<img width="441" height="450" alt="Case 2" src="https://github.com/user-attachments/assets/50226794-ca15-45fd-bbbc-da8f7523ade6" />
<img width="473" height="464" alt="case 1" src="https://github.com/user-attachments/assets/1f50d265-5a9c-4a0f-b1c7-f884694fb817" />
<img width="796" height="567" alt="SCHEMATICS" src="https://github.com/user-attachments/assets/f1a75195-138c-44de-a3be-60529f97346f" />
<img width="393" height="534" alt="PixelBoard PCB 1" src="https://github.com/user-attachments/assets/153fb95c-2dec-4ef1-b1fb-b23d83db908b" />
<img width="396" height="521" alt="Pixelboard PCB" src="https://github.com/user-attachments/assets/0407c92c-6b7d-4999-858d-f47d7eeefdf6" />


## Features

* 16×16 LED matrix
* 256 individually addressable WS2812B LEDs
* Custom ESP32-based controller PCB
* WLED firmware
* Wi-Fi control
* USB-C programming and power input
* 5V LED power output
* 5V logic-level shifting for LED data
* Single 3-pin JST LED matrix connector
* 2D matrix effects
* Audio-reactive effects
* Serpentine LED layout
* Custom enclosure and diffuser

## Hardware

| Component                              | Quantity |
| -------------------------------------- | -------: |
| Flexible 16×16 NeoPixel RGB LED Matrix |        1 |
| Custom PixelBoard Controller PCB       |        1 |
| ESP32-WROOM-32                         |        1 |
| 74AHCT125 Logic Level Shifter          |        1 |
| CH340C USB-to-Serial Converter         |        1 |
| AP2112K-3.3 Voltage Regulator          |        1 |
| LED Diffusion Acrylic                  |        1 |
| JST PH 3-Pin Cable                     |        1 |
| M2.5 Screws & Standoffs                |    1 set |
| 5V 2A Power Supply                     |        1 |
| USB-C Cable                            |        1 |

See [`bom.csv`](bom.csv) for the complete Bill of Materials, part numbers, prices, and product links.

## Custom PCB

PixelBoard uses a **custom-designed 2-layer PCB** instead of the Adafruit Sparkle Motion controller.

The PCB integrates the main electronics required to operate the LED matrix:

* ESP32-WROOM-32 controller
* CH340C USB-to-serial interface
* AP2112K 3.3V regulator
* 74AHCT125 5V logic-level shifter
* USB-C connector
* BOOT and RESET buttons
* 2A resettable fuse
* LED power filtering
* Single 3-pin JST LED output

The PCB is designed to fit within approximately **33 × 45 mm**.

## Wiring

The LED matrix connects directly to the custom PCB through the single 3-pin JST output.

```text
Custom PixelBoard PCB
        |
        | +5V  ------------> LED Matrix 5V
        |
        | GND  ------------> LED Matrix GND
        |
        | DATA ------------> LED Matrix DIN
```

The PCB uses a **74AHCT125** to shift the ESP32's 3.3V data signal to a 5V logic-level signal for the WS2812B matrix.

The LED data path is:

```text
ESP32 GPIO21
      |
      v
74AHCT125
      |
      v
330Ω Series Resistor
      |
      v
JST DATA
      |
      v
LED Matrix DIN
```

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

| Setting     | Value                 |
| ----------- | --------------------- |
| Controller  | Custom PixelBoard PCB |
| LED Type    | WS281x / WS2812B      |
| LED Count   | 256                   |
| Color Order | GRB                   |
| Data GPIO   | 21                    |
| Matrix      | 16 × 16               |
| First LED   | Bottom Left           |
| Orientation | Horizontal            |
| Serpentine  | ON                    |

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

The LED matrix is powered from a **5V 2A power supply** connected to the custom PCB.

The PCB separates the LED power path from the ESP32's 3.3V supply using an onboard **AP2112K-3.3 regulator** and includes a **2A resettable fuse** on the LED power path.

A large bulk capacitor is also placed near the LED output to help reduce voltage fluctuations caused by rapid changes in LED current.

The 256 LEDs can draw significant current at high brightness. For this reason, WLED's brightness and current limiting should be configured appropriately.

Do not operate the complete matrix at unrestricted full-white brightness from a 5V 2A supply.

## PCB Design

The custom PCB was designed in **KiCad**.

### PCB Specifications

| Specification         | Value                    |
| --------------------- | ------------------------ |
| PCB Type              | Custom 2-layer PCB       |
| Board Size            | Approximately 33 × 45 mm |
| Controller            | ESP32-WROOM-32           |
| LED Data GPIO         | GPIO21                   |
| Logic Level           | 5V LED data              |
| LED Output            | 3-pin JST                |
| LED Supply            | 5V                       |
| Main LED Power Trace  | 1.5 mm                   |
| Standard Signal Trace | 0.5 mm                   |
| Ground                | F.Cu + B.Cu copper pours |
| USB                   | USB-C                    |

The PCB files, schematic, and manufacturing files are located in the `hardware` directory.

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
│   └── WLED Configuration.md
├── enclosure/
└── images/
```

## Resources

* [WLED Installer](https://install.wled.me/)
* [WLED Documentation](https://kno.wled.ge/)
* [16×16 NeoPixel Matrix](https://www.adafruit.com/product/2547)

## License

This project is open-source. See the `LICENSE` file for details.

---

**PixelBoard — 16×16 pixels, 256 LEDs, powered by a custom PCB and WLED.**
