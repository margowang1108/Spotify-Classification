# Spotify_Classification

Final Project for Machine Learning Course using Neural Network

* Summary
In this project, I built a neural network classifier to classify music genre in spottily. The model achieve an AUC score of 0.93. In this report, I will provide details explanation for my data processing, dimension reduction, model selection/building and model evaluation process.

* Data Processing 

2.1 Cleaning
The original data set has 50,005 entries. I firstly drop the rows that contain nan and end up with 50,000 row. The tempo contain special character ’?’ and has a data type of string. I deleted rows that has tempo value ’?’ and convert the column into float. The duration ms column has value -1, which is not realistic. I delete the rows that has -1 as value for duration ms. After performing steps above to clean the data, I am left with 40560, and I believe these are enough data to train my neural network. Not all the columns are useful for prediction. Therefore, my predictor include following columns: popularity, acousticness, danceability, duration ms, energy, instrumentalness, liveness,
loudness, speechiness, tempo, valence, key, mode. My outcome is music genre.

2.2 Dummy Encoding
Two columns that I include as my predictor are categorical and are formatted as string, namely key and mode. I encode them into dummy variables. The key variable is expended tokey A,key A,key B,key C,key C,key D,key D,key E,key F,key F,key G,key G#. The mode variable is expended to mode Major and mode Minor. I also dummy encoded the outcome variables to 10 dummy variables to indicate genre. After performing these encoding, I end up with predictor with 25 columns and outcome with 10 columns.

2.3 Train Test Split
To ensure the balance of both of my training and testing data. For each genre, I randomly select 90% of songs as my training data and the rest 10% of my testing data. Therefore, every genre will have roughly the same number of songs in both training and testing set. This method is to be distinguish from calling train-test-split function. Train-test-split polls from all the data set, where I split the data set for each genre with a ratio of 9:1 to ensure the balance of training and testing set. Eventually, I end up with 36,504 songs in my training set and 4,056 for testing.

2.4 Normalization
For further analysis and the PCA dimension reduction that comes later, I normalize all my numerical data. I need to set the numerical data to the same scale to perform PCA meaningfully. Therefore, I zscore all my numerical data and leave the dummy variables untouched. I also perform my normlization after the train test split to make sure that these two set are completely independent, otherwise, information from the test set will be carried over to the training set.


