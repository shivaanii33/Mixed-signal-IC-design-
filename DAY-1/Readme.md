
# Day 1 – Introduction to Analog IC Design & Bandgap Reference Basics 
##  Objective of Day 1
The objective of Day 1 was to build a **strong foundation in analog and mixed-signal IC design**, understand **MOSFET operation**, and introduce the **need for stable reference circuits** such as **Bandgap References** in integrated circuits.

## **Introduction to Analog and Mixed-Signal IC Design**

Analog IC design focuses on circuits that process continuous real-world signals such as voltage, current, temperature, sound, and pressure. Since these signals originate from the physical world, analog circuits are required to sense, amplify, filter, and condition them before further processing.

Digital ICs operate using discrete signal levels (0 and 1), whereas mixed-signal ICs integrate both analog and digital circuits on the same chip. This integration allows real-world analog signals to be converted into digital form and processed by digital logic efficiently.

Common examples of mixed-signal circuits include:
- Analog-to-Digital Converters (ADCs)
- Digital-to-Analog Converters (DACs)
- System-on-Chip (SoC) devices
- Automotive, communication, and IoT electronics

Mixed-signal IC design must handle challenges such as process variation, supply voltage variation, and temperature changes (PVT), along with noise coupling between analog and digital blocks. To overcome these challenges, Electronic Design Automation (EDA) tools such as Cadence are used for schematic design, simulation, layout, and verification.

Analog and mixed-signal ICs form the critical interface between the physical world and digital processing systems and are essential in modern electronic applications.

## **MOSFET Fundamentals**

The Metal–Oxide–Semiconductor Field Effect Transistor (MOSFET) is a voltage-controlled device extensively used in analog and digital integrated circuits. In analog IC design, MOSFETs primarily operate as **voltage-controlled current sources**.

A MOSFET consists of four terminals: Gate (G), Drain (D), Source (S), and Body (B). The gate is insulated from the channel by a thin oxide layer, resulting in **negligible gate current** and high input impedance.

---

### Regions of Operation (NMOS)

**1. Cut-off Region**
- Condition:  
  `VGS < VTH`
- Channel is not formed  
- Drain current:  
  `ID ≈ 0`

**2. Triode (Linear) Region**
- Condition:  
  `VGS > VTH` and `VDS < VGS − VTH`
- MOSFET behaves as a voltage-controlled resistor  
- Drain current:  
  `ID = μn Cox (W/L) [ (VGS − VTH)VDS − (VDS² / 2) ]`
- If `VDS << 2(VGS − VTH)` then 
  - `Ron = 1/(μn Cox (W/L) (VGS − VTH)`

**3. Saturation Region**
- Condition:  
  `VGS > VTH` and `VDS ≥ VGS − VTH`
- Channel pinch-off occurs  
- MOSFET behaves as a current source  
- Drain current:  
  `ID = (1/2) μn Cox (W/L) (VGS − VTH)² (1 + λVDS)`

---

### PMOS Operation

PMOS equations are similar in magnitude but opposite in polarity:

- Saturation current:  
  `|ID| = (1/2) μp Cox (W/L) (|VGS| − |VTH|)² (1 + λ|VDS|)`

---


### Key Observations

- MOSFETs in saturation act as **current sources**
- Drain current depends on:
  - Gate overdrive voltage `(VGS − VTH)`
  - Aspect ratio `(W/L)`
- Channel-length modulation makes the current source non-ideal
- NMOS and PMOS have identical small-signal models
- MOSFETs are fundamental building blocks for analog ICs

---

### Applications in Analog IC Design
- Current mirrors
- Amplifiers
- Biasing networks
- Bandgap reference circuits
- LDOs and PLL bias blocks

## **Introduction to Mixed-Signal IC Design Flow**

Mixed-signal IC design integrates **analog and digital circuits** on a single chip. Since both domains have different design requirements, a structured design flow is followed to ensure correct functionality, performance, and reliability.

---

### Design Specification
- Define system specifications and constraints
- Consider:
  - Process variation
  - Supply voltage variation
  - Temperature variation (PVT)
- Develop test benches for verification

---

### Domain-Specific Design

**Analog Domain**
- Schematic capture
- Circuit-level simulation
- Optimization for gain, bandwidth, power, and noise

**Digital Domain**
- RTL design entry
- Behavioral and functional simulation
- Logic synthesis

---

### Physical Design
- Analog layout using parameterized cells (PCells)
- Digital place and route
- Power and clock planning
- Layout verification:
  - Design Rule Check (DRC)
  - Layout Versus Schematic (LVS)
- Parasitic extraction and post-layout simulation

---

### Mixed-Signal Verification
- Co-simulation of analog and digital blocks
- Verification across PVT corners
- Ensure correct interaction between domains

---

### Full-Chip Integration and Tape-Out
- Integration of all analog and digital blocks
- Final physical verification
- GDSII generation and tape-out for fabrication

---

### Summary
The mixed-signal IC design flow coordinates analog and digital design processes to ensure reliable operation under process, voltage, and temperature variations. Proper verification at each stage is essential for successful IC fabrication.
## **Three Important Blocks in Chip Design**

Even the most advanced digital or mixed-signal chip cannot work reliably on its own. Every IC depends on a few **basic analog blocks** that provide stable **voltage**, **current**, and **timing**. The three most important blocks are the **PLL**, **Bandgap Reference (BGR)**, and **Low Dropout Regulator (LDO)**.

---

### 1️⃣ Phase-Locked Loop (PLL)

A Phase-Locked Loop (PLL) is used to generate **clean and accurate clock signals** inside a chip. It continuously compares its output clock with a reference clock and adjusts itself until both are synchronized.

In simple words, a PLL makes sure that **all parts of the chip run at the correct speed and at the right time**.

**Why PLL matters:**
- Digital circuits depend completely on clock timing
- Small clock errors can reduce performance or cause failures
- High-speed chips cannot work without PLLs

**Where it is used:**
- Processors and microcontrollers
- Communication systems (Wi-Fi, 5G)
- High-speed digital and mixed-signal ICs

---

### 2️⃣ Bandgap Reference (BGR)

A Bandgap Reference (BGR) provides a **stable reference voltage** that does not change much with temperature, supply voltage, or manufacturing variations. For silicon chips, this reference is usually around **1.2 V**.

Simply put, the BGR acts like a **voltage anchor** for the entire chip.

**Why BGR matters:**
- Transistor behavior changes with temperature
- A small reference error affects the whole chip
- Accurate biasing depends on a stable reference

**Where it is used:**
- ADCs and DACs
- Voltage regulators
- Biasing circuits in analog blocks

---

### 3️⃣ Low Dropout Regulator (LDO)

An LDO is an on-chip voltage regulator that provides a **clean and steady supply voltage** to different blocks of the IC. It helps protect sensitive analog circuits from noisy or unstable power sources.

In simple terms, an LDO acts like a **noise filter and stabilizer** for power.

**Why LDO matters:**
- External power supplies are often noisy
- Analog blocks need clean power to work correctly
- Voltage fluctuations can cause malfunction or data errors

**Where it is used:**
- Powering PLLs and ADCs
- Supplying analog and RF blocks
- On-chip power management

---

### How These Blocks Work Together

- The **BGR** creates a stable reference voltage  
- The **LDO** uses this reference to generate clean supply voltages  
- The **PLL** uses the clean supply and reference to generate accurate clocks  

Together, these blocks ensure that the chip works **reliably across process, voltage, and temperature variations**.

---

## **Basic Bandgap Reference Circuit** 

![Basic Bandgap Reference Circuit](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/e0dc4744559a0af65f98d32f78892feb640943aa/DAY-1/images/Screenshot%202026-01-27%20205517.png)

## Temperature-Independent Reference Voltage


In integrated circuit (IC) design, many critical blocks such as ADCs, DACs, LDOs, and PLLs require a stable reference voltage. This reference must remain nearly constant even when temperature, supply voltage, and process parameters vary. A Bandgap Reference (BGR) circuit is used to generate such a temperature-independent reference voltage.

---

## Need for Temperature-Independent References

Transistor parameters change with temperature, including base–emitter voltage, threshold voltage, and carrier mobility. If the reference voltage varies with temperature, it leads to gain errors in ADCs and DACs, incorrect biasing, and degraded circuit performance. Hence, ICs require a reference voltage with a near-zero temperature coefficient (TC).

---

## Temperature Dependence of BJT Base–Emitter Voltage (CTAT)

The collector current of a BJT is given by:

IC = IS · exp(VBE / VT)

where VT = kT / q is the thermal voltage.

Rewriting the equation:

VBE = VT ln(IC / IS)

At room temperature (approximately 300 K):

∂VBE / ∂T ≈ −1.5 mV/K

This shows that the base–emitter voltage decreases as temperature increases. Hence, VBE has a negative temperature coefficient and is classified as a CTAT (Complementary To Absolute Temperature) voltage.

---

## PTAT Voltage Generation Using Two BJTs

Consider two identical BJTs operating at different current densities. Let transistor Q1 carry current I and transistor Q2 carry current nI. The difference between their base–emitter voltages is:

ΔVBE = VBE1 − VBE2 = VT ln(n)

Since VT = kT / q, the voltage difference ΔVBE is directly proportional to absolute temperature:

ΔVBE ∝ T

Thus, ΔVBE has a positive temperature coefficient and is called a PTAT (Proportional To Absolute Temperature) voltage.

---

## Core Idea of Bandgap Reference

The basic idea of a bandgap reference is to combine two voltages with opposite temperature coefficients:

- CTAT voltage: VBE (decreases with temperature)
- PTAT voltage: VT ln(n) (increases with temperature)

By adding these voltages with proper scaling, the temperature dependence can be cancelled:

VREF = VBE + α · VT ln(n)

where α is a scaling factor determined by resistor ratios in the circuit.

---

## Condition for Zero Temperature Coefficient

For the reference voltage to be temperature-independent:

∂VREF / ∂T = 0

At room temperature:

∂VBE / ∂T ≈ −1.5 mV/K  
∂VT / ∂T ≈ +0.087 mV/K  

To cancel the temperature dependence:

α · ln(n) · 0.087 ≈ 1.5  
α ln(n) ≈ 17.2

This condition is achieved by choosing suitable resistor values and current ratios in the bandgap circuit.

---

## Resulting Bandgap Reference Voltage

When CTAT and PTAT components are properly combined, the reference voltage becomes approximately:

VREF ≈ 1.2 – 1.25 V

As temperature approaches absolute zero:

VREF → Eg / q

where Eg is the silicon bandgap energy. This behavior gives the circuit its name, the bandgap reference.

---

## Practical Bandgap Reference Circuit Operation

In a practical bandgap reference circuit:
- An operational amplifier forces two nodes to the same voltage
- The difference in VBE generates a PTAT current through a resistor
- This PTAT voltage is scaled and added to a CTAT voltage
- The output reference voltage is taken from the amplifier output

This structure ensures robustness against temperature, process, and supply variations.

---

## Key Observations

- VBE alone is not temperature-stable
- ΔVBE provides a reliable PTAT voltage
- Combining CTAT and PTAT voltages results in near-zero temperature coefficient
- Small reference errors can affect the entire IC

---

## Applications of Bandgap Reference

- Reference voltages for ADCs and DACs
- LDO voltage regulation
- Biasing circuits
- PLL and clock bias networks

---

#### Summary

A bandgap reference circuit generates a stable, temperature-independent voltage by combining a CTAT voltage (VBE) with a PTAT voltage (VT ln(n)). This reference is a fundamental building block in IC design and ensures reliable operation across process, voltage, and temperature variations.




## **MOS circuit analyses**
### Circuit 1 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/e0202da5639b745d4106bd9c803b1f6b613bbbc4/DAY-1/images/Screenshot%202026-01-28%20174011.png)

**Paramerters**

- input voltage Vin = 100mVp-p, Vdc = 0.6V, 1KHz 
- mosfet's w = 120nm (default) l = 45nm 
- Rd = 1Kohm 
- Supply VDD =1V 


**1) DC Analysis** 


![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/e0202da5639b745d4106bd9c803b1f6b613bbbc4/DAY-1/images/Screenshot%202026-01-28%20174057.png)

region of the operation is 2 - **saturation**, which is the necessary condition for the mosfet to work as the commmon sourse amplifier.

---


- In order to set the proper operation point Vdc and Rd and made as variables and parametric analysis is carried out using Vdc variation from 0 to 1V with 0.1 as a step size 
- meanwhile the Rd variable is choosen as the sweeping variable during the dc analysis and it is varied form 100 to 10000ohms 
- Hence the results are obtained by varing Rd wrt Output for the different values of Vdc 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/e0202da5639b745d4106bd9c803b1f6b613bbbc4/DAY-1/images/Screenshot%202026-01-28%20174147.png)


In order to obtain the maximum swing of the output, the values of Vdc and Rd are choosen in such a way that Vout will be equal to VDD/2.

- Therefore from the Result Rd is fixed as 5Kohms and Vdc=0.6V 

---

**2) Transient Analysis** 

After fixing the values of Vdc and Rd transient analysis is obtained by giving stoptime as 5ms 

![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/e0202da5639b745d4106bd9c803b1f6b613bbbc4/DAY-1/images/Screenshot%202026-01-28%20174201.png)

The output waveform is inverted as it is a CS amplifier and it is amplified with the desired gain 

---

**2) AC Analysis** 

For Vin the AC amplitude is given as 1V and now ac analysis is carried out wrt frequency varying from 0.1Hz to 10THz with 20 as a points per decade 


![circuit 1 ](https://github.com/shivaanii33/Mixed-signal-IC-design-/blob/e0202da5639b745d4106bd9c803b1f6b613bbbc4/DAY-1/images/Screenshot%202026-01-28%20174213.png)

The gain is found as 3.25 nearly 

As frequency increases, Vout starts decreasing sharply after a certain frequency.

This roll-off is due to:

- MOSFET parasitic capacitances (Cgs, Cgd)

- Load resistance (RD) forming RC poles

- The circuit exhibits low-pass behavior.

- Observation: The circuit has a limited bandwidth.
- The frequency at which Vout starts dropping significantly represents the cut-off frequency.

- Beyond this frequency, the amplifier cannot respond effectively to the input signal.

- Gain reduces rapidly at high frequencies.






