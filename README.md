---
title: "Readme.md"
author: "Kurt Kessler"
date: "August 21, 2014"
output: html_document
---


#Purpose of this document
* The following code is the course project for Getting and Cleaning Data


```{r}
# run_analysis.R
# Getting and Cleaning Data - Course Project


# You should create one R script called run_analysis.R that does the following. 
# 1. Merges the training and the test sets to create one data set.
# 2. Extracts only the measurements on the mean and standard deviation for each measurement. 
# 3. Uses descriptive activity names to name the activities in the data set
# 4. Appropriately labels the data set with descriptive variable names. 
# 5. Creates a second, independent tidy data set with the average of each variable for each activity and each subject. 



# 1. Merges the training and the test sets to create one data set.
# setwd("~/Dropbox/Learning/Coursera/Data Science/3 - Getting and Cleaning Data/Course Project")
# setwd("C:/Users/kkessler/Dropbox/Learning/Coursera/Data Science/3 - Getting and Cleaning Data/Course Project")
# The data consists of 4 files for the training as well as the test data:
# - features.txt - column names of the variables (used for both test data and training data)
# - X_test.txt and x_train.txt - 
# - y_train.txt and y_train.txt - labels 
# - subject_test.txt and subject_train.txt - 

# Import the features file (column names of the variables) and import the data
features <- read.table("./UCI HAR Dataset/features.txt")
column_names <- c("Subject", "Activity", as.character(features[,2]))

x_test_data <- read.table("./UCI HAR Dataset/test/X_test.txt")
x_test_labels <- read.table("./UCI HAR Dataset/test/y_test.txt")
x_test_subjects <- read.table("./UCI HAR Dataset/test/subject_test.txt")

x_train_data <- read.table("./UCI HAR Dataset/train/X_train.txt")
x_train_labels <- read.table("./UCI HAR Dataset/train/y_train.txt")
x_train_subjects <- read.table("./UCI HAR Dataset/train/subject_train.txt")

# Merge data, labels, and subject columns
test_data <- cbind(x_test_subjects, x_test_labels, x_test_data)
train_data <- cbind(x_train_subjects, x_train_labels, x_train_data)

# Name the columns of the test / training data set
names(test_data)  <- column_names
names(train_data) <- column_names

# Last - Combine the test and train data sets
data_all <- rbind(test_data, train_data)



# 2. Extracts only the measurements on the mean and standard deviation for each measurement. 
# The grep function was NOT discussed in class.  But the next line selects only column names where
# "mean" or "std" is in the column name.  Yeah, it took me a while....
# http://stackoverflow.com/questions/4220631/how-do-i-grep-in-r
# http://stat.ethz.ch/R-manual/R-devel/library/base/html/grep.html
# http://www.endmemo.com/program/R/grep.php
tmp <- grep("(mean|std)\\(\\)", colnames(data_all), value = TRUE)
data_all_filter <- data_all[, c("Subject", "Activity", tmp)]
rm(tmp)



# 3. Uses descriptive activity names to name the activities in the data set
# Import the activity labels
activity_labels <- read.table("./UCI HAR Dataset/activity_labels.txt")
colnames(activity_labels) <- c("activity", "label")

# Make the activity column a factor and recode the levels
tmp <- activity_labels$activity
names(tmp) <- activity_labels$label
data_all_filter$Activity <- factor(data_all_filter$Activity, levels = tmp, labels = names(tmp))
rm(tmp)



# 4. Appropriately labels the data set with descriptive variable names.
# gsub function - http://www.endmemo.com/program/R/grep.php
colnames(data_all_filter) <- gsub("\\(\\)", "", tolower(colnames(data_all_filter)))
colnames(data_all_filter) <- gsub("-", ".", colnames(data_all_filter))



# 5. Creates a second, independent tidy data set with the average of each variable for each activity and each subject.
library(reshape2)
# http://cran.r-project.org/web/packages/reshape2/reshape2.pdf
column_ids <- colnames(data_all_filter)[1:2]
column_vars <- colnames(data_all_filter)[3:length(colnames(data_all_filter))]

# Reshape the data and take the mean of each variable by subject and activity
tmp <- melt(data_all_filter, id=column_ids, measure.vars=column_vars)
data_cast <- dcast(tmp, subject + activity ~ variable, mean)
rm(tmp)

# Add 'avg' to the variable name to differentiate the data in the new data set.
colnames(data_cast) <- c(column_ids, gsub("(.*)", "avg.\\1", column_vars))


# Write data sets to a file
write.table(data_all_filter, file = "class_output.txt", row.names = FALSE, quote = FALSE)
write.table(data_cast, file = "class_output_avg.txt", row.names = FALSE, quote = FALSE)


```

