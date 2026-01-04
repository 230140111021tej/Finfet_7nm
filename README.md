# FinFET 7nm Circuit Design & Characterization

![FinFET Device Structure](./Images/finfet.png)

This repository presents my work on designing, simulating, and characterizing FinFET-based analog and digital circuits at the advanced 7nm technology node. The project is completed as part of the VSD 7nm FinFET Workshop, utilizing the ASAP 7nm PDK and tools for schematic entry, simulation, and analysis.

---

## Table of Contents

- [Introduction](#introduction)
- [Characterization of CMOS VTC](#characterization-of-cmos-vtc)
- [CMOS Inverter_vtc Characteristics](#cmos-inverter_vtc-characteristics)
- [Design of BandGap Reference Circuit with Xschem](#design-of-bandgap-reference-circuit-with-xschem)
- [Results](#results)
- [Acknowledgements](#acknowledgements)
- [References](#references)

---

## Introduction

### What is FinFET?

A FinFET (Fin Field-Effect Transistor) is a type of non-planar, multi-gate transistor, widely adopted for sub-22nm CMOS technology due to its superior control over short-channel effects, reduced leakage, and enhanced performance. FinFET replaces the planar "MOSFET" channel with a thin, vertical fin, allowing the gate to wrap around the channel on three sides, resulting in improved electrostatic control and better device characteristics.

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

FinFETs are now ubiquitous in 7nm technology and below, powering most modern SoCs, CPUs, GPUs, and RFICs.

---

## Characterization of CMOS VTC

### NFET Schematic

*NMOS device schematic created in Xschem for Id/Vd simulations:*

![NFET Schematic](./Images/nfetsch.png)

---

### NFET Id-Vd Characteristics

*Simulation setup and extracted transfer characteristics for NMOS:*

![NFET Id vs Vd Simulation Setup](./Images/nfet_id_vs_vd_characteristics.png)
![Id vs Vd Plot](./Images/id_vs_vd.png)

---

## CMOS Inverter_vtc Characteristics

### Output Waveform (Inverter)

*Transient simulation showing inverter's output switching behavior:*

![Output Waveform of Inverter](./Images/OP%20waveform%20of%20inverter.png)

---

### Drain Current

*Shows inverter drain current characteristics during switching:*

![Drain Current](./Images/Drain%20current.png)

---

### Output Resistance

*Calculated inverter output resistance:*

![Output Resistance](./Images/Output%20Resistance.png)

---

### Transconductance

*Inverter transconductance result (gm versus input):*

![Transconductance](./Images/Transconductance.png)

---

### Inverter Schematic

*CMOS inverter schematic captured in Xschem:*

![Inverter Schematic](./Images/invertersch.png)

---

### Switching Threshold Voltage

*Waveform used to determine the inverter’s V_th and noise margins:*

![Switching Threshold Voltage](./Images/switching_threshold_voltage.png)

---

## Design of BandGap Reference Circuit with Xschem

### BandGap Reference (Architecture Reference)

*Reference block diagram for bandgap circuit using SBCM:*

![Bandgap Reference Block](./Images/reference.png)

---

### Xschem Bandgap Schematic

*Bandgap reference full schematic as drawn in Xschem:*

![Bandgap Xschem Schematic](./Images/Xschem%20schematic.png)

---

### Vref vs Temperature

*Simulation showing reference voltage stability across temperature sweep:*

![Vref vs Temperature](./Images/Vref.png)

---

### PTAT/CTAT Voltages

*Simulated PTAT/CTAT voltage behavior in the bandgap circuit:*

![Vctat](./Images/Vctat.png)

---

## Results

All simulation results, schematics, and plots are located in:

- [`/Images`](./Images) — Circuit diagrams and waveforms
- [`/results`](./results) — Measurement tables and plots
- [`/spice_code`](./spice_code) — SPICE simulation files

### Bandgap Reference Characterization Table

| S.No | VDD (V) | Temp (°C) | Vref (V) | Line Reg. (mV/V) | Startup Time (ns) |
|------|---------|-----------|----------|------------------|-------------------|
| 1    | 0.80    | 27        | 0.6760   | 845.0            | 3.48              |
| 2    | 0.90    | 27        | 0.7770   | 863.3            | 4.2               |
| 3    | 1.00    | 27        | 0.8779   | 877.9            | 4.5               |
| 4    | 1.00    | -40       | 0.8281   | 828.0            | 66.89             |
| 5    | 1.00    | 125       | 0.9220   | 922.0            | 1.03              |

### Final Inverter Characterization Table

| Test # | nfin_p | nfin_n | Id (A)      | Power (W)  | tpd (ps) | Gain (Av) | NML (V) | NMH (V)  | gm (S)    | f (Hz)      |
|--------|--------|--------|-------------|------------|----------|-----------|---------|----------|-----------|-------------|
|   1    |   4    |   4    | -6.33E-05   | 8.50E-06   |   25.3   |   6.43    | 0.0444  | -0.0320  | 3.53E-04  | 2.25E+10    |
|   2    |   9    |   9    | -1.42E-04   | 1.91E-05   |   25.3   |   6.43    | 0.0444  | -0.0320  | 7.94E-04  | 2.25E+10    |
|   3    |  14    |  14    | -2.22E-04   | 2.97E-05   |   25.3   |   6.43    | 0.0444  | -0.0320  | 1.24E-03  | 2.25E+10    |
|  ...   |  ...   |  ...   | ...         | ...        | ...      | ...       | ...     | ...      | ...       | ...         |

---

## Acknowledgements

Special thanks to:

- [Kunal Ghosh](https://github.com/kunalg123) (VSD Co-Founder)
- [Soundarya Madhuri Royyuru](https://github.com/RSMadhuri66/Bandgap-Reference-Circuit-with-SCMB-with-ASAP-7nm-PDK-)
- Instructors & community mentors from VSDIAT.

---

## References

- [Bandgap Circuit VSDIAT](https://github.com/vsdip/vsdopen2021_bgr/tree/main)
- [ASAP 7nm Xschem Reference](https://github.com/AsahiroKenpachi/asap_7nm_Xschem)
- [FinFET Theory - IIT Labs](https://vlsi-iitg.vlabs.ac.in/CMOS_theory.html)
- [NGSPICE Tutorial](https://ngspice.sourceforge.io/docs/ngspice-manual.pdf)
- Further reading in design and characterization papers linked in reference repos.

---

_If you use this repository, please star/fork and acknowledge accordingly!_
