# moa-classification
[Download data](https://www.kaggle.com/c/lish-moa/data)

[NBViewer](https://nbviewer.jupyter.org/github/Mainakdeb/moa-classification/blob/master/moa-classification.ipynb)

## Notes [reference](https://www.kaggle.com/c/lish-moa/discussion/184005)
* Metric is log loss (aka cross entropy). This is beneficial as there will be no gap between the loss and competition metric. On the other hand, this metric has been criticized for being unintuitive and a bad fit for highly unbalanced problems such as this.
* Alternative loss functions:
  * AUC
  * Hamming Loss
  * Jaccard Index
  * Micro/Macro-averaging
  * Exact Match Ratio
  * Top-k Error

## Needs urgent fix
* Inconsistent validation losses on the same validation set with `model.eval()` possibly because we load it with `shuffle = True`

## Checklist/To-do
* ~Check performance on scaled and unscaled data~ -> used `sklearn.preprocessing.Normalizer()`
* ~try `sklearn.compose.ColumnTransformer`~
* ~try using log loss~ -> BCEWithLogits is the way to go 
* ~use K-Fold Cross validation~  -> works 
* ~exploit the fact that for all features where `features.cp_type ==  "ctl_vehicle"` the corresponding labels are all zeros [reference](https://www.kaggle.com/nicohrubec/pytorch-multilabel-neural-network), check the last cell~ -> new best score
* ~use only the top features~ [reference](https://www.kaggle.com/simakov/keras-multilabel-neural-network-v1-2)
* Bunch of novel [ideas](https://www.kaggle.com/c/lish-moa/discussion/183377): 
  * Try out [Stratified K fold](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html)
  * ~Try using MultiLabelStratifiedKFold from iterstat~ [video](https://youtu.be/VRVit0-0AXE?t=1704), time = `28:24` -> using now  
  
* thread on [model blends](https://www.kaggle.com/c/lish-moa/discussion/185650)
* **try out ensemble nets** [Great video](https://www.youtube.com/watch?v=TuIgtitqJho&t=1779s)
* need to balance the multilabel targets --mainak -> model fails to generalise becuse class distribution may be different in test set
* ~Use [label powersets](http://scikit.ml/api/skmultilearn.problem_transform.lp.html) - Transform the multi-label problem to a multi-class problem --mayukh~
* ~try training on only non zero labels, and hardcode the rest~ kind of works, but hard to say yes because of a possible bottleneck on the model
* ~move to [optuna](https://optuna.org/)~ -> optuna implemented
* pre-set training folds
* Another possibility:
    * Where we train 2 models on 2 halves of the target tensor of size 206, and then stack them horizontally for inference 
* Ecode cp_time into 3 seperate binary columns -> under way

* **Interesting properties**:
    * For target columns `atp-sensitive_potassium_channel_antagonist` and `erbb2_inhibitor` all rows are `0` where `cp_dose == 'D2'`
    * For target columns `atp-sensitive_potassium_channel_antagonist` and `erbb2_inhibitor` all rows are `0` also where `cp_time != 48`
* [only notebook](https://www.kaggle.com/utkukubilay/pytorch-moa-0-01867) better than our 0.01872
