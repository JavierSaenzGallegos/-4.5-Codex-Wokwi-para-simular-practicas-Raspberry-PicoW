# Firmware Architecture

## Source Layout
- `src/main.cpp`
  - Keypad matrix definition (`keys`)
  - Pin maps (`ledPins`, `rowPins`, `colPins`)
  - Initialization (`setup`)
  - Event loop (`loop`)

## Behavioral Flow
1. **Boot/Setup**
   - Configure all LED pins as outputs.
   - Initialize all LEDs to OFF.

2. **Main Loop**
   - Read one key event using `keypad.getKey()`.
   - If a valid key is pressed, execute a `switch` action:
     - `1..8`: turn ON corresponding numeric LED.
     - `9`: turn ON all numeric LEDs.
     - `0`: turn OFF all numeric LEDs.
     - `A..D`: turn ON corresponding alpha LED.
     - `*`: turn ON all alpha LEDs.
     - `#`: turn OFF all alpha LEDs.
   - Wait 10ms (`delay(10)`) for light debouncing/poll pacing.

## Design Notes
- Core logic is intentionally unchanged from the provided source.
- Code follows an Arduino-style runtime model and is suitable for Wokwi simulation.
- For Pico SDK migration, preserve state/action mapping and replace Arduino HAL calls (`pinMode`, `digitalWrite`, `delay`) with SDK equivalents.
