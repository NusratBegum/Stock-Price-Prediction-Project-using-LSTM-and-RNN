# Stock Price Prediction using LSTM and RNN

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)](https://www.tensorflow.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)

A comprehensive deep learning project that uses Recurrent Neural Networks (RNN) and Long Short-Term Memory (LSTM) networks to predict stock prices based on historical data and technical indicators.

## Project Overview

This project demonstrates the application of deep learning techniques for time series forecasting in financial markets. It predicts future stock closing prices using historical price data and technical indicators such as RSI, EMA, MACD, and Bollinger Bands.

### Key Features

- **Multiple Model Architectures**: Implementation of Simple RNN, Univariate LSTM, and Multivariate LSTM models
- **Comprehensive Data Analysis**: In-depth exploratory data analysis with statistical testing
- **Technical Indicators**: Integration of RSI, EMA, MACD, and Bollinger Bands
- **Rigorous Evaluation**: Multiple metrics including RMSE, MAE, MAPE, R², and direction accuracy
- **Future Forecasting**: Recursive prediction for next 30 days
- **Interactive Visualizations**: Rich matplotlib and seaborn visualizations

## Dataset

- **Source**: [NASDAQ Stock Market Dataset](https://www.kaggle.com/datasets/jacksoncrow/stock-market-dataset) from Kaggle
- **Stock Analyzed**: Apple Inc. (AAPL)
- **Time Period**: 1980-12-12 to 2020-04-01 (9,909 trading days)
- **Features**: Open, High, Low, Close, Adjusted Close, Volume

## Getting Started

> **Quick Start**: Want to get running fast? See [QUICKSTART.md](QUICKSTART.md) for a 5-minute setup guide!

### Prerequisites

- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- Kaggle API credentials (for dataset download)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/NusratBegum/Stock-Price-Prediction-Project-using-LSTM-and-RNN.git
   cd Stock-Price-Prediction-Project-using-LSTM-and-RNN
   ```

2. **Install required packages**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up Kaggle API** (for dataset download)
   - Create a Kaggle account at [kaggle.com](https://www.kaggle.com)
   - Go to Account Settings → API → Create New API Token
   - This downloads `kaggle.json` file
   - Place it in `~/.kaggle/` directory (Linux/Mac) or `C:\Users\<Username>\.kaggle\` (Windows)
   - Set permissions: `chmod 600 ~/.kaggle/kaggle.json` (Linux/Mac)

4. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook main.ipynb
   ```

## Notebook Structure

The project is organized into 16 comprehensive sections:

| Section | Description |
|---------|-------------|
| **1. Project Overview** | Problem statement, objectives, and success metrics |
| **2. Setup & Import** | Library imports and environment configuration |
| **3. Data Collection** | Download and explore NASDAQ dataset |
| **4. Data Understanding** | Feature types and statistical properties |
| **5. Data Quality** | Missing values and data integrity checks |
| **6. EDA** | Exploratory data analysis with visualizations |
| **7. Hypothesis Testing** | Statistical tests for normality and stationarity |
| **8. Feature Engineering** | Technical indicators (RSI, EMA, MACD, Bollinger Bands) |
| **9. Preprocessing** | Data scaling and sequence creation |
| **10. Model Theory** | RNN and LSTM architecture explanations |
| **11. Model Development** | Building and training three models |
| **12. Model Evaluation** | Performance comparison using multiple metrics |
| **13. Prediction Analysis** | Visualizing predictions vs actual prices |
| **14. Future Forecasting** | 30-day recursive prediction |
| **15. Limitations** | Discussion of challenges and constraints |
| **16. Conclusions** | Key findings and recommendations |

## Models Implemented

### 1. Simple RNN
- Basic recurrent architecture
- Single RNN layer with 50 units
- Baseline model for comparison

### 2. Univariate LSTM
- Single feature input (Close price)
- Two LSTM layers (100 and 50 units)
- Dropout regularization
- Early stopping and learning rate reduction

### 3. Multivariate LSTM
- Multiple features (Close, RSI, EMA, MACD)
- Two LSTM layers (100 and 50 units)
- Dropout regularization
- Bidirectional option available

## Model Performance

Example performance metrics on test data:

| Model | RMSE | MAE | MAPE (%) | R² Score |
|-------|------|-----|----------|----------|
| Simple RNN | X.XX | X.XX | X.XX | X.XXX |
| LSTM (Univariate) | X.XX | X.XX | X.XX | X.XXX |
| LSTM (Multivariate) | X.XX | X.XX | X.XX | X.XXX |

*Note: Actual values will be generated when you run the notebook*

## Technical Indicators

The project implements several technical indicators:

- **RSI (Relative Strength Index)**: Momentum indicator measuring overbought/oversold conditions
- **EMA (Exponential Moving Average)**: Trend-following indicator
- **MACD (Moving Average Convergence Divergence)**: Trend and momentum indicator
- **Bollinger Bands**: Volatility indicator with upper/lower bands

## Visualizations

The notebook includes various visualizations:

- Historical price trends
- Volume analysis
- Technical indicator plots
- Correlation heatmaps
- Training history curves
- Prediction vs actual comparisons
- Error distribution analysis
- Future price forecasts

## Important Disclaimer

**This project is for EDUCATIONAL PURPOSES ONLY.**

- Past performance does NOT guarantee future results
- Stock markets are inherently unpredictable
- These models should NOT be used for actual trading decisions
- Always consult financial professionals for investment advice
- Markets can be influenced by unpredictable external factors

## Learning Outcomes

This project demonstrates:

1. **Data Science Workflow**: Complete pipeline from data collection to model deployment
2. **Time Series Analysis**: Understanding sequential data patterns
3. **Deep Learning**: Practical implementation of RNN and LSTM architectures
4. **Feature Engineering**: Creating meaningful technical indicators
5. **Model Evaluation**: Comprehensive performance assessment
6. **Financial Markets**: Understanding stock price dynamics

## Methodology

### Data Preprocessing
1. Load historical stock data
2. Check for missing values and outliers
3. Create technical indicators
4. Normalize features using MinMax scaling
5. Create sequences for time series modeling

### Model Training
1. Split data into train/test sets (80/20)
2. Create 60-day sequences
3. Train models with early stopping
4. Monitor validation loss for overfitting

### Evaluation
1. Calculate regression metrics (RMSE, MAE, MAPE, R²)
2. Analyze prediction lag
3. Compare direction accuracy
4. Visualize predictions

## Dependencies

Main libraries used:

- **NumPy**: Numerical computing
- **Pandas**: Data manipulation
- **Matplotlib & Seaborn**: Visualization
- **TensorFlow/Keras**: Deep learning framework
- **Scikit-learn**: Preprocessing and metrics
- **SciPy**: Statistical analysis
- **KaggleHub**: Dataset download

See `requirements.txt` for complete list with versions.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Nusrat Begum**

- GitHub: [@NusratBegum](https://github.com/NusratBegum)

## Acknowledgments

- Dataset: [NASDAQ Stock Market Dataset](https://www.kaggle.com/datasets/jacksoncrow/stock-market-dataset) by Jackson Crow on Kaggle
- Inspiration: Financial time series forecasting research
- TensorFlow/Keras documentation and tutorials

## Documentation

Complete documentation is available:

- **[QUICKSTART.md](QUICKSTART.md)**: Get up and running in 5 minutes
- **[SETUP.md](SETUP.md)**: Detailed installation guide for all platforms
- **[USAGE.md](USAGE.md)**: Comprehensive usage instructions and examples
- **[CONTRIBUTING.md](CONTRIBUTING.md)**: Guidelines for contributing to the project
- **[CHANGELOG.md](CHANGELOG.md)**: Project version history and changes

## Contact

For questions or feedback, please open an issue in this repository.

## Future Enhancements

Potential improvements for this project:

- [ ] Implement Transformer models for better long-range dependencies
- [ ] Add sentiment analysis from financial news and social media
- [ ] Incorporate macroeconomic indicators (GDP, interest rates, inflation)
- [ ] Develop ensemble methods combining multiple models
- [ ] Create a web dashboard for interactive predictions
- [ ] Implement trading strategy backtesting
- [ ] Add more stocks for comparative analysis
- [ ] Explore reinforcement learning for automated trading

## References

- Hochreiter, S., & Schmidhuber, J. (1997). Long Short-Term Memory. Neural Computation.
- Graves, A. (2012). Supervised Sequence Labelling with Recurrent Neural Networks.
- Technical Analysis literature on RSI, MACD, and other indicators
- TensorFlow documentation: https://www.tensorflow.org/
- Financial market analysis resources

---

**Note**: This is an academic project demonstrating machine learning techniques. Stock market prediction is extremely challenging, and real-world trading involves many factors not captured by these models. Always perform due diligence and consult professionals before making investment decisions.
