--- 
title_meta  : Chapter 1
title       : Basics of R, summary statistics and tabulation
description : "In this chapter, you will get to know some basic features of R. You will also learn to check the summary statistics of continuous variables and draw some simple graphs."
 
--- type:NormalExercise lang:r xp:100 skills:1 key:3d083aaefb
## Let's get started
 
In the box below you can see the instructions for the exercise. On the right in the upper window you can type your code. That window is called editor. You can execute the code by pressing Ctrl+Enter (Cmd+Enter in Mac) when the cursor is on the same line with your command. If your command is on multiple lines you must select all those rows and then Ctrl+Enter or Cmd+Enter. When you run your commands, the results appear in the window under the editor. That window is called console.
 
You can use R as a calculator. You can run basic mathematical operations like this: 
 
- Addition: `+`
- Subtraction: `-`
- Multiplication: `*`
- Division: `/`
- Exponentiation: `^`
 
In order to understand better your own code, or in case you want to save it as an actual R script (It is possible if you have R installed in your computer.) it is good to comment on your code. That can be done by typing `#` at the beginning of the row. Any text you type on that row will be considered as a comment. For example _Calculate the mean of these numbers: 1, 3, 8, 10, 12_ in the editor window is a comment.
 
*** =instructions
 - Assume we have a sample of ten people from the cardiac-dataset. Their ejectionfractions (in percents) are 64, 57, 52, 37, 57, 62, 60, 57, 57 and 37. 
   - Calculate the mean of ejectionfraction for the sample. 
   - Calculate the standard deviation of ejectionfraction for the sample. 

*** =hint
Just revise the formulas of mean and standard deviation! Write the numbers on the console and run the lines.
 
*** =pre_exercise_code
```{r}
 # no pec
```
 
*** =sample_code
```{r}
# Calculate the arithmetic mean of these numbers: 1, 3, 8, 10, 12
(1 + 3 + 8 + 10 + 12) / 5
 
# Calculate the standard deviation of these numbers: 1, 3, 8, 10, 12

sqrt((((1 - 6.8)^2) + ((3 - 6.8)^2) + ((8 - 6.8)^2) + ((10 - 6.8)^2) + ((12 - 6.8)^2)) / (5 - 1))
 
# Calculate the arithmetic mean of the ejectiofraction

 
# Calculate the standard deviation of the ejectiofraction
 

```
 
*** =solution
```{r}
# Calculate the arithmetic mean of the ejectiofraction
(64 + 57 + 52 + 37 + 57 + 62 + 60 + 57 + 57 + 37) /10 
 
# Calculate the standard deviation of the ejectiofraction
sqrt((((64 - 54)^2) + ((57 - 54)^2) + ((52 - 54)^2) + ((37 - 54)^2) + ((57 - 54)^2) + ((62 - 54)^2) + ((60 - 54)^2) + ((57 - 54)^2) + ((57 - 54)^2) + ((37 - 54)^2)) / 9 )

```
 
*** =sct
```{r}
test_output_contains("54", incorrect_msg = "Make sure to add the values together and divide them by the sample size (10).")
test_output_contains("9.533", incorrect_msg = "Make sure that you have studied well the formula of standard deviation.")
success_msg("Awesome! This clearly was a piece of cake to you! Now let's move on to the next exercise.")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:cb2334e4d3
## Checking out the data! 
 
When you get a new data set, it is a good practice to first give it a quick overview: to check how many samples you have, how many variables you have, how many females/males, what is the age distrtibution for example. For categorical variables, table() is a good idea and for continous variables use summary(). To know what variables you have in your data, just type colnames(data).
 
*** =instructions
 - Find out how many observations does the cardiac-data contain. 
 - Find out how many observations does the diabetes-data contain.
 - Find out how many females are in cardiac-data.
 - Find out how many female are in diabetes- data.
 - What is the age-range in cardiac-data?
 - What is the age-range in diabetes-data?

*** =hint
Checking the dimensions of the dataset is a good way to find out how many observations are there. 
Remember to connect variables to the dataset with a '$' sign.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Hint! You can refer to our data sets just by typing "cardiac" and "diabetes". To refer to any variable in that data just type it in tho form data$variable, for example cardiac$gender.


# Fill in the sample sizes:
# Cardiac:
# Diabetes: 

# Females in cardiac-data:
# Females in diabetes-data: 
 
# Age distribution in cardiac-data:


# Age distribution in cardiac-data:
 
 
```
 
*** =solution
```{r}
# Fill in the sample sizes:
# Cardiac: 558
# Diabetes: 403

# Females in cardiac-data: 338
# Females in diabetes-data: 234
 
# Age distribution in cardiac-data:


# Age distribution in cardiac-data:

 
 
```
 
*** =sct
```{r}
test_student_typed("558", not_typed_msg = "Make sure that you have the right sample size for cardiac-data.")
test_student_typed("403", not_typed_msg = "Make sure that you have the right sample size for diabetes-data.")
test_student_typed("338", not_typed_msg = "Make sure that you have the right female number cardiac-data.")
test_student_typed("234", not_typed_msg = "Make sure that you have the right female number for diabetes-data.")

success_msg("Great! You're getting master at R! ")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:1428bf2042
## Basic plotting
 
When checking out your data, the good next step is to visualize the variables. This is how you get the first idea of their distributions and can spot the possible outliers (the kind of values that are very different from the other values.) The propably most commonly used plotting commands are hist() for histrogram, barplot() for barplot, plot() for scatter plot and boxplot() for boxplot. 
 
*** =instructions
 - Draw a barplot of the variable 'gender' in diabetes-dataset.
 
 - Draw a histogram of the variable 'age' in cardiac-dataset.
 
 - Draw a histogram of the variable 'bhr' (= "basal heart rate") in cardiac-dataset. Is there anything weird?
 
 - Draw a boxplot for cholesterol ('chol') in diabetes- data by gender.
 
 - Draw a scatter-plot for the variables maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data 


*** =hint
Checking the dimensions of the dataset is a good way to find out how many observations are there. 
Remember to connect variables to the dataset with a '$' sign.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
 
*** =sample_code
```{r}
# Draw a barplot of the variable 'gender' in cardiac-dataset
 
barplot(table(cardiac$gender))
 
# Draw a histogram of the variable 'cholmmol' (cholesterol in mmol) in diabetes-dataset
 
hist(diabetes$cholmmol)
 
# Draw a barplot of the variable 'gender' in diabetes-dataset

 
# Draw a histogram of the variable 'age' in cardiac-dataset


# Draw a histogram of the variable 'bhr' (= "basal heart rate") in cardiac-dataset. Is there anything weird?

 
# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender.

 
# Draw a scatter-plot for the variables maximum heart rate ('maxhr') and systolic blood pressure ('sbp') in cardiac-data 

 
```
 
*** =solution
```{r}
# Draw a barplot of the variable 'gender' in diabetes-dataset
 
barplot(table(diabetes$gender))
 
# Draw a barplot of the variable 'age' in cardiac-dataset
hist(cardiac$age)
```
 
*** =sct
```{r}
test_student_typed("barplot(table(diabetes$gender))", not_typed_msg = "Make sure that you have added the table-command inside the barplot-command.")
test_student_typed("hist(cardiac$age)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("hist(cardiac$bhr)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("boxplot(diabetes$chol~diabetes$gender)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")
test_student_typed("plot(cardiac$maxhr,cardiac$sbp)", not_typed_msg = "Make sure that you have not made any spelling mistakes.")

success_msg("Awesome! You old plotting wizard!")
```
--- type:NormalExercise lang:r xp:100 skills:1 key:1c76838a8c

## Making plots more fancy
 
Plots are cooler with some colours in it. Title is a good way to tell people what the plot is about. One of R's best features is it wide range of colours, and easy wat of adjusting your plots to be exactly as you want.

*** =hint
Just add the title and colour options inside the plotting code, just like in the example.
 
*** =pre_exercise_code
```{r}
cardiac<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Cardiac.txt",header=T,row.names=1)
diabetes<-read.table("https://raw.githubusercontent.com/paulabergman/intro-to-biostatistics-with-r/master/Diabetes.txt",header=TRUE,row.names=1)
```
*** =instructions
- Draw a barplot of the variable 'gender' in diabetes-dataset. Add a title and colour to you plot. Don't be afraid to get creative!
- Draw a histogram of the variable 'age' in cardiac-dataset. Add a title and colour to you plot.
- Draw a boxplot for cholesterol ('chol') in diabetes- data by gender. Add a title and different colours for the two boxes. 
 
*** =sample_code
```{r}
# Draw a barplot of the variable 'gender' in cardiac-dataset. Add a title and colour to you plot.
 
barplot(table(cardiac$gender),main="Gender in cardiac-dataset",col="tomato")

# Draw a barplot of the variable 'gender' in diabetes-dataset. Add a title and colour to you plot.
 

# Draw a histogram of the variable 'age' in cardiac-dataset. Add a title and colour to you plot.


# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender. Add a title and different colours for the two boxes. Hint! use col=c("colour1","colour2")  
 
 
 
```
 
*** =solution
```{r}
# Draw a barplot of the variable 'gender' in diabetes-dataset
 
barplot(table(diabetes$gender),main="Title",col="red")
 
# Draw a barplot of the variable 'age' in cardiac-dataset
hist(cardiac$age,main="Title",col="red")

# Draw a boxplot for cholesterol ('chol') in diabetes- data by gender. Add a title and different colours for the two boxes. 
boxplot(diabetes$chol~diabetes$gender, col=c("red", "blue"))

```
 
*** =sct
```{r}
test_function("barplot", incorrect_msg = "Did you enter both title and colour options?")
test_function("hist",, incorrect_msg = "Did you enter both title and colour options?")
success_msg("Oh your plots look just fabulous!")
```

