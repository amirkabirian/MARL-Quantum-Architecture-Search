# MARL-Quantum-Architecture-Search

<p align="left">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"/>
  <img src="https://img.shields.io/badge/python-3.10+-blue.svg" alt="Python 3.10+"/>
  <img src="https://img.shields.io/badge/Qiskit-1.0+-purple.svg" alt="Qiskit 1.0+"/>
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white" alt="PyTorch"/>
</p>

## Executive Summary & Scientific Motivation

In the Noisy Intermediate-Scale Quantum (NISQ) era, quantum hardware is severely constrained by short decoherence times ($T_1, T_2$) and high two-qubit gate error rates ($10^{-3}$ to $10^{-2}$). As quantum circuits grow in depth, accumulated gate noise rapidly diminishes execution fidelity, rendering computational outputs indistinguishable from random physical noise.

Standard quantum transpilers rely heavily on heuristic pass managers or evolutionary search algorithms. While effective for basic layouts, these traditional techniques fail to navigate the combinatorial explosion of non-local gate equivalences in large-scale Ansätze.

**MARL-Quantum-Architecture-Search (MARL-QAS)** addresses this core bottleneck by framing Quantum Architecture Search (QAS) and circuit transpilation as a Multi-Agent Reinforcement Learning problem. By training cooperative sub-agents in PyTorch over custom Gymnasium quantum environments, the framework autonomously discovers optimal gate compression paths, reducing CNOT counts and overall circuit depth while preserving strict process fidelity.

---

## Theoretical Framework & Mathematical Formulation

### 1. Quantum State & Unitary Process Fidelity
To guarantee that the optimized quantum circuit $\tilde{U}$ mathematically mirrors the target operator $U_{target}$, we evaluate process fidelity using the normalized Hilbert-Schmidt inner product:

$$F_{process}(U_{target}, \tilde{U}) = \frac{1}{d^2} \left\vert{} \text{Tr}\left( U_{target}^\dagger \tilde{U} \right) \right\vert{}^2$$

where $d = 2^N$ represents the Hilbert space dimension for an $N$-qubit system.

### 2. Multi-Agent Reward Function Design
The reinforcement learning reward structure is designed to enforce physical fidelity while penalizing excessive circuit depth ($D$):

$$R(s_t, a_t) = \left( F_{process} \right)^2 - \gamma \cdot D(\tilde{U}_t)$$

where $\gamma = 0.05$ is a depth-decay regularization factor preventing structural truncation without functional convergence.

---

## Historical Context & State-of-the-Art Position

1. **Rule-Based Transpilation (2015–2020):** Early compilers used deterministic term-rewriting rules, which lacked flexibility across varied hardware topologies.
2. **Single-Agent RL & Heuristics (2020–2023):** Deep Q-Networks (DQN) were applied to small circuits, but suffered from exponential action-space scaling as qubit count grew.
3. **MARL-QAS (Proposed Framework - 2026):** By decomposing the circuit into multi-qubit sub-domains, distributed Actor-Critic agents optimize local CNOT cancelling and global phase alignment in parallel.

---

## Key Features

- **Custom Quantum Gymnasium Environment:** Simulates quantum state unitaries, action spaces for gate operations (CNOT removal, single-qubit gate merging), and fidelity-based reward functions.
- **Multi-Agent Actor-Critic Architecture:** Distributed reinforcement learning sub-agents optimizing local and global gate parameters in parallel.
- **Fidelity-Aware Depth Reduction:** Balances unitary process fidelity ($F \approx 1.0$) with aggressive circuit depth compression to mitigate decoherence noise.
- **Reproducible Pipeline:** Modular Jupyter notebooks executable seamlessly within free Google Colab environments.

---

## Repository Structure

```text
MARL-Quantum-Architecture-Search/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── 01_quantum_circuit_environment.ipynb
│   ├── 02_marl_agent_training.ipynb
│   └── 03_qas_benchmark_demo.ipynb
└── assets/
    └── marl_qas_optimization.png
