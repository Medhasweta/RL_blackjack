# Blackjack Reinforcement Learning Agent

## Overview
This code defines a reinforcement learning agent that learns to play a simplified version of the blackjack game. The objective is to maximize rewards by learning an optimal policy for when to "hit" or "stick" based on the current state of the game.

## How It Works

### Environment
The environment (`Environment` class) simulates the blackjack game with the following characteristics:
- The state space is defined by the player's current card sum (ranging from 12 to 21) and the dealer's showing card (1-10).
- Actions are binary: 0 for "stick" (stop receiving cards) and 1 for "hit" (receive another card).
- The deck is a standard 52-card set, reshuffled with each deal (sampling with replacement).

### Agent
The agent (`Agent` class) interacts with the environment and learns from the outcomes of its actions using the following methods:
- **Epsilon-greedy strategy**: The agent explores the action space with a probability of `epsilon` to ensure a balance between exploration and exploitation.
- **Reward Averaging**: After each episode (game), the agent updates its action-value function estimates (Q-values) based on the total reward received in the episode.
- **Policy**: The agent maintains a policy, represented as Q-values, for taking actions based on the current state.

### Training
The script trains the agent by repeatedly playing the game and updating the agent's policy based on the rewards received:
- Each game is an episode where the agent starts with a random state.
- The agent selects actions using its current policy, observes rewards, and tracks state transitions.
- At the end of the episode, the agent updates its Q-values based on the cumulative rewards received.

### Output
- The script prints the training progress periodically.
- After every fixed number of episodes, it displays the current greedy policy (the best action for each state).

## Usage
Ensure you have the necessary libraries: `random`, `pickle`, `numpy`, and `collections`. Then run the script to train the agent. Modify `N_episodes` to change the number of games played for training.

## Key Concepts
- **State Dimension**: The dimension of the state space representing possible game states.
- **Action Dimension**: The number of possible actions the agent can take.
- **Q-value (Q(s,a))**: The expected reward for taking action a in state s, following policy π.

## Conclusion
This script represents a basic approach to training a reinforcement learning agent using reward averaging in a simplified blackjack environment. The agent's policy improves over time, learning to make better decisions based on the current state of the game.
