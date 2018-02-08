---
title       : Chapter 2
description : Insert the chapter description here

--- type:NormalExercise lang:r xp:100 skills:1 key:0491de7d21
## <<<New Exercise>>>


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
library(dplyr)
library(ggplot2)
set.seed(1234)
n <- 1000
k <- 20
noise <- data.frame(y = rnorm(n), x = rnorm(n), z = rep(1:k))
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
