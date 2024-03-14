# Report on Car Price Prediction

## 1. Problem Statement:
The objective of this project is to create a predictive model for estimating car prices based on various features. By analyzing the relationship between different numerical attributes of cars and their prices, we aim to build an accurate linear regression model. This model can provide valuable insights for both buyers and sellers in the automotive market.

## 2. Introduction:
Accurately predicting car prices is essential for stakeholders such as dealerships, manufacturers, and consumers. Understanding the factors influencing car prices can aid in making informed decisions regarding pricing strategies, purchasing, and investments. This project utilizes a dataset containing information about cars and their attributes to develop a predictive model, shedding light on how these attributes affect car prices.

## 3. Dataset Details:

The dataset includes information about various cars, each represented by a different row.

| Attribute         | Description                                                                                               |
|-------------------|-----------------------------------------------------------------------------------------------------------|
| ID                | An identifier for each car entry.                                                                         |
| Symboling        | A rating assigned to each car indicating its risk level (e.g., insurance risk).                           |
| Name              | The name or model of the car.                                                                             |
| Fuel Types        | The type of fuel the car uses (e.g., gas, diesel).                                                        |
| Aspiration        | The method of aspiration for the engine (e.g., std for standard, turbo for turbocharged).                  |
| Door Numbers      | The number of doors the car has.                                                                         |
| Car Body          | The body style of the car (e.g., sedan, convertible, hatchback).                                          |
| Drive Wheels      | The type of wheels that receive power from the engine (e.g., fwd for front-wheel drive, rwd for rear-wheel drive). |
| Engine Location   | The location of the engine in the car (e.g., front, rear).                                                |
| Wheelbase         | The distance between the centers of the front and rear wheels.                                            |
| Engine Size       | The volume of the engine displacement, often measured in liters or cubic centimeters.                     |
| Fuel System       | The type of fuel delivery system used by the engine (e.g., mpfi, 2bbl).                                   |
| Bore Ratio        | The diameter of each cylinder in the engine.                                                              |
| Stroke            | The length of the piston stroke in the engine.                                                            |
| Compression Ratio | The ratio of the volume of the combustion chamber when the piston is at the bottom of its stroke to the volume when it's at the top. |
| Horsepower        | The power output of the engine.                                                                           |
| Peak RPM          | The maximum revolutions per minute of the engine.                                                         |
| City MPG          | The estimated miles per gallon (MPG) the car can achieve in city driving conditions.                      |
| Highway MPG       | The estimated miles per gallon (MPG) the car can achieve on the highway.                                  |
| Price             | The price of the car.                                                                                    |

## 4. Methodology

### Data Loading and Inspection:
Load the dataset and inspect its structure, including features and the target variable.

### Data Preprocessing:
Handle missing values, encode categorical variables, and scale numerical features if needed.

### Exploratory Data Analysis (EDA):
Explore the dataset, identify correlations between features and the target variable, and visualize patterns.

### Feature Selection:
Select relevant features with significant correlation with the target variable for model training.

### Model Training:
Split the data into training and testing sets, then train a linear regression model using selected features.

### Model Evaluation:
Evaluate the trained model using metrics such as MSE, MAE, R2, and RMSE to assess its performance.

### Visualization:
Visualize actual vs. predicted prices and plot regression lines to understand predictive accuracy.

## 5. Model Training Process

- **Importing Required Libraries**:
  - Imports necessary libraries and modules for building and evaluating a linear regression model.

- **Loading Data**:
  - Reads the data from a CSV file into a pandas DataFrame.

- **EDA**:
  - Inspects the data, summarizes statistics, explores unique values, and identifies columns.

- **Data Selection**:
  - Selects numerical columns for analysis.

- **Correlation Analysis**:
  - Calculates correlation coefficients between numerical features and the target variable ('price').

- **Creating a New DataFrame**:
  - Creates a new DataFrame using 'enginesize' and 'price' for model training.

- **Splitting Data**:
  - Splits the data into training and testing sets.

- **Model Creation**:
  - Initializes a Linear Regression model.

- **Model Training**:
  - Fits the model to the training data.

- **Evaluation Metrics**:
  - Calculates evaluation metrics including MSE, RMSE, MAE, and R2 score.

- **Plotting Actual vs. Predicted Values**:
  - Visualizes the relationship between actual and predicted prices.

- **Plotting Regression Model Line**:
  - Plots the regression line to visualize the model's fit.

- **Predicting Prices based on Engine Size**:
  - Generates predicted prices based on engine size.

## 6. Result

- Key Findings:
  - Engine size is identified as the most influential feature in determining car prices.
  - The linear regression model demonstrates reasonable performance in predicting car prices.
  - Evaluation metrics indicate the model captures a significant portion of the variance in car prices.

## 7. Conclusion

In conclusion, this project successfully develops a predictive model for estimating car prices based on various attributes, with a focus on engine size. The model provides valuable insights for stakeholders in the automotive industry, aiding in pricing strategies and decision-making processes. Further enhancements and refinements to the model could improve its predictive accuracy and broaden its applicability.

