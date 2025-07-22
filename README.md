# MathBeaver Fine-tuning Setup Guide

## Overview

This project fine-tunes the Phi-4-reasoning-plus model with SOS chain of thought training data (from Bohan) using the LoRA through Axolotl.

[<img src="https://raw.githubusercontent.com/axolotl-ai-cloud/axolotl/main/image/axolotl-badge-web.png" alt="Built with Axolotl" width="200" height="32"/>](https://github.com/axolotl-ai-cloud/axolotl)

# Colab Link to QA testing with trained model

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1p37fHrCF41H8iUPr-23Sm1g37I53yikm?usp=sharing)

## Prerequisites

- RunPod instance with enough disk memory
- SSH access to RunPod
- Python 3.11 or higher
- Access to training data (Google Drive folder)

## Setup Instructions

### 1. Initial Setup

SSH into your RunPod instance and navigate to the workspace:

```bash
# Connect to RunPod
ssh runpod-tcp

# CD to workspace
cd /workspace

# Git clone repo
cd mathbeaver-finetune
cd into "data" folder
pip install gdown

```

### 2. Clone Shivam's repo (Richard's branch)
```bash
git clone https://github.com/Shivamshaiv/mathbeaver-finetune.git
```


### 3. Download files from Bohan's drive
```bash

# download training data into "data" in the "Data_SOS_Cot" folder
# to get the first 50 folders from Bohan's google drive of SOS training data
gdown --folder https://drive.google.com/drive/folders/1E1tHwS7YQOajZcjWsMXpTaPdRZm9jYcC --remaining-ok
```

### 4. Set up environment 
``` bash
conda create -n phi-tuning python=3.11
conda init
# restart shell
conda activate phi-tuning

#install axolotl
pip install axolotl
```

### 5. Preprocess data to ChatML format

run `python preprocess_data_chatml.py`

### 6. Configure config file (with small number of examples)

Run training script: `python run_training.py --config config_test.yaml`

### 7. Results

Output saved to `outputs` directory









