# Multi-Agent Reinforcement Learning: Pacman Capture the Flag

This repository contains the implementation and analysis of advanced Multi-Agent Reinforcement Learning (MARL) algorithms applied to the Pacman Capture the Flag environment. The project evolves from basic Independent Q-Learning (IQL) to centralized training architectures, exploring the synergy between value decomposition and coordinated exploration.

## Core Architectures
- **QMix & QPLEX**: Transitioned from standard QMix to **QPLEX (Duplex Dueling)** to bypass monotonicity constraints and enable more complex cooperative strategies (e.g., sacrificial plays).
- **Agent Architecture**: Integration of **Dueling DQN** and **N-Step Returns** to accelerate credit assignment in sparse-reward scenarios.

## Key Innovations
- **Coordinated Exploration**: Implementation of **Count-Based Exploration (CBE)** using a custom domain-specific state abstraction (Position + Ally Context + Food Map sectors) to overcome the limits of $\epsilon$-greedy in large state spaces.
- **Reward Engineering**: Integration of **Potential-Based Reward Shaping (PBRS)** and **Action Masking** to guide agents through complex navigation and home-delivery cycles.
- **Component Interference Analysis**: A rigorous study on the "Fully Loaded" configuration, documenting how destructive interference between PBRS, PER, and Time Penalties can lead to performance regression.

## Performance: The "Apotheosis" Configuration
The research culminated in a finely-tuned configuration consisting of:
- **Architecture**: QPLEX with Input Normalization.
- **Exploration**: Advanced CBE ($\beta=0.1$).
- **Dynamics**: $N=3$ step returns (PER disabled for low-variance updates).
- **Constraints**: Constant Time Penalty for aggressive "Blitz" strategies.

**Result**: Achieved a **97% Win Rate** against the `heuristicTeam` on the tournament map (`bloxCapture.lay`).

## Project Files
- `A3_notebook.ipynb`: Complete implementation of the training pipeline, mixers, and buffers.
- `A3_report.pdf`: Detailed theoretical reflection, experimental logs, and hyperparameter sensitivity analysis.
