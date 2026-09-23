# MARL-Quantum-Architecture-Search

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Qiskit 1.0+](https://img.shields.io/badge/Qiskit-1.0+-purple.svg)](https://qiskit.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?logo=pytorch&logoColor=white)](https://pytorch.org/)

## Overview
**MARL-Quantum-Architecture-Search** is a research-oriented framework designed for automated quantum circuit depth optimization and transpilation in Noisy Intermediate-Scale Quantum (NISQ) architectures. By leveraging Multi-Agent Reinforcement Learning (MARL) via PyTorch and custom Gymnasium environments integrated with Qiskit, the model dynamically searches for optimal gate combinations, reducing circuit depth while maintaining high process fidelity.

## Key Features
- **Custom Quantum Gymnasium Environment:** Simulates quantum state unitaries, action spaces for gate operations (CNOT removal, single-qubit gate merging), and fidelity-based reward functions.
- **Multi-Agent Actor-Critic Architecture:** Distributed reinforcement learning sub-agents optimizing local and global gate parameters in parallel.
- **Fidelity-Aware Depth Reduction:** Balances unitary process fidelity ($F \approx 1.0$) with aggressive circuit depth compression to mitigate decoherence noise.
- **Reproducible Pipeline:** Modular Jupyter notebooks executable seamlessly within free Google Colab environments.

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
