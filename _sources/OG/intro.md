(Chap_OGintro)=
# Overlapping Generations Macro Model

The model we are training you to use is called `OG-Core`. "OG" refers to the model being an overlapping generations model. "Core" refers to the fact that the model is a core model, meaning that it is a foundational model that can then be parameterized to represent a specific economy.

The phrase "overlapping generations" refers to a key feature of this class of model, which is that there are multiple generations of economic agents (individuals or households) whose lives overlap. That is, at any point in time, there are several generations of agents living and making economic decisions.  Thus, if one would like to do any analysis of intergenerational transfers (e.g., through a public pension system or through environmental policies that impose costs today to have benefits in the future), then one needs to use an overlapping generations model.[^citation_note]

To further describe `OG-Core`, it is a dynamic, general equilibrium, overlapping generations model.  The adjective "dynamic" refers to the model accounting for the dimension of time. Agents are forward looking and consider tradeoffs between today and the future. The adjective "general equilibrium" refers to the model accounting for the fact that all markets are in equilibrium.  That is, the model is a system of equations that are solved simultaneously.  By imposing an equilibrium on the model, we are ensuring consistency in the choices economic agents make and aggregate outcomes.

There are two types of equilibria we solve for when solving the `OG-Core` model.  One is the steady-state equilibrium, which represents the economy in the vary long run, when policy has been stabilized and all variables are growing at the same rate.  The other is the transition path equilibrium, which represents the economy from the short run up to the long-run steady state.  Over the transition path, policy may vary and variables may be growing at different rates.  We refer the reader to the detailed [`OG-Core` documentation](https://pslmodels.github.io/OG-Core/content/intro/intro.html) for a full characterization of these equilibria.  But it is important to note that the `OG-Core` model is a general equilibrium model that solves for both the steady-state equilibrium and the transition path equilibrium.  And in the model solution algorithm, one much work backwards in time - solving for the steady-state equilibrium first and then solving for the transition path equilibrium.


## A Comparison to Other Macro Models

There are essentially six types of macroeconomic models that are used for policy analysis.  These are: (1) Econometric macroeconomic models, (2) Solow growth models, (3) DSGE models, (4) CGE models, (5) Hybrid macro models, and (6) Overlapping generations models.  We briefly describe each of these models and their strengths and weaknesses.

Econometric models are used to predict future outcomes based on past data, using a statistical model. These models can be fairly accurate in predicting the trajectory of the economy if there are no policy changes.  However, these models are not well suited for counterfactual policy analysis, since changes in policy often affect the relationships between macroeconomic variables and therefore the statistical model is not well suited for predicting the future.  These models are often used to form a baseline for policy analysis.

The Solow growth model is a foundational model in macroeconomics and underlies many modern macroeconomic models. The Solow model is a dynamic model and can account for counterfactual policy.  However, the Solow model uses a representative agent, so it cannot do distributional analysis.  The Solow model also uses an infinitely-lived agent, so it cannot do intergenerational analysis.  The Solow model is best suited for long-run analysis.

Dynamic Stochastic General Equilibrium (DSGE) models can model the short and long run and can be used for counter-factual policy analysis. These models can have heterogeneous agents, so they can do distributional analysis.  However, DSGE models use an infinitely-lived agent, so they cannot do intergenerational analysis.  DSGE models are also typically solved with methods that are not suitable for large policy changes, since they use approximations to solve the model.  This limits there use for analysis of significant policy changes or large economic shocks.

Computable General Equilibrium (CGE) models typically refer to a specific type of CGE model, despite the fact that many classes of models (Solow, DSGE, OG) are all solve for a general equilibrium using computational methods.  CGE usually refers to models that have a rich specification of the economy (e.g., heterogeneous agents and many production sectors), but that models economic decision makers in a static way. That is, CGE models do not account for the dimension of time.  CGE models have become less common in recent years in favor of dynamic models that account for the dimension of time.  However, CGE models still have wide use in regional analysis and in trade analysis, where its important to be able to model very detailed geographies or industrial sectors.

Hybrid macroeconomic models are not commonly used, but some important policy institutions use them, such as the United States' Joint Committee on Taxation.  These models have a long run equilibrium similar to the steady-state of an OG model.  And they do allow modeling of both the short and long run, include heterogenous agents, and finitely-lived agents (therefore can do intergenerational analysis).  However, in the short run, agents are myopic and the model is not in equilibrium.  This limits the usefulness of these models for policy analysis.

OG models typically feature some of the best components from each of these: forward looking agents, finitely-lived agents allowing for intergenerational analysis, heterogeneous agents, a modeling of the economy's general equilibrium in the short and long run.  The code these features impose is a more complex and computationally costly solution algorithm.  However, the solution algorithm is global and therefore can accommodate large policy changes.  This makes OG models well suited for policy analysis.  And in the design of OG-Core, we've leveraged tools of high performance computing to make the solution algorithm as efficient as possible.

## An Overview of OG-Core

Details of the OG-Core model are available in its [online documentation](https://pslmodels.github.io/OG-Core/content/intro/intro.html).  Here we provide a brief overview of the model and its solution algorithm.

On the demand side, the OG-Core framework models agents (households or individuals) who live up to `S` economically active periods from age `E` to `E+S`, where `E` is the age they become economically active. In each period of life, agents choose how much to consume, work, and save. Their consumption choices are made across `I` different consumption goods.  A new generation of agents is born each model period, and these size of these generations is determined by demographic projections taken from outside the model.  In each generation there are `J` different types of agents who differ in their lifetime labor productivity profiles, the relative value they place in intentional bequests and their time discount rate (i.e., their amount of patience when waiting for a future payoff).

The supply side of the economy is comprised of a representative firm for each of `M` production industries.  These firms use capital, labor, and public infrastructure to produce their differentiated output good via a constant elasticity of substitution production function that displays constant returns to scale. These output goods are combined in a fixed way to produce the `I` consumption goods.  A simplification made in the model solution is that the capital good (used for investment in private capital and government infrastructure) is produced by just one industry, usually calibrated to the manufacturing sector.

The government sector can impose taxes on income (personal and corporate), wealth, bequests, and consumption. These revenues are used to finance government spending on public infrastructure investment, a public good (that does not affect agents' utility), and transfer payments to households.  The government can also borrow or save in private capital markets.  The government is able to run budget deficits over the transitio path, however, the model enforces a government budget constraint in the steady-state equilibrium so that debt cannot grow faster than the economy in the long run.

The rest of the world is modeled simply.  Individuals migrate in and out based on an exogenous, but time varying, process for immigration. Net capital flows into and out of the economy, supporting private capital investment and government borrowing.

The market clearing conditions ensure that in each period, the supply of labor from the `SxJ` household is equal to the total demand from labor from the `M` firms.  Total supply of savings from households must match the total demand for savings from the government's borrowing and from the firms use of capital. Finally, the total demand for consumption goods from households must equal the total supply of consumption goods as determined from the firms' production of the `M` output goods and their mapping into the `I` consumption goods.


## Country Calibrations of OG-Core

As described above, `OG-Core` is a foundational and general model.  It has all the pieces, but it doesn't represent any specific economy.  To represent a specific economy, one must calibrate the model to that economy.  This involves setting the values of the parameters of the model to so that the model output matches that of the economy you wish to model.  `OG-Core` has thousands of parameters, so this can be a significant task.  Some current country-specific calibrations (with varying degrees of detail) have been done for the [United States](https://github.com/PSLmodels/OG-USA), the [United Kingdom](https://github.com/PSLmodels/OG-UK), [South Africa](https://github.com/EAPD-DRB/OG-ZAF), [India](https://github.com/Revenue-Academy/OG-IND), and [Malaysia](https://github.com/Revenue-Academy/OG-MYS).

Each of these country calibrations can be used a examples when creating a calibration of a country of interest to you.  In chapters that follow, we'll provide some more details on how part of this calibration are done and give you example exercises related to the calibration process to hel you better understand it.

What comes out of these calibration packages is a `Calibration` class object that contains new parameter values and that can be used to update teh `Specifications` class object that is passed to the `OG-Core` model and that represents the parameterization of the model.  We will describe this process in more detail in the chapters that follow.


(SecOGintroFootnotes)=
## Footnotes

The footnotes from this chapter.

[^citation_note]: For examples of OG modesl used for policy analysis, see {cite}`AuerbachEtAl:1981,AuerbachEtAl:1983`, {cite}`AuerbachKotlikoff:1983a,AuerbachKotlikoff:1983b,AuerbachKotlikoff:1983c`, and {cite}`AuerbachKotlikoff:1985`.
