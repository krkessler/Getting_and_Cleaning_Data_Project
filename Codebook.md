#Codebook

##Purpose of this R code
* From the Getting and Cleaning Data course project description
>_The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. The
goal is to prepare tidy data that can be used for later analysis. You will be graded by your peers on a
series of yes/no questions related to the project. You will be required to submit: 1) a tidy data set as
described below, 2) a link to a Github repository with your script for performing the analysis, and 3) a
code book that describes the variables, the data, and any transformations or work that you performed to
clean up the data called CodeBook.md. You should also include a README.md in the repo with your
scripts. This repo explains how all of the scripts work and how they are connected.  

>>One of the most exciting areas in all of data science right now is wearable computing - see for example
this article (http://www.insideactivitytracking.com/data-science-activity-tracking-and-the-battle-for-the-
worlds-top-sports-brand/). Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most
advanced algorithms to attract new users. The data linked to from the course website represent data
collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available
at the site where the data was obtained: 

>>http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
>>(http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones) 

>>Here are the data for the project: 
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
(https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)   

>>You should create one R script called run_analysis.R that does the following.   
1 Merges the training and the test sets to create one data set.  
2  Extracts only the measurements on the mean and standard deviation for each measurement.   
3  Uses descriptive activity names to name the activities in the data set  
4  Appropriately labels the data set with descriptive variable names.   
5  Creates a second, independent tidy data set with the average of each variable for each activity and each subject. _

##Source data
* The data can be found [here](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)

##Fields used in Class_Output_Avg.txt
###Class_Output_Avg.txt is the output file requried by the project
* subject                       
* activity                      
* avg.tbodyacc.mean.x           
* avg.tbodyacc.mean.y          
* avg.tbodyacc.mean.z           
* avg.tbodyacc.std.x            
* avg.tbodyacc.std.y            
* avg.tbodyacc.std.z           
* avg.tgravityacc.mean.x        
* avg.tgravityacc.mean.y        
* avg.tgravityacc.mean.z        
* avg.tgravityacc.std.x        
* avg.tgravityacc.std.y         
* avg.tgravityacc.std.z         
* avg.tbodyaccjerk.mean.x       
* avg.tbodyaccjerk.mean.y      
* avg.tbodyaccjerk.mean.z       
* avg.tbodyaccjerk.std.x        
* avg.tbodyaccjerk.std.y        
* avg.tbodyaccjerk.std.z       
* avg.tbodygyro.mean.x          
* avg.tbodygyro.mean.y          
* avg.tbodygyro.mean.z          
* avg.tbodygyro.std.x          
* avg.tbodygyro.std.y           
* avg.tbodygyro.std.z           
* avg.tbodygyrojerk.mean.x      
* avg.tbodygyrojerk.mean.y     
* avg.tbodygyrojerk.mean.z      
* avg.tbodygyrojerk.std.x       
* avg.tbodygyrojerk.std.y       
* avg.tbodygyrojerk.std.z      
* avg.tbodyaccmag.mean          
* avg.tbodyaccmag.std           
* avg.tgravityaccmag.mean       
* avg.tgravityaccmag.std       
* avg.tbodyaccjerkmag.mean      
* avg.tbodyaccjerkmag.std       
* avg.tbodygyromag.mean         
* avg.tbodygyromag.std         
* avg.tbodygyrojerkmag.mean     
* avg.tbodygyrojerkmag.std      
* avg.fbodyacc.mean.x           
* avg.fbodyacc.mean.y          
* avg.fbodyacc.mean.z           
* avg.fbodyacc.std.x            
* avg.fbodyacc.std.y            
* avg.fbodyacc.std.z           
* avg.fbodyaccjerk.mean.x       
* avg.fbodyaccjerk.mean.y       
* avg.fbodyaccjerk.mean.z       
* avg.fbodyaccjerk.std.x       
* avg.fbodyaccjerk.std.y        
* avg.fbodyaccjerk.std.z        
* avg.fbodygyro.mean.x          
* avg.fbodygyro.mean.y         
* avg.fbodygyro.mean.z          
* avg.fbodygyro.std.x           
* avg.fbodygyro.std.y           
* avg.fbodygyro.std.z          
* avg.fbodyaccmag.mean          
* avg.fbodyaccmag.std           
* avg.fbodybodyaccjerkmag.mean  
* avg.fbodybodyaccjerkmag.std  
* avg.fbodybodygyromag.mean     
* avg.fbodybodygyromag.std      
* avg.fbodybodygyrojerkmag.mean 
* avg.fbodybodygyrojerkmag.std 