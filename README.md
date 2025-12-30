# FinFET 7nm Circuit Design & Characterization

This repository documents the design, simulation, and analysis of advanced FinFET-based analog and digital circuits at 7nm, using the ASAP 7nm PDK, Xschem for schematic capture, and NGSPICE for circuit simulation.  
Work inspired by the VSDIAT workshop and repositories:

- [Bandgap Reference Circuit with SCMB](https://github.com/RSMadhuri66/Bandgap-Reference-Circuit-with-SCMB-with-ASAP-7nm-PDK-)
- [7nm FinFET Workshop VSDIAT](https://github.com/Shank012/7nm-FinFET-Workshop-VSDIAT)

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

A FinFET is a 3D transistor widely used in advanced CMOS nodes (≤22nm) for superior gate control, reduced leakage, and improved scaling.  
Unlike planar MOSFETs, the gate wraps around a vertical "fin" structure, drastically reducing short-channel effects.

![FinFET Diagram](./Images/finfet_diagram.png)

| Feature              | Planar MOSFET     | FinFET (3D MOSFET)         |
|----------------------|-------------------|----------------------------|
| Structure            | Flat channel      | Vertical fin-shaped channel|
| Gate Control         | Gate on 1 side    | Gate on 3 sides            |
| Leakage Current      | High <32nm        | Very low                   |
| Performance          | Limited scaling   | Higher speed, better Ion   |
| Power Consumption    | Higher            | Lower                      |

FinFETs are the backbone for 7nm nodes and below in modern SoCs, CPUs, GPUs, and analog ICs.

---

## Lab 1: FinFET Inverter Design

### Schematic & Setup

Design and simulate a CMOS inverter using ASAP 7nm FinFET models.  
Schematic created in Xschem:

![Inverter Schematic](./Images/inverter_schematic.png)

### Inverter Analysis

- **Input & Output Waveform:** SPICE simulation of signal transmission and logic levels.
- **Voltage Transfer Characteristic (VTC):** Measurement of switching thresholds, gain, noise margin.
- **W/L Ratio Variation:** Evaluation of electrical characteristics for different transistor size ratios.

#### Example Waveforms

![Inverter Waveform](./Images/inverter_waveform.png)
![VTC Curve](./Images/vtc_curve.png)

### Measurement Table

| Parameter      | Value      |
|----------------|-----------|
| Vth            | 0.32 V    |
| Max Gain       | 4.5       |
| Noise Margin   | 0.12 V    |
| Power          | 0.62 mW   |
| Frequency      | 10 MHz    |

#### W/L Ratio Study

![W/L Results](./Images/wl_study.png)

---

## Lab 2: Bandgap Reference Circuit Design

### Overview

The Bandgap Reference generates a temperature-independent voltage, essential for analog/reference applications.  
Uses a Self-Biased Current Mirror (SBCM) approach for improved reliability.

#### Schematic

![Bandgap Reference Schematic](./Images/bandgap_sch.png)

### Simulation Results

- **Vref vs. Temperature Sweep:**
  
  ![Vref vs. Temperature](./Images/vref_vs_temp.png)

- **Line Regulation Analysis:**
  
  ![Line Regulation](./Images/line_regulation.png)

- **Transient/Startup Time:**
  
  ![Startup Time](./Images/startup_time.png)

#### Measurement Table

| Temperature (°C) | Vref (V) |
|------------------|----------|
| -45              | 1.61     |
| 0                | 1.60     |
| 25               | 1.60     |
| 85               | 1.62     |
| 125              | 1.62     |

---

## Results

All simulation results, measurement tables, and images are available in:

- [`/Images`](./Images) — schematics and waveforms
- [`/results`](./results) — measurement data and analysis
- [`/spice_code`](./spice_code) — simulation files

---

## Acknowledgements

Special thanks to:

- [Kunal Ghosh](https://github.com/kunalg123) (VSD Co-Founder)
- [Soundarya Madhuri Royyuru](https://github.com/RSMadhuri66/Bandgap-Reference-Circuit-with-SCMB-with-ASAP-7nm-PDK-)
- VSDIAT instructors and assistants

---

## References

- [Bandgap Reference Circuit with SCMB](https://github.com/RSMadhuri66/Bandgap-Reference-Circuit-with-SCMB-with-ASAP-7nm-PDK-)
- [7nm FinFET Workshop VSDIAT](https://github.com/Shank012/7nm-FinFET-Workshop-VSDIAT)
- [ASAP 7nm PDK Xschem Repo](https://github.com/AsahiroKenpachi/asap_7nm_Xschem)
- IIT Labs: [FinFET Theory](https://vlsi-iitg.vlabs.ac.in/CMOS_theory.html)
- [NGSPICE Manual](https://ngspice.sourceforge.io/docs/ngspice-manual.pdf)

---

_If you use this repository, please star/fork and mention in your projects!_
