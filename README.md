---
title: "Tidy Data Set"
date: "06-19-2015"

---


## Step 0


**Reading Data into R:**


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



## Step 1

**Combine data in to one data set:**



      colnames(testSubj) <- "S1"
      colnames(testY) <- "Y1"
      testAll <- cbind(testSubj, testY, testX)

      colnames(trainSubj) <- "S1"
      colnames(trainY) <- "Y1"
      trainAll <- cbind(trainSubj, trainY, trainX)

      onedataset <- rbind(testAll, trainAll)


## Step 2

**Extract measurements on the mean and standard deviation:**



      fIndex1 <- mutate(features, index = V1 + 2)

      fIndex2 <- fIndex1[c(1:6, 41:46, 81:86, 121:126, 161:166, 201:202, 214:215, 227:228, 240:241,
                          253:254, 266:271, 345:350, 424:429, 503:504, 516:517, 529:530, 542:543),]
                    
      fIndex <- c(1, 2, fIndex2$index)

      MeanStd <- onedataset[, fIndex]


## Step 3 & 4

**Label with descriptive activity names and descriptive variable names:**


      Names1 <- mutate(MeanStd, Y1 = factor(Y1, labels = activity_labels$V2))

      Names2 <- c("Subject", "Activity", fIndex2$V2)

      colnames(Names1) <- Names2

      DataSet1 <- arrange(Names1, Activity, Subject)



## Step 5


**Create independent tidy data set with the average of each variable for each activity and each subject:**


**First create separate data sets for each Activity:**





      walking <- DataSet1[(DataSet1$Activity == "WALKING"),]
      walking_upstairs <- DataSet1[(DataSet1$Activity == "WALKING_UPSTAIRS"),]
      walking_downstairs <- DataSet1[(DataSet1$Activity == "WALKING_DOWNSTAIRS"),]
      sitting <- DataSet1[(DataSet1$Activity == "SITTING"),]
      standing <- DataSet1[(DataSet1$Activity == "STANDING"),]
      laying <- DataSet1[(DataSet1$Activity == "LAYING"),]



**Next generate averages for each Activity by Subject:**



      walking2 <- walking%>% group_by(Subject)%>% summarise_each(funs(mean))
      walking_upstairs2 <- walking_upstairs%>% group_by(Subject)%>% summarise_each(funs(mean))
      walking_downstairs2 <- walking_downstairs%>% group_by(Subject)%>% summarise_each(funs(mean))
      sitting2 <- sitting%>% group_by(Subject)%>% summarise_each(funs(mean))
      standing2 <- standing%>% group_by(Subject)%>% summarise_each(funs(mean))
      laying2 <- laying%>% group_by(Subject)%>% summarise_each(funs(mean))




**Next clean up data sets:**



      walking3 <- mutate(walking2, Activity = factor(Activity, labels = "WALKING"))
      walking_upstairs3 <- mutate(walking_upstairs2, Activity = factor(Activity, labels = "WALKING_UPSTAIRS"))
      walking_downstairs3 <- mutate(walking_downstairs2, Activity = factor(Activity, labels= "WALKING_DOWNSTAIRS"))
      sitting3 <- mutate(sitting2, Activity = factor(Activity, labels = "SITTING"))
      standing3 <- mutate(standing2, Activity = factor(Activity, labels = "STANDING"))
      laying3 <- mutate(laying2, Activity = factor(Activity, labels = "LAYING"))



**Next combine data into one tidy data set:**



      DataTidy <- rbind(walking3, walking_upstairs3, walking_downstairs3, sitting3, standing3, laying3)


**Generate text file to illistrate tidy data set:**




      write.table(DataTidy, file = "./DataTidy.txt", row.name = FALSE)





