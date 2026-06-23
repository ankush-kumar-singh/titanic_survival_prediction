# 🚢 Titanic Survival Prediction using Machine Learning

## 📌 Project Overview

The objective of this project is to analyze the Titanic dataset, identify the factors that influenced passenger survival, and build machine learning models to predict whether a passenger survived the disaster.

This project covers the complete Data Science workflow including data cleaning, exploratory data analysis (EDA), feature engineering, machine learning model building, model evaluation, and Kaggle competition submission.

---

## 🛠️ Skills Demonstrated

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Data Cleaning
* Missing Value Handling
* Exploratory Data Analysis (EDA)
* Feature Engineering
* Data Preprocessing
* Machine Learning
* Logistic Regression
* Decision Tree
* Random Forest
* Model Evaluation
* Feature Importance Analysis

---

## 📂 Dataset Information

**Dataset:** Titanic Dataset (Kaggle)

**Rows:** 891

**Target Variable:**

* 0 = Did Not Survive
* 1 = Survived

### Features Used

| Feature  | Description                |
| -------- | -------------------------- |
| Pclass   | Passenger Class            |
| Sex      | Passenger Gender           |
| Age      | Passenger Age              |
| SibSp    | Number of Siblings/Spouses |
| Parch    | Number of Parents/Children |
| Fare     | Ticket Fare                |
| Cabin    | Cabin Information          |
| Embarked | Port of Embarkation        |

---

## 🧹 Data Cleaning

### Missing Value Handling

#### Age

* 177 values were missing.
* Missing values were filled using the median age grouped by Passenger Class and Sex.

| Pclass | Sex    | Median Age |
| ------ | ------ | ---------: |
| 1      | Female |       35.0 |
| 1      | Male   |       40.0 |
| 2      | Female |       28.0 |
| 2      | Male   |       30.0 |
| 3      | Female |       21.5 |
| 3      | Male   |       25.0 |

This approach preserves demographic differences better than using a global mean or median.

#### Embarked

* 2 values were missing.
* Filled using the mode (most frequent embarkation port).

#### Cabin

* Only 204 out of 891 values were available.
* The Cabin column contained excessive missing values.
* A new feature named HasCabin was created.
* The original Cabin column was dropped.

### Removed Columns

* PassengerId
* Name
* Ticket
* Cabin

---

## ⚙️ Feature Engineering

### 1. HasCabin

A new binary feature was created:

* 1 = Cabin information available
* 0 = Cabin information missing

### 2. FamilySize

FamilySize = SibSp + Parch + 1

The +1 represents the passenger themselves.

### 3. IsAlone

A new binary feature was created:

* 1 = Passenger was traveling alone
* 0 = Passenger was traveling with family

---

## 📊 Exploratory Data Analysis (EDA)

### Survival Rate by Gender

| Gender | Survival Rate |
| ------ | ------------: |
| Female |        74.20% |
| Male   |        18.89% |

#### Insight

Female passengers had significantly higher survival rates than male passengers.

---

### Survival Rate by Passenger Class

| Passenger Class | Survival Rate |
| --------------- | ------------: |
| 1st Class       |        62.96% |
| 2nd Class       |        47.28% |
| 3rd Class       |        24.24% |

#### Insight

Passengers traveling in higher classes had better chances of survival.

---

### Survival Rate by Age Group

| Age Group | Survival Rate |
| --------- | ------------: |
| 0–12      |        57.97% |
| 12–18     |        42.86% |
| 18–35     |        35.80% |
| 35–60     |        38.43% |
| 60+       |        22.73% |

#### Insight

Children had the highest survival rates while elderly passengers had the lowest.

---

### Survival Rate by Fare Group

| Fare Range    | Survival Rate |
| ------------- | ------------: |
| 0 – 7.91      |        19.73% |
| 7.91 – 14.45  |        30.36% |
| 14.45 – 31.00 |        45.50% |
| Above 31.00   |        58.11% |

#### Insight

Passengers paying higher fares generally had higher survival rates.

---

### Survival Rate by Cabin Information

| HasCabin                    | Survival Rate |
| --------------------------- | ------------: |
| No Cabin Information        |        29.99% |
| Cabin Information Available |        66.67% |

---

### Survival Rate by Embarkation Port

| Embarked        | Survival Rate |
| --------------- | ------------: |
| Cherbourg (C)   |        55.36% |
| Queenstown (Q)  |        38.96% |
| Southampton (S) |        33.70% |

---

## 📸 Project Visualizations

### Survival Rate by Gender

![Gender Survival](images/gender_survival.png)

### Survival Rate by Passenger Class

![Passenger Class Survival](images/pclass_survival.png)

### Survival Rate by Fare Group

![Fare Survival](images/fare_survival.png)

### Correlation Heatmap

![Correlation Heatmap](images/correlation_heatmap.png)

### Random Forest Feature Importance

![Feature Importance](images/feature_importance.png)

---

## 🔄 Data Preprocessing

### One-Hot Encoding

Categorical variables were converted into numerical features.

Encoded Features:

* Sex_male
* Embarked_Q
* Embarked_S

### Train-Test Split

The dataset was divided into:

* Training Set: 80%
* Testing Set: 20%

Result:

* Training Samples: 712
* Testing Samples: 179

---

## 🤖 Machine Learning Models

### Logistic Regression

Accuracy: **81.01%**

### Decision Tree

Accuracy: **78.21%**

### Random Forest

Accuracy: **82.68%**

---

## 📈 Model Comparison

| Model               | Accuracy |
| ------------------- | -------: |
| Logistic Regression |   81.01% |
| Decision Tree       |   78.21% |
| Random Forest       |   82.68% |

---

## 🏆 Best Performing Model

### Random Forest Classifier

Accuracy Achieved: **82.68%**

The Random Forest model outperformed the other models and provided the best balance between bias and variance.

---

## 📊 Random Forest Feature Importance

| Feature    | Importance |
| ---------- | ---------: |
| Sex_male   |     0.2531 |
| Fare       |     0.2487 |
| Age        |     0.2472 |
| Pclass     |     0.0690 |
| FamilySize |     0.0472 |
| HasCabin   |     0.0366 |
| SibSp      |     0.0289 |
| Embarked_S |     0.0253 |
| Parch      |     0.0231 |
| IsAlone    |     0.0106 |
| Embarked_Q |     0.0104 |

---

## 🔍 Key Findings

* Female passengers had much higher survival rates.
* First-class passengers survived more frequently.
* Higher fare passengers were more likely to survive.
* Children had higher survival rates than elderly passengers.
* Cabin information was strongly associated with survival.
* Gender, Fare, Age, and Passenger Class were the most important predictors.

---

## 🏅 Kaggle Competition Submission

A prediction file was generated using the Random Forest model and submitted to the Kaggle Titanic competition.

Submission File:

```text
submission.csv
```

Submission Format:

```text
PassengerId,Survived
892,0
893,1
894,0
...
```

---

## 📁 Repository Structure

```text
Titanic-Survival-Prediction/
│
├── datasets/
│   ├── train.csv
│   ├── test.csv
│   └── gender_submission.csv
│
├── images/
│   ├── gender_survival.png
│   ├── pclass_survival.png
│   ├── fare_survival.png
│   ├── correlation_heatmap.png
│   └── feature_importance.png
│
├── dashboards/
│   └── Titanic_Dashboard.pbix
│
├── Titanic_Survival_Prediction.ipynb
├── README.md
├── requirements.txt
└── submission.csv
```

---

## 🚀 Future Improvements

* Hyperparameter Tuning
* Cross Validation
* XGBoost Implementation
* Advanced Feature Engineering
* Streamlit Deployment
* Interactive Power BI Dashboard

---

## 📚 Libraries Used

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

---

## 👨‍💻 Author

**Ankush Kumar Singh**

B.Tech CSE (Data Science)

Passionate about Data Analysis, Machine Learning, and solving real-world problems using data.
