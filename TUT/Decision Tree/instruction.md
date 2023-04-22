# Tutorial: Tree-based Method
For today's tutorial, I will mainly use jupyter notebook (or JupyterLab).
You can write and run the code with me to better understand the content.
There are two notebooks in this folder:
- `demo.ipynb`: A notebook with full codes (if you can understand all the content, I think you do not need to attend this tutorial)
- `demo_blank.ipynb`: You can use this notebook to write and run codes with me.

The following is the list of the version of packages (just in case you encounter errors related to the version):
- jupyterlab: 1.2.6
- matplotlib: 3.6.1
- numpy: 1.23.4
- pandas: 1.5.0
- scikit-learn: 1.1.2

The following is FAQ of this content, you can take a look.
1. Why the test accuracy was worse in the best parameters.
    - This is because the best parameters are determined only by the training dataset (more specifically, validation dataset). So, when you compare the models in test dataset, the model with best parameters is not necessarily the best in accuracy.

2. How to calculate the feature importances
    - Feature importance shows how many times each feature was used in splitting the distribution in each node. In sklearn, we get the normalized version.

3. How to access the classifiers in BaggingClassifier
    - `BaggingClassifier` contains multiple classifiers. And, you can access them by `clf.estimators_[i]`, where i is the index of the models.

4. `random_state` in BaggingClassifier
    - One of the usages of `random_state` in `BaggingClassifier` to determine the `random_state` of `DecisionTreeClassifier`. So,  `random_state` set in `DecisionTreeClassifier` will be ignored.
    - So, you don’t need to set `random_state` in `DecisionTreeClassifier` if you use it for `BaggingClassifier`.

5. Difference Between min_samples_split and min_samples_leaf
    - `min_samples_leaf`: the minimum number of samples of each leaf. So, if you set this as 3, you can’t create a leaf with less than 3 nodes(samples).
    - `min_samples_split`: the minimum number of samples that will be considered for splitting. So, if you set this as 10, the node with 5 samples can’t be considered for splitting (the node becomes a leaf).