# Environment Setup Guide

## Overview
이 프로젝트는 Python 3.10과 Conda 가상환경 `myvenv`를 기준으로 합니다.
기본 분석/머신러닝 패키지는 `requirements.txt`, 딥러닝 패키지는
`requirements-deep-learning.txt`에서 관리합니다.

## Environment Details

## Setup
```bash
# Create the environment once
conda create -n myvenv python=3.10 -y

# Activate it whenever you work on this project
conda activate myvenv

# Install the packages used by the data-analysis and ML notebooks
python -m pip install -r requirements.txt

# Install these only when you start the deep-learning problems
python -m pip install -r requirements-deep-learning.txt

# Register the environment as a VS Code/Jupyter notebook kernel
python -m ipykernel install --user --name myvenv --display-name "Python (myvenv)"
```

In VS Code, select **Python (myvenv)** as the notebook kernel. The deep-learning
file can be installed later in the same environment when those problems are reached.

## Verify Installation

Run this test after installing `requirements.txt`:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split

print("Core libraries imported successfully!")
print(f"NumPy: {np.__version__}")
print(f"Pandas: {pd.__version__}")
```

After installing `requirements-deep-learning.txt`, verify TensorFlow and PyTorch
separately with `import tensorflow` and `import torch`.

## Notes

- NumPy is pinned to 1.25.2 in `requirements.txt`; it stays below NumPy 2 and is
   compatible with TensorFlow 2.15.0.
- The notebooks load CSV files from local `data/` and `data2/` folders. Keep those
   datasets in the expected locations before running the exercises.
- PyTorch may install a large wheel. On a machine with a CUDA GPU, use the install
   command recommended by the official PyTorch selector for that machine.
