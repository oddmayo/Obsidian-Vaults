# Statistical Learning

## What is statistical learning?

![[Pasted image 20220831151516.png]]

## Notation
Here sales is a #response or #target variable: $Y$
TV is a #feature or #input or #predictors:  $X_1$

Input vector: $X=\begin{pmatrix} X_1 & X_2 & X_3 \end{pmatrix}$

Finally the model $Y = f(X) + e$, where $e$ is the error and other discrepancies

## What is $f$ good for?

- With a good $f$ we can make predictions of $Y$ at new points $X = x$.
- Understand if the predictors are important in explaning the target variable
- Depending on the complexity of $f$, we may be able to understand how each feature impacts the target varible.

Is there an ideal $f$?
	Yes it is called the **regression function** $f(x)=E(Y|X=x)$

## The regression function
Is the **ideal** or **optimal** #predictor of $Y$ with regard to the mean-squared error (minimizing it)

$e=Y-f(x)$ is the **irreducible error** even knowing $f$

![[Pasted image 20220831154202.png]]

## Parametric and structured models
- A linear model is specified in terms of $p+1$ parameters
- These #parameters are estimated by fitting the model to the #training data
- A linear model is a good approximation to the true $f$

![[Pasted image 20220831155004.png]]

When no erros are made in the fitted model this is known as #overfitting

## Trade offs
- Prediction #accuracy VS #interpretability
- Good fit VS over-fit VS under-fit
- Parsimony VS black box

![[Pasted image 20220831155415.png]]

## Assessing Model Accuracy

Mean Squared Error for both #training and #test data

![[Pasted image 20220831155703.png]]

## Bias-Variance trade-off
As the #flexibility of $\hat{f}$ increases, its variance increases and its #bias decreases. So chossing the flexibility based on average test error amounts to a bias-variance trade-off.

## Classification problems
Here the response variable $Y$ is *qualitative* and we use *conditional probabilities*
We measure the performance using the *misclassificatioh error rate*

![[Pasted image 20220831165450.png]]


