# Multiple-Regression
In this project, the investors can have an insight into the results. They will found out in which startup invest their money.
In the linear regression model, the following results can be found:
1. Which independent variable has the highest effect on the profit
2. Predict future profits for new startups based on the same information.
For the purposes of this project, the following preprocessing steps have been made to the dataset: 

---

**Importing the dataset**

`dataset = read.csv('50_Startups.csv')`

**Encoding categorical data**

```

dataset$State = factor(dataset$State,
                       levels = c('New York', 'California', 'Florida'),
                       labels = c(1, 2, 3))
```

**Splitting the dataset into the Training set and Test set**

```
install.packages('caTools') 
library(caTools)
set.seed(123)  
split = sample.split(dataset$DependentVariable, SplitRatio = 0.8)
training_set = subset(dataset, split == TRUE)
test_set = subset(dataset, split == FALSE)
```

**Fitting Multiple Linear Regression to the Training set**

```
regressor = lm(formula = Profit ~ .,
               data = training_set)              
 ```              

```
summary(regressor)
```
```
Call:
lm(formula = Profit ~ ., data = training_set)

Residuals:
   Min     1Q Median     3Q    Max 
-33128  -4865      5   6098  18065 

Coefficients:
                  Estimate Std. Error t value Pr(>|t|)    
(Intercept)      4.965e+04  7.637e+03   6.501 1.94e-07 ***
R.D.Spend        7.986e-01  5.604e-02  14.251 6.70e-16 ***
Administration  -2.942e-02  5.828e-02  -0.505    0.617    
Marketing.Spend  3.268e-02  2.127e-02   1.537    0.134    
State2           1.213e+02  3.751e+03   0.032    0.974    
State3           2.376e+02  4.127e+03   0.058    0.954    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 9908 on 34 degrees of freedom
Multiple R-squared:  0.9499,	Adjusted R-squared:  0.9425 
F-statistic:   129 on 5 and 34 DF,  p-value: < 2.2e-16
```
**Predicting the Test set results**

```
y_pred = predict(regressor, newdata = test_set)
```
