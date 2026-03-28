
## Circuit 2


## Differential Amplifier (Active Load) – Analysis



##  Aim

To design and analyze a MOS differential amplifier with active load, determine its DC operating point, and evaluate its performance in terms of gain, linearity, and frequency response using LTspice.



# Introduction

A differential amplifier amplifies the difference between two input signals while rejecting common-mode signals. In this circuit, an active load (current mirror) is used instead of resistors, which increases gain and improves performance.



# Circuit Description

The circuit consists of:

- M1, M2 → NMOS differential pair  
- M3, M4 → PMOS current mirror (active load)  
- M5 → Tail current source  


![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-28%20172015.png)


# Given Parameters



$V_{DD} = 0.9\ \mathrm{V}$  
$V_{SS} = -0.9\ \mathrm{V}$  
$P = 2.2\ \mathrm{mW}$  
$V_{T} \approx 0.4\ \mathrm{V}$  
$V_{ov} \approx 0.39\ \mathrm{V}$  
$L = 540\ \mathrm{nm}$


# Design Calculations

## Tail Current

$I_{SS} = \dfrac{P}{V_{DD} - V_{SS}}$  

$I_{SS} = \dfrac{2.2\ \mathrm{mW}}{1.8\ \mathrm{V}}$  

$I_{SS} \approx 1.22\ \mathrm{mA}$  


## Branch Current

$I_{D} = \dfrac{I_{SS}}{2}$  

$I_{D} \approx 0.61\ \mathrm{mA}$  


## Bias Voltage

$V_{GS} = V_{T} + V_{ov}$  

$V_{GS} = 0.34 + 0.3 = 0.64\ \mathrm{V}$  

$V_{B} = V_{S} + V_{GS}$  

$V_{B} = -0.9 + 0.64$  

$V_{B} \approx -0.26\ \mathrm{V}$



## DC Analysis (Simulation)


![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-28%20172139.png)


## 🔹 Results

# Calculated Values

$I_{SS} \approx 1.23\ \mathrm{mA}$  

$I_{D1} = I_{D2} \approx 0.615\ \mathrm{mA}$  

$V_{p} \approx -0.724\ \mathrm{V}$  

$V_{out1} \approx V_{out2} \approx -0.055\ \mathrm{V}$

#  Input Common Mode Range (ICMR)

The input common-mode range is defined as the range of input voltage for which all transistors remain in saturation.



# Minimum Input Common Mode Voltage

Condition:

Input NMOS must remain ON:

# Minimum Input Common Mode Voltage

$V_{GS} \geq V_{T}$  

Using:

$V_{GS} = V_{ICM} - V_{S}$  

So,

$V_{ICM(min)} = V_{S} + V_{T}$  

Now,

$V_{S} = V_{SS} + V_{ov}$  

$V_{S} = -0.9 + 0.3 = -0.6\ \mathrm{V}$  

Therefore:

$V_{ICM(min)} = -0.6 + 0.4$  

$V_{ICM(min)} = -0.2\ \mathrm{V}$

# Maximum Input Common Mode Voltage

Condition:

Input NMOS must remain in saturation:

# Maximum Input Common Mode Voltage

$V_{DS} \geq V_{ov}$  

Using:

$V_{D} \approx V_{DD} - V_{ov}$  

$V_{D} = 0.9 - 0.3 = 0.6\ \mathrm{V}$  

Now,

$V_{ICM(max)} = V_{D} - V_{ov}$  

$V_{ICM(max)} = 0.6 - 0.3$  

$V_{ICM(max)} = 0.3\ \mathrm{V}$  


# Final Input Common Mode Range

$-0.2\ \mathrm{V} \leq V_{ICM} \leq 0.3\ \mathrm{V}$


# Differential Input Voltage Range (Linear Region)

For linear operation:

V_id < √2 × V_ov  

V_id < 1.414 × 0.3  

V_id < 0.42 V  



# Conclusion

- ICMR: -0.2 V to 0.3 V  
- Linear region condition: V_id < 0.42 V  


# ifferential Input Voltage Range (Linear Region)

The differential amplifier operates in the linear region only when both transistors (M1 and M2) remain in saturation.

 

#  Condition for Linear Operation

For MOS differential pair:

$V_{id} < \sqrt{2} \times V_{ov}$

 
# Given

$V_{ov} = 0.39\ \mathrm{V}$  


# 🔹 Calculation

$V_{id(max)} = \sqrt{2} \times V_{ov}$  

$V_{id(max)} = 1.414 \times 0.3$  

$V_{id(max)} \approx 0.42\ \mathrm{V}$  


# Final Range

$-0.42\ \mathrm{V} \leq V_{id} \leq 0.42\ \mathrm{V}$  


# Conclusion

For $|V_{id}| < 0.42\ \mathrm{V}$ → circuit behaves as linear amplifier  

For $|V_{id}| > 0.42\ \mathrm{V}$ → one transistor turns OFF → nonlinear behavior occurs


# Step 2: Transient Analysis and Linearity Observation

Transient analysis is performed to observe the linear behavior of the differential amplifier with active load.

Load capacitor:

$C_{L}$ = 10 pF  # Condition for Linear Operation

For linear operation:

$V_{id} < \sqrt{2} \times V_{ov}$  

$V_{id} < 1.414 \times 0.3 \approx 0.42\ \mathrm{V}$  


# (a) Case 1: $V_{id} < \sqrt{2} V_{ov}$

Set a small differential input:

Example:  
$V_{in1} = +20\ \mathrm{mV}$  
$V_{in2} = -20\ \mathrm{mV}$  

So,

$V_{id} = 40\ \mathrm{mV} < 0.42\ \mathrm{V}$  

# Observation:

Output is sinusoidal  
No distortion observed  
Outputs are equal in magnitude and opposite in phase  
Circuit operates in linear region  


# (b) Case 2: $V_{id} > \sqrt{2} V_{ov}$

![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-27%20170759.png)

Set a large differential input:

Example:  
$V_{in1} = +300\ \mathrm{mV}$  
$V_{in2} = -300\ \mathrm{mV}$  

So,

$V_{id} = 600\ \mathrm{mV} > 0.42\ \mathrm{V}$  

Observation:

Output becomes distorted  
Peaks are flattened  
One transistor carries most of the current  
Other transistor approaches cutoff  
Nonlinear behavior is observed  


# (c) Comparison and Interpretation

| Condition | Input Level | Output Behavior | Operation |
|-----------|-------------|----------------|-----------|
| $V_{id} < \sqrt{2} V_{ov}$ | Small signal | Clean sinusoidal | Linear |
| $V_{id} > \sqrt{2} V_{ov}$ | Large signal | Distorted waveform | Nonlinear |


# Conclusion

The differential amplifier operates linearly only for small input signals. When the input exceeds the limit $\sqrt{2} \times V_{ov}$, the circuit enters nonlinear region and distortion occurs.


# 🔷 1.4 AC Analysis

In AC analysis, the frequency response of the differential amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the range between the lower cutoff frequency ($f_{L}$) and upper cutoff frequency ($f_{H}$), measured at the −3 dB points.

![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-27%20164251.png)


# Midband Gain

From AC simulation (cursor reading):

$A_{v} = 12.45\ \mathrm{dB}$  

The corresponding linear gain is:

$A_{v} = 10^{(12.45/20)} \approx 4.19$  


# Theoretical Gain Calculation

# Given Values

Drain current: $I_{D} = 0.61\ \mathrm{mA}$  
Overdrive voltage: $V_{ov} = 0.3\ \mathrm{V}$  
Drain resistance: $R_{D} = 1.47\ \mathrm{k\Omega}$  
Channel length modulation parameter: $\lambda = 0.1$  


# Step 1: Transconductance ($g_{m}$)

$g_{m} = \frac{2 I_{D}}{V_{ov}}$  

$g_{m} = \frac{2 \times 0.61\ \mathrm{mA}}{0.3}$  

$g_{m} \approx 4.07\ \mathrm{mS}$  


# Step 2: Output Resistance ($r_{o}$)

$r_{o} = \frac{1}{\lambda I_{D}}$  

$r_{o} = \frac{1}{0.1 \times 0.61\ \mathrm{mA}}$  

$r_{o} = \frac{1}{0.000061}$  

$r_{o} \approx 16.4\ \mathrm{k\Omega}$  


# Step 3: Effective Load Resistance

$R_{eff} = R_{D} \parallel r_{o}$  

$R_{eff} = \frac{1.47\ \mathrm{k\Omega} \times 16.4\ \mathrm{k\Omega}}{1.47\ \mathrm{k\Omega} + 16.4\ \mathrm{k\Omega}}$  

$R_{eff} \approx 1.35\ \mathrm{k\Omega}$  


# Step 4: Voltage Gain

$A_{v} = g_{m} \times R_{eff}$  

$A_{v} = 4.07 \times 10^{-3} \times 1350$  

$A_{v} \approx 5.5$  


Reason for Difference Between Theoretical and Simulated Gain

- Theoretical calculations neglect parasitic effects  
- Channel length modulation reduces gain  
- Finite output resistance of MOSFET reduces effective load  
- Presence of load capacitance affects gain  
- Simulation uses real device models (TSMC 0.18)  
- Gain is measured as single-ended output instead of differential output  

Hence, the simulated gain is lower than the theoretical value.


# −3 dB Gain

$A_{v(-3dB)} = 12.45 - 3$  

$A_{v(-3dB)} = 9.45\ \mathrm{dB}$  


# Cutoff Frequencies

Lower cutoff frequency:

$f_{L} \approx 0\ \mathrm{Hz}$  

Upper cutoff frequency (from graph):

$f_{H} \approx 316.2\ \mathrm{MHz}$  


# Bandwidth

$BW = f_{H} - f_{L}$  

$BW \approx 316.2\ \mathrm{MHz}$  


# Observation

Gain is constant in midband region  
Gain decreases at higher frequencies due to capacitive effects  
The roll-off indicates limited bandwidth  


# Conclusion

The AC analysis shows that the differential amplifier has a high bandwidth.  
The gain decreases at higher frequencies due to parasitic capacitances and load capacitor effects.  
The amplifier demonstrates a gain-bandwidth trade-off.
