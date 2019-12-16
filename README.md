# Classifying Songs by Artist Using Machine Learning Classification Techniques 

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



