(SecFiscalPolicy)=
# Fiscal Policy

Governments in the `OG-Core` model may raise revenue through the taxation of personal and corporate income,  payroll taxes, consumption taxes, taxes on bequests, and wealth taxes. These revenues, along with government borrowing, as you used to finance expenditures on transfers, government investment in infrastructure, spending on a public good, and interest payments on debt.  Here, we discuss the calibration of each of these parameters.

<!-- ## Tax rates


## Pension systems -->


## Spending parameters

Government spending, at least that is modeled outside of the net tax functions or pension functions, is modeled as an exogenous fraction of GDP, with an exception in some parameterizations that we discuss below.  By calibrating spending as a fraction of GDP, on avoids any need to convert between model and data units and it also more accurately mimics the empirical fact that the size of governments tends to grow with the size of the economy.  There are three spending related parameters that are shares of GDP.  These are `alpha_G`, the ratio of government spending on public goods to GDP, `alpha_T`, the ratio of government spending on transfers to GPD, and `alpha_I`, the ratio of government spending on infrastructure to GDP.

To calibrate these ratios, one can generally use national accounts data in combination with government budget reports.  The challenging piece to ensure that the definition of spending in the data and the model are aligned.  For example, if you are explicitly modeling the pension system and using the net tax functions to capture some non-pension spending programs (such as income-tested welfare benefits), then you will want to exclude those spending programs when computing total transfers by year as the numerator in the `alpha_T` ratio.  Another strategy, to make sure you are fully capturing government outlays, is to compute one of the spending ratios as a residual.  For example, if you have data on government spending on public goods and transfers (again, after taking out what is accounted for in the modeling of pensions and taxes), you can compute the infrastructure spending ratio as a residual (= 1 - `alpha_G` - `alpha_T`).

The default way in which total transfers, $TR_t = alpha_{T,t} * GDP_{t}$ gets allocated to households is as a lump-sum, uniformly distributed transfer.  But you can adjust this distribution to match the true distribution of transfers across the population by adjusting the `eta` parameter. This is a three dimensional array that is `TxSxJ`. It sums to one in each model period and represents the fraction of transfers in that year distributed to each age (`S`) and lifetime income group (`J`). You can thus approximate the age and mean-tested transfers with this matrix, as well as policy changes that affect the distribution of transfers across the population over time.

As a final note, one will need to set the value for the initial infrastructure to GDP ratio, `initial_Kg_ratio`.  To find this, one needs an estimate of the stock of public infrastructure.  If no report exists reporting this an approximation would be to say that $K_g = \frac{I_g,t} / \delta_{g}$, where $I_{g,t}$ is the among of infrastructure spending (at present or averaged over recent years) and $\delta_g$ is the ratio of depreciation on this infrastructure (e.g., 2\% per annum).

## Government financing parameters

Governments can run an unbalanced budget, but in order for an equilibrium to exist, deficits must be restricted such that they do not grow faster than GDP (if they did, interest payments on the debt would grow beyond available resources).  Governments therefore can borrow to finance outlays.  As there is no idiosyncratic risk on private capital in the model, we build in a risk premium by allowing the government to borrow at a rate lower than the private market.  If the rate the private market pays is given by `r`, then the government pays an interest rate of `r_gov = r_gov_scale * r - r_gov_shift`.  The `r_gov_scale` and `r_gov_shift` parameters are two that one would calibrate to the economy in question.  We advise doing this by looking at the historical haircut on private interest rates that the government has paid.  For example, if the government has paid an average interest rate of 1.5 percentage points below the private market, then `r_gov_scale` would be 1.0 and `r_gov_shift` would be 0.015.  One can do this in a systematic manner by finding time series data on government debt and corporate debt of the same maturity and estimating the two parameters directly.  For example, with these data you can estimate, via OLS, the following equation:

```{math}
r_{gov,t} = \alpha + \beta r_{corp,t} + \epsilon_t
```

where $r_{gov,t}$ is the interest rate on government debt and $r_t$ is the interest rate on corporate debt.  The parameter $\beta$ would then be the value of `r_gov_scale` and $\alpha$ would be the negative of the value of `r_gov_shift`.

Finally, we need to calibrate the initial government debt to GDP ratio, `initial_debt_ratio`.  This is done by finding the ratio of government debt to GDP in the most recent year of data and setting `initial_debt_ratio` equal to that value.


(SecCalibFiscalExercises)=
## Exercises

```{exercise-start}
:label: ExerCalib-macro_reg
:class: green
```
Now let's estimate the autocorrelation in GDP growth, assuming is a first order auto-regressive process (AR1).  We'll do this with the `statsmodles.OLS` function.

First, create a new column in your data frame that is the lagged value of GDP growth.  Then, use the [`statsmodels.regression.linear_model.OLS`](https://www.statsmodels.org/dev/generated/statsmodels.regression.linear_model.OLS.html) function to estimate the following equation:

   ```{math}
   y_{t} = \alpha  + \rho y_{t-1} + \varepsilon_{t}
   ```

What did you estimate as $\alpha$?  What does this represent?  How persistent is the growth process in South Africa?

```{exercise-end}
```
