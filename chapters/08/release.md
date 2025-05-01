# Package Release

```{warning}
This page is in preparation to be publicly available in May, 2025.
```

## PyPI Account


## PyPI API Token


## PyPI Upload [^1]

[^1]: This step is planned to be automated using GitHub Actions.

To build required files, do as follows in the repository root folder.

```none
python -m build
```

which produces the files in "dist" subfolder.

To upload them to PyPI, you will be asked to give an API token [^2] to the twine command invoked as follows.

```none
twine upload dist/*
```

[^2]: The API token should be kept safely somewhere.

See also:
* <a href="https://twine.readthedocs.io/en/stable/">Twine</a>