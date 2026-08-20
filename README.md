# Kidney Exchange Programs under Novel HLA Compatibility Paradigms

Code and computational results accompanying the paper:

> **Maximizing Effectiveness and Equity in Kidney Exchange Programs for Novel Compatibility Paradigms.**
> Valentina Peralta Clarke, Hans de Ferrante, Francisco Pérez-Galarce, Joris van de Klundert.

The study builds a realistic Kidney Exchange Program (KEP) from real-life data and simulates KEP
optimization under three HLA compatibility paradigms — antigen, allele, and eplet based —
to compare KEP effectiveness and equity across ethnic subpopulations, and proposes equity-weighted
optimization models that reduce ethnic inequities without sacrificing access to transplant.

This repository holds the complete computational analysis (code + result tables) referenced in the paper.

## Repository structure

```
code/
  ABO+DSA/            # "plain" compatibility graph (ABO + DSA, no HLA-mismatch threshold)
                      #   sim + equity search, 10 / 6 / 4 loci
  ABO+DSA+HLA/        # "threshold" compatibility graph (ABO + DSA + HLA mismatch threshold)
                      #   sim + equity search, 10 / 6 / 4 loci
  supplementary/      # extra experiments: balanced-data, Caucasian-only, transplant bounds,
                      #   departure-rate sensitivity
results/              # all result tables (.xlsx): baseline, equity, sensitivity, per loci set
```

Each simulation notebook runs 100 imputed pools over a 10-year horizon (first 5 years are warm-up)
and writes result tables to `results/`. The integer programs are solved with Gurobi.

## Environment

- Python 3.13.5
- Gurobi 12.0.3 (a valid Gurobi license is required)

```bash
pip install -r requirements.txt
```

## Data availability

The case study is built from the OPTN/UNOS star file, obtained under a Data Sharing Agreement.
The patient-level data — and the imputed recipient/donor pools and mismatch matrices derived from it —
cannot be redistributed and are therefore not included in this repository (see `.gitignore`).

The data are available directly from OPTN/UNOS under their data request process. Once obtained, point the
code at your local copy:

```bash
export KEP_DATA_DIR=/path/to/your/data      # holds pool_simulations/, pool_matrices/, and the imputed CSVs
```

The imputed recipient/donor pools and the precomputed mismatch matrices (including eplet mismatch,
computed following the HLA Eplet Registry definitions) are derived from the protected HLA typings and
are therefore not included, and neither are the data-preparation notebooks that operate on individual
patient records.

## License

Code released under the MIT License (see `LICENSE`). 
