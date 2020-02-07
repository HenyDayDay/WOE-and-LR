# WOE-and-LR
Traditional Credit Scoring/Underwriting Model with Weight of Evidence (WOE), Logistic Regression(LR), CatBoost, Xgboost, and LightGBM-based feature selection. 

In the big data era, one of the major challenging is to deal with massive features. In subprime financial market, thousand of variables are collected from credit bureau like TransUnion, Experian, Equifax, and etc. The raw datasets usually contain 1000 variables to 7000 variables. 

Traditional credit scoring using information value to select variables, it can be improved through introducing machine learning based feature selection methods. Our proposed method has been validated in the real credit data like personal loan and auto loan. It boosts the KS performance 30% on average compared to information-value based feature selection. 

Due to the strictly requirement if regulation and interpretability, we only use gradient boost tree in feature selection, we believe the excellent feature engineering can achieve similar performance with gradient boost tree by using logistic regression. 

The purpose of this repository is to create a pipeline of python codes including data preprocessing, feature selection, feature engineering, modeling, scorecard and evaluation. 


1. Data Preprocessing includes a variety of statistical analysis, e.g. Univariate analysis, Bi-variate analysis, distribution 

2. Feature Selection: LightGBM, Xgboost, CatBoost. We 
    We only recommend CatBoost when there are many categorical variables since it takes long time to run on CPU. The author claimed it run much faster on GPU but I never have chance to validate it. Hyperparameter: Bayesian Optimization

3. Feature Engineering: OneHotEncoder, missing value imputation, Weight of Evidence, Special value
    special value cause significant shift in logistic regression. e.g. Experian used the larget number as special value, like 96, 97, 98,99 or 996,997,998, 999. However, the special value usually represents no trades or no activities which is similar to 0.  
    missing value: we have seen performance of missing values change over years since these bureaus can collect more data for users. 
    
4. Modeling: Logistic Regression with regularization (e.g. L1 and L2)
   Stepwise LR with Backward Sequential Feature Selection

5. Scorecard: user-defined parameters: Factor, pdo (Points to double the odds), offset

6. Evaluation: KS and AUC, Correlation, P value and VIF (Variance inflation factors) It's old-school and boring statistics but your boss will like them
