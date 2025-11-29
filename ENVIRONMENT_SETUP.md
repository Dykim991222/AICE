# Environment Setup Guide

## Overview
이 프로젝트는 다음 환경에서 설정되고 테스트되었습니다:
- **Python**: 3.10 (conda-forge)
- **Conda Environment**: myvenv
- **Package Manager**: conda (conda-forge channel)

## Environment Details

### Core Libraries & Versions
```
numpy==1.24.3                    # Numerical computing
pandas==2.3.3                    # Data manipulation
matplotlib==3.10.8               # Data visualization
seaborn==0.13.2                  # Statistical visualization
scikit-learn==1.7.2              # Machine learning
tensorflow==2.15.0               # Deep learning (CPU)
keras==2.15.0                    # Neural networks API
jupyter==1.1.1                   # Notebook environment
jupyterlab==4.5.0                # JupyterLab IDE
```

### Python Version
```
python==3.10.19
```

## Installation Instructions

### Option 1: Using Conda (Recommended)
```bash
# 1. Create new environment
conda create -n myvenv python=3.10 -y

# 2. Activate environment
conda activate myvenv

# 3. Install packages from conda-forge
conda install -c conda-forge tensorflow==2.15.0 scikit-learn pandas numpy==1.24.3 matplotlib seaborn jupyter jupyterlab -y
```

### Option 2: Using requirements.txt
```bash
# 1. Create and activate environment (same as above)
conda create -n myvenv python=3.10 -y
conda activate myvenv

# 2. Install from requirements.txt
pip install -r requirements.txt
```

## Important Notes

### ⚠️ Compatibility Issue: TensorFlow & NumPy
- **TensorFlow 2.15.0** requires **NumPy 1.24.3**
- DO NOT use NumPy 2.x versions (causes binary incompatibility error)
- Error message if incompatible: 
  ```
  ValueError: numpy.dtype size changed, may indicate binary incompatibility
  ```

### Why Use conda-forge?
- **Better binary compatibility** for TensorFlow on macOS ARM64
- **Automatic dependency resolution** prevents version conflicts
- **Pre-built wheels** for faster installation

## Verifying Installation

Run this test to verify everything works:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from tensorflow.keras.layers import Dense

print("✅ All libraries imported successfully!")
print(f"NumPy: {np.__version__}")
print(f"Pandas: {pd.__version__}")
print(f"TensorFlow: {__import__('tensorflow').__version__}")
```

## Troubleshooting

### Issue: `ValueError: numpy.dtype size changed`
**Solution**: Reinstall environment with correct NumPy version
```bash
conda remove -n myvenv --all -y
conda create -n myvenv python=3.10 -y
conda activate myvenv
conda install -c conda-forge tensorflow==2.15.0 numpy==1.24.3 -y
```

### Issue: Jupyter Notebook not starting
**Solution**: Reinstall jupyter
```bash
conda install -c conda-forge jupyter jupyterlab -y
```

### Issue: TensorFlow still failing after install
**Solution**: Use pip to downgrade NumPy if needed
```bash
pip install --force-reinstall numpy==1.24.3
```

## Configuration Files

- `.vscode/settings.json`: VS Code editor autocomplete disabled
- `.gitignore`: Data folder excluded from version control
- `requirements.txt`: Full package list with versions
- `ENVIRONMENT_SETUP.md`: This file

## Notes for Collaborators

If you're cloning this repository:

1. Create the environment:
   ```bash
   conda create -n myvenv python=3.10 -y
   conda activate myvenv
   ```

2. Install dependencies:
   ```bash
   conda install -c conda-forge tensorflow==2.15.0 scikit-learn pandas numpy==1.24.3 matplotlib seaborn jupyter jupyterlab -y
   ```

3. Create `data/` folder locally (not in repo):
   ```bash
   mkdir -p data
   ```

4. Add your dataset files to `data/` folder

---

**Last Updated**: 2025-11-29  
**Python Version**: 3.10.19  
**conda-forge Channel Used**: Yes
