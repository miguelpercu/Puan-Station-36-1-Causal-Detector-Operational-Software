# Puan Station 36+1 Causal Detector – Operational Software Package

**Author:** Miguel Ángel Percudani  
**ORCID:** [0009-0007-1748-3212](https://orcid.org/0009-0007-1748-3212)  
**Version:** 1.1  
**Date:** April 2026  
**DOI:** [10.5281/zenodo.19704792](https://doi.org/10.5281/zenodo.19704792)

## Overview

This package contains the complete software suite, construction manual, and precision technical notes for the **Puan Station 36+1 Coil Rotational Detector**. The detector is a tabletop instrument designed to measure scalar torsion fields as predicted by the **Universal Applicable Time (UAT)** and **Unified Principle of Causality (UPC)** frameworks.

The system consists of 36 peripheral coils arranged in a ring (nominal $10^\circ$ angular step) and one central observer coil. A $7\%$ table rotation asymmetry and a logarithmic torsion parameter $\tau = 0.3697$ are applied electronically. The central coil is amplified with a fixed gain of $1.9694$, and the expected saturation RMS is $0.7071$ ($1/\sqrt{2}$).

The software dynamically calculates the correct operating frequency for the current date using the UAT Inflationary Drift $\alpha = 0.046$ Hz/day (reference epoch: May 27, 2023, $f_0 = 84.4$ Hz). This ensures that the experiment remains replicable at any future date.

## Package Contents

| File / Folder | Description |
| :--- | :--- |
| `puan_36ch_generator.py` | **Operational script.** Generates the 36 synchronized sinusoidal signals for the peripheral coils. Auto‑calibrates the frequency for the current date. |
| `puan_rms_monitor.py` | **Operational script.** Captures the central coil signal and displays the live RMS value. |
| `Puan_Station_Manual_EN.pdf` | Complete construction and calibration manual (English). Includes coil specs, mechanical layout, wiring diagrams, and step‑by‑step instructions. |
| `Technical_Note_INA128_EN.pdf` | Precision technical note on grounding, shielding, and INA128 instrumentation amplifier implementation. Critical for achieving noise‑free measurements. |
| `simulation/` | Folder containing a **digital twin simulation** for conceptual validation. **Not for hardware operation.** |
| `simulation/puan_combined_demo.py` | Self‑contained simulation of the 36+1 detector logic. Verifies that the phase equations produce the expected RMS (~0.7050). |
| `simulation/README_SIMULATION.txt` | Explanation of the simulation script. |

## Requirements

- Python 3.7 or later
- NumPy
- SoundDevice (`pip install sounddevice`)

For hardware operation, the following additional components are required (see the manual for details):
- 5 × 8‑channel audio interfaces with Word Clock (e.g., Behringer UMC1820)
- INA128 instrumentation amplifier with precision 51 kΩ gain resistor
- 36 identical air‑core coils (100 turns, 10 cm diameter) + 1 central coil
- Battery power supply (±12 V, ±5 V) for low‑noise operation

## Quick Start (Simulation)

To verify the mathematical correctness of the phase equations without any hardware, run the simulation script:

```bash
cd simulation
python puan_combined_demo.py