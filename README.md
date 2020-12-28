# Optimizing an ML Pipeline in Azure

## Overview: 
The main objective of this project was tp learn the power of Azure ML studio. And how to use some common methods to create and optimize an ML pipeline using Python SDK and a provided Scikit learn model. And then to compare with Azure AutoML run and both their results.

## Summary: 
We were given two notebooks namely project.ipynb and a train.py. It already had all the instructoins on how to procedd with the task upto its successful completion. For any trivial queries or better understanding the syntax, there was plenty of context on Official Microsoft Documentation for Azure. The dataset was about a bank marketing and we had to predict if a customer will subscribe to bank term deposit. The best performing model was a Soft Voting Ensemble found using AutoML. It contained XGBoost Classifier with a standard scaler wrapper.

![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/1.PNG)


## Scikit-Learn Pipeline: 
The pipeline consists of a compute instance cluster and inference cluster where the models are stored.

**Explain the pipeline architecture, including data, hyperparameter tuning, and classification algorithm.**

The dataset is first retrieved using AzureDataFactory class. 
Some preprocessing steps were performed like converting categorical variable to binary encoding, one hot encoding
Then dataset is split in ratio of 67/33 (train/test)
Then the model is trained using the hyperparameters passed from command line
The hyperparameters that can be tuned are C an max_iter. C is the inverse regularization parameter and max_iter is the maximum number of iterations.
Then accuracy was calculated on the test set which is also the defining metric.

### What are the benefits of the parameter sampler you chose?

The inverse parameter value C is one of the important parameters from business context and it controls the overfitting of the model. Normally a good thing is to see the change in accuracy by increasing or decreasing C by 10x
The number of iterations is also an important factor because if the problem is too complex then they do help in training for longer durations.

### What are the benefits of the early stopping policy you chose?

It saves a lot of computational resources
It saves a lot of time for the Data Scientist as we have clearly defined the patience level and the deviation that we can expect at maximum.

## AutoML
**In 1-2 sentences, describe the model and hyperparameters generated by AutoML. AutoML was quite a surprise. I never knew it could run on so many models and so fast. The models were XGBoost, LightGBM, RandomForests, BoostedTrees, SGDClassifier with varying input preprocessing normalizations like: Min Max Scaling, Standard Scaling etc.**
![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/2.PNG)
### Pipeline comparison
Compare the two models and their performance. What are the differences in accuracy? In architecture? If there was a difference, why do you think there was one? The difference in accuracy is not too much. AutoML accuracy -> 0.91720 Hyperdrive accuracy -> 0.91105.
![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/3-hyper.PNG)
![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/3-auto.PNG)
Both architectures can be seen and compared in the images below.
![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/4.PNG)
The difference is definitely a result of the difference in the batch size of the runs and the maximum number of iterations performed. A bigger difference can also be linked to the use of different algorithms in both cases.
![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/4.1.PNG)
## Future Work
**What are some areas of improvement for future experiments? Why might these improvements help the model? I would love to give my custom cross validation strategy for the future experiments.** 
For future experiments, the project can be expanded to include other metrics for logistic regression studies such as maximum number of batch sizes, loss functions, L2 regularization and median absolute errors. Classification reports from the XGBoosting function can be expanded to include a matrix for false positives, false negatives, true positives and true negatives. The threshold for parameters can also be expanded to include a wider range. All these steps will help in providing a clearer interpretation of the models and their approach to predicting the output.

### If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section. 
![alt text](https://github.com/hammad-alt/udacityproject1/blob/main/images/5.png)


