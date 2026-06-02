# AIMD Tutorial Roadmap

This repo is a publishable Jupyter Book tutorial for ab initio molecular dynamics workflows using VASP, ASE, and pymatgen. It should work as both a useful educational resource and a portfolio artifact that demonstrates practical simulation workflow knowledge.

The goal is not to build a large course. The goal is a compact, credible, runnable tutorial set that a graduate student, postdoc, or technically curious hiring manager can inspect and trust.

## Operating Model

- Track concrete tutorial work in GitHub Issues.
- Keep this file as the product view: audience, milestones, epics, priorities, and task inventory.
- Keep notebooks self-contained where possible.
- Do not ship copyrighted VASP binaries, POTCAR data, or proprietary outputs.
- Use small, curated, license-safe example data for analysis cells.
- Prefer clear explanations and reproducible analysis over research-scale completeness.

## Priority Rubric

- P0: Blocks publication, trust, build/deploy, or basic notebook usability.
- P1: Important MVP tutorial content.
- P2: Useful polish, benchmarking, and portfolio integration.
- P3: Later extensions.

## Size Rubric

- S: One focused file or checklist.
- M: One notebook, audit, or deploy/documentation task.
- L: Cross-notebook work or data/model packaging.
- XL: Split before implementation.

## Current Snapshot - 2026-05-31

- Jupyter Book scaffold exists with `_config.yml`, `_toc.yml`, `intro.md`, and three notebooks.
- Current notebooks:
  - `notebooks/01_bulk_water.ipynb`
  - `notebooks/02_water_on_pt111.ipynb`
  - `notebooks/03_constrained_md.ipynb`
- GitHub Pages workflow exists at `.github/workflows/deploy.yml`.
- `_build/html/` exists locally from a prior build.
- `requirements.txt` pins Jupyter Book, ASE, pymatgen, numpy, scipy, matplotlib, and nglview.
- `data/bulk_water/`, `data/water_pt111/`, and `data/constrained_md/` currently contain only `.gitkeep`.
- The notebooks reference precomputed VASP outputs under `data/...`, so fully runnable analysis is not yet guaranteed.
- No `README.md` exists.
- `AGENTS.md` has external-review TODOs for Matlantis and a Ray Shan LinkedIn post.
- Only unrelated working-tree changes observed before this roadmap were agent-structure files: `CLAUDE.md` symlink state and untracked `AGENTS.md`.

## Product Goals

1. Publishable tutorial: the book builds cleanly and can be deployed to GitHub Pages.
2. Runnable learning path: readers can run analysis cells with small example data or clear fallback instructions.
3. Practical AIMD workflow: notebooks teach setup, execution context, diagnostics, and analysis without pretending to run VASP in-browser.
4. Portfolio value: the tutorial clearly demonstrates scientific computing, AIMD judgment, and communication skill.
5. Maintainable content: future notebook updates have clear acceptance criteria and verification steps.

## Milestones

### M0 - Publishable Scaffold

Goal: make the repo trustworthy as a public tutorial site.

Acceptance:
- `jupyter-book build .` succeeds from a clean environment or blockers are documented.
- GitHub Pages deploy workflow is verified.
- A project README exists with purpose, build command, data policy, and VASP limitations.
- The landing page explains what is runnable locally/Colab versus what requires HPC/VASP.
- No broken public links or obvious placeholder content remain.

### M1 - Runnable Notebook MVP

Goal: each tutorial can be opened and followed without immediate missing-file failures.

Acceptance:
- Each notebook has learning objectives, inputs, expected outputs, and interpretation guidance.
- Analysis cells either run against curated sample data or fail gracefully with clear instructions.
- Data directories contain license-safe sample data, synthetic data, or documented download/generation steps.
- Colab badges open the intended notebooks.
- Notebook outputs and plots are pedagogically useful, not just code scaffolding.

### M2 - Technical Depth and Validation

Goal: make the examples technically credible for AIMD practitioners.

Acceptance:
- Bulk water tutorial includes equilibration diagnostics, RDF, MSD, and diffusion caveats.
- Pt-water tutorial includes slab setup, AIMD settings, density/orientation analysis, and surface-specific caveats.
- Constrained MD tutorial includes window setup, REPORT parsing, mean-force integration, and convergence checks.
- VASP input templates avoid unsafe or misleading defaults.
- Limitations are stated clearly.

### M3 - Portfolio Integration

Goal: make the tutorial discoverable from career-facing materials.

Acceptance:
- Portfolio website links to the tutorial with a short project description.
- README and landing page explain why the tutorial matters.
- Screenshots or figures are suitable for a project showcase.
- The tutorial can be cited or shared in applications/interview follow-up.

### M4 - Maintenance and Extensions

Goal: make future content additions low-risk.

Acceptance:
- Build and link checks are documented.
- Notebook smoke-test strategy is defined.
- External tutorial benchmarking is reviewed and converted into concrete tasks.
- Candidate extension topics are parked as P2/P3 issues rather than added ad hoc.

## Epics

### Build, Deploy, and Docs

Scope:
- Jupyter Book build
- GitHub Pages workflow
- README
- landing page
- repo metadata

Representative tasks:
- P0 S: Verify `jupyter-book build .` on the current repo.
- P0 S: Add a project README.
- P0 S: Verify GitHub Pages deploy settings and expected public URL.
- P0 S: Clarify in `intro.md` what needs VASP/HPC and what runs in Colab.
- P1 S: Add basic troubleshooting for dependency install/build issues.

### Notebook Runnability and Data

Scope:
- `notebooks/*.ipynb`
- `data/`
- Colab execution
- sample trajectories and analysis inputs

Representative tasks:
- P0 M: Audit all notebooks for missing data, runtime failures, and unclear Colab behavior.
- P0 M: Decide sample-data strategy: curated tiny VASP outputs, synthetic mock data, or generation scripts.
- P1 M: Add minimal bulk-water sample data or graceful fallback cells.
- P1 M: Add minimal Pt-water sample data or graceful fallback cells.
- P1 M: Add minimal constrained-MD REPORT samples or graceful fallback cells.
- P1 M: Add a data README with provenance, licensing, and file-size policy.

### AIMD Pedagogy

Scope:
- learning objectives
- explanations
- interpretation sections
- assumptions and caveats

Representative tasks:
- P1 M: Review bulk-water notebook for clarity, caveats, and analysis flow.
- P1 M: Review water-on-Pt(111) notebook for surface-specific interpretation.
- P1 M: Review constrained-MD notebook for Blue-Moon clarity and correctness.
- P1 S: Add a glossary or short prerequisites page if needed.
- P2 M: Add a "common AIMD mistakes" section.

### VASP and HPC Reproducibility

Scope:
- VASP input templates
- HPC workflow guidance
- output collection instructions
- VASP licensing boundaries

Representative tasks:
- P1 M: Audit INCAR/KPOINTS/POSCAR guidance for safe tutorial defaults.
- P1 M: Add a generic HPC run checklist without cluster-specific secrets.
- P1 S: Clarify POTCAR/licensing limitations.
- P2 M: Add sample Slurm script templates if useful.
- P2 S: Add notes on output files needed for each analysis.

### Visualization and UX

Scope:
- static plots
- notebook output readability
- Jupyter Book navigation
- mobile/desktop rendering

Representative tasks:
- P1 M: Verify rendered notebook pages for plot readability and broken widgets.
- P1 S: Replace fragile interactive visualizations with static fallbacks where needed.
- P2 M: Add clean static figures for the landing page or project showcase.
- P2 S: Check headings, anchors, and notebook navigation.

### Benchmarking and External Review

Scope:
- Matlantis tutorial review
- Ray Shan post review
- comparable public tutorial structure

Representative tasks:
- P2 M: Review Matlantis atomistic simulation tutorial and extract useful structure ideas.
- P2 S: Review Ray Shan tutorial-design post if accessible.
- P2 M: Compare this tutorial against 2-3 public AIMD/ASE tutorials and identify gaps.

### Portfolio Integration

Scope:
- `~/Gits/vpasumarthi.github.io/`
- project screenshots
- concise positioning
- external sharing

Representative tasks:
- P1 S: Add or update portfolio website link after the tutorial is publishable.
- P1 S: Add a short shareable description for the project.
- P2 M: Create a project showcase page or screenshot set.
- P2 S: Add a stable citation/share link if the project becomes public.

## Ready-To-Delegate Tasks

### Notebook Runnability Audit

Priority: P0
Size: M
Compute: light agent or build-needed

Goal: determine exactly what prevents each notebook from being runnable by a reader.

Scope:
- `notebooks/01_bulk_water.ipynb`
- `notebooks/02_water_on_pt111.ipynb`
- `notebooks/03_constrained_md.ipynb`
- `data/`
- `_config.yml`
- `_toc.yml`

Acceptance:
- List missing files, cells likely to fail, dependency issues, and Colab-specific problems.
- Separate build-only issues from notebook-execution issues.
- Recommend the smallest sample-data or fallback strategy for each notebook.
- Do not add large data files without explicit approval.

### Publishable Scaffold Checklist

Priority: P0
Size: M
Compute: light agent

Goal: get the repo ready to be shared publicly as a tutorial site.

Scope:
- `README.md`
- `intro.md`
- `_config.yml`
- `.github/workflows/deploy.yml`
- repo metadata assumptions

Acceptance:
- README draft explains purpose, audience, build command, data policy, and VASP limitations.
- Landing page states what can be run locally/Colab and what requires HPC.
- Build/deploy path is verified or blockers are listed.
- No public-facing placeholder docs remain.

### Sample Data Strategy

Priority: P0
Size: M
Compute: light agent

Goal: decide how the tutorial should support runnable analysis without shipping problematic or huge files.

Scope:
- `data/bulk_water/`
- `data/water_pt111/`
- `data/constrained_md/`
- notebook file expectations

Acceptance:
- Propose a per-notebook sample-data plan.
- Identify whether each dataset should be real curated output, synthetic pedagogical output, or generated in-notebook.
- Include file-size and licensing constraints.
- Identify follow-up implementation tasks.

### Technical Validation Pass

Priority: P1
Size: L
Compute: expert review

Goal: review scientific correctness and caveats before sharing broadly.

Scope:
- all notebooks
- VASP templates
- analysis formulas
- interpretation text

Acceptance:
- Flag technically risky statements or defaults.
- Check RDF, MSD, density-profile, orientation, and Blue-Moon analysis assumptions.
- Recommend corrections with minimal scope.
- Do not expand the tutorial beyond the three current examples unless necessary.

## Initial Issue Seeds

1. P0 M: Notebook runnability audit.
2. P0 M: Publishable scaffold checklist.
3. P0 M: Sample data strategy.
4. P0 S: Add project README.
5. P0 S: Verify `jupyter-book build .` and GitHub Pages deploy assumptions.
6. P1 M: Bulk-water notebook completion pass.
7. P1 M: Water-on-Pt(111) notebook completion pass.
8. P1 M: Constrained-MD notebook completion pass.
9. P1 M: Add data provenance and licensing notes.
10. P1 S: Add portfolio website link once publishable.
11. P2 M: Review Matlantis tutorial for useful structure ideas.
12. P2 S: Review Ray Shan tutorial-design post if accessible.

## Recommended Next Task

Start with **Notebook Runnability Audit**. The site can build with notebook execution disabled, but a reader who opens the notebooks will likely hit missing `data/...` files unless sample data or graceful fallback behavior is added.
