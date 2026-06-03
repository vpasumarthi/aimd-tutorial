# Ab Initio Molecular Dynamics Tutorial

A hands-on guide to setting up, running, and analyzing AIMD simulations using VASP, ASE, and pymatgen.

## Tutorials

1. **Bulk Liquid Water** -- Set up NVT AIMD for 32 H₂O, then compute radial distribution functions, mean squared displacement, and the self-diffusion coefficient.
2. **Water on Pt(111)** -- Build a metal-water slab model, run AIMD at the interface, and analyze water density profiles and molecular orientations near the surface.
3. **Constrained MD / Blue-Moon Ensemble** -- Map free energy profiles along a reaction coordinate using constrained AIMD and thermodynamic integration.

## Prerequisites

- Familiarity with DFT and VASP
- Basic Python (NumPy, Matplotlib)
- Access to an HPC cluster for running VASP

## What needs VASP/HPC vs. what runs in Colab/local

The actual AIMD simulations run with VASP, which is licensed software meant for an HPC cluster. The notebooks never run VASP in the browser or in Colab. Everything else (structure setup and trajectory analysis) runs in Google Colab or locally with the Python stack in `requirements.txt` (ASE, pymatgen, NumPy, SciPy, Matplotlib, nglview).

**Requires VASP on HPC:**
- Running the AIMD itself to produce the trajectory and output files (`XDATCAR`, `OSZICAR`, and, for constrained MD, `REPORT`). Each notebook provides the VASP input templates for this step: INCAR, KPOINTS, POSCAR, and POTCAR, plus an ICONST file for the constrained-MD example.

**Runs in Colab or locally (no VASP):**
- Structure setup, such as building the Pt(111) slab with pymatgen in Tutorial 2.
- All trajectory analysis and plotting: radial distribution functions, mean squared displacement, and diffusion (Tutorial 1); density profiles and water orientation (Tutorial 2); and Blue-Moon mean-force integration and convergence checks (Tutorial 3).

The analysis cells read precomputed VASP outputs from the `data/` directories. The repository ships these directories as placeholders, so copy the relevant outputs from your own runs into `data/<system>/` before running the analysis cells.

## Getting started

Browse the tutorials in the sidebar, or open any notebook directly in Google Colab. Each tutorial includes VASP input file templates (for running on HPC) and analysis code that works on pre-computed trajectory data.
