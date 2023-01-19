# Human Functional MRI Exploratory Analysis on Visual Perception Using Classification Models

## Problem

Cognitive neuroscience is one of the most important fields for studying human intelligence and fMRI serves as a very useful tool for measuring neural activity, providing us with a wealth of data and allowing for inferences to what goes on both in the brain and outside of the brain such as external stimuli.
In this project, we aim to examine the BOLD5000 dataset, from one of the largest human fMRI study on visual perception, by perform a variety of exploratory analysis to assess whether we can make predictions about the stimuli based on brain activity changes.

## Data

### Data Selection
* The data source is from the fMRI project BOLD5000, a large scale human functional MRI study that includes over 5000 images paired with fMRI imaging data from subjects shown these photos.
### Project Description and Motivation
* The main focus of my final project will be to utilize the fMRI voxel ROI data from the over 5000 records and perform exploratory analysis by training a few different classifiers for assessing the predictability of sentiment on the visual input vs. brain activity changes (represented by beta values of fMRI voxel data).

## Cleaning the Data

To get the labels for our data, we perform the following data cleaning to extract two sets of labels: 
1. Sentiment labels: this is from behavioral data collected as the subjects rank whether they like or dislike the images shown to them
2. Scene labels: this represents whether the image stimulus is of a scene or an object

## Learning Model

Here we explore the correlation between our fMRI data and their labels using different machine learning classification techniques: random forest classifier, support vector machine, and multi-layer perceptron.

## Tuning and Feature Extraction

For tuning and feature extraction, we implement two different methods for the different classifiers.
* Recursive feature elimination with cross validation: RFECV recursively eliminates features from the dataset and performs k-fold cross validation to find the optimal number of features and calculates the best accuracy score achieved this way. Here we perform RFECV on our random forest classifier for each brain region.
* Grid search: To find out the best set of hyper-parameters for our MLP classifier, we perform an exhaustive search trying out different combinations of the parameters.

## Refection

1. What issues did you encounter when acquiring and cleaning the data?
   
   *The BOLD5000 is a very large dataset containing a variety of different data types and formats, including large fMRI raw files as well as some highly technical data that took time to navigate around. To better understand the dataset, the author needed to thoroughly read the published paper and clarifications on the project page to figure out the correct data to extract. Some challenges include: downloading and filtering through large amount of data; writing data processing code to label the dataset correctly.*

2. What features did you use in your final model and why were others excluded?
   
   *Two different types of feature selection techniques were used: RFECV (Recursive feature elimination with cross validation) and t-SNE. RFECV was able to reduce the number of features for some brain regions by doing k-fold cross validation; t-SNE in our case was not super effective for visualizing our high-dimensional data as shown in the visualization portion.*
   
3. Which ML methods did you use and why? Which performed best before you started tuning? Did things change after tuning?
   
   *As this is an exploratory project on the relationship between fMRI readings in visual processing regions of the brain and subject input stimuli, I used three different classification methods: random forest classifier, support vector machine, and multi-layer perceptron classifier. Recursive feature elimination with cross validation was used for the RFC classifier and the accuracy results were just slightly better and unfortunately not a lot of features could be eliminated. For the MLP classifier, a grid search is performed to find the best set of hyper-parameters for the neural net and it resulted in a 0.06 increase in accuracy.*

4. What was your accuracy before and then after cross validation?
   
      *Before cross validation, the accuracy was 0.6-0.8 for different brain regions. The best accuracy achieved after RFECV is about 80% across brain regions.*

5. What was the most challenging part of this project?
   
   *fMRI is a challenging topic and data type to perform machine learning on because of the high level of technicality as well as high dimensional data. There were many possible options to explore for classification and feature extraction, so with limited time it is difficult to find the best one.
   Also, with limited experience in data visualization in Python, it takes a fair amount of research to learn different ways to chart plots and set parameters using plotting packages.*

## References

1. https://towardsdatascience.com/pca-using-python-scikit-learn-e653f8989e60
2. https://www.kaggle.com/code/minc33/visualizing-high-dimensional-clusters/notebook
3. https://github.com/christianversloot/machine-learning-articles/blob/main/how-to-normalize-or-standardize-a-dataset-in-python.md
4. https://towardsdatascience.com/feature-extraction-techniques-d619b56e31be
5. https://medium.com/data-folks-indonesia/the-underlying-idea-of-t-sne-6ce4cff4f7
6. https://github.com/christianversloot/machine-learning-articles/blob/main/how-to-normalize-or-standardize-a-dataset-in-python.md
7. https://machinelearningmastery.com/feature-selection-with-real-and-categorical-data/
8. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5635046/
9. https://machinelearningmastery.com/rfe-feature-selection-in-python/
10. https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html#sklearn.svm.SVC
11. https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFECV.html#sklearn.feature_selection.RFECV
12. https://scikit-learn.org/stable/modules/svm.html
13. https://plotly.com/python/3d-scatter-plots/
14. https://matplotlib.org/stable/tutorials/introductory/quick_start.html#sphx-glr-tutorials-introductory-quick-start-py
15. https://michael-fuchs-python.netlify.app/2021/02/03/nn-multi-layer-perceptron-classifier-mlpclassifier/#mlpclassifier
