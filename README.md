# MathBeaver Fine-tuning Setup Guide

## Overview

This project fine-tunes the Phi-4-reasoning-plus model with SOS chain of thought training data (from Bohan) using the LoRA through Axolotl.

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


### 2. Download files from Bohan's drive
```bash

# download training data into "data" in the "Data_SOS_Cot" folder
# to get the first 50 folders from Bohan's google drive of SOS training data
gdown --folder https://drive.google.com/drive/folders/1E1tHwS7YQOajZcjWsMXpTaPdRZm9jYcC --remaining-ok
```

### 3. Set up environment 
``` bash
conda create -n phi-tuning python=3.11
conda init
# restart shell
conda activate phi-tuning

#install axolotl
pip install axolotl
```

### 4. Preprocess data to ChatML format

run `python preprocess_data_chatml.py`

### 5. Configure config file (with small number of examples)

Run training script: `python run_training.py --config config_test.yaml`

### 6. Results

Output saved to `outputs` directory









