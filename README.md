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

### What is FinFET?

A FinFET (Fin Field-Effect Transistor) is a type of non-planar, multi-gate transistor, widely adopted for sub-22nm CMOS technology due to its superior control over short-channel effects, reduced leakage, and enhanced performance. FinFET replaces the planar "MOSFET" channel with a thin, vertical fin, allowing the gate to wrap around the channel on three sides, resulting in improved electrostatic control and better device characteristics.

<details>
  <summary>Comparison Table</summary>

| **Feature**           | **Planar MOSFET** | **FinFET** (3D MOSFET)             |
|-----------------------|-------------------|-------------------------------------|
| Structure             | Flat channel      | Vertical fin-shaped channel         |
| Gate Control          | Gate on 1 side    | Gate on 3 sides                     |
| Leakage Current       | High at <32nm     | Very low                            |
| Performance           | Limited scaling   | Higher speed, better Ion            |
| Power Consumption     | Higher            | Lower                               |
| Technology Node       | ≥45nm              | ≤22nm (industry standard)           |
| SCE Resistance        | Poor              | Excellent                           |

</details>

FinFETs are now ubiquitous in 7nm technology and below, powering most modern SoCs, CPUs, GPUs, and RFICs.

---

## Lab 1: FinFET Inverter Design

Design and characterization of a CMOS inverter using ASAP 7nm FinFET process.

### Key Steps
- **Schematic Design:** Using Xschem/other EDA tool.
- **SPICE Simulation:** Extraction of VTC, delay, power consumption, noise margin, transconductance, and other key metrics.
- **W/L Ratio Variation:** Explore the effect of transistor sizing on performance.
- **Result Visualization:** Plots of input vs. output, VTC curve, gain, ID, delay, and power.

_Example Schematic, Waveforms & Results:_
- [Add your inverter schematic here]
- [Add plots for VTC, gain, ID, etc.]

---

## Lab 2: Bandgap Reference Circuit Design

Designing a temperature-independent bandgap reference voltage circuit utilizing self-biased current mirror (SBCM) architecture with ASAP 7nm PDK.

### Overview

A bandgap reference circuit provides a highly stable voltage source, insensitive to supply voltage, temperature, and process variations. Integration of a Self-Biased Current Mirror (SBCM) enhances startup reliability, power efficiency, and process robustness.

#### Key Steps
- **Circuit Schematic:** Implement PTAT and CTAT branches.
- **Biasing:** Generation of stable reference current and voltage.
- **Simulation:** DC and temperature sweeps to ensure performance from -45°C to 125°C.
- **Results:** Vref stability, line regulation, transient response, startup time.

_Example Schematic & Plots:_
- [Add your bandgap schematic here]
- [Add Vref vs. temperature plot]
- [Add startup/line regulation plots]

---

## Results

All simulation results, schematics, and plots are located in:

- [`/Images`](./Images) — Circuit diagrams and waveforms
- [`/results`](./results) — Measurement tables and plots
- [`/spice_code`](./spice_code) — SPICE simulation files

Update with specific data, measurement tables, and images as you progress.

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
