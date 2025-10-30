# Testing Conventions

## Test Tools

We use pytest with coverage reports and some other extensions. Install the following packages for testing.

```
pip install -U pytest
pip install -U pytest-cov
pip install -U pytest-env
pip install -U pytest-order
```

## Minimal Test in molass-library repository

If you have installed the above packages, the minimal way to test it is as follows.

In the repository root:

```
python run_tests.py --test tests/tutorial 
```

This will run the test scripts which test example codes in the [tutorial](https://biosaxs-dev.github.io/molass-tutorial/) using minimal data provided by `molass_data` package. Other advanced ways for testing will be described below. 

## Test Scripts Organizing

Test scripts are classified as shown in the following table and located under "tests" folder.

:::{table} TestScipt Classification and Folder Naming
:widths: auto
:align: center

| Target Type   | Folder Name  | Remark |
| :------- | :------- | :-------|
| Library | generic | for common features |
|         | specific | for PF-specific features like flowchange, etc. |
| Notebook document | tutorial | for the tutorial book |
|          | essence  | for the essence book |
|          | technical | for the technical report book |
:::

Subfoldes and script files should be named and placed roughly as suggested below.

```
molass-library/
    tests/
        generic/
            010_DataObjects/
                test_010_SSD.py
                test_020_Curve.py
                ...
            020_DataUtils/
                test_010_DataUtils.py
                ...
        specific/
            010_Geometric/
                test_010_Peaklike.py
                ...
            020_FlowChange/
                test_010_FlowChange.py

        tutorial/
            01-quicK_start.py
```
As shown in the above table, tests are first classified by the two target types, namely the Molass Library itself and the codes included in the Jupyter Book documents.

One of the reasons for dividing the library tests into the two categories "generic" and "specific" is as follows.

The generic folder should be kept relatively simple by excluding site-specific tests such as "FlowChange", which arises only from unique experiment practice at some SAXS beamlines in [Photon Factory](https://www2.kek.jp/imss/pf/eng/), Japan and often includes complex issues irrelevant to generic cases.


```{note}
Three-digit numbers are just for ordering in the following sense.
* ease for glancing over roughly in created (or logical) order
* order of test execution

```

## Running Tests
### Test Data Settings

For basic tests, we also use data package `molass_data`, which was introduced for the document notebooks like [Tutorial](https://biosaxs-dev.github.io/molass-tutorial/).

The data sets named `SAMPLE*` are included in the data package `molass_data`. For extra tests, prepare `local_settings.py` like shown below, as explained at [Local](https://biosaxs-dev.github.io/molass-library/source/molass.Local.html) module reference.

```python
LocalSettings = dict(
    DATA_ROOT_FOLDER=r"D:\AllExperimentData",
)
```

Data sets for `DATA_ROOT_FOLDER` is currently not provided for download. If you need them, let us know by opening an issue using the ![github icon](../../images/mark-github.svg) button at upper right corner of this page.

### Test Utility
We have developed a utility script `run_tests.py` which has the following basic features.

* Multiple modes: batch, save, interactive, both
* Flexible targeting: Single files, directories, ranges (--range 1-3)
* Interactive plotting: Proper matplotlib GUI display

It also has the following capabilities.

* Systematic matplotlib control with @control_matplotlib_plot
* Numerical warning suppression with @suppress_numerical_warnings
* Ordered test execution with pytest-order support

Here are some usage examples. 

```
# Run all tutorial tests interactively
python run_tests.py --test tests/tutorial --mode interactive

# Run specific test with range
python run_tests.py --test tests/generic/810_VoxelSpace/test_010_shapes.py --range 1-2 --mode interactive

# Run only a specific test function in a file
python run_tests.py --test tests/specific/110_Trimming/test_010_Trimming.py --function test_020_20180605_Backsub3 --mode interactive

# Batch testing for CI/CD
python run_tests.py --test tests/generic --mode batch

# Save plots for documentation
python run_tests.py --test tests/tutorial --mode save --plot-dir documentation-plots
```
```{note}
**What is CI/CD?**  
CI/CD stands for Continuous Integration and Continuous Deployment (or Delivery). It refers to automated processes that build, test, and deploy code changes, ensuring software quality and rapid delivery.
```

You can use the `--function` argument to run only a specific test function (or method) within a test script. This is especially useful for debugging or developing a single test interactively. The function name should match exactly as defined in the script (e.g., `test_foo` or `TestClass::test_method`).

The matplotlib control modes are summarized below.

| Mode         | Plots Shown | Plots Saved | Use Case                           |
|--------------|-------------|-------------|------------------------------------|
| `batch`      | No          | No          | (Default) Fast automated testing, CI/CD      |
| `save`       | No          | Yes         | Debugging, headless documentation  |
| `interactive`| Yes         | No          | Manual verification, development   |
| `both`       | Yes         | Yes         | Comprehensive testing and archival |

Test script example `example_test.py` is given to implement the above control.

:::{admonition} A note on the python path of this pytest execution
:class: tip

The python path in this execution is ensured to be set as the current repositoy root by the following specification in pyproject.toml with some other settings.

```
[tool.pytest.ini_options]
python_files = ["test_*.py", "*_test.py", "*.py"]
pythonpath = [
  ".",
  "../molass-legacy",
]
env = [
    "MOLASS_ENABLE_PLOTS=false",
    "MOLASS_SAVE_PLOTS=false"
]
filterwarnings = [
    "ignore::SyntaxWarning",
    "ignore::DeprecationWarning",
    "ignore:.*non-interactive.*:UserWarning",
]
```
:::


## Test Coverage

To measure code coverage, use the `--coverage` option with `run_tests.py`, for example:

```
python run_tests.py --test tests/tutorial --coverage
```

This will run the tests and generate an HTML coverage report in the `htmlcov` directory. Open `htmlcov/index.html` in your browser to view detailed coverage results.

### Attribution

Some of the insights and suggestions in this chapter were generated with the assistance of `GitHub Copilot`, an AI programming assistant. Its contributions helped refine the content and provide practical examples for testing workflows.