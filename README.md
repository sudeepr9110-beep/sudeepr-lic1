# Experiment 1: CS Amplifier
## Aim
To implement and analyze a PMOS-based Common Source amplifier in LTSpice using the TSMC 180 nm technology
## Components Required

## Theory
A Common Source (CS) amplifier using a PMOS transistor is a single-stage voltage amplifier in which the source terminal is common to both input and output. In this arrangement, the input is applied to the gate, and the output is taken from the drain, while the source is tied to the supply voltage VDD.

For a PMOS transistor, the current flows when:
VSG > |VTP|

For the transistor to act as an amplifier, it must be in the saturation region, where the drain current is nearly constant and controlled by the gate voltage. For saturation, the transistor satisfies the following condition:
VSD > VSG-|VTP|

 In saturation, the drain current is expressed as:
 
 ID ​= (1/2)*​μp​Cox​*(W/l)*​(VSG​−∣VTP​∣)^2
 
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
# DC Analysis
![Image description](https://github.com/sudeepr9110-beep/sudeepr-lic1/blob/main/Screenshot%202026-02-24%20224159.png?raw=true)
