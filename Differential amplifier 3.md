## Circuit 3

## CMOS Differential Amplifier Analysis  (PMOS Current Mirror Load)

##  Overview  

This repository presents the analysis of a CMOS differential amplifier using a
PMOS current mirror as an active load. The circuit is designed for high gain and
balanced operation.

###  Components
- M1, M2 → NMOS differential pair  
- M3, M4 → PMOS current mirror  
- Tail current source → 1 mA  
- Supply voltage → 1.8 V  


##  1. DC Analysis  

### Input Bias  

Vin1 = 0.9V + 50mV sin(2π1000t)  
Vin2 = 0.9V + 60mV sin(2π1000t)  

For DC:

Vin1 = Vin2 = 0.9V  

<img width="451" height="435" alt="image" src="https://github.com/user-attachments/assets/53f2d483-3104-44c4-8c1a-4d80acafa8e6" />


## Current Distribution  

Itail = 1 mA  

ID1 = ID2 = Itail / 2  

ID1 = ID2 = 0.5 mA  

## Current Mirror  

M3 is diode-connected  

ID3 = 0.5 mA  

ID4 = 0.5 mA  

### Output Voltage  

Vout1 ≈ Vout2  

Vout ≈ 0.9 V  

### Region Check  

NMOS:  

VOV = VGS - VTH = 0.9 - 0.4 = 0.5 V  

→ Saturation  

PMOS:  

VTHp ≈ -0.4 V  

→ Saturation  

---

### DC Summary  

| Parameter | Value |
|----------|------|
| VDD | 1.8 V |
| Tail Current | 1 mA |
| ID1 | 0.5 mA |
| ID2 | 0.5 mA |
| Output Voltage | ≈ 0.9 V |
| Region | Saturation |


##  2. AC Analysis  

### Input Signals  

vin1 = 50 mV sin(ωt)  
vin2 = 60 mV sin(ωt)  


### Differential Input  

vid = vin1 - vin2  

vid = -10 mV  

|vid| = 10 mV  


### Transconductance  

gm = 2ID / VOV  

gm = 2 × 0.5 mA / 0.2 V  

gm = 5 mS  


### Output Resistance  

ron = 50 kΩ  
rop = 50 kΩ  

Rout = 25 kΩ  

### Voltage Gain  

Av = gm × Rout  

Av = 5 mS × 25 kΩ  

Av = 125  


### Output Voltage  

vo = Av × vid  

vo = 1.25 V  


### Frequency Response  

Input frequency = 1 kHz  

Bandwidth = MHz range  

→ Gain remains constant  

### AC Summary  

| Parameter | Value |
|----------|------|
| Differential Input | 10 mV |
| gm | 5 mS |
| Rout | 25 kΩ |
| Gain | 125 |
| Output | ≈ 1.25 V |


##  Conclusion  

- Balanced DC operation splits current equally  
- Active load improves gain  
- Small input signal gives large output  
- Circuit works efficiently within given frequency  


