# Artificial Neural Network (ANN)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1PJyq1qkVigJ0Eps7w-9UHQhLPsKuO-Y5)

## Project Overview

This repository contains a Google Colab project (`ANN_SDP.ipynb`) that builds, trains, evaluates, and visualizes an Artificial Neural Network (ANN) for handwritten digit classification using TensorFlow/Keras.

## Objective

Classify grayscale handwritten digit images (0–9) from the MNIST dataset using a sequential feedforward neural network.

## Repository Structure

```text
ANN/
├── ANN_SDP.ipynb       # Google Colab notebook with code and preserved outputs
├── README.md           # Project documentation
├── requirements.txt    # Required Python packages
└── .gitignore          # Git ignore rules for Python and Jupyter
```

## Technologies and Libraries Used

- **Python 3**
- **TensorFlow** (`2.21.0` in the Colab run) / `tf.keras`
- **NumPy**
- **Matplotlib**

## Dataset Information

The notebook loads the **MNIST** dataset directly via `tf.keras.datasets.mnist.load_data()`:

- **Training set:** `60,000` images of shape `(28, 28)` and `60,000` labels
- **Testing set:** `10,000` images of shape `(28, 28)` and `10,000` labels
- **Classes:** 10 handwritten digit classes (`0` through `9`)

## Workflow and Implementation Steps

1. **Import Libraries:** Load `tensorflow`, `numpy`, and `matplotlib.pyplot`.
2. **Load Dataset:** Load MNIST training and test splits via `tf.keras.datasets.mnist.load_data()`.
3. **Sample Visualization:** Display the first training image (`x_train[0]`) in grayscale.
4. **Preprocessing:** Normalize pixel values to `float32` in the range `[0.0, 1.0]` by dividing by `255.0`.
5. **Model Architecture:** Build a `tf.keras.models.Sequential` model with:
   - `Flatten(input_shape=(28, 28))` → output shape `(None, 784)`, `0` parameters
   - `Dense(128, activation='relu')` → output shape `(None, 128)`, `100,480` parameters
   - `Dense(10, activation='softmax')` → output shape `(None, 10)`, `1,290` parameters
   - **Total parameters:** `101,770` (all trainable)
6. **Compilation:** Compile with `optimizer='adam'`, `loss='sparse_categorical_crossentropy'`, and `metrics=['accuracy']`.
7. **Training:** Train for `5` epochs with `batch_size=32` and `validation_split=0.2`.
8. **Evaluation & Prediction:** Evaluate on the test set (`x_test`, `y_test`), print predicted vs. actual labels for the first 5 test samples, and plot a `2x5` grid of predictions for the first 10 test images.

## Model Training

Training configuration:
- **Epochs:** `5`
- **Batch size:** `32`
- **Validation split:** `0.2` (`1,500` steps per epoch)

Recorded metrics at **Epoch 5/5**:
- **Training Accuracy:** `0.9987`
- **Training Loss:** `0.0043`
- **Validation Accuracy:** `0.9875`
- **Validation Loss:** `0.0411`

## Evaluation Metrics and Results

Evaluated on the `10,000`-sample test set (`313` batches):
- **Test Accuracy:** `97.59%` (`97.58999943733215 %`)
- **Test Loss:** `0.1098` (printed in the notebook as `10.976509749889374 %`)

Sample predictions on the first 5 test images all matched the ground truth labels (`7`, `2`, `1`, `0`, `4`).

## How to Run the Project Using Google Colab

1. Click the **Open in Colab** badge above or open [ANN_SDP.ipynb](https://colab.research.google.com/drive/1PJyq1qkVigJ0Eps7w-9UHQhLPsKuO-Y5) directly in Google Colab (or upload `ANN_SDP.ipynb` from this repository to Colab).
2. Run the cells sequentially from top to bottom (`Runtime` → `Run all`).

To run locally instead:

```bash
pip install -r requirements.txt
jupyter notebook ANN_SDP.ipynb
```
