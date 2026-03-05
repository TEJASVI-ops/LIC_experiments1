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

<img width="1174" height="604" alt="image" src="https://github.com/user-attachments/assets/88c17619-c4f7-4404-9446-c70833ff96d9" />



---

## 2.3 Theoretical Calculations

### Drain Current

```
ID (theoretical) = 500 µA
```

---

### Source Voltage

```
Vrs = ID × RS
```

```
Vrs = (500 µA)(400 Ω)
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
Vout = 2 / 2 + 0.2
```

```
Vout =1+ 0.2
```

```
Vout = 1.2 V
```



## 2.5 Observation

- The simulated drain current is very close to the theoretical value.
- The simulated source voltage nearly matches the expected **0.2 V**.
- The output voltage shows a small deviation due to **device parameters, channel length modulation, and model effects in 0.18 µm technology**.

The practical (simulation) results closely agree with the theoretical calculations.

---

# 3. Transient Analysis

## 3.1 Input Signal
<img width="1361" height="624" alt="image" src="https://github.com/user-attachments/assets/c9dc2c92-2134-4ac9-a930-ac4dc8cecba5" />
### Measured Input Values

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 0.81 | V |
| Peak Voltage |819.95856|mV|
| Minimum Voltage | 800.0554 | mV |
| Input Amplitude | 20 | mV |
| Frequency | 1 | kHz |

---

---





## 3.2 Output Voltage

v<img width="1361" height="607" alt="image" src="https://github.com/user-attachments/assets/ffff7cda-fc0d-4d16-8679-bc0f8b0a9e1e" />

| Parameter | Value | Unit |
|------------|--------|------|
| DC Offset | 0.81 | V |
| Peak Voltage |819.95856|mV|
| Minimum Voltage |1.454123 | V |
| Input Amplitude | 535.9877 | mV |
| Frequency | 1 | kHz |




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

## 5.2 Gain calculations 
Voltage gain:

$$
A_v = \frac{V_{out(pp)}}{V_{in(pp)}}
$$

$$
A_v = \frac{535.9877}{20}
$$

$$
A_v \approx 26.79
$$

Since the Common Source amplifier produces phase inversion:

$$
A_v \approx -26.79
$$






### AC Analysis
<img width="1362" height="601" alt="image" src="https://github.com/user-attachments/assets/3d239ff1-1fce-4129-a257-5fd07bc8f0d9" />


## Gain Conversion to Decibels (dB)

Given voltage gain:

Av = 26.79

The formula to convert voltage gain to decibels (dB) is:

Gain (dB) = 20 log10(Av)

Substituting the value:

Gain (dB) = 20 log10(26.79)

= 20 × 1.428

= 28.56 dB

## Final Answer:

Voltage Gain = 28.56 dB





### Midband Gain
<img width="1362" height="628" alt="image" src="https://github.com/user-attachments/assets/898a1e57-ea7f-4080-a723-9e26903dfae7" />


$$
A_v \approx 28.56\,dB
$$

### Half-Power (-3 dB) Frequency

$$
28.56 - 3 = 25.56\,dB
$$

From the graph, gain reaches 2.4 dB at approximately:

$$
f_H \approx 33.8844\,GHz
$$

### Bandwidth

Since no low-frequency cutoff is observed:

$$
BW = f_H
$$

$$
BW \approx 33.8844\,GHz
$$
