# Documentation

```{warning}
This page is in preparation to be publicly available in May, 2025.
```

## Documents to be maintained

We have the following documents, including this book, to maintain.

|No |   Book Name           | Book License | Used Tool |
|:-:|:--------------------------|:--------|:-----------|
| 1 |[Molass Legacy Reference](https://freesemt.github.io/molass-legacy/) |GPL-3.0 |Sphinx |
| 2 |[Molass Libray Reference](https://freesemt.github.io/molass-library/)|GPL-3.0 |Sphinx |
| 3 |[Molass Libray Essence](https://freesemt.github.io/molass-essence/)  |CC BY 4.0|Jupyter Book|
| 4 |[Molass Libray Tutorial](https://freesemt.github.io/molass-tutorial/)|CC BY 4.0|Jupyter Book|
| 5 |[Molass Developer's Handbook](https://freesemt.github.io/molass-develop/)|CC BY 4.0|Jupyter Book|

For the first two reference books, we use [Sphinx](https://github.com/sphinx-doc/sphinx) directly to generate function documents from their [docstrings](https://peps.python.org/pep-0257/). For others, [Jupyter Book](https://github.com/jupyter-book/jupyter-book), which depends on Sphinx, is used.

## How to use Jupyter Book

```{note}
Do not confuse "Jupyter Notebook" and "Jupyter Book". The former is a file for programming, while the latter is a tool for publishing.
```

### Tool Package Installation

To use Jupyter Book, you need to install the following two packages.

```
pip install -U jupyter-book
pip install -U ghp-import
```

### Initial Book

Each initial book was created as follows.

    ・ jupyter-book create example-repo
    ・ create an empty repository for book-repo on GitHub
    ・ git clone book-repo
    ・ copy the contents of example-repo to book-repo

```{note}
You need this procedure only when you create a new book.
```

### Manual Book Edit

When you edit the source files manually, first files to be attended are the following two.

    ・ _config.yml
    ・ _toc.yml

These files are usually placed either at the root of the repository or a sub folder named like "docs". Compare them with those of an existing book you already know, then you should begin to know which source file to edit. To edit the source file, which is either a markdown text file like "coding_style.md" or a Jupyter notebook like "prepare.ipynb", you should be well acquainted on the syntax summarized in [MyST syntax cheat sheet](https://jupyterbook.org/en/stable/reference/cheatsheet.html).

```{note}
Syntaxes of markdown texts differ slightly denending on the tools they are processed with. Be sure to follow the `MyST syntax` here. On the other hand for GitHub texts like `README.md`, follow [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).
```

See also as you proceed:

* [Create your first book](https://jupyterbook.org/en/stable/start/your-first-book)
* [MyST syntax cheat sheet](https://jupyterbook.org/en/stable/reference/cheatsheet.html)

### Book Update Cycle

We repeat the following cycle to update, brief descriptions of which will follow below.

    ・ edit manually
    ・ generate locally
    ・ synchronize master branch
    ・ deploy gh-pages branch

```{note}
For maintenance of the web page, the two branches, namely master and gh-pages, are involved. The former keeps the source and the latter the generated target.
```

After manual edit, local generation should be achieved as follows in Command Prompt:

```none
cd book-repo
jupyter-book build .
```

After generation, check the generated local output in _build/html with the browser. Re-edit as needed until you are satisfied.

Synchronization of the master branches, local and remote, should be achieved as follows in VS Code:

    ・ commit in VS Code
    ・ synchronize with GitHub in VS Code

(Re)creation and synchronization of the gh-pages branches, local and remote, should be achienved as follows in Command Prompt:

```none
ghp-import -n -p -f _build/html
```

The web page will be updated in a few minutes, as a result of automatic deployment of GitHub Pages.
If you are interested in details of this step, see the [README](https://github.com/c-w/ghp-import) of ghp-import.

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

The web page will be updated in a few minutes.