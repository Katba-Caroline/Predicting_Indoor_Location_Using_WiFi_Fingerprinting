# Predicting_Indoor_Location_Using_WiFi_Fingerprinting
### Table of Contents

1. [Libraries](#Libraries)
2. [Project Description](#ProjectDescription)
3. [Data](#Data)
4. [Approaches in the Literature](#ApproachesinLit)
5. [Literature on Indoor Localization](#LitonIndoorLoc)
6. [My Approach: Multi-label Classification](#MultiLabelClassification)
7. [Literature on Multi-Label Classification](#LitonMultiLabelClassification)
8. [Notebook Table of Contents](#NotebookTableofContents)
9. [Results](#Results)
10. [Future Improvements](#FutureImprovements)

  
## Libraries <a name="Libraries"></a>
* Numpy
* Pandas
* Seaborn
* Matplotlib
* Scipy
* Sklearn
* Skmultilearn

## Project Description <a name="ProjectDescription"></a>
In this project, I predict Indoor Location of users using Wifi fingerprints with a combination of Principal Component Analysis (PSA) and Multi-label Classification using skmultilearn
Many businesses and service providers rely on localization services in order to better serve their patrons. Thanks to the inclusion of GPS sensors in mobile devices, Outdoor localization problems have been solved in a variety of ways and very accurately. However, indoor localization is still an open problem mainly due to the loss of GPS signal in indoor environments.
Therefore, the problem of indoor localization has recently garnered increased attention from researchers who have opted to focus more on cheaper software solutions in place of expensive hardware solutions. 

Indoor localization has many use cases and exhibits great potential for solving problems in:
- Indoor navigation for humans and robots
- Targeted advertising 
- Emergency response
- Assisted living 

## Data <a name="Data"></a>

This data set is still unfortunately one of a kind and was recently presented by Joaquín Torres-Sospedra, Raúl Montoliu, Adolfo Martínez-Usó, Tomar J. Arnau, Joan P. Avariento, Mauri Benedito-Bordonau, Joaquín Huerta [UJIIndoorLoc: A New Multi-building and Multi-floor Database for WLAN Fingerprint-based Indoor Localization Problems In Proceedings of the Fifth International Conference on Indoor Positioning and Indoor Navigation, 2014.](https://www.ncbi.nlm.nih.gov/pubmed/28287447)

The UJIIndoorLoc database covers three buildings of Universitat Jaume I with 4 or more floors and almost 110.000 m2. It was created in 2013 by means of more than 20 different users and 25 Android devices. The database consists of 19,937 training/reference records (trainingData.csv file) and 1111 validation/test records (validationData.csv file).

The 529 attributes contain the WiFi fingerprint, the coordinates where it was taken, and other useful information. Each WiFi fingerprint can be characterized by the detected Wireless Access Points (WAPs) and the corresponding Received Signal Strength Intensity (RSSI). The intensity values are represented as negative integer values ranging -104dBm (extremely poor signal) to 0dbM. The positive value 100 is used to denote when a WAP was not detected. During the database creation, 520 different WAPs were detected. Thus, the WiFi fingerprint is composed by 520 intensity values.

*A visual mapping of the Longitude and Latitude data to get an image of campus*
![alt text](https://github.com/Katba-Caroline/Predicting_Indoor_Location_Using_WiFi_Fingerprinting/blob/master/Images/data_map.png) 

*A visual mapping of the users who collected the data in each building*
![alt text](https://github.com/Katba-Caroline/Predicting_Indoor_Location_Using_WiFi_Fingerprinting/blob/master/Images/map2_users.png)

*Scatter Matrix of the Attributes*
![alt text](https://github.com/Katba-Caroline/Predicting_Indoor_Location_Using_WiFi_Fingerprinting/blob/master/Images/matrix.png)

*Histogram of the Attributes*
![alt text](https://github.com/Katba-Caroline/Predicting_Indoor_Location_Using_WiFi_Fingerprinting/blob/master/Images/attribute_histogram_plots.png)


## Approaches in the Literature <a name="ApproachesinLit"></a>
  
Although available Data for indoor localization has unfortunately been scant, many have used this data to solve several problems in a variety of ways. Those approaches include the following: 

- Location identification using regression techniques
- Floor positioning using classification
- Building recognition using deep learning models
- Trajectory tracking using a combination of the above methods
- read more [here](https://www.ncbi.nlm.nih.gov/pubmed/28287447)

## Literature on Indoor Localization <a name="LitonIndoorLoc"></a>

Here are several of the papers available on the topic that helped me in my research:
- [WaP: Indoor localization and tracking using WiFi-Assisted Particle filter](https://www.researchgate.net/publication/286669860_WaP_Indoor_localization_and_tracking_using_WiFi-Assisted_Particle_filter)
- [Machine Learning for Indoor Localization
Using Mobile Phone-Based Sensors](https://arxiv.org/pdf/1505.06125.pdf)
- [Low-effort place recognition with WiFi
fingerprints using deep learning](https://arxiv.org/pdf/1611.02049v1.pdf)
- [Indoor Location Prediction Using Multiple Wireless Received
Signal Strengths](https://pdfs.semanticscholar.org/837a/2fd3f8012519707e23b2aee0850d457c950e.pdf)
- [Reliable indoor location prediction using conformal
prediction](http://khuong.uk/Papers/reliable_indoor_journal.pdf)
- [Indoor Localization using Place and Motion Signatures](https://pdfs.semanticscholar.org/2a24/2b0e4d4468946a51282fc6c1b728c8308f34.pdf)

## My Approach: Multi-label Classification <a name="MultiLabelClassification"></a>

To my knowledge, my approach is a unique approach that has not been applied to the problem before. I treat the problem as a classification problem, but with a twist that can save time, effort and precious memory. I treat this problem as a Multi-Label Classification problem, wherein my model simultaneously predicts *Building ID and Floor ID* for a given input. 
Using a combination of Principal Component Analysis (PCA) and Multi-Label K Nearest Neighbor (MLKNN) algorithms, the model is able to predict the Building ID AND Floor ID simultaneously with 98.7% accuracy score and 0.003 Hamming loss. 
This model can also be expanded to include Space ID as well.
 

The "Difference between multi-class classification & multi-label classification is that in multi-class problems the classes are mutually exclusive, whereas for multi-label problems each label represents a different classification task, but the tasks are somehow related." read more [here.](https://towardsdatascience.com/journey-to-the-center-of-multi-label-classification-384c40229bff)

Although many of the previosuly mentioned approaches yielded excellent results, many of them relied on predicting only one independent variable at a time regardless of the technique. For example, predicting only the building ID or the floor ID independently. In my opinion creating separate models for such a prediction task can be quite costly in terms of compute power, memory and time savings. Especially when using Neural Networks which can require great computational powers. Such losses, especially in time can be even deadly. Imagine a fire on the 4th floor of a particular building in a university. Having a model that can accurately and quickly predict how many people are in that exact area can be tremendously helpful to emergency response personnel.

## Literature on Multi-Label Classification <a name="LitonMultiLabelClassification"></a>

- [How Is a Data-Driven Approach Better than Random Choice in Label Space Division for Multi-Label Classification?](https://www.mdpi.com/1099-4300/18/8/282/htm)
- [Multi-Label Classification Problem Analysis, Metrics and Techniques](https://www.springer.com/us/book/9783319411101)
- [ML-KNN: A lazy learning approach to multi-label learning](https://www.sciencedirect.com/science/article/abs/pii/S0031320307000027)
- [Multi-label Classification: Problem Transformation methods in
Tamil Phoneme classification](https://www.sciencedirect.com/science/article/pii/S1877050917319440)
- [Multi-label Classification: A Comparative Study on
Threshold Selection Methods](http://dmip.webs.upv.es/LMCE2014/Papers/lmce2014_submission_11.pdf)
- [A Tutorial on Multi-label Classification Techniques](https://www.researchgate.net/publication/225379571_A_Tutorial_on_Multi-label_Classification_Techniques)
- [Multi-Label Classification of Music Into Emotions](http://lpis.csd.auth.gr/publications/tsoumakas-ismir08.pdf)

## Notebook Table of Contents <a name="NotebookTableofContents"></a>
- Exploratory Data Analysis (EDA)
- Preprocessing
- Model Applications
- Model Predictions
- Model Predictions for Validation Data 
    - I tested the model on the validation data set, a completely new and unseen data set to test the model.
    
## Results <a name="Results"></a>
- Using a combination of Principal Component Analysis (PCA) and Multi-Label K Nearest Neighbor (MLKNN) algorithms, the model is able to predict the Building ID AND Floor ID simultaneously on the Validation data with 81% accuracy score.
- All of the predictions have been translated  and saved to an external CSV to reflect the proper Building ID and Floor ID.

## Future Improvements <a name="FutureImprovements"></a>
- This is a very unique data set and has become a harbinger of what's to come. Yet, sadly, it is one of a kind, thereby severly limiting our ability to innovate any further.
- Additionally, the majority of Space IDs(classroom information) in the Validation dataset were nulls, this severly hindered the ability to include Space ID in the model as well.
- I hope that there will be clearer documentation and more lucid examples of skmultilearn (a very powerful toolkit) in the near future. 
