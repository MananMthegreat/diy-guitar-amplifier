# V1 Schematic

## Functional Schematic

```text
                         +9 V DC
                           │
                     ┌─────┴─────┐
                     │           │
                   3.9 kΩ      LED + 220 Ω
                     │           │
                     │          GND
                     │
                  NTE451
                ┌────D
Guitar TIP ────G      │
          │     │     S
          │     │     │
        1 MΩ    │    1 kΩ
          │     │     │
         GND   GND   GND
                     
NTE451 drain
     │
    47 nF
     │
     ├────────── A10K master volume ──────────┐
     │                                          │
     │                                      wiper
     │                                          │
     │                                     LM386 pin 3
     │                                          │
     │                                      LM386N-1
     │                                          │
     │                                     pin 5 output
     │                                          │
     │                       ┌──── 10 Ω ─── 47 nF ─── GND
     │                       │
     │                     220 µF
     │                       │
     │                       └────── 8 Ω / 0.5 W speaker ─── GND
     │
     └── other volume outer lug → GND

LM386 pin 6 → +9 V
LM386 pin 4 → GND
LM386 pin 2 → GND / input reference
LM386 pins 1 and 8 → no external gain capacitor in V1
LM386 pin 7 → unused in minimal V1
```

## Connection Summary

### NTE451

- Drain → 3.9 kΩ → +9 V
- Source → 1 kΩ → GND
- Gate → guitar TIP
- Gate → 1 MΩ → GND
- Drain → 47 nF coupling capacitor → volume input

### A10K Master Volume

- Outer lug 1 → 47 nF coupling capacitor from NTE451 drain
- Wiper → LM386 pin 3
- Outer lug 2 → GND

### LM386N-1

- Pin 2 → GND
- Pin 3 → volume wiper
- Pin 4 → GND
- Pin 5 → output coupling capacitor
- Pin 6 → +9 V
- Pin 7 → unused
- Pins 1 and 8 → open in V1

### Output

- LM386 pin 5 → 220 µF electrolytic capacitor positive terminal
- Capacitor negative terminal → speaker positive
- Speaker negative → GND
- LM386 pin 5 → 10 Ω resistor → 47 nF capacitor → GND

## Important Polarity

The **220 µF electrolytic capacitor is polarized**. Its positive terminal goes toward LM386 pin 5.

The 47 nF coupling capacitor and 47 nF Zobel capacitor are non-polar.

## Breadboard Implementation

This is a functional documentation diagram, not a physical breadboard layout. The exact breadboard row positions may change during development.

Always verify the physical connections with a multimeter before applying power.
