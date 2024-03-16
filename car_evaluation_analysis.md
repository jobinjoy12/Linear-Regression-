# Report on Analysis of Decision Tree Classifier for Car Evaluation Dataset

## 1. Problem Statement:
This report aims to analyze the performance of a decision tree classifier on a car evaluation dataset. Specifically, we investigate the impact of varying tree depth and min samples split parameters on the classifier's accuracy.

## 2. Introduction:
Decision tree classifiers are valuable tools for classification tasks due to their interpretability and effectiveness. However, their performance can vary based on dataset characteristics and parameter choices. In this report, we explore how different parameter settings affect the accuracy of a decision tree classifier applied to a car evaluation dataset.

## 3. Dataset Details:
The car evaluation dataset comprises attributes like buying price, maintenance price, number of doors, persons, luggage boot size, safety rating, and car class (acceptable, unacceptable, good, or very good). The dataset is free from missing values and has undergone preprocessing to encode categorical variables.

## 4. Methodology:
We utilize a decision tree classifier with the entropy criterion for our analysis. Two key parameters, tree depth and min samples split, are varied systematically to identify their impact on classifier accuracy.

## 5. Model Training Process

- **Importing Required Libraries**:
  - Imports necessary libraries for data handling, model building, evaluation, and visualization.
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
import pandas as pd
import category_encoders as ce
from sklearn.metrics import accuracy_score
from matplotlib import pyplot as plt
import pickle
import pandas as pd
from sklearn import tree
```

- **Loading Data**:
  - Reads the car evaluation dataset into a pandas DataFrame.
```python
df = pd.read_csv('car_evaluation.csv')
```

- **EDA**:
  - Provides an overview of the dataset, examining its structure, information, and missing values.
  - Analyzes the distribution of categorical variables and class distribution.
Data Overview

```python
print(df.head())
df.shape
df.info()
df.isnull().sum()
```
Examining the value counts of categorical variables

```python
col_names = ['buying', 'maint', 'doors', 'persons', 'lug_boot', 'safety', 'class']
for col in col_names:
  print(df[col].value_counts())
```

Analysis of `class` distribution

```python
df['class'].value_counts()
```
Feature-Target Separation

```python
X = df.drop(['class'], axis=1)
y = df['class']
```


- **Data Preparation**:
  - Separates features and target variables.
  - Splits the data into training and testing sets.
```python
X_train,X_test,y_train,y_test=train_test_split(X,y,test_size=0.33, random_state=42)
```

- **Data Encoding**:
  - Encodes categorical variables using ordinal encoding.
```python
encoder = ce.OrdinalEncoder(cols=['buying', 'maint', 'doors', 'persons', 'lug_boot', 'safety'])
X_train = encoder.fit_transform(X_train)
X_test = encoder.transform(X_test)
```

- **Model Creation**:
  - Initializes a Decision Tree Classifier with the entropy criterion.
```python
clf = DecisionTreeClassifier(criterion="entropy")
```

- **Model Training**:
  - Trains the classifier on the training set.
```python
clf.fit(X_train, y_train)
```

- **Model Performance Evaluation**:
  - Assesses the classifier's performance on the training and testing sets.
  - Generates accuracy scores for different parameter configurations.

- **Graphical Representation of Decision Tree**:
  - Visualizes the decision tree classifier.

- **Systematic Analysis**:
  - Performs a systematic analysis by varying tree depth and min samples split parameters.
  - Records accuracy scores for each parameter combination.
```python
for depth in depths:
    for min_samples_split in min_samples_splits:
        # Create and train decision tree classifier
        clf = DecisionTreeClassifier(criterion="entropy", max_depth=depth, min_samples_split=min_samples_split, random_state=42)
        clf.fit(X_train, y_train)
```
- **Decision Tree Accuracy vs. Min Samples Split**

![min_samples](https://github.com/Rahul-Biju-03/Python-For-ML/assets/106422354/f5dd4409-7a82-4bfa-94cc-bf3ea3813f10)

## 6. Result

- Analysis reveals that increasing tree depth generally leads to improved accuracy.
- Accuracy remains consistent for a depth of 3 across different min samples split values.
- Deeper trees with smaller min samples split tend to offer higher accuracy, with the best performance achieved at a depth of 9 and min samples split of 2, yielding approximately 96.14% accuracy.

## 7. Conclusion

The decision tree classifier demonstrates promising performance on the car evaluation dataset, with accuracy improving with deeper trees and smaller min samples split. However, careful consideration is needed to prevent overfitting, especially with deeper trees. Further optimization and validation techniques such as cross-validation can enhance the model's robustness. Overall, this analysis highlights the effectiveness of decision tree classifiers for car evaluation tasks, offering valuable insights for model optimization and future research.
