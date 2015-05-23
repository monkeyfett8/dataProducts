---
title       : MT Cars Predictive Model
subtitle    : Predicting MPG from regression
author      : monkeyfett8
job         : Coursera Data Products Class
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Need for Fuel Economy Prediction

Fuel economy is a very important factor in choosing a car.  FOr some it is the most important factor.  This tool is to provide a way for customers to choose what characteristics they want in a car before purchasing. 

Source data is from the Motor Trend magazine dataset from 1974.  This data set has 32 cars and their characteristics.


```r
dat <- mtcars
```

--- .class #id 

## Tool Prediction Model

For this tool a model is made using a linear regression in R.  First the most imporant factors must be chosen.  An example of the data set is shown below.


```r
dat[1,]
```

```
##           mpg cyl disp  hp drat   wt  qsec vs am gear carb
## Mazda RX4  21   6  160 110  3.9 2.62 16.46  0  1    4    4
```

Tyoically in cars fuel economy is driven by three factors, the number of cylinders in the engine, the engine power output, and the total vehicle weight.  From this a regression is made.


```r
mtModel <- lm(mpg ~ hp + wt + cyl, data=dat)
```

---

## Model Check

Now the model can be checked to see if it appropreate and represents the data well.


```r
summary(mtModel)$coefficients
```

```
##               Estimate Std. Error   t value     Pr(>|t|)
## (Intercept) 38.7517874 1.78686403 21.687038 4.799399e-19
## hp          -0.0180381 0.01187625 -1.518838 1.400152e-01
## wt          -3.1669731 0.74057588 -4.276365 1.994765e-04
## cyl         -0.9416168 0.55091638 -1.709183 9.848010e-02
```

While the model is not very good of a fit by the variables it is enough to provide customers with some idea of how the main factors affect the performance of their vehicles.


---

## Using the Model

The model is [available online here](http://monkeyfett8.shinyapps.io/project/) and looks like the image below.

!["Tool Preview"](assets/img/toolShot.png)

---

## Using model (cont.)

On the left side of the tool are the 3 input values, cylinders, power, and weight.  These can be adjusted on the fly.  On the right is an output of the registered input values and the predictionoutput from the Fuel Economy model.  This prediction will update in real time with the inputs.

This model will help customers understand how engine size and power, and car weight can affect their fuel economy.  While this data is relatively old it still shows trends that can be applicable to current shopping.
