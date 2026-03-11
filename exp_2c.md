### EXP2 – CIRCUIT 2c – 
Common Source Amplifier with Diode-Connected NMOS Current Source and PMOS Active Load
-------------------------------------------------------------

### Circuit Implementation in LTspice
<img width="1915" height="967" alt="image" src="https://github.com/user-attachments/assets/c87dc8d3-0a0f-4274-97bd-32e65d11522d" />



---## Width Selection – Circuit 2c
The transistor widths were initially calculated using the square-law
saturation current equation to obtain **ID ≈ 200 µA**.

| Device | Calculated Width | Practical Width |
|------|------|------|
| M1 (NMOS – Cascode) | 15.16 µm | 101.7 µm |
| M2 (NMOS – Input) | 15.16 µm |101.7µm |
| M3 (PMOS – Active Load) | 35.9 µm |72 µm |

### Justification
During LTspice simulation, the theoretical widths did not produce exactly **200 µA** due to non-ideal MOSFET effects.

| Reason | Effect |
|------|------|
| Channel length modulation | Changes effective drain current |
| Cascode bias sensitivity | Small voltage changes affect current |
| Mobility degradation | Reduces current compared to ideal model |

Therefore the widths were slightly adjusted in simulation until the desired operating current **ID ≈ 200 µA** was obtained while keeping all transistors in **saturation region**.

----
## Transient Analysis – Circuit 2c (Cascode)



---
### Input Waveform

<img width="1903" height="882" alt="image" src="https://github.com/user-attachments/assets/e53547eb-18e5-48e3-a4f0-8d845ab71cb4" />


---

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 1.12 | V |
| Peak Voltage |1.1299|V|
| Minimum Voltage | 1.11 | V |
| Input Amplitude | 20 | mV |
| Frequency | 1 | kHz |


### Output Waveform

<img width="1897" height="875" alt="image" src="https://github.com/user-attachments/assets/08a49471-6177-4756-b937-6f44c494c5e1" />


---

| Parameter | Value | Unit |
|------------|--------|------|

| Peak Voltage |1.3104|V|
| Minimum Voltage |875.19 | mV |
| Input Amplitude |435.24 | mV |
| Frequency | 1 | kHz |


# AC Analysis – Circuit 2c

Small-signal AC analysis was performed to determine the frequency response and gain characteristics of the cascode amplifier.

### Simulation Parameters

| AC Command | Input AC Magnitude |
|------------|--------------------|
| `.ac dec 1000 .001 1G` | 1 V |

---
<img width="1905" height="886" alt="image" src="https://github.com/user-attachments/assets/59ecc523-dea2-4a4e-9e75-a47fe2fc5fd7" />


---
## Gain and Frequency Characteristics – Circuit 2c

| Parameter | Calculation | Result |
|-----------|-------------|--------|
| Midband Gain | From AC plot | **27 dB (≈ 22.392 V/V)** |
| −3 dB Bandwidth | From AC plot | **79.432823MHz MHz** |
| Gain Bandwidth Product (GBW) | 22.39×79.432 | **≈ 107.48 MHz** |
| Unity Gain Bandwidth (UGB) | Frequency at 0 dB | **=3.1622777GHz** |

-----
# Theoretical Gain – Circuit 2c

For TSMC 180 nm CMOS technology, the channel-length modulation parameter typically lies in the rangeλ ≈ 0.1 – 0.2 V⁻¹

Given

| Parameter | Value |
|-----------|------|
| ID | 200 µA |
| Vov | 0.20 V |


Output resistance

ro = 1 / (λ ID)

Taking a typical value λ = 0.15 V⁻¹

ro = 1 / (0.15 × 200 µA)

ro ≈ **33.3 kΩ**

Thus

ro1 ≈ ro2 ≈ ro3 ≈ **33.3 kΩ**

---
### Gain Expression

For the cascode stage with active load

Av =
− gm1 /
(1 + gm1ro2 + ro2/ro1)
×
([gm1ro2ro1 + ro2 + ro1] ∥ ro3)

---
### Calculation

| Step | Result |
|-----|-------|
| Denominator | 1 + (1.6mS × 33.3k) + 1 = **55.3** |
| Bracket term | (1.6mS × 33.3k × 33.3k + 66.6k) ∥ 33.3k |
| | **≈ 32.7 kΩ** |

Voltage gain

$$
A_v = \frac{V_{out}}{V_{in}}
$$

$$
A_v = \frac{435.24}{20}}
$$
$$
A_v = 21.762
$$

Gain in dB

Av(dB) = 20 log(21.762)

Av ≈ **−26.75**

---
### Reason for Difference Between Theory and Simulation

The theoretical calculation uses a simplified small-signal MOS model where

ro = 1 / (λID)

However, LTspice uses the complete **BSIM MOSFET model**, which includes:

• mobility degradation  
• body effect  
• velocity saturation  
• detailed channel-length modulation  

These effects increase the effective output resistance of the cascode stage,resulting in a higher simulated gain (**≈ 26.75 dB**) compared to the simplified analytical value.

---
