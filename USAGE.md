# Usage Guide

This guide provides detailed instructions on how to use the Stock Price Prediction project.

## Table of Contents

1. [Quick Start](#quick-start)
2. [Detailed Walkthrough](#detailed-walkthrough)
3. [Customization Options](#customization-options)
4. [Understanding the Output](#understanding-the-output)
5. [Troubleshooting](#troubleshooting)
6. [Advanced Usage](#advanced-usage)

## Quick Start

### Running the Notebook

1. **Start Jupyter Notebook**
   ```bash
   jupyter notebook main.ipynb
   ```

2. **Run All Cells**
   - Click `Kernel` → `Restart & Run All`
   - Or use keyboard shortcut: `Shift + Enter` for each cell

3. **Wait for Completion**
   - Data download: ~2-5 minutes
   - Model training: ~10-20 minutes per model
   - Total time: ~30-60 minutes depending on hardware

## Detailed Walkthrough

### Section-by-Section Guide

#### 1. Setup (Sections 1-2)
```python
# The notebook automatically:
# - Imports required libraries
# - Sets random seeds for reproducibility
# - Configures display settings
```

**What to check:**
- No import errors
- TensorFlow version compatibility
- Python version (3.8+)

#### 2. Data Collection (Section 3)
```python
# Downloads NASDAQ dataset from Kaggle
path = kagglehub.dataset_download("jacksoncrow/stock-market-dataset")
```

**Prerequisites:**
- Kaggle API credentials configured
- Internet connection
- ~1GB free disk space

**What you get:**
- Apple (AAPL) stock data
- 9,909 trading days (1980-2020)
- OHLCV data (Open, High, Low, Close, Volume)

#### 3. Data Analysis (Sections 4-7)

**Exploratory Data Analysis:**
- Price distribution histograms
- Correlation heatmaps
- Time series plots
- Volume analysis

**Statistical Testing:**
- Normality tests (Shapiro-Wilk, Jarque-Bera)
- Stationarity tests (Augmented Dickey-Fuller)
- Autocorrelation analysis

#### 4. Feature Engineering (Section 8)

**Technical Indicators Created:**

1. **RSI (Relative Strength Index)**
   - Default period: 14 days
   - Range: 0-100
   - Overbought: >70, Oversold: <30

2. **EMA (Exponential Moving Average)**
   - 12-day and 26-day EMAs
   - Trend following indicator

3. **MACD (Moving Average Convergence Divergence)**
   - MACD line, Signal line, Histogram
   - Momentum and trend indicator

4. **Bollinger Bands**
   - Middle band: 20-day SMA
   - Upper/Lower bands: ±2 standard deviations

#### 5. Model Training (Sections 9-11)

**Preprocessing:**
```python
# Sequence length (lookback period)
SEQUENCE_LENGTH = 60  # 60 days of historical data

# Train/Test split
TRAIN_SPLIT = 0.8  # 80% training, 20% testing
```

**Model Architectures:**

**Simple RNN:**
```python
model = Sequential([
    SimpleRNN(50, input_shape=(60, 1)),
    Dense(1)
])
```

**LSTM (Univariate):**
```python
model = Sequential([
    LSTM(100, return_sequences=True, input_shape=(60, 1)),
    Dropout(0.2),
    LSTM(50),
    Dropout(0.2),
    Dense(1)
])
```

**LSTM (Multivariate):**
```python
model = Sequential([
    LSTM(100, return_sequences=True, input_shape=(60, 4)),  # 4 features
    Dropout(0.2),
    LSTM(50),
    Dropout(0.2),
    Dense(1)
])
```

**Training Parameters:**
- Optimizer: Adam (learning rate: 0.001)
- Loss: Mean Squared Error (MSE)
- Epochs: 100 (with early stopping)
- Batch size: 32
- Validation split: 20%

#### 6. Evaluation (Sections 12-13)

**Metrics Calculated:**
- **RMSE**: Root Mean Squared Error (in dollars)
- **MAE**: Mean Absolute Error (average error)
- **MAPE**: Mean Absolute Percentage Error (%)
- **R²**: Coefficient of determination (0-1)
- **Direction Accuracy**: % of correct up/down predictions

**Visualizations:**
- Prediction vs Actual plots
- Error distribution histograms
- Scatter plots (Actual vs Predicted)
- Zoomed views for detail

#### 7. Future Forecasting (Section 14)

```python
# Predict next 30 days
FUTURE_DAYS = 30
future_predictions = predict_future(lstm_model, last_sequence, scaler_uni, FUTURE_DAYS)
```

**How it works:**
1. Takes last 60 days of data
2. Predicts next day
3. Adds prediction to sequence
4. Repeats for 30 days (recursive prediction)

## Customization Options

### Change the Stock Symbol

To analyze a different stock:

1. **Modify the stock symbol**
   ```python
   # In Section 3
   stock_symbol = 'AAPL'  # Change to 'GOOGL', 'MSFT', etc.
   ```

2. **Verify data availability**
   - Check if the stock exists in the dataset
   - Located in `stocks/` folder

### Adjust Model Parameters

**Sequence Length:**
```python
SEQUENCE_LENGTH = 60  # Try 30, 90, or 120
```

**Training Epochs:**
```python
EPOCHS = 100  # Increase to 150 or 200 for better training
```

**LSTM Units:**
```python
# Increase model capacity
LSTM(150, return_sequences=True)  # Instead of 100
LSTM(75)  # Instead of 50
```

**Dropout Rate:**
```python
Dropout(0.3)  # Increase from 0.2 to prevent overfitting
```

### Modify Technical Indicators

**RSI Period:**
```python
rsi_period = 14  # Try 9 or 21
df['RSI'] = calculate_rsi(df['Close'], period=rsi_period)
```

**EMA Periods:**
```python
ema_short = 12  # Try 10 or 15
ema_long = 26   # Try 20 or 30
```

**MACD Parameters:**
```python
df['MACD'] = df['EMA_12'] - df['EMA_26']
df['MACD_Signal'] = df['MACD'].ewm(span=9).mean()  # Try span=10 or 12
```

### Change Train/Test Split

```python
TRAIN_SPLIT = 0.8  # Try 0.7 or 0.9
```

## Understanding the Output

### Model Performance Interpretation

**Good Performance Indicators:**
- Low RMSE and MAE (relative to stock price)
- High R² score (closer to 1.0)
- Low MAPE (under 5-10%)
- Direction accuracy > 50%

**Example:**
```
Model: LSTM (Univariate)
RMSE: 5.23    # Average error of ~$5.23
MAE: 3.87     # Absolute average error of ~$3.87
MAPE: 2.14%   # Average error of 2.14%
R²: 0.987     # Explains 98.7% of variance
```

### Prediction Plots

**What to look for:**
- **Prediction lag**: Predictions following actual with delay
- **Trend capture**: Model following overall trends
- **Outlier handling**: Performance during sudden changes
- **Convergence**: Predictions getting closer over time

### Training History

**Loss Curves:**
- Training loss should decrease
- Validation loss should follow training loss
- Gap indicates overfitting

**Good Training:**
```
Both losses decrease smoothly
Small gap between train and validation
Early stopping kicks in appropriately
```

**Overfitting Signs:**
```
Training loss very low
Validation loss remains high or increases
Large gap between the two
```

## Troubleshooting

### Common Issues

#### 1. Kaggle API Error
**Problem:** `OSError: Could not find kaggle.json`

**Solution:**
```bash
# Place kaggle.json in correct location
mkdir -p ~/.kaggle
cp path/to/kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json
```

#### 2. Memory Error
**Problem:** `MemoryError` during training

**Solutions:**
- Reduce batch size: `batch_size=16`
- Reduce sequence length: `SEQUENCE_LENGTH=30`
- Use smaller model: fewer LSTM units
- Close other applications

#### 3. Slow Training
**Problem:** Training takes too long

**Solutions:**
- Use GPU if available (TensorFlow should detect automatically)
- Reduce epochs: `EPOCHS=50`
- Increase batch size: `batch_size=64`
- Reduce model complexity

#### 4. Poor Predictions
**Problem:** Model predictions are inaccurate

**Solutions:**
- Check data quality (missing values, outliers)
- Increase sequence length for more context
- Try different features
- Adjust model architecture
- Increase training epochs
- Reduce learning rate

#### 5. Import Errors
**Problem:** `ModuleNotFoundError`

**Solution:**
```bash
pip install -r requirements.txt
# Or install specific package
pip install tensorflow
```

## Advanced Usage

### GPU Acceleration

**Check GPU availability:**
```python
import tensorflow as tf
print("GPU Available:", tf.config.list_physical_devices('GPU'))
```

**Configure GPU memory:**
```python
gpus = tf.config.experimental.list_physical_devices('GPU')
if gpus:
    tf.config.experimental.set_memory_growth(gpus[0], True)
```

### Hyperparameter Tuning

**Grid search example:**
```python
sequence_lengths = [30, 60, 90]
lstm_units = [50, 100, 150]

for seq_len in sequence_lengths:
    for units in lstm_units:
        # Train model with these parameters
        # Evaluate performance
        # Save best configuration
```

### Ensemble Methods

**Combine multiple models:**
```python
# Average predictions from all models
ensemble_pred = (rnn_pred + lstm_pred + lstm_multi_pred) / 3

# Weighted average
ensemble_pred = 0.2 * rnn_pred + 0.3 * lstm_pred + 0.5 * lstm_multi_pred
```

### Save and Load Models

**Save trained model:**
```python
lstm_model.save('saved_models/lstm_model.h5')
```

**Load model:**
```python
from tensorflow.keras.models import load_model
loaded_model = load_model('saved_models/lstm_model.h5')
```

### Export Results

**Save predictions to CSV:**
```python
results_df = pd.DataFrame({
    'Date': test_dates,
    'Actual': lstm_actual,
    'Predicted': lstm_pred,
    'Error': lstm_actual - lstm_pred
})
results_df.to_csv('predictions.csv', index=False)
```

### Batch Processing

**Analyze multiple stocks:**
```python
stocks = ['AAPL', 'GOOGL', 'MSFT', 'AMZN']
results = {}

for stock in stocks:
    # Load data for stock
    # Train model
    # Evaluate
    results[stock] = metrics
```

## Best Practices

1. **Always run with reproducible seeds**
   - Ensures consistent results
   - Helps with debugging

2. **Monitor training progress**
   - Watch for overfitting
   - Use early stopping

3. **Validate assumptions**
   - Check data quality
   - Verify statistical properties

4. **Document experiments**
   - Keep track of hyperparameters
   - Note what works and what doesn't

5. **Use version control**
   - Commit working versions
   - Track changes systematically

## Performance Tips

1. **Data Processing:**
   - Load data once, reuse
   - Cache preprocessed data
   - Use efficient data structures

2. **Model Training:**
   - Start with smaller models
   - Gradually increase complexity
   - Use callbacks (EarlyStopping, ReduceLROnPlateau)

3. **Memory Management:**
   - Clear variables when done: `del large_variable`
   - Use generators for large datasets
   - Monitor memory usage

4. **Computational Efficiency:**
   - Use vectorized operations
   - Leverage NumPy broadcasting
   - Profile code to find bottlenecks

## Additional Resources

- TensorFlow Documentation: https://www.tensorflow.org/
- Keras Documentation: https://keras.io/
- Technical Analysis: https://www.investopedia.com/
- Time Series Forecasting: https://otexts.com/fpp2/

## Getting Help

If you encounter issues:

1. Check this usage guide
2. Review the README.md
3. Search existing GitHub issues
4. Create a new issue with:
   - Error message
   - Steps to reproduce
   - Environment details (Python version, OS)
   - Relevant code snippets

---

**Happy Forecasting!**
