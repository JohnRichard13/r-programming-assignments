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

Module #3 Assigment 
Analyzing 2016 data “Poll” Data in R

library(ggplot2)
library(reshape2)

Name <- c("Jeb", "Donald", "Ted", "Marco", "Carly", "Hillary", "Bernie")
ABC_poll <- c(4,62,51,21,2,14,15)
CBS_poll <- c(12,75,43,19,1,21,19)

df_polls <- data.frame(Name, ABC_poll, CBS_poll)
str(df_polls)
head(df_polls)

mean(df_polls$ABC_poll)
median(df_polls$CBS_poll)
range(df_polls[, c("ABC_poll","CBS_poll")])

df_polls$Diff <- df_polls$CBS_poll - df_polls$ABC_poll

df_long <- melt(df_polls[, c("Name", "ABC_poll", "CBS_poll")], id.vars = "Name")


ggplot(df_long, aes(x = Name, y = value, fill = variable)) +
  geom_bar(stat = "identity", position = "dodge") +
  labs(title = "ABC vs CBS Poll Results",
       x = "Candidate", y = "Poll Percentage",
       fill = "Poll Source") +
  theme_minimal()

  <img width="678" height="555" alt="image" src="https://github.com/user-attachments/assets/13355c21-8a20-4c23-85c3-fbcf43e2f2c5" />
