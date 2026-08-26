# WLED Configuration

PixelBoard uses **WLED** on the **Adafruit Sparkle Motion** to control a 16×16 WS2812B LED matrix.

After installing WLED, configure the LED matrix using the settings below.

## LED Settings

Open the WLED interface and go to:

**Config → LED Preferences**

Under **LED Outputs**, use the following settings:

| Setting     | Value                  |
| ----------- | ---------------------- |
| LED Type    | WS281x                 |
| mA/LED      | 55 mA (typ. 5V WS281x) |
| Color Order | GRB                    |
| Start       | 0                      |
| Length      | 256                    |
| Data GPIO   | 21                     |

Click **Save** after entering the settings.

## 2D Configuration

To configure the 16×16 matrix correctly, go to:

**Config → 2D Configuration**

Under **2D Setup**:

* **2D Mode:** 2D Matrix

Under **LED Panel Layout**:

| Setting     | Value       |
| ----------- | ----------- |
| 1st LED     | Bottom Left |
| Orientation | Horizontal  |
| Serpentine  | ON          |
| Width       | 16          |
| Height      | 16          |

The resulting matrix contains:

**16 × 16 = 256 LEDs**

Click **Save** after applying the settings.

### LED Layout

The matrix uses a **serpentine layout**, meaning each row alternates its direction.

```text
→ → → → → → → → → → → → → → → →
← ← ← ← ← ← ← ← ← ← ← ← ← ← ← ←
→ → → → → → → → → → → → → → → →
← ← ← ← ← ← ← ← ← ← ← ← ← ← ← ←
              ...
→ → → → → → → → → → → → → → → →
← ← ← ← ← ← ← ← ← ← ← ← ← ← ← ←
```

The first LED is located at the **bottom-left** of the matrix.

## 2D Effects

WLED provides effects specifically designed for 2D LED matrices.

To find them:

1. Open the WLED homepage.
2. Go to the **Effects** section.
3. Click the effect search box.
4. Select the **Matrix** category.
5. WLED will display the available 2D effects.
6. Select an effect to display it on PixelBoard.

These effects take advantage of the 16×16 matrix rather than treating the LEDs as a simple 1D strip.

## Audio Reactive Configuration

PixelBoard can also use WLED's audio-reactive features with an I2S digital microphone.

Open:

**Config → Usermods**

Find the **Audio Reactive** section and enable it.

### Digital Microphone

Under the **Digitalmic** type dropdown, select:

**Generic I2S**

Use the following pin configuration:

| I2S Signal | GPIO |
| ---------- | ---: |
| I2S SD     |   25 |
| I2S WS     |   33 |
| I2S SCK    |   26 |

Enable **Audio Reactive** and click **Save**.

## Configuration Summary

| Category        | Setting                 |
| --------------- | ----------------------- |
| Controller      | Adafruit Sparkle Motion |
| Firmware        | WLED                    |
| LED Type        | WS281x / WS2812B        |
| LED Count       | 256                     |
| Matrix          | 16 × 16                 |
| Color Order     | GRB                     |
| Data GPIO       | 21                      |
| First LED       | Bottom Left             |
| Orientation     | Horizontal              |
| Serpentine      | ON                      |
| 2D Mode         | 2D Matrix               |
| Audio Reactive  | Enabled                 |
| Microphone Type | Generic I2S             |
| I2S SD          | GPIO 25                 |
| I2S WS          | GPIO 33                 |
| I2S SCK         | GPIO 26                 |

> **Important:** These GPIO assignments are based on the Adafruit Sparkle Motion configuration described in the project documentation. Make sure your PixelBoard wiring matches these pins before powering the matrix.

## Resources

* [WLED Installer](https://install.wled.me/)
* [WLED Documentation](https://kno.wled.ge/)
* [Adafruit Sparkle Motion](https://learn.adafruit.com/adafruit-sparkle-motion)

