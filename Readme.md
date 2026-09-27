# Computational Neuron Modeling

A computational study of neuronal dynamics using progressively more detailed mathematical models, implemented in Python.

This repository contains two main neuron models: a **Leaky Integrate-and-Fire (LIF)** model for introducing basic neuronal dynamics and a **Hodgkin–Huxley (HH)** model for mechanistic simulation of membrane excitability and action-potential generation.

## Repository Structure

```text
computational-neuron-modeling/
│
├── lif-model/
│   └── Basic leaky integrate-and-fire neuron model
│
├── hodgkin-huxley/
│   └── Hodgkin–Huxley neuron simulations and analysis
│
└── README.md
```

## 1. Leaky Integrate-and-Fire Model

The `lif-model` folder contains a simplified mathematical representation of a neuron based on the leaky integrate-and-fire model.

The model:

* Represents the membrane potential using a leaky integration equation
* Applies external input current
* Generates a spike when the membrane potential reaches a threshold
* Resets the membrane potential after a spike
* Calculates spike times and firing rates
* Demonstrates the firing-rate versus input-current (**f–I**) relationship
* Can be extended to time-varying or noisy input currents

The LIF model provides a simple starting point for understanding how changes in input current affect neuronal firing.

## 2. Hodgkin–Huxley Model

The `hodgkin-huxley` folder contains a mechanistic model of neuronal excitability based on the Hodgkin–Huxley formalism.

The model describes the membrane potential using sodium, potassium, and leak currents:

$$
C_m\frac{dV}{dt}
=
I_{\mathrm{ext}}
-
I_{\mathrm{Na}}
-
I_{\mathrm{K}}
-
I_{\mathrm{L}}
$$

The sodium and potassium currents are controlled by voltage-dependent gating variables:

* \(m\) — sodium activation
* \(h\) — sodium inactivation
* \(n\) — potassium activation

The HH simulations include:

* Constant external current stimulation
* Step-shaped input currents
* Temporally correlated noisy input using an Ornstein–Uhlenbeck process
* Membrane-potential dynamics
* Sodium and potassium gating dynamics
* Action-potential detection
* Spike-count and firing-rate analysis
* Inter-spike interval (ISI) analysis
* Firing-rate versus input-current (**f–I**) analysis

## Current Analysis

The project is being developed toward a quantitative investigation of how fluctuations in external input influence neuronal firing.

The planned analysis examines how increasing noise intensity affects:

* Firing rate
* Mean inter-spike interval
* Inter-spike interval variability
* Coefficient of variation (CV) of the ISI

Repeated simulations with different noise realizations can be used to characterize the statistical response of the HH neuron to stochastic input.

## Technologies

* **Python**
* **NumPy** — numerical computation
* **Matplotlib** — visualization
* **Hodgkin–Huxley equations** — mechanistic neuronal modeling
* **Leaky Integrate-and-Fire model** — simplified neuronal modeling

## Purpose

The purpose of this repository is to explore computational models of neuronal dynamics, progressing from a simple integrate-and-fire description to a biophysically motivated Hodgkin–Huxley model.

The project focuses on understanding how mathematical descriptions of membrane dynamics translate external inputs into observable neuronal behavior such as action potentials, firing rates, and spike-timing variability.

