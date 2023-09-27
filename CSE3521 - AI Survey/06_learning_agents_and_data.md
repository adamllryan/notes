# Intro
Uncertainty and oversimplification caused issues with classic AI models!
We are good at making decisions but not good at explaining our decisions. It's harder for us to define rules of how we make our decisions than to make decisions. 

Solution: Let's make the machine learn itself and let it create rules itself. 
This is *machine learning*!

# Learning Agents
## Key parts
*Data*: collected from past observations (training data)
*Modeling*: devised to capture the patterns in data. ***All models are wrong***! They may just be useful. 
*Prediction*: apply the model to forecast what is going to happen in the future. 
## Learning Algorithms
We pass in training data into the learning algorithm and then we are returned with a learned model and patterns. 

## Training data vs. Test data
>[!NOTE] 70/30 SPLIT!!!
> We often split the dataset into 70 % training and 30% testing data. We can also split further into validation training set data. 

*Training data*: we will use the training data to train the model. We often use batches to help mitigate errors or issues in segments of the data. However, batches may cause outliers be ignored because they effectively average all the batches. 
*Test data*: We use a smaller subset of the training data (split off before we test it so that no test data present in training data or vice versa). 

# Data
Our dataset is a collection of data instances or examples. Its definition depends on the problem. 
[[Data Representation]]
[[Feature Variables]]
## Popular data instances
Computer vision: image & video
Natural language processing: sentence & document
Speech: utterance
Robotics: LiDAR point cloud
Health care: electronic health records

## Feature extraction
We can extract features from our data if our data contains a certain pattern or feature. 
[[Feature Extraction]]
[[Bag-of-words Representation]]
[[Dataset Representation]]
[[Dimensionality reduction]]

