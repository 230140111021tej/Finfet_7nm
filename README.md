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
| Technology Node       | ≥45nm             | ≤22nm (industry standard)           |
| SCE Resistance        | Poor              | Excellent                           |

</details>

FinFETs are now ubiquitous in 7nm technology and below, powering most modern SoCs, CPUs, GPUs, and RFICs.

---

## Lab 1: FinFET Inverter Design

Design and characterization of a CMOS inverter using the ASAP 7nm FinFET process.

### Key Steps
- **Schematic Design:** Using Xschem/other EDA tool.
- **SPICE Simulation:** Extraction of VTC, delay, power consumption, noise margin, transconductance, and other key metrics.
- **W/L Ratio Variation:** Explore the effect of transistor sizing on performance.
- **Result Visualization:** Plots of input vs. output, VTC curve, gain, ID, delay, and power.

_Example Schematic, Waveforms & Results:_
## Inverter Characterization

#### Output Waveform
![OP waveform of inverter](./Images/OP%20waveform%20of%20inverter.png)

#### Drain Current
![Drain current](./Images/Drain%20current.png)

#### Voltage Transfer Characteristic (VTC)
![Vctat](./Images/Vctat.png)

#### Transconductance (gm)
![Transconductance](./Images/Transconductance.png)

#### Output Resistance
![Output Resistance](./Images/Output%20Resistance.png)

#### W/L Ratio Effect
![wl ratio](./Images/wl%20ratio.png)

#### ID-V Characteristics
![id](./Images/id.png)

## Bandgap Reference Results

#### Reference Voltage vs Temperature
![Vref](./Images/Vref.png)

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
- ![Bandgap_Xschem Schematic](.Images/Xschem%20schematic.png)


---

## Results

All simulation results, schematics, and plots are located in:

- [`/Images`](./Images) — Circuit diagrams and waveforms
- [`/results`](./results) — Measurement tables and plots
- [`/spice_code`](./spice_code) — SPICE simulation files

### Bandgap Reference Characterization Table

The following table summarizes the key performance parameters of the bandgap reference circuit across different supply voltages and temperatures, including the output reference voltage (Vref), line regulation, and startup times.

| S.No | VDD (V) | Temp (°C) | Vref (V) | Line Reg. (mV/V) | Startup Time (ns) |
|------|---------|-----------|----------|------------------|-------------------|
| 1    | 0.80    | 27        | 0.6760   | 845.0            | 3.48              |
| 2    | 0.90    | 27        | 0.7770   | 863.3            | 4.2               |
| 3    | 1.00    | 27        | 0.8779   | 877.9            | 4.5               |
| 4    | 1.00    | -40       | 0.8281   | 828.0            | 66.89             |
| 5    | 1.00    | 125       | 0.9220   | 922.0            | 1.03              |

### Final Inverter Characterization Table

This table presents key electrical characteristics of the inverter by sweeping the number of fins for PMOS (nfin_p) and NMOS (nfin_n) devices and measuring current (Id), power, delay (tpd), gain, noise margins (NML, NMH), transconductance (gm), and frequency of operation.

| Test # | nfin_p | nfin_n | Id (A)      | Power (W)  | tpd (ps) | Gain (Av) | NML (V) | NMH (V)  | gm (S)    | f (Hz)      |
|--------|--------|--------|-------------|------------|----------|-----------|---------|----------|-----------|-------------|
|   1    |   4    |   4    | -6.33E-05   | 8.50E-06   |   25.3   |   6.43    | 0.0444  | -0.0320  | 3.53E-04  | 2.25E+10    |
|   2    |   9    |   9    | -1.42E-04   | 1.91E-05   |   25.3   |   6.43    | 0.0444  | -0.0320  | 7.94E-04  | 2.25E+10    |
|   3    |  14    |  14    | -2.22E-04   | 2.97E-05   |   25.3   |   6.43    | 0.0444  | -0.0320  | 1.24E-03  | 2.25E+10    |
|   4    |  17    |  17    | -2.69E-04   | 3.61E-05   |   25.3   |   6.43    | 0.0444  | -0.0320  | 1.50E-03  | 2.25E+10    |
|   5    |   4    |   9    | -8.42E-05   | 1.23E-05   |   24.85  |   6.70    | 0.0265  | -0.0138  | 4.29E-04  | 2.27E+10    |
|   6    |   9    |  14    | -1.78E-04   | 2.37E-05   |   25.02  |   6.52    | 0.0346  | -0.0127  | 8.95E-04  | 2.26E+10    |
|   7    |  14    |  17    | -2.50E-04   | 3.28E-05   |   25.16  |   6.45    | 0.0404  | -0.0124  | 1.31E-03  | 2.25E+10    |
|   8    |  17    |   4    | -7.40E-05   | 1.52E-05   |   26.22  |   6.87    | 0.0611  | -0.0267  | 7.99E-04  | 2.16E+10    |
|   9    |   4    |  14    | -8.70E-05   | 1.45E-05   |   24.63  |   7.04    | 0.0175  | -0.0124  | 4.59E-04  | 2.28E+10    |
|  10    |   9    |  17    | -1.85E-04   | 2.58E-05   |   24.93  |   6.60    | 0.0307  | -0.0120  | 9.34E-04  | 2.27E+10    |
|  11    |  17    |   9    | -7.36E-05   | 1.42E-05   |   26.08  |   6.78    | 0.0613  | -0.0184  | 7.32E-04  | 2.16E+10    |
|  12    |  14    |   4    | -1.60E-04   | 2.53E-05   |   25.68  |   6.53    | 0.0556  | -0.0422  | 1.19E-03  | 2.20E+10    |

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
