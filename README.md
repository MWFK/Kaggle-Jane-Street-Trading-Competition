# Kaggle-Jane-Street-Trading-Competition


https://effectiveml.com/using-grid-search-to-optimise-catboost-parameters.html

Gradient Boosting
CatBoost is a gradient boosting library, I'll give a short description of how gradient boosting works in this section (see here for some more info).

'Gradient boosting' comes from the idea of 'boosting' or improving weak models by combining them with many other weak models to create a strong model. Gradient boosting is an extension of boosting where the process of additively generating weak models is formalised as a gradient descent algorithm over an objective function. Gradient boosting is a supervised, which means that it takes a set of labelled training instances as input and builds a model that tries to correctly predict the label of new unseen examples based on features provided.

Many different types of models can be used for gradient boosting, but in practice decision trees are almost always used. To begin training, a single decision tree is build to predict the label. This first decision tree will predict some instances but will fail for other instances. Subtracting the predicted label from the true label shows whether the prediction is an underestimate or an overestimate.

To improve the model, we can build another decision tree, but this time try to predict the residuals instead of the original labels. This can be thought of as building another model to correct for the error in the current model. After adding the new tree to the model, make new predictions and then calculate residuals again. In order to make predictions with multiple trees, simply pass the given instance through every tree and sum up the predictions from each tree. By building predictors that estimate the residual, we are actually minimising the gradient of the squared error between the real and predicted labels.

If we don't want to use squared error, we can use some other differentiable function such as cross entropy, then predict those residuals instead. This covers the basics of gradient boosting, but there are extra terms for e.g. regularisation.


Weak Learner
Decision trees are used as the weak learner in gradient boosting. Specifically regression trees are used that output real values for splits and whose output can be added together, allowing subsequent models outputs to be added and “correct” the residuals in the predictions.


GB vs RF
Like random forests, gradient boosting is a set of decision trees. The two main differences are: How trees are built: random forests builds each tree independently while gradient boosting builds one tree at a time.
