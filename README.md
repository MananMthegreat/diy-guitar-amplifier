# DIY Guitar Amplifier

A small, breadboard-built guitar amplifier developed using an NTE451 JFET preamp and an LM386N-1 power amplifier.

## V1 Status

**Functional prototype.**

V1 has now been successfully tested with a guitar signal and produces amplified audio through the 8 Ω speaker. The circuit remains a breadboard prototype, but the core analog signal path is working.

V1 has one user control: an **A10K master volume**.

## V1 Signal Path

```text
Guitar / pickup
      ↓
1/4" input jack
      ↓
NTE451 JFET preamp
      ↓
A10K master volume
      ↓
LM386N-1 amplifier
      ↓
220 µF output coupling capacitor
      ↓
8 Ω / 0.5 W speaker
```

## Hardware

| Component | Value / Part |
|---|---|
| Amplifier IC | LM386N-1 |
| Input/preamp transistor | NTE451 N-channel JFET |
| Power supply | 9 V DC power cable |
| Speaker | 8 Ω, 0.5 W |
| Volume control | A10K potentiometer |
| Input | 1/4" chassis guitar jack |
| Drain resistor | 3.9 kΩ |
| Source resistor | 1 kΩ |
| Gate resistor | 1 MΩ |
| Input coupling capacitor | 47 nF |
| Output coupling capacitor | 220 µF electrolytic |
| Output stability network | 10 Ω + 47 nF Zobel network |
| Power indicator | LED + 220 Ω resistor |
| Build platform | Solderless breadboard |

## NTE451 Bias Testing

The NTE451 stage was tested from the 9 V supply before being used as the preamp.

Initial test conditions:
- 3.9 kΩ drain resistor from +9 V to the drain
- Gate connected to ground
- Adjustable source resistance to ground

The initial drain voltage was approximately **0.6 V**. After adjusting the source resistance, the drain reached approximately **4.17 V** while the source was approximately **1.20 V**.

The adjustable resistance was then replaced with a **1 kΩ fixed source resistor**, producing a drain voltage of approximately **3.9 to 4.0 V**.

These measurements were used to establish the V1 bias point.

## LM386 Measurements

Measured on the V1 circuit:

| Pin | Function | Measured voltage |
|---|---|---:|
| 4 | Ground | ~0.01 V |
| 5 | Output | ~5.3 V DC |
| 6 | Supply | ~9.0 V DC |

The approximately half-supply DC voltage at the LM386 output is consistent with its biased output stage.

## First Successful Audio Test

After the electrical troubleshooting and bias checks, V1 successfully produced amplified guitar audio through the speaker.

The amplifier was tested as a real analog signal chain rather than only being verified by DC voltage measurements. This confirmed that the input, preamp, volume control, LM386 stage, output coupling, and speaker path were functioning together.

The project is still considered a prototype. The 8 Ω / 0.5 W speaker is small, so high output levels can produce audible distortion. The master volume provides control over the signal level entering the LM386 stage.

## Troubleshooting Journey

V1 did not work immediately. The build required repeated electrical checks and isolation of individual sections.

Key debugging steps included:

1. Verifying the 9 V supply.
2. Checking LM386 supply, ground, and output voltages.
3. Testing the NTE451 stage independently.
4. Measuring the NTE451 drain and source voltages.
5. Using an adjustable resistance to find a useful operating point.
6. Replacing the temporary adjustment with a 1 kΩ source resistor.
7. Verifying capacitor values and polarity.
8. Checking the guitar jack tip and sleeve connections.
9. Adding and verifying the A10K master volume control.
10. Testing the complete signal path with a guitar.

The final successful test confirmed that the problem was not simply a power or speaker issue: the circuit was capable of passing and amplifying the guitar signal.

## Design Notes

V1 deliberately avoids digital processing and extra controls. There is no ESP32, OLED, Bluetooth, Wi-Fi, digital effects, or EQ in this version.

The goal of V1 was to learn the fundamentals of:

- JFET biasing
- Analog signal amplification
- LM386 amplifier circuits
- Coupling capacitors
- Volume control
- Speaker output stages
- Breadboard prototyping
- Measuring and debugging a real circuit

## Future Development

V2 is planned as a separate development stage. Possible future features include an ESP32-based digital section, display controls, EQ/effects, and a modular extension that keeps the basic V1 amplifier usable on its own.

Those features are intentionally **not part of V1**.

## Repository Structure

```text
├── README.md
├── docs/
│   ├── V1_BUILD.md
│   ├── COMPONENTS.md
│   ├── TESTING.md
│   └── TROUBLESHOOTING.md
├── schematics/
│   └── V1_SCHEMATIC.md
├── images/
│   └── README.md
└── v2/
    └── README.md
```

## Author

Manan Mishra
