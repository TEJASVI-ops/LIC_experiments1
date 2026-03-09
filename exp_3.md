### EXP2 – CIRCUIT 2B – 
Common Source Amplifier with Diode-Connected NMOS Current Source and PMOS Active Load
-------------------------------------------------------------

### Circuit Implementation in LTspice
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/d42eac1b-c5f3-4c9d-b682-9396946cb67c" />



---## Width Selection – Circuit 2B
The transistor widths were initially calculated using the square-law
saturation current equation to obtain **ID ≈ 200 µA**.

| Device | Calculated Width | Practical Width |
|------|------|------|
| M1 (NMOS – Cascode) | 15.16 µm | 34.305u µm |
| M2 (NMOS – Input) | 15.16 µm |35.305µm |
| M3 (PMOS – Active Load) | 35.9 µm |34.305 µm |

### Justification
During LTspice simulation, the theoretical widths did not produce exactly **200 µA** due to non-ideal MOSFET effects.

| Reason | Effect |
|------|------|
| Channel length modulation | Changes effective drain current |
| Cascode bias sensitivity | Small voltage changes affect current |
| Mobility degradation | Reduces current compared to ideal model |

Therefore the widths were slightly adjusted in simulation until the desired operating current **ID ≈ 200 µA** was obtained while keeping all transistors in **saturation region**.

----
## Transient Analysis – Circuit 2B (Cascode)

### Input Signal Parameters

| Waveform | Frequency | Amplitude | DC Offset |
|----------|-----------|-----------|-----------|
| Sine | 1 kHz | 10 mV | 0.866 V |

| Simulation Command | Value |
|--------------------|-------|


---
### Input Waveform

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/f01785a2-a7f3-4849-b900-82eeaff16552" />


---

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 0.81 | V |
| Peak Voltage |819.95856|mV|
| Minimum Voltage | 800.0554 | mV |
| Input Amplitude | 20 | mV |
| Frequency | 1 | kHz |


### Output Waveform

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/b2b8bdb5-ff93-4e68-af60-e7f610b83a95" />


---

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 0.81 | V |
| Peak Voltage |819.95856|mV|
| Minimum Voltage | 800.0554 | mV |
| Input Amplitude | 20 | mV |
| Frequency | 1 | kHz |


# AC Analysis – Circuit 2B

Small-signal AC analysis was performed to determine the frequency response and gain characteristics of the cascode amplifier.

### Simulation Parameters

| AC Command | Input AC Magnitude |
|------------|--------------------|
| `.ac dec 1000 .1 1G` | 1 V |

---
<img width="1915" height="848" alt="2bac_gain" src="https://github.com/user-attachments/assets/eb71ebf0-3b06-49f0-aa7c-752a2d80bcfd" />

---
## Gain and Frequency Characteristics – Circuit 2B

| Parameter | Calculation | Result |
|-----------|-------------|--------|
| Midband Gain | From AC plot | **6.94 dB (≈ 2.22 V/V)** |
| −3 dB Bandwidth | From AC plot | **48.417 MHz** |
| Gain Bandwidth Product (GBW) | 2.22 × 48.417 MHz | **≈ 107.48 MHz** |
| Unity Gain Bandwidth (UGB) | Frequency at 0 dB | **=90.782 MHz** |

-----
# Theoretical Gain – Circuit 2B

For TSMC 180 nm CMOS technology, the channel-length modulation parameter typically lies in the rangeλ ≈ 0.1 – 0.2 V⁻¹

Given

| Parameter | Value |
|-----------|------|
| ID | 200 µA |
| Vov | 0.20 V |
| gm | 1.6 mS |

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

Av = (1.6mS / 55.3) × 32.7k

Av ≈ **0.94 V/V**

Gain in dB

Av(dB) = 20 log(0.94)

Av ≈ **−0.5 dB**

---
### Reason for Difference Between Theory and Simulation

The theoretical calculation uses a simplified small-signal MOS model where

ro = 1 / (λID)

However, LTspice uses the complete **BSIM MOSFET model**, which includes:

• mobility degradation  
• body effect  
• velocity saturation  
• detailed channel-length modulation  

These effects increase the effective output resistance of the cascode stage,resulting in a higher simulated gain (**≈ 6.9 dB**) compared to the simplified analytical value.

---
### EXP2 – CIRCUIT 2C – 
Common Source Amplifier with Diode-Connected NMOS Current Source and PMOS Active Load
-------------------------------------------------------------

### Circuit Implementation in LTspice
<img width="759" height="850" alt="circuit2c" src="https://github.com/user-attachments/assets/f8919fea-a198-4e16-bd7e-c94ccda1caae" />

---
# DC Analysis – Circuit 2C

## Design Conditions

| VDD | ID | VTHn | VTHp |
|----|----|----|----|
| 2 V | 200 µA | 0.36 V | −0.39 V |

---
## Voltage Limits for Saturation Operation

| Parameter | Minimum | Maximum | Reason |
|-----------|---------|---------|--------|
| VGS (NMOS) | ≥ 0.36 V | ≤ 1.8 V | Channel formation |
| VDS (NMOS) | ≥ VOV | ≤ 1.8 V | Saturation condition |
| VSG (PMOS) | ≥ 0.39 V | ≤ 1.8 V | PMOS conduction |
| VSD (PMOS) | ≥ VOV | ≤ 1.8 V | Saturation condition |

---
# Overdrive Voltage Verification

| Calculation | Result |
|-------------|--------|
| VGS = VTH + VOV = 0.36 + 0.25 | **0.61 V** |
| VOV = VGS − VTH = 0.61 − 0.36 | **0.25 V** |

### Allowable Range

| Minimum VOV | Maximum VOV |
|-------------|-------------|
| > 0 | < VDS |

Since

VDS ≈ **0.9 V**

the allowable range becomes

0 < VOV < 0.9 V

The obtained value

**VOV = 0.25 V**

lies comfortably within this range.

### Justification
A moderate overdrive voltage

• provides sufficient transconductance  
• maintains stable drain current  
• leaves voltage headroom for signal swing

---
# Diode-Connected NMOS Bias (M3)

In a diode-connected MOSFET

VD = VG

Thus

| Calculation | Result |
|-------------|--------|
| VGS3 = VTH + VOV = 0.36 + 0.25 | **0.61 V** |

Since the source of M3 is grounded

| Node | Voltage |
|------|--------|
| VS3 | 0 V |
| VD3 = VG3 | **0.61 V** |

This node becomes the **source of M1**.

Therefore

| Node | Voltage |
|------|--------|
| VS1 | **0.61 V** |

### Justification

The diode-connected NMOS automatically adjusts its gate-source voltage to maintain the desired drain current (≈200 µA). This fixes the node voltage at approximately **0.61 V**, establishing the correct bias for the amplifier.

---
# Gate Bias of M1

For transistor M1 to carry the same current:

| Calculation | Result |
|-------------|--------|
| VGS1 = VTH + VOV = 0.36 + 0.25 | **0.61 V** |
| VG1 = VS1 + VGS1 = 0.61 + 0.61 | **1.22 V** |

Thus the **input DC bias voltage** is

**VIN(DC) ≈ 1.22 V**

---
# Output Voltage Selection

For maximum signal swing

VDS ≈ VDD / 2

| Calculation | Result |
|-------------|--------|
| VDS = 2/ 2 | **1 V** |

Therefore

| Calculation | Result |
|-------------|--------|
| Vout = VDS + VS1 = 0.9 + 0.61 | **≈ 1.5 V** |

---
# PMOS Active Load Bias

| Calculation | Result |
|-------------|--------|
| VSG2 = |VTHp| + VOV = 0.39 + 0.25 | **0.64 V** |
| VG2 = VDD − VSG2 = 1.8 − 0.64 | **1.16 V** |

Drain-source voltage

| Calculation | Result |
|-------------|--------|
| VSD2 = 1.8 − 1.5 | **0.3 V** |

### Saturation Check

| Device | Condition | Result |
|------|-----------|--------|
| M1 (NMOS) | VDS ≥ VOV | 0.9 ≥ 0.25 ✔ |
| M3 (NMOS) | VDS ≥ VOV | 0.61 ≥ 0.25 ✔ |
| M2 (PMOS) | VSD ≥ VOV | 0.3 ≥ 0.25 ✔ |

Thus **all transistors operate in saturation region**.

---
# Final DC Operating Point

| VS1 | Vout | VG1 | VG2 | ID | VOV |
|----|----|----|----|----|----|
| 0.61 V | 1.5 V | 1.22 V | 1.16 V | 200 µA | 0.25 V |

The diode-connected NMOS automatically establishes the correct source voltage for M1, ensuring stable biasing and maintaining all transistors in saturation.

---
### LTspice Operating Point

<img width="605" height="541" alt="circuit2cop" src="https://github.com/user-attachments/assets/4974f15c-eb00-422d-be8b-91ca110c9c50" />

## Width Selection – Circuit 2C
The transistor widths were initially calculated using the square-law saturation current equation to obtain **ID ≈ 200 µA**.

| Device | Calculated Width | Practical Width |
|------|------|------|
| M1 (NMOS – Amplifier) | 15.16 µm | 26.34 µm |
| M2 (PMOS – Active Load) | 35.9 µm | 87.87 µm |
| M3 (NMOS – Diode Connected Current Source) | 15.16 µm | 33.26 µm |

### Justification

During LTspice simulation, the theoretical widths did not produce exactly **200 µA** due to practical MOSFET model effects.

| Reason | Effect |
|------|------|
| Channel length modulation | Changes effective drain current |
| Diode-connected bias sensitivity | Current strongly depends on VGS |
| Mobility degradation | Reduces current compared to ideal model |

Therefore the widths were slightly adjusted in simulation until the desired operating current **ID ≈ 200 µA** was obtained while keeping all transistors in **saturation region**.

---
## Transient Analysis – Circuit 2C (Common Source with Diode-Connected Current Source)

### Input Signal Parameters

| Waveform | Frequency | Amplitude | DC Offset |
|----------|-----------|-----------|-----------|
| Sine | 1 kHz | 10 mV | 1.22 V |

| Simulation Command | Value |
|--------------------|-------|
| Transient Command | `.tran 0 5m` |

---
### Input Waveform

<img width="1919" height="861" alt="2ct_input" src="https://github.com/user-attachments/assets/488921a3-53c6-42f0-b3b1-63ef0d9aa6ec" />

---
### Output Waveform

<img width="1919" height="857" alt="2ct_output" src="https://github.com/user-attachments/assets/fdd3775a-909a-4a35-aa28-f4aa44f14767" />

---
### Input & Output Comparison

<img width="1909" height="858" alt="2ct_combined" src="https://github.com/user-attachments/assets/feda64ee-1a11-4c39-af94-20888a61345f" />

---
## Practical Gain Calculation

| Vin(p-p) | Vout(p-p) | Gain (Av) | Gain (dB) |
|----------|-----------|-----------|-----------|
| 1.229 − 1.210 = **0.019 V** | 1.618 − 1.235 = **0.383 V** | 0.383 / 0.019 = **20.16 V/V** | **26.08 dB** |

---
### Observation

The output waveform is inverted with respect to the input signal, confirming **common-source operation**. The output amplitude is significantly larger than the input amplitude, demonstrating proper voltage amplification while maintaining a stable bias point around **1.5 V**.

----
# AC Analysis – Circuit 2C

Small-signal AC analysis was performed to determine the **frequency response, midband gain, and bandwidth** of the amplifier.

### Simulation Parameters

| Parameter | Value |
|-----------|------|
| AC Command | `.ac dec 1000 .1 1G` |
| Input AC magnitude | 1 V |

---
<img width="1917" height="862" alt="2cac_gain" src="https://github.com/user-attachments/assets/a3375b34-a0da-4127-876e-fd4659fe7594" />

---
## Frequency Response Results – Circuit 2C

| Gain (dB) | Gain (V/V) | −3 dB Gain | Bandwidth | GBW | UGB |
|-----------|------------|------------|-----------|------|------|
| 25.55 dB | 10^(25.55/20) = **18.94** | 22.55 dB | **119.124 MHz** | 18.94 × 119.124 MHz = **2.25 GHz** | **≈ 2.691 GHz** |

The AC response confirms the amplifier’s midband gain and bandwidth. The gain–bandwidth product and unity gain bandwidth were obtainedfrom the same frequency response plot.
