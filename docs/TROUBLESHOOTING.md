# V1 Troubleshooting

This document records the main checks and known issues for the V1 prototype.

## 1. No Audio

If the speaker produces no guitar signal:

- Confirm the 9 V supply is present.
- Confirm all grounds are connected together.
- Confirm the guitar/pickup plug reaches the jack TIP connection.
- Confirm the NTE451 gate has the 1 MΩ resistor to ground.
- Confirm the NTE451 drain resistor is 3.9 kΩ.
- Confirm the source resistor is 1 kΩ.
- Confirm the 47 nF coupling capacitor is connected from the NTE451 drain to the volume control.
- Confirm the volume wiper reaches LM386 pin 3.
- Confirm the LM386 is powered on pin 6 and grounded on pin 4.
- Confirm the 220 µF output capacitor polarity.
- Confirm the speaker is connected after the output capacitor.

## 2. Loud Hum or Static

Possible causes include:

- Poor breadboard ground connections
- Long jumper wires acting as antennas
- Floating input connections
- Incorrect jack terminal identification
- A noisy or poorly regulated 9 V supply
- Unwanted feedback between input and output wiring

Keep the input wiring short and physically separated from the speaker/output wiring where practical.

## 3. LM386 Output Has DC Voltage

The LM386 output pin normally has a DC bias voltage. A measured value of approximately 5.3 V at pin 5 with a 9 V supply was observed on this build.

Do not connect the speaker directly to pin 5. The 220 µF output coupling capacitor is required to block the DC component.

## 4. NTE451 Drain Voltage Is Wrong

The NTE451 operating point depends on the individual JFET. If the drain voltage is far from the documented V1 range, check:

- 3.9 kΩ drain resistor value
- 1 kΩ source resistor value
- Gate-to-ground 1 MΩ resistor
- NTE451 orientation and pin order
- Breadboard row placement
- Supply voltage

The NTE451 was empirically biased to approximately 3.9 to 4.0 V at the drain using the 1 kΩ source resistor.

## 5. Volume Control Does Not Work

The A10K potentiometer should be wired as:

```text
NTE451 coupling capacitor → outer lug
                              │
                           A10K pot
                              │
                        wiper → LM386 pin 3
                              │
                         other outer lug
                              ↓
                             GND
```

If the control works backwards, the two outer lugs can be swapped. The wiper should remain connected to LM386 pin 3.

## 6. Speaker Clicks or Pops

A click when power is applied can be related to the amplifier's output bias charging through the coupling capacitor. Persistent loud clicking or oscillation is not considered a completed result and should be investigated before normal use.

## 7. Breadboard Problems

Breadboards can create intermittent faults through poor contact or accidental row connections.

Check each important node individually instead of assuming nearby holes are connected. The center trench separates the two terminal-strip halves.

## Safety

Disconnect power before changing component wiring. Never short the 9 V supply deliberately. The LM386 output can drive a small speaker, but the 0.5 W speaker used in V1 should not be subjected to excessive power.

## Debugging Method

The preferred approach is to debug from the power supply toward the speaker:

```text
9 V supply
   ↓
NTE451 DC bias
   ↓
NTE451 signal output
   ↓
Volume control
   ↓
LM386 input
   ↓
LM386 output
   ↓
Coupling capacitor
   ↓
Speaker
```

Measure one stage at a time instead of changing several parts at once. This makes each change easier to evaluate.
