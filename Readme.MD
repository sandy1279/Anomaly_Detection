# Intrusion Detection using LSTM

## Overview
This project implements an Intrusion Detection System (IDS) using a Long Short-Term Memory (LSTM) neural network. It processes the UNSW-NB15 dataset to classify network traffic as either normal (0) or attack (1).

## Dataset
The dataset used is **UNSW-NB15**, which consists of normal and malicious network traffic data. It is split into training and testing sets.

- **Training Data:** `UNSW_NB15_training-set.parquet`
- **Testing Data:** `UNSW_NB15_testing-set.parquet`

## Installation
Ensure you have the necessary dependencies installed:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn tensorflow
```
For handling parquet files:
```bash
pip install pyarrow fastparquet
```

## Preprocessing Steps
1. **Data Loading:** Merges training and testing datasets.
2. **Handling Missing Data:** Checks for null and empty values.
3. **Duplicate Removal:** Drops duplicate rows.
4. **Categorical Encoding:** Encodes categorical columns using `LabelEncoder`.
5. **Class Balancing:** Uses `SMOTE` to handle class imbalance.
6. **Feature Scaling:** Standardizes selected features using `StandardScaler`.
7. **Data Reshaping:** Converts features into a 3D format for LSTM.

## Model Architecture
The LSTM model consists of:
- **LSTM Layer 1:** 64 units, `return_sequences=True`
- **Dropout Layer:** 20% to reduce overfitting
- **LSTM Layer 2:** 32 units, `return_sequences=False`
- **Dense Layer:** 16 neurons with ReLU activation
- **Output Layer:** 1 neuron with Sigmoid activation for binary classification
- **Optimizer:** Adam
- **Loss Function:** Binary Cross-Entropy

## Training
- **Epochs:** 10
- **Batch Size:** 64
- **Validation Split:** 20%

## Evaluation Metrics
The model is evaluated using:
- **Accuracy**
- **Precision, Recall, F1-score** (from `classification_report`)
- **Confusion Matrix**

## Results
Example classification report:
```
              precision    recall  f1-score   support

         0.0       0.97      0.73      0.84     15993
         1.0       0.79      0.98      0.87     15993

    accuracy                           0.86     31986
   macro avg       0.88      0.86      0.86     31986
weighted avg       0.88      0.86      0.86     31986
```
- The model detects attacks well but has some false alarms.
- Improvements can be made using **BiLSTM, CNN-LSTM, or threshold tuning**.

## Future Improvements
- **Hyperparameter tuning** (learning rate, batch size, LSTM units)
- **Alternative architectures** (BiLSTM, CNN-LSTM, Transformer-based models)
- **Feature engineering** (using domain knowledge to select better features)

## Usage
Run the script in a Python environment:
```bash
python notebook.py
```
Modify hyperparameters and dataset paths as needed.

## License
This project is for educational purposes and follows an open-source license.

