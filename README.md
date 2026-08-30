# DreamerV3 CartPole-v1 Experiments

A showcase of training and evaluating DreamerV3 (and PPO) on the CartPole-v1 environment using Eclectic-Sheep's SheepRL (`sheeprl`) framework.

---

## Table of Contents

- [Installation](#installation)
- [Dependencies](#dependencies)
- [Usage](#usage)
  - [Clone Repository](#clone-repository)
  - [Train DreamerV3 Agent](#train-dreamerv3-agent)
  - [Train PPO Agent](#train-ppo-agent)
  - [Visualize with TensorBoard](#visualize-with-tensorboard)
- [Directory Structure](#directory-structure)
- [Results](#results)
- [Status](#status)

---

## Installation

Install all required Python packages by running:

```bash
pip install -r requirements.txt
```

> If you are in a Jupyter or Colab environment, prepend `%` to each line:
>
> ```bash
> %pip install -r requirements.txt
> ```

---

## Dependencies

Key components are listed in `requirements.txt`:

- `lightning`, `omegaconf`, `hydra-core`, `rich`: core framework and config
- `gymnasium`, `gymnasium[atari]`, `dm_control`: environments
- `torchvision`, `moviepy`, `opencv-python`: image/video utilities
- `python-dotenv`, `tensorboard`: logging and environment

`sheeprl` itself is **not** in `requirements.txt` — it is not pip-installed. Per
[Usage](#usage) below, you clone `Eclectic-Sheep/sheeprl` and run its `sheeprl.py`
CLI directly from inside the clone.

Install all with:

```bash
pip install -r requirements.txt
```

---

## Usage

### Clone Repository

```bash
git clone https://github.com/Eclectic-Sheep/sheeprl.git
cd sheeprl
```

### Train DreamerV3 Agent

Quick 10k-step demo:

```bash
python sheeprl.py \
  exp=dreamer_v3 \
  env=gym env.id=CartPole-v1 \
  fabric.accelerator=cpu fabric.devices=1 \
  env.num_envs=1 env.sync_env=true
```

### Train PPO Agent

Quick 10k-step demo:

```bash
python sheeprl.py \
  exp=ppo \
  env=gym env.id=CartPole-v1 \
  fabric.accelerator=cpu fabric.devices=1 \
  env.num_envs=1 env.sync_env=true
```

### Visualize with TensorBoard

```bash
tensorboard --logdir logs/runs
```

---

## Directory Structure

```
sheeprl/                             # Root of cloned SheepRL repo
├── logs/                            # Training outputs
│   └── runs/                        # Organized by experiment and env
│       ├── dreamer_v3/              # DreamerV3 runs
│       │   └── CartPole-v1/         # CartPole-v1 logs
│       │       └── <timestamp>/      # Timestamped run folders
│       │           ├── version_0/   # Versioning
│       │           │   ├── checkpoints/   # Saved .ckpt files
│       │           │   ├── events.out.*    # TensorBoard logs
│       │           │   └── hparams.yaml    # Hyperparam snapshot
│       └── ppo/                     # PPO runs (similar structure)
├── sheeprl.py                       # CLI entrypoint
└── requirements.txt                 # Python dependencies
```

---

## Results

All recorded videos of the trained agents are stored in the `results/` directory at the repo root:

```
results/
├── dreamer_v3/                      # DreamerV3 videos
│   └── CartPole-v1/                 # DreamerV3 CartPole-v1 runs
│       └── video.mp4                # Example rollout video
└── ppo/                             # PPO videos
    └── CartPole-v1/                 # PPO CartPole-v1 runs
        └── video.mp4                # Example rollout video
```

You can play these `.mp4` files to review agent behaviors.

**No quantitative comparison data was retained**: no reward curves, learning curves, seeds, or hyperparameters for either run were kept, so this repo cannot support a rigorous DreamerV3-vs-PPO comparison -- only qualitative video evidence of each agent's behavior.

---

## Status

This repository is **archived**. For a more complete, actively maintained treatment of reinforcement learning, see [`reinforcement_learning_course`](https://github.com/denis-samatov/reinforcement_learning_course).

