# MSK_brain_lower_grade_glioma_project

<img src="images/dna_repo.jpg" width="400" height="200"/>


# Prediction for Subtype of LGG: 

In 2016, WHO changed the classification of Brain Lower Grade Glioma by the presence or absense of iscocitrate dehydrogenase (IDH) mutation and chromosome 1p/19q codeletion instead of from histology diagnosis, so now there are 3 categories: 

1) IDH mutation with 1p/19q codeletion (oligodendroglioma); 

2) IDH mutation without 1p/19q codeletion (most grades II and III astrocytoma)

3) IDH wildtype (most glioblastoma)

The classification provides better prognostications according to TCGA's description, and this would be discussed in **Emile's part, Overall Survival (OS) Analysis**.

THIS part is to **predict the 1p/19q codeletion status using gene expression matrix (RNA-Seq)**. The supervised learning model, random forest classifier was used with future selection by f_regression score function, which give a high accuracy score, around **98%**. Using Non-negative Matrix Factorization A = WH with rank = 20, the accuracy score of random forest model with H as features is **97%**, and metagene 10, 2 and 1 are the most important features.

The model's top features, here genes might be not the "real" top features: After training the random forest model 50 times, I find that top genes are totally different, and if we using the genes that never has feature importance (feature_importance_val = 0) as features to train the RF model, it still could get 97% accuracy. If there is not data leakage (in most paper about BLGG, they all have around 97% accuracy), then it would means the genes has highly correlations between each other, I would say gene is an environment for tumor, we could not see gene one by one, and we need to group them and cluster in some ways that could be measured and reversed. There are 3 methods I could come up to solve this: 

**Method 1: Non-Negative Matrix Factorization**
This method has already be implemented (with 97% accuracy score) and need to do more to scale the data using Max-Min scaler; and also might need to use some NLP method to find the functionality of the metagenes (gene group). 

**Method 2: Correlation Matrix** 
Remove the highly correlated genes (similarity) in the features. 

**Method 3: NLP for gene Description** 
Firstly, cluster the genes with NLP methods using data from gene library (gene description, GO terms, etc.) and then use this clustered gene groups as features to predict the subtype of tumor or do OS analysis.


**Future Analysis Plans ...** 
1. Use Non-negative Matrix Factorization/Deep Learning model to detect the local behavior of genes associated with tumor subtype. 
2. Assign or cluster genes into metagenes and try to find the biological interpretation for these metagenes.



# Jin

### I focused on predicting the Mutation count.

**The models I used is Poisson regression model,because this helps to identify which predictor variables are associated with the mutation count and how strong these associations are .**

### Results
-Mean squared error: 35.91208791208791 R-squared: 0.7939618834888497
The Poisson regression model was used to predict the mutation count using the X variables. The model achieved a good R-squared value of 0.79, indicating that it is a reliable model for prediction. This means that the X variables included in the model are useful in explaining the variability in the mutation count, and they have a reasonably strong relationship with the outcome variable. 

-Coefficients: After calculating coefficients of x variables, the feature importance information was then extracted using the coefficients obtained from the model. The top five features with the largest coefficients were TMB_NONSYNONYMOUS_0.033333333, SAMPLE_ID_TCGA-HT-8107-01, SAMPLE_ID_TCGA-P5-A5F6-01, MSI_SCORE_MANTIS_0.3526, and MSI_SENSOR_SCORE_0.48. These features suggest that the presence of certain gene mutations, tumor mutation burden, and microsatellite instability score may be important predictors of mutation count.

-Next steps: We may want to use NMF to identify patterns and relationships between the features. NMF is a matrix factorization that decomposes a matrix into two matrices of lower rank. In this case, the input matrix X is factorized into two matrices W and H, where W represents the basis vectors and H represents the coefficient matrix. In our case, X is a data matrix where each row represents a different sample or observation (e.g. a cell in a single-cell RNA sequencing dataset). W represents a set of "metagenes" (or gene expression patterns) that are shared across patients, and H represents the contribution of each patient to each metagene. (Not sure whether this is on the right track)

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

#### Using Zscores

- Cox Elastic Net gives 94% training R2, 81% test R2
