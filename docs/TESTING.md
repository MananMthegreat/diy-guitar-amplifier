# V1 Testing

## Current Status

V1 is a **functional analog guitar amplifier prototype**.

The circuit has been successfully tested with a guitar signal and produced amplified audio through the 8 Ω / 0.5 W speaker.

## Electrical Measurements

### NTE451 bias testing

- Initial drain voltage: approximately **0.6 V**
- Adjusted drain voltage: approximately **4.17 V**
- Source voltage during adjustment: approximately **1.20 V**
- Final drain voltage with the 1 kΩ source resistor: approximately **3.9 to 4.0 V**

### LM386 measurements

| Pin | Function | Measured voltage |
|---|---|---:|
| 4 | Ground | ~0.01 V |
| 5 | Output | ~5.3 V DC |
| 6 | Supply | ~9.0 V DC |

## Audio Test

The final V1 circuit successfully passed a guitar signal through the NTE451 preamp, A10K master volume, LM386N-1 amplifier, output coupling capacitor, and 8 Ω speaker.

This confirms the complete analog signal path is functioning.

## Observations

The small 0.5 W speaker can become audibly distorted when driven hard. This is not being treated as evidence that the entire amplifier is non-functional. The master volume can be used to reduce the signal level entering the LM386 stage.

## Test Limitations

V1 remains a breadboard prototype. More detailed measurements such as frequency response, output power, distortion, and signal amplitude under load have not been characterized yet.
