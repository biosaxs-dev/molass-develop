# Documentation

```{warning}
This page is in preparation to be publicly available in April, 2025.
```

## Documents to be maintained

We have the following documents to maintain.

|No |   Document Name           |    Tool    |
|:-:|:--------------------------|:-----------|
| 1 |[Molass Legacy Reference](https://freesemt.github.io/molass-legacy/)|Sphinx      |
| 2 |[Molass Libray Reference](https://freesemt.github.io/molass-library/)|Sphinx      |
| 3 |[Molass Libray Essense](https://freesemt.github.io/molass-essense/)      |Jupyter Book|
| 4 |[Molass Libray Tutorial](https://freesemt.github.io/molass-tutorial/)     |Jupyter Book|
| 5 |[Molass Developpers Handbook](https://freesemt.github.io/molass-develop/)|Jupyter Book|

For the first two reference books, we use [Sphinx](https://github.com/sphinx-doc/sphinx) directly to generate function documents from their docstrings. For others, [Jupyter Book](https://github.com/jupyter-book/jupyter-book) is used.

## How to use Jupyter Book

### Tool Package Installation

We use the following two packages.

```
pip install -U jupyter-book
pip install -U ghp-import
```

### Create Template Book

    ・ jupyter-book create template-repo
    ・ create a repository on GitHub
    ・ git clone book-repo
    ・ copy the contents of template-repo to book-repo

### Edit Manually


### Deployment

```none
cd book-repo
jupyter-book build .
```

    ・ commit in VS Code
    ・ sync with GitHub in VS Code

```none
ghp-import -n -p -f _build/html
```

## How to use Sphinx

### Tool Package Installation

```none
pip install sphinx~=7.0 
pip install sphinx-book-theme
```

### Gererate Function Documents

At the repository root:

```none
mkdir docs
sphinx-apidoc --output-dir docs molass --separate
```

### Edit Manually



### Deployment

At docs:

```none
make html
ghp-import -n -p -f _build/html
```