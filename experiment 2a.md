## CS Ampliier with active load
Aim:
To design and simulate a CS amplifier with active load and analyze its gain and bandwidth.
Given specifications,

VDD = 2 V

Power ≤ 1.5 mW

CL = 1 pF

Technology = 180 nm

Vth(n) = 0.36 V

Vtp(p) = 0.39 V

Assume,

Vov = 0.25 V


Circuit diagram:

<img width="1487" height="961" alt="Screenshot 2026-03-02 224150" src="https://github.com/user-attachments/assets/8808d4a1-a653-4b83-aa83-180c9c12188b" />


Theory:

A Common Source (CS) amplifier is a MOSFET amplifier configuration in which the source terminal is common to both input and output. 
The input signal is applied at the gate and the output is taken from the drain. 
In this experiment, NMOS acts as the amplifying device and PMOS acts as an active load.
Overdrive voltage:

Vov = VGS - VTH

Transconductance:
gm = 2ID / Vov

Output resistance:
ro = 1 / (λ ID)

Voltage Gain:
Av = -gm (ro_n || ro_p) / (1 + gmRs)

Bandwidth:
BW = fH - fL

To find Rs:

 VS = 0.2 V

Drain current ID = 500 uA

VS = ID × RS

RS = VS / ID

RS = 0.2 / (500 × 10^-6)

RS = 400 Ω

For proper biasing and keep NMOS in saturation region.

VDS ≥ VOV

We assumed,

VOV = 0.25 V

With VS = 0.2 V,

Design Calculations:

P = VDD × ID

P = 2 × 500uA

P = 1000uA


VGS = Vov + VTH

VGS = 0.25 + 0.36

VGS = 0.61 V


Vout ≈ (VDD / 2)+VS

Vout ≈ (2 / 2)+0.2

Vout ≈ 1.2 V

Assume, VS=0.2V

VDS = Vout − VS

VDS = 1.2 − 0.2

VDS = 1 V


For PMOS:

VSD = VDD − Vout

VSD = 2 − 1.2

VSD = 0.8 V

VOV(p) = 0.25 V

Since VSD > VOV(p),

PMOS operates in saturation region.

gm = 2ID / Vov

gm = (2 × 500A) / 0.25

gm = 4 mS


Assume λ = 0.1

ro = 1 / (λ ID)

ro = 1 / (0.1 × 500µA)

ro = 20 kΩ

(ro_n || ro_p) ≈ 10 kΩ


Av = -gm (ro_n || ro_p) / (1 + gmRs)

Av = (-4mS × 10kΩ) / (1 + (4mS × 400Ω))

Av ≈ -15.384 V/V

Av(dB) = 20 log(15.384)

Av(dB) = 23.741 dB


Procedure:

1. Draw schematic in LTspice.

2. Place NMOS and PMOS transistors.

3. Set VDD = 2 V.

4. Apply bias voltage 1.36 V to PMOS gate.

5. Apply input signal:
   SINE(0.81 10m 1k)

6. Add Rs = 400 Ω.

7. Include commands:
   .op
   .tran 5m
   .ac dec 10 000.1 100G

8. Run Operating Point analysis.

9. Run Transient analysis.

10. Run AC analysis.


Operating Point:

<img width="1594" height="792" alt="Screenshot 2026-03-02 223920" src="https://github.com/user-attachments/assets/2332ab1a-b76d-4c3e-a8d7-adde024cc2d2" />

VDD = 2V
Vbias = 1.36 V

Vout = 1.203 V

ID(M1) = 545 uA

ID(M2) = 545 uA


Transistors operating in saturation region.

ID=un*Cox*(W/L)*(Vov)^2*(1/2)

Theoritical calculated width, W for NMOS = 38.854 um, W for PMOS = 91.um.

In Simulation for ID=545 uA and Vout=1.2V , W for NMOS = 220um, W for PMOS = 222.5um


Transient Analysis:

Input waveform

<img width="1910" height="823" alt="Screenshot 2026-03-02 224055" src="https://github.com/user-attachments/assets/c4eddaab-03c6-4fb8-bc1d-df5024a6c6ef" />

Output Waveform

<img width="1919" height="829" alt="Screenshot 2026-03-02 224031" src="https://github.com/user-attachments/assets/ecbd254b-abfc-48ee-86b1-5fda162090d9" />



Input:

SINE(0.81 10m 1k)

10m = Peak amplitude

Vin(p-p) = 55.39V

Measured Vout ≈ 20V (approx)

Av = Vout(p-p) / Vin(p-p)

Av ≈ 26.76 V/V

Av(dB) = 28.54 dB


AC Analysis:

<img width="1910" height="833" alt="Screenshot 2026-03-02 224118" src="https://github.com/user-attachments/assets/b0969b98-6ad6-4bab-8fd9-84b85c024149" />


Midband Gain = 28.6 dB

High cutoff frequency (fH) = 29.35 MHz

Low cutoff frequency (fL) ≈ 0 Hz

Bandwidth:

BW = 29.35 MHz


Comparision:

Theoretical Gain = 23.74 dB

Simulated Gain = 28.6 dB

Theoretical Av = 15.384 V/V

Simulated Av = 26.76 V/V

Bandwidth = 29.35 MHz




Inference:

* Simulated gain is lower due to:

* Channel length modulation, which reduces output resistance 

* Parasitic capacitances and resistances present in practical MOSFET models.

* Body effect and mobility degradation in real devices.

* Source degeneration (if resistor is used), which reduces effective gm​

* Non-ideal biasing conditions.

