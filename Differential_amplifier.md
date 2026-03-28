## Experiment 04


## Differential Amplifier Analysis


# Aim
To design and simulate a MOS differential amplifier with resistive load, establish its DC biasing conditions, and analyze key performance metrics including voltage gain, input common-mode range (ICMR), and linearity.


# Introduction

A differential amplifier is a fundamental building block in analog circuit design that amplifies the difference between two input signals while rejecting common-mode components. This property makes it highly suitable for applications such as operational amplifiers, comparators, and various signal-processing circuits.

In MOS-based differential amplifiers, two matched transistors share a common current source, ensuring symmetrical operation and stable biasing conditions. Such a configuration provides high differential gain, improved linearity, and strong noise rejection capability.

In this experiment, a MOS differential amplifier with a resistive load is designed and analyzed. The objective is to determine the DC operating point, evaluate important performance parameters such as voltage gain and input common-mode range (ICMR), and verify the amplifier’s linearity through simulation. The results obtained from simulation help in understanding the practical behavior and performance characteristics of the differential amplifier.

# Theory

 
 Differential Amplifier with Resistive Load

A MOS differential amplifier consists of two identical MOSFETs whose sources are connected together and biased using a constant current source. The drains are connected to resistive loads. The circuit amplifies the difference between two input signals while rejecting common-mode signals.

# Working Principle 

When equal voltages are applied to both inputs, the tail current supplied by the current source divides equally between the two transistors. As a result, both transistors operate symmetrically, producing equal output voltages at the drains.

When a differential input signal is applied, the symmetry of the circuit is disturbed. One transistor conducts more current while the other conducts less. This redistribution of current causes opposite voltage variations across the load resistors. Consequently, amplified differential output signals are produced at the drains.

Thus, the MOS differential amplifier provides high gain for differential inputs while maintaining strong rejection of common-mode signals.
# Power Constraint

The total current is limited by the supply voltages:
$P = (V_{DD} - V_{SS}) \times I_{SS}$
Using power relation:

P = Vtotal × ISS  

$I_{SS}$= 2.2 mW/ 1.8 V  

$I_{SS}$ = 1.22 mA .

# Drain Current

In a symmetrical differential amplifier:

$I_{d}$ = $I_{SS}$ / 2

Each transistor carries half of the tail current under balanced conditions.

# Load Resistance

The drain resistor converts current into voltage:

RD = ($V_{DD} − V_{out}) / I_{D}$

It plays a major role in determining the gain.

# Bias Point

The bias point ensures that the MOSFET operates in saturation.

Important voltages:

$V_{G}$ (Gate voltage)
$V_{S}$ (Source voltage)
$V_{D}$ (Drain voltage)

Condition for saturation:

$V_{DS} > V_{GS} − V_{T}$

# Width Calculation

The drain current equation is:

$I_{D} = (1/2) μnCox (W/L) ($$ V_{ov})²$

This is used to calculate the required transistor width W.

# Input Common Mode Range (ICMR)

ICMR is the range of input voltage for which transistors remain in saturation.

Minimum value:

$V_{ICM(min)} = V_{S} + V_{T} + V_{GS}$

Maximum value:

$V_{ICM(max)} = V_{D} + V_{T}$

# Output Common Mode Range

The output voltage must stay within limits to maintain saturation. It is bounded by supply voltages and saturation conditions.

# Differential Input Voltage Range (Linear Region)

For linear operation:

$V_{id} < \sqrt{2} \times V_{ov}$

If this condition is violated, the amplifier becomes nonlinear and distortion occurs.

# Transient Analysis and Linearity

Transient analysis studies time-domain behavior:

Small input → linear, sinusoidal output
Large input → distorted output
# Theoretical Gain

Without channel length modulation:

$A_{v} = g_{m} \times R_{D}$

With channel length modulation:

$A_{v} = g_{m} \times (R_{D} \parallel r_{o})$

Where:

$g_{m} = \frac{2 I_{D}}{V_{ov}}$


$r_{o} = \frac{1}{\lambda I_{D}}$
# AC Analysis

AC analysis determines frequency response:

Midband gain → constant gain region
Cutoff frequencies → where gain drops
Bandwidth → frequency range of operation

## Circuit 01


##  Working of the Circuit

The MOS differential amplifier operates based on the principle of current steering between two matched transistors.

When equal voltages are applied at both inputs (common-mode input), the tail current **I_SS** splits equally between the two transistors:

$I_{D1} = I_{D2} = \frac{I_{SS}}{2}$ 
 Output voltages at both drains are equal  

Hence, no differential output is produced.


## Differential Operation

When a differential input is applied:

# Case 1: $V_{in1} > V_{in2}$

Transistor M1 conducts more current  
Transistor M2 conducts less current  
Voltage drop across $R_{D}$ of M1 increases → V_out1 decreases  
Voltage drop across  $R_{D}$ of M2 decreases → V_out2 increases  


# Case 2: $V_{in2} > V_{in1}$

 Transistor M2 conducts more current  
 Transistor M1 conducts less current  
  $V_{out2}$  decreases and$V_{out1}$  increases  



#  Output Characteristics

 Outputs are equal in magnitude  
 Outputs are 180° out of phase  


## DC Analysis


<img width="900" height="546" alt="image" src="https://github.com/user-attachments/assets/6750b22e-6a54-44d2-9e16-4f72a819b0cb" />





#  Design Calculations

# Given Parameters

 $V_{DD} = 0.9\ \mathrm{V}$  
$V_{SS} = -0.9\ \mathrm{V}$  
Power $P = 2.2\ \mathrm{mW}$  
$V_{outCM} = 0\ \mathrm{V}$  
$V_{S} = -0.7\ \mathrm{V}$  
$V_{T} = 0.4\ \mathrm{V}$  
$V_{ov} = 0.3\ \mathrm{V}$  
$L = 540\ \mathrm{nm}$ 



 

Since the circuit is symmetrical:

$I_{D} = \frac{I_{SS}}{2}$  
$I_{D} \approx 0.61\ \mathrm{mA}$ 


# 2. Load Resistance Calculation

$R_{D} = \frac{V_{DD} - V_{out}}{I_{D}}$  

$R_{D} = \frac{0.9 - 0}{0.61\ \mathrm{mA}}$  

$R_{D} \approx 1.47\ \mathrm{k\Omega}$


#  3. Bias Point Calculation

$V_{G} = 0\ \mathrm{V}$  
$V_{S} = -0.7\ \mathrm{V}$  
$V_{D} = 0\ \mathrm{V}$  

$V_{GS} = V_{G} - V_{S} = 0 - (-0.7) = 0.7\ \mathrm{V}$  
$V_{DS} = V_{D} - V_{S} = 0 - (-0.7) = 0.7\ \mathrm{V}$  

Since $V_{DS} > V_{ov}$, the MOSFET operates in saturation.


# 4. Width Calculation

$I_{D} = \frac{1}{2} \mu_{n} C_{ox} \left(\frac{W}{L}\right) (V_{ov})^2$  

Assuming $\mu_{n} C_{ox} \approx 200\ \mu\mathrm{A/V^2}$:

$\frac{W}{L} \approx 67.8$  

$W = 67.8 \times 540\ \mathrm{nm}$  

$W \approx 37\ \mathrm{\mu m}$ 


<img width="959" height="547" alt="image" src="https://github.com/user-attachments/assets/49111bf8-262b-4a0d-bf4d-320a3f29e140" />



#  5. Input Common Mode Range (ICMR)

Minimum value:

$V_{ICM(min)} = V_{S} + V_{T}$  
$V_{ICM(min)} = -0.7 + 0.4 = -0.3\ \mathrm{V}$  

Maximum value:

$V_{ICM(max)} = V_{D} + V_{T}$  
$V_{ICM(max)} = 0 + 0.4 = 0.4\ \mathrm{V}$  

Final range:

$-0.3\ \mathrm{V} \leq V_{ICM} \leq 0.4\ \mathrm{V}$

# 6. Differential Input Voltage Range (Linear Region)

For linear operation:

$V_{id} < \sqrt{2} \times V_{ov}$  

$V_{id} < 1.414 \times 0.3 \approx 0.42\ \mathrm{V}$

# 7. Output Voltage Range

Minimum output voltage:

$V_{out(min)} = V_{S} + V_{ov} = -0.7 + 0.3 = -0.4\ \mathrm{V}$  

Maximum output voltage:

$V_{out(max)} = V_{DD} = 0.9\ \mathrm{V}$


## Transient Analysis and Linearity Observation

Transient analysis is performed to observe the linear behavior of the differential amplifier.

A load capacitor is connected at the output:

$C_L$ = 10 pF  


![Image description](https://github.com/praphul-biradar/LIC-LAB/blob/main/Screenshot%202026-03-27%20164439.png)


# Condition for Linear Operation

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

- Output is sinusoidal  
- No distortion observed  
- Outputs are equal in magnitude and opposite in phase  
- Circuit operates in linear region

 <img width="1363" height="589" alt="image" src="https://github.com/user-attachments/assets/80b49f02-152d-45f3-9290-c3bb52739336" />



# (b) Case 2: $V_{id} > \sqrt{2} V_{ov}$

Set a large differential input:

Example:  
$V_{in1} = +300\ \mathrm{mV}$  
$V_{in2} = -300\ \mathrm{mV}$  

So,

$V_{id} = 600\ \mathrm{mV} > 0.42\ \mathrm{V}$

# Observation:

- Output becomes distorted  
- Peaks are flattened  
- One transistor carries most of the current  
- Other transistor approaches cutoff  
- Nonlinear behavior is observed

  <img width="1353" height="584" alt="image" src="https://github.com/user-attachments/assets/487c5a11-f85e-4dcf-ad51-8082f8347060" />


# (c) Comparison and Interpretation

| Condition         | Input Level   | Output Behavior     | Operation   |
|------------------|---------------|------------------|------------|
| $V_{id} < \sqrt{2} V_{ov}$ | Small signal   | Clean sinusoidal  | Linear     |
| $V_{id} > \sqrt{2} V_{ov}$ | Large signal   | Distorted waveform | Nonlinear |

# Conclusion

The differential amplifier operates linearly only for small input signals. When the input exceeds the limit $\sqrt{2} \times V_{ov}$, the circuit enters nonlinear region and distortion occurs.

# 1.4 AC Analysis

In AC analysis, the frequency response of the differential amplifier is observed.  
The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the range between the lower cutoff frequency ($f_{L}$) and upper cutoff frequency ($f_{H}$), measured at the −3 dB points.

# Midband Gain

From AC simulation (cursor reading):

$A_{v} = 12.45\ \mathrm{dB}$  

Corresponding linear gain:

$A_{v} = 10^{(12.45/20)} \approx 4.19$

# Theoretical Gain Calculation

## Given Values

Drain current: $I_{D} = 0.61\ \mathrm{mA}$  
Overdrive voltage: $V_{ov} = 0.3\ \mathrm{V}$  
Drain resistance: $R_{D} = 1.47\ \mathrm{k\Omega}$  
Channel length modulation parameter: $\lambda = 0.1$

## Step 1: Transconductance ($g_{m}$)

$g_{m} = \frac{2 I_{D}}{V_{ov}}$  

$g_{m} = \frac{2 \times 0.61\ \mathrm{mA}}{0.3} \approx 4.07\ \mathrm{mS}$

## Step 2: Output Resistance ($r_{o}$)

$r_{o} = \frac{1}{\lambda \times I_{D}}$  

$r_{o} = \frac{1}{0.1 \times 0.61\ \mathrm{mA}} \approx 16.4\ \mathrm{k\Omega}$

## Step 3: Effective Load Resistance

$R_{eff} = R_{D} \parallel r_{o}$  

$R_{eff} = \frac{1.47\ \mathrm{k\Omega} \times 16.4\ \mathrm{k\Omega}}{1.47\ \mathrm{k\Omega} + 16.4\ \mathrm{k\Omega}} \approx 1.35\ \mathrm{k\Omega}$

## Step 4: Voltage Gain

$A_{v} = g_{m} \times R_{eff}$  

$A_{v} = 4.07 \times 10^{-3} \times 1350 \approx 5.5$

### Reason for Difference Between Theoretical and Simulated Gain

- Theoretical calculations neglect parasitic effects  
- Channel length modulation reduces gain  
- Finite output resistance of MOSFET reduces effective load  
- Presence of load capacitance affects gain  
- Simulation uses real device models (TSMC 0.18)  
- Gain is measured as single-ended output instead of differential output  

Hence, the simulated gain is lower than the theoretical value.

# −3 dB Gain

$A_{v(-3dB)} = 12.45 - 3 = 9.45\ \mathrm{dB}$

# Cutoff Frequencies

Lower cutoff frequency:

$f_{L} \approx 0\ \mathrm{Hz}$  

Upper cutoff frequency (from graph):

$f_{H} \approx 316.2\ \mathrm{MHz}$

# Bandwidth

$BW = f_{H} - f_{L} \approx 316.2\ \mathrm{MHz}$

# Observation

- Gain is constant in midband region  
- Gain decreases at higher frequencies due to capacitive effects  
- The roll-off indicates limited bandwidth

# Conclusion

The AC analysis shows that the differential amplifier has a high bandwidth.  
The gain decreases at higher frequencies due to parasitic capacitances and load capacitor effects.  
The amplifier demonstrates a gain-bandwidth trade-off.
