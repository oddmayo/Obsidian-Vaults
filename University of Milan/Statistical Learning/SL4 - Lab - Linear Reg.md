# Lab 1 - Summary
**Dataset**: 10 variables of housing for 105 italian provinces

## Describe rent_pr variable
Average house rent prices (euro per squared meter)

```
library(readxl)
Dataset <- read_excel("rents.xlsx")
```

```
ggdensity(Dataset, x = "rent_pr", fill = "lightgray", title = "rent_pr") +
  stat_overlay_normal_density(color = "red", linetype = "dashed")
```

![[Pasted image 20220901201952.png]]

**Not normally distributed**, we reject the null hypothesis of the shapiro wilk test

**But** the logarithm of the variable improves:

```
Dataset$logrent=log(Dataset$rent_pr)
```

```
ggdensity(Dataset, x = "logrent", fill = "lightgray", title = "logrent") +
  stat_overlay_normal_density(color = "red", linetype = "dashed")
```

![[Pasted image 20220901202250.png]]

## Compute correlation matrix between the variables rent_pr, sell_pr, transport, education, income

```
library("Hmisc")
rcorr(as.matrix(mydata))
```
```
##           rent_pr inhab agepop transport density education income
## rent_pr      1.00  0.18   0.27     -0.10    0.17      0.02   0.43
## inhab        0.18  1.00  -0.30     -0.08    0.64      0.50   0.20
## agepop       0.27 -0.30   1.00      0.34   -0.18     -0.03   0.55
## transport   -0.10 -0.08   0.34      1.00   -0.11     -0.08   0.17
## density      0.17  0.64  -0.18     -0.11    1.00      0.56   0.19
## education    0.02  0.50  -0.03     -0.08    0.56      1.00   0.26
## income       0.43  0.20   0.55      0.17    0.19      0.26   1.00
## 
## n= 104 
## 
## 
## P
##           rent_pr inhab  agepop transport density education income
## rent_pr           0.0662 0.0051 0.3364    0.0931  0.8046    0.0000
## inhab     0.0662         0.0017 0.4466    0.0000  0.0000    0.0381
## agepop    0.0051  0.0017        0.0004    0.0703  0.7554    0.0000
## transport 0.3364  0.4466 0.0004           0.2829  0.3951    0.0819
## density   0.0931  0.0000 0.0703 0.2829            0.0000    0.0521
## education 0.8046  0.0000 0.7554 0.3951    0.0000            0.0087
## income    0.0000  0.0381 0.0000 0.0819    0.0521  0.0087
```

The variable most correlate with _rent_pr_ is _income_. Also inhab, agepop, density have a significant #correlation at 10%.

## Does rent_pr differ significantly fro regional capital?

First gotta assign correct label categories of the #factor variable capital
```
library(gplots)
library(plyr)
Dataset$capital <- factor(Dataset$capital,
levels = c(1,0),
labels = c("yes", "no"))
boxplot(rent_pr~capital, data=Dataset)
```

![[Pasted image 20220901202910.png]]

```
t.test(rent_pr~capital, alternative='two.sided', conf.level=.95, var.equal=FALSE, data=Dataset)
```
```
## 
##  Welch Two Sample t-test
## 
## data:  rent_pr by capital
## t = 0.88807, df = 28.47, p-value = 0.3819
## alternative hypothesis: true difference in means is not equal to 0
## 95 percent confidence interval:
##  -0.8711318  2.2063223
## sample estimates:
## mean in group yes  mean in group no 
##          8.432000          7.764405
```

The _rent_pr_ doesn’t differ for _capital_: the t statistics is 0.88, lower than 2, the confidence interval on the difference in means includes 0 and the #p-value is larger than 0.05.

## Does rent_pr differ significantly for geographical area?

Assign correct label to categories of the factor variable area
```
Dataset$area <- factor(Dataset$area,
levels = c(1,2,3,4),
labels = c("centre", "isles", "north","south"))
```

_Boxplot_ -library(car) - insted of _boxplot_ allow to print the identify the outlier with the row names. We assign the _provices_ to the row names
```
library(car)
rownames(Dataset)<-Dataset$province
dd=Dataset[,-c(1,2,12)]
rownames(dd)<-Dataset$province
Boxplot(rent_pr~area, id=TRUE, data=Dataset)
```
![[Pasted image 20220901203249.png]]
```
summary(aov(rent_pr ~ area, data=Dataset))
```
```
##              Df Sum Sq Mean Sq F value   Pr(>F)    
## area          3  150.1   50.04   6.479 0.000473 ***
## Residuals   100  772.3    7.72                     
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

The _rent_pr_ differs for _area_: the F-statistic is 6,47, larget than the critical value, the p-value is lower than 0.05. Looking to the conffidence iterval plot, seems that that only south differs form north and center and north from south.

## Does the rental price per square meter depend linearlt on per capita income?
```
plot(rent_pr~income, col="darkgreen", pch=19, cex=1,data=Dataset)
mod<-lm(rent_pr~income, data=Dataset)
abline(mod, col="red", lwd=3)
```
![[Pasted image 20220901203521.png]]

```
summary(mod)
```
```
## 
## Call:
## lm(formula = rent_pr ~ income, data = Dataset)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -4.4243 -1.6546 -0.6557  0.6826 12.8601 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 1.7204929  1.3233530   1.300    0.196    
## income      0.0003738  0.0000785   4.762 6.36e-06 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.72 on 102 degrees of freedom
## Multiple R-squared:  0.1819, Adjusted R-squared:  0.1739 
## F-statistic: 22.68 on 1 and 102 DF,  p-value: 6.359e-06
```

The per capita _income_ of a province affect positively the _rent_pr_. Knowing the _income_ is possible t exaplin the 18% of the variance of _rent_pr_. An increasing of 1 of _income_ prodice and increasigf or 0.00037 of the average house rent prices (euro per squared meter). Make more sense to comment of 100 or 1000 of increasing of income, that produces 0.037 and 0.37 increase respecively.

## Does the model improve if the logarithm is used?

We try with the 3 models:
-   linear-log
-   log-linear
-   log-log

Rember that the interpretation of the slope parameter changes:
-   Δ 1 % in X, Δβ1 linear in Y
-   Δ 1 linear in X, Δβ1 % in Y
-   Δ 1 % in X in X, Δβ1 % in Y

log-linear gives the best results
```
mod2<-lm(log(rent_pr)~income, data=Dataset)
```

## Estimate a linear model to predict the rental price per square meter using all the relevant variables

Check theory at [[SL3 - Linear Regression]]

**full model** We includes all the possible covariates and factors in the model. We do not consider the _sell_pr_ (it is, as well ad _rent_pr_, an outcome variable). R creates automatically dummies variable for factor

```
full.model <- lm(log(rent_pr) ~., data = dd)
summary(full.model)
```

```
## 
## Call:
## lm(formula = log(rent_pr) ~ ., data = dd)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.66036 -0.16654 -0.03865  0.16595  0.85307 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)   
## (Intercept)  4.111e-01  9.296e-01   0.442  0.65939   
## inhab        8.479e-08  6.908e-08   1.227  0.22274   
## agepop       2.071e-02  2.178e-02   0.951  0.34407   
## transport   -9.914e-04  5.823e-04  -1.703  0.09198 . 
## education   -1.321e-03  7.689e-04  -1.718  0.08921 . 
## income       5.325e-05  1.680e-05   3.170  0.00206 **
## density      1.454e-04  9.828e-05   1.480  0.14227   
## capitalno    7.843e-02  8.600e-02   0.912  0.36415   
## areaisles    4.034e-02  1.196e-01   0.337  0.73657   
## areanorth   -1.913e-01  7.849e-02  -2.437  0.01670 * 
## areasouth   -1.679e-01  1.067e-01  -1.574  0.11900   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.2676 on 93 degrees of freedom
## Multiple R-squared:  0.3898, Adjusted R-squared:  0.3242 
## F-statistic: 5.942 on 10 and 93 DF,  p-value: 6.693e-07
```

**Stepwise regression model** We apply the steptwise approach, other more advanced methods to select the subset of features will be presented during the course (best subset selection shrinkage methods).

```
library(MASS)
step.model <- stepAIC(full.model, direction = "both", 
                      trace = FALSE, k=3)
summary(step.model)
```

```
## 
## Call:
## lm(formula = log(rent_pr) ~ income + density + area, data = dd)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.52982 -0.17085 -0.04161  0.13941  0.95951 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  1.327e+00  2.351e-01   5.646  1.6e-07 ***
## income       4.759e-05  1.345e-05   3.539 0.000616 ***
## density      1.220e-04  7.158e-05   1.705 0.091421 .  
## areaisles    1.735e-03  1.124e-01   0.015 0.987720    
## areanorth   -1.923e-01  7.468e-02  -2.575 0.011521 *  
## areasouth   -2.343e-01  9.771e-02  -2.398 0.018357 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.2704 on 98 degrees of freedom
## Multiple R-squared:  0.3438, Adjusted R-squared:  0.3103 
## F-statistic: 10.27 on 5 and 98 DF,  p-value: 6.212e-08
```

## Check diagnostics

**Collinarity**
```
vif(step.model) # variance inflation factors 
```
```
##             GVIF Df GVIF^(1/(2*Df))
## income  2.970173  1        1.723419
## density 1.059846  1        1.029488
## area    2.931425  3        1.196318
```

```
shapiro.test(step.model$residuals)
```
```
## 
##  Shapiro-Wilk normality test
## 
## data:  step.model$residuals
## W = 0.94828, p-value = 0.000483
```

```
dd$fit<-step.model$fitted.values
dd$res<-step.model$residuals
ggdensity(dd, x = "res", fill = "lightgray", title = "Residuals") +
  stat_overlay_normal_density(color = "red", linetype = "dashed")
```

![[Pasted image 20220901205031.png]]


#Heteroskedasticity occurs when the variance for all observations in a data set are not the same. Conversely, when the variance for all observations are equal, we call that homoskedasticity. Why should we care about heteroskedasticity? Because it is a violation of the ordinary least square assumption that var(yi)=var(ei)=σ2var(yi)=var(ei)=σ2. In the presence of heteroskedasticity, there are two main consequences on the least squares estimators:

-   The least squares estimator is still a linear and unbiased estimator, but it is no longer best. That is, there is another estimator with a smaller variance.
-   The standard errors computed for the least squares estimators are incorrect. This can affect confidence intervals and hypothesis testing that use those standard errors, which could lead to misleading conclusions.

_Note_: Robust regression does not address issues of heterogeneity of variance.

```
# Evaluate homoscedasticity
# non-constant error variance test
ncvTest(step.model)
```
```
## Non-constant Variance Score Test 
## Variance formula: ~ fitted.values 
## Chisquare = 0.7047359, Df = 1, p = 0.4012
```

When we reject the null hypothesis in the previous tests, so we conclude that heteroskedasticity is present, we can use the _sandwich_ package that implement robust standard erros. In this case, p-value are larger that 0.05, so the homoskedasticity hipothesis is accepted

```
library(lmtest)
library(sandwich)
bptest(step.model)
```
```
## 
##  studentized Breusch-Pagan test
## 
## data:  step.model
## BP = 6.2853, df = 5, p-value = 0.2794
```

```
coeftest(step.model, vcov = vcovHC(step.model, "HC1"))  
```
```
## 
## t test of coefficients:
## 
##                Estimate  Std. Error t value  Pr(>|t|)    
## (Intercept)  1.3272e+00  1.7806e-01  7.4535 3.646e-11 ***
## income       4.7594e-05  1.0084e-05  4.7198 7.856e-06 ***
## density      1.2201e-04  3.6664e-05  3.3279  0.001233 ** 
## areaisles    1.7346e-03  1.2693e-01  0.0137  0.989124    
## areanorth   -1.9230e-01  8.0855e-02 -2.3784  0.019328 *  
## areasouth   -2.3434e-01  9.1989e-02 -2.5475  0.012406 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```
