# V1 Build Guide

## Overview

V1 is a simple analog guitar amplifier built on a solderless breadboard. The design uses an NTE451 N-channel JFET as the input preamp and an LM386N-1 as the power amplifier.

**Status:** Currently under development

**Important:** V1 has not been confirmed with a guitar signal yet because an electric guitar is not currently available for testing.

## Signal Path

```text
Guitar / pickup
      ↓
1/4" input jack
      ↓
NTE451 JFET preamp
      ↓
47 nF coupling capacitor
      ↓
A10K master volume
      ↓
LM386N-1
      ↓
220 µF output coupling capacitor
      ↓
8 Ω / 0.5 W speaker
```

## Power

V1 is powered from a **9 V DC power cable**.

The LM386N-1 accepts a 4 V to 12 V supply, so 9 V is within its supply range.

A separate LED with a 220 Ω resistor is used as a power indicator.

## NTE451 Preamp

The NTE451 is configured as a self-biased common-source stage.

```text
+9 V
 │
3.9 kΩ
 │
Drain
 │
NTE451
 │
Source
 │
1 kΩ
 │
GND
```

The gate is connected to the guitar input and has a **1 MΩ resistor to ground** to establish the DC reference.

### Bias measurements

During the bias setup, the drain was initially measured at approximately 0.6 V. A temporary adjustable source resistance was then used to move the drain toward the middle of the supply. A drain voltage of approximately 4.17 V was reached with the source around 1.20 V.

The adjustable resistor was replaced with a **1 kΩ fixed source resistor**, producing a drain voltage of approximately 3.9 to 4.0 V.

These measurements are the documented V1 bias point. Individual JFETs can vary, so the measured circuit is more useful than assuming a single datasheet value.

## Master Volume

V1 has one user control: an **A10K audio-taper potentiometer**.

The wiring is:

- One outer lug: signal from the NTE451 coupling capacitor
- Middle lug / wiper: LM386 pin 3
- Other outer lug: ground

This makes the potentiometer the master volume control between the preamp and LM386 input.

## LM386 Stage

The LM386N-1 uses pin 3 as the non-inverting input and pin 5 as the output.

For V1:

- Pin 2: ground / inverting input reference
- Pin 3: master volume wiper
- Pin 4: ground
- Pin 5: output
- Pin 6: +9 V supply
- Pin 7: unused in the minimal V1 design
- Pins 1 and 8: no external gain capacitor in V1

The default LM386 voltage gain is 20 when pins 1 and 8 are left open.

## Speaker Output

The LM386 output is DC-biased, so the speaker is connected through a **220 µF electrolytic coupling capacitor**.

```text
LM386 pin 5 → 220 µF (+) → 220 µF (-) → speaker +
speaker - → GND
```

A **10 Ω resistor in series with a 47 nF capacitor** is connected from the LM386 output to ground as the output stability / Zobel network.

## Breadboard Notes

The circuit is being prototyped on a solderless breadboard. The center trench separates the two five-hole terminal strips, so connections crossing the center must use a jumper wire.

Power rails should also be checked with a multimeter because separate rail sections may not be electrically connected.

## Build Philosophy

V1 is intentionally small. The goal is to verify the analog signal chain, measure real circuit behavior, and debug the amplifier before adding digital features or extra controls.
