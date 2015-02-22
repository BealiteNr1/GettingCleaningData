###Objective
Coursera course "Getting and Cleaning Data" in February 2015 had a course project:

"The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. 
The goal is to prepare tidy data that can be used for later analysis."

That´s what we were asked to do with the data mentioned below:

"You should create one R script called [run_analysis.R] that does the following. 
1. Merges the training and the test sets to create one data set.
2. Extracts only the measurements on the mean and standard deviation for each measurement. 
3. Uses descriptive activity names to name the activities in the data set.
4. Appropriately labels the data set with descriptive variable names. 
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject."

###Data source
Data stemming from site http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones, 
there you can find detailed information on data set.
Course project data [getdata_projectfiles_UCI HAR Dataset.zip] had been downloaded from Coursera site.
Codefile [run_analysis.R] assumes zip-file extracted in in working directory (i.e. data in subdirectories \test and \train)
Mass data in files [X_train.txt], [X_test.txt] has 561(!) columns; column names in [features.txt]
In addition there is one more data column in files [subject_train.txt] and [subject_test.txt]
There is one (small) file [activity_labels.txt] with names related to activity numbers.

###Description of work done
* read [features.txt] into data frame and analyze column structure
* "disable" columns other than needed (i.e. only with relevance to "mean and standard deviation"); thus, amount of input will be significantly smaller (see data description on original site for names of variables)
* read test data into data frames and add subject-column with cbind
* read/process train data analogously
* concatenate data frames with with rbind
* aggregate data on activity numer and subject number computing the mean (average) of measure variables
* set column name for activity number in order to be able to match to activity name
* read activity labels and match to activity number with merge-function
* export data frame with write table-function
