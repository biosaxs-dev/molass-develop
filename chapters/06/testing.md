# Testing Convention

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
        010_DataObjects/
            test_010_SSD.py
            test_020_Curve.py
            ...
        020_DataUtils/
            ...
        
```

## Running Tests

To run the tests, do as follows in command prompt:

```
cd tests
pytest --cov=molass
```

:::{admonition} A note on the python path of this pytest execution
:class: tip

The python path in this execution is ensured to be set as the current repositoy root by the following setting in pyproject.toml.

```none
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