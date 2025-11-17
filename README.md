# Autonomous Highway Driving with Deep Reinforcement Learning

This project implements and compares four deep reinforcement learning (DRL) algorithms - DQN, PPO, TD3, and SAC - for autonomous highway driving using the `highway-env` simulation environment. All agents are trained using Multi-layer perceptron(MLP) based policies, and cover discrete and continuous action spaces are explored.

## Project Objective

The goal is to train reinforcement learning agents to learn safe and efficient driving behavior, specifically:

- Maintaining high speed without collisions
- Following lane discipline
- Navigating dynamic traffic environments

## Algorithms Implemented

| Algorithm | Type                  | Action Space | Notes                                      |
|-----------|-----------------------|--------------|--------------------------------------------|
| DQN       | Value-based           | Discrete     | Prone to instability and high collision    |
| PPO       | Policy gradient       | Discrete     | Stable and realistic driving behavior      |
| TD3       | Actor-Critic          | Continuous   | No collisions but unrealistic off-road use |
| SAC       | Actor-Critic + Entropy| Continuous   | Balanced learning with low collisions      |

## System Setup

- GPU: NVIDIA RTX 4060
- CPU: Intel Core i7
- RAM: 32 GB
- OS: Windows 11
- Python: 3.10+


