# Multiclass-and-Multilabel-Classification

The task is to perform multi-class and multi-label classfication using Support Vector Machines (SVMs) 
and K-Means Clustering algorithms.

## Dataset
The Anuran Calls (MFCCs) dataset contains the acoustic features extracted from syllables of anuran (frogs) calls, 
including the family, the genus, and the species labels. This dataset was created segmenting 60 audio records belonging 
to 4 different family, 8 genus, and 10 species. Each audio corresponds to one specimen (an individual frog).
There are total 7195 instances described using 22 real-valued features. 

## Support Vector Machines
One-vs-all Support Vector Machines (SVMs) fit K SVMs, each time comparing one of the K classes to the remaining K-1 classes.
The new data point would be classified under a certain class if and only if that class's SVM accepted it and all other 
classes' SVMs rejected it. So, one-vs-all SVM has been trained for each of the labels, using Gaussian kernels.
The weight of the SVM penalty and the width of the gaussian kernel has been found out using 10-fold cross-validation.

The gaussian kernel SVM has been compared with linear L1-penalized SVM for this dataset by computing exact match loss and
hamming loss. The weight of SVM penalty is again found out using 10-fold cross-validation. Since there is a problem of class 
imbalance in the dataset, SMOTE has been applied to over-sample the minority class and test the classifiers.

## K-Means Clustering
The data points have been clustered using K-means clustering by monte-carlo simulation and silhouette analysis has been used 
to choose the optimal number of clusters K. The label for each cluster is then determined by majority polling. The average
hamming loss and exact match loss has been computed for the monte-carlo simulation.

## Exact Match Score and Hamming Loss
In multilabel classification, exact match score defines the subset accuracy, i.e. the number of observations for which the 
actual set of labels correspond to the predicted set of labels for that obervation. In other words, if the entire set of 
predicted labels for a sample strictly match the actual set of labels, then the subset accuracy will be 1, otherwise it 
is 0. <br/>
Hamming Loss computes the average hamming distance between two set of samples. It is the fraction of observations for which 
labels are not predicted properly. In other words, if an observation has 3 labels, and 2 out of these 3 labels are not 
predicted correctly, then the hamming distance is 2. <br/>
 
