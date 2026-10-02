# CSE 401 Numerical Analysis and Simulation Assignment

**Student:** Jonayed Mohiuddin

**Student ID:** 2105060

**Assigned topic:** Golden-Section Search

The topic allocation is correct:

\[
(060 \bmod 15)+1=1,
\]

and Topic 1 is Golden-Section Search.

## Required deliverables

- `2105060.pdf` — compiled LaTeX Beamer slide deck
- `2105060_LaTeX_Source.zip` — the `.tex` source and every required asset

The work is being developed in small, reviewable stages. The content and slide
sequence are specified in [`docs/assignment_blueprint.md`](docs/assignment_blueprint.md).

## Build command (once the deck source is added)

```powershell
latexmk -pdf -interaction=nonstopmode -halt-on-error 2105060.tex
```

The final archive must not contain LaTeX build by-products.
