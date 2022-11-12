
![[Pasted image 20221112181017.png]]

The first is when I have only one linear combination and two integrated

And a second situation when I have two different linear combinations and 1 integrated

As the model gest bigger the situations get more complicated


---


**Lag length criteria**

![[Pasted image 20221112182156.png]]

3 lags

Knowing the correct number of lags gives me the information to how many lags to specify in the vector error correction mechanism

Before estimating I need to know how many cointegrated relations I have

**Test for cointegration** (Johansen system)

For all situations (constant and intercept)

![[Pasted image 20221112182440.png]]

There is one cointegrated relation according to Schwarz criteria with no trend and no intercept. In other words...

![[Pasted image 20221112182631.png]]


**Estimation with Vector Error Correction**

Select two lags as we use first differences

![[Pasted image 20221112183035.png]]

We test if both these elements are 1
![[Pasted image 20221112185027.png]]


And we test if the coefficient of Cointegrated equation affecting the Dynamics of the first equation X is zero

![[Pasted image 20221112200137.png]]
These assumptions are not rejected

**Impulse response function**

X seems to cause Y and not the other way around

![[Pasted image 20221112200602.png]]

In the long run they are completely running together because they are cointegrated