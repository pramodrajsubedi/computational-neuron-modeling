# Leaky Integrate-and-Fire (LIF) Neuron Model

A minimal Python implementation of the Leaky Integrate-and-Fire (LIF) neuron model, simulating subthreshold membrane dynamics, spike generation, and frequency-current (f-I) characterisation.

---

## Overview

The LIF model approximates a neuron as an RC circuit. The membrane potential integrates input current, leaks toward rest, and fires a spike when it crosses a threshold — after which it resets. Despite its simplicity, it captures the essential spiking behaviour of real neurons.

---

## Model Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| `v_rest` | −65.0 mV | Resting membrane potential |
| `v_threshold` | −50.0 mV | Spike threshold |
| `v_reset` | −70.0 mV | Post-spike reset potential |
| `tau` | 10.0 ms | Membrane time constant |
| `R` | 10.0 MΩ | Membrane resistance |
| `dt` | 0.1 ms | Integration time step |
| `T` | 200.0 ms | Simulation duration |

---

## Governing Equation

The membrane potential evolves according to:

$$\tau \frac{dV}{dt} = -(V - V_{rest}) + R \cdot I_{ext}$$

When `V ≥ v_threshold`, a spike is recorded and `V` is immediately reset to `v_reset`.

---

## Simulations

### 1. Single Run — Constant Input Current
Runs the model at `I = 2.0 nA` for 200 ms. Prints total spike count and saves the membrane voltage trace to `membrane_voltage.png`.

**Output:**
```
Number of spikes at 2.0 nA : 12
```

### 2. f-I Curve
Sweeps input current from 0 to 5 nA across 50 linearly spaced values, computes the steady-state firing rate (Hz) for each, and saves the curve to `f_i_curve.png`.

**Sample output:**
```
Current: 0.00 nA, Firing Rate:   0.00 Hz
Current: 1.53 nA, Firing Rate:  20.00 Hz
Current: 2.04 nA, Firing Rate:  65.00 Hz
Current: 3.06 nA, Firing Rate: 120.00 Hz
Current: 4.59 nA, Firing Rate: 200.00 Hz
```

---

## Output Files

| File | Description |
|------|-------------|
| `membrane_voltage.png` | Voltage trace at I = 2.0 nA |
| `f_i_curve.png` | Firing rate vs. input current |

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

```bash
jupyter notebook code.ipynb
```

Run cells top-to-bottom. Parameters are defined in the second cell and propagate through all simulations.

---

## Reference

Lapicque, L. (1907). Recherches quantitatives sur l'excitation électrique des nerfs traitée comme une polarisation. *Journal de Physiologie et de Pathologie Générale*, 9, 620–635.
