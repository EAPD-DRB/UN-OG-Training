(SecMacroParams)=
# Macro parameters

There are a number of parameters of the `OG-Core` model that are calibrated using macroeconomic data from national accounts or national government reports.  In general, we've tended to read in data that inform these values in a single module, such as the [`macro_params.py`](https://github.com/EAPD-DRB/OG-ZAF/blob/main/ogzaf/macro_params.py) module in `OG-ZAF`.  We break the discussion of the parameters calibrated from macro data into separate groupings based in what they represent in `OG-Core`.

## Economic growth and production

The `OG-Core` model needs to be stationary in order to employ traditional solution methods.  This means that in the model solution, there cannot be underlying growth in the model objects.  However, the model is able to allow for such underlying growth, which may be driven by population growth rates (as discussed above) or underlying changes in productivity.  In order to solve the model, then, trend growth from these sources are removed.[^stationary_note].  However, since different variables grow at different rates, we need to know both the underlying growth rates of the population and of technological growth.  The population growth rate was determined from the demographic data and described in Section {ref}`SecDemographics`. We use macroeconomic data, namely the growth rate in gross domestic product per capita to pin down the rate of growth in (labor-augmenting) technological change, `g_y_annual` in `OG-Core`.  Let $\hat{y}_t$ represent the growth rate in GDP per capital from year $t-1$ to year $t$.  We find the value of `g_y_annual` as equal to the long-run average of $\hat{y}_t$:

```{math}
:label: g_y_calib
 g_y = \sum_{t = \text{First year of data}}^{\text{Most recent year of data}} \hat{y}_t
```

Note that you will want to use some judgement in what is the appropriate time period for the "first year of data". For example, if the economy in question is now a market economy, but your data extend back to a time when it was not a market economy, you will probably want to exclude those data from the non-market economy period.  In addition, you might alter the calibration of `g_y` to be more forward looking and, rather than base future growth on recent history, you may use long run economic forecasts for GDP per capita.  But in either case the important thing is to be sure you are correctly mapping the data to the theoretical concept of `g_y`, which is measuring the constant rate of growth in output per person in the long run.


### Firm production
Changes in productivity in the short run are accounted for by changes in total factor productivity (TFP).  This parameter is denoted as `Z` in `OG-Core` and is represented by a 2-dimensional array that is `TxM` in size, where `T` is the number of time periods over the transition path and `M` is the number of industries.  Thus, you may have total factor productivity, that changes over time and varies across production industry. Values of `Z` are found through [growth accounting](https://www.imf.org/external/pubs/ft/wp/1999/wp9977.pdf) techniques. However, you may not want to (or easily be able to) do the accounting yourself because it is often difficult to find the necessary data to do such accounting, which requires industry specific capital stocks.  You might find research on sectoral TFP from central banks or other sources.  For the calibration of sectoral TFP from South Africa, we used data published by the central bank. You can find a nice discussion of the process used in that case in [this GitHub Issue](https://github.com/EAPD-DRB/OG-ZAF/issues/29).

In addition to the level of TFP, the production functions of firms are determined by the shares of income attributable to capital, labor, and infrastructure (public capital) and the elasticity of substitution between these inputs. These are the parameters `gamma`, which is the share of income attributable to capital, and `gamma_g`, which is the share of income attributable to infrastructure. The remainder, $1-\gamma-\gamma_g$ is the share attributable to labor.  Factor shares can be determined through national accounts data.  The share out output paid to labor is found from the ration of labor income (wages and salaries) to GDP, while capital's share of income can be found through the payments to capital (interest, dividends, profits) divided by GDP.  The share of output attributed to infrastructure will then be found as a residual (= 1 - labor share - capital share), as the OG-Core model requires a constant returns to scale production function.  Determining the elasticity of substitution between inputs is more involved and would require detailed panel with prices and quantities.  We therefore recommend using a default calibration with a unit elasticity ($\epsilon_m = 1$) for each industry -- or finding other research from your economy of interest where this parameter has been estimated.

Finally, we need to map the $M$ output goods to the $I$ consumption goods.  The `OG-Core` model assumes what is called a "fixed coefficient" matrix for the mapping between producer outputs and consumption goods.  That is, a fixed share of each output good is required to produce each consumption good.  This is represented by an `MxI` matrix denoted as $\Pi$, which has elements $\pi_{m,i}$ that is the share out consumption good $i$ that is from output good $m$.  Note that the columns of this matrix must sum to one (i.e., we need to fully account for the output goods that go into each input good).  The $\Pi$ matrix can be calibrated directly from a input-output tables that are typically produced through national accounts.  In the `OG-ZAF` project, there is a nice example of calibrating the $\Pi$ matrix using input-output data in detailed producer outputs and consumer goods categories available in the social accounting matrix files available from [UNU Wider](https://www.wider.unu.edu/social-accounting-matrices).


## International finance

The `OG-Core` model parameterizes the degree of economic openness with two parameters relating to international capital flows.  The first is the fraction of new government debt issues which are purchased by foreign investors, `zeta_D`.  This parameter can be calibrated through financial accounts data that shows the location of buyers of government debt.  The second parameter reflects the amount of excess capital demand that is satisfied by foreign investors.  Here, excess demand is defined as the difference between the capital demand of firms at the interest rate outside the domestic economy (i.e., the world interest rate) and the capital of demand from firms if they face teh domestic interest rate.  The  parameter `zeta_D` takes a value between zero and one and is the share of this excess demand for capital that foreign investors make up.  A value of zero would represent a closed economy, which no foreign investment in domestic capital. While a value of one represented a small open economy, where the domestic interest rate is equated to the world interest rate since capital flows in (or out) freely.  One cannot look just at financial accounts data to calibrate `zeta_D` , because the excess demand concept is model based and there's not a direct analog in the data.  Rather, we have utilized an approach of moving the value of `zeta_D` up or down based on the size of the economy relative to the world, with countries that have a smaller share of world financial market activity having a `zeta_D` closer to one. Of course, one would also like to consider any capital controls that may be in place in the economy of interest.  If there are capital controls, then the value of `zeta_D` should be set to a smaller value.

## Exercises
```{exercise-start}
:label: ExerCalib-macro_datareader
:class: green
```
The [Federal Reserve Economic Database](https://fred.stlouisfed.org) (FRED) contains macroeconomic data for a number of countries and a user friendly interface.  In addition, tools, such as [`pandas-datareader`](https://pandas-datareader.readthedocs.io) make it extremely easy to access the FRED API.  In this exercise, use `pandas-datareader` to download the quarterly, real GDP time series for South Africa from FRED.  Plot it.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-macro_freq
:class: green
```
Now, use the [`datetime`](https://docs.python.org/3/library/datetime.html#datetime-objects) object functions to collapse the quarterly GDP data to annual data.  Plot it.
```{exercise-end}
```

```{exercise-start}
:label: ExerCalib-macro_gy
:class: green
```
With your annual data, compute the annual growth rate for each year.  Plot the time series of growth rates.
```{exercise-end}
```


(SecOGCalibrationMacroFootnotes)=
## Footnotes

The footnotes from this chapter.

[^stationary_note]: For specifics on how this is done, please see the `OG-Core` [Stationarization Chapter](https://pslmodels.github.io/OG-Core/content/theory/stationarization.html).
