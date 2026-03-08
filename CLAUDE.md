# AIMD Tutorial

Interactive tutorial site for ab initio molecular dynamics simulations, built with Jupyter Book and deployed to GitHub Pages.

## Purpose

Pedagogical resource for graduate students and postdocs starting AIMD. Covers setup, execution, and analysis of AIMD simulations using VASP, ASE, and pymatgen. Designed to be:
- Self-contained with clean, minimal example systems
- Runnable via Google Colab (analysis notebooks) or HPC (VASP runs)
- Linked from portfolio website (vpasumarthi.github.io)

## Tech Stack

- **Jupyter Book** for site generation
- **GitHub Pages** for hosting (via GitHub Actions)
- **Jupyter notebooks** (.ipynb) for interactive tutorials
- **VASP** for AIMD calculations (input files provided, not run in notebooks)
- **ASE** + **pymatgen** for structure setup and trajectory analysis
- **Matplotlib** for visualization

## Build Commands

```bash
# Install dependencies
pip install -r requirements.txt

# Build the book
jupyter-book build .

# Local preview
open _build/html/index.html
```

## Repo Structure

```
aimd-tutorial/
├── _config.yml              # Jupyter Book config
├── _toc.yml                 # Table of contents
├── intro.md                 # Landing page
├── notebooks/               # Tutorial notebooks
├── data/                    # Example VASP outputs (small, curated)
├── figures/                 # Static figures
├── requirements.txt         # Python dependencies
├── .github/workflows/       # GitHub Actions for Pages deployment
└── CLAUDE.md
```

## Content Guidelines

- Each notebook should be self-contained with clear learning objectives
- VASP input files are provided as templates; actual AIMD runs happen on HPC, not in notebooks
- Analysis notebooks work with pre-computed trajectory data shipped in `data/`
- Keep example systems small and clean — pedagogical clarity over research complexity
- Use ASE for trajectory I/O and analysis; pymatgen for structure setup and VASP I/O
- All visualizations should be publication-quality matplotlib (no interactive widgets that break in static builds)

## Preferences

- No em dashes in writing
- Keep explanations concise and practical
- Code cells should have comments explaining the "why," not just the "what"
