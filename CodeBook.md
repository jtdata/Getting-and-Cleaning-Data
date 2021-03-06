#Code Book
##Raw data collection

The raw data were obtained from the UCI Machine Learning repository, particularly the Human Activity Recognition Using Smartphones Data Set [1] that was used by the original collectors to conduct experiments exploiting Support Vector Machine (SVM) [2].

Activity Recognition (AR) aimed to recognize the actions and goals of one or more agents from a series of observations on the agents' actions and the environmental conditions [3]. The collectors used a sensor based approach employing smartphones as sensing tools. Smartphones were an effective solution for AR, because they came with embedded built-in sensors such as microphones, dual cameras, accelerometers, gyroscopes, etc.

The data set was built from experiments carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (walking, walking upstairs, walking downstairs, sitting, standing, laying) while wearing a Samsung Galaxy SII on the waist. Using its embedded accelerometer and gyroscope, 3-axial linear acceleration and 3-axial angular velocity were captured at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually [4].

The obtained data set was randomly partitioned into two sets, where 70% of the volunteers were selected for generating the training data and 30% the test data.
##Signals

The 3-axial time domain [5] signals from accelerometer and gyroscope were captured at a constant rate of 50 Hz [6] and then filtered to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals using another filter. The body linear acceleration and angular velocity were derived in time to obtain Jerk signals [7]. The magnitude [8] of these three-dimensional signals were also calculated using the Euclidean norm [9]. Then a Fast Fourier Transform (FFT) [10] was applied to some of these time domain signals to obtain frequency domain [11] signals.

The signals were sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window at 50 Hz). From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

The set of variables estimated from these signals were:

    mean(): Mean value
    std(): Standard deviation
    mad(): Median absolute deviation
    max(): Largest value in array
    min(): Smallest value in array
    sma(): Signal magnitude area
    energy(): Energy measure. Sum of the squares divided by the number of values.
    iqr(): Interquartile range
    entropy(): Signal entropy
    arCoeff(): Autoregression coefficients with Burg order equal to 4
    correlation(): Correlation coefficient between two signals
    maxInds(): Index of the frequency component with largest magnitude
    meanFreq(): Weighted average of the frequency components to obtain a mean frequency
    skewness(): Skewness of the frequency domain signal
    kurtosis(): Kurtosis of the frequency domain signal
    bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
    angle(): Angle between some vectors.

No unit of measures was reported because all features were normalized and bounded within [-1,1].
##Data transformation

Test and training data (X_train.txt, X_test.txt), subject ids (subject_train.txt, subject_test.txt) and activity ids (y_train.txt, y_test.txt) were merged to obtain a single data set. Variables were labelled with the names assigned by original collectors (features.txt).

From the merged data set an intermediate data set was extracted with only the values of estimated mean (variables with labels that contain "mean") and standard deviation (variables with labels that contain "std").

A new column was added to intermediate data set with the activity description. Activity id column was used to look up descriptions in activity_labels.txt.

Labels from the original collectors were changed to obtain valid R names without parentheses, dashes and commas, and to obtain more descriptive labels

From the intermediate data set a final tidy data set was created where numeric variables were averaged for each activity and subject.

The tidy data set contained 10299 observations with 81 variables divided into activity labels (Activity): WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING; 
identifiers of the subject carrying out the experiment (Subject): 1, 3, 5, 6, 7, 8, 11, 14, 15, 16, 17, 19, 21, 22, 23, 25, 26, 27, 28, 29, 30; 
a 79-feature vector with time and frequency domain signal variables (numeric)

The following list relates the 17 signals to the variable names in the data set. ".XYZ" denotes three variables, one for each axis.

Body Acceleration - TimeDomain.BodyAcceleration.XYZ - FrequencyDomain.BodyAcceleration.XYZ
Gravity Acceleration - TimeDomain.GravityAcceleration.XYZ
Body Acceleration Jerk - TimeDomain.BodyAccelerationJerk.XYZ - FrequencyDomain.BodyAccelerationJerk.XYZ
Body Angular Speed - TimeDomain.BodyAngularSpeed.XYZ - FrequencyDomain.BodyAngularSpeed.XYZ
Body Angular Acceleration - TimeDomain.BodyAngularAcceleration.XYZ 	
Body Acceleration Magnitude - TimeDomain.BodyAccelerationMagnitude - FrequencyDomain.BodyAccelerationMagnitude
Gravity Acceleration Magnitude - TimeDomain.GravityAccelerationMagnitude 	
Body Acceleration Jerk Magnitude - TimeDomain.BodyAccelerationJerkMagnitude - FrequencyDomain.BodyAccelerationJerkMagnitude
Body Angular Speed Magnitude - TimeDomain.BodyAngularSpeedMagnitude - FrequencyDomain.BodyAngularSpeedMagnitude
Body Angular Acceleration Magnitude -TimeDomain.BodyAngularAccelerationMagnitude -	FrequencyDomain.BodyAngularAccelerationMagnitude

For variables derived from mean and standard deviation estimation, the previous labels were edited to include the terms "Mean" or "StandardDeviation".

The data set was then written to the file sensor_avg_by_act_sub.txt.
##References

1. Human Activity Recognition Using Smartphones Data Set. URL: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones.
2. Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012
3. Activity recognition. URL: http://en.wikipedia.org/wiki/Activity_recognition. 
4. Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. A Public Domain Dataset for Human Activity Recognition Using Smartphones. ESANN 2013 proceedings, European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning. Bruges (Belgium), 24-26 April 2013
5. Time domain. URL: http://en.wikipedia.org/wiki/Time-domain.
6. Hertz. URL: http://en.wikipedia.org/wiki/Hertz.
7. Jerk. URL: http://en.wikipedia.org/wiki/Jerk_(physics).
8. Magnitude. URL: http://en.wikipedia.org/wiki/Magnitude_(mathematics). 
9. Euclidean norm. URL: http://en.wikipedia.org/wiki/Norm_(mathematics)#Euclidean_norm. 
10. Fast Fourier transform. URL: http://en.wikipedia.org/wiki/Fast_Fourier_Transform. 
11. Frequency domain. URL: http://en.wikipedia.org/wiki/Frequency_domain. 
12. Tidy data set. URL: https://github.com/jtleek/datasharing#the-tidy-data-set. 
