---
title       : Chapter 2
description : Insert the chapter description here

--- type:NormalExercise lang:r xp:100 skills:1 key:0491de7d21
## ggplot2 Exercise


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
set.seed(1234)
library(dplyr)
n <- 1000
k <- 20
noise <- data.frame(y = rnorm(n), x = rnorm(n), z = rep(1:k))
library(ggplot2)
```

*** =sample_code
```{r}
# Create faceted scatterplot

```

*** =solution
```{r}
# Create faceted scatterplot
ggplot(data = noise, aes(x = x, y = y)) +
  geom_point() + 
  facet_wrap(~ z)
```

*** =sct
```{r}
test_ggplot(1)
```



--- type:NormalExercise lang:r xp:100 skills:1 key:25ff2f0853
## Modifying Variable in PEC


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
wine <- read.csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1048/datasets/wine.csv')
custom_seed(42)
wine <- wine[sample(nrow(wine), 100), ]
```

*** =sample_code
```{r}
x <- rnorm(100)
```

*** =solution
```{r}
wine_head <- head(wine)
```

*** =sct
```{r}
test_expression_output("wine_head")
test_error()
```
