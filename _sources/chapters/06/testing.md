# Testing Conventions

## Test Tools

We use pytest with coverage reports. Install the following packages for testing.

```
pip install -U pytest
pip install -U pytest-cov
```

## Test Scripts Organizing

Test scripts should be named and placed as suggested in the following way.

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

```

One reason for dividing tests into the two categories, namely "generic" and "specific", is as follows.

The generic folder should be kept relatively simple by excluding site-specific tests such as "FlowChange", which arises only from unique experiment practice at some SAXS beamlines in [Photon Factory](https://www2.kek.jp/imss/pf/eng/), Japan and often includes complex issues irrelevant to generic cases.

```{note}
Three-digit numbers are just for ordering in the following sense.
* ease for glancing over roughly in created (or logical) order
* order of test execution

```

## Running Tests
### Test Data Settings

Since we have introduced data package `molass_data` for the [Tutorial](https://molass-saxs.github.io/molass-tutorial/), we also use those data sets for basic tests.
Depending on the category, used data will vary as shown below.

:::{table} Data Usage depending on Test Category
:widths: auto
:align: center

| Data Name / test folder| generic test usage | specific test usage |
| :---             |:---:|:---:|
| SAMPLE1    | Yes | No |
| SAMPLE2    | Yes | No |
| SAMPLE3    | Yes | No |
| SAMPLE4    | Yes | No |
| DATA_ROOT_FOLDER | No  | Yes |
| test folder      | tests/generic | tests/specific |
:::

The data sets named `SAMPLE*` are included in the data package `molass_data`. For specific tests, prepare `local_settings.py` like shown below, as explained at [Local](https://molass-saxs.github.io/molass-library/source/molass.Local.html) module reference.

```python
LocalSettings = dict(
    DATA_ROOT_FOLDER=r"D:\AllExperimentData",
)
```

Data sets for `DATA_ROOT_FOLDER` is currently not provided for download. If you need them, let us know by opening an issue using the ![github icon](../../images/mark-github.svg) button at upper right corner of this page.

### Command Lines
To run generic tests only, do as follows in command prompt:

```
cd tests/generic
pytest --cov=molass
```

To run specic tests only, do as follows in command prompt:

```
cd tests/specific
pytest --cov=molass
```

To run all tests, do as follows in command prompt:

```
cd tests
pytest --cov=molass
```

:::{admonition} A note on the python path of this pytest execution
:class: tip

The python path in this execution is ensured to be set as the current repositoy root by the following specification in pyproject.toml.

```
[tool.pytest.ini_options]
pythonpath = [
  ".",
  "../molass-legacy",  
]
```
:::

For detailed tests coverage, execute as follows:

```
pytest --cov=molass --cov-report=html
```

and check the results in `test_folder/htmlcov/index.html` with your browser, where `test_folder` is one of `tests/generic`, `tests/specific` or `tests` depending on how you ran the tests.

### Efficient Testing During Development

When developing new features, running all tests can be time-consuming. For quick checks, you can simply run a specific test file or function using pytest. For example:

```
pytest path/to/test_file.py
pytest path/to/test_file.py::test_function_name
```

More broadly, you can ask `GitHub Copilot`:

"I use pytest to run all tests, which is great for checking overall software quality. But when developing a new feature, I need quick checks for specific parts of the code. Any advice on how to do this efficiently?"

### Matplotlib Control for Testing

Note the following requirements when running tests that generate matplotlib plots:
- **Interactive mode** is needed for manual inspection and verification
- **Batch mode** is required for automated testing, CI/CD pipelines, and headless environments
- **Saving plots** is useful for debugging and documentation purposes

To address these conflicting requirements, utility script `run_tests.py` is provided which offers four distinct modes to handle matplotlib figures:

| Mode         | Plots Shown | Plots Saved | Use Case                           |
|--------------|-------------|-------------|------------------------------------|
| `batch`      | No          | No          | Fast automated testing, CI/CD      |
| `save`       | No          | Yes         | Debugging, headless documentation  |
| `interactive`| Yes         | No          | Manual verification, development   |
| `both`       | Yes         | Yes         | Comprehensive testing and archival |

Usage syntax is as follows.

```
python run_tests.py [--mode MODE] [--test TEST_PATH] [--plot-dir PLOT_DIR]
```

Examples:

* Run all tests in batch mode (default):

```
python run_tests.py
```

* Test specific folder with interactive plots:

```
python run_tests.py --mode interactive --test tests/generic/
```

Test script example `example_test.py` is given to implement the above control.

### Attribution

Some of the insights and suggestions in this chapter were generated with the assistance of `GitHub Copilot`, an AI programming assistant. Its contributions helped refine the content and provide practical examples for testing workflows.