# Machine Learning
Here are two definitions:

- **Machine learning** is a set of methods that can automatically detect patterns in data and then apply those patterns to predict future data (or perform some other form of decision making). 
- **Machine learning** refers to the automated detection of meaningful patterns in data. 

There are three key ingredients to machine learning:
- **data**, collected from past observations.
- **modelling**, devised to capture patterns in the data. 
- **prediction**, to apply the model to forecast what will happen in the future. 

All models are incorrect, but they may be useful. We must tolerate randomness and mistakes because many things are [[01_agent_design#Environment Types|stochastic]] by nature. 

Often, we can run into the issue where our training data is only memorized by our model. This is called **overfitting** and is noticeable when we observe good performance on training data but not new, unseen data. We want to achieve **generalization**, where the model generalizes patterns for future data. 
## Test Data
**Training data** is used to train the model. We often use batches to help mitigate errors or issues in segments of the data. However, batches may cause outliers be ignored because they effectively average all the batches. 
**Test data** is a smaller subset of the dataset, split off early on such that none of it is present in the training data. We want this so we can see if the model can accurately predict outcomes with new, unseen information. 

# Data
Our dataset is a collection of data instances or examples. Its definition depends on the problem. It is made up of **feature variables**, which store numerical or categorical values. Categorical values have no inherent ordering, like the color of a car. 

## One-Hot Vector
A **one-hot vector** is a vector that stores every feature variable. 0 and 1 represent false and true. 

## Feature Extraction
We can extract features from our data if our data contains a certain pattern or feature. **Feature extraction** starts from our initial measured data and builds derived values that are intended to be *informative*, *non-redundant*, *facilitating future learning and generalizing steps*, and *leading towards better human interpretations*. Feature extraction is used in [[18_modern_neural_networks#Text and Language|NLP]] and [[18_modern_neural_networks#Computer Vision|computer vision]]. 
