# MathBeaver Fine-tuning Setup Guide

This guide documents the steps to fine-tune the Microsoft Phi-4 model using chain-of-thought mathematical reasoning data on RunPod.

## Project Overview

This project fine-tunes the Phi-4-reasoning-plus model with sum-of-squares chain-of-thought training data using the LoRA (Low-Rank Adaptation) technique through Axolotl.

## Prerequisites

- RunPod instance with CUDA-compatible GPU (recommended: 24GB+ VRAM)
- SSH access to RunPod
- Python 3.11 or higher
- Access to training data (Google Drive folder)

## Setup Instructions

### 1. Initial Setup

SSH into your RunPod instance and navigate to the workspace:

```bash
# Connect to RunPod
ssh your-runpod-connection

# Navigate to workspace
cd /workspace

# Clone or navigate to project directory
cd mathbeaver-finetune


SSH into runpod-tcp

cd into workspace in home

cd into mathbeaver_finetune

cd into "data" folder

pip install gdown

run: gdown --folder https://drive.google.com/drive/folders/1E1tHwS7YQOajZcjWsMXpTaPdRZm9jYcC --remaining-ok

to get the first 50 folders from Bohan's google drive of SOS training data

download training data into "data" in the "Data_SOS_Cot" folder

conda create -n phi-tuning python=3.11
conda init
restart shell
conda activate phi-tuning

# Install Axolotl
pip install axolotl

Preprocess data to ChatML format

Edit config file: config_cot.yaml

Start screen session

screen -S training

Run training script: python run_training.py --config config_cot.yaml

ctrl+A, then D

Monitor progress later:

ssh your-runpod-connection

# List screen sessions
screen -ls

# Reconnect to your training session
screen -r training









