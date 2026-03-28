
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

# Tail Current

$I_{SS} = \dfrac{P}{V_{DD} - V_{SS}}$  

$I_{SS} = \dfrac{2.2\ \mathrm{mW}}{1.8\ \mathrm{V}}$  

$I_{SS} \approx 1.22\ \mathrm{mA}$ 



# Branch Current

$I_{D} = \dfrac{I_{SS}}{2}$  

$I_{D} \approx 0.61\ \mathrm{mA}$  


# Bias Voltage

$V_{GS} = V_{T} + V_{ov}$  

$V_{GS} = 0.34 + 0.3 = 0.64\ \mathrm{V}$  

$V_{B} = V_{S} + V_{GS}$  

$V_{B} = -0.9 + 0.64$  

$V_{B} \approx -0.26\ \mathrm{V}$


## DC Analysis (Simulation)


![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-28%20172139.png)


##  Results

$I_{SS} \approx 1.23\ \mathrm{mA}$  

$I_{D1} = I_{D2} \approx 0.615\ \mathrm{mA}$  

$V_{p} \approx -0.724\ \mathrm{V}$  

$V_{out1} \approx V_{out2} \approx -0.055\ \mathrm{V}$


# Minimum Input Common Mode Voltage

Condition:  
Input NMOS must remain ON:

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

$V_{id} < \sqrt{2} \times V_{ov}$  

$V_{id} < 1.414 \times 0.3$  

$V_{id} < 0.42\ \mathrm{V}$  


# Conclusion

- ICMR: $-0.2\ \mathrm{V}$ to $0.3\ \mathrm{V}$  
- Linear region condition: $V_{id} < 0.42\ \mathrm{V}$  


# Differential Input Voltage Range (Linear Region)

The differential amplifier operates in the linear region only when both transistors (M1 and M2) remain in saturation.


# Condition for Linear Operation

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

$C_{L} = 10\ \mathrm{pF}$  


# (a) Case 1: $V_{id} < \sqrt{2} V_{ov}$

Condition:

$V_{id} < 1.414 \times V_{ov}$  

$V_{id} < 1.414 \times 0.3 \approx 0.42\ \mathrm{V}$  

Set small differential input:

$V_{in1} = +10\ \mathrm{mV}$  
$V_{in2} = -10\ \mathrm{mV}$  

$V_{id} = 20\ \mathrm{mV} < 0.42\ \mathrm{V}$  

## Observation:

- Output waveforms are sinusoidal  
- No distortion observed  
- Outputs are equal in magnitude  
- Outputs are 180° out of phase  
- Circuit operates in linear region  


# (b) Case 2: $V_{id} > \sqrt{2} V_{ov}$

![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-28%20194740.png)

Condition:

$V_{id} > 0.42\ \mathrm{V}$  

Set large differential input:

$V_{in1} = +300\ \mathrm{mV}$  
$V_{in2} = -300\ \mathrm{mV}$  

$V_{id} = 600\ \mathrm{mV} > 0.42\ \mathrm{V}$  


# Observation:

- Output becomes distorted  
- Peaks are clipped or flattened  
- One transistor carries most of the current  
- Other transistor goes near cutoff  
- Nonlinear behavior is observed  


# (c) Comparison and Interpretation

| Condition | Input ($V_{id}$) | Output Behavior | Operation |
|-----------|------------------|-----------------|-----------|
| $V_{id} < \sqrt{2} V_{ov}$ | Small (20 mV) | Clean sinusoidal | Linear |
| $V_{id} > \sqrt{2} V_{ov}$ | Large (600 mV) | Distorted | Nonlinear |


# Conclusion

The differential amplifier with active load behaves as a linear amplifier for small input signals. When the input exceeds $\sqrt{2} \times V_{ov}$, the circuit enters nonlinear region and distortion occurs.


## 🔷 AC Analysis

In AC analysis, the frequency response of the differential amplifier is observed.

![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-28%20194658.png)


# Midband Gain

From the flat region of the plot:

$A_{v} \approx 6\ \mathrm{dB}$  

Convert to linear:

$A_{v} = 10^{(6/20)} \approx 2$  


# Cutoff Frequencies

Lower cutoff frequency:

$f_{L} \approx 0\ \mathrm{Hz}$  


Upper cutoff frequency:

From graph at −3 dB point:

$A_{v} - 3 = 6 - 3 = 3\ \mathrm{dB}$  

$f_{H} \approx 3\ \mathrm{GHz}\ \text{to}\ 5\ \mathrm{GHz}$ (approx)


# Bandwidth

$BW = f_{H} - f_{L}$  

$BW \approx 4\ \mathrm{GHz}$  


# Unity Gain Bandwidth (UGB)

![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-28%20194209.png)

Unity Gain Bandwidth is defined as the frequency at which the gain becomes 0 dB.

From AC plot:

$UGB \approx 5.035\ \mathrm{GHz}$  


# Observation

- Gain crosses 0 dB at ≈ 5 GHz  
- Phase at this point ≈ −90°  
- Indicates stable amplifier behavior  


# Conclusion

The Unity Gain Bandwidth of the differential amplifier is approximately $5.035\ \mathrm{GHz}$.


# Conclusion

The amplifier shows a flat midband gain of approximately 6 dB with a very high bandwidth in the GHz range. The gain starts decreasing after the upper cutoff frequency, indicating typical high-frequency roll-off behavior. 
