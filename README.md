# Raspberry Pi Pico W Keypad-to-LED Controller

## Overview
This project drives **12 LEDs** from a **4x4 membrane keypad** using a Raspberry Pi Pico W.
The firmware is C++ in an Arduino-style structure (`setup()` / `loop()`) and was organized from the supplied source while preserving behavior.

## Repository Structure
- `src/main.cpp` – main firmware logic (unchanged behavior)
- `docs/wiring.md` – wiring, pin map, components
- `docs/architecture.md` – module and behavior breakdown
- `diagram.json` – Wokwi project hardware diagram
- `CMakeLists.txt` – minimal project metadata
- `lib/` – optional local libraries (currently empty)

## Features
- Reads keypresses from a 4x4 matrix keypad.
- Controls 8 blue LEDs mapped to numeric keys (`1..8`) plus group commands (`9` ON all, `0` OFF all).
- Controls 4 red LEDs mapped to letter keys (`A..D`) plus group commands (`*` ON all, `#` OFF all).

## Pin Summary
- Keypad rows: GP26, GP22, GP21, GP20
- Keypad cols: GP19, GP18, GP17, GP16
- LED GPIOs: GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4, GP3, GP2, GP28, GP27

See full table in `docs/wiring.md`.

## Run in Wokwi
1. Create a new Raspberry Pi Pico / Pico W project in Wokwi.
2. Copy `src/main.cpp` into the sketch editor.
3. Paste `diagram.json` into Wokwi's `diagram.json`.
4. Ensure the Keypad library is available in the simulation environment.
5. Start simulation and press keypad keys to observe LED behavior.

## Run on Real Hardware (Pico W)
> The provided source is Arduino-style C++. Recommended toolchain: **Arduino IDE** with Raspberry Pi Pico core.

1. Install Arduino IDE.
2. Add Raspberry Pi Pico board package (Raspberry Pi Pico/RP2040 core).
3. Install `Keypad` library.
4. Select board: **Raspberry Pi Pico W**.
5. Wire hardware exactly as in `docs/wiring.md`.
6. Build and upload.

## Wi-Fi Notes
This firmware does **not** use Wi-Fi APIs. No credentials are required.
If future versions add Wi-Fi, store credentials in a separate, ignored config file (e.g., `secrets.h`) and never commit secrets.
