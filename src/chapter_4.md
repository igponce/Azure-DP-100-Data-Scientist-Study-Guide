# Chapter 4: Develop Models

## Certification objetives covered

- Select an algorithmic approach
  - Determine appropriate performance metrics
  - Implement appropriate algorithms
  - Consider data preparation steps that are specific to the selected algorithms

- Split datasets
   - Determine ideal split based on the nature of the data
   - Determine number of splits
   - Determine relative size of splits
   - Ensure splits are balanced

- Identify data imbalances
   - Resample a dataset to impose balance
   - Adjust performance metric to resolve imbalances
   - Implement penalization
   
- Train the model
   - Select early stopping criteria
   - Tune hyper-parameters

- Evaluate model performance
   - Score models against evaluation metrics
   - Implement cross-validation
   - Identify and address overfitting
   - Identify root cause of performance results

## Select an algorithmic approach

Consult the [Azure Machine Learning Algorhtm cheat sheet](https://docs.microsoft.com/en-us/azure/machine-learning/studio/algorithm-cheat-sheet )    

### Determine appropriate performance metrics

### Implement appropriate algorithms

### Consider data preparation steps that are specific to the selected algorithms

After selecting an algorithm, care must be taken to be sure data is in appropiate format for the algoritm to work.

For instance, do we have categorical data?

Some algorithms might not work with categorical data and might need to use a different representation for categorical variables (like one-hot-encoding).

Other algorithms might work better when data is around [-1, 1] range, thus scaling and nomalizing might be needed befor training, and might be undone *after* inference if the dependent variable (what we want to predict) is scaled and normalized.

This latter case is important when we are dealing with distances that have exponentiation (like euclidean distances).


## Split datasets
### Determine ideal split based on the nature of the data
### Determine number of splits
### Determine relative size of splits

### Ensure splits are balanced

When we are splitting a malance dataset into train and test subsets randomly, we might be splitting the dataset inadvertently in an unbalance manner.

Unbalanced data is a bad choice for training a machine learning algorithm because the model will be biased to the class with more training samples. The worst-case scenario is when the model overfits the majority class, and does not learn the minority one.

# Identify data imbalances

## Resample a dataset to impose balance
   See (Kaggle)[https://www.kaggle.com/rafjaa/resampling-strategies-for-imbalanced-datasets]

Two possible strategies are *undersampling* and *oversampling*.

**Undersampling** implies getting _less_ data from the majority class to match the number of samples in the minority.

**Oversampling** is the opposite: we keep the majority class samples intact and make copies from the minority class samples until we match the number of samples in the majority class.

An oversampling technique is (SMOTE)[Synthetic Minority Oversample TEchnique].

**[SMOTE](https://imbalanced-learn.readthedocs.io/en/stable/over_sampling.html#smote-adasyn)** Oversampling consist in generating syntethic data samples between original ones.   

   - Adjust performance metric to resolve imbalances 
   - Implement penalization


## Train the model

###  Select early stopping criteria

### Tune hyper-parameters

## Evaluate model performance

### Score models against evaluation metrics

### Implement cross-validation

### Identify and address overfitting

Overfitting appears when your model learns the training set perfectly; but is not able to generalyze.

Usually the model results with the training set will be better than with the test set... but not **way far** better.

A model overfits when its **training** results are **much, much, better** than its **test result** and the test results are not good.

How to address overfitting?

Ovefitting occurs when you are fitting a model too powerful for the dataset you have.

A good way to address this issue is **penalizing** the use of models with too many parameters, by adding the value of that parameters to the loss function, multiplied by a factor (that we call lambda)

\\[ regularizedLoss(\theta,x) = loss(\theta, x) + \lambda \sum { \theta_i ^ 2 } \\]

This is called **regularization**

### Identify root cause of performance results
