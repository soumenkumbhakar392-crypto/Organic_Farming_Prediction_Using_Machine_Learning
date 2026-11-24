# 🌱 Organic Farming Suitability Prediction

A machine-learning project that predicts whether agricultural land is suitable for organic farming using soil and environmental parameters.

## Project Overview

This project demonstrates how a **Random Forest Classifier** can be used to classify land as:

- **Suitable**
- **Not Suitable**

The prediction is based on five input features:

| Feature | Description | Synthetic data range used |
|---|---|---:|
| `Soil_pH` | Soil acidity/alkalinity | 4.5–9.0 |
| `Temperature` | Temperature in °C | 15–40 |
| `Rainfall` | Rainfall in mm | 200–1500 |
| `Humidity` | Relative humidity in % | 30–95 |
| `Soil_Moisture` | Soil moisture in % | 10–90 |

> **Important:** The notebook creates 500 synthetic sample records. Its suitability labels are generated from illustrative threshold rules, not from field measurements or expert-verified agronomic data. Treat the model as an educational demonstration, not as a real-world farming or land-use recommendation.

## Objectives

- Develop a machine-learning-based organic farming suitability predictor.
- Explore soil and environmental conditions.
- Visualize feature distributions and suitability classes.
- Train and evaluate a Random Forest model.
- Demonstrate predictions using manual inputs and an interactive notebook form.

## Technologies and Libraries

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- IPyWidgets

## Repository Contents

```text
.
├── Organic_Farming_Prediction.ipynb
└── README.md
```

## How the Project Works

1. **Generate the dataset:** Create 500 records with randomly generated soil and environmental values. A fixed NumPy seed (`42`) makes the generated data reproducible.
2. **Create target labels:** Assign `Suitable` when all of the following conditions are met:
   - Soil pH is between 6.0 and 7.5.
   - Temperature is between 18°C and 32°C.
   - Rainfall is between 500 mm and 1200 mm.
   - Humidity is between 40% and 85%.
   - Soil moisture is between 30% and 75%.

   Otherwise, assign `Not Suitable`.
3. **Preprocess the data:** Inspect dataset information, missing values, duplicate rows, and descriptive statistics; remove duplicate rows.
4. **Prepare features and target:** Use the five environmental columns as `X` and `Suitability` as `y`.
5. **Split the data:** Use an 80% training / 20% testing split with `random_state=42` and stratification.
6. **Visualize the data:** Plot distributions for the input features and compare suitability class counts.
7. **Train the model:** Fit a `RandomForestClassifier` with 100 trees and `random_state=42`.
8. **Evaluate the model:** Review accuracy, the classification report, and a confusion matrix.
9. **Train a class-weighted model:** Train another Random Forest using `class_weight='balanced'`, then evaluate it using the same types of metrics.
10. **Make predictions:** Enter values manually or use the IPyWidgets form in the notebook.

## Installation

Make sure Python 3 and Jupyter Notebook or JupyterLab are installed.

Install the required libraries:

```bash
pip install pandas numpy matplotlib scikit-learn ipywidgets notebook
```

For JupyterLab, ensure that your IPyWidgets installation is supported by your JupyterLab version.

## Run the Notebook

1. Clone or download this repository.
2. Open a terminal in the project directory.
3. Start Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open `Organic_Farming_Prediction.ipynb`.
5. Run the notebook cells **from top to bottom** so that the dataset, train/test split, trained model, and widget controls are created before prediction.

The interactive form uses IPyWidgets and must be run in a notebook environment that supports widget rendering. If widgets do not appear, use the manual-input prediction cell or check your Jupyter/IPyWidgets setup.

## Model and Evaluation

The notebook first trains a standard Random Forest model and evaluates it with:

- Accuracy
- Precision, recall, and F1-score (classification report)
- Confusion matrix

It then trains a second Random Forest with `class_weight='balanced'` to account for class imbalance and repeats the evaluation.

The notebook prints the actual evaluation results when run. No fixed accuracy figure is stated here because the results should be taken from the execution environment.

## Making a Prediction

The notebook accepts these values:

1. Soil pH
2. Temperature (°C)
3. Rainfall (mm)
4. Humidity (%)
5. Soil moisture (%)

The trained model returns either `Suitable` or `Not Suitable`. The notebook includes both a console-input example and an IPyWidgets-based input form.

## Limitations

- The dataset is synthetic and generated from the same threshold rules used to create the target labels.
- The model may learn those artificial rules rather than real agricultural relationships.
- The feature ranges and suitability thresholds are illustrative and are not universal recommendations.
- The notebook does not account for other factors such as soil texture, nutrients, slope, drainage, crop type, local climate patterns, pests, or land-management history.
- Predictions should not be used as the sole basis for agricultural decisions.

For practical deployment, replace the generated data with representative, validated field data; consult local agronomic expertise; and validate the model on independent real-world observations.

## Future Improvements

- Use real soil-test and weather datasets.
- Add soil nutrients (such as nitrogen, phosphorus, and potassium), soil texture, drainage, and crop-specific requirements.
- Apply cross-validation and hyperparameter tuning.
- Compare Random Forest with other classification algorithms.
- Add input validation and clearer feedback for out-of-range values.
- Evaluate the model on an independent real-world test dataset.

## License

No license is specified in this project. Add a `LICENSE` file if you intend to distribute or reuse the project under particular terms.
