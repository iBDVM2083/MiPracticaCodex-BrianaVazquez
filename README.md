#    Tecnológico Nacional de México
#   Instituto Tecnológico de Tijuana
#        Subdirección Académica
# Departamento de Sistemas y Computación
##  Ingeniería en Sistemas Computacionales
##        LENGUAJES DE INTERFAZ
##   Profesor: MC. René Solis Reyes
##     Semestre febrero - junio 2026
----
# Practica Bloque: 4.5 📌 Codex + Wokwi para simular practicas Raspberry PicoW
# Objetivo:  USO DE CODEX
----

# 📝 Vazquez Muñoz, Briana Daniela y 23212083


-----

# Pico W Keypad + 12 LED Controller

Documentation-first repository for a **Raspberry Pi Pico W (RP2040)** project that reads a **4x4 membrane keypad** and controls **12 LEDs**.

> Core firmware logic is preserved from the provided source. This repository organizes files and adds production-grade documentation.

## Repository Structure

```text
.
├── CMakeLists.txt
├── diagram.json
├── include/
├── src/
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Features

- 4x4 keypad scan via `Keypad` library.
- 12 independent LED outputs on GPIO pins.
- Key-to-action mapping:
  - `1..8` -> turn on individual blue LEDs.
  - `9` -> turn on blue LED bank (1..8).
  - `0` -> turn off blue LED bank (1..8).
  - `A..D` -> turn on individual red LEDs.
  - `*` -> turn on red LED bank (A..D).
  - `#` -> turn off red LED bank (A..D).

## Components (from `diagram.json`)

- 1x Raspberry Pi Pico / Pico W (RP2040 target)
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red)
- 12x 220Ω resistors (LED current limiting)
- 4x 1kΩ resistors (keypad row pull-up network to 3V3)
- Jumper wires

## Build / Flash Options

### Option A: Wokwi (recommended for this exact source)

This source uses **Arduino-style APIs** (`setup()`, `loop()`, `Keypad.h`).

1. Create a new Wokwi Raspberry Pi Pico project.
2. Copy `src/main.cpp` into the simulation code file.
3. Import/replace circuit with `diagram.json`.
4. Run simulation and open serial monitor if needed.

### Option B: Real Pico W hardware (Arduino-Pico core)

1. Install Arduino IDE.
2. Install **Raspberry Pi Pico/RP2040 (Arduino-Pico)** board package.
3. Install **Keypad** library via Library Manager.
4. Open `src/main.cpp` as sketch content.
5. Select board: **Raspberry Pi Pico W**.
6. Put Pico W in BOOTSEL mode and upload.

### Option C: Native Pico SDK

A minimal `CMakeLists.txt` scaffold is included for repository consistency, but current firmware is still Arduino-style. To use Pico SDK directly, APIs would need adaptation (intentionally not done to preserve logic).

## Wi-Fi Notes

- This firmware does **not** use Wi-Fi.
- No credentials are required.
- If Wi-Fi is added later, use environment/config files and never hardcode SSID/password in source control.

## Documentation

- Wiring details: `docs/wiring.md`
- Firmware/module architecture: `docs/architecture.md`
