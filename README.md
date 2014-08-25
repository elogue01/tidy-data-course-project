tidy-data-course-project
========================

This repo contains the R script, codebook and README files for the Getting and 
Cleaning Data Course Project.

## Data Set Explanation

For this assignment, data obtained from the Human Activity Recognition Using 
Smartphones Data Set Version 1.0 was obtained from the url: 
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
These raw data are from an experiment carried out with 30 volunteers in which 
each subject performed six activities wearing a smartphone. Data was obtained 
from the embedded accelerometer and gyroscope sensors in the x,y and z axis. 
This raw data set was processed using the R script contained in this repo.  An
explanation of what this R script does follows.

## R Script Explanation

1.  Prior to running this script the data was downloaded from the web using the
url: 
"https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
This downloaded a directory named "UCI HAR Data" onto the desktop which 
contained directories named "train" and "test". 

2.  The script first reads the data from the train and test directories using
the read.table() function.  This function takes a long time to read the x_test 
and x_train data but fread, which would read these data more rapidly, would not 
read the data without throwing an error " Not positioned correctly after testing
format of header row. ch=' ' ". If a peer reviewer has insight in how to get 
fread to work in this case, I would be interested in knowing the answer.

3. These tables are then combined into one large data set using rbind() and
cbind() functions.  At this time the first two columns are also named 
"subject"" and "activity"" to correspond to the data in those first two columns. 

4. This large dataframe is then subsetted so that only the mean and standard 
deviation values are retained in the new data set.

5. The subsetted data set is then ordered according to the subject number and 
the numeric activity code.  This is not specifically called for in the 
assignment instructions but makes the data look nicer and more readable in my 
opinion.

6. The numeric activity codes are then replaced with descriptive activity names 
that correspond to the numeric codes in the activity_lables.txt file.

7. The data is then converted using the data.table() function. Using the data 
table package the means are calculated for each subject and activity combination
in each column. Descriptive variable names are also added in this set which is 
out of sequence with the assignment instructions but still results in the 
desired output.  The descriptive variable names are in CamelCase in order to 
increase the readability of these names.

8. Finally, the R script writes the tidy data set into a text file using the 
write.table() function.  This table is readable using the read.table() function.




