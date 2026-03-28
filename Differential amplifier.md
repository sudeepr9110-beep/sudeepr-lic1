# **Experiment 04**

## **Differential Amplifier Analysis**

## **Circuit 1



## **Aim**

To design and analyze a MOS differential amplifier for the given specifications and 
study its DC operating point, transient response, and frequency characteristics.

## Circuit 1

## **Given Specifications**

*  VDD = 0.9V 
*  VSS = -0.9V 
*  VICM = 0V 
*  VOCM = 0V 
*  VP = -0.7V 
*  Channel Length ( L = 540nm )
*  Power ( P = 2.2mW ) 


## **Circuit Description**

The circuit consists of two identical NMOS transistors forming a differential pair.
A constant current source is connected at the common source node, and resistors are
used as loads at the drain terminals.

Inputs are applied to the gates, and outputs are taken from the drains. The circuit
amplifies only the difference between the inputs.

<img width="959" height="547" alt="image" src="https://github.com/user-attachments/assets/346b8078-7fa2-4330-be9c-40e6ede559fc" />


Using power relation:

[
P = V * I 

ISS = P / VDD-VSS
]

[
ISS = 2.2mW / 1.8V  = 1.22mA
]



### **Current Distribution**

[
ID = ISS / 2 = 0.61mA
]

RD = VDD / ID =	0.9 / 0.61 mA	= 1.475 kΩ

Vout(max) =	VDD	=	0.9 V

Vout(min) =	VDD - (ID × RD) =	0.9 - 0.9 =	0 V

VGS =	Vg − Vs	= 0 − (−0.7) =	0.7 V

Vov =	VGS − VT	= 0.7 − 0.366 = 	0.334 V

W = (2·ID·L) / (unCox·Vov²) =	(2 × 0.61mA × 540nm) / (230.3µA × 0.334²)	= 25.67 um
 
# **Step 1: DC Analysis**

### **Operating Point**

<img width="772" height="566" alt="Screenshot 2026-03-28 223150" src="https://github.com/user-attachments/assets/754cc548-2440-4a65-b339-185118ab83b9" />


### **Observations**

* Equal drain currents → symmetry
* Output voltage ≈ 0 → balanced condition
* Source node ≈ ( -0.7V )


### **Conclusion (DC)**

The circuit is properly biased and both MOSFETs operate in saturation region.



# **Step 2: Common Mode Limits**

### **Minimum Value**

[
VCM(min) = VP + VT
]

[
V{CM(min) = -0.7 + 0.366 = -0.334V
]


### **Maximum Value**

[
VCM(max) = VD + VT
]

[
VCM(max) = 0 + 0.366 = 0.366V
]


### **Range**

[
−0.334V <= VCM​ <= 0.366V
]


# **Step 3: Linear Range Condition**

[
Vid < sqrt{2}Vov

]

* Both transistors remain active
* Current sharing is smooth
* Output is linear

---

# **Step 4: Gain (Small Signal)**

[
g_m = 2I_D /{V_{OV}
]

gm = 2*0.61mA / 0.3 = 4.07mS
[

r_{o} = {1} / {lambda* I_{D}} 

r_{o} = {1} / {0.1*0.61} = approx 16.4kohm

R_{eff} = R_{D} || r_{o}

R_{eff} = 1.47k*16.4k / 1.47k+16.4k = 1.35kohm

A_v = g_m* R_D
]

A_{v} = 4.07 * 10^{-3} * 1350 = approx 5.5


 Larger channel length (540 nm) gives:

* Higher output resistance
* Slightly higher gain

---

# **Step 5: Transient Analysis**


<img width="1915" height="1084" alt="image" src="https://github.com/user-attachments/assets/bc3174a0-def8-46b9-aec4-61057c946238" />

  
### **Case 1: Small Input**

[
Vid < sqrt{2}VOV
]

<img width="1363" height="589" alt="image" src="https://github.com/user-attachments/assets/a9a22b2e-f389-460e-bcd7-12ff7ba95ca3" />



**Observation:**

* Output is sinusoidal
* No distortion


### **Case 2: Large Input**

[
Vid> qrt{2}V_{OV}
]


<img width="1353" height="584" alt="image" src="https://github.com/user-attachments/assets/4f0d6801-1dc0-4c04-b83b-7469dd65e08e" />


**Observation:**

* Output becomes distorted
* One MOSFET turns OFF



### **Comparison**

* Small input → linear amplifier
* Large input → non-linear behavior


# **Step 6: AC Analysis**


<img width="1914" height="991" alt="image" src="https://github.com/user-attachments/assets/c250245d-b920-4e8a-89c3-ffcd57f74020" />


<img width="1348" height="317" alt="image" src="https://github.com/user-attachments/assets/17a1a4b3-0cc6-4320-838e-4156b26e1ed3" />



# Midband Gain

From AC simulation :

A_{v} = 12.45dB  

Corresponding linear gain:

A_{v} = 10^{(12.45/20)} =approx 4.19

# −3 dB Gain

A_{v(-3dB)} = 12.45 - 3 = 9.45dB

# Cutoff Frequencies

Lower cutoff frequency:

f_{L} = 0Hz 

Upper cutoff frequency (from graph):

f_{H} = 316.2MHz

# Bandwidth


<img width="1353" height="670" alt="image" src="https://github.com/user-attachments/assets/41bf5824-e88d-4538-860f-c63e53bfbe6c" />


BW = f_{H} - f_{L} = approx 316.2MHz}



* Gain remains constant in midband
* Bandwidth is limited by ( C_L )
* Gain-bandwidth product remains nearly constant


# **Step 7: Comparison with Theory**

* DC results match expected values
* Gain obtained is close to theoretical
* Slight variation due to practical effects


# **Conclusion**

The MOS differential amplifier operates correctly within the specified conditions.
It provides linear amplification for small input signals and shows non-linear behavior
for large inputs. The simulation results are in good agreement with theoretical 
expectations.


## **Circuit 2**

##  Aim

To design and analyze a CMOS differential amplifier using an active load, determine its DC operating point, and evaluate its performance in terms of gain, linearity, and frequency response using LTspice.


##  Introduction

A differential amplifier is a fundamental analog building block used to amplify the difference between two input signals while rejecting common-mode signals. It is widely used in operational amplifiers, comparators, and communication circuits.

In this design, a PMOS current mirror is used as an active load instead of resistors. This approach improves gain, enhances output resistance, reduces power consumption, and is highly suitable for integrated circuit implementation.


##  Circuit Description

<img width="1233" height="920" alt="image" src="https://github.com/user-attachments/assets/0b67d802-b7b0-4824-9eba-df8a35eb6516" />

The circuit consists of:

- **M1, M2** → NMOS differential pair  
- **M3, M4** → PMOS current mirror (active load)  
- **M5** → Tail current source  

###  Working Principle

- A constant current is provided by the tail transistor (M5)  
- The current splits between M1 and M2 based on input difference  
- PMOS current mirror converts differential current into output voltage  
- Outputs are taken from the drain terminals  

## Given Parameters

| Parameter | Value |
|----------|------|
| VDD | 0.9 V |
| VSS | -0.9 V |
| Power (P) | 2.2 mW |
| Threshold Voltage (V_T) | ≈ 0.4 V |
| Overdrive Voltage (V_ov) | ≈ 0.39 V |
| Channel Length (L) | 540 nm |


##  Design Calculations

###  Tail Current

[
I_{SS} = {P} / {V_{DD} - V_{SS}} = {2.2{ mW} / {1.8 V} = approx 1.22mA
]

###  Branch Current

[
I_D = {I_{SS}} / {2} = approx 0.61mA
]


###  Bias Voltage

[
V_{GS} = V_T + V_{ov} = 0.34 + 0.3 = 0.64V
]

[
V_B = V_S + V_{GS} = -0.9 + 0.64 = approx -0.26V
]

##  DC Operating Point Analysis

###  Simulation Results

- Tail current ( I_{SS} = approx 1.23 mA )  
- Branch currents ( I_{D1} = I_{D2} = approx 0.615 mA )  
- Output voltages ( V_{out1} = V_{out2} = approx -0.055 V)  
- Source node voltage ( V_p =approx -0.724 V)

###  Interpretation

- Equal current distribution confirms proper symmetry  
- Equal outputs indicate zero differential input  
- All transistors operate in saturation region  
- Circuit is correctly biased and stable  


##  Input Common Mode Range (ICMR)

###  Minimum Value

[
V_{ICM(min)} = V_S + V_T = -0.6 + 0.4 = -0.2V
]


###  Maximum Value

[
V_{ICM(max)} = V_D - V_{ov} = 0.6 - 0.3 = 0.3 V
]


### Final Range

[
-0.2 V <= V_ICM <= 0.3 V
]


##  Differential Input Range (Linearity)

[
Vid(max) ​= sqrt 2 * Vov ​= 0.42 V
]

- Linear operation: ( |V_{id}| < 0.42 V )  
- Nonlinear operation: ( |V_{id}| > 0.42 V )


##  Transient Analysis

###  Case 1: Small Signal

(a) Case 1: V_id < √2 V_ov

- ( V_{id} = 20 mV)

**Observation:**
- Output is sinusoidal  
- No distortion  
- 180° phase difference  

 Circuit operates in linear region  


###  Case 2: Large Signal

(b) Case 2: V_id > √2 V_ov

- ( V_{id} = 600 mV)

- <img width="1912" height="486" alt="image" src="https://github.com/user-attachments/assets/f02251f7-0d80-4ae4-9f29-de694d6fb2e3" />


**Observation:**
- Output waveform is distorted  
- Clipping occurs  
- One transistor dominates conduction  

Circuit operates in nonlinear region  

##  AC Analysis

<img width="1883" height="473" alt="image" src="https://github.com/user-attachments/assets/959a0f21-b6c1-47b4-8db9-ed5a22cd76b0" />

###  Midband Gain

[
A_v = 6 dB 

Convert to linear:

A_v = 10^(6/20) = 2
]


###  Cutoff Frequencies

- Lower cutoff frequency ≈ 0 Hz  
- Upper cutoff frequency ≈ 3–5 GHz  


###  Bandwidth

[
BW = 4 GHz
]


##  Key Points

- Active load increases gain due to high output resistance  
- Current mirror improves matching and efficiency  
- Differential operation reduces noise  
- High bandwidth indicates suitability for high-speed applications  



##  Conclusion

The CMOS differential amplifier with active load is successfully designed and analyzed. The circuit operates with proper biasing and symmetry, ensuring equal current distribution under balanced conditions. It achieves a midband gain of approximately 6 dB and exhibits a wide bandwidth in the GHz range. The amplifier behaves linearly for small differential inputs and becomes nonlinear for large signals. Overall, the design demonstrates efficient and stable performance suitable for modern analog integrated circuits.



