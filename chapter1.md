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

test_function("names", args = "mydata",
              not_called_msg = "You didn't call `names()`!",
              incorrect_msg = "You didn't call `names(mydata)` with the correct argument, `mydata`.")

success_msg("Good work!")
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

