# Quick Start Guide

Get up and running with the Stock Price Prediction project in just a few minutes!

## ⚡ 5-Minute Setup

### 1. Prerequisites Check
```bash
# Check Python version (need 3.8+)
python --version

# Check pip
pip --version
```

### 2. Clone & Install
```bash
# Clone the repository
git clone https://github.com/NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN.git
cd Stock-Price-Prediction-Project-using-LSTM-and-RNN

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 3. Setup Kaggle API
```bash
# 1. Get your API token from https://www.kaggle.com/account
# 2. Download kaggle.json
# 3. Place it in ~/.kaggle/ directory

# On Linux/macOS:
mkdir -p ~/.kaggle
cp /path/to/kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json

# On Windows:
mkdir %USERPROFILE%\.kaggle
copy C:\path\to\kaggle.json %USERPROFILE%\.kaggle\
```

### 4. Run the Notebook
```bash
# Start Jupyter
jupyter notebook main.ipynb

# In Jupyter:
# - Click "Kernel" → "Restart & Run All"
# - Wait for completion (~30-60 minutes)
```

## 📊 What You'll Get

- **Data Analysis**: Comprehensive EDA of Apple stock (1980-2020)
- **3 Models**: Simple RNN, Univariate LSTM, Multivariate LSTM
- **Visualizations**: 20+ plots showing trends, predictions, and analysis
- **Forecasts**: 30-day future price predictions
- **Performance Metrics**: RMSE, MAE, MAPE, R², Direction Accuracy

## 🎯 Expected Timeline

| Step | Time | What Happens |
|------|------|--------------|
| Installation | 5 min | Download dependencies |
| Data Download | 2-5 min | Download NASDAQ dataset (~1GB) |
| Data Processing | 5 min | Clean and prepare data |
| Model Training | 15-30 min | Train 3 models |
| Evaluation | 5 min | Generate predictions and metrics |
| **Total** | **30-60 min** | Complete analysis |

## 🚨 Common First-Time Issues

### Issue 1: Kaggle API Error
```
OSError: Could not find kaggle.json
```
**Fix**: Follow Step 3 above to setup Kaggle credentials.

### Issue 2: Memory Error
```
MemoryError during model training
```
**Fix**: Close other applications, or reduce batch_size in notebook.

### Issue 3: Module Not Found
```
ModuleNotFoundError: No module named 'tensorflow'
```
**Fix**: Make sure virtual environment is activated and run `pip install -r requirements.txt`

## 📚 Next Steps

After successful run:

1. **Explore Results**: Review model performance metrics
2. **Customize**: Try different stocks or parameters (see [USAGE.md](USAGE.md))
3. **Contribute**: Improve models or add features (see [CONTRIBUTING.md](CONTRIBUTING.md))

## 💡 Tips for First Run

- **Be patient**: First run takes longer due to data download
- **Check memory**: Close unnecessary applications
- **Read outputs**: Each cell explains what's happening
- **Save work**: Jupyter auto-saves, but save manually too

## 🆘 Need Help?

- **Full Setup Guide**: [SETUP.md](SETUP.md)
- **Detailed Usage**: [USAGE.md](USAGE.md)
- **Troubleshooting**: Check SETUP.md troubleshooting section
- **Issues**: [GitHub Issues](https://github.com/NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN/issues)

## ⚠️ Important Reminder

This project is **for educational purposes only**. Do not use these predictions for actual trading decisions. Always consult financial professionals for investment advice.

---

**Ready to start? Run the commands above and you'll be forecasting in minutes! 🚀**
