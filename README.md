# Multiple-Regression
In this project, the investors can have an insight into the results. They will found out in which startup invest their money.
In the linear regression model, the following results can be found:
1. Which independent variable has the highest effect on the profit
2. Predict future profits for new startups based on the same information.
For the purposes of this project, the following preprocessing steps have been made to the dataset: 

---

##Importing the dataset

`dataset = read.csv('50_Startups.csv')`

##Encoding categorical data

```

dataset$State = factor(dataset$State,
                       levels = c('New York', 'California', 'Florida'),
                       labels = c(1, 2, 3))

```

##Splitting the dataset into the Training set and Test set

```
install.packages('caTools') 
library(caTools)
set.seed(123)  
split = sample.split(dataset$DependentVariable, SplitRatio = 0.8)
training_set = subset(dataset, split == TRUE)
test_set = subset(dataset, split == FALSE)

```
