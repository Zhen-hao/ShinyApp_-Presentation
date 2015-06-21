---
title       : Predicting Miles per gallon (MPG) by horsepower and weight
subtitle    : A pitch for the shiny application 
author      : Zhenhao Li

framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
url:
  lib: ../../librariesNew
  assets: ../../assets
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}

---

## Two use cases
* Case 1
  * Bob knows that his car is of 200 horsepower and weighs 3000 lb
  * Bob does not know his the miles per gallon (MPG) of his car
  * Bob can use this app to get a predicted value of the MPG of his car

* Case 2
  * Alice wants to buy a new car but the dealer only knows the car's weight and horsepower
  * Alice needs to find out the MPG of that car before making her decision
  * Alice can use this app to get a predicted value of the MPG of her wanted car


---

## Prediction method

*  The app use a linear regression model to make prediction which has the form 
$$
PMG = \beta_0 + \beta_1 \text{Horsepower} + \beta_2 \text{Weight} + \epsilon
$$


* The model is built from the data set mtcars and the details of the model is shown below

```r
fit <- lm(mpg ~  hp  + wt, data = mtcars)
summary(fit)$coefficient
```

```
               Estimate Std. Error   t value     Pr(>|t|)
(Intercept) 37.22727012 1.59878754 23.284689 2.565459e-20
hp          -0.03177295 0.00902971 -3.518712 1.451229e-03
wt          -3.87783074 0.63273349 -6.128695 1.119647e-06
```

---

## App manule

* Use the slider Gross Horsepower to select the horsepower value 
* Use the slider Weight to select the weight value
* The predicted value of MPG will be given as a number
* The predicted value will be shown as aline in the Histogram of MPG values in mtcars if it is in the range


---

## Example Bob's car
Suppose Bob uses the app and sets the horsepower value to 200 and the weight value to 3000 lb, he would get a predicted value shown below

```r
data(mtcars)
newData <-  data.frame(hp=200, wt=3000/1000)
predict(fit, newData )
```

```
       1 
19.23919 
```


