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

Consult the (Azure Machine Learning Algorhtm cheat sheet)[
https://docs.microsoft.com/en-us/azure/machine-learning/studio/algorithm-cheat-sheet ]

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
   - Resample a dataset to impose balance
   - Adjust performance metric to resolve imbalances 
   - Implement penalization
   
## Train the model
###  Select early stopping criteria
### Tune hyper-parameters

## Evaluate model performance
### Score models against evaluation metrics
### Implement cross-validation
### Identify and address overfitting
### Identify root cause of performance results