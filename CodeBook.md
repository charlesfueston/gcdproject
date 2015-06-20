---
title: "Code Book"
date: "06-19-2015"
---





### Introduction:

Students were provided with the raw data (Please see References.)<sup>2</sup> and asked to clean and summarize it.  The final data set is a subset of the original data containing "only the measurements on the mean and standard deviation for each measurement."  Which has been further summarized by taking only "the average of each variable for each activity and each subject."   


Study Design: 
=============


**Overview:**

Human Activity Recognition Using Smartphones Dataset
Version 1.0

Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Università degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws


The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities
(WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. 
Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. 
The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, 
where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows 
of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was 
separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency 
components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables 
from the time and frequency domain. See 'features_info.txt' for more details. 

**Overview section is quoted from "README.txt".** (Please see References.)<sup>2</sup>


**Feature Selection:** 


The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using
a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the 
acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using 
another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals
(tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ).  Also the magnitude of these three-dimensional signals were calculated using the 
Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ,
fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.


**Features selection section is quoted from "features_info.txt".**  (Please see References.)<sup>2</sup>



Code book:
==========


**Data set:**

The final data set is 68 columns by 180 rows.  Two columns contain attributes and 66 columns contain variables.  Each row contains the mean value, measured in cycles per second, of the mean and standard deviation for each activity performed by each subject. (30 subjects times 6 activities = 180)  



**Attribute labels:**

- Subject: An identifier of the subject who carried out the experiment
- Activity: Activity labels: "WALKING", "WALKING_UPSTAIRS", "WALKING_DOWNSTAIRS", "SITTING", "STANDING", "LAYING"

**Variable labels:**

**The following variable labels were taken from the original data set. (Please see special notes)<sup>1</sup>   It should be noted that for this data set a summary was calculated for the "average of each variable for each activity and each subject". So the following mnemonics now refer to these averages measured in cycle per second.(Please see special notes)<sup>1</sup>**

### Descriptions of variable Mnemonics:    

- tBodyAcc-mean()-X: Time domain signal, Body Acceleration, mean, X-Axis
- tBodyAcc-mean()-Y: Time domain signal, Body Acceleration, mean, Y-Axis
- tBodyAcc-mean()-Z: Time domain signal, Body Acceleration, mean, Z-Axis
- tBodyAcc-std()-X: Time domain signal, Body Acceleration, Standard deviation, X-Axis 
- tBodyAcc-std()-Y: Time domain signal, Body Acceleration, Standard deviation, Y-Axis
- tBodyAcc-std()-Z: Time domain signal, Body Acceleration, Standard deviation, Z-Axis
- tGravityAcc-mean()-X: Time domain signal, Gravity Acceleration, mean, X-Axis 
- tGravityAcc-mean()-Y: Time domain signal, Gravity Acceleration, mean, Y-Axis
- tGravityAcc-mean()-Z: Time domain signal, Gravity Acceleration, mean, Z-Axis
- tGravityAcc-std()-X: Time domain signal, Gravity Acceleration, Standard deviation, X-Axis
- tGravityAcc-std()-Y: Time domain signal, Gravity Acceleration, Standard deviation, Y-Axis
- tGravityAcc-std()-Z: Time domain signal, Gravity Acceleration, Standard deviation, Z-Axis
- tBodyAccJerk-mean()-X: Time domain signal, Body Acceleration Jerk, mean, X-Axis
- tBodyAccJerk-mean()-Y: Time domain signal, Body Acceleration Jerk, mean, Y-Axis
- tBodyAccJerk-mean()-Z: Time domain signal, Body Acceleration Jerk, mean, Z-Axis
- tBodyAccJerk-std()-X: Time domain signal, Body Acceleration Jerk, Standard deviation, X-Axis
- tBodyAccJerk-std()-Y: Time domain signal, Body Acceleration Jerk, Standard deviation, Y-Axis
- tBodyAccJerk-std()-Z: Time domain signal, Body Acceleration Jerk, Standard deviation,
- tBodyGyro-mean()-X: Time domain signal, Body Angular Velocity (Gyroscope), mean, X-Axis, Unit of Measure: Radians
- tBodyGyro-mean()-Y: Time domain signal, Body Angular Velocity (Gyroscope), mean, Y-Axis
- tBodyGyro-mean()-Z: Time domain signal, Body Angular Velocity (Gyroscope), mean, Z-Axis
- tBodyGyro-std()-X: Time domain signal, Body Angular Velocity (Gyroscope), Standard deviation, X-Axis
- tBodyGyro-std()-Y: Time domain signal, Body Angular Velocity (Gyroscope), Standard deviation, Y-Axis
- tBodyGyro-std()-Z: Time domain signal, Body Angular Velocity (Gyroscope), Standard deviation, Z-Axis
- tBodyGyroJerk-mean()-X: Time domain signal, Body Angular Velocity Jerk (Gyroscope), mean, X-Axis
- tBodyGyroJerk-mean()-Y: Time domain signal, Body Angular Velocity Jerk (Gyroscope), mean, Y-Axis 
- tBodyGyroJerk-mean()-Z: Time domain signal, Body Angular Velocity Jerk (Gyroscope), mean, Z-Axis
- tBodyGyroJerk-std()-X: Time domain signal, Body Angular Velocity Jerk (Gyroscope), Standard deviation, X-Axis
- tBodyGyroJerk-std()-Y: Time domain signal, Body Angular Velocity Jerk (Gyroscope), Standard deviation, Y-Axis
- tBodyGyroJerk-std()-Z: Time domain signal, Body Angular Velocity Jerk (Gyroscope), Standard deviation, Z-Axis
- tBodyAccMag-mean(): Time domain signal, Body Acceleration Magnitude, mean
- tBodyAccMag-std(): Time domain signal, Body Acceleration Magntitude, Standard deviation
- tGravityAccMag-mean(): Time domain signal, Gravity Acceleration Magnitude, mean
- tGravityAccMag-std(): Time domain signal, Gravity Acceleration Magnitude, Standard deviation
- tBodyAccJerkMag-mean(): Time domain signal, Body Acceleration Jerk Magntitude, mean
- tBodyAccJerkMag-std(): Time domain signal, Body Acceleration Jerk Magntitude, Standard deviation
- tBodyGyroMag-mean(): Time domain signal, Body Angular Velocity Magnitude (Gyroscope), mean 
- tBodyGyroMag-std(): Time domain signal,  Body Angular Velocity Magnitude (Gyroscope), Standard deviation
- tBodyGyroJerkMag-mean(): Time domain signal, Body Angular Velocity Jerk Magnitude (Gyroscope), mean
- tBodyGyroJerkMag-std(): Time domain signal,  Body Angular Velocity Jerk Magnitude (Gyroscope), Standard deviation
- fBodyAcc-mean()-X: Frequency domain signal, Body Acceleration, mean, X-Axis
- fBodyAcc-mean()-Y: Frequency domain signal, Body Acceleration, mean, Y-Axis
- fBodyAcc-mean()-Z: Frequency domain signal, Body Acceleration, mean, Z-Axis
- fBodyAcc-std()-X: Frequency domain signal, Body Acceleration, Standard deviation, X-Axis
- fBodyAcc-std()-Y: Frequency domain signal, Body Acceleration, Standard deviation, Y-Axis
- fBodyAcc-std()-Z: Frequency domain signal, Body Acceleration, Standard deviation, Z-Axis
- fBodyAccJerk-mean()-X: Frequency domain signal, Body Acceleration Jerk, mean, X-Axis
- fBodyAccJerk-mean()-Y: Frequency domain signal, Body Acceleration Jerk, mean, Y-Axis
- fBodyAccJerk-mean()-Z: Frequency domain signal, Body Acceleration Jerk, mean, Z-Axis
- fBodyAccJerk-std()-X: Frequency domain signal, Body Acceleration Jerk, Standard deviation, X-Axis
- fBodyAccJerk-std()-Y: Frequency domain signal, Body Acceleration Jerk, Standard deviation, Y-Axis
- fBodyAccJerk-std()-Z: Frequency domain signal, Body Acceleration Jerk, Standard deviation, Z-Axis
- fBodyGyro-mean()-X: Frequency domain signal, Body Angular Velocity (Gyroscope), mean, X-Axis
- fBodyGyro-mean()-Y: Frequency domain signal, Body Angular Velocity (Gyroscope), mean, Y-Axis
- fBodyGyro-mean()-Z: Frequency domain signal, Body Angular Velocity (Gyroscope), mean, Z-Axis
- fBodyGyro-std()-X: Frequency domain signal, Body Angular Velocity (Gyroscope), Standard deviation, X-Axis
- fBodyGyro-std()-Y: Frequency domain signal, Body Angular Velocity (Gyroscope), Standard deviation, Y-Axis
- fBodyGyro-std()-Z: Frequency domain signal, Body Angular Velocity (Gyroscope), Standard deviation, Z-Axis
- fBodyAccMag-mean(): Frequency domain signal, Body Acceleration Magnitude, mean
- fBodyAccMag-std(): Frequency domain signal, Body Acceleration Magnitude, Standard deviation
- fBodyBodyAccJerkMag-mean(): Frequency domain signal, Body Acceleration Jerk Magnitude, mean
- fBodyBodyAccJerkMag-std(): Frequency domain signal, Body Acceleration Jerk Magnitude, Standard deviation
- fBodyBodyGyroMag-mean(): Frequency domain signal,  Body Angular Velocity Jerk Magnitude (Gyroscope), mean
- fBodyBodyGyroMag-std(): Frequency domain signal,  Body Angular Velocity Jerk Magnitude (Gyroscope), Standard deviation
- fBodyBodyGyroJerkMag-mean(): Frequency domain signal,  Body Angular Velocity Jerk Magnitude (Gyroscope), mean
- fBodyBodyGyroJerkMag-std(): Frequency domain signal,  Body Angular Velocity Jerk Magnitude (Gyroscope), Standard deviation



## <sup>1</sup>Special Notes:


### Variable labels:

After considering assigning new more "human readable" variable names I made the decision to import the variable labels assigned by the physicists who designed the study.  The grading rubric for the Course Project does not mention variable names so I went to the Community Discussion Forum for guidance. 


 ".....but using the existing names (and noting they represent aggregated means in the CodeBook) would be good enough."

David Hood, Course Teaching Assistant

https://class.coursera.org/getdata-015/forum/thread?thread_id=27


### Units of Measure:

**The units of measure are cycle per second,**

"The cycle per second was a once-common English name for the unit of frequency now known as the hertz."

https://en.wikipedia.org/wiki/Cycle_per_second


**however they can be expressed differently.**

"Even though angular velocity, angular frequency and the unit hertz all have the dimension 1/s (reciprocal second), angular velocity and angular frequency are not expressed in hertz,[5] but rather in an appropriate angular unit such as radians per second."

https://en.wikipedia.org/wiki/Hertz



## <sup>2</sup>References:


### Raw Data:

The raw data for the project was downloaded from: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 


### Data Description:

A full description is available at the site where the data was obtained by the JHU-Coursera, Data Science staff: 

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 


### Citation:

Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. 
A Public Domain Dataset for Human Activity Recognition Using Smartphones. 
21th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. 
Bruges, Belgium 24-26 April 2013.



