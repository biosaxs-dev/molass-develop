# Git Environment

## GitHub

If not yet, create an account at <a href="https://github.com/signup">Sign up to GitHub</a>.

## Git

If not yet, install git with "64-bit Git for Windows Setup" from <a href="https://git-scm.com/downloads/win">Download for Windows</a>.

And set your account info as like follows.

```none
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

See also:
* <a href="https://code.visualstudio.com/docs/sourcecontrol/overview">Using Git source control in VS Code</a>

## Git Large File Storage

For large files larger than 50MB, it is recommended to use Git Large File Storage (LFS). 

### Install Git LFS

This install command, which sets up Git LFS hooks globally, needs to be run once per machine.

```none
git lfs install
```

The following steps are required to track files in a repository.

### Track Settings

Add track info in Command Prompt:

```none
git lfs track "sec_simulation.ipynb"
```

```none
git add .gitattributes
git add chapters\81\sec_simulation.ipynb
```

Synchronize in Command Prompt:

```none
git commit -m "Track sec_simulation.ipynb with Git LFS"
git push origin main
```

Or do it in VS Code.