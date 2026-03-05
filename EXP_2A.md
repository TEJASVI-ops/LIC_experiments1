# Linear Integrated Circuits Laboratory

## Experiment 02  
### MOS Common Source Amplifier Configurations (TSMC 180 nm)

---

# 1. Objective

The objective of this experiment is to **design, simulate, and analyze different MOSFET amplifier configurations** using **TSMC 180 nm CMOS technology** in **LTspice**.

The amplifier configurations investigated in this experiment are:

1. **Common Source amplifier with source degeneration**
2. **Cascode MOS amplifier**
3. **Current mirror loaded common source amplifier**

Each circuit is analyzed using **DC operating point analysis, transient simulation, and AC frequency response** to evaluate:

- Biasing conditions  
- Voltage gain  
- Signal inversion  
- Bandwidth and frequency response  

---

# 2. Software and Technology

| Item | Specification |
|-----|---------------|
| Simulation Tool | LTspice |
| Technology | TSMC 180 nm CMOS |
| Supply Voltage |2 V |
| Devices Used | NMOS and PMOS |

The circuits are designed using **TSMC 180 nm MOSFET models**, which represent realistic transistor behavior used in CMOS integrated circuits.

---

# 3. Background Theory

MOSFET amplifiers operate with the transistor biased in the **saturation region**, where the drain current mainly depends on the **gate–source voltage**.

When the MOSFET operates in saturation, it behaves as a **voltage-controlled current source**, which enables the device to amplify small input signals.

For an NMOS transistor to remain in saturation:

```
VDS ≥ VGS − VTH
```

Where:

- **VGS** → Gate–source voltage  
- **VTH** → Threshold voltage  
- **VDS** → Drain–source voltage  

To ensure proper amplification, the transistor must **remain in the saturation region for the entire signal swing**.

---

## Important MOSFET Relations

| Parameter | Expression | Description |
|-----------|------------|-------------|
| Drain Current | ID = (1/2) μCox (W/L) Vov² | Drain current in saturation |
| Overdrive Voltage | Vov = VGS − VTH | Effective gate voltage |
| Transconductance | gm = 2ID / Vov | Small-signal gain parameter |
| Output Resistance | ro = 1 / (λID) | Effect of channel length modulation |
| Voltage Gain | Av = − gm Rout | Approximate voltage gain of a CS amplifier |

These equations are used for **transistor sizing and theoretical gain calculations** in MOS amplifier design.

---

# 4. Technology Parameters (TSMC 180 nm)

The design is implemented using **TSMC 180 nm CMOS technology**.  
The following technology parameters are used for device sizing and circuit analysis.

| Parameter | Value |
|----------|------|
| Supply Voltage |2 V |
| Target Drain Current | 500 µA |
| Overdrive Voltage | 0.20 V |
| Channel Length | 180 nm |
| Electron Mobility | 273.8 × 10⁻⁴ m²/V·s |
| Hole Mobility | 115.7 × 10⁻⁴ m²/V·s |
| Oxide Thickness | 4.1 nm |

---

## Gate Oxide Capacitance

The gate oxide capacitance per unit area is given by

```
Cox = εox / tox
```

Where

- **εox** = Permittivity of silicon dioxide  
- **tox** = Oxide thickness  

Substituting the values:

```
Cox = (3.54 × 10⁻¹¹) / (4.1 × 10⁻⁹)
```

```
Cox ≈ 8.63 mF/m²
```

---

# 5. Process Transconductance Parameters

The process transconductance parameter is calculated as

```
μCox
```

| Device | Result |
|------|------|
| μnCox | ≈ 236 µA/V² |
| μpCox | ≈ 113.5µA/V² |

These parameters are used to determine the **required transistor width for the desired drain current**.

---

# 6. Transistor Sizing

The MOSFET width is obtained using the **saturation current equation**

```
ID = (1/2) μCox (W/L) Vov²
```

Rearranging the equation to obtain the transistor width:

```
W = (2 ID L) / ( μCox Vov² )
```

This equation is used to determine the required **NMOS and PMOS widths** for the target drain current of **200 µA**.

---

# 7. Calculated Transistor Widths

Using the saturation current equation

```
ID = (1/2) μCox (W/L) Vov²
```

the transistor widths are calculated to achieve the **target drain current of 200 µA** with **Vov = 0.25 V** and **L = 0.18 µm**.

| Device | Calculated Width |
|------|------------------|
| NMOS | ≈ 38.855µm |
| PMOS | ≈ 91.2 µm |

The **PMOS width is larger than the NMOS width** because **hole mobility is lower than electron mobility**, requiring a wider device to carry the same current.

---

## Final Transistor Aspect Ratios

| Transistor | W | L | W/L |
|-----------|---|---|-----|
| NMOS | 38.855µm | 0.18 µm |215.86 |
| PMOS |  91.2 µm | 0.18 µm | 506.66 |

These aspect ratios are used in the LTspice simulation to ensure the desired **drain current of approximately 200 µA** while maintaining proper biasing conditions.

---

# Circuit 2A  
## Source Degenerated Common Source Amplifier

A **source resistor RS** is introduced at the source terminal of the NMOS transistor.  
This configuration provides **local negative feedback**, which improves bias stability and linearity.

### Advantages

- Improved bias stability  
- Reduced gain sensitivity to device variations  
- Better linearity  
- Controlled voltage gain  

The approximate voltage gain is given by

```
Av = − gm1 Rout / (1 + gm1 RS)
```

---

## LTspice Circuit
<img width="1024" height="568" alt="image" src="https://github.com/user-attachments/assets/f655b6fb-af1a-47ee-8ea0-4342ece6e7de" />


The circuit is designed such that the MOSFET operates with

```
ID ≈ 500 µA
```

while maintaining maximum possible output voltage swing.

---

# DC Operating Point Analysis

The DC biasing is selected to ensure that **both NMOS and PMOS operate in saturation**.

## Design Conditions

| Parameter | Value |
|----------|------|
| VDD | 2 V |
| ID | 500 µA |
| VTHn | 0.36 V |
| VTHp | −0.39 V |

---

## Saturation Conditions

| Device | Condition |
|------|-----------|
| NMOS | VDS ≥ Vov |
| PMOS | VSD ≥ Vov |

---

## Choice of Drain Voltage

To obtain **maximum symmetrical output swing**, the drain voltage is chosen approximately at half of the supply voltage.

```
VD ≈ VDD / 2
```

```
VD = 2 / 2
```

```
VD ≈ 1 V
```

---

## Source Voltage

A small voltage drop is introduced across the source resistor to stabilize the operating point.

```
VS ≈ 0.2 V
```

---

## Output Voltage

```
VDS = Vout − VS
```

```
1 = Vout − 0.2
```

```
Vout ≈ 1.2 V
```

---

## Source Resistor

```
RS = VS / ID
```

```
RS = 0.2 / (500 µA)
```

```
RS = 0.4 kΩ
```

---

## NMOS Gate Voltage

```
VGS = VTH + Vov
```

```
VGS = 0.36 + 0.25
```

```
VGS = 0.61 V
```

Gate voltage:

```
VG = VGS + VS
```

```
VG ≈ 0.81 V
```

---

## PMOS Gate Voltage

```
VSG = Vov + |VTHp|
```

```
VSG = 0.25 + 0.39
```

```
VSG = 0.64 V
```

PMOS gate voltage:

```
VGp = VDD − VSG
```

```
VGp ≈ 1.36 V
```

---

## Saturation Verification

Both transistors operate in the **saturation region**, ensuring proper amplifier operation.

---

## 2.2 DC Currents (Simulation)

| Parameter | Value | Unit |
|-----------|--------|------|
| **Id (M1)** | **0.000297364** | A |
| **Id (M2)** | **−0.000297364** | A |
| I(R1) | 0.000297364 | A |
| Is (M1) | −0.000297364 | A |
| Is (M2) | 0.000297364 | A |

---

## 2.3 Theoretical Calculations

### Drain Current

```
ID (theoretical) = 300 µA
```

---

### Source Voltage

```
Vrs = ID × RS
```

```
Vrs = (300 µA)(666.67 Ω)
```

```
Vrs ≈ 0.2 V
```

---

### Output Voltage

```
Vout = VDD / 2 + 0.2
```

```
Vout = 1.5 / 2 + 0.2
```

```
Vout = 0.75 + 0.2
```

```
Vout = 0.95 V
```



## 2.5 Observation

- The simulated drain current is very close to the theoretical value.
- The simulated source voltage nearly matches the expected **0.2 V**.
- The output voltage shows a small deviation due to **device parameters, channel length modulation, and model effects in 0.18 µm technology**.

The practical (simulation) results closely agree with the theoretical calculations.

---

# 3. Transient Analysis

![Transient Analysis](https://github.com/user-attachments/assets/0fdb1235-34b4-4f74-aaa7-8c059e63c987)

---

## 3.1 Input Signal

```
Vin(t) = 0.81 + 10 mV sin(2π · 1 kHz · t)
```

```
VDC = 0.81 V
```

```
Vm = 10 mV
```

```
f = 1 kHz
```

---

## 3.2 Output Voltage

```
Vout(t) = VOUT,DC + vout(t)
```

```
VOUT,DC ≈ 0.970546 V
```

```
vout(t) = Av · 10 mV · sin(2π · 1 kHz · t)
```

---

## 3.3 Source Voltage

```
Vrs(t) = 0.198243 + vrs(t)
```

---

## 3.4 Drain Current

```
ID(t) = 297.364 µA + id(t)
```

```
id(t) = gm · 10 mV · sin(2π · 1 kHz · t)
```

---

# 4. Transient Analysis – Output Voltage Waveform

![Output Waveform](https://github.com/user-attachments/assets/e9635040-8da1-4b96-8b2d-e510618b801b)

---

## 4.1 Observed Output Waveform

```
VOUT,DC ≈ 0.970546 V
```

---

## 4.2 Peak and Minimum Values

```
Vout,max ≈ 1.06 V
Vout,min ≈ 0.86 V
```

---

## 4.3 Peak-to-Peak Voltage

```
Vout,pp = Vout,max − Vout,min
```

```
Vout,pp = 1.06 − 0.86 = 0.20 V
```

```
Vout,peak = Vout,pp / 2 = 0.10 V
```

---

## 4.4 Frequency Verification

```
T ≈ 1 ms
```

```
f = 1 / T = 1 / 1 ms = 1 kHz
```

---

## 4.5 Output Voltage Expression

```
Vout(t) ≈ 0.970546 + 0.10 sin(2π × 1 kHz × t)
```

---

# 4.6 Transient Analysis – Input Voltage Waveform

![Input Waveform](https://github.com/user-attachments/assets/4a7af064-eed5-4e2f-8b2a-66d9c2ed31b3)

---

## 4.6.1 Observed Input Waveform

```
VIN,DC ≈ 0.81 V
```

---

## 4.6.2 Peak and Minimum Values

```
Vin,max ≈ 0.82 V
Vin,min ≈ 0.80 V
```

---

## 4.6.3 Peak-to-Peak Voltage

```
Vin,pp = Vin,max − Vin,min
```

```
Vin,pp = 0.82 − 0.80 = 0.02 V
```

```
Vin,peak = Vin,pp / 2 = 0.01 V = 10 mV
```

---

## 4.6.4 Frequency Verification

```
T ≈ 1 ms
```

```
f = 1 / T = 1 / 1 ms = 1 kHz
```

---

## 4.6.5 Input Voltage Expression

```
Vin(t) ≈ 0.81 + 0.01 sin(2π × 1 kHz × t)
```

---

# 5. Theoretical Voltage Gain Calculation

Given:

```
Id = 500 µA
λ = 0.1 V⁻¹
Vov = 0.25 V
Rs = 400 Ω
```

---

## 5.1 Transconductance (gm)

```
gm = 2Id / Vov
```

```
gm = (2 × 500 × 10⁻⁶) / 0.25
```

```
gm = 0.0004 S
```

```
gm = 2.4 mS
```

---

## 5.2 Output Resistance (ro)

```
ro = 1 / (λ Id)
```

```
ro ≈ 33,333 Ω
```

```
ro ≈ 33.3 kΩ
```

---

## 5.3 Effective Output Resistance

```
ro,eff = ro / 2
```

```
ro,eff ≈ 16,667 Ω
```

```
ro,eff ≈ 16.7 kΩ
```

---

## 5.4 Gain Without Source Degeneration

```
Av = gm × ro,eff
```

```
Av ≈ 40
```

```
Av,dB ≈ 32 dB
```

---

## 5.5 Gain With Source Degeneration

```
Av = − gm ro,eff / (1 + gm Rs)
```

```
gm ro,eff ≈ 40
```

```
gm Rs ≈ 1.6
```

```
Av ≈ −15.38
```

```
|Av| ≈ 15.38
```

```
Av,dB ≈ 23.7 dB
```

---

### Final Comparison

```
Gain without Rs ≈ 40 (32 dB)
Gain with Rs ≈ 15.38 (23.7 dB)
Practical Gain ≈ 10 (20 dB)
```

---

# 7. AC Analysis

![AC Analysis](https://github.com/user-attachments/assets/a1c8e12c-4be3-43de-b52f-e0b82adc940c)

AC command:

```
.ac dec 100 100 100G
```

---

![AC Frequency Response](https://github.com/user-attachments/assets/6a0ebec4-a6bb-4c4e-a79b-27777815278c)

---

## 7.1 Midband Gain

```
Av ≈ 15.38
```

```
Av,dB ≈ 20.7 dB
```

---

## 7.2 Frequency Response

### Low Frequency Region

- Gain ≈ constant  
- Phase ≈ 180°

### High Frequency Region

- Gain decreases due to **Cgs, Cgd, Cdb**

---

![Bandwidth Graph](https://github.com/user-attachments/assets/ffd7f58b-6cf0-4cfb-9971-661229e47ad3)

---

## 7.3 Bandwidth

```
Midband gain = 20.7 dB
```

```
Cutoff gain = 20.7 − 3
```

```
Cutoff gain ≈ 17.7 dB
```

```
Bandwidth = fH − fL
```
