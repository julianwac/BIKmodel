# BIK model

Model credit risk and examine models using shapley values 


## Folder structure

Code:
* 02_skrypty - load and transform raw data

Current code are in top level jupiter files like:
* 01_loaddata.ipynb
* 02_train_model1.ipynb
* 02_train_model2.ipynb
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
