# Documentation

```{warning}
This page is in preparation to be publicly available in April, 2025.
```

## Jupyter Book

### Tool Package Installation

```
pip install -U jupyter-book
pip install -U ghp-import
```

### Create Template Book

    ・ jupyter-book create book-for-repo
    ・ create a repository on GitHub
    ・ git clone book-repo
    ・ copy the contents of book-for-repo to book-repo

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

## SPhinx

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