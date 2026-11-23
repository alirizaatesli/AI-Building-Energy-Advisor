
# AI Building Energy Advisor

**MTH4800 – Innovation Campus Artificial Intelligence**

**Group 14 | Assignment 1 & Assignment 2**

## Project Overview

AI Building Energy Advisor is a machine learning project that investigates how architectural characteristics relate to the heating and cooling loads of residential buildings.

The project aims to predict simulated heating and cooling loads from building design features, compare different machine learning approaches, and evaluate their ability to generalize to previously unseen building geometries.

The study relates to **UN Sustainable Development Goal 7 (Affordable and Clean Energy)** and **Goal 13 (Climate Action)**.

**Project scope:** This is a research prototype using simulated building data. It does not predict actual electricity bills, measured energy consumption, guaranteed energy savings, or carbon emissions reductions.

## Project Progress

| Assignment | Focus | Status |
|---|---|---|
| Assignment 1 | Project selection, exploratory data analysis, and initial model evaluation | Completed |
| Assignment 2 | Extended model evaluation, cross-validation, geometry-aware validation, and Istanbul climate analysis | Completed |

## Dataset

The project uses the **UCI Energy Efficiency Dataset**.

- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/242/energy+efficiency)
- **Observations:** 768 simulated building configurations
- **Input features:** 8 architectural characteristics
- **Prediction targets:** Heating Load and Cooling Load
- **Missing values:** 0
- **Base geometries:** 12, with 64 configurations per geometry

### Input Features

1. Relative Compactness
2. Surface Area
3. Wall Area
4. Roof Area
5. Overall Height
6. Orientation
7. Glazing Area
8. Glazing Area Distribution

The dataset represents simulated configurations rather than real-world building energy bills.

## Assignment 1: Exploratory Data Analysis & Initial Models

**Notebook:** [Assignment_1.ipynb](Assignment_1.ipynb)

Assignment 1 established the foundation of the project through:

- Data loading and quality assessment
- Descriptive statistics
- Heating and cooling load distributions
- Correlation analysis
- Exploratory visualizations
- Initial Linear Regression and Random Forest experiments
- Actual vs. predicted comparisons

## Assignment 2: Model Exploration & Results

**Notebook:** [Assignment_2.ipynb](Assignment_2.ipynb)

Assignment 2 extended the initial work to investigate the reliability and generalization performance of the machine learning models.

### Methodology

Two regression approaches were evaluated:

- **Linear Regression:** An interpretable baseline model.
- **Random Forest Regressor:** A nonlinear ensemble model using 200 decision trees.

The initial experiment used an **80/20 train-test split** with `random_state=42`.

Model performance was evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Coefficient of Determination (R²)

### Initial Test Results

| Model | Target | MAE | RMSE | R² |
|---|---|---:|---:|---:|
| Linear Regression | Heating Load | 2.1820 | 3.0254 | 0.9122 |
| Linear Regression | Cooling Load | 2.1953 | 3.1454 | 0.8932 |
| Random Forest | Heating Load | 0.3477 | 0.4975 | 0.9976 |
| Random Forest | Cooling Load | 1.1664 | 1.9062 | 0.9608 |

Random Forest achieved lower errors and higher R² values for both targets under the initial random train-test split.

### Cross-Validation

To examine model reliability, the following validation methods were applied:

1. **Random 5-Fold Cross-Validation:** Evaluates performance across five randomly partitioned folds.
2. **Geometry-Aware 4-Fold GroupKFold:** Keeps configurations from the same base geometry together during validation.
3. **Leave-One-Geometry-Out (LOGO):** Evaluates models on each previously unseen base geometry.

### Geometry-Aware Validation Results

The following results were obtained using 4-fold GroupKFold across the complete dataset.

| Model | Target | Mean MAE | Mean R² |
|---|---|---:|---:|
| Linear Regression | Heating Load | 4.1055 | 0.6232 |
| Linear Regression | Cooling Load | 4.5395 | 0.5246 |
| Random Forest | Heating Load | 4.2673 | 0.4703 |
| Random Forest | Cooling Load | 5.0804 | 0.4055 |

Performance decreased considerably when previously unseen building geometries were used for validation.

Under this evaluation strategy, Linear Regression achieved lower mean MAE and higher mean R² than Random Forest for both targets.

### Feature Importance & Design Analysis

Additional investigations included:

- Random Forest feature importance analysis
- Relationships between glazing area and heating/cooling loads
- Relationships between orientation and heating/cooling loads
- Identification of important architectural predictors

Relative Compactness was among the leading predictors. Overall Height, Surface Area, and Roof Area also contributed to the models.

These findings describe patterns within the dataset and should not be interpreted as causal effects.

### Istanbul Climate Analysis

A separate climate analysis was conducted using the **Istanbul Atatürk Airport TMYx 2009–2023 EPW weather file**.

- **Hourly weather records:** 8,760
- **January mean temperature:** 7.48 °C
- **August mean temperature:** 26.41 °C
- **Highest monthly solar irradiation:** Approximately 214.2 kWh/m² in July

**Important:** The Istanbul weather data were not used to train or validate the current machine learning models. No EnergyPlus simulation has been performed as part of the completed analysis.

### Key Findings

The main research finding is that strong performance under random validation does not necessarily translate into equally strong performance on previously unseen building geometries.

Although Random Forest performed very well under random splitting, geometry-aware validation exposed substantially larger prediction errors.

This highlights the importance of selecting validation strategies that reflect the intended generalization task.

## How to Run

### Assignment 1

1. Open [Assignment_1.ipynb](Assignment_1.ipynb) in Google Colab.
2. Download the Energy Efficiency dataset from the source above.
3. Run the notebook cells in order.
4. Upload the CSV file when prompted.
5. Review the exploratory analysis and initial model results.

### Assignment 2

1. Open [Assignment_2.ipynb](Assignment_2.ipynb) in Google Colab.
2. Prepare the dataset file named `energy_efficiency_data.csv`.
3. Run the notebook cells sequentially.
4. Upload the CSV file when prompted.
5. Upload the Istanbul Atatürk Airport TMYx 2009–2023 EPW weather file when prompted.
6. Review the model evaluations, validation experiments, design analyses, and climate visualizations.

The notebook uses manual file uploads. Running the analysis requires access to the original dataset and the separate EPW weather file.

## Limitations

- The dataset consists of simulated building configurations rather than measured building energy consumption.
- It contains only 12 distinct base building geometries.
- Random train-test performance can be overly optimistic for generalization to unseen geometries.
- The models have not been validated using real building measurements.
- Predictions should not be treated as actual electricity bills or guaranteed energy savings.
- The Istanbul climate analysis is separate from the machine learning model training.

## Future Development

Potential next steps include:

- Generating additional Istanbul-specific building simulations using EnergyPlus and EPW weather data.
- Evaluating controlled changes in glazing ratio and building orientation.
- Improving generalization to previously unseen geometries.
- Investigating validation using measured building data.
- Exploring an interactive application for heating and cooling load predictions.

Future assignments will follow their respective official requirements.

## Team — Group 14

- Ayşe Canan Çalışkan
- Tuğba Karademir
- Ali Rıza Ateşli
- Ebubekir Diker

## References

1. Tsanas, A., & Xifara, A. (2012). Accurate quantitative estimation of energy performance of residential buildings using statistical machine learning tools. *Energy and Buildings, 49*, 560–567. https://doi.org/10.1016/j.enbuild.2012.03.003
2. [UCI Energy Efficiency Dataset](https://doi.org/10.24432/C51307)
3. [Climate.OneBuilding — TMYx Weather Data](https://climate.onebuilding.org/)
