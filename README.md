# r-programming-assignments
John Richard
LIS 4370

Module #2 Assignment
Importing Data and Function Evaluation in R

In this assignment, we were assigned to evaluate the myMean function within R. We were tasked at using the provided vector and the myMean function to see the recorded output or error. 

myMean <- function(assignment2) {
  return(sum(assignment) / length(someData))
}

assignment2 <- c(16, 18, 14, 22, 27, 17, 19, 17, 17, 22, 20, 22)

myMean(assignment2)
# Error in sum(assignment) : object 'assignment' not found

The reason that the function failed was due to writing "assignment" instead of "assignment2". Additionally, someData is incorrect as it does not exist and should display "assignment2".

myMean <- function(assignment2) {
  return(sum(assignment2) / length(assignment2))
}

myMean(assignment2)
# [1] 19.25

Once those errors are fixed the myMean displays the correct mean of the sample and there are no errors to be found. 

