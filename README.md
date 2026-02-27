# Experiment–1  
# Common Source Amplifier Analysis – PMOS

This experiment demonstrates the DC, AC, and Transient analysis of a PMOS Common Source (CS) amplifier using LTspice.

---

# Abstract

The PMOS Common Source amplifier is analyzed to study its biasing condition, voltage gain, and frequency response.  
DC analysis determines the operating point, AC analysis determines gain and bandwidth, and transient analysis verifies amplification and phase inversion.

---

# Theory

## PMOS Common Source Amplifier

In a PMOS CS amplifier:

- Input is applied to the gate  
- Output is taken from the drain  
- Source is connected to $( V_{DD} $)

The output is 180° out of phase with the input.

---

## Conditions for Proper Operation

For correct amplification, the MOSFET must operate in the **saturation region**.

The required conditions are:

1. $V_{SG} \geq V_{th}$  
   → To turn the transistor ON  

2. $V_{SD} > V_{GS} - V_{th}$  
   → To keep the transistor in saturation  

3. The input signal $v_{in}$ must be small  
   → To ensure small-signal operation  

4. Proper biasing and correct selection of $R_D$  
   → To obtain stable operation and sufficient voltage gain  

---

## Drain Current Equation

In saturation region:

$$
I_D = \frac{1}{2} k_p (V_{SG} - |V_{th}|)^2
$$

---

## Small Signal Gain

$$
A_v = -g_m R_D
$$

$$
g_m = \frac{2I_D}{V_{ov}}
$$

Negative sign indicates phase inversion.

---

## Given Design Requirements

| Parameter | Symbol | Value | Unit | Description |
|------------|---------|--------|------|-------------|
| Supply Voltage | VDD | 2 | V | DC power supply |
| Maximum Power | Pmax | ≤1.5 | mW | Power constraint |
| Load Capacitance | CL | 1 | pF | Output load |
| NMOS Channel Length | Ln | 560 | nm | Technology parameter |
| Technology Node | — | 180 | nm | CMOS process |
| Simulation Tool | — | LTspice | — | Design environment |

---

## Derived Parameter (From Power Constraint)

| Parameter | Formula | Calculated Value | Unit |
|------------|----------|------------------|------|
| Maximum Drain Current | ID ≤ Pmax / VDD | ≤ 0.750 | mA |

## Circuit Diagram
<img width="996" height="537" alt="image" src="https://github.com/user-attachments/assets/fd0a35be-1e7c-4f7f-a2ed-3af930c4ea62" />




## DC analysis is performed to determine the biasing condition (operating point) of the MOSFET.

It calculates the steady-state values of $I_D$, $V_{SG}$, and $V_{SD}$ to ensure the transistor operates in the **saturation region** for proper and distortion-free amplification.
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/d9bfb0c6-cff0-4df4-88ce-f98966269261" />

# Simulated DC Operating Point Results

| Parameter | Symbol | Simulated Value | Unit |
|------------|---------|----------------|------|
| Supply Voltage | VDD | 2 | V |
| Input Voltage | Vin | 1.409 | V |
| Output Voltage | Vout | 1| V |
| Drain Current | ID |500 | mA |
| Current through RD | I(RD) | 500 | mA |
| Supply Current | I(VDD) | 500 | mA |

---
## Power Calculation

P = VDD × ID  

P = 2 × 0.500mA  

P = 1 mW

---

# DC Sweep Analysis – PMOS CS Amplifier


In a PMOS Common Source amplifier, the **gate voltage $(V_G$) controls the **source-to-gate voltage $(V_{SG}$) and hence the drain current $(I_D$).  


By sweeping \(V_G\) from 0 to \(V_{DD}\), we can plot $(V_{out}$) vs $(V_G$) to find the **DC bias point**.  


The bias is chosen so that the drain voltage is approximately half of $(V_{DD}$) for maximum output swing, keeping the transistor in **saturation**.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/d7ed9898-050d-49c2-a5c1-b16a630afc7c" />

# Transient Analysis of Common Source (CS) Amplifier

## Introduction

Transient analysis is performed to study the time-domain behavior of the Common Source (CS) amplifier. It shows how the output voltage changes with respect to time when an input signal is applied.

## Purpose of Transient Analysis

The main objectives are:

- To observe signal amplification over time
- To verify phase inversion (180° phase shift)
- To measure voltage gain from input and output waveforms
- To check signal distortion and stability




## Voltage Gain Measurement

Voltage gain is calculated using peak values:

$$
A_v = \frac{V_{out}}{V_{in}}
$$

Since the CS amplifier inverts the signal:

$$
A_v = - \frac{V_{out}}{V_{in}}


# Transient Analysis – Common Source Amplifier

---
## 1. Theoritical calculation for gain

$$
A_v = -g_m R_D
$$

where $g_m$=transconductance

  $R_d$ =Resistor

  $$
g_m = \frac{2 I_D}{V_{ov}}
$$

 $$
g_m = \frac{2.0.5mA}{0.2V}
$$

  $$
  g_m=0.005
  $$

  $$
A_v = -g_m R_D
$$

$$
A_v = -0.005*2000
$$

$$
A_v = -10
$$

## 1. Pratical calculation for gain

## 1. Input Waveform $V_{in}$
<img width="1365" height="589" alt="image" src="https://github.com/user-attachments/assets/4b996eef-c9ca-4e25-bca1-b62e538d1677" />
" />


<p align="center">
  

**Fig 1:** Transient response of input signal $V_{in}$.

---

## Measured Input Values (From Cursor)

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 1.409 | V |
| Peak Voltage | 1.4188 | V |
| Minimum Voltage | 1.3989 | V |
| Peak-to-Peak Voltage | 19.69 | mV |
| Input Amplitude | 9.845| mV |
| Frequency | 1 | kHz |


---

---

## 2. Output Waveform $(V_{out})$

<img width="1363" height="629" alt="image" src="https://github.com/user-attachments/assets/e7ab2374-60e6-45c9-97e4-326ba31872db" />



</p>

**Fig 2:** Transient response of output signal $V_{out}$.

---

## Measured Output Values (From Cursor)

| Parameter | Value | Unit |
|------------|--------|------|
| Peak Voltage | 1.108 | V |
| Minimum Voltage | 898.7544| mV |
| Peak-to-Peak Voltage |209.372 | mV |
| Output Amplitude |104.686 | mV |




---

## Peak-to-Peak Calculation

$$
V_{pp} = V_{max} - V_{min}
$$

$$
V_{pp} = 1.1081 - 898.7544
$$

$$
V_{pp} \approx 209.372\,mV
$$
<p align="center">
  <img width="1359" height="591" alt="image" src="https://github.com/user-attachments/assets/d166d104-0a46-4f51-b660-b8854f8ea1eb" />

</p>
---
## Voltage Gain Calculation

Input peak-to-peak voltage:

$$
V_{in(pp)} = 1.4188 - 1.399
$$

$$
V_{in(pp)} = 19.669\,mV
$$

Output peak-to-peak voltage:

$$
V_{out(pp)} = 209.37\,mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(pp)}}{V_{in(pp)}}
$$

$$
A_v = \frac{209.372}{19.66}
$$

$$
A_v \approx 10.64
$$

Since the Common Source amplifier produces phase inversion:

$$
A_v \approx -10.64
$$

### Reason for Negative Gain

The gain of a PMOS Common Source amplifier is negative because it produces phase inversion.
When the input voltage increases (gate voltage rises toward $(V_{DD})$, the source-to-gate voltage $(V_{SG})$ decreases.
This reduces the drain current $(I_D)$, causing a smaller voltage drop across $(R_D)$.
As a result, the output voltage increases, making the output 180° out of phase with the input.

## AC Analysis
<img width="1356" height="601" alt="image" src="https://github.com/user-attachments/assets/90c91d92-9868-4f3d-a196-3109f2accdc7" />



AC analysis is used to determine the frequency response of the amplifier.
To get the proper bandwidth we need to add a capacitor of 1FF because

$$
A_{vdB}= 20log(A_v)
$$


$$
A_{vdB}= 20log(10.64)
$$


$$
A_{vdB}= 20.538
$$




### Midband Gain
<img width="1350" height="620" alt="image" src="https://github.com/user-attachments/assets/eac91870-9be0-42a1-86f8-18dde6351660" />



### Half-Power (-3 dB) Frequency

$$
20.538 - 3 = 17.538
$$

From the graph, gain reaches 17.538 dB at approximately:

$$
f_H \approx 453.54MHz
$$

### Bandwidth

Since no low-frequency cutoff is observed:

$$
BW = f_H
$$

$$
BW \approx 453.54MHz
$$


