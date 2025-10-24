# Stock Market Trend Prediction Using LSTM

## Overview
This project predicts the trend for the upcoming 5 candles in stock market data as one of three classes: Uptrend, Downtrend, or Neutral. The model uses historical price and technical indicators processed with an LSTM deep learning architecture.

## Step-by-Step Instructions to Run

1. **Dependencies**  
   Install the required Python libraries

2. **Dataset Upload**  
- Upload the `large_32.csv` dataset file to your working directory or Google Colab environment.
- Ensure it is accessible at the path used in the code, or modify the path accordingly.

3. **Execution Order**  
Run the notebook cells in the following order:
- Data Loading and Inspection
- Label Generation (creating 5-candle trend labels)
- Feature Normalization
- Sequence Creation (windowing data for LSTM input)
- Train/Validation/Test Split (time series-aware)
- Model Building: LSTM definition
- Model Training with validation monitoring
- Training Metrics Visualization
- Model Evaluation on test set including confusion matrix
- Trend Prediction Visualization (color-coded line plot)

---

## Assumptions

- The future trend label for each sample is defined by the next **5 consecutive candles**:  
- *Uptrend*: All 5 candles have Close > Open  
- *Downtrend*: All 5 candles have Close < Open  
- *Neutral*: Any other mixed cases

- The last 5 rows in the dataset cannot be labeled due to insufficient lookahead; these rows are dropped.

- The time-series nature of data is preserved: no shuffling during train/test splits.

- Window length for LSTM input is 30 by default; can be adjusted for capturing relevant historical context.

---

## Non-Standard Techniques Used

- **Custom Label Generation**: Programmatic multi-step lookahead label creation based on price action.

- **LSTM Deep Learning Model**: Captures temporal dependencies in the price and technical features.

- **Sequence Windowing**: Creates 3D input tensors required by LSTMs.

- **Trend Visualization**: Color-coded line plot mapping predictions to trend types for intuitive interpretation.

No additional data augmentation techniques or custom loss functions were used in this version.

## Insights and Challenges

- Handling time-series data requires careful splitting to avoid data leakage.

- Labeling multi-step trends posed a challenge in defining clear classes with real market noise.

- Model performance depends heavily on feature quality and window size; hyperparameter tuning is recommended.

- Future improvements may include Transformer-based architectures, advanced feature engineering, and ensemble models.

## Suggestions for Improvements

- Experiment with variable window lengths or bidirectional LSTMs for richer context.

- Explore attention mechanisms to weigh important past candles.

- Use external data sources or news sentiment for multi-modal prediction.

- Implement more granular trend classifications or regression for continuous price movement prediction.
