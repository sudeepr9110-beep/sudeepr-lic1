# Experiment 2b

# Aim: 

To design and analyze a Common Source amplifier with current source load.


Given specifications:

VDD = 2V

Power ≤ 1.5 mW

CL = 1 pF

Technology = 180 nm

Ln = 560 nm

Vth = 0.36 V

Vtp = 0.39 V

Circuit diagram:
<img width="1347" height="886" alt="image" src="https://github.com/user-attachments/assets/96e55bbc-d26c-4dac-a6da-bf7412ff59ab" />


Assumed parameters:

VOV = 0.2 V

λn = 0.1

λp = 0.12

Theory:

A Common Source amplifier provides voltage gain
of 180° phase shift.


M1 → Amplifying NMOS

M2 → Current source NMOS

M3 → PMOS active load


In saturation:

ID = (µCox /2)(W/L)(VOV)^2

gm = 2ID / VOV

ro = 1 / (λID)

Voltage gain:

Av = -gm (ro1 || ro3)


DC Design Calculations:


1. Power :

P = VDD × ID

P = 2 × 500uA

P = 1000 mW

2. VG Calculations:

 For M1(PMOS), 

0.25 = VSG − 0.39

VSG = 0.64 V

VG3 = 2 − 0.64

VG3 = 1.36 V

For M2,

VOV = VGS − VTH

VGS = 0.25 + 0.36

VGS = 0.61 V

Assume VS1 = 0.3 V

VG2 = VGS + VS2

VG2 = 0.61 + 0.3

VG2 = 0.91 V

For M3,

VS3 = 0 V

VGS3 = 0.61 V

VG3 = 0.61 V

3. Output Voltage:

Vout ≈ VDD / 2 + VRS

Vout = 2 / 2 + 0.3

Vout = 1.3 V


4. Saturation Verification:

M1,

VDS1 = 1.3 − 0.3

VDS1 = 1 V

1 ≥ 0.25 

M2,

VDS2 = 0.3 V

0.3 ≥ 0.25 

M3,

VSD3 = 2 − 1.3

VSD3 = 0.7 V

0.7 ≥ 0.25 

5. Small Signal Parameters:

gm = 2ID / VOV

gm = (2 × 500uA) / 0.25

gm = 4 mS

ro1 = 1 / (0.1 × 500uA)

ro1 = 20 kΩ

ro3 = 1 / (0.12 × 500uA)

ro3 = 16.66 kΩ

Rout = ro1 || ro3

Rout = 9.088 kΩ


6. Theoretical gain:

Av = (-gm*(ro1||ro3))/(1+(gm*ro2))

Av = -0.44 V/V

Av(dB) = 20 log(0.44)

Av(dB) ≈ -7.130 dB


7. Width Calculations:

NMOS,

ID = (µnCox /2)(W/L)(VOV)^2

500µA = (µnCox /2)(W/560nm)(0.25)^2

Wn = 38.854 um

PMOS,

500µA = (µpCox /2)(W/560nm)(0.2)^2

Wp = 91.2 um


Operating Point:
<img width="1669" height="814" alt="Screenshot 2026-03-02 220400" src="https://github.com/user-attachments/assets/4697a250-9d56-4245-b05e-1b797ccbae86" />


ID = 503.33 uA

Vout = 1.301 V

Biasing is verified with this values


Transient Analysis:

Input wavwform

<img width="1909" height="888" alt="Screenshot 2026-03-02 222836" src="https://github.com/user-attachments/assets/247bee2f-4353-4c54-8d7b-a2a41ea3f434" />

Output waveform

<img width="1905" height="896" alt="Screenshot 2026-03-02 222648" src="https://github.com/user-attachments/assets/c954d521-973b-4000-b290-7c0d7884a878" />


SINE(0.91 10m 1k)

Vin(p-p) = 19.999 V

Vout(p-p) = 46.889 V

Av = 2.344 V/V

Av(dB) = 7.399 dB


AC Analysis:



