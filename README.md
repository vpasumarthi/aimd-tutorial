# Ab Initio Molecular Dynamics (AIMD) Tutorial

This repository contains an interactive tutorial for learning how to set up, execute, and analyze Ab Initio Molecular Dynamics (AIMD) simulations using VASP, ASE, and pymatgen.

The tutorial is built as a [Jupyter Book](https://jupyterbook.org/) and is designed to be accessible for graduate students and postdocs starting with AIMD.

## Tutorials

The book is organized into three main modules:

1. **Bulk Liquid Water** -- Setup and analysis of NVT AIMD for liquid water.
2. **Water on Pt(111)** -- Interfacial MD of water on a metal surface, including density profiles and molecular orientation analysis.
3. **Constrained MD / Blue-Moon Ensemble** -- Free energy sampling and thermodynamic integration for chemical reactions.

## Installation

To build the book locally or run the analysis notebooks, install the required dependencies:

```bash
pip install -r requirements.txt
```

## Building the Book

To generate the static HTML version of the tutorial:

```bash
jupyter-book build .
```

The output will be available in `_build/html/index.html`.

## Repository Structure

- `notebooks/`: Interactive Jupyter notebooks containing the tutorial content and analysis code.
- `data/`: Curated example VASP output files (XDATCAR, OSZICAR, etc.) for analysis.
- `figures/`: Static figures used in the documentation.
- `_config.yml`: Jupyter Book configuration.
- `_toc.yml`: Table of contents for the book.
- `intro.md`: Landing page content.
- `CLAUDE.md`: Development guidelines and preferences.

## License

This project is intended for pedagogical purposes.
