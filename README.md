# MSK_brain_lower_grade_glioma_project

<img src="image.jpg" width="800" height="200"/>

Each member focused his analysis on a specific dependent variable

# Siqi

# Jin
## I focused on predicting the **Mutation count**. 
### The models I used right now is linear regression, but I consider to change to others like Lasso regression to improve the accuracy and R-squared value. 
### Results
-Mean squared error: 8100.792835393206
R-squared: -45.47660982946169
-Not informative yet and will improve on that. 

# Emile

## I focused on predicting the **Survival Rate**. 

### The features I use are
- Gene expression
- Clinical data (age, sex, race, prior diagnosis, radiation therapy...)

### The models I used:

- LASSO
- Random Forest
- GradientBoosting
- SVM
- Cox Survival Model Elastic Net

### Results
- Cox Elastic Net is the only decent model, with **87%** R2 on testing data
- Feature importance and explainability: Diagnosis Age plays an important role, as well as genes 118430, 55970, 406, 4214
