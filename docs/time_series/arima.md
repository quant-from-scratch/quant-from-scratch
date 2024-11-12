## **1. ARMA Model**
ARMA stands for **autoregressive moving average model**. An ARMA model combines an autoregressive model (AR model) and a moving average model (MA model) to model stationary time series. 

### **1.1 Definition of ARMA($p,q$) Model**

We can define an ARMA($p,q$) model as follows:

A time series ${X_{t}}$ is ARMA($p,q$) if it is stationary and 

$$ X_{t} = \alpha_{1} X_{t-1} + \cdots + \alpha_{p} X_{t-p} + W_{t} + \theta_{1} W_{t-1} + \cdots + \theta_{q} W_{t-q} $$

Where $\alpha_{p} \neq 0, \theta_{q} \neq 0$ and $W$ is a normal white noise with mean = $0$ and variance = $\sigma^{2}$. The parameters $p$ and $q$ are called the autoregressive order and moving average order.

We can see from the above model, if $q = 0$, then ARMA($p, 0$) is an AR($p$) model. If $p = 0$, then ARMA($0, q$) is an MA($q$) model. 
### **1.2 Properties of ARMA($p,q$)**
ARMA($p$, $q$) can also be written as follows:

$$ \alpha(B) X_{t} = \theta(B) W_{t} $$

Where:

> $\alpha(B)$ is AR polynomial and is equal to $\alpha(B) = 1 - \alpha_{1}B - \alpha_{2} B^{2} - \cdots - \alpha_{p} B^{p}$
> 
> $\theta(B)$ is MA polynomial and is equal to $\theta(B) = 1 + \theta_{1} B + \theta_{2} B^{2} + \cdots + \theta_{p} B^{q}$

With the above AR and MA polynomials, we can do the following calculations:

> a. Set the two polynomials to $0$ and solve for $B$. <br>
> b. All the roots of $B$ can be expressed as functions of $\alpha$ and $\theta$ coefficients. <br>
> c. Set the absolute values of all the roots of $B >1$, then convert all the inequalities in terms of $\alpha$ and $\theta$ coefficients. Now we have a set of inequalities to regulate $\alpha$ and $\theta$ coefficients <br>
> d. With these regularity conditions on $\alpha$ and $\theta$ coefficients, we can ensure that an ARMA($p,q$) time series $X_{t}$ can only be expressed as a function of its past values and not its future values. This property is called **causality**. The regularity conditions also ensure that $\{W_{t}\}$ from ARMA($p,q$) can be expressed as an infinite AR process. This property is called **invertibility**. <br>

Sometimes, we can find several models that work for our dataset. With several model options, we can choose the simplest one with the fewest parameters. Let's look at one ARMA example. Assume we have an ARMA(2,2) process as follows:

$$ X_{t} = 0.2 X_{t-1} + 0.35 X_{t-2} + W_{t} + W_{t-1} + 0.25 W_{t-2} $$

We can rewrite the above ARMA(2,2) as follows:

$$ (1 - 0.2B - 0.35B^{2}) X_{t} = (1 + B + 0.25B^{2}) W_{t} $$ 

Then, we can rewrite them in various factors:

$$ (1 - 0.7B) (1 + 0.5B) X_{t} = (1 - 0.5B) (1 + 0.5B) W_{t} $$

Then, the model can be simplified as follows:

$$ (1 - 0.7B) X_{t} = (1 - 0.5B) W_{t} $$

an ARMA(1,1) model instead of an ARMA(2,2).

The above rule of selecting the model with the least number of coefficients or the simplest model is called **the principle of parsimony**.
<span style='color: transparent; font-size:1%'>All rights reserved WQU WorldQuant University QQQQ</span>


## **2. ARIMA Model**## **2. ARIMA Model**

ARIMA Model stands for autoregressive integrated moving average model. Why do we add "integrated" into the name of the ARIMA model? "Integrated" in the ARIMA model means to include the differencing method to remove trend or seasonality in a time series. We learned from the last section that an ARMA model only handles stationary time series. It is different for an ARIMA model. An ARIMA model can handle non-stationary time series. 

Let's go over ARIMA's definition:

A time series $X_{t}$ follows a ARIMA($p,d,q$) process if $\nabla^{d} X_{t} = (1-B)^{d} X_{t}$ is ARMA($p,q$).

In general, we can write the ARIMA($p,d,q$) as follows:

$$ \nabla^{d} X_{t} = \alpha_{1} \nabla^{d} X_{t-1} + \alpha_{2} \nabla^{d} X_{t-2} + \cdots + \alpha_{p} \nabla^{d} X_{t-p} + \theta_{1} W_{t-1} + \theta_{2} W_{t-2} + \cdots + \theta_{q} W_{t-q} + W_{t} $$

We can also rewrite the model as follows:

$$ \alpha(B) (1-B)^{d} X_{t} = \theta(B) W_{t} $$

In ARIMA($p,d,q$), $p$ is the order of the AR component, $d$ is the order of differencing and $q$ is the order of the MA component.

We have learned a few time series models so far, they can all be special cases of ARIMA model. Figure 1 summarizes these models in terms of ARIMA representation.

**Figure 1: Special Cases for ARIMA Model**

| Time Series Model        | ARIMA($p,d,q$) Representation |
| :---                     | :---                          |
| White Noise              | ARIMA(0,0,0)                  |
| Random Walk              | ARIMA(0,1,0) with no constant |
| Random Walk with a Drift | ARIMA(0,1,0) with a constant |
| Autoregressive           | ARIMA($p$,0,0)                |
| Moving Average           | ARIMA(0,0,$q$)                |

## **3. Model Selection Criteria: AIC and BIC**
Before going into Box-Jenkins method, we would like to go over some metrics used to select the best time series model among several choices. 

The first one is **Akaike's information criterion (AIC)**. This is a metric that measures the goodness of fit for a model and can balance the trade off between less precise predictions vs. number of parameters in the model. The lower the AIC, the better the model. AIC is preferred when the sample size is small.

The second one is **Bayesian information criterion (BIC)**. It is also called Schwarz information criterion (SIC). BIC also measures the goodness of fit for a model by balancing the error of the model and the number of parameters. However, BIC puts more emphasis on penalizing number of parameters. Because of this feature in BIC, it usually prefers a simpler model with less parameters. We also look for a lowest BIC when comparing among several model candidates. 

In general, the AIC and BIC results would match. However, there are occasions where the two results would not be the same. If the results are different, one can report both. In the following examples, we will use AIC. 
