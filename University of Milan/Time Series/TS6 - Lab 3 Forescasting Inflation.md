![[Pasted image 20221112170138.png]]


Inflation should not go too high or too low

Test for unit root
![[Pasted image 20221112171730.png]]

P-value above the critical value so we don´t reject the null hypothesis: possible unit root

**Correlogram**

![[Pasted image 20221112171917.png]]

The autocorrelation seems to stay high for quite a while and partial autocorrelation also stay up: it suggest an autoregressive component but also a moving average component

Estimating multiple ARMA models and selecting the best one based on Schwarz information criterium
![[Pasted image 20221112172940.png]]

**Correlogram of the residuals**
![[Pasted image 20221112173232.png]]

Well within boundaries
The null hypothesis that is errors resemble an independent process is not rejected, so the ARMA(1,1) is a good choice

If I want to do the model in first differences: correlogram with 1st differences

![[Pasted image 20221112173438.png]]

Moving average (1), estimation of this:

![[Pasted image 20221112173520.png]]

Estimates are similar, this one imposes rho=1 and compensates by having a slightly more negative value for the moving average

Correlation of the residuals
![[Pasted image 20221112173657.png]]
Also resemble an independent process


So we have two candidate models for forecast:

Unit root one with ARMA(1,1) or first differences one with MA(1)


**Forecast of ARMA(1,1)**
![[Pasted image 20221112173850.png]]




**Forecast with MA(1)**

![[Pasted image 20221112174125.png]]


**Comparison with simple forecast**

![[Pasted image 20221112174330.png]]

**Seeing the forecast error**

![[Pasted image 20221112174604.png]]

Naïve forecast is all over the place
The ARMA and MA are close to each other
The professional forecasters seems to be closer

**See the squares of the errors**

The best forecast is the best with the smallest mean squared error
![[Pasted image 20221112174948.png]]

The professional forecasters are the best, followed by the ARMA and MA models

To see if the difference between means is significant we estimate a model with the difference of the professional forecasters and the ARMA model 

![[Pasted image 20221112175513.png]]

There is a difference but not statistically significant

Now between the ARMA and the naïve model
![[Pasted image 20221112175721.png]]

There is a difference, t-statistic > 1.96


**In summary**

Imposing the unit root resulted in a slightly smaller mean squared error
(Not a good model from economics point of view but it does a good forecast)

The forecast of the professionals is not statistically better than our models








