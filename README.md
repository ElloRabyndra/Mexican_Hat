# Mexican Hat — Competitive Network Activation Pattern

A Python implementation of the Mexican Hat (Lateral Inhibition) algorithm for competitive neural networks. Simulates how activation patterns evolve across neurons over multiple iterations using excitatory and inhibitory neighborhood weights.

## Overview
The Mexican Hat algorithm models lateral inhibition in competitive networks: neurons close to the winning unit are excited, while those further away are inhibited. Over iterations, this sharpens the activation pattern into a clear peak.

## Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| R1 | 1 | Radius of positive (excitatory) weights |
| R2 | 3 | Radius of negative (inhibitory) weights |
| c1 | 0.6 | Positive weight value for neighbors within R1 |
| c2 | −0.4 | Negative weight value for neighbors within R2 |
| n | 7 | Number of neurons (x₁ to x₇) |

**Initial input vector:** `x = (0.0, 0.5, 0.8, 1.0, 0.8, 0.5, 0.0)`

## How It Works
1. **Weight assignment** — for each neuron pair `(i, j)`, the connection weight is determined by their distance `d = |i − j|`:
   - `d ≤ R1` → weight = `c1` (excitatory)
   - `R1 < d ≤ R2` → weight = `c2` (inhibitory)
   - `d > R2` → weight = `0` (no connection)
2. **Net input calculation** — each neuron computes a weighted sum of all other neurons' current activations.
3. **Activation function** — output is clipped to `[0, x_max]`, where `x_max` is the maximum raw net input of that iteration.
4. **Iteration** — steps 2–3 repeat for each time step (`t=1`, `t=2`).

## Contents
```text
mexican_hat_chart.ipynb   # Main notebook
mexican_hat_plot.png      
```

## Usage
Open and run `mexican_hat_chart.ipynb` in Jupyter. The notebook contains two cells:
- **Cell 1** — defines parameters, weight function, iteration logic, and prints activation values at each time step
- **Cell 2** — plots the activation pattern for t=0, t=1, and t=2, and saves the chart as `mexican_hat_plot.png`

## Requirements
```text
numpy
matplotlib
```

Install with:
```bash
pip install numpy matplotlib
```

## Output
The notebook produces a line chart showing how the activation pattern sharpens over iterations, with the central neuron (x₄) converging to the dominant peak.

| Time | Peak Value |
|------|------------|
| t=0  | 1.0000 |
| t=1  | 1.1600 |
| t=2  | 1.6800 |
