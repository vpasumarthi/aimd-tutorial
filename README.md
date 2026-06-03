# Ab Initio Molecular Dynamics Tutorial

A hands-on tutorial for setting up, running, and analyzing ab initio molecular
dynamics (AIMD) simulations with VASP, ASE, and pymatgen. It is built with
Jupyter Book and published to GitHub Pages.

**Live site:** https://vpasumarthi.github.io/aimd-tutorial/

## What it covers

Three self-contained tutorials, each pairing VASP input templates (for running
on HPC) with Python analysis of precomputed trajectory data:

1. **Bulk liquid water** (`notebooks/01_bulk_water.ipynb`): NVT AIMD of 32 H2O,
   radial distribution functions, mean squared displacement, and the
   self-diffusion coefficient.
2. **Water on Pt(111)** (`notebooks/02_water_on_pt111.ipynb`): metal-water slab
   setup with pymatgen, water density profiles, and molecular orientation
   analysis near the surface.
3. **Constrained MD / Blue-Moon ensemble** (`notebooks/03_constrained_md.ipynb`):
   free energy profiles along a reaction coordinate via constrained AIMD and
   thermodynamic integration.

## What needs VASP/HPC vs. Colab/local

The AIMD simulations themselves run with VASP on an HPC cluster. Everything else
(structure setup and all trajectory analysis) runs in Google Colab or locally
with the Python stack in `requirements.txt`. See the landing page (`intro.md`)
for the full breakdown. The analysis cells read precomputed VASP outputs from
`data/`; supply your own from your runs.

## Build locally

```bash
# 1. Install dependencies (Python 3.11 or newer)
pip install -r requirements.txt

# 2. Build the book
jupyter-book build .

# 3. Open the rendered site
open _build/html/index.html
```

To check links:

```bash
jupyter-book build . --builder linkcheck
```

## Deployment

Pushes to `main` trigger the GitHub Actions workflow in
`.github/workflows/deploy.yml`, which builds the book and publishes
`_build/html` to GitHub Pages at the live site URL above.

## Data and VASP notes

- VASP is licensed software and is not run in the notebooks or in Colab. The
  notebooks provide INCAR, KPOINTS, POSCAR, POTCAR, and (for constrained MD)
  ICONST templates for running on your own cluster.
- No VASP binaries, POTCAR data, or proprietary outputs are shipped.
- The `data/` directories hold placeholders. Copy the relevant VASP outputs
  (`XDATCAR`, `OSZICAR`, `REPORT`) from your runs into `data/<system>/` before
  running the analysis cells.
