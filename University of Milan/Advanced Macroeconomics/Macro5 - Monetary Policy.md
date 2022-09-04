# Monetary Policy
## Monetary policy implementation
How does the CB implement the intended value of $r_t$ for #inflation_targeting ? [[Macro3 - Aggregare Suply]] The interest rate that affects aggregate demand is the **real interest rate** $r_t$ *but* is not under direct control of the CB plus it has long maturity

The instruments under direct control (linked to $r$) of the CB are:
1. Short-term **nominal interest rate**: $i$
2. Quantity of **reserve money**: $R$

We need to follow *3 steps*:
1. Use the *fisher equation* $\rightarrow$ connect $r$ and $i$
2. Use the *term structure* of interest rate $\rightarrow$ from long to short maturity
3. Use the i*nterbank market* for reserve money $\rightarrow$ connect $i$ and $R$

## 1. Inflation expectations and the Fisher Equation
**Fisher Equation:**  $r_t=i_t-\pi_{t+1}$ 

A vaue of $r_t$ is *equivalent* to $i_t$ conditional upon knowledge of inflation expectations

We assume perfect foresight $\pi_{t+1}^e=\pi_{t+1}$ (CB has info on  $\pi_{t+1}^e$ thanks to surveys and models)

We can rewrite the **MP rule**: 
![[Pasted image 20220904131049.png]]

The CB does not control the nominal interest rate with the same (relatively long) maturity of $r_t$. The **CB controls a series of short-term nominal interest rates**.

Need to move from long maturity rate to short maturity. The *term structure* relates interest rates with different maturities

## 2. The term structure of interest rates
Express them in annualized terms

![[Pasted image 20220904131507.png]]

Suppose an investor has $\texteuro1$ to invest on a 2-year horizon an can use bonds of only two maturities: 3 months and 2 years.
**If** there is no barrier to arbitrage and investors are risk-neutral then the expected returns on the two strategies **should be equal**

The *interest rate* on **long maturity** (risk) bonds *equals* the forward average of the interest rates on **shorter maturity** bonds

![[Pasted image 20220904185424.png]]

Since investors are in general risk-averse, they will require a #term_premium for long maturity bonds ($\varphi$)

The term structure implies that the **CB can influence long-maturity** nominal interest rates by manipulating short term $i$. The relevant policy rate is the *interest rate* on the short term loans in #interbank_markets

### Monetary policy implementation

Recalling the #fisher_equation
![[Pasted image 20220904185828.png]]

The CB can use short-term $i$ to manipulate long term $i$ if:

1. The path of short-term interest rates is *sufficiently predictable* ($i$)
2. The *term premium* is relatively stable
Except in times of financial turmoil

## 3. Use the interbank market for reserve money
Call $i^M$ the short term nominal interest rate, nor freely set by the CB but by the *interbank market*

### A bank can settle a transitory deficit
- By interbank *loan*
- By outright *payment*

$i^M$ is the reate at which banks lend to each other in the very short runon the interbank market

$i^M$ is the **equilibrum interest rate** on interbank loans

Reserves that banks hold on accounts at the CB earn the *interest rate on reserves* $i^R$ 

The **CB set directly** $i^R$ (exogenous)

### A bank in surplus may choose to
- Keep its excess reserve money on the account at the CB and earn $i^R$
- Lend its excess reserve money to banks in deficit and earn $i^M$

Condition $i^M \geq i^R$  is *necessarily satisfied*

$i^M - i^R$ is the *opportunity cost* of reserves kept at the CB

The demand for reserve money $R^d=R^d(i^m-i^R,y)$ function

This is *under the control of the CB* through **open market operations**
- Buy assets $R^s\uparrow$ 
- Sell assets $R^s\downarrow$

**$i^M$ is determined by equality of demand and supply**
![[Pasted image 20220904192333.png]]

In the short run y can be considered exogenous and constant

To raise $i^M$ the CB can:
![[Pasted image 20220904192514.png]]

---
**In summary** the machanism:
![[Pasted image 20220904192644.png]]

## The Taylor rule (instead of MP for the CB's behavior)
It **relates** the short term nominal interest rate *$i^M$ to the inflation gap* to an empirical measure of the output gap

It represents a statistical regularity and not a proper representation of CB's behavior. *The CB tries to influence AD by influencing $r_t$ (indirectly) with its monetary policy*

It's popular because it helps CBs to communicate about the path of short teerm nominal interest rates, making the CB more credible

## The #taylor_principle (necessary for macro stability within our AD-AS model) $\pi_t \rightarrow \overline{\pi}$  

[[Macro4 - AD-AS Eq.]]

The CB's target for the nominal interest rate should react more than one-for-one to inflation

**$r_t$ should increase when $\pi_t$ rises**; MP is consistent with this principle only if $\gamma >0$  

![[Pasted image 20220904193620.png]]


