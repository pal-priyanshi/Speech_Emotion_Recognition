
This Repo contains part of the work for the project for ELEC-E5510, Aalto University.

The Crowd-sourced Emotional Multimodal Actors Dataset (CREMA-D} is considered for this speech emotion recognition task, due to its diversity of subjects, ranging from race to age. It consists of 7,442 original clips from 91 actors. These clips were from 48 male and 43 female actors between the ages of 20 and 74 coming from a variety of races and ethnicities (African America, Asian, Caucasian, Hispanic, and Unspecified).

Actors spoke from a selection of 12 sentences. The sentences were presented using one of six different emotions (Anger, Disgust, Fear, Happy, Neutral, and Sad) and four different emotion levels (Low, Medium, High, and Unspecified).

The sentences were as follows:
It's eleven o'clock (IEO),
That is exactly what happened (TIE),
I'm on my way to the meeting (IOM),
I wonder what this is about (IWW),
The airplane is almost full (TAI),
Maybe tomorrow it will be cold (MTI),
I would like a new alarm clock (IWL),
I think I have a doctor's appointment (ITH),
Don't forget a jacket (DFA),
I think I've seen this before (ITS),
The surface is slick (TSI),
We'll stop in a couple of minutes (WSI).

![alt text](https://github.com/pal-priyanshi/Speech_Emotion_Recognition/blob/main/crema_d_data_desc.jpg)

**How distinct are the emotion clusters based on audio features and to what degree?**

Two parts are involved to our approach for this problem. To extract audio features, 13-dimensional MFCCs are obtained for each file, correspondiong to 7,332 audio files. Then, the MFCC features are standardized by removing the mean and scaling to unit variance.  

As we know, the dataset is contains audio clips specific to 6 emotions and to observe how distict or closely related they are, K-means clustering algorithm is deployed for 6 clusters on the standardised MFCC features, followed by Principal Component Analysis with two components for visualisation. 
The results for each cluster is as follows:\\


![alt text](https://github.com/pal-priyanshi/Speech_Emotion_Recognition/blob/main/k_means_clustering.jpg)

*Interpretation*: It can be observed that the emotions aren't well separable based on audio features solely, such as MFCCs. Although some emotions are a bit more distinct [(Cluster-3, anger), (Cluster-4, Sadness)], rest seem to be somewhat related. The Cluster-2 was supposed to be Neutral but it can be similar to any other Emotion in terms of MFCCs. The indicates the recognising emotions solely based on speech based features may be quite complex for the given dataset and it is further confirmed that the clusters aren't that easil well formed (given the Silhouette score was found to be lower than 0.2, indicating low cluster quality)

**How well can Speech Emotion Recognition (SER) be performed using Random Forest and SVM classification approach?**

The following classical methods for classification are considered: Random Forest and Support Vector Machines (SVM). Also, Random Forest and SVMs are conventionally used for various classification tasks in general.
The data is split into training (5,209) and test set (2,233).

![alt text](https://github.com/pal-priyanshi/Speech_Emotion_Recognition/blob/main/classification_using_RF_SVM.jpg)

*Interpretation*: In both classification models, ``Anger" and "Sad" is more easily recognisable. It can also be observed that ``Sad" can be similar to ``Fear", as seen in the confusion matrices. The hardest emotion to recognise was ``Fear". 

Lastly, although the classical models did not have very good accuracy, it still helped us understand more about which emotions can be close to which other ones, the easily and the hard to recognise ones. Therefore, certainly models with better accuracy are required, be it through much thorough fine-tuning , using hybrid models made of the classical models or through pre-trained models.

A small note worth mentioning is that, Although Fear and Disgust seemed harder to recognise, similar to human crowdsourcing, Sad was contrarily recognised better.
