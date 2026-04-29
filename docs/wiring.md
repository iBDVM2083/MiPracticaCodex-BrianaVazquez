# Wiring and GPIO Mapping (Raspberry Pi Pico W)

## Overview

The keypad uses 8 GPIO lines (4 rows + 4 columns). LEDs are each controlled by dedicated GPIO outputs through 220Ω series resistors, with LED cathodes tied to GND.

## GPIO Map

| Function | GPIO | Physical Signal |
|---|---:|---|
| Keypad Row R1 | GP26 | `rowPins[0]` |
| Keypad Row R2 | GP22 | `rowPins[1]` |
| Keypad Row R3 | GP21 | `rowPins[2]` |
| Keypad Row R4 | GP20 | `rowPins[3]` |
| Keypad Col C1 | GP19 | `colPins[0]` |
| Keypad Col C2 | GP18 | `colPins[1]` |
| Keypad Col C3 | GP17 | `colPins[2]` |
| Keypad Col C4 | GP16 | `colPins[3]` |
| LED 1 | GP11 | `ledPins[0]` |
| LED 2 | GP10 | `ledPins[1]` |
| LED 3 | GP9 | `ledPins[2]` |
| LED 4 | GP8 | `ledPins[3]` |
| LED 5 | GP7 | `ledPins[4]` |
| LED 6 | GP6 | `ledPins[5]` |
| LED 7 | GP5 | `ledPins[6]` |
| LED 8 | GP4 | `ledPins[7]` |
| LED A | GP3 | `ledPins[8]` |
| LED B | GP2 | `ledPins[9]` |
| LED C | GP28 | `ledPins[10]` |
| LED D | GP27 | `ledPins[11]` |

## Passive Components

- **LED resistors**: 12 × 220Ω in series with LED anodes.
- **Keypad row pull-ups**: 4 × 1kΩ from row net to 3V3 (`R1..R4` network in diagram).

## Power and Ground

- Pico `3V3` feeds keypad pull-up resistor chain.
- All LED cathodes return to Pico GND.
- Common ground is mandatory for stable keypad/LED operation.

## Assumptions

- Based on provided `diagram.json`, the board part is `wokwi-pi-pico`; project target is **Pico W** and GPIO compatibility is maintained.
