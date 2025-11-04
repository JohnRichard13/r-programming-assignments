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

Module #4 Assignemnt
Visualizing and Interpreting Hospital Patient Data

Freqeuncy <- c(0.6, 0.3, 0.4, 0.4, 0.2, 0.6, 0.3, 0.4, 0.9, 0.2)
BloodPressure <- c(103, 87, 32, 42, 59, 109, 78, 205, 135, 176)
FirstAssess <- c(1, 1, 1, 1, 0, 0, 0, 0, NA, 1)
SecondAssess <- c(0, 0, 1, 1, 0, 0, 1, 1, 1, 1)
FinalDecision <- c(0, 1, 0, 1, 0, 1, 0, 1, 1, 1)


df_hosp <- data.frame(
  Freqeuncy, BloodPressure, FirstAssess,
  SecondAssess, FinalDecision, stringsAsFactors = FALSE
)

summary(df_hosp)
df_hosp <- na.omit(df_hosp)


boxplot(
  BloodPressure ~ FirstAssess,
  data = df_hosp,
  names = c("Good", "Bad"),
  ylab = "Blood Pressure",
  main = "BP by First MD Assessment"
)

<img width="686" height="507" alt="image" src="https://github.com/user-attachments/assets/04eebbda-5d2c-4d33-801b-eb47a6a07261" />

boxplot(
  BloodPressure ~ SecondAssess,
  data = df_hosp,
  names = c("Low","High"),
  ylab = "Blood Pressure",
  main = "BP by Second MD Assessment"
)

<img width="690" height="516" alt="image" src="https://github.com/user-attachments/assets/8c140201-a767-46a0-9514-9579ec2674fe" />

boxplot(
  BloodPressure ~ FinalDecision,
  data = df_hosp,
  names = c("Low", "High"),
  ylab = "Blood Pressure",
  main = "BP by Final Decision"
)

<img width="666" height="507" alt="image" src="https://github.com/user-attachments/assets/3ffd14f2-8a42-45fb-beaa-670d032bebd4" />

hist(
  df_hosp$Freqeuncy,
  breaks = seq(0, 1, by = 0.1),
  xlab = "Visit Frequency",
  main = "Histogram of Visit Frequency"
)

<img width="685" height="509" alt="image" src="https://github.com/user-attachments/assets/3091c5ca-0529-43e5-8233-9572322ab888" />

hist(
  df_hosp$BloodPressure,
  breaks = 8,
  xlab = "Blood Pressure",
  main = "Histogram of Blood Pressure"
)

<img width="686" height="517" alt="image" src="https://github.com/user-attachments/assets/695144e3-d40b-46d4-b2d3-52be0b5fd2a7" />

Module #5 Assignment
Matrix Algebra in R

A <- matrix(1:100, nrow = 10)
B <- matrix(1:1000, nrow = 10)

dim(A) 
dim(B)

invA <- solve(A)
detA <- det(A)

invB <- tryCatch(solve(B), error = function(e) e)
detB <- tryCatch(det(B),   error = function(e) e)

print(invA)
print(detA)
print(invB)
print(detB)

Module #6 Assignment
Matrix Operations and Construction

A <- matrix(c(2, 0, 1, 3), ncol = 2)
B <- matrix(c(5, 2, 4, -1), ncol = 2)

A_plus_B <- A + B
A_plus_B


A_minus_B <- A - B
A_minus_B

D <- diag(c(4, 1, 2, 3))
D

M <- diag(c(3, 3, 3, 3, 3))
M[1, 2:5] <- 1
M[2:5, 1] <- 2
M

Module #7 Assignment
Exploring R’s Object Oriented Systems

data("mtcars")
head(mtcars)
str(mtcars)

print(mtcars)


summary(mtcars)
summary(mtcars$mpg)


plot(mtcars$mpg, mtcars$hp, main = "MPG vs Horsepower", xlab = "MPG", ylab = "Horsepower")
plot(as.factor(mtcars$cyl), mtcars$mpg, main="MPG by Cylinders")


class(mtcars)
class(mtcars$mpg)


s3_obj <- list(name = "John", age = 22, GPA = 3.7)
class(s3_obj) <- "student_s3"


print.student_s3 <- function(x) {
  cat("S3 Student Object:\n")
  cat("Name:", x$name, "\nAge:", x$age, "\nGPA:", x$GPA, "\n")
  
}


print(s3_obj)


setClass("student_s4",
         slots = c(name = "character", age = "numeric", GPA = "numeric"))

s4_obj <- new("student_s4", name = "John", age = 22, GPA = 3.7)

setMethod("show", "student_s4", function(object) {
  cat("S4 Student Object:\n")
  cat("Name:", object@name, "\nAge:", object@age, "\nGPA:", object@GPA, "\n")
})

s4_obj

Module #8 Assignment
Input/Output, String Manipulation, and the plyr Package

student6 <- read.table("Assignment 6 Dataset.txt", header = TRUE, sep = "," , stringsAsFactors = FALSE)

head(student6)

library(plyr)
gender_mean <- ddply(
  student6,
  "Sex",
  summarise,
  GradeAverage = mean(Grade, na.rm = TRUE)
)

print(gender_mean)

write.table(
  gender_mean,
  file = "gender_mean.txt",
  sep = "\t",
  row.names = FALSE
)


i_students <- subset(
  student6,
  grepl("i", Name, ignore.case = TRUE)
)

i_students

write.csv(
  i_students$Name, 
  file = "i_students.csv",
  row.names = FALSE,
  quote = FALSE
)


write.csv(
  i_students,
  file = "i_students_full,csv",
  row.names = FALSE
)

list.files()


Module # 9 Assignment
Visualization in R - Base Graphics, Lattice, and ggplot2.

data("airquality")

head(airquality)

str(airquality)

summary(airquality)

air_data <- na.omit(airquality)

plot(air_data$Temp, air_data$Ozone,
     main = "Base R: Ozone vs Temperature",
     xlab = "Temperature (F)",
     ylab = "Ozone (ppb)",
     col = "blue",
     pch = 16)

hist(air_data$Wind,
     main = "Base R: Wind Distribution",
     xlab = "Wind (mph)",
     col = "lightgreen",
     breaks = 10)

library(lattice)

xyplot(Ozone ~ Temp | factor(Month),
       data = air_data,
       main = "Lattice: Ozone vs Temp by Month",
       xlab = "Temperature (F)",
       ylab = "Ozone (ppb)",
       pch = 16,
       col = "blue")

bwplot(Ozone ~ factor(Month),
       data = air_data,
       main = "Lattice: Ozone by Month")

library(ggplot2)

ggplot(air_data, aes(x = Temp, y = Ozone)) +
  geom_point(color = "blue") +
  geom_smooth(method = "lm", se = FALSE, color = "red") +
  facet_wrap(~ Month) +
  labs(title = "ggplot2: Ozone vs Temp by Month",
       x = "Temperature (F)",
       y = "Ozone (ppb)")

ggplot(air_data, aes(x = Wind)) +
  geom_histogram(binwidth = 1, fill = "lightgreen", color = "black") +
  labs(title = "ggplot2: Wind Distribution",
       x = "Wind (mph)",
       y = "Count")
  
Module # 11 Assignment
tukey.outlier <- function(x) {
  q1 <- quantile(x, 0.25, na.rm = TRUE)
  q3 <- quantile(x, 0.75, na.rm = TRUE)
  iqr <- q3 - q1
  (x < (q1 - 1.5 * iqr)) | (x > (q3 + 1.5 * iqr))
}


tukey_multiple <- function(x) {
  outliers <- array(TRUE, dim = dim(x))
  for (j in seq_len(ncol(x))) {
    outliers[, j] <- outliers[, j] & tukey.outlier(x[, j])
  }
  
  outlier.vec <- logical(nrow(x))
  for (i in seq_len(nrow(x))) {
    outlier.vec[i] <- all(outliers[i, ])
  }
  
  return(outlier.vec)
}

set.seed(123)
test_mat <- matrix(rnorm(50), nrow = 10)
tukey_multiple(test_mat)
