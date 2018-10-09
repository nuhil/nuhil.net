+++
languageCode = "bn-bd"
title = "How to choose right algorithm or model for my machine learning task"
author = "Nuhil Mehdy"
categories = ["AI", "Machine Learning", "Deep Learning", "Data Science", "Algorithm"]
tags = ["AI", "Machine Learning", "Deep Learning", "Data Science", "Algorithm"]
date = 2018-10-01T00:00:00-00:00
description = "List of popular machine learning algorithms, models or estimators as a cheat sheet."
featured = ""
featuredalt = "Machine Learning Algorithms"
featuredpath = ""
linktitle = ""
type = "post"
+++

I've been curating a list of popular machine learning algorithms, models or estimators in a single table as a handy cheat sheet. Each of them has attached reference links for quick look up. So far, my resources are [Microsoft Azure ML](https://studio.azureml.net/), [Scikit-learn](http://scikit-learn.org/stable/), [Tensorflow](https://www.tensorflow.org/). I will be adding more variants of these algorithms and models with specific reference frequently.

| Regression | Two-class Classification | Multi-class Classification | Clustering | Anomaly Detection | Dimensionality Reduction |
|---|---|---|---|---|---|
|Linear Regression<sup>[1](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html), [2](https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/linear-regression)</sup>|Logistic Regression<sup>[1](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html), [2](https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/two-class-logistic-regression)</sup>|Logistic Regression<sup>[1](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html), [2](https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/two-class-logistic-regression)</sup>|Gaussian mixture model<sup>[1](http://scikit-learn.org/stable/modules/mixture.html)</sup>|PCA-based Anomaly Detection<sup>[1](https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/pca-based-anomaly-detection)</sup>|Principal Component Analysis<sup>[1](http://scikit-learn.org/stable/modules/decomposition.html#principal-component-analysis-pca)</sup>|
|Bayesian Linear Regression<sup>[1](https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/bayesian-linear-regression)</sup>|Bayes’ Point Machine<sup>[1](https://docs.microsoft.com/en-us/azure/machine-learning/studio-module-reference/two-class-bayes-point-machine)</sup>|Linear Discriminant Analysis<sup>[1](http://scikit-learn.org/stable/modules/lda_qda.html)</sup>|||Linear Discriminant Analysis<sup>[1](http://scikit-learn.org/stable/modules/lda_qda.html)|
|Boosted Decision Tree<sup>[1](https://msdn.microsoft.com/library/azure/dn905801.aspx)</sup>|Boosted Decision Tree<sup>[1](https://msdn.microsoft.com/library/azure/dn905801.aspx)</sup>||||Kernel Approximation<sup>[1](http://scikit-learn.org/stable/modules/kernel_approximation.html)</sup>|
|Decision Forest<sup>[1](https://msdn.microsoft.com/library/azure/dn905862.aspx), [2](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html)</sup>|Decision Forest<sup>[1](https://msdn.microsoft.com/library/azure/dn905862.aspx), [2](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)|Decision Forest<sup>[1](https://msdn.microsoft.com/library/azure/dn905862.aspx), [2](http://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)|||Locally Linear Embedding<sup>[1](http://scikit-learn.org/stable/modules/manifold.html#locally-linear-embedding)</sup>|
|Fast Forest Quantile<sup>[1](https://msdn.microsoft.com/library/azure/dn913093.aspx)</sup>|Decision Jungle<sup>[1](https://msdn.microsoft.com/library/azure/dn905976.aspx)</sup>|Decision Jungle<sup>[1](https://msdn.microsoft.com/library/azure/dn905976.aspx)||||
|Support Vector Regression<sup>[1](http://scikit-learn.org/stable/modules/svm.html#regression)</sup>|Support Vector Machine<sup>[1](http://scikit-learn.org/stable/modules/svm.html#classification), [2](https://msdn.microsoft.com/library/azure/dn905835.aspx)</sup>|||Support Vector Machine<sup>[1](https://msdn.microsoft.com/library/azure/dn913103.aspx)</sup>||
|Ridge Regression<sup>[1](http://scikit-learn.org/stable/modules/linear_model.html#ridge-regression)</sup>|Locally Deep Support Vector Machine<sup>[1](https://msdn.microsoft.com/library/azure/dn913070.aspx)</sup>|||||
||Linear Support Vector Classifier<sup>[1](http://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html#sklearn.svm.LinearSVC)</sup>|||||
|K Nearest Neighbors<sup>[1](http://scikit-learn.org/stable/modules/neighbors.html#regression)</sup>|K Nearest Neighbors<sup>[1](http://scikit-learn.org/stable/modules/neighbors.html#classification)</sup>|K Nearest Neighbors<sup>[1](http://scikit-learn.org/stable/modules/neighbors.html#classification)|K-means<sup>[1](http://scikit-learn.org/stable/modules/clustering.html#k-means)</sup>|K-means<sup>[1](http://scikit-learn.org/stable/modules/clustering.html#k-means), [2](https://msdn.microsoft.com/library/azure/5049a09b-bd90-4c4e-9b46-7c87e3a36810/)||
|Ordinal<sup>[1](https://msdn.microsoft.com/library/azure/dn906029.aspx)</sup>||One-v-all<sup>[1](https://msdn.microsoft.com/library/azure/dn905887.aspx)</sup>||||
|SGD Regressor<sup>[1](http://scikit-learn.org/stable/modules/sgd.html#regression)</sup>|SGD Classifier<sup>[1](http://scikit-learn.org/stable/modules/sgd.html#classification)</sup>|||||
|Poisson<sup>[1](https://msdn.microsoft.com/library/azure/dn905988.aspx)</sup>||||||
|Lasso<sup>[1](http://scikit-learn.org/stable/modules/linear_model.html#lasso)</sup>||||||
|ElasticNet<sup>[1](http://scikit-learn.org/stable/modules/linear_model.html#elastic-net)</sup>||||||
|Neural Network<sup>[1](https://www.tensorflow.org/tutorials/keras/basic_regression), [2](https://msdn.microsoft.com/library/azure/dn905924.aspx)</sup>|Neural Network<sup>[1](https://www.tensorflow.org/tutorials/keras/basic_classification), [2](https://msdn.microsoft.com/library/azure/dn905947.aspx)</sup>|Neural Network<sup>[1](https://www.tensorflow.org/tutorials/keras/basic_classification), [2](https://msdn.microsoft.com/library/azure/dn906030.aspx)</sup>||||