<!-- AI Context Standard v0.8 - Adopted: 2026-03-25 -->
# AI Assistant Initialization Guide — molass-develop

**Purpose**: Initialize AI context for working in this repository  
**Created**: March 24, 2026

---

## What this repository is about

This repository holds the Jupyter Book source for the [Molass Developer's Handbook](https://biosaxs-dev.github.io/molass-develop/) web book — guidance for collaborators and contributors to the molass project.

---

## Repository-specific conventions

- **Format**: [MyST Markdown syntax](https://jupyterbook.org/en/stable/reference/cheatsheet.html) is used throughout unless otherwise stated
- **Build tool**: Jupyter Book
- **Audience**: Developers and contributors to the molass ecosystem

---

## Repository structure

```
molass-develop/
├── .github/
│   └── copilot-instructions.md  ← this file (auto-loaded by GitHub Copilot)
├── _config.yml
├── _toc.yml
├── chapters/
│   ├── intro.md
│   ├── COPILOT_CONTEXT.md  ← book chapter on AI-assisted development practices
│   ├── 01/ … 12/           ← handbook chapters
└── _build/html/            ← built output
```

---

## Multi-root workspace context

| Repository | Role | Tool |
|------------|------|------|
| `molass-library` | Main library (Python source) | Python / Sphinx |
| `molass-legacy` | Legacy GUI predecessor; required runtime dep | Python / Sphinx |
| `modeling-vs-model_free` | Research: decomposition criteria | Markdown / Notebooks |
| `molass-tutorial` | Usage documentation | Jupyter Book / MyST |
| `molass-essence` | Theory documentation | Jupyter Book / MyST |
| `molass-technical` | Technical report | Jupyter Book / MyST |
| `molass-develop` | **This repo**: developer handbook | Jupyter Book / MyST |
| `molass-beginner` | Beginner onboarding (Agent mode) | Markdown |

---

## Building the book

```bash
jupyter-book build .
```

Output goes to `_build/html/`.

---

## 🔄 Updates

**Latest**: March 25, 2026 — Updated to AI Context Standard v0.8; added `init.prompt.md` and `vscode-version.txt`  
**Previous**: March 24, 2026 — Created `.github/copilot-instructions.md` (AI Context Standard v0.7)
