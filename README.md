# RL-Mario-Agent

A deep Q-learning agent that learns to play level 1-1 of *Super Mario Bros.* from raw game frames, built with PyTorch and OpenAI Gym.
Project with the Vision and Language Group, IIT Roorkee (2022).

The game environment comes from [`gym-super-mario-bros`](https://pypi.org/project/gym-super-mario-bros/).

## Method

The agent uses **deep Q-learning (DQN)** with two standard stabilisation techniques:

- **Experience replay:** transitions are stored in a replay buffer (30,000 entries) and sampled in random mini-batches, which breaks the correlation between consecutive frames.
- **Target network:** a second copy of the Q-network, updated every 5,000 steps, computes the learning targets, so the targets don't shift at every update.

The training target is `r + γ · max_a Q_target(s', a)`, optimised with the Huber (smooth L1) loss and Adam.

**Input processing:** frames are max-pooled over 4 skipped frames, converted to greyscale, resized to 84×84, stacked in groups of 4 and scaled to [0, 1]. The agent uses the `RIGHT_ONLY` action set.

**Network:** three convolutional layers (32, 64, 64 filters) followed by two fully connected layers (512 units, then one output per action).

## Hyperparameters

| Parameter | Value |
|---|---|
| Episodes | 2000 |
| Learning rate | 0.00025 |
| Discount factor (γ) | 0.9 |
| Batch size | 32 |
| Replay buffer size | 30,000 |
| Exploration (ε) | 1.0 → 0.02, decay 0.99 per update |
| Target-network update | every 5,000 steps |

## Results

Average reward per 500 episodes over training:

<img src="https://user-images.githubusercontent.com/108410048/176499258-0609ee71-69e0-4cdc-9d29-e9d4e022e0b5.jpeg" width="500">

The agent learns to make steady progress through the level and reached the end of level 1-1 during training. Longer training (around 10,000 episodes) would likely make this more consistent.

## Running

Open `MARIO_FINAL.ipynb` in Google Colab; the first cell installs the dependencies.

## Libraries

PyTorch, gym / gym-super-mario-bros, nes-py, OpenCV, NumPy, Matplotlib.

---
Project by **Pratyush Jha** and **Sudatt Kayal**.
