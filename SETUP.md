# Setup Guide

Complete installation and setup instructions for the Stock Price Prediction project.

## Table of Contents

1. [System Requirements](#system-requirements)
2. [Installation Methods](#installation-methods)
3. [Kaggle API Setup](#kaggle-api-setup)
4. [Verification](#verification)
5. [Platform-Specific Instructions](#platform-specific-instructions)
6. [GPU Setup (Optional)](#gpu-setup-optional)
7. [Troubleshooting](#troubleshooting)

## System Requirements

### Minimum Requirements
- **OS**: Windows 10, macOS 10.14+, or Linux (Ubuntu 18.04+)
- **Python**: 3.8 or higher
- **RAM**: 8 GB minimum
- **Storage**: 5 GB free space
- **Internet**: Required for dataset download

### Recommended Requirements
- **OS**: Latest stable version
- **Python**: 3.10 or 3.11
- **RAM**: 16 GB or more
- **Storage**: 10 GB free space
- **GPU**: NVIDIA GPU with CUDA support (optional, for faster training)

### Software Dependencies
- Python 3.8+
- pip (Python package manager)
- Jupyter Notebook or JupyterLab
- Git (for cloning repository)

## Installation Methods

### Method 1: Using pip (Recommended)

#### Step 1: Clone the Repository

```bash
# Using HTTPS
git clone https://github.com/NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN.git

# Or using SSH
git clone git@github.com:NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN.git

# Navigate to project directory
cd Stock-Price-Prediction-Project-using-LSTM-and-RNN
```

#### Step 2: Create Virtual Environment

**Using venv (built-in):**
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate

# On macOS/Linux:
source venv/bin/activate
```

**Using conda (alternative):**
```bash
# Create conda environment
conda create -n stock-prediction python=3.10

# Activate environment
conda activate stock-prediction
```

#### Step 3: Install Dependencies

```bash
# Upgrade pip
pip install --upgrade pip

# Install requirements
pip install -r requirements.txt
```

#### Step 4: Verify Installation

```bash
# Check Python version
python --version

# Check installed packages
pip list

# Test imports
python -c "import tensorflow as tf; import numpy as np; import pandas as pd; print('All imports successful!')"
```

### Method 2: Using Conda

```bash
# Clone repository
git clone https://github.com/NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN.git
cd Stock-Price-Prediction-Project-using-LSTM-and-RNN

# Create environment from requirements
conda create -n stock-prediction python=3.10
conda activate stock-prediction

# Install packages
pip install -r requirements.txt

# Or install individually with conda
conda install numpy pandas matplotlib seaborn scikit-learn scipy jupyter
pip install tensorflow kagglehub
```

### Method 3: Using Docker (Advanced)

```dockerfile
# Create Dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8888

CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--no-browser", "--allow-root"]
```

```bash
# Build Docker image
docker build -t stock-prediction .

# Run container
docker run -p 8888:8888 -v $(pwd):/app stock-prediction
```

## Kaggle API Setup

The project downloads data from Kaggle, which requires API authentication.

### Step 1: Create Kaggle Account

1. Visit [kaggle.com](https://www.kaggle.com)
2. Sign up or log in to your account

### Step 2: Generate API Token

1. Go to your account settings: https://www.kaggle.com/account
2. Scroll to "API" section
3. Click "Create New API Token"
4. This downloads `kaggle.json` file

### Step 3: Configure API Credentials

#### On Linux/macOS:

```bash
# Create .kaggle directory
mkdir -p ~/.kaggle

# Copy kaggle.json to .kaggle directory
cp /path/to/downloaded/kaggle.json ~/.kaggle/

# Set proper permissions (important for security)
chmod 600 ~/.kaggle/kaggle.json
```

#### On Windows:

```cmd
# Create .kaggle directory
mkdir %USERPROFILE%\.kaggle

# Copy kaggle.json
copy C:\path\to\downloaded\kaggle.json %USERPROFILE%\.kaggle\

# No need to change permissions on Windows
```

### Step 4: Verify Kaggle API

```bash
# Test Kaggle API
kaggle datasets list

# If successful, you'll see a list of datasets
```

### Alternative: Environment Variables

Instead of using `kaggle.json`, you can set environment variables:

```bash
# On Linux/macOS
export KAGGLE_USERNAME=your_username
export KAGGLE_KEY=your_api_key

# On Windows (Command Prompt)
set KAGGLE_USERNAME=your_username
set KAGGLE_KEY=your_api_key

# On Windows (PowerShell)
$env:KAGGLE_USERNAME="your_username"
$env:KAGGLE_KEY="your_api_key"
```

## Verification

### Check Installation

Run this verification script:

```python
# save as verify_setup.py
import sys
import pkg_resources

def check_python_version():
    version = sys.version_info
    print(f"Python version: {version.major}.{version.minor}.{version.micro}")
    if version.major >= 3 and version.minor >= 8:
        print("[OK] Python version is compatible")
        return True
    else:
        print("[FAIL] Python version must be 3.8 or higher")
        return False

def check_packages():
    required = {
        'numpy': '2.0.0',
        'pandas': '2.0.0',
        'tensorflow': '2.15.0',
        'matplotlib': '3.7.0',
        'seaborn': '0.12.0',
        'scikit-learn': '1.3.0',
        'scipy': '1.10.0',
        'jupyter': '1.0.0',
        'kagglehub': '0.1.0'
    }
    
    print("\nChecking packages:")
    all_installed = True
    
    for package, min_version in required.items():
        try:
            version = pkg_resources.get_distribution(package).version
            print(f"[OK] {package}: {version}")
        except pkg_resources.DistributionNotFound:
            print(f"[FAIL] {package}: NOT INSTALLED")
            all_installed = False
    
    return all_installed

def check_imports():
    print("\nChecking imports:")
    imports = [
        'numpy',
        'pandas',
        'tensorflow',
        'matplotlib',
        'seaborn',
        'sklearn',
        'scipy',
        'kagglehub'
    ]
    
    all_imported = True
    for module in imports:
        try:
            __import__(module)
            print(f"[OK] {module}")
        except ImportError as e:
            print(f"[FAIL] {module}: {e}")
            all_imported = False
    
    return all_imported

if __name__ == "__main__":
    print("=" * 50)
    print("SETUP VERIFICATION")
    print("=" * 50)
    
    checks = [
        check_python_version(),
        check_packages(),
        check_imports()
    ]
    
    print("\n" + "=" * 50)
    if all(checks):
        print("[OK] All checks passed! Setup is complete.")
    else:
        print("[FAIL] Some checks failed. Please review the errors above.")
    print("=" * 50)
```

Run the verification:
```bash
python verify_setup.py
```

### Test Jupyter Notebook

```bash
# Start Jupyter
jupyter notebook

# A browser window should open
# Try creating a new Python 3 notebook
# Test basic imports:
import numpy as np
import pandas as pd
import tensorflow as tf
print("Setup verified!")
```

## Platform-Specific Instructions

### Windows

#### Using Anaconda (Recommended for Windows):

1. **Download Anaconda**: https://www.anaconda.com/download
2. **Install Anaconda** with default settings
3. **Open Anaconda Prompt**
4. **Follow Method 2 instructions** (Using Conda)

#### Common Windows Issues:

**Long Path Names:**
```cmd
# Enable long path support
reg add HKLM\SYSTEM\CurrentControlSet\Control\FileSystem /v LongPathsEnabled /t REG_DWORD /d 1 /f
```

**Visual C++ Redistributable:**
- Some packages require Visual C++
- Download: https://aka.ms/vs/17/release/vc_redist.x64.exe

### macOS

#### Install Xcode Command Line Tools:
```bash
xcode-select --install
```

#### Using Homebrew:
```bash
# Install Homebrew if not installed
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Python
brew install python@3.10

# Verify installation
python3 --version
```

#### Apple Silicon (M1/M2) Macs:

TensorFlow on Apple Silicon:
```bash
# Install Apple's tensorflow
pip install tensorflow-macos
pip install tensorflow-metal  # For GPU acceleration
```

### Linux (Ubuntu/Debian)

#### Install Python and dependencies:
```bash
# Update package list
sudo apt update

# Install Python and pip
sudo apt install python3.10 python3-pip python3-venv

# Install system dependencies
sudo apt install build-essential python3-dev

# Install git
sudo apt install git
```

#### Virtual Environment:
```bash
# Install venv if not available
sudo apt install python3.10-venv

# Create and activate
python3 -m venv venv
source venv/bin/activate
```

## GPU Setup (Optional)

For faster model training with NVIDIA GPU.

### Check GPU Availability

```python
import tensorflow as tf
print("GPU Available:", len(tf.config.list_physical_devices('GPU')) > 0)
print("GPU Devices:", tf.config.list_physical_devices('GPU'))
```

### CUDA Setup

#### For CUDA 11.8 (TensorFlow 2.15+):

**Windows:**
1. Download CUDA Toolkit 11.8: https://developer.nvidia.com/cuda-11-8-0-download-archive
2. Download cuDNN 8.6: https://developer.nvidia.com/cudnn
3. Install both with default settings
4. Add to PATH if not automatic

**Linux:**
```bash
# Install CUDA
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda-repo-ubuntu2204-11-8-local_11.8.0-520.61.05-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2204-11-8-local_11.8.0-520.61.05-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2204-11-8-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda

# Add to PATH
echo 'export PATH=/usr/local/cuda-11.8/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda-11.8/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

### Verify GPU Setup

```bash
# Check NVIDIA driver
nvidia-smi

# Test TensorFlow GPU
python -c "import tensorflow as tf; print('GPU:', tf.config.list_physical_devices('GPU'))"
```

## Troubleshooting

### Common Issues

#### 1. ModuleNotFoundError

**Problem:** `ModuleNotFoundError: No module named 'xyz'`

**Solution:**
```bash
# Make sure virtual environment is activated
pip install -r requirements.txt

# Or install specific package
pip install package-name
```

#### 2. Permission Denied

**Problem:** `Permission denied` when installing packages

**Solution:**
```bash
# Use --user flag
pip install --user package-name

# Or use virtual environment (recommended)
```

#### 3. SSL Certificate Error

**Problem:** SSL verification failed

**Solution:**
```bash
# Upgrade pip and certificates
pip install --upgrade pip certifi

# Or temporarily disable SSL verification (not recommended)
pip install --trusted-host pypi.org --trusted-host files.pythonhosted.org package-name
```

#### 4. Kaggle API Not Found

**Problem:** `kaggle: command not found`

**Solution:**
```bash
# Install Kaggle CLI
pip install kaggle

# Verify installation
which kaggle  # On Unix
where kaggle  # On Windows
```

#### 5. TensorFlow Import Error

**Problem:** `ImportError: cannot import name 'xyz' from 'tensorflow'`

**Solution:**
```bash
# Reinstall TensorFlow
pip uninstall tensorflow
pip install tensorflow==2.15.0

# Clear cache
pip cache purge
```

#### 6. Jupyter Kernel Not Found

**Problem:** Jupyter can't find the kernel

**Solution:**
```bash
# Install ipykernel in virtual environment
pip install ipykernel

# Register kernel
python -m ipykernel install --user --name=stock-prediction --display-name="Stock Prediction"

# Select kernel in Jupyter: Kernel > Change Kernel > Stock Prediction
```

### Getting Additional Help

If you encounter issues not covered here:

1. **Check GitHub Issues**: https://github.com/NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN/issues
2. **Create New Issue**: Provide error message, OS, Python version, steps to reproduce
3. **Stack Overflow**: Search for similar issues
4. **Official Documentation**: TensorFlow, Pandas, NumPy docs

## Post-Setup Steps

After successful installation:

1. **Run verification script**
2. **Launch Jupyter Notebook**
3. **Open main.ipynb**
4. **Run first few cells** to confirm everything works
5. **Read USAGE.md** for detailed usage instructions

## Environment Management

### Save Current Environment

```bash
# Save exact versions
pip freeze > requirements-freeze.txt

# Create conda environment file
conda env export > environment.yml
```

### Reproduce Environment

```bash
# From requirements
pip install -r requirements-freeze.txt

# From conda environment
conda env create -f environment.yml
```

### Update Packages

```bash
# Update all packages
pip install --upgrade -r requirements.txt

# Update specific package
pip install --upgrade tensorflow
```

---

**Setup Complete! Ready to start forecasting!**

For next steps, see [USAGE.md](USAGE.md).
