# MLBoxingAnalysis
During this project I will be training a Long Short Term Memory (LSTM) network to detect which punch is being thrown during shadow boxing. This project was inspired by a talk given by [Zack Akil](https://github.com/ZackAkil/) about using Google's VideoIntelligence API to analyse a penalty shootout, as well as [Dale Markowitz](https://daleonai.com/machine-learning-for-sports)'s tennis serve analyser and [Anudeep Ayinaparthi](https://github.com/anudeepayina/CricketTracker)'s cricket shot classifier. 

## Google Cloud Platform
This project makes use of GCP's VideoIntelligence API, which is available through GCP's web console, or programmatically using the corresponding Python libraries. In order to set up your own GCP account to use the notebooks in this project, please see [this](https://github.com/google/making_with_ml/blob/master/sports_ai/Sports_AI_Analysis.ipynb) link. The VideoIntelligence API has a function called *detect_person* which returns the position of all the identified "person" landmarks in the frame, e.g. left shoulder, right shoulder etc.

## Input data
For this project I recorded a number of videos of myself throwing a number of punches while shadow boxing. These videos were split up so that I had short video snippets of individual punches, which were then uploaded to my GCP project bucket to be processed by the VideoIntelligence API. The videos in question were filmed using a fixed camera, where I was always facing the camera when throwing punches. 

## Preprocessing of data
In the notebook, some preprocessing is done to make the input data suitable for training a machine learning model. This preprocessing involves normalising all of the data, such that the position of each landmark in a frame is relative to the the position of the same landmark in the first frame. 

## Training an LSTM
As the input data for this classifier is time dependent (as it tracks the movement of identified landmarks over time), an LSTM model was used to classify each video. LSTMs are a type of recurrent neural network that are suitable for this sort of problem, and perform better tha simple neural networks when given long input sequences. [This](https://towardsdatascience.com/illustrated-guide-to-lstms-and-gru-s-a-step-by-step-explanation-44e9eb85bf21) article is a great resource on how LSTMs overcome some of the shortfalls of simple RNN models.
