---
title: "Tidy Data Set"
date: "06-19-2015"

---


## Step 0


**Reading Data into R:**

**Hint: If you unpacked the data into a subdirectory called "UCI HAR Dataset" utilize that directory as your working directory - setwd("./UCI HAR Dataset")**


      # The "Samsung data" should be loaded into your working directory before running this code.
      # Link: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
      
      # Hint: If you unpacked the data into a subdirectory called "UCI HAR Dataset" 
      # utilize that directory as your working directory - setwd("./UCI HAR Dataset")

      # This code was run using R version 3.1.3 with the dplyr library as the only extra package. 

      # Load dplyr

      library(dplyr)

      # Read data into R 

      activity_labels <- read.table("./activity_labels.txt", stringsAsFactors = FALSE)
      features <- read.table("./features.txt", stringsAsFactors = FALSE)
      testSubj <- read.table("./test/subject_test.txt")
      testY <- read.table("./test/y_test.txt")
      testX <- read.table("./test/X_test.txt")
      trainSubj <- read.table("./train/subject_train.txt")
      trainY <- read.table("./train/y_train.txt")
      trainX <- read.table("./train/X_train.txt")


I spent some time reviewing the instructions and data before starting this project, and determined that the files "activity_labels.txt", "features.txt", "subject_test.txt", "X_test.txt", "y_test.txt", "subject_train.txt", "X_train.txt", and "y_train.txt" held the data need to complete the assignment.  The files were in good condition so I was able to use the read.table() command to load the files into R. 



## Step 1

**Combine data in to one data set:**

      colnames(testSubj) <- "S1"
      colnames(testY) <- "Y1"
      testAll <- cbind(testSubj, testY, testX)

      colnames(trainSubj) <- "S1"
      colnames(trainY) <- "Y1"
      trainAll <- cbind(trainSubj, trainY, trainX)

      onedataset <- rbind(testAll, trainAll)


Before starting the process of combining the data sets the colnames() function was used to assigned column names to "subject_test" (S1), "y_test" (Y1), "subject_train" (S1), and "y_train"(Y1).  Doing this avoided the problem of having three different columns named "V1" in the table of combined data.  The cbind() function was then used to combined all "test" files together, and then all "train" files together.  Then the rbind() function was used to combine all the data into one data set appropriately named "onedataset"  


## Step 2

**Extract measurements on the mean and standard deviation:**


      fIndex1 <- mutate(features, index = V1 + 2)

      fIndex2 <- fIndex1[c(1:6, 41:46, 81:86, 121:126, 161:166, 201:202, 214:215, 227:228, 240:241,
                          253:254, 266:271, 345:350, 424:429, 503:504, 516:517, 529:530, 542:543),]
                    
      fIndex <- c(1, 2, fIndex2$index)

      MeanStd <- onedataset[, fIndex]


Before "[e]xtract[ing] only the measurements on the mean and standard deviation for each measurement" an index was created.  First the mutate() function was used to add an index column to the "features" and a new data.frame named  "fIndex1" was created.  Then "fIndex2" was created from a subset of "fIndex1" which contained the labels and column numbers for the measurements required for the assignment, and from this the final key "fIndex" was created.  "fIndex"  was used to subset "onedataset" extracting only the required messurements and creating "MeanStd".  (Special note the subset of "fIndex1" was selected by identifying the "variables of the feature vector for each pattern" mark as mean(), or std().  The applicable rows were then isolated in the subset.)    



## Step 3 & 4

**Label with descriptive activity names and descriptive variable names:**


      Names1 <- mutate(MeanStd, Y1 = factor(Y1, labels = activity_labels$V2))

      Names2 <- c("Subject", "Activity", fIndex2$V2)

      colnames(Names1) <- Names2

      DataSet1 <- arrange(Names1, Activity, Subject)


Using the mutate() function, column Y1 in "MeanStd"  was change into factor labels and "Names1" was created.  Then the column names were stored in an vector called "Names2", and using the colnames() function "Names2" provided the column names for "Names1".  The arrange() function was then used to create a new data.frame called "DataSet1" with the data from "Names1" arranged by "Activity", and "Subject". 


## Step 5


**Create independent tidy data set with the average of each variable for each activity and each subject:**


**First create separate data sets for each Activity:**


      walking <- DataSet1[(DataSet1$Activity == "WALKING"),]
      walking_upstairs <- DataSet1[(DataSet1$Activity == "WALKING_UPSTAIRS"),]
      walking_downstairs <- DataSet1[(DataSet1$Activity == "WALKING_DOWNSTAIRS"),]
      sitting <- DataSet1[(DataSet1$Activity == "SITTING"),]
      standing <- DataSet1[(DataSet1$Activity == "STANDING"),]
      laying <- DataSet1[(DataSet1$Activity == "LAYING"),]

Subsets of data from "DataSet1" was used to create six new data frames, separating the data by activity. 


**Next generate averages for each Activity by Subject:**


      walking2 <- walking%>% group_by(Subject)%>% summarise_each(funs(mean))
      walking_upstairs2 <- walking_upstairs%>% group_by(Subject)%>% summarise_each(funs(mean))
      walking_downstairs2 <- walking_downstairs%>% group_by(Subject)%>% summarise_each(funs(mean))
      sitting2 <- sitting%>% group_by(Subject)%>% summarise_each(funs(mean))
      standing2 <- standing%>% group_by(Subject)%>% summarise_each(funs(mean))
      laying2 <- laying%>% group_by(Subject)%>% summarise_each(funs(mean))


These data frames were each grouped by "Subject" utilizing the Group_by() function, and the mean was calculated for each measurement for each subject utilizing the summarise_each() function.


**Next clean up data sets:**


      walking3 <- mutate(walking2, Activity = factor(Activity, labels = "WALKING"))
      walking_upstairs3 <- mutate(walking_upstairs2, Activity = factor(Activity, labels = "WALKING_UPSTAIRS"))
      walking_downstairs3 <- mutate(walking_downstairs2, Activity = factor(Activity, labels= "WALKING_DOWNSTAIRS"))
      sitting3 <- mutate(sitting2, Activity = factor(Activity, labels = "SITTING"))
      standing3 <- mutate(standing2, Activity = factor(Activity, labels = "STANDING"))
      laying3 <- mutate(laying2, Activity = factor(Activity, labels = "LAYING"))

When R computed the mean using the group_by() and summarise_each() functions it converted the factor labels in the "Activity" column into factor levels.  So the factor function was used to reconvert all these back into factor labels.


**Next combine data into one tidy data set:**


      DataTidy <- rbind(walking3, walking_upstairs3, walking_downstairs3, sitting3, standing3, laying3)

Now the rbind() function was used to join all these back into one tidy data set call "DataTidy".

**Generate text file to illistrate tidy data set:**


      write.table(DataTidy, file = "./DataTidy.txt", row.name = FALSE)

Using the write.table() function a text file was created for sharing the data.




