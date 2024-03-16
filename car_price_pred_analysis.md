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
```python 
import pickle
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, mean_absolute_error, r2_score
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

```

- **Loading Data**:
  - Reads the data from a CSV file into a pandas DataFrame.
```python
df = pd.read_csv('car_dataset.csv')
```


- **EDA**:
  - Inspects the data, summarizes statistics, explores unique values, and identifies columns.
```python
# check the shape
df.shape
# first five rows of the dataframe
df.head()
# describe the dataframe with some statistical info
df.describe()
# check data types in the dataframe
df.info()
# check unique data for each feature in the dataframe
df.nunique()
# column names of the dataframe
df.columns
```

- **Data Selection**:
  - Selects numerical columns for analysis.
```python
numerical_columns = ['wheelbase', 'enginesize', 'boreratio', 'stroke', 'compressionratio', 'horsepower', 'peakrpm', 'citympg']
```
  
- **Correlation Analysis**:
  - Calculates correlation coefficients between numerical features and the target variable ('price').
```python
# Calculate correlation coefficients with respect to "price"
correlation_with_price = df[numerical_columns].corrwith(df['price']).abs().sort_values(ascending=False)
```

- **Creating a New DataFrame**:
  - Creates a new DataFrame using 'enginesize' and 'price' for model training.
```python
x = new_df['enginesize']
y = new_df['price']
```

- **Splitting Data**:
  - Splits the data into training and testing sets.
```python
x_train, x_test, y_train, y_test = train_test_split(x, y, test_size=0.2, random_state=0)
```

- **Model Creation**:
  - Initializes a Linear Regression model.
```python
model = LinearRegression()
```

- **Model Training**:
  - Fits the model to the training data.
```python
model.fit(x_train.values.reshape(-1,1), y_train)
```

- **Evaluation metric - R2**
  - Calculates evaluation metric - R2 score.

- **Plotting Actual vs. Predicted Values**:
  - Visualizes the relationship between actual and predicted prices.

- **Plotting Regression Model Line**:
  - Plots the regression line to visualize the model's fit.

- **Predicting Prices based on Engine Size**:
  - Generates predicted prices based on engine size.

| Engine Size | Predicted Price |
|-------------|-----------------|
| 91          | 7339.34         |
| 161         | 18841.42        |
| 136         | 14733.53        |
| 61          | 2409.87         |
| 109         | 10297.01        |
| 146         | 16376.69        |
| 92          | 7503.65         |
| 92          | 7503.65         |
| 181         | 22127.73        |
| 92          | 7503.65         |
| 164         | 19334.36        |
| 203         | 25742.67        |
| 70          | 3888.71         |
| 134         | 14404.90        |
| 90          | 7175.02         |
| 146         | 16376.69        |
| 132         | 14076.27        |
| 136         | 14733.53        |
| 110         | 10461.33        |
| 92          | 7503.65         |
| 110         | 10461.33        |
| 120         | 12104.48        |
| 132         | 14076.27        |
| 146         | 16376.69        |
| 171         | 20484.57        |
| 97          | 8325.23         |
| 98          | 8489.54         |
| 120         | 12104.48        |
| 98          | 8489.54         |
| 97          | 8325.23         |
| 109         | 10297.01        |
| 109         | 10297.01        |
| 151         | 17198.26        |
| 122         | 12433.11        |
| 97          | 8325.23         |
| 209         | 26728.56        |
| 109         | 10297.01        |
| 121         | 12268.80        |
| 90          | 7175.02         |
| 304         | 42338.53        |
| 90          | 7175.02         |

## 6. Result

Following an extensive analysis and the implementation of a linear regression model, we have successfully created a predictive framework for estimating car prices based on engine size. Here are the key observations and outcomes:

**Key Observations:**
- **Feature Importance:** Engine size emerges as the most critical factor in determining car prices. It showcases the highest correlation coefficient with the target variable (price) compared to other numerical attributes examined in the dataset.
  
**Model Performance:** The linear regression model exhibits satisfactory performance in predicting car prices, as indicated by an R-squared (R2) score of approximately 0.78. This score suggests that the model captures a considerable portion of the variance in the target variable, reflecting a reasonable level of predictive accuracy.

**Insights from Predictions:** Despite the inherent variability in car prices, the model's predictions align closely with actual prices. Evaluation metrics and scatter plot visualizations validate the model's effectiveness in estimating car prices based on engine size, providing valuable insights for decision-making processes.

Overall, through meticulous analysis and modeling efforts, we have developed a robust framework capable of reliably estimating car prices, with engine size serving as a pivotal determinant.

## 7. Conclusion

This project has successfully developed a predictive model for estimating car prices based on various attributes, with a particular emphasis on engine size. The findings highlight the importance of engine size in determining car prices, suggesting that it serves as a significant factor for both buyers and sellers to consider.

Moving forward, further enhancements and refinements to the model could be explored to improve its predictive accuracy and broaden its applicability. Additionally, incorporating additional features and exploring advanced modeling techniques may offer deeper insights into the complex dynamics of car pricing in the automotive market.

Overall, the developed model represents a valuable tool for stakeholders in the automotive industry, providing actionable insights that can inform pricing strategies, facilitate decision-making processes, and ultimately enhance the overall efficiency and effectiveness of operations within the industry.




