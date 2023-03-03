# MSK_brain_lower_grade_glioma_project

<img src="image.jpg" width="800" height="200"/>

Each member focused his analysis on a specific dependent variable

# Prediction for Subtype of LGG: 

In 2016, WHO changed the classification of Brain Lower Grade Glioma by the presence or absense of iscocitrate dehydrogenase (IDH) mutation and chromosome 1p/19q codeletion instead of from histology diagnosis, so now there are 3 categories: 

1) IDH mutation with 1p/19q codeletion (oligodendroglioma); 

2) IDH mutation without 1p/19q codeletion (most grades II and III astrocytoma)

3) IDH wildtype (most glioblastoma)

The classification provides better prognostications according to TCGA's description, and this would be discussed in **Emile's part, Overall Survival (OS) Analysis**.

THIS part is to **predict the 1p/19q codeletion status using gene expression matrix (RNA-Seq)**. The supervised learning model, random forest classifier was used with future selection by f_regression score function, which give a high accuracy score, around **98%**. Using Non-negative Matrix Factorization A = WH with rank = 20, the accuracy score of random forest model with H as features is **97%**, and metagene 10, 2 and 1 are the most important features.


**Future Analysis Plans ...** 
1. Use Non-negative Matrix Factorization/Deep Learning model to detect the local behavior of genes associated with tumor subtype. 
2. Assign or cluster genes into metagenes and try to find the biological interpretation for these metagenes.



# Jin

### I focused on predicting the Mutation count.

**The models I used right now is linear regression, but I consider to change to others like Lasso regression to improve the accuracy and R-squared value.**

### Results
-Mean squared error: 8100.792835393206 R-squared: -45.47660982946169 -Not informative yet and will improve on that.


# Emile

### I focused on predicting the **Survival Rate**. 

#### The features I use are
- Gene expression
- Clinical data (age, sex, race, prior diagnosis, radiation therapy...)

#### The models I used:

- LASSO
- Random Forest
- GradientBoosting
- SVM
- Cox Survival Model Elastic Net

#### Results
- Cox Elastic Net is the only decent model, with **87%** R2 on testing data
- Feature importance and explainability: Diagnosis Age plays an important role, as well as genes 118430, 55970, 406, 4214
