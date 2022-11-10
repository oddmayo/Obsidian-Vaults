![[Pasted image 20221110225038.png]]

**Estimate mean of this series**

In EViews we have to make a regression in the constant which is the sample average. For the variance indicate the use of a autoregression consistent estimate: HAC (Newey-West); autocovariances with the triangular kernel

![[Pasted image 20221110225649.png]]

p-value of 0.8 > 0.05 I don´t reject the null hypothesis that the mean is zero

Let us test AR(2)

![[Pasted image 20221110225941.png]]
Complex roots, cyclical pattern of AR
Coefficient are the $\phi$

**Correlogram**
![[Pasted image 20221110230823.png]]

**Wald test coefficient restrictions**

On the first and second coefficients

![[Pasted image 20221110231417.png]]
Don´t reject the null hypothesis, the lags are significant


**Forecast with the moving average**

![[Pasted image 20221110232209.png]]

![[Pasted image 20221110232249.png]]

Forecast from observation 100 to 120


**Estimating the regression** 


![[Pasted image 20221110232458.png]]

Y on X

![[Pasted image 20221110232536.png]]

Standard errors computed assuming independent residuals (which I don´t because this is a time series)

Adjust with the long run variance HAC (Newey-West)

![[Pasted image 20221110232703.png]]

Coefficients remain the same but the standard errors are different





