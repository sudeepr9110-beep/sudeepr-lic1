# Experiment 1: CS Amplifier
## Aim
To implement and analyze a PMOS-based Common Source amplifier in LTSpice using the TSMC 180 nm technology

## Theory
A Common Source (CS) amplifier using a PMOS transistor is a single-stage voltage amplifier in which the source terminal is common to both input and output. In this arrangement, the input is applied to the gate, and the output is taken from the drain, while the source is tied to the supply voltage VDD.

For a PMOS transistor, the current flows when:
VSG > |VTP|

For the transistor to act as an amplifier, it must be in the saturation region, where the drain current is nearly constant and controlled by the gate voltage. For saturation, the transistor satisfies the following condition:
VSD > VSG-|VTP|

 In saturation, the drain current is expressed as:
 
 ID ​= (1/2)​μp​Cox​(W/l)*​(VSG​−∣VTP​∣)^2
 
 A small AC signal is applied to the gate, resulting in a small variation in VSG,, which in turn changes the drain current. The varying current through the load results in a varying output voltage, leading to amplification.

The small-signal voltage gain of a CS amplifier is expressed as:
Av = -gmRout
where

𝑔m = transconductance
Rout = output resistance

The negative sign shows that there's a 180 ° phase difference between the input and affair signals. 
 
 The transconductance value is given by 
 gm = (2ID/Vov)
Where Vov = VSG-|VTP| is a overdrive voltage

The power  dispersion in the circuit is given by 
P = VDD * ID

# Circuit Diagram
<img width="1109" height="851" alt="Screenshot 2026-02-24 224159" src="https://github.com/user-attachments/assets/5b60dae7-7597-4a66-9249-a1a673b2d547" />

Given design values
VDD = 2V,
Pmax = 1.5mW,
CL = 1pF,
Ln = 560nm

# Calculation
P = VDD * ID

ID = P/VDD

ID = 1.5*10^-3/ 2 V 

ID = 750uA 

Channel Length (L) = 180nm.

Supply Voltage (Vdd) = 2V.

# DC Analysis
DC analysis of the PMOS Common Source amplifier is employed to find its operating point, also known as the Q-point. In this analysis, only DC voltages and currents are taken into account, and the AC signal is assumed to be zero. The source is tied to ( VDD ), and a proper gate bias voltage is applied such that ( VSG > |VTP| ), thus turning the transistor ON and keeping it in the saturation region. The drain current ( ID ) is determined using the saturation current equation, and the output DC voltage is determined as ( VD = VDD - IDRD ). The bias is adjusted to ensure that the transistor is in saturation, the output voltage is near the middle of the supply voltage for maximum signal swing, and the power dissipation ( P = VDD/ ID ) is within the defined limit.
# DC Sweep
DC Sweep analysis is used to see how the Common Source amplifier works when a DC voltage changes over a range. Usually, the gate voltage (VGS) is varied while keeping other values constant. This allows us to observe how the drain current (ID) and output voltage (VD) respond. When VGS is below the threshold voltage, the MOSFET stays OFF, and the drain current is almost zero. As VGS rises above the threshold, the MOSFET turns ON, and the drain current increases. This reveals different regions of operation, including cutoff, triode, and saturation. This analysis helps identify the right operating point (Q-point) and understand the static characteristics of the amplifier.
# AC Analysis
The AC analysis of a PMOS Common Source amplifier is employed to find the small-signal voltage gain and phase relationship between the input and output of the amplifier by applying a small AC signal to the input while maintaining the DC conditions constant. In AC analysis, the DC power supply ( VDD ) is considered as AC ground, and the transistor is modeled using a small-signal equivalent circuit. A small change in the gate-to-source voltage results in a corresponding small change in the drain current expressed as ( id = gm vsg ), where ( gm ) is the transconductance. This fluctuating drain current, in turn, causes an amplified output voltage through the output resistance. The voltage gain is given by ( Av = -gm Rout ), and the negative sign shows a 180° phase shift between the input and output signals.
# Transient Analysis
The transient analysis of a PMOS Common Source amplifier is carried out to analyze the time-domain behavior of the circuit when a time-varying input signal (sine, square, or pulse wave) is applied. Unlike DC analysis (steady-state) and AC analysis (small-signal frequency response), the transient analysis indicates how the output voltage varies with time. When an input signal is applied to the gate, it results in the variation of (VSG), which in turn affects the drain current and results in an output voltage at the drain. This analysis is used to analyze the waveform, amplitude, phase reversal (180°), rise time, fall time, and distortion.

# Procedure
Step 1: Create new circuit
Open LTSpice → Click File → New Schematic.
Save the file with a proper name.

Step 2: Add components
Place these parts in the circuit:

* NMOS transistor (180 nm CMOS model)
* Resistor ( Rd= 2k )
* Two voltage sources (V1 and V2)
* Ground

Step 3: Connect and set values

* Set V1 = 2V (DC supply).
* Set V2 = SINE(1.4 10m 1k)
  (1.4V DC bias, 10mV signal, 1kHz frequency).
* Connect Rd (2kΩ) between V1 and drain.

Step 4: Add simulation commands

Go to Simulate → Edit Simulation Cmd and add:

* .op → For DC analysis
* .ac dec 10 0001 1G → For AC analysis
* .tran 5m → For transient analysis
Place these commands on the schematic.

Step 5: Run the circuit

Click the Run button.
View the results in the waveform window.

Step 6: Check results

* In DC analysis, check ( VGS P = VDD * ID)
* In AC analysis, we find the frequency response, mid-band gain, bandwidth, and unity gain bandwidth of the amplifier.
* In Transient analysis, to calculate gain
  

# Results

# DC Analysis
<img width="1897" height="854" alt="Screenshot 2026-02-27 125009" src="https://github.com/user-attachments/assets/5bf8be21-a02a-441f-a842-e150c699be5a" />


Theoritical
Pmos : W= 144um

Practical
Pmos: W=333.5um

Id=500.40uA
Vout=1.0008V

# DC Sweep
<img width="1908" height="856" alt="Screenshot 2026-02-27 125419" src="https://github.com/user-attachments/assets/80b92e4a-94bd-40b9-9ef5-944018ab47f9" />

# Transient Analysis
Input waveform
<img width="1916" height="867" alt="Screenshot 2026-02-27 125340" src="https://github.com/user-attachments/assets/8561397a-1ed7-4cfc-8288-61bffe3ea647" />


Output waveform
<img width="1908" height="860" alt="Screenshot 2026-02-27 125201" src="https://github.com/user-attachments/assets/05e1b6c8-50e7-4992-9009-17c9d10728d0" />

Theoritical 

 Transconductance value

 gm = 2ID/VOV
 
    = 2*500u/0.2
    
    =5mS

 Av= gm*Rd
 
   =5m*2k
   
   =10

   Gain in decibles

   Av(dB)=20log10(10)

        =20dB

   Practical
   
  Av = Vout/Vin
  
 Av = 212.936/19.997
 
 Av = 10.648

 Gain in decibles

 Av(dB)=20log10(10.648)

      =20.545dB
      
Therefore theoritical and practical values are almost equal

# AC Analysis
<img width="1917" height="848" alt="image" src="https://github.com/user-attachments/assets/1080b748-74e3-4632-a6ad-116bf9822a2b" />

AC analysis is performed to find the frequency response, mid-band gain, bandwidth, and unity gain bandwidth of the amplifier.

Mid-Band Gain

From the AC frequency response graph:

Gain ≈ 20.6 dB

This is equivalent to:

Av ≈ 10.6 V/V

Bandwidt

From simulation:

Bandwidth = 79.6 MHz

Unity Gain Bandwidth (UGB)

UGB = Av × BW

UGB = 10.6 * 79.6 MHz

UGB = 843.76 MHz


# Inference

From the above experiment, the Common Source amplifier with a 180nm MOSFET has been successfully designed and simulated using LTSpice. The DC analysis has verified that the MOSFET was biased in the saturation region. The AC analysis has shown that the circuit was capable of voltage gain with a 180° phase shift between the input and output signals. The transient analysis has confirmed that the output signal was amplified compared to the input signal. Therefore, it can be concluded that the Common Source amplifier is capable of amplifying small input signals when it is properly biased and designed under the specified power and supply
