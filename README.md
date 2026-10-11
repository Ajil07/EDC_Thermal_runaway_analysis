# Comparative Analysis of Thermal Runaway in BJT Circuits: Fixed Bias vs. Voltage Divider Bias

A SPICE-based investigation into BJT thermal instability, demonstrating how emitter negative feedback prevents thermal runaway during severe temperature shifts.

---

## 📌 Project Overview
Bipolar Junction Transistors (BJTs) are vulnerable to thermal runaway due to temperature-dependent parameters:
- Base-emitter voltage drop: $\frac{dV_{BE}}{dT} \approx -2.0\,\text{mV/}^\circ\text{C}$
- Reverse saturation leakage current: $I_{CBO}$ approximately doubles every $10^\circ\text{C}$
- Forward current gain: $\beta$ increases with temperature

This project compares two biasing networks across a wide temperature sweep ($25^\circ\text{C}$ to $150^\circ\text{C}$) to observe Q-point migration and saturation onset.

---

## ⚡ Circuit Topologies & Specifications

| Parameter | Fixed Bias (`Q_FIXED`) | Voltage Divider Bias (`Q_VDB`) |
| :--- | :--- | :--- |
| **Transistor Model** | 2N2222 NPN | 2N2222 NPN |
| **Supply Voltage ($V_{CC}$)** | $12\,\text{V}$ | $12\,\text{V}$ |
| **Collector Resistor ($R_C$)** | $1\,\text{k}\Omega$ | $1\,\text{k}\Omega$ |
| **Bias Resistors** | $R_B = 220\,\text{k}\Omega$ | $R_1 = 22\,\text{k}\Omega,\; R_2 = 10\,\text{k}\Omega$ |
| **Emitter Resistor ($R_E$)** | None ($0\,\Omega$) | $470\,\Omega$ |
| **Feedback Mechanism** | None (Open-loop) | Negative feedback via $R_E$ |

---

## 📊 Key Findings

| Metric | Fixed Bias (`Rc1`) | Voltage Divider Bias (`Rc2`) | Verdict |
| :--- | :--- | :--- | :--- |
| **Stability Factor ($S$)** | $\approx 201$ | $\approx 14.5$ | VDB is $\approx 13.8\times$ more stable |
| **Current at $25^\circ\text{C}$** | $\approx 10.0\,\text{mA}$ | $\approx 6.0\,\text{mA}$ | Both operate in linear active mode |
| **Current at $150^\circ\text{C}$** | $\approx 11.8\,\text{mA}$ (Saturated) | $\approx 6.6\,\text{mA}$ (Active) | VDB preserves amplification |
| **Total Drift ($\Delta I_C$)** | $+1.8\,\text{mA}$ ($+18\%$) | $+0.6\,\text{mA}$ ($+10\%$) | VDB tightly clamps drift |
| **Saturation Onset** | $\approx 65^\circ\text{C}$ | None ($V_{CE} \ge 2.29\,\text{V}$) | Fixed bias fails above $65^\circ\text{C}$ |

---

## 🛠️ Simulation Setup
- **Software**: LTspice (v26.1 or later)
- **SPICE Directive**:
  ```spice
  .dc temp 25 150 1


Sweeps ambient junction temperature from $25^\circ\text{C}$ to $150^\circ\text{C}$ in $1^\circ\text{C}$ increments (126 total operating points).


👥 Authors:
Ajil Reji (Roll No: 6)
Geojin Mathew (Roll No: 31)
Jeril Liju Philip (Roll No: 38)
Joshua Joseph Varghese (Roll No: 41)
Meeval Varghese (Roll No: 47)