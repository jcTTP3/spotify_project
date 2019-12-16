# Classifying Songs by Artist Using Machine Learning

## Goal

The aim of this project is to correctly classify artists using individual track information gathered from Spotify.

## The Data
Spotify provides artist, album, and track information that is available to the public through their API. For this project, I collected tracks from the studio albums of Bruce Springsteen, Fleetwood Mac, Red Hot Chilli Peppers, The Rolling Stones, Kanye West, Jay-Z, and Kendrick Lamar. Spotify also provides 13 audio features for each track that I ultimately used to classify each song by artist. Additionally, Spotify provides audio analysis on the individual sections of songs which I used to engineer features to enhance the classification model.
* 7 Artists
* 164 Albums
* 2,832 individual trakcs
* 31,185 sections of tracks

I dropped the live albums belonging to these 7 artists due to the difference in sound profile between live and recorded music. Also, some of these artists (mostly The Rolling Stones, Fleetwood Mac, and Bruce Springsteen) have re-released versions of the same song. These duplicates were also dropped from the data set for modeling. Additionally, Jay-Z has one A-Cappella album which was also dropped for modeling purposes.

## Features

For the puropose of this project, I used the 13 audio features that Spotify provides for every track through their API including acousticness, danceability, energy, instrumentalness, liveness, loudness, speechiness, valence, key, mode, duration, time signature, 
and tempo. At first glance, it appeared that enrgy, speechiness, and loudness were the most distinguishing features for each particular artist.

INSERT PICTURES

Additionally, I hypothesized that intra-song variability could help differentiate the artists in my data set.  I built 6 different features to capture variability, including the number of sections in a given song, the average duration of each section, the standard deviation of the length of sections, the standard deviation of the loudness throughout a track, the standard deviation of the tempo throughout a track, an the total number of keys used throughout a track. Initially, the variability (std) of the loudness of a song stood out as a feature that may help to distinguish between the artists.

INSERT PICTURE

## The Model

### Evaluation Metric
Given the class inbalance of my dataset, along with the number of classes I chose, the metric I focused on for model performance was the f1 score, a combination of both precision and recall. 

### Baseline Model
Using a dummy classifier with the stratified method of classification, that relies on the distribution of classes to make predictions, yielded a very overall accuracy rate and corresponding f1 scores for each class

INSERT CONFUSION MATRIX FOR DUMMY AND CLASSIFICATION REPORT

### Final Model
Ultimately, the best model that yielded the best results was a Random Forest using parameters optimized with GridSearch. Model Parameters:
* criterion: 'gini'
* max_depth: 7
* max_features: 'sqrt'
* min_samples_leaf: 5
* min_samples_split: 5
* n_estimators: 150
This model achieved an overall accuracy score of 69% and the following f1 scores for each individual class:

INSERT CONFUSION MATRIX AND CLASSIFICATION REPORT

Overall, the model predicted most artists in the dataset with similar ability, besides two of the rappers in the dataset, Kanye West and Kendrick Lamar. As shown below, speechiness and loudness were the two most important features to distinguish between artists. 

INSERT FEATURE IMPORTANCE GRAPHIC

Given that these were the two most important features and the underrepresentation of Kanye West and Kendrick Lamar in the dataset, it somewhat makes sense that the model mostly predicted these two's songs as Jay-Z. It is also somewhat encouraging that the model suggests that these artists' songs belong to another rapper, rather than a rock and roll artists used in the data set. 

INSERT RAP FEATURES

## Other Methods Attempted
Before settling on the optimized random forest, I attempted the following methods to achieve better classification results. Each had its own specific drawbacks.

* AdaBoost- _poor model results_
* GradientBoost- _overfitting_
* SMOTE (to resample the underrepresented data)- _no improvement in classifiying underrepresented artists_

## Conclusion and Ideas for Further Exploration
Through these techniques, it is possible to classify artists by individual track audio qualities (according to Spotify), to an extent. In some cases, the model misclassifies songs, especially artists who do not have an extensive library of recorded music to train a model on. This model is also highly specific towards the particular artists chosen in this dataset. 

In the future, I would like to explore enhancing this model by classifying artists using audio files themselves, rather than pre-defined features from Spotify. Additionally, it would be interesitng to incorporate the lyrical style of artists into the model using Natural Language Processing.

