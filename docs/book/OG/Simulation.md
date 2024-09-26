(Chap_OGsimulation)=

# Simulating `OG-Core`

`OG-Core` provides the model of the economy. That is, it specifies the different economic actors (firms, households, government governments), how they interact with each other (e.g., in a competitive market with perfect information), and defines the equilibrium conditions (i.e, supply is equal to demand in all markets, households act to maximize their utility, and firms act to maximize their profits).  A particular model solution combines this structure with a given parameterization of the economy (e.g., what exactly are consumers maximizing?  How do firms produce output? What are tax rates?).

Therefore, to simulate the model, we will combine the structure with a given parameterization.  The key programming interface for simulating the model is the [`ogcore.execute.runner`](https://pslmodels.github.io/OG-Core/content/api/execute.html) function, which has one necessary argument, `p`, an instance of the `ogcore.parameters.Specifications` class object.  This `p` object is what carries the model parameters.  Thus this function is the key to simulating the model with different parameterizations.

`OG-Core` comes with a default set of parameters.  Thus, to simulation the model with this baseline set of parameters, we can do:

```python
import ogcore

p = ogcore.parameters.Specifications()
ogcore.execute.runner(p)

```

This will simulate the model and save pickle files with dictionaries of results to a directory on your computer (you can modify the `Specifications` object to change this directory).

Oftentimes, we want to see how the economy changes if we change one of the parameters. This allows our model to speak to counterfactuals through simulation. For example, we can ask questions such as "what would happen to personal incomes if we cut taxes by 20%?" or "what is the effects on interest rates of an two percentage point increase in the ratio of government debt to GDP?" or "what happens to wages if fertility rates decline by 10%?".  In the terminology we use for `OG-Core` we refer to the baseline as the economy before the change, and the reform as the economy after the change.

To simulate a reform, we'd simply change the parameterization of the economy and then re-run the model.  For example, to simulate a change in the corporate income tax rate to 15%, we could do:

```python
import ogcore

p_reform = ogcore.parameters.Specifications(
    output_base = './OUTPUT_REFORM',
    baseline = False,
)
p_reform.update_specifications({'cit_rate': [[0.15]]})
ogcore.execute.runner(p_reform)

```

This above will simulate the model and save pickle files dictionaries of results to the `'./OUTPUT_REFORM'` directory on your computer.  The output of this run can then be compared to that in the `'./OUTPUT_BASELINE'` directory to see the effects of the reform on the economy.  `OG-Core` has some built in functions for creating tables and figures that are helpful in comparing these results.  We discuss those in the next chapter, {ref}`Chap_OGoutput`.

## Exercises:

```{exercise-start}
:label: ExerSim_cit
:class: green
```
Using the above code blocks as an example, simulate the effects of a change in the corporate income tax rate (note the default in `OG-Core` is 21%). Just simulate the effects on the steady state (see the keyword arguments to the `runner` function).  Warning: `OG-Core` allows the corporate income tax rate to vary over time and across industries, so you will need to enter it as a list of lists (even if it's just a scalar that applies to all industries and time).
```{exercise-end}
```