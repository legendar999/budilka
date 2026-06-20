# Budilka (Arduino Alarm Clock)

An **alarm-clock** project for the **Arduino Uno**, built with **[PlatformIO](https://platformio.org/)**. It shows the time on a 16×2 character LCD and keeps accurate time with a real-time clock (RTC) module.

> ⚠️ **Work in progress** — the firmware is in an early stage. The base setup (LCD + RTC library, project scaffolding) is in place; alarm logic is being built on top.

---

## Hardware

- **Arduino Uno** (ATmega328P)
- **16×2 character LCD** (HD44780-compatible) driven via the `LiquidCrystal` library
- **RTC module** (e.g. DS1307 / DS3231) via the `makuna/RTC` library
- *(planned)* buzzer + push-buttons for setting and triggering the alarm

### LCD wiring

The current pin mapping in `src/main.cpp` is:

```cpp
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
//               RS   E  D4 D5 D6 D7
```

| LCD pin | Arduino pin |
| ------- | ----------- |
| RS      | 12          |
| E       | 11          |
| D4      | 5           |
| D5      | 4           |
| D6      | 3           |
| D7      | 2           |

---

## Build & Upload (PlatformIO)

1. Install **PlatformIO** (the VS Code extension or the `pio` CLI).
2. Connect the Arduino Uno over USB.
3. From the `Budilka/` folder:

   ```bash
   pio run            # build
   pio run -t upload  # build & flash to the board
   pio device monitor # (optional) open the serial monitor
   ```

---

## Dependencies

Declared in `Budilka/platformio.ini`:

- `LiquidCrystal@^1.0.7`
- `makuna/RTC@^2.5.0`

PlatformIO installs these automatically on the first build.

---

## Project Structure

```
Budilka/
├── platformio.ini     # board config (Arduino Uno) and library deps
├── src/
│   └── main.cpp        # firmware entry point
├── include/            # project headers
├── lib/                # private/local libraries
└── test/               # unit tests
```

---

## License

Released under the [MIT License](LICENSE).
