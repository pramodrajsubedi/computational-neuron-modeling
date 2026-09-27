# Hodgkin-Huxley Neuron Model Simulation

A from-scratch implementation of the classic Hodgkin-Huxley (HH) conductance-based neuron model in Python, simulating action potential generation under various input current regimes.

---

## Overview

The Hodgkin-Huxley model describes how ionic currents through voltage-gated channels generate action potentials in a neuron's membrane. This notebook builds the model progressively, starting from the basic equations and adding increasingly realistic input stimuli.

---

## Model Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| `C_m` | 1.0 µF/cm² | Membrane capacitance |
| `g_Na` | 120.0 mS/cm² | Max sodium conductance |
| `g_K` | 36.0 mS/cm² | Max potassium conductance |
| `g_L` | 0.3 mS/cm² | Leak conductance |
| `E_Na` | +50.0 mV | Sodium reversal potential |
| `E_K` | −77.0 mV | Potassium reversal potential |
| `E_L` | −54.387 mV | Leak reversal potential |
| `dt` | 0.01 ms | Integration time step |
| `T` | 100.0 ms | Simulation duration |
| `V₀` | −65.0 mV | Initial membrane potential |

---

## Simulations

### 1. Basic Model — Constant Current
Applies a constant external current (`I_ext = 10 µA/cm²`) across the full simulation window. Demonstrates the fundamental action potential waveform.

### 2. Step Current Input
Applies a square-wave stimulus (10 µA/cm² from t = 10 ms to t = 80 ms). Shows spike initiation at stimulus onset and cessation at offset.

### 3. Noisy Step Input
Adds independent Gaussian noise (`σ = 1.0 µA/cm²`) to the step stimulus. Models stochastic synaptic input and illustrates variability in spike timing.

### 4. Temporally Correlated (Ornstein-Uhlenbeck) Input
Replaces white noise with an Ornstein-Uhlenbeck (OU) process (`τ_noise = 5 ms`), producing smoothly correlated fluctuations — a more physiologically realistic noise model.

### 5. Gating Variable Visualization
Plots all four state variables simultaneously (`V`, `m`, `h`, `n`) against time, revealing the dynamics of sodium activation/inactivation and potassium activation that underlie each spike.

### 6. Spike Detection & ISI Analysis
Detects action potentials via a 0 mV threshold crossing, then computes:
- Spike count and spike times
- Firing rate (Hz)
- Inter-spike intervals (ISI) and mean ISI

### 7. f-I Curve
Sweeps constant input currents from 0 to 20 µA/cm² in 1 µA/cm² steps and plots firing rate vs. input current — the canonical frequency-current (f-I) characterisation of a neuron.

---

## Requirements

```
numpy
matplotlib
```

Install with:

```bash
pip install numpy matplotlib
```

---

## Usage

Open and run `code.ipynb` in Jupyter:

```bash
jupyter notebook code.ipynb
```

All sections are self-contained and run top-to-bottom. The HH parameters and time array are defined once at the top and reused across all simulations.

---

## Equations

The model integrates the following ODEs using forward Euler at `dt = 0.01 ms`:

**Membrane potential:**
$$C_m \frac{dV}{dt} = I_{ext} - I_{Na} - I_K - I_L$$

**Ionic currents:**
$$I_{Na} = g_{Na} \cdot m^3 h (V - E_{Na})$$
$$I_K = g_K \cdot n^4 (V - E_K)$$
$$I_L = g_L (V - E_L)$$

**Gating variables** follow first-order kinetics:
$$\frac{dx}{dt} = \alpha_x(V)(1 - x) - \beta_x(V) \cdot x \quad \text{for } x \in \{m, h, n\}$$

---

## Reference

Hodgkin, A. L., & Huxley, A. F. (1952). A quantitative description of membrane current and its application to conduction and excitation in nerve. *Journal of Physiology*, 117(4), 500–544.
