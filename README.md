# AI Building Energy Advisor

**MTH4800 – Innovation Campus Artificial Intelligence**

**Group 14 – Assignment 1 & Assignment 2: AI Building Energy Advisor**

## Project Overview

AI Building Energy Advisor is a machine learning project designed to estimate the heating and cooling loads of residential building configurations using architectural characteristics.

The project supports **UN Sustainable Development Goal 7 (Affordable and Clean Energy)** and **Goal 13 (Climate Action)** by exploring how building design characteristics relate to energy efficiency.

## Dataset

- **Dataset:** Energy Efficiency Data Set
- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/242/energy+efficiency)
- **Records:** 768
- **Input Features:** 8 architectural characteristics
- **Target Variables:** Heating Load and Cooling Load
- **Missing Values:** 0

The dataset contains simulated building configurations rather than real-world electricity bills.

## Exploratory Data Analysis

The Google Colab notebook includes:

- Data quality and missing-value analysis
- Descriptive statistics
- Heating and cooling load distributions
- Correlation analysis
- Relationships between building characteristics and energy loads
- Actual vs. predicted visualizations

## Machine Learning Models

Two models were evaluated using an 80/20 train-test split:

1. Linear Regression
2. Random Forest Regressor

### Initial Results

| Model | Target | MAE | R² |
|---|---|---:|---:|
| Linear Regression | Heating Load | 2.1820 | 0.9122 |
| Linear Regression | Cooling Load | 2.1953 | 0.8932 |
| Random Forest | Heating Load | 0.3477 | 0.9976 |
| Random Forest | Cooling Load | 1.1664 | 0.9608 |

Random Forest achieved lower prediction errors and higher R² scores on both targets in the initial experiment.

## How to Run

1. Open [Assignment 1 Notebook](Assignment_1.ipynb) in Google Colab.
2. Download the Energy Efficiency dataset from the source above.
3. Run the notebook cells.
4. Upload the CSV file when prompted.
5. Review the EDA visualizations and model results.

### Running Assignment 2

1. Open [Assignment 2 Notebook](Assignment_2.ipynb) in Google Colab.
2. Download the UCI Energy Efficiency dataset and prepare the `energy_efficiency_data.csv` file.
3. Run the notebook cells in order and upload the CSV file when prompted.
4. Upload the Istanbul Atatürk Airport TMYx 2009–2023 EPW weather file when prompted.
5. Review the model evaluation results, cross-validation experiments, feature importance analysis, and Istanbul climate visualizations.

Note: The notebook uses manual file uploads. The Istanbul weather analysis is separate from the machine learning model training.
## Project Progress & Future Development

**Assignment 1 — Completed:** Project selection, dataset exploration, exploratory data analysis, and initial machine learning experiments.

**Assignment 2 — Completed:** Extended model evaluation, random and geometry-aware cross-validation, Leave-One-Geometry-Out validation, feature importance analysis, and separate Istanbul climate data analysis.

**Future Development:** Investigate Istanbul-specific EnergyPlus simulations, improve generalization to unseen building geometries, and explore a possible interactive application for building heating and cooling load predictions.

**Assignment 3:** Further development and evaluation will follow the official assignment requirements.
## Limitations

The model is trained on simulated building configurations. Predictions should not be interpreted as actual electricity bills or guaranteed energy savings. Real-world validation would be required before practical deployment.
## Assignment 2: Model Exploration & Results

In Assignment 2, we extended our AI Building Energy Advisor project by evaluating machine learning models and investigating their ability to generalize to unseen building geometries.

### Work Completed

- Analyzed the UCI Energy Efficiency dataset containing 768 simulated building configurations, 8 input features, and 2 prediction targets.
- Trained and evaluated Linear Regression and Random Forest models to predict Heating Load and Cooling Load.
- Evaluated model performance using MAE, RMSE, and R².
- Applied random 5-fold cross-validation and geometry-aware 4-fold GroupKFold validation.
- Conducted Leave-One-Geometry-Out (LOGO) validation to examine performance on previously unseen geometries.
- Analyzed feature importance, glazing area, and building orientation.
- Analyzed Istanbul Atatürk Airport TMYx 2009–2023 weather data separately using an EPW file.

### Key Findings

Random Forest achieved strong results under random validation. However, performance decreased substantially when models were evaluated on previously unseen building geometries.

The dataset contains only 12 unique base geometries, each represented by 64 configurations.

Under full-dataset geometry-aware GroupKFold validation, Linear Regression outperformed Random Forest for both heating and cooling load prediction.

### Limitations and Future Work

The models were developed using simulated data and have not been validated using measured energy consumption from real buildings.

The Istanbul climate analysis was conducted separately and was not used to train the current machine learning models.

Future work will investigate generating additional Istanbul-specific building simulations using EnergyPlus and evaluating glazing ratio and orientation under controlled conditions.

### Assignment 2 Notebook

[Open Assignment 2 Notebook](Assignment_2.ipynb)
## Team

- Ayşe Canan Çalışkan
- Tuğba Karademir
- Ali Rıza Ateşli
- Ebubekir Diker
## References

Tsanas, A., & Xifara, A. (2012). Accurate quantitative estimation of energy performance of residential buildings using statistical machine learning tools. *Energy and Buildings, 49*, 560–567.
