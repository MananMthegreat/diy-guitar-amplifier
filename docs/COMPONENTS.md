# V1 Components

## Core Components

| Component | Value / Part | Purpose |
|---|---|---|
| JFET | NTE451, N-channel | Input preamp |
| Amplifier IC | LM386N-1 | Power amplifier |
| Speaker | 8 Ω, 0.5 W | Audio output |
| Potentiometer | A10K audio taper | Master volume |
| Input jack | 1/4" chassis jack | Guitar/pickup input |
| Power supply | 9 V DC power cable | Circuit power |

## Resistors

| Value | Quantity / Use | Purpose |
|---|---|---|
| 3.9 kΩ | NTE451 drain resistor | Sets drain load |
| 1 kΩ | NTE451 source resistor | Sets source bias |
| 1 MΩ | NTE451 gate resistor | Provides DC gate reference |
| 10 Ω | Zobel network | Output stability |
| 220 Ω | LED resistor | Limits LED current |

## Capacitors

| Value | Type / Use | Purpose |
|---|---|---|
| 47 nF | Input/preamp coupling | Blocks DC between stages |
| 220 µF | Electrolytic output coupling | Blocks LM386 output DC from speaker |
| 47 nF | Zobel network | High-frequency output stabilization |

## Indicator

- LED
- 220 Ω series resistor

The LED is connected to the 9 V supply as a simple power-on indicator.

## Prototype Hardware

- Solderless breadboard
- Jumper wires
- 9 V DC power cable
- 8 Ω / 0.5 W speaker

## Parts Not Used in V1

V1 intentionally does **not** include:

- ESP32
- OLED display
- Bluetooth
- Wi-Fi
- Digital effects
- Digital EQ
- Footswitch controls
- Additional user controls
- LM386 gain capacitor between pins 1 and 8

These are potential future-development items and are not part of the V1 circuit.

## Component Selection Notes

The NTE451 has relatively wide device-to-device characteristics, so its operating point was established experimentally using the actual device rather than relying only on a nominal datasheet value.

The A10K audio-taper potentiometer is used as the single master volume control. Its wiper feeds the LM386 non-inverting input.
