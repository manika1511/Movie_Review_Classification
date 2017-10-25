# Movie Review Classification

This project aims at implementing a k-Nearest Neighbor Classifier to predict the sentiment for 25000 movie reviews. Positive
sentiment is represented by a review rating of +1 and negative sentiment is represented by a review rating of -1. 
The dataset consists of a train.dat file to be used for training the classifier and test.dat file for testing the classifier. 
The train.dat file consists of the reviews with the labels. The test.dat file consists of only reviews, labels are missing.

## Approach: 
Step 1: Read the train and the test data set 

Step 2: Split the train dataset into reviews and labels and the test dataset into reviews 

Step 3: Data pre-processing:  
a)	Remove the html tags, digits, punctuation (except apostrophe) and URLs from the reviews  
b)	Perform lemmatization and stemming on the reviews to reduce inflectional forms and sometimes derivationally related forms 
    of a word to a common base form  
c)	Lower-casing the reviews and then split them into words  
d)	Filtering out the words of length < 4 so that the trivial/ common words like ‘are’, ‘the’, etc. are removed.  
e)	Combine the split words into a string  
f)	Perform the same data pre-processing steps 3a) to 3f) on the test dataset reviews also.  

Step 4: Form CSR matrix using Tfidf vectorizer using L2 normalization for both train and test dataset. This function also 
scales the vector values based on the importance of the words.   

Step 5: The similarity of each test review with the train review is calculated by doing the dot product of the test_csr matrix 
and transpose of train_csr matrix  

Step 6: Find the top-k similar train reviews for all the test reviews and their indices  

Step 7: To predict the label for a test review, find the weighted average of the labels of the k-nearest neighbors of the test 
review. If the weighted average is greater than 0, then the label will be ‘+1’ else the label will be ‘-1’.    

### The Accuracy achieved by following this methodology is 83.94%.  
