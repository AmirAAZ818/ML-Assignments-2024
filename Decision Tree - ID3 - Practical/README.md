# Decision Tree Classifier - ID3: Assignment Report

This Folder contains the solution and a comprehensive report for the Decision Tree Classification assignment from the Machine Learning course. The project focuses on building and evaluating a decision tree model using the ID3 algorithm on a **Salary** dataset.

## Summary of Key Achievements and Analysis

The primary goal of this assignment was to train a decision tree model to predict an individual's annual income class ($>50K$ or $<=50K$) based on a set of demographic and work-related features. A detailed analysis of the dataset, feature selection techniques, and model performance is included in the full report.

### 1. Dataset Analysis and Preprocessing

The **Salary** dataset, consisting of 32,561 instances with 15 features, was thoroughly analyzed. Key observations from the data visualization phase include:
* **Gender Imbalance**: The male population is approximately twice that of the female population.
* **Age Distribution**: Most individuals in the dataset are in their 30s and 40s.
* **Class Imbalance**: The dataset is highly imbalanced, with the minor class representing the higher income bracket ($>50K$). This imbalance significantly impacts the model's performance metrics, particularly **Recall**.

### 2. Feature Selection
To identify the most relevant features for the model, the **Chi-Square Test** was employed. This statistical method measures the dependence between each feature and the target variable (salary class). The $\chi^2$ values were calculated for all features, as shown in the table below, revealing their relative importance.

| Feature Name | $\chi^2$ Value |
|:---:|:---:|
| Relationship | 3659 |
| Capital Gain | 1866 |
| Marital Status | 1123 |
| Age | 1113 |
| Occupation | 504 |
| Sex | 502 |
| Education | 297 |
| Hours per Week | 199 |
| Work class | 47 |
| Race | 33 |
| Native Country | 13 |

Based on this analysis, the features `education-num`, `fnlwgt`, and `capital-loss` were manually removed due to redundancy or low relevance.

### 3. Model Training and Pruning

The ID3 algorithm was modified to include a pruning mechanism based on an **Information Gain (IG) threshold**. This technique helps prevent overfitting and improves the model's generalization capabilities on unseen data. The model was trained under three different scenarios for comparison:

1.  **All Features**: Using all available features.
2.  **Top 8 Features**: Using the 8 features with the highest $\chi^2$ scores.
3.  **Top 4 Features**: Using the 4 features with the highest $\chi^2$ scores.

The performance of each model was evaluated on a held-out test set (20% of the data).

### 4. Results and Conclusion

The final models were compared based on various metrics including Accuracy, F1 Score, Precision, and Recall.

| Method Used | IG Threshold | Accuracy | Precision | Recall | F1 Score |
| :---: |:---:|:---:|:---:|:---:|:---:|
| All Features | 12.0 | 81.0\% | 73.0\% | 40.0\% | 52.0\% |
| $\chi^2$ - Top 8 | 1.0 | 81.0\% | 72.0\% | 41.0\% | **53.0\%** |
| $\chi^2$ - Top 4 | 0 | 77.0\% | 74.0\% | 13.0\% | 22.0\% |

The analysis shows that the model trained on the **top 8 features** with an IG threshold of 1.0 achieved the best overall performance, with an **F1 Score of 53.0%**. It is important to note that the low **Recall** value across all models is likely a direct result of the dataset's unbalanced nature. The model shows a bias towards the majority class ($<=50K$), leading to a higher number of False Negatives and a subsequent drop in Recall.
***

## Curiosity: Dataset Visualization with PCA

For a deeper understanding of the data, Principal Component Analysis (**PCA**) was used to visualize the dataset in 2 and 3 dimensions. When using **two components**, the separation between the positive ($>50K$) and negative ($<=50K$) classes is not very distinct. However, by using **three components**, the separability of the classes noticeably increases, suggesting that a 3D view captures a more informative representation of the data.

<div style="display: flex; justify-content: space-between;">
  <img src="ML-2024\ID3\Assets\pca2.png" alt="PCA With 2 Components" style="width: 30%;"/>
  <img src="ML-2024\ID3\Assets\pca3.png" alt="PCA With 3 Components" style="width: 30%;"/>
</div>