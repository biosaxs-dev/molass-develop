# Package Release

```{warning}
This page is in preparation to be publicly available in May, 2025.
```

## PyPI Account



## PyPI API Token



## PyPI Upload

### Using the GitHub Actions

1. Go to the `"Actions"` tab in the [Molass Library repository](https://github.com/nshimizu0721/molass-library).
2. Select `"Manual Upload Python Package to PyPI"` workflow.
3. Click the `"Run workflow"` button.

### Using Twine
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