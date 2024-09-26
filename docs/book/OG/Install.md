(Chap_OGinstall)=

# Installing `OG-Core`

## Installing and Running OG-Core from Python Package Index (PyPI.org)

* Open your terminal (or Conda command prompt), and make sure you have the most recent version of `pip` (the Python Index Package manager) by typing on a Unix/macOS machine `python3 -m pip install --upgrade pip` or on a Windows machine `py -m pip install --upgrade pip`.
* Install the [`ogcore`](https://pypi.org/project/ogcore/) package from the Python Package Index by typing `pip install ogcore`.
* Navigate to a folder `./YourFolderName/` where you want to save scripts to run OG-Core and output from the simulations in those scripts.
* Save the python script [`run_ogcore_example.py`](https://github.com/PSLmodels/OG-Core/blob/master/run_examples/run_ogcore_example.py) from the OG-Core GitHub repository in the folder where you are working on your local machine `./YourFolderName/run_ogcore_example.py`.
* Run the model with an example reform from terminal/command prompt by typing `python run_ogcore_example.py`
* You can adjust the `run_ogcore_example.py` script by modifying model parameters specified in the `og_spec` dictionary.
* Model outputs will be saved in the following files:
  * `./run_example_plots`
    * This folder will contain a number of plots generated from OG-Core to help you visualize the output from your run
  * `./ogcore_example_output.csv`
    * This is a summary of the percentage changes in macro variables over the first ten years and in the steady-state.
  * `./OUTPUT_BASELINE/model_params.pkl`
    * Model parameters used in the baseline run
    * See [`execute.py`](https://github.com/PSLmodels/OG-Core/blob/master/ogcore/execute.py) in the OG-Core repository for items in the dictionary object in this pickle file
  * `./OUTPUT_BASELINE/SS/SS_vars.pkl`
    * Outputs from the model steady state solution under the baseline policy
    * See [`SS.py`](https://github.com/PSLmodels/OG-Core/blob/master/ogcore/SS.py) in the OG-Core repository for what is in the dictionary object in this pickle file
  * `./OUTPUT_BASELINE/TPI/TPI_vars.pkl`
    * Outputs from the model time path solution under the baseline policy
    * See [`TPI.py`](https://github.com/PSLmodels/OG-Core/blob/master/ogcore/TPI.py) in the OG-Core repository for what is in the dictionary object in this pickle file
  * An analogous set of files in the `./OUTPUT_REFORM` directory, which represent objects from the simulation of the reform policy

Note that, depending on your machine, a full model run (solving for the full time path equilibrium for the baseline and reform policies) can take more than two hours of compute time.

If you run into errors running the example script, please open a new issue in the OG-Core repo with a description of the issue and any relevant trace backs you receive.

The CSV output file `./ogcore_example_output.csv` can be compared to the [`./run_examples/expected_ogcore_example_output.csv`](https://github.com/PSLmodels/OG-Core/blob/master/run_examples/expected_ogcore_example_output.csv) file in the OG-Core repository to confirm that you are generating the expected output. The easiest way to do this is to copy the [`example-diffs`](https://github.com/PSLmodels/OG-Core/blob/master/run_examples/example-diffs) and [`example-diffs.bat`](https://github.com/PSLmodels/OG-Core/blob/master/run_examples/example-diffs.bat) files from the OG-Core repository and use the `sh example-diffs` command (or `example-diffs` on Windows) from the `run_examples` directory. If you run into errors running the example script, please open a new issue in the OG-Core repo with a description of the issue and any relevant trace backs you receive.


## Installing and Running OG-Core from GitHub repository

* Install the [Anaconda distribution](https://www.anaconda.com/distribution/) of Python
* Clone the [`OG-Core` repository](https://github.com/PSLmodels/OG-Core) to a directory on your computer
* From the terminal (or Conda command prompt), navigate to the directory to which you cloned this repository and run `conda env create -f environment.yml`
* Then, `conda activate ogcore-dev`
* Then install by `pip install -e .`
* Navigate to `./run_examples`
* Run the model with an example reform from terminal/command prompt by typing `python run_ogcore_example.py`
* You can adjust the `./run_examples/run_ogcore_example.py` script by modifying model parameters specified in the `og_spec` dictionary.
* Model outputs will be saved in the following files:
  * `./run_examples/run_example_plots`
    * This folder will contain a number of plots generated from OG-Core to help you visualize the output from your run
  * `./run_examples/ogcore_example_output.csv`
    * This is a summary of the percentage changes in macro variables over the first ten years and in the steady-state.
  * `./run_examples/OUTPUT_BASELINE/model_params.pkl`
    * Model parameters used in the baseline run
    * See `execute.py` for items in the dictionary object in this pickle file
  * `./run_examples/OUTPUT_BASELINE/SS/SS_vars.pkl`
    * Outputs from the model steady state solution under the baseline policy
    * See `SS.py` for what is in the dictionary object in this pickle file
  * `./run_examples/OUTPUT_BASELINE/TPI/TPI_vars.pkl`
    * Outputs from the model time path solution under the baseline policy
    * See `TPI.py` for what is in the dictionary object in this pickle file
  * An analogous set of files in the `./run_examples/OUTPUT_REFORM` directory, which represent objects from the simulation of the reform policy

Note that, depending on your machine, a full model run (solving for the full time path equilibrium for the baseline and reform policies) can take more than two hours of compute time.

If you run into errors running the example script, please open a new issue in the OG-Core repo with a description of the issue and any relevant trace backs you receive.

The CSV output file `./run_examples/ogcore_example_output.csv` can be compared to the `./run_examples/expected_ogcore_example_output.csv` file that is checked into the repository to confirm that you are generating the expected output. The easiest way to do this is to use the `sh example-diffs` command (or `example-diffs` on Windows) from the `run_examples` directory. If you run into errors running the example script, please open a new issue in the OG-Core repo with a description of the issue and any relevant trace backs you receive.

## Exercises
```{exercise-start}
:label: ExerInstall-install
:class: green
```
Intall and run the `OG-Core` example file as instructed above on your computer.  How long did it take to execute?
```{exercise-end}
```
