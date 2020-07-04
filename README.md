# Surge Pricing Type Analysis
The cab aggregator service is popular nowadays and users could download their app on smartphones and book a cab from anywhere in the cities they operate in. The app will search for cabs from various service providers and provide the best option to their client across available options. The project aims to build the predictive model to help determine the surge pricing type for each trip each based on their characteristics. It could help to allocate resources effectively and improve the transportation efficiency.  

## Data description 
![alt text](https://github.com/Freiheit77/Surge-Pricing-Type-Analysis/blob/master/pictures/data%20dictionary.png)

## Data cleaning
1. Missing values are checked and filled in two major ways: naive (mean/median) imputation and KNN imputation
2. Exploratory data analysis for continuous and categorical variables  

## Model development 
1. Random forest (based on data by naive imputation; based on data by knn imputation)

       1）These two datasets gave almost the same OOS accuracy. 
       3) Half of the data were missing in 'Var1' variable and its feature importance increased in the model underlying knn imputation than naive imputation. 

2. CatBoostClassifier 

       1) It supports multiple Categories of data, such as audio, text, image including historical data and could handel them automatically. We can use CatBoost without any explicit pre-processing to convert categories into numbers. CatBoost converts categorical values into numbers using various statistics on combinations of categorical features and combinations of categorical and numerical features.  
       2) CatBoost does not require conversion of data set to any specific format like XGBoost and LightGBM.
       3) It reduces the need for extensive hyperparameter tuning and lower the chances of overfitting also which leads to more generalized models.
       
3. XGBoost

       1) XGBoost is a scalable decision-tree-based ensemble Machine Learning algorithm that uses a gradient boosting framework.
       2) It penalizes more complex models through both LASSO (L1) and Ridge (L2) regularization to prevent overfitting.
       3) The algorithm comes with built-in cross-validation method at each iteration.
      ![alt text](https://github.com/Freiheit77/Surge-Pricing-Type-Analysis/blob/master/pictures/Evolution%20of%20XGBoost%20Algorithm%20from%20Decision%20Trees.png)
       
4. LightGBM
       
       1) Light GBM is a gradient boosting framework that uses tree based learning algorithm.
       2) Light GBM grows tree leaf-wise while other algorithm grows level-wise. It will choose the leaf with max delta loss to grow. When growing the same leaf, Leaf-wise algorithm can reduce more loss than a level-wise algorithm. 
       3) Light GBM can handle the large size of data and takes lower memory to run. (faster than XGBoost)
       4) It is not suggested for small datasets (fewer than 10k rows). Light GBM is sensitive to overfitting and can easily overfit small data.
      ![alt text](https://github.com/Freiheit77/Surge-Pricing-Type-Analysis/blob/master/pictures/leaf-wise%20vs%20level-wise.png)

5. [Parameter tuning](https://github.com/Freiheit77/Surge-Pricing-Type-Analysis/blob/master/pictures/XGBoost%20vs%20CatBoost%20vs%20LightGBM.png)

## Cross validation methods
1. StratifiedKFold:
       
       1) The folds are selected so that the mean response value is approximately equal in all the folds. 
       2) The StratifiedKFold is used in classification problems, which means the estimator is a classifier and y is either binary or multiclass.
       
2. KFold

       1) It could be used in both classification and regression problems.
       
## Result 
1. The top 3 important features in these algorithms were Trip_Distance, Customer_Rating and Life_Style_Index.
2. Model comparison: 

       

### Reference
1. [What is LightGBM, How to implement it? How to fine tune the parameters?](https://medium.com/@pushkarmandot/https-medium-com-pushkarmandot-what-is-lightgbm-how-to-implement-it-how-to-fine-tune-the-parameters-60347819b7fc)
2. [XGBoost Algorithm: Long May She Reign!](https://towardsdatascience.com/https-medium-com-vishalmorde-xgboost-algorithm-long-she-may-rein-edd9f99be63d)
3. [XGBOOST vs LightGBM: Which algorithm wins the race](https://towardsdatascience.com/lightgbm-vs-xgboost-which-algorithm-win-the-race-1ff7dd4917d)
4. [Good summary of XGBoost vs CatBoost vs LightGBM](https://www.kaggle.com/c/LANL-Earthquake-Prediction/discussion/89909)
5. [CatBoost vs. Light GBM vs. XGBoost](https://towardsdatascience.com/catboost-vs-light-gbm-vs-xgboost-5f93620723db)
