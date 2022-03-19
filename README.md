# Tanzanian Waterpoints: Ternary classification with three ML models
**Author**: [Nick Timpano](mailto:nick.timpano@gmail.com)

## Overview
In this notebook I analyze data on waterpoints located in Tanzania in order to build a model to predict the operational status of a given waterpoint. To do so, I preprocess the data and build three main kinds of machine learning models. I tune hyperparameters, evaluate and test these models and then generate predictions in order to obtain useful insights. 

#### Business Problem / Audience 
Here, I sought to build a model to predict operational status of a given waterpoint, and unlock insights that would be useful to the Tanzanian government, or any party interested in improving waterpoint infrastructure in Tanzania. 

## Data 
The data was provided in three main files: training labels, training values and test values. More Information can be found [here](https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/25/). The csv files can be viewed [here](https://github.com/timpanon/tanzanian_waterpoint_classification). 

## Methods/Techniques 
- Three types of models were fitted: XGBoost, Random Forests, and Logistic Regression 
- Due to the class imbalance, SMOTE oversampling was used. 
![status_group](./plots/labels_analysis.png)
- In order to build models to best identify waterpoints that need care, recall scores for the two in need classes ('functional needs repair' and 'non functional') were maximized. Thus, false negatives (missing waterpoints that need help) were minimized. 

## Results
- XGBoost produced the strongest model in predicting operational status of waterpoints.      
![model comparison](./plots/model_comparison_radar.png)
- The geography (`region`), installer (`installer`), age of the waterpoint (`construction_year`) and amount of water (`quantity_group`) all seem to have a relationship with `status_group`.  
- Waterpoints installed by certain parties seem to have more issues.  
![RWE Installed Waterpoints](./plots/installer_RWE_count_plot.png) 
- These regions were predicted to have the highest concentrations of non functional waterpoints.  
![waterpoint predictions](./plots/map_waterpoints_predictions.png)
- The majority of dry waterpoints are non-functional.  
![dry waterpoints](./plots/quantity_group_dry_plot.png)

## Conclusions 
Based on the model and the analysis of data, these were the findings and recommendations: 
- Visiting waterpoints in locations around Lake Victoria, and targeting waterpoints that were dry is recommended as a first priority. 
- Focusing on these main features was recommended: quantity of water, installer, construction year and region 

## Next Steps 
- Other machine learning algorithms: KNN, Naive Bayes, and Support Vector Machines are missing from the above trials. Due to the size of the data, training time should be considered. 
= More feature selection techniques: Due to the larger number of features present in the dataset, utilizing other methods to refine the feature list could improve model performance and efficiency. 
- Metrics: As mentioned above, the final models chosen in this analysis were based on optimizing for recall of the minority classes. Other metrics, like f-1 score and precision can be prioritized in future studies. In addition other resampling techniques could be experimented with to see if this positively affects results. 
- More feature engineering: Conducting more EDA and experimenting with other ways of creating new features could yield more positive outcomes. 
- Further investigation: Digging deeper into some of the insights. For example, it seems like waterpoints around Lake Victoria have more issues. Why? What makes waterpoints installed by certain parties more likely to have issues?

## More Information 
To see the full EDA please see the [Jupyter Notebook](./tanzania_classification.ipynb). 

For more information, contact [Nick Timpano](mailto:nick.timpano@gmail.com)

## Repo Structure 

```
├── plots
├── tanzania_test_values.csv
├── tanzania_training_labels.csv
├── tanzania_training_values.csv
├── README.md
└── tanzania_classification.ipynb
```