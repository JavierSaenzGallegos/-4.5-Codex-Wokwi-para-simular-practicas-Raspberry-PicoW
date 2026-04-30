# Wiring and GPIO Mapping

## Components List (from Wokwi diagram)
- 1x Raspberry Pi Pico / Pico W (`wokwi-pi-pico`)
- 1x 4x4 membrane keypad (`wokwi-membrane-keypad`)
- 12x LEDs (`wokwi-led`): 8 blue + 4 red
- 12x LED resistors: 220Ω (`r1..r12`)
- 4x keypad pull-up resistors: 1kΩ (`rp1..rp4`) tied to 3V3 on row lines

## Keypad Connections
| Keypad Signal | Pico W GPIO |
|---|---|
| C4 | GP16 |
| C3 | GP17 |
| C2 | GP18 |
| C1 | GP19 |
| R4 | GP20 |
| R3 | GP21 |
| R2 | GP22 |
| R1 | GP26 |

## LED Connections
All LED cathodes are tied to Pico GND.

| LED Label | Function Group | Pico W GPIO |
|---|---|---|
| 1 | Numeric | GP11 |
| 2 | Numeric | GP10 |
| 3 | Numeric | GP9 |
| 4 | Numeric | GP8 |
| 5 | Numeric | GP7 |
| 6 | Numeric | GP6 |
| 7 | Numeric | GP5 |
| 8 | Numeric | GP4 |
| A | Alpha | GP3 |
| B | Alpha | GP2 |
| C | Alpha | GP28 |
| D | Alpha | GP27 |

## Power and Ground
- Keypad row pull-up network (`rp1..rp4`) connects to **3V3**.
- LEDs sink to **GND**.
- Pico and all peripherals share a common ground.

## Assumptions
- Diagram part is `wokwi-pi-pico`; firmware target requested is Pico W. GPIO mappings are compatible for this use case.
- Serial monitor uses GP0/GP1 in the diagram; firmware does not use UART explicitly.
