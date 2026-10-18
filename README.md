# AI Building Energy Advisor

**MTH4800 – Innovation Campus Artificial Intelligence**

**Group 14 – Assignment 1: Project Selection & Exploratory Data Analysis**


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

1. Open `samsung_project.ipynb` in Google Colab.
2. Download the Energy Efficiency dataset from the source above.
3. Run the notebook cells.
4. Upload the CSV file when prompted.
5. Review the EDA visualizations and model results.

## Future Development

**Assignment 2:** Develop a Streamlit application that allows users to enter building characteristics and obtain heating and cooling load predictions.

**Assignment 3:** Test the application with different inputs, evaluate model limitations, document ethical considerations, and prepare the final report and demonstration.

## Limitations

The model is trained on simulated building configurations. Predictions should not be interpreted as actual electricity bills or guaranteed energy savings. Real-world validation would be required before practical deployment.

## Team

- Ayşe Canan Çalışkan
- Tuğba Karademir
- Ali Rıza Ateşli

## References

Tsanas, A., & Xifara, A. (2012). Accurate quantitative estimation of energy performance of residential buildings using statistical machine learning tools. *Energy and Buildings, 49*, 560–567.
