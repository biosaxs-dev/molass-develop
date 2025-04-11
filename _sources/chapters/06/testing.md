# Testing Conventions

## Test Tools

We use pytest with coverage reports. Install the following packages for testing.

```
pip install -U pytest
pip install -U pytest-cov
```

## Test Scripts Naming and Locations

Test scripts should be named and placed like suggested in the following way.

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

The generic folder should be kept relatively simple by excluding site-specific tests such as "FlowChange", which arises only from unique experiment practice at some SAXS beamlines in Photon Factory, Japan and often includes complex issues irrelevant to generic cases.

```{note}
Three-digit numbers are just for ordering in the following sense.
* ease for glancing over roughly in created (or logical) order
* order of test execution

```

## Running Tests

To run the tests, do as follows in command prompt:

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

and check the results in `tests/htmlcov/index.html` with your browser.