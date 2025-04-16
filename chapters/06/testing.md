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

Depending on the category, used data will vary as shown below.

:::{table} Data Usage depending on Test Category
:widths: auto
:align: center

| Data Name / test folder| generic tests usage | specific tests usage |
| :---             |:---:|:---:|
| ORIGINAL_DATA    | Yes | Yes |
| TUTORIAL_DATA    | Yes | Yes |
| DATA_ROOT_FOLDER | No  | Yes |
| test folder      | tests/generic | tests/specific |
:::

The data names above are partly the same as those referenced in [Local Settings](https://nshimizu0721.github.io/molass-tutorial/chapters/00/prepare.html#local-settings) of the [Tutorial](https://nshimizu0721.github.io/molass-tutorial/), the locations of which you should specify in the `local_settings.py` script as stated there. It would look something like the following code.

```python
LocalSettings = dict(
    TUTORIAL_DATA=r"D:\MolassData\tutorial_data",
    ORIGINAL_DATA=r"D:\MolassData\original_data",
    DATA_ROOT_FOLDER=r"D:\AllExperimentData",
)
```

Data sets for `DATA_ROOT_FOLDER` is currently not provided for download from the book pages. Let us know by opening an issue using the ![github icon](../../images/github.svg) button at upper right corner of this page.

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
  "."
]
```
:::

For detailed tests coverage, execute as follows:

```
pytest --cov=molass --cov-report=html
```

and check the results in `test_folder/htmlcov/index.html` with your browser, where `test_folder` is one of `tests/generic`, `tests/specific` or `tests` depending on how you ran the tests.