---
title       : Measures of Central Tendency
description : Compute the 3 measures of central tendency on a meterological dataset
attachments :
  slides_link : 



--- type:NormalExercise lang:r xp:100 skills:1 key:9887466a86
## Welcome Message
Welecome to the Meteo 815 example on Measures of Central Tendency! In this example, we will continue off of the example online and apply the 3 measures of central tendency to temperature data from New York City. 

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

--- type:NormalExercise lang:r xp:100 skills:1 key:ac394022a0
## Names of Variables

Welecome to the Meteo 815 example on Measures of Central Tendency! In this example, we will continue off of the example online and apply the 3 measures of central tendency to temperature data from New York City. 


A dataset with a selection of movies, `movie_selection`, is available in the workspace.

*** =instructions
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

*** =pre_exercise_code
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

*** =sample_code
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()

success_msg("Good work!")
```
