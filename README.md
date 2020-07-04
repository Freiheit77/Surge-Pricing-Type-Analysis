# Surge-Pricing-Type-Analysis
The cab aggregator service is popular nowadays and users could download their app on smartphones and book a cab from anywhere in the cities they operate in. The app will search for cabs from various service providers and provide the best option to their client across available options. The project aims to build the predictive model to help determine the surge pricing type for each trip each based on their characteristics. It could help to allocate resources effectively and improve the transportation efficiency.  

## Data description 
![alt text](https://github.com/Freiheit77/Surge-Pricing-Type-Analysis/blob/master/data%20dictionary.png)

## Data cleaning
1. Missing values are checked and filled in two major ways: naive (mean/median) imputation and KNN imputation
2. Exploratory data analysis for continuous and categorical variables  

## Model development 
1. Random forest (based on data by naive imputation; based on data by knn imputation)
2. CatBoostClassifier 
3. LightGBM
4. XGBoost
