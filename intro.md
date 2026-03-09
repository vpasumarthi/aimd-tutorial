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

## Getting started

Browse the tutorials in the sidebar, or open any notebook directly in Google Colab. Each tutorial includes VASP input file templates (for running on HPC) and analysis code that works on pre-computed trajectory data.
