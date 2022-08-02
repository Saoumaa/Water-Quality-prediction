# Water-Quality-prediction

This is a classification problem. Here we are to predict the classification of a water sample ,if it's safe for usage or not.

## Importing Libraries.
All necessary libraries needed to perform a classification analysis were imported, some of them include:
1. pandas 
2. numpy
3. matplotlib.pyplot
4. seaborn
5. sklearn
6. catboost 
The mentioned libraries plays important role in this task.

## Loading the dataset
The dataset was gotten from kaggle. It has 7999 rows and 21 columns.
All the features of the dataset are numerical ,only the target feature is categorical.
To make the dataset ready for other processes, some cleaning were performed.
The data is found to have no null values in it.

## Exploratory Data Analysis
A general histogram plot of the data is shown below.
![download](https://user-images.githubusercontent.com/104036386/182481467-22f28e2c-5181-44d2-9a4e-b5f29b4047aa.png)

Countplot was performed to visualize the target variable, the result is shown below.
![download](https://user-images.githubusercontent.com/104036386/182481575-82b9ade0-2ddc-4aa8-8cc5-63df5f511e5e.png)

With this result, it is very much obvious that the data is imbalanced. The fact that the data is imbalance will make the model we will be using to classify the data biased, it will classify more water samples as unsafe. Hence the needful thing to be done is to balance the data. The data ws balanced using SMOTE. 
The result from balancing the data, is shown below.

![download](https://user-images.githubusercontent.com/104036386/182481896-322a7f4e-b003-425f-88b9-255e139f4fdb.png)
The resulting dataset have 14168 rows and 21 columns
Now that the data is balanced, it will be nice to see of there any change in the dataset generally. Another histogam will be plotted to see this.

![download](https://user-images.githubusercontent.com/104036386/182482076-67618702-5028-4c25-9c25-b874f89993b0.png)
Yes, there's significant difference between the two general plots.

## Preprocessing
Preprocessing involves the removal of outliers and making the data distributed.
BUt in this case, much won't be done.
Below are some boxplots of some features of the data.

#### Aluminium
![download](https://user-images.githubusercontent.com/104036386/182482440-4be118fa-9485-4fa8-a8ce-0f52e12b5506.png)

#### Ammonia
![download](https://user-images.githubusercontent.com/104036386/182482470-2014524d-36e1-4ab2-bbf5-5ce2773afa07.png)

#### Arsenic
![download](https://user-images.githubusercontent.com/104036386/182482562-1642be7e-e2de-4f87-bd4e-cf5a1c3f9738.png)

#### Bacteria
![download](https://user-images.githubusercontent.com/104036386/182482595-027f4239-251c-4c97-9e77-5afd9385e103.png)

#### Viruses
![download](https://user-images.githubusercontent.com/104036386/182482677-c5348918-7f0e-420f-88df-22196e5a01e1.png)

Looking at the results of the plots, majority of the data were skewed and only Arsenic appears to have an outlier in the data.
Considering the fact that only Arsenic appears to have outliers, it is considered to leave it that way, and that the removal of outliers from it might bring changes to other features that are still good.

### Correlation 

Correlation between the target feature and other variables were made, the plot of the result is shown below.

![download](https://user-images.githubusercontent.com/104036386/182483225-457407b4-558d-4889-9bf9-394620db7398.png)

### Standardizing 

Since all the features of the data are numerical, then the other preprocessing that might be needed is to scale the data. Sklearn standardscaler is used to scale the data.

In preparation for a classification model, the dataset was splitted into train ,validation and test set.

## Modeling

#### Logistic Regression
This is the first classification model used to train the data, the result is shown below.
The model was used to predict the validation data.

![image](https://user-images.githubusercontent.com/104036386/182484178-b003e363-5854-43da-be6b-c11ee03f5ace.png)

The confusion matrix is shown below
![download](https://user-images.githubusercontent.com/104036386/182484228-82f97885-eec0-4867-b242-be7a1f90a15f.png)

Upon using the model to predict the test set, the result is shown below.

![image](https://user-images.githubusercontent.com/104036386/182484462-bcab1ffe-8a68-459c-9fc0-f4b34107981b.png)

The confusion matrix is also shown below
![download](https://user-images.githubusercontent.com/104036386/182484570-4fc50ae0-d38a-40f5-93b5-a9791e034982.png)

Other classification models were used also, and they perform excellently, the least gotten was na accuracy of 95%.

#### CatBoost Classifier

This is the best model of all the models used, it achieved an accuracy of 98%
The result is shown below (Validation data)

![image](https://user-images.githubusercontent.com/104036386/182484870-f316f932-34dd-4cd6-81a6-5118ac5fa4a1.png)

The confusion matrix is shown below.

![image](https://user-images.githubusercontent.com/104036386/182484976-cd02a2d0-0e08-4443-9de3-96a04553b55d.png)

This is a very good result, imagine the outliers were removed, it's possible to achieve a perfect classification model.

The result from predicting the test set is shown below.

![image](https://user-images.githubusercontent.com/104036386/182485147-0fa7e82b-fad0-42d4-a775-a07de5296159.png)

Confusion Matrix

![image](https://user-images.githubusercontent.com/104036386/182485179-977cb6db-7e04-4e93-91cd-b55f14f0ce4f.png)

### Conlcusion.

The performance of the madel can be enhanced by removing the ourliers in the dataset.
CatBoost Classifier is a good model.
