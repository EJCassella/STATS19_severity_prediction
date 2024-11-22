# STATS19_severity_prediction

👷‍♀️ under construction 👷‍♀️

### Introduction

Welcome to my STATS19 severity prediction repo.!

The aim of the model developed here is to use the STATS19 'Casualty' and 'Collision' datasets and see whether we can predict the severity of the Casualty's injuries. Specifically, we are focusing on the data from South Yorkshire.

What could this model be used for?

Using the feature importances of the developed model, we could:

- Determine whether the data captured in these STATS19 records are sufficient to predict collision outcomes. (evaluate data quality)
- Target safety courses / information for particularly vulnerable road users. (resource allocation)
- Compare / contrast contributary factors between South Yorkshire and the rest of Great Britain, idetifying where road safety can be improved in this region. (anomaly detection)
- Where / if particular road features are identified as strongly associated with Serious collision outcomes, can we map these back to the roads in South Yorkshire and identify where physical changes to the roads might improve safety (resource allocation).

The datasets used in this project are available on the data.gov.uk website:
https://www.data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data

Specifically, the "Road Safety - Casualties last 5 years" and "Road Safety - Collisions last 5 years" have been used (downloaded on 2024-11-22).

### Key considerations

- Predictor is grouped as 'slight' or 'serious', a.k.a KSI (killed or seriously injured). If we are trying to predict which features lead to the most serious injuries, distinguishing between a serious injury or death seems unnecessary and makes model evaluation a lot more complicated.
- The dataset for South Yorkshire is not huge, so using cross-validation (to use as much data as possible for training) seems more appropriate than having a trianing-validation-testing split.
- There is a large imbalance in the 'slight' or 'serious' classes, so we need to evaluate our model appropriately and potentially consider additional techniques to improve the model performance. We also need to ensure the training and testing data is appropriately stratified (also using stratified K fold cross-validation).
- There are multiple entries for some of the accident references, i.e. where there are multiple casualties. We should be careful that there isn't data leakage between the training and testing datasets if the same collision is split between the two.
- This dataset has a large number of high-cardinality categorical features. This will take quite some playing around to encode the data appropriately without leading to severe model overfitting.

### Planned future work

- Improved feature selection and engineering to reduce overfitting and capture some data trends better (e.g. 'rush_hour').
- Try additional techniques to improve performance on our unbalanced dataset, namely over or undersampling methods.
- Pull out the feature importances from the final model.
- Evaluate the model on our testing data once it's fine tuned (the key will be reducing the overfitting).
- Look to include the "Vehicle" data to improve model performance.
- Look to include other datasets that might enhance what we already have (e.g. accurate weather information? traffic volume / use data?)
