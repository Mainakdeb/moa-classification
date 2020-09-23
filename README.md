# moa-classification
[Download data](https://www.kaggle.com/c/lish-moa/data)

[NBViewer](https://nbviewer.jupyter.org/github/Mainakdeb/moa-classification/blob/master/moa-classification.ipynb)

## Notes
* This is not a multilabel classification problem. This is a multilabel probability prediction problem


## Checklist/To-do
* ~Check performance on scaled and unscaled data~ -> used `sklearn.preprocessing.Normalizer()`
* ~try `sklearn.compose.ColumnTransformer`~
* batch size goes from 128 to 64 gradually 
* ~try using log loss~ -> BCEWithLogits is the way to go 
* implement [`VarianceThreshold`](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.VarianceThreshold.html) for feature selection
* ~use K-Fold Cross validation~  -> works 
* ~exploit the fact that for all features where `features.cp_type ==  "ctl_vehicle"` the corresponding labels are all zeros [reference](https://www.kaggle.com/nicohrubec/pytorch-multilabel-neural-network), check the last cell~ -> new best score
* use only the top features [reference](https://www.kaggle.com/simakov/keras-multilabel-neural-network-v1-2)
* Bunch of novel [ideas](https://www.kaggle.com/c/lish-moa/discussion/183377): 
  * Try out [Stratified K fold](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html) 
  * Look at the `target_counts` used [here](https://www.kaggle.com/gogo827jz/fork-of-keras-multilabel-neural-network) for stratified k fold 
* thread on [model blends](https://www.kaggle.com/c/lish-moa/discussion/185650)
* try out ensemble nets (split based on data type)
