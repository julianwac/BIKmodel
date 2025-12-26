# BIK model

Model credit risk and examine models using shapley values 

# TODO:
1. **Create model chalangers** (like logistic regression) for result comparison (it is in project description)
2. **Handle missing values in consitent way** - LightGBM (modification of XGBoost) treats missing values as meaningful data observation during model training/predition. Check if using 0 to fill missing values is meaningful for all columns. In case that missing values do not have meaningful interpretation, try to inpute it in some way. **01_loaddata.ipynb**
3. **Rebalance data samples** - Currently % of defaulted (STATUS=1) customers is significantly different between both samples which influence the predicted probabilities. In sample with higer % of defaults models will be more likly to assing higher default probs. Shapley values are based on predicted probabilities so thier interpretation might be different. It might be beneficial to rebalance both samples using bootstraping to aling them on % of defaults. **01_loaddata.ipynb**
3. **Feature engenering** - Should we transform variables in anyway (log, WoE, Binning)? Can we create any additional features? Should we use all columns for modeling? Most columns should have high correlation and reflect similar information. **01_loaddata.ipynb**
4. **Dependence plots** - Feature and predition values relations have expected trends? (Model predict higher risk for customers with high debt) **03_compare_models.ipynb**
5. **Predition explainability** - Explain preditions for specific observations. Do they differ between models? (for example force plots show it, in general shapley values explain how each variable influenced final predition) **03_compare_models.ipynb**
6. **LIME** - so far we used only SHAP values for explainablity. Check if results from Local Interpretable Model-Agnostic Explanations differ. Here is [link to LIME documentation](https://lime-ml.readthedocs.io/en/latest/)

**Check description of project on enauczaniu.**  
**Do we have eveything?**

## Folder structure

Code:
* 02_skrypty - load and transform raw data

Current code are in top level jupiter files like:
* 01_loaddata.ipynb
* 02_train_model_new.ipynb
* 02_train_model_old.ipynb
* 03_compare_models.ipynb


Data:

All data is in 01_dane:
* 02_dane_finlne - baseline datafile from last semester
* 03_modeling_data - ready to use csv, with new, old data and modeling/validation samples
* 04_models - saved pickles with trained models

03_results - stores all relevant plots from modeling and testing


## Remarks

Default definition between both datasets is not consitent. 
For this reason, results and models are not comparable and **any conclutions are meaningless**.

New dataset from BIK has status column with values 0,1,2 while the old dataset has values only 0,1.
* It was assumed that 0,1 in new data sample means non-default while 2 means default. 
* In old dataset it was assumed that 1 means default.

Such assumptions might be not valid, however BIK is not willing to provide more data with consitent column definitons. 
Additionaly provided datasets do not have any documentation.

It is assumed that datasets comes from different years, however there is no column like income, that could help to weight risk factors and make them **relative**. For example:

* Sum of instalments/debt is not good risk factor. It should be compared with income to differentiate between different economic situation of customers. 
* Customer earning 1 000 PLN with debt of 500 000 PLN, has greater risk then someone earning 50 000 PLN with the same debt.
* Due to inflation using raw monetary values **might result in deterioation of model quality overtime**

