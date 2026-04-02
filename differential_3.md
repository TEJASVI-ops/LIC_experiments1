# CMOS Differential Amplifier Analysis

## Circuit Overview
The circuit is a **CMOS Differential Amplifier with PMOS Current Mirror Load**.

Transistors used:
- **M1, M2:** NMOS differential pair
- **M3, M4:** PMOS current mirror active load
- **Tail Current Source:** 1 mA
- **Supply Voltage:** 1.8 V

---

# 1. DC Analysis (Operating Point)

## Supply
VDD = 1.8 V

## Input Bias
$V_{in1} = 0.9\,V + 50\,mV \sin(2\pi1000t)$  

$V_{in2} = 0.9\,V + 60\,mV \sin(2\pi1000t)$

For DC analysis only the DC value is considered.

$V_{in1} = V_{in2} = 0.9\,V$

<img width="451" height="435" alt="image" src="https://github.com/user-attachments/assets/26955334-687a-4830-b17c-ed27a4565b7a" />


## Current Distribution
$I_{tail} = 1\,mA$

$I_{D1} = I_{D2} = \frac{I_{tail}}{2}$

$I_{D1} = I_{D2} = 0.5\,mA$

---

## Current Mirror Operation

M3 is diode connected.

$I_{D3} = I_{D1} = 0.5\,mA $
Current mirrored to M4:

$I_{D4} = 0.5\,mA $

---

## Output Voltages

Since both branches carry equal current:

$V_{out1} \approx V_{out2}$

$V_{out} \approx \frac{V_{DD}}{2}$

$V_{out} \approx 0.9\,V$

---

## Transistor Region Check

### NMOS (M1, M2)

Saturation condition:
$V_{DS} \ge V_{GS} - V_{TH}$

$V_{THn} \approx 0.4\,V$

$V_{GS} = 0.9\,V$

$V_{OV} = V_{GS} - V_{TH}$

$V_{OV} = 0.9 - 0.4 = 0.5\,V$

Thus NMOS operate in **saturation**.

---

### PMOS (M3, M4)

Condition:

$V_{SD} \ge V_{SG} - |V_{THp}|$

Typical threshold:

$V_{THp} \approx -0.4\,V$

Thus PMOS also operate in **saturation region**.

---

# DC Operating Point Summary

| Parameter | Value |
|----------|------|
| Supply Voltage | 1.8 V |
| Tail Current | 1 mA |
| ID1 | 0.5 mA |
| ID2 | 0.5 mA |
| ID3 | 0.5 mA |
| ID4 | 0.5 mA |
| Vout1 | ≈ 0.9 V |
| Vout2 | ≈ 0.9 V |
| Region | Saturation |

---

# 2. AC Analysis (Small Signal Analysis)

AC components of the input signals:
$v_{in1} = 50\,mV \sin(\omega t)$  
$v_{in2} = 60\,mV \sin(\omega t)$

Differential input:

$v_{id} = v_{in1} - v_{in2}$

$v_{id} = 50\,mV - 60\,mV$

$v_{id} = -10\,mV$

---

# Small Signal Model

Voltage gain of differential amplifier:

$A_d = g_m \times R_{out}$

Where:
$g_m$ = transconductance  

$R_{out}$ = output resistance
---

# Transconductance

$g_m = \frac{2I_D}{V_{OV}}$

$I_D = 0.5\,mA$

$V_{OV} \approx 0.2\,V$

$g_m = \frac{2 \times 0.5\,mA}{0.2}$

$g_m = 5\,mS$
---

# Output Resistance

$R_{out} = r_{on} \parallel r_{op}$

Typical values:

$r_{on} \approx 50\,k\Omega$

$r_{op} \approx 50\,k\Omega$

$R_{out} \approx 25\,k\Omega$

---

# Voltage Gain

Av = gm × Rout

Av = 5 mS × 25 kΩ

Av ≈ 125

---

# Output Voltage

vo = Av × vid

vo = 125 × 10 mV

vo ≈ 1.25 V

---

# Frequency Response

Input Frequency:

f = 1 kHz

Typical CMOS differential amplifier bandwidth:

Several MHz

Therefore 1 kHz lies well inside the passband and gain remains constant.

---

# Final AC Results

| Parameter | Value |
|----------|------|
| Differential Input | 10 mV |
| Transconductance | 5 mS |
| Output Resistance | 25 kΩ |
| Voltage Gain | ≈125 |
| Output Swing | ≈1.25 V |
| Bandwidth | MHz Range |

---

# Conclusion

- The circuit functions as a **CMOS differential amplifier with active load**.
- The tail current splits equally between the NMOS transistors during DC operation.
- Small differential input voltage produces amplified output.
- Gain depends mainly on **transconductance and output resistance**.


