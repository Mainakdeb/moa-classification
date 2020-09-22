# moa-classification
[Download data](https://www.kaggle.com/c/lish-moa/data)

[NBViewer](https://nbviewer.jupyter.org/github/Mainakdeb/moa-classification/blob/master/moa-classification.ipynb)

## Checklist/To-do
* ~Check performance on scaled and unscaled data~ -> used `sklearn.preprocessing.Normalizer()`
* ~try `sklearn.compose.ColumnTransformer`~
* batch size goes from 128 to 64 gradually 
* ~try using log loss~ -> BCEWithLogits is the way to go 
* implement [`VarianceThreshold`](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.VarianceThreshold.html) for feature selection
* ~use K-Fold Cross validation~  -> works 
* exploit the fact that for all features where `features.cp_type ==  "ctl_vehicle"` the corresponding labels are all zeros [reference](https://www.kaggle.com/nicohrubec/pytorch-multilabel-neural-network), check the last cell
* use only the top features [reference](https://www.kaggle.com/simakov/keras-multilabel-neural-network-v1-2)
