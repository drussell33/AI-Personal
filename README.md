# AI-Personal

![Repo Size](https://img.shields.io/github/repo-size/drussell33/AI-Personal)
![Last Commit](https://img.shields.io/github/last-commit/drussell33/AI-Personal)
![Top Language](https://img.shields.io/github/languages/top/drussell33/AI-Personal)

AI-Personal is a learning-focused collection of Python experiments covering reinforcement learning and large language model workflows. The repository brings together standalone implementations for Deep Q-Learning, Deep Convolutional Q-Learning, A3C, PPO, SAC, and an LLM fine-tuning script, primarily using Gymnasium Atari and control environments. It is best understood as a personal research sandbox rather than a packaged application.

## Key Features

- Standalone reinforcement learning implementations for:
  - A3C
  - Deep Q-Learning
  - Deep Convolutional Q-Learning
  - PPO
  - SAC
- Environment setup scripts for Gymnasium Atari and Box2D-based experiments
- Atari preprocessing logic for stacked grayscale frames in the A3C implementation
- Experience replay and target-network workflow in the Deep Q-Learning implementation
- Convolutional Q-network pipeline for Ms. Pac-Man training
- PPO actor-critic implementation for continuous action spaces
- SAC actor/critic and replay-buffer implementation for continuous control
- LLM fine-tuning workflow using LoRA, TRL, Transformers, and a medical-terms dataset
- Video export helpers using `imageio` and IPython HTML display in several RL scripts

## Tech Stack

### Backend
- Python
- PyTorch

### Frontend
- None in the current repository

### Database
- None in the current repository

### Tools / Services
- Gymnasium
- ALE-Py
- OpenCV
- Pillow
- Torchvision
- ImageIO
- IPython display utilities
- Hugging Face Transformers
- Datasets
- PEFT
- TRL
- BitsAndBytes

## Architecture Overview

This repository does not follow a traditional frontend/backend/database application architecture. Instead, it is organized as a set of independent Python training scripts grouped by algorithm family.

At a high level, each reinforcement learning script follows a similar flow:

1. Create a Gymnasium environment.
2. Define a neural network architecture in PyTorch.
3. Wrap training behavior in an agent class.
4. Run a training loop that interacts directly with the environment.
5. Optionally save checkpoints or render episode output to video.

Visible implementation patterns include:

- **Neural network classes** for policy/value or Q-network definitions
- **Agent classes** encapsulating action selection and training updates
- **Replay buffers / memory buffers** for DQN, PPO, and SAC-style workflows
- **Environment preprocessing wrappers** for Atari observations
- **Separation of model definition and training loop** within individual scripts

There is no shared package layer, no dependency injection setup, no DTO layer, and no API surface. Each folder is effectively a self-contained experiment.

## Project Structure

```tree
AI-Personal/
├── A3C/
│   ├── Installs.txt
│   └── a3c.py
├── Deep Convolutional Q-Learning/
│   ├── Installs.txt
│   └── deep_convolutional_q_learning.py
├── Deep Q-Learning/
│   ├── Installs.txt
│   └── deep_q_learning.py
├── LLMs/
│   ├── Installs.txt
│   └── llms.py
├── PPO and SAC/
│   ├── ppo.py
│   └── sac.py
└── README.md
```

### Folder Notes

- **A3C/**  
  Contains an Asynchronous Advantage Actor-Critic style implementation for `KungFuMasterNoFrameskip-v0`, including custom Atari preprocessing and batched environment handling.

- **Deep Convolutional Q-Learning/**  
  Contains a convolutional DQN-style training script for `MsPacmanNoFrameskip-v0`.

- **Deep Q-Learning/**  
  Contains a fully connected DQN implementation for `LunarLander-v3`, including replay memory and target-network soft updates.

- **LLMs/**  
  Contains a supervised fine-tuning script for a LLaMA-based causal language model using LoRA and TRL.

- **PPO and SAC/**  
  Contains separate implementations for PPO and SAC targeting continuous-control training with `CarRacing-v3`.

## Getting Started

### Prerequisites

Because the repository does not include a `requirements.txt`, dependencies need to be installed manually based on the scripts.

Recommended environment:

- Python 3.10+
- pip
- Git
- SWIG
- A working PyTorch installation
- Optional: Jupyter / IPython if you want to use the embedded video display helpers

### Installation

```bash
git clone https://github.com/drussell33/AI-Personal.git
cd AI-Personal
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

**Windows**
```bash
.venv\Scripts\activate
```

**macOS / Linux**
```bash
source .venv/bin/activate
```

Install the packages referenced by the repository:

```bash
pip install torch numpy opencv-python pillow torchvision imageio ipython
pip install gymnasium ale-py "gymnasium[atari,accept-rom-license,box2d]"
pip install transformers datasets peft trl bitsandbytes
```

If your platform requires it, install SWIG before Box2D-related environments:

```bash
# Ubuntu / Debian
sudo apt-get install -y swig
```

### Usage

Run individual experiments directly from their folders.

#### A3C

```bash
python "A3C/a3c.py"
```

#### Deep Convolutional Q-Learning

```bash
python "Deep Convolutional Q-Learning/deep_convolutional_q_learning.py"
```

#### Deep Q-Learning

```bash
python "Deep Q-Learning/deep_q_learning.py"
```

#### LLM Fine-Tuning

```bash
python "LLMs/llms.py"
```

#### PPO

```bash
python "PPO and SAC/ppo.py"
```

#### SAC

```bash
python "PPO and SAC/sac.py"
```

## Roadmap

- [x] Add A3C experiment for Atari-style training
- [x] Add Deep Q-Learning experiment for LunarLander
- [x] Add Deep Convolutional Q-Learning experiment for Ms. Pac-Man
- [x] Add PPO implementation for continuous control
- [x] Add SAC implementation for continuous control
- [x] Add LLM fine-tuning example using LoRA and TRL
- [ ] Add a repository-level `requirements.txt`
- [ ] Add per-project setup instructions and expected environment versions
- [ ] Add saved model checkpoints and evaluation guidance
- [ ] Add reproducibility settings and seed management across all scripts
- [ ] Refactor shared RL utilities into reusable modules
- [ ] Add tests, linting, and formatting configuration
- [ ] Add screenshots, training curves, and demo outputs
- [ ] Document known issues and compatibility notes for Gymnasium environments

## Contributing

Contributions are welcome through the standard GitHub workflow:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Commit with clear messages
5. Push your branch
6. Open a pull request

For best results, keep changes scoped, document any new dependencies, and update this README when adding new experiments or folders.

## Screenshots / Demo

Screenshots, sample rollouts, and demo outputs have not been documented in the repository yet.

Suggested additions for this section:

- Training screenshots
- Environment rollouts
- Saved evaluation videos
- Loss / reward curves

## Contact

- GitHub: [drussell33](https://github.com/drussell33)
