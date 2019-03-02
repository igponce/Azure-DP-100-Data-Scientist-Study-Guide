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

Sometimes you need to stop training a model because it does not improve.
When you are training a model in front of a termina or notebook, it is easy to spot that the model does not improve, or it's overfitting.

If you're running a model in the background as part of a process, or you are not able to monitor this training, then it is useful to have an early stopping criteria.

For example, [Keras](https://keras.io) has a callback called [EarlyStopping]() that is triggered when the model does not improve after a number of epochs (defined by the 'patience' parameter):

```{python}

checkpointer = ModelCheckpoint(filepath='/tmp/weights.hdf5', verbose=1, save_best_only=True)

earlyStop = EarlyStopping(monitor='val_loss',
   min_delta=0.0001, 
   patience = 4, # Number of epochs to wait without improvement
   verbose = 0, 
   mode = 'auto', # 'min' = loss should be descendig, 'max' = loss should be ascending, 'auto' = choose automatically from results on first run
   baseline = None, # Baseline value for the monitored quantity to reach. Training will stop if the model doesn't show improvement over the baseline.
   restore_best_weights = False )
model.fit(x_train, y_train, batch_size=128, epochs=20, verbose=0, validation_data=(X_test, Y_test), callbacks=[checkpointer, earlyStop ])


```

### Tune hyper-parameters

We call **hyper-parameters** the arguments we supply to the machine learning algorithm (not the training data).

For instance, a LeakyRelu activation function is defined as 

\\[ f(x) = 
   \begin{cases} 
   x,          & \text{if $x$> 0 } \\\\
   \beta x, & \text{ otherwise } 
   \end{cases}
\\]

In this case \\( \beta \\) is an hyperparameter. It defines part of the model structure and remains fixed during the training; **but** there.

Other kinds of hyperparameters examples are learning rate, tree depth (in random forest), etc.

If *hyperparameters* are fixed during training, and shape so much the model performance and outcome, how can we choose the best values for them?

The answer is simple, but surprising at first sight: training the model, and use gradient descent on the hyperparameter space to get the best values.

This approach has a catch, too: you need data to find the best hyperparameter values, and that data cannot be used later for training or validation because you'll introduce bias.

The solution is splitting the dataset into 3 subsets: Train, Test, and Cross-validation (xval).

The cross-validation set wil be used first to get the best hyperparamenters for the model (or even choose which kind of model works best) 

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
