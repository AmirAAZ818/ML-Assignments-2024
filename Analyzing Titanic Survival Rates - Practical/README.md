# Titanic Survival Rates Analysis Assignment

## Overview

This repository contains an Exploratory Data Analysis (`EDA`) of the famous Titanic dataset. The analysis examines passenger survival rates based on features like class, gender, age, and family size. EDA involves data cleaning, statistical examination, and visualization to uncover insights into factors influencing survival during the Titanic disaster.

The report is structured into sections covering introduction, dataset description, data cleaning, statistical analysis with visualizations, and conclusions. It uses Python for data processing (implied in methods like Iterative Imputation) and includes visualizations as well.

### Key tools/libraries

- **Pandas** for data manipulation.

- **Matplotlib/Seaborn** for Visualizations

- **Scikit-learn** for imputation.

## Dataset Description

The Titanic dataset includes 11 features and 1309 samples from Kaggle's "Titanic - Machine Learning from Disaster" competition. Key features:

- **Survived**: 0 (Dead), 1 (Alive)
- **Pclass**: Ticket class (1: First, 2: Second, 3: Third)
- **Sex**: Gender (0: Female, 1: Male)
- **Age**: Passenger age (decimals for children under 1)
- **SibSp**: Number of siblings/spouses aboard
- **ParCh**: Number of parents/children aboard
- **Fare**: Ticket fare
- **Embarked**: Port of embarkation (C: Cherbourg, Q: Queenstown, S: Southampton)

> Other features like Ticket, Cabin, and Name were removed as irrelevant to survival.

## Data Collection and Cleaning

- **Merging Data**: Combined `train.csv`, `test.csv`, and `gender_submission.csv` using inner joins and concatenation.
- **Handling Missing Values**:
  - Columns with missing data: `Age`, `Fare`, `Embarked`, `Cabin`.
  - `Cabin` removed entirely.
  - `Fare` imputed using mean grouped by `Pclass` and `Sex`.
  - `Embarked` filled with most frequent port per `Pclass`.
  - `Age` imputed via Iterative Imputation (regression-based).

Important Figures:
- ![Count of Missing and Not Missing Data](https://github.com/AmirAAZ818/ML-2024/blob/main/Analyzing%20Titanic%20Survival%20Rates%20-%20Practical/Assets/Count-of-missing-and-not-missing%20data-for-each-column.png)  
  Frequency of missing vs. non-missing data per feature.
- ![Missing vs Not Missing Rate]([./figs/Missing%20vs%20Not%20Missing%20Rate.png](https://github.com/AmirAAZ818/ML-2024/blob/main/Analyzing%20Titanic%20Survival%20Rates%20-%20Practical/Assets/Missing%20vs%20Not%20Missing%20Rate.png))  
  Ratio of missing data for affected columns.
- ![Fare Mean for Different Combinations](./figs/Fare%20Mean%20for%20Different%20Combination.png)  
  Mean Fare by Pclass and Sex combinations.

## Statistical Analysis and Visualization

Focuses on population distribution, survival rates, and age-related trends.

- **Population Distribution**: By `Sex`, `Pclass`, and `Embarked`.  
  ![Passenger's Population in Different Groups](./figs/Passenger's%20Population%20In%20Different%20Groups.png)

- **Survival Analysis**:
  - Overall: ~62% died (mostly males due to higher male count).
  - By `Sex` and `Pclass`: Higher survival for females and first-class passengers.
  - `Age` Distribution: Children (esp. <1 year) had higher survival; peak non-survivors at age 25.
  - `Family Size`: Inverse relationship with survival (larger families had lower survival rates). New feature: Family Population = SibSp + ParCh.

  Important Figures:
  - ![Survival Rate of Passengers by Pclass](./figs/Survival%20Rate%20of%20the%20Passengers%20by%20Pclass.png)  
    Survival ratios by Sex, Pclass, and overall.
  - ![Age Distribution for Different Survival Status](./figs/Age%20Distribution%20for%20Different%20Survival%20Status.png)  
    Age histograms for survivors vs. non-survivors.
  - ![Survival of Passengers by Family Population](./figs/Survival%20of%20Passengers%20by%20Family%20Population.png)  
    Family size frequency by survival status.

- **Age Analysis**: Box plots show age spreads by survival and Pclass.  
  - Upper class: Late 30s median age.
  - Middle class: Late 20s.
  - Lower class: Mid-20s.
  - Older adults (>60) mostly non-survivors; children mostly from upper/middle classes.

  Important Figure:
  - ![Box Plots of Age Column in Different Groups](./figs/Box%20plots%20of%20Age%20Column%20in%20Different%20Groups.png)

## Conclusions

- Over half the passengers (~800) died, predominantly males.
- Family size inversely correlates with survival.
- Children and infants had high survival rates; elderly low.
- Class influences age demographics and survival (wealthier classes older, higher survival).

> These insights highlight social and demographic factors in the disaster.
