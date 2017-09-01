---
title       : Measures of Central Tendency
description : Compute the 3 measures of central tendency on a meterological dataset
attachments :
  slides_link : 

--- type:NormalExercise lang:r xp:100 skills:1 key:ac394022a0
## Names of Variables
The dataset of NYC monthly temperatures, 'mydata', is avaialble in the workspace. Let's look at what variables are avaialble. 

*** =instructions
- List the variables in the 'mydata' data frame.

*** =hint
- Try using the function 'names()'

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
# load in monthly NYC temperatures 
mydata <- read.csv("https://www.e-education.psu.edu/meteo815/sites/www.e-education.psu.edu.meteo815/files/Rfiles/monthly_NYC_temperatures.csv")

```

*** =sample_code
```{r}
# mydata is available in your workspace

# List the variable names for 'mydata'

```

*** =solution
```{r}
# mydata is available in your workspace

# List the variable names for 'mydata'
names(mydata)

```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("names", args = "x",
              not_called_msg = "You didn't call `names()`!",
              incorrect_msg = "You didn't call `names(object = ...)` with the correct argument, `mydata`.")

success_msg("Good work!")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:68f32aad96
## Convert Date
For this analysis, we are going to look at the December monthly temperatures instead of the November monthly temperatures. However, before we can begin we must extract out only the december temperatures. Let's get started. 

*** =instructions
We first need to convert the date string to a real date. Using the variable 'DATE' from the dataframe 'mydata', set mydata$DATE to a real date instead of a string.
*** =hint
You need to use the function as.Date() and paste together the mydata$DATE string appropriately, that is Year, Month, Day. 
*** =pre_exercise_code
```{r}
# load in monthly NYC temperatures 
mydata <- read.csv("https://www.e-education.psu.edu/meteo815/sites/www.e-education.psu.edu.meteo815/files/Rfiles/monthly_NYC_temperatures.csv")
```

*** =sample_code
```{r}
# mydata is available in your workspace

# Convert string date to real date
mydata$DATE <- 
```

*** =solution
```{r}
mydata$DATE <- as.Date(paste0(substr(mydata$DATE,1,4),"-",
                     substr(mydata$DATE,5,6),"-",
                     substr(mydata$DATE,7,8)))
```

*** =sct
```{r}
test_function("as.Date", args = "x",
              not_called_msg = "You didn't call `as.Date`!",
              incorrect_msg = "You didn't call `as.Date` with the correct arguments, pasting the date string together")

success_msg("Good work!")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:a2fd15067b
## December Temperatures
We only want to examine the December temperatures since we already looked at the November ones. 

*** =instructions
Now, extract out only the december mean monthly temperatures (mydata$MNTM) from 1980-2009 in degrees C. You will need to divide by 10 to obtain the correct units. Set the temperatures to the variable 'dec_temp'.  
*** =hint
Make sure you extract out for only months equal to 12 and years less than 2010. 
*** =pre_exercise_code
```{r}
# load in monthly NYC temperatures 
mydata <- read.csv("https://www.e-education.psu.edu/meteo815/sites/www.e-education.psu.edu.meteo815/files/Rfiles/monthly_NYC_temperatures.csv")

# change Date from string to real date
mydata$DATE <- as.Date(paste0(substr(mydata$DATE,1,4),"-",
                     substr(mydata$DATE,5,6),"-",
                     substr(mydata$DATE,7,8)))

```

*** =sample_code
```{r}
# mydata is available in your workspace

# Extract out December temperatures from 1980-2009
dec_temp <- 

```

*** =solution
```{r}
dec_temp<-mydata$MNTM[which(format(mydata$DATE,"%m")==12 & format(mydata$DATE,"%Y")<2010)]/10
```

*** =sct
```{r}
test_object("dec_temp",
                     incorrect_msg = "Make sure you are subsetting for the months of December from 1980-2010")
success_msg("Great job!")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:a71330a87e
## Compute Mean
Fantastic! Now we are all set up to compute the 3 measures of centeral tendency. First up is the mean. As a reminder, the mean represents the average value.

*** =instructions
Compute the 30-year mean (1980-2009) of the December temperatures and set it to the variable decTemp_mean.
*** =hint
Try using the function mean() and make sure you account for missing values. 
*** =pre_exercise_code
```{r}
# load in monthly NYC temperatures 
mydata <- read.csv("https://www.e-education.psu.edu/meteo815/sites/www.e-education.psu.edu.meteo815/files/Rfiles/monthly_NYC_temperatures.csv")

# change Date from string to real date
mydata$DATE <- as.Date(paste0(substr(mydata$DATE,1,4),"-",
                     substr(mydata$DATE,5,6),"-",
                     substr(mydata$DATE,7,8)))

# Extract out December temperatures from 1980-2009
dec_temp <- mydata$MNTM[which(format(mydata$DATE,"%m")==12 & format(mydata$DATE,"%Y")<2010)]/10
```

*** =sample_code
```{r}
# dec_temp is avaialble in your workspace

# Compute the 30-year Mean
decTemp_mean <- 
```

*** =solution
```{r}
decTemp_mean <- mean(dec_temp,na.rm=TRUE)
```

*** =sct
```{r}
test_object("decTemp_mean",
                     incorrect_msg = "Make sure you are use the function mean() and account for missing values")
success_msg("Better than Average job!")
```

--- type:NormalExercise lang:r xp:100 skills:1 key:b464a2f9ec
## Compute Median
Now, let's compute the median. The median represents the middle value of the dataset.

*** =instructions
Compute the median for the december temperatures and set the value to decTemp_median. 
*** =hint
Try using the function median() and again, make sure you account for missing values. 
*** =pre_exercise_code
```{r}
# load in monthly NYC temperatures 
mydata <- read.csv("https://www.e-education.psu.edu/meteo815/sites/www.e-education.psu.edu.meteo815/files/Rfiles/monthly_NYC_temperatures.csv")

# change Date from string to real date
mydata$DATE <- as.Date(paste0(substr(mydata$DATE,1,4),"-",
                     substr(mydata$DATE,5,6),"-",
                     substr(mydata$DATE,7,8)))

# Extract out December temperatures from 1980-2009
dec_temp <- mydata$MNTM[which(format(mydata$DATE,"%m")==12 & format(mydata$DATE,"%Y")<2010)]/10
```

*** =sample_code
```{r}
# dec_temp is avaialble in your workspace

# Compute the 30-year Median
decTemp_median <- 
```

*** =solution
```{r}
decTemp_median <- median(dec_temp,na.rm=TRUE)
```

*** =sct
```{r}
test_object("decTemp_median",
                     incorrect_msg = "Make sure you are use the function median() and account for missing values")
success_msg("Awesome Job!")
```
--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:e0883902aa
## R packages for Mode

The final measure of central tendency is the mode which reprsents the most frequent value. What package should we use to compute the mode?

*** =instructions
- Modest
- Stats
- Psych

*** =hint
Look for the one that has mode in the name. 

*** =pre_exercise_code
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct. Try Again."
msg_success <- "Exactly! We use the package Modest. For more information check out the R Documentation [https://cran.r-project.org/web/packages/modest/modest.pdf]."
test_mc(correct = 1, feedback_msgs = c(msg_success, msg_bad, msg_bad))
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1bc151f0bd
## Compute Mode
Now compute the final measure of central tendency, the mode. What function from the package modest would you use to compute mode?

*** =instructions
- mode
- mfv
- mtw
*** =hint
Check out the documentation page for more information. [https://cran.r-project.org/web/packages/modest/modest.pdf]
*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg_bad <- "That is not correct. Try Again."
msg_success <- "Exactly! We use the mfv. Specifically we would write:
decTemp_median <- mfv(dec_temp)."
test_mc(correct = 1, feedback_msgs = c(msg_bad,msg_success,msg_bad))
```
