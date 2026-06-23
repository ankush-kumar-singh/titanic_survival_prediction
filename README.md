# 🚢 Titanic Survival Prediction using Machine Learning

## 📌 Project Overview

The objective of this project is to analyze the Titanic dataset, identify the factors that influenced passenger survival, and build machine learning models to predict whether a passenger survived the disaster.

This project covers the complete Data Science workflow including data cleaning, exploratory data analysis (EDA), feature engineering, machine learning model building, and model evaluation.

---

## 🛠️ Skills Demonstrated

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Data Cleaning
- Missing Value Handling
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Data Preprocessing
- Machine Learning
- Logistic Regression
- Decision Tree
- Random Forest
- Model Evaluation

---


Also update the **Dataset Information** section to:

```md
## 📂 Dataset Information

**Source:** Kaggle Titanic - Machine Learning from Disaster

Dataset Files:

- train.csv → Training dataset
- test.csv → Test dataset used for Kaggle submission
- gender_submission.csv → Sample submission file provided by Kaggle

Training Dataset:

- Rows: 891
- Features: 11
- Target Variable: Survived

Target Variable:

- 0 = Did Not Survive
- 1 = Survived

## 🧹 Data Cleaning

### Missing Value Handling

#### Age

- 177 values were missing.
- Missing values were filled using the median age grouped by **Passenger Class** and **Sex**.

| Pclass | Sex | Median Age |
|---------|---------|---------:|
| 1 | Female | 35.0 |
| 1 | Male | 40.0 |
| 2 | Female | 28.0 |
| 2 | Male | 30.0 |
| 3 | Female | 21.5 |
| 3 | Male | 25.0 |

This approach preserves demographic differences better than using a global mean or median.

---

#### Embarked

- 2 values were missing.
- Filled using the mode (most frequent embarkation port).

---

#### Cabin

- Only 204 out of 891 values were available.
- Due to excessive missing values, the Cabin column was dropped.

---

#### Removed Columns

The following columns were removed because they do not directly contribute to prediction:

- PassengerId
- Name
- Ticket
- Cabin

---

## ⚙️ Feature Engineering

### 1. HasCabin

A new feature was created:

- 1 = Cabin information available
- 0 = Cabin information missing

---

### 2. FamilySize

```python
FamilySize = SibSp + Parch + 1
````md
The +1 represents the passenger themselves.

This feature was created to capture the effect of family presence on survival. Passengers traveling with small families often had higher survival rates compared to those traveling alone or with very large families.

---

### 3. IsAlone

A new binary feature was created:

- 1 = Traveling Alone
- 0 = Traveling With Family

This feature helps distinguish between solo travelers and passengers accompanied by family members.

---

## 📊 Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to identify patterns and relationships between passenger characteristics and survival outcomes.

### Survival Rate by Gender

| Gender | Survival Rate |
|----------|----------:|
| Female | 74.20% |
| Male | 18.89% |

#### Insight

Female passengers had a significantly higher survival rate than male passengers, supporting the historical "women and children first" evacuation policy.

---

### Survival Rate by Passenger Class

| Passenger Class | Survival Rate |
|----------|----------:|
| 1st Class | 62.96% |
| 2nd Class | 47.28% |
| 3rd Class | 24.24% |

#### Insight

Passengers traveling in higher classes were more likely to survive. First-class passengers had better access to lifeboats and evacuation routes.

---

### Survival Rate by Age Group

| Age Group | Survival Rate |
|----------|----------:|
| 0–12 | 57.97% |
| 12–18 | 42.86% |
| 18–35 | 35.80% |
| 35–60 | 38.43% |
| 60+ | 22.73% |

#### Insight

Children had the highest survival rates, while elderly passengers had the lowest.

---

### Survival Rate by Fare Group

| Fare Range | Survival Rate |
|----------|----------:|
| 0 – 7.91 | 19.73% |
| 7.91 – 14.45 | 30.36% |
| 14.45 – 31.00 | 45.50% |
| Above 31.00 | 58.11% |

#### Insight

Passengers paying higher fares generally had better survival chances. Fare acted as a proxy for wealth and passenger class.

---

### Survival Rate by Cabin Information

| HasCabin | Survival Rate |
|----------|----------:|
| No Cabin Information | 29.99% |
| Cabin Information Available | 66.67% |

#### Insight

Passengers with recorded cabin information survived at much higher rates.

---

### Survival Rate by Embarkation Port

| Embarked | Survival Rate |
|----------|----------:|
| Cherbourg (C) | 55.36% |
| Queenstown (Q) | 38.96% |
| Southampton (S) | 33.70% |

#### Insight

Passengers embarking from Cherbourg had the highest survival rates, largely due to a greater proportion of first-class travelers.

---

## 📸 Project Visualizations

### Survival Rate by Gender

![Gender Survival](images/gender_survival.png)

### Survival Rate by Passenger Class

![Pclass Survival](images/pclass_survival.png)

### Survival Rate by Fare Group

![Fare Survival](images/fare_survival.png)

### Correlation Heatmap

![Heatmap](images/correlation_heatmap.png)

### Random Forest Feature Importance

![Feature Importance](images/feature_importance.png)

---

## 🔄 Data Preprocessing

Before training machine learning models, the dataset was transformed into a format suitable for machine learning algorithms.

### One-Hot Encoding

Categorical variables were converted into numerical features.

Original Features:

- Sex
- Embarked

Generated Features:

- Sex_male
- Embarked_Q
- Embarked_S

---

### Train-Test Split

The dataset was divided into:

- Training Set: 80%
- Testing Set: 20%

Result:

- Training Samples: 712
- Testing Samples: 179

---

## 🤖 Machine Learning Models

Three machine learning models were trained and evaluated.

| Model | Accuracy |
|---------|---------:|
| Logistic Regression | 81.01% |
| Decision Tree | 78.21% |
| Random Forest | 82.68% |

---

## 🏆 Best Performing Model

### Random Forest Classifier

**Accuracy: 82.68%**

Random Forest achieved the highest accuracy among all tested models.

The ensemble approach reduced overfitting and improved generalization compared to a single Decision Tree.

---

## 📈 Random Forest Feature Importance

| Feature | Importance |
|----------|----------:|
| Sex_male | 0.2531 |
| Fare | 0.2487 |
| Age | 0.2472 |
| Pclass | 0.0690 |
| FamilySize | 0.0472 |
| HasCabin | 0.0366 |
| SibSp | 0.0289 |
| Embarked_S | 0.0253 |
| Parch | 0.0231 |
| IsAlone | 0.0106 |
| Embarked_Q | 0.0104 |

---

## 🔍 Key Findings

- Female passengers had significantly higher survival rates than male passengers.
- First-class passengers survived more often than third-class passengers.
- Higher fare passengers had greater survival chances.
- Children had higher survival rates than elderly passengers.
- Passengers with cabin information survived more frequently.
- Family size influenced survival probability.
- Gender, Fare, Age, and Passenger Class were the strongest predictors of survival.

---

## 🎯 Conclusion

This project successfully explored the Titanic dataset, identified key survival patterns, and developed predictive machine learning models.

The analysis revealed that gender, fare, age, and passenger class were the most influential factors affecting survival.

Among all models tested, the Random Forest Classifier achieved the highest accuracy of **82.68%**, making it the best-performing model for this dataset.

This project demonstrates a complete end-to-end machine learning workflow, including data cleaning, exploratory data analysis, feature engineering, model building, and evaluation.

---

## 🚀 Future Improvements

Potential improvements include:

- Hyperparameter Tuning
- Cross Validation
- Extracting Passenger Titles from Names
- Advanced Feature Engineering
- XGBoost Implementation
- Power BI Dashboard Creation
- Model Deployment using Streamlit or Flask

---

## 📚 Libraries Used

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
````

---

## 🏅 Kaggle Competition Submission

A submission file was generated using the Random Forest model predictions.

Submission Format:

```text
PassengerId,Survived
892,0
893,1
894,0
...

## 👨‍💻 Author

**Ankush Kumar Singh**

B.Tech CSE (Data Science)

Passionate about Data Analysis, Machine Learning, and solving real-world problems using data.

```
```


