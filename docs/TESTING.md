# V1 Testing

## Current Status

V1 is **currently under development**. Electrical measurements have been taken, but full audio testing with a guitar has not been completed.

No claim of finished audio performance is made in this repository until a real guitar signal has been tested.

## Power Checks

Before connecting an audio source:

1. Confirm the supply is approximately 9 V DC.
2. Confirm circuit ground is continuous across the required breadboard rails.
3. Confirm the power LED operates through its 220 Ω resistor.
4. Confirm there are no accidental shorts between +9 V and ground.

## NTE451 Bias Test

Documented measurements from the V1 bias setup:

| Measurement | Approx. value |
|---|---:|
| Initial drain voltage | 0.6 V |
| Adjusted drain voltage | 4.17 V |
| Adjusted source voltage | 1.20 V |
| Fixed source resistor | 1 kΩ |
| Final drain voltage | 3.9 to 4.0 V |

The final 1 kΩ source resistor was selected after the adjustable-resistance bias test.

## LM386 DC Test

Measured on the V1 circuit:

| Pin | Function | Measured voltage |
|---|---|---:|
| 4 | Ground | ~0.01 V |
| 5 | Output | ~5.3 V |
| 6 | Supply | ~9.0 V |

The output pin sitting near half the supply voltage is expected for the LM386's biased output stage. The output coupling capacitor prevents this DC bias from being applied directly to the speaker.

## Audio Test Plan

Once a suitable guitar signal source is available:

1. Set the master volume to minimum.
2. Power the amplifier.
3. Confirm the power LED is on.
4. Connect the guitar/pickup to the input jack.
5. Slowly increase the master volume.
6. Listen for clean signal, excessive noise, oscillation, or distortion.
7. If the circuit does not respond, check the signal path stage by stage.

## Useful Measurements

A multimeter can verify DC operating points and power connections. It is not a replacement for an oscilloscope when checking small audio waveforms.

Useful DC checks include:

- Supply voltage
- NTE451 drain voltage
- NTE451 source voltage
- LM386 pin 4 ground
- LM386 pin 5 output bias
- LM386 pin 6 supply

## Test Results Log

| Date | Test | Result | Notes |
|---|---|---|---|
| TBD | Power check | Pending | Final documented test after build verification |
| TBD | NTE451 bias | Completed | Drain approximately 3.9 to 4.0 V with 1 kΩ source resistor |
| TBD | LM386 DC bias | Completed | Pin 5 approximately 5.3 V at 9 V supply |
| TBD | Guitar audio | Pending | Electric guitar currently unavailable |

## Testing Philosophy

Measurements in this project are recorded as measured values, not assumed values. The repository will be updated as new tests are performed.
