---
title       : Chapter 1
description : This is the first chapter.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

---
## A really bad movie

```yaml
type: MultipleChoiceExercise
lang: r
xp: 50
skills: 1
key: cb75e904ce
```

Have a look at the plot that showed up in the viewer to the right. Which type of movie has the worst rating assigned to it?

`@instructions`
- Adventure
- Action
- Animation
- Comedy

`@hint`
Have a look at the plot. Which color does the point with the lowest rating have?

`@pre_exercise_code`
```{r}
# The pre exercise code runs code to initialize the user's workspace.
# You can use it to load packages, initialize datasets and draw a plot in the viewer

movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

library(ggplot2)

ggplot(movies, aes(x = runtime, y = rating, col = genre)) + geom_point()
```

`@sct`
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```

---
## More movies

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: e013750490
```

In the previous exercise, you saw a dataset about movies. In this exercise, we'll have a look at yet another dataset about movies!

A dataset with a selection of movies, `movie_selection`, is available in the workspace.

`@instructions`
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

`@hint`
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`.

`@pre_exercise_code`
```{r}
# You can also prepare your dataset in a specific way in the pre exercise code
load(url("https://s3.amazonaws.com/assets.datacamp.com/course/teach/movies.RData"))
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"), c("Genre", "Rating", "Run")]

# Clean up the environment
rm(Movies)
```

`@sample_code`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

`@solution`
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

`@sct`
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



---
## Bullet Exercise

```yaml
type: BulletExercise
key: 530e23fcbb
lang: r
xp: 100
```


`@pre_exercise_code`
```{r}

```


***

### Sub Exercise 1

```yaml
type: NormalExercise
xp: 100
key: 636ae50119
```

`@instructions`

This is the first sub-exercise 

`@sample_code`

```{r}
# Sample Code for Exercise 1
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Exercise 2

```yaml
type: NormalExercise
xp: 100
key: c721038005
```

`@instructions`

This is the second sub-exercise.


`@sample_code`

```{r}
# Sample Code for Exercise 2
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

---
## Tab Exercise

```yaml
type: TabExercise
lang: r
xp: 100
key: 43b65f47bb
```

This is a Tab Exercise


`@pre_exercise_code`
```{r}

```


***

### Sub Exercise 1

```yaml
type: NormalExercise
xp: 100
key: f1c09bceac
```

`@instructions`

This is the first sub-exercise 

`@sample_code`

```{r}
# Sample Code for Exercise 1
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Exercise 2

```yaml
type: NormalExercise
xp: 100
key: a43e6c8fe1
```

`@instructions`

This is the second sub-exercise.


`@sample_code`

```{r}
# Sample Code for Exercise 2
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```



---
## Base Graphics vs. Ggplot2 (Part 1)

```yaml
type: TabExercise
key: a39aef6095
lang: r
xp: 100
```

To better appreciate `ggplot2` and understand how it works differently from base package, let us create a scatterplot of `hp` (horsepower) vs `drat` (rear axle ratio), colored by `cyl` (number of cylinders).

```{r}
# Base Graphics
plot(mtcars$hp, mtcars$drat, col = as.factor(mtcars$cyl))

# Ggplot2
ggplot(mtcars, aes(x = hp, y = drat, col = as.factor(cyl))) +
  geom_point()
```

Note that in both cases, we convert `cyl` to a factor as it represents discrete categories.


`@pre_exercise_code`
```{r}

```


***

### Sub Heading

```yaml
type: NormalExercise
xp: 100
key: fa5be44690
```

`@instructions`

Use base graphics to create a scatterplot of `mpg` vs `wt` colored by `gear` 


`@sample_code`
```{r}
# Create a scatterplot of `mpg` vs `wt` colored by `gear`
# Use base graphics
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
key: 60a1c29d4f
```

`@instructions`

Use ggplot2 to create a scatterplot of `mpg` vs `wt` colored by `gear` 


`@sample_code`
```{r}
# Create a scatterplot of `mpg` vs `wt` colored by `gear` 
# Use ggplot2
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```



---
## Select - GroupBy - Summarize

```yaml
type: TabExercise
key: ccbb1ef0c8
lang: r
xp: 100
```


`@pre_exercise_code`
```{r}
library(dplyr)
```


***

### Select

```yaml
type: NormalExercise
xp: 100
```

`@instructions`

Create a dataframe `mtcars_d` from `mtcars` by selecting columns `mpg` to `cyl`.

`@sample_code`
```{r}
mtcars_d <- ___(mtcars, ___:___)
```


`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### GroupBy

```yaml
type: NormalExercise
xp: 100
```

`@instructions`

Group the dataframe `mtcars_d` by `cyl` and assign it to `mtcars_dg`

`@sample_code`

```{r}
mtcars_d <- select(mtcars, mpg:cyl)
mtcars_dg <- groupby(mtcars_d, cyl)
```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```



***

### Summarize

```yaml
type: NormalExercise
key: ad17cf6354
```


`@instructions`

Compute the average mileage for each group, and save dataframe as `mtcars_dgs` 

`@hint`


`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@sct`
```{r}

```



---
## How many visitors could your site get (3)?

```yaml
type: TabExercise
key: 1f2f33d8f5
lang: r
xp: 100
```

In the last exercise you updated the probability distribution over the underlying proportions of clicks (proportion\_clicks) using new data. Now we want to use this updated proportion\_clicks to predict how many visitors we would get if we ran the ad campaign again.

The result from the last exercise is still in the data frame posterior, but if you look at `posterior$n_visits` you'll see it's just 13 repeated over and over again. This makes sense as posterior represents what the model knew about the outcome of the last ad campaign after having seen the data.


`@pre_exercise_code`
```{r}
set.seed(123)
n_samples <- 100000
n_ads_shown <- 100
proportion_clicks <- runif(n_samples, min = 0.0, max = 0.2)
n_visitors <- rbinom(n = n_samples, size = n_ads_shown, prob = proportion_clicks)
temp_prior <- data.frame(proportion_clicks, n_visitors)
posterior <- temp_prior[temp_prior$n_visitors == 13, ]
rm(proportion_clicks, n_visitors, temp_prior)
```

***

### Sub Heading

```yaml
type: NormalExercise
xp: 100
```

`@instructions`

Assign `posterior` to a new variable called `prior` which will represent the uncertainty regarding the new ad campaign you haven't run yet.

`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
```


`@instructions`

Take a look at the first rows in prior using the `head` function.

`@sample_code`
```{r}
prior <- posterior

```

`@solution`
```{r}

```

`@hint`

`@sct`
```{r}

```



---

## Use lapply with your own Function

```yaml
type: BulletExercise
key: a5a60079e2
lang: r
xp: 100
```

In the previous exercise you used `lapply()` to convert the information about your favorite pioneering statisticians to a list of vectors composed of two character strings.


```{r}
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")
split <- strsplit(pioneers, split = ":")
split_low <- lapply(split, tolower)
```

Let us now write some custom functions and `lapply` them to select the names and the birth years separately.

`@pre_exercise_code`

```{r}
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")
split <- strsplit(pioneers, split = ":")
split_low <- lapply(split, tolower)
```


***
### Select name

`@instructions`

Write a function `select_first()` to extract the **first** element of a vector and apply it over the elements of `split_low`.

`@sample_code`

```{r}
# Write function select_first()
select_first <- function(x) { x[1] }

# Apply select_first() over split_low: names
names <- ___(split_low, ___)
```

`@hint`

`@solution`
```{r}
# Write function select_first()
select_first <- function(x) { x[1] }

# Apply select_first() over split_low: names
names <- lapply(split_low, select_first)
```

`@sct`
```{r}

```

***

### Sub Heading 2

```yaml
type: NormalExercise
xp: 100
```

`@instructions`

Write a function `select_second()` to extract the **second** element of a vector and apply it over the elements of `names`.

`@sample_code`

```{r}
# Write function select_second()
select_second <- 

# Apply select_second() over split_low: years
years <- 
```

`@hint`

`@solution`
```{r}

```

`@sct`
```{r}

```
