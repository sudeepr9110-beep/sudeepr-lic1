# **Experiment 04**

## **Differential Amplifier Analysis**



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

<img width="590" height="550" alt="image" src="https://github.com/user-attachments/assets/630399fb-a218-4941-aa84-e49a2268c95e" />


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


  
### **Case 1: Small Input**

[
Vid < sqrt{2}VOV
]

<img width="1915" height="1084" alt="image" src="https://github.com/user-attachments/assets/98f3ab44-3ad7-45d8-ace7-b008ebcfb6f3" />


**Observation:**

* Output is sinusoidal
* No distortion


### **Case 2: Large Input**

[
Vid> qrt{2}V_{OV}
]

**Observation:**

* Output becomes distorted
* One MOSFET turns OFF



### **Comparison**

* Small input → linear amplifier
* Large input → non-linear behavior


# **Step 6: AC Analysis**

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
