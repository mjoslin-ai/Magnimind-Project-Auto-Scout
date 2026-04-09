# Magnimind


## Preprocessing

### Scaling
Many algorithms are sensitive to scale of features

Scale when using KNN, SVM, neural net, logistic regression (many features), PCA, clustering

 Types:

  * StandardScaler: zero mean and a standard deviation of one

  * RobustScaler: computes the median and quartiles, not skewed by outliers

 * MinMaxScaler: shifts features so they are between 0 and 1

 * Normalizer: scales each row to a unit vector, which maintains direction angle

 * MaxAbsScaler: used on sparse data when most features are zero and sets the maziumum absolute values to one

### Pipelines
* Used to avoid data leakage, where preprocessing (scaling, feature selection, etc.) must be applied independently to each fold during cross-validation.

* Pipeline chains preprocessing steps + final estimator into a single object.

* Calling .predict() or .score() applies the same fitted transformations (learned during .fit()) to new data, no leakage.

### Principal Component Analysis (PCA)

**Logic:**

* Linear transformation to maximize variance with principal components that reduces dimensionality.

* Scaling is very important for PCA to maximize variance.

**Parameters:**

* n_components: The number of principal components you want to keep. This can be a fixed number (e.g., 2 or 3) or a percentage of variance you want to retain (e.g., 0.95).

# Models

## Linear Regression

### Ordinary Least Squares
**Logic:** 
* Minimize the sum of the squares of the differences between the actual values (yi​) and the predicted values (y^​i​).

**Parameters:**
* Weights (w or coef_): These are the coefficients assigned to each feature. They represent the "strength" and direction of the relationship. A high positive weight means the feature has a strong positive impact on the prediction.

* Bias (b or intercept_): Also known as the intercept, this represents the value of y when all input features are zero.

### Ridge Regression
**Logic:**
* Minimize the squared difference between predictions and actual values

* Keep the "size" (the L2 norm) of the weight vector w as small as possible.

* By pushing coefficients toward zero, it decreases the "slope" of the model, making it simpler and less sensitive to noise.

**Parameters:**
* Alpha (α=0): The penalty is gone. The model is identical to Ordinary Least Squares.

* Alpha (α=∞): The penalty is so high that all weights (w) are pushed to zero, resulting in a flat, constant model.

* Optimal α is problem-specific, use Grid Search (typically GridSearchCV) to find the best value.

**Why use Ridge?:**
* Better than OLS when there is less data, where a complex model will easily "memorize" the noise.

* In OLS, highly correlated features can cause coefficients to "explode," where ridge forces these into a "reasonable range."

### Lasso Regression

**Logic:**
* Lasso (Least Absolute Shrinkage and Selection Operator) is similar to Ridge Regression, but it changes the math behind the penalty. While Ridge uses the sum of squares (L2), Lasso uses the sum of absolute values (L1).

**Parameters:**
* Low α: The model behaves like Ordinary Least Squares.

* High α: More coefficients are pushed to zero. If α is too high, all coefficients can become zero, leaving you with a model that predicts nothing.

**Why use Lasso?:**
* Highly attractive for high-dimensional data where it can reduce a complex model (e.g., 104 features) down to a much smaller subset (e.g., 64 non-zero features).

## Linear Classification

### Logistic Regression

**Logic:**
* Logistic Regression is a classification algorithm that applies a transformation to turn a real number into a probability.

* Uses Log-Loss instead of Mean Squared Error, a penalty for predicting a high probability for the wrong class.

**Parameters:**
* Small C (C=1/α): High regularization (strong penalty), leading to a simpler model.

* Large C: Low regularization (weak penalty), allowing the model to fit the training data more closely.

## Both

### SVM

**Logic:**
* While Logistic Regression tries to maximize the probability of the data, the Linear SVM focuses on geometry. It aims to find the widest margin that separates two classes.

* Large Margin: Better generalization and less prone to overfitting.

* Small Margin: Higher risk of overfitting as the model "tightens" too much around specific data points.

**Parameters:**

C controls the trade-off between margin width and misclassification.

* Low C (C=1/α, e.g., 0.1): Wider margin width

* High C (e.g., 1.0): Narrower margin width

### Decision Trees

**Logic:**
* Root Node: The top-level question that initiates the first split.

* Internal Nodes: Points where the data is split further based on a feature threshold.

* Leaves (Terminal Nodes): The final regions containing the predicted class (usually the majority class of the points in that region).

* The goal of every split is to maximize Purity—meaning the resulting subsets should consist mostly of one class.

**Parameters:**
* Gini Index: A measure of how often a randomly chosen element would be incorrectly identified. Lower is better.

* Entropy: Measures the "disorder" or uncertainty in the data.

    * Entropy = 0: The node is perfectly pure (all instances belong to one class).

    * High Entropy: The classes are spread out (e.g., a 50/50 split).

### Ensemble

* Combine multiple individual machine learning models to improve prediction accuracy

**Logic:**
* Categorized by how they build and combine their base estimators

* Averaging (Bagging) Methods
    * Principle: Build several estimators independently and average their predictions.

    * Goal: Reduce variance (overfitting).

    * Examples: Bagging, Random Forests.

* Boosting Methods
    * Principle: Build estimators sequentially. Each new model attempts to correct the errors (reduce the bias) of the previous models.

    * Goal: Reduce bias (underfitting) and combine weak models into a powerful one.

    * Examples: AdaBoost, Gradient Tree Boosting.

**Parameters:**
* A Voting Classifier is a meta-model that trains several different types of models (e.g., Logistic Regression, SVM, Random Forest) on the same data and aggregates their results.

* Hard Voting
    * Majority rule: The class that gets the most "votes" from the individual classifiers wins.

* Soft Voting
    * Weighted average: Averages the predicted probabilities for each class and picks the one with the highest average.

## Clustering

Discovery of natural groups and derive features from clusters

* High Intra-cluster Similarity: Data points within the same group are as similar as possible.
* High Inter-cluster Dissimilarity: Data points in different groups are as different as possible.

### K-Means

**Logic:**

* Step 1: You pick a number for k (Pro Tip: Using init='k-means++' is the modern standard, as it places initial centroids far apart to speed up convergence.)
* Step 2: Cluster Assignment
* Step 3: Move the Centroid
* Step 4: Repeat until Convergence

**Parameters:**

* n_clusters (k): The number of groups you want the algorithm to find.

**Optimal k:**

* Elbow Method: Find the "elbow" point where the rate of decrease levels off significantly. Adding more clusters beyond this point provides diminishing returns.
* Silhouette Method: An average score close to +1 indicates well-defined clusters. You choose the k that yields the highest average silhouette score across the whole dataset.

Use Elbow when you need a quick, visual "good enough" answer.

Use Silhouette when you want to ensure that your clusters are actually distinct from one another and not just "tightly packed."

### Hierarchical Clustering

**K-Means vs. Hierarchical Clustering:**

* While K-Means tries to find the "center" of groups, Hierarchical Clustering focuses on the relationships between data points, building a tree-like structure of clusters.

* No need to pre-define k.

* Can find clusters of various shapes and does not Assumes clusters are spherical. 

**Logic:**

* Start at the bottom: Treat every single data point as its own individual cluster.
* Find the closest pair: Identify the two clusters that are the most similar based on a distance metric (like Euclidean distance).
* Merge them: Combine those two into a single, larger cluster.
* Repeat: Keep merging the closest clusters until only one giant cluster (containing all data points) remains.

**Dendrogram:**

It is a diagram that records every merge the algorithm made.

* Y-Axis: Represents the distance (dissimilarity) between clusters. The higher the horizontal line, the more different the clusters were when they merged.
* X-Axis: Represents the individual data points.

**Finding the Optimal k:**

Look for the "tallest" vertical lines to make your cut, representing the most distinct groups.