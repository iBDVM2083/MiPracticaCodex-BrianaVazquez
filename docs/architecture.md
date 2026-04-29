# Firmware Architecture

## File Layout

- `src/main.cpp`: Main firmware logic (preserved behavior).
- `include/`: Reserved for future headers and module extraction.
- `docs/wiring.md`: Hardware wiring and pin map.

## Runtime Flow

1. **Initialization (`setup`)**
   - Configures all LED GPIO pins as outputs.
   - Clears all LEDs to LOW.

2. **Main loop (`loop`)**
   - Reads one key using `keypad.getKey()`.
   - If a key is pressed, enters a `switch` dispatch block.
   - Executes direct LED ON/OFF writes according to key semantics.
   - Waits `10 ms` per iteration.

## Keypad-to-LED Behavior Matrix

- `1`..`8`: set corresponding blue LED HIGH.
- `9`: set blue bank (LED1..LED8) HIGH.
- `0`: set blue bank (LED1..LED8) LOW.
- `A`..`D`: set corresponding red LED HIGH.
- `*`: set red bank (LEDA..LEDD) HIGH.
- `#`: set red bank (LEDA..LEDD) LOW.

## Design Notes

- No debounce logic beyond loop delay.
- Actions are level-setting only; no toggle mode.
- LEDs remain in last commanded state until overwritten.
- No Wi-Fi or network stack interaction in current firmware.
