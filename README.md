# FinFET 7nm Circuit Design & Characterization

This repository presents my work on designing, simulating, and characterizing FinFET-based analog and digital circuits at the advanced 7nm technology node. The project is completed as part of the VSD 7nm FinFET Workshop, utilizing the ASAP 7nm PDK and tools for schematic entry, simulation, and analysis.

---

## Table of Contents

- [Introduction](#introduction)
- [Lab 1: FinFET Inverter Design](#lab-1-finfet-inverter-design)
- [Lab 2: Bandgap Reference Circuit Design](#lab-2-bandgap-reference-circuit-design)
- [Results](#results)
- [Acknowledgements](#acknowledgements)
- [References](#references)

---

## Introduction

<details>
  <summary>Comparison Table</summary>

| **Feature**           | **Planar MOSFET** | **FinFET (3D MOSFET)**        |
|-----------------------|-------------------|-------------------------------|
| Structure             | Flat channel      | Vertical fin-shaped channel   |
| Gate Control          | Gate on 1 side    | Gate on 3 sides               |
| Leakage Current       | High at <32nm     | Very low                      |
| Performance           | Limited scaling   | Higher speed, better Ion      |
| Power Consumption     | Higher            | Lower                         |
| Technology Node       | ≥45nm             | ≤22nm                         |
| SCE Resistance        | Poor              | Excellent                     |

</details>

FinFETs are now standard in 7nm technology and below, powering modern SoCs and analog circuits.

---

## Lab 1: FinFET Inverter Characterization

### Schematic of CMOS Inverter

*This schematic was created using Xschem and simulates the inverter using ASAP 7nm PDK:*

![OP waveform of inverter](./Images/OP%20waveform%20of%20inverter.png)

---

### Id-Vd Characteristics (NMOS)

*This plot represents the drain current (Id) as a function of drain voltage (Vd) for the NMOS device. The current is calculated using NGSPICE (`let id=v2#branch`):*

![id](./Images/id.png)

---

### Drain Current - Transfer Characteristics

*Shows the variation of drain current with gate voltage, a key metric for transistor operation:*

![Drain current](./Images/Drain%20current.png)

---

### Voltage Transfer Characteristic (VTC) & Switching Threshold

*The VTC curve plots input vs output voltage. Used to calculate Vth, noise margins, and to assess inverter performance.*

![Vctat](./Images/Vctat.png)

---

### Transconductance (gm)

*Evaluates the derivative of current with respect to input voltage (`let gm = real(deriv(id, nfet_in))`):*

![Transconductance](./Images/Transconductance.png)

---

### Output Resistance

*Shows output resistance, calculated as the derivative of output voltage to drain current:*

![Output Resistance](./Images/Output%20Resistance.png)

---

### W/L Ratio Sweep

*Analysis sweep of W/L ratio (here nfin count for PMOS and NMOS) and its effect on inverter speed, current, and noise margin:*

![wl ratio](./Images/wl%20ratio.png)

---

## Lab 2: Bandgap Reference Results

### Reference Voltage vs Temperature

*This plot shows how the bandgap reference voltage (Vref) behaves versus temperature, indicating temperature independence.*

![Vref](./Images/Vref.png)

---

### Results Tables

#### Bandgap Reference Characterization Table

| S.No | VDD (V) | Temp (°C) | Vref (V) | Line Reg. (mV/V) | Startup Time (ns) |
|------|---------|-----------|----------|------------------|-------------------|
| 1    | 0.80    | 27        | 0.6760   | 845.0            | 3.48              |
| 2    | 0.90    | 27        | 0.7770   | 863.3            | 4.2               |
| 3    | 1.00    | 27        | 0.8779   | 877.9            | 4.5               |
| 4    | 1.00    | -40       | 0.8281   | 828.0            | 66.89             |
| 5    | 1.00    | 125       | 0.9220   | 922.0            | 1.03              |

#### Final Inverter Characterization Table

| Test # | nfin_p | nfin_n | Id (A)      | Power (W)  | tpd (ps) | Gain (Av) | NML (V) | NMH (V)  | gm (S)    | f (Hz)      |
|--------|--------|--------|-------------|------------|----------|-----------|---------|----------|-----------|-------------|
|   1    |   4    |   4    | -6.33E-05   | 8.50E-06   |   25.3   |   6.43    | 0.0444  | -0.0320  | 3.53E-04  | 2.25E+10    |
|   ...  |  ...   |  ...   | ...         | ...        | ...      | ...       | ...     | ...      | ...       | ...         |

---

## Acknowledgements

Special thanks to:

- [Kunal Ghosh](https://github.com/kunalg123) (VSD Co-Founder)
- [Soundarya Madhuri Royyuru](https://github.com/RSMadhuri66/Bandgap-Reference-Circuit-with-SCMB-with-ASAP-7nm-PDK-)
- VSDIAT instructors & community

---

## References

- [Bandgap Reference Github](https://github.com/johnkustin/bandgapReferenceCircuit)
- [vsdopen2021_bgr](https://github.com/vsdip/vsdopen2021_bgr/tree/main)
- [ASAP 7nm Xschem Repo](https://github.com/AsahiroKenpachi/asap_7nm_Xschem)
- [FinFET Theory - IIT Labs](https://vlsi-iitg.vlabs.ac.in/CMOS_theory.html)
- [NGSPICE Manual](https://ngspice.sourceforge.io/docs/ngspice-manual.pdf)

---

_If you use this repository, please star/fork and acknowledge accordingly!_
