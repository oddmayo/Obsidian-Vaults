# Linear regression

Linear regression is an approach of #supervised learning both simple and useful.

True regression functions are nevel linear [[SL2 - Statistical Learning]]

## Simple linear regression using a single predictor X

![[Pasted image 20220831170844.png]]

![[Pasted image 20220831171317.png]]

## Estimation of the parameters by least squares
$e_i  = y_i - \hat{y}_i$ represents the $ith$ *residual* 
Residual sum of squares RSS: $e^2_1+e^2_2+...+e^2_n$ 

## Assessing the accuracy of the coeficient estimates
The #standard_error of an estimator reflects how it varies under repeated sampling. These can be used to compute *confidence intervals*.

## Hypothesis testing

![[Pasted image 20220831192742.png]]

Compute the probability of observing any value equal to $|t|$ or larger. This is called the #p-value

We can also compute the #Residual_Standard_Error and the #R_Squared or the fraction of variance explained

## Multiple Linear Regression
![[Pasted image 20220831194530.png]]

Where $B_j$ is the *average effect on $Y$ of a one unit increase in $X_j$*, holding all other predictors fixed.

## Interpreting regression coefficients
The ideal escenario occurs when the #predictors are uncorrelated. When they are correlated the **variance tends to increase** and interpretations become hazardous.

Therefore **claims of causality should be avoided**.

## Is at least one predictor useful?
For that question we use the *F-statistic*

## Deciding on the important variables
- Forward selection: begin with the null model
- Backward selection: begin with all variables

## Other considerations
**Qualitative predictors**: they take #discrete values
These are called *categorical* or *factor* variables

For these we create a #dummy variable:
![[Pasted image 20220831200040.png]]

Always be one fewer dummy variable than the number of levels (if more than two), the level with no dummy variable is the *baseline*

## Extensions
If we remove the additive assumption we have: *interactions* and *nonlinearity*:

**Interactions**: interaction effect
![[Pasted image 20220831200353.png]]

To check if interactions are important we comparte the model with and without interactions

**Hierarchy**: if we include an interaction effect in a model, we should also include the main effects, even if its associated #p-value is not significant (because interactions are hard to interpret without main effects). 

**Nonlinearity**
![[Pasted image 20220831202816.png]]
![[Pasted image 20220831202828.png]]
