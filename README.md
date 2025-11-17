# Autonomous Highway Driving with Deep Reinforcement Learning

This project implements and compares four deep reinforcement learning (DRL) algorithms - DQN, PPO, TD3, and SAC - for autonomous highway driving using the `highway-env` simulation environment. All agents are trained using Multi-layer Perceptron (MLP) based policies, covering both discrete and continuous action spaces.

## Objective

The goal is to train reinforcement learning agents to learn safe and efficient driving behavior, specifically:
- Maintaining high speed without collisions
- Following lane discipline
- Navigating dynamic traffic environments
- Balancing safety, efficiency, and traffic rule compliance

## Findings

### Performance Summary
- **PPO**: Most consistent and safe driving behavior with stable lane-keeping
- **SAC**: Strong learning capability with minimal safety violations after training
- **TD3**: Zero collisions achieved but exploited environment by drifting off-road
- **DQN**: Struggled with stability and demonstrated erratic performance

### Algorithm Behavior Analysis
- **Discrete action algorithms** (DQN, PPO) produced more predictable driving behavior
- **Continuous control algorithms** (TD3, SAC) showed drifting behavior due to fine-grained control
- PPO demonstrated the best trade-off between learning stability and realistic driving
- TD3's perfect collision record came at the cost of unrealistic off-road driving

## Algorithms Implemented

| Algorithm | Type                  | Action Space | Key Characteristics                               | Performance |
|-----------|-----------------------|--------------|---------------------------------------------------|-------------|
| DQN       | Value-based           | Discrete     | ε-greedy policy, experience replay               | Erratic, high collision rate |
| PPO       | Policy gradient       | Discrete     | Clipped objective, stable updates                | **Best overall - stable and realistic** |
| TD3       | Actor-Critic          | Continuous   | Twin critics, delayed policy updates             | Zero collisions but off-road drifting |
| SAC       | Actor-Critic + Entropy| Continuous   | Entropy regularization, auto-tuned temperature   | Strong learning, low collisions |

## Environment Configuration

We used `highway-fast-v0` environment with the following key parameters:
- **Lanes**: 4 lanes for dense highway simulation
- **Vehicles**: 30 vehicles for meaningful interactions
- **Reward Structure**: 
  - Collision penalty: -2.0
  - High speed reward: 0.4 (20-30 units range)
  - Right lane reward: 0.1
  - No lane change reward/penalty

## Training environment

- **GPU**: NVIDIA RTX 4060 (8GB VRAM)
- **CPU**: Intel Core i7
- **RAM**: 32 GB
- **OS**: Windows 11
- **Python**: 3.10+
- **Training Time**: ~28 hours total for the final training (100,000 timesteps per algorithm)

## Training Details

### Hyperparameters
- **Learning Rate**: 1e-3 to 5e-4 depending on algorithm
- **Batch Size**: 64 for all algorithms
- **Buffer Size**: 100k for replay-based methods
- **Gamma**: 0.99 for all algorithms
- **Network Architecture**: (512, 256) for DQN/PPO, (400, 300) for TD3/SAC

## Results and Metrics

### Evaluation Metrics
- **Average Reward**: Learning performance and policy optimization
- **Collision Rate**: Safety evaluation and risk assessment
- **Episode Length**: Behavioral consistency and task completion

### Key Observations
1. **PPO** showed excellent lane discipline and realistic driving patterns
2. **SAC** initially drifted but learned to stabilize with continued training
3. **TD3** exploited reward function by avoiding collisions through off-road driving
4. **DQN** suffered from training instability and inconsistent performance

## Future Improvements

1. **Off-road Penalty**: Add explicit penalties for leaving road boundaries
2. **CnnPolicy**: Experiment with visual input instead of state observations
3. **Hybrid Approaches**: Combine imitation learning with RL for faster convergence
4. **Safety Constraints**: Implement Control Barrier Functions for rule enforcement
5. **Curriculum Learning**: Progressive difficulty increase for complex behaviors

