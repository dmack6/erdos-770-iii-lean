# Lean-checked arithmetic reduction for Erdős Problem 770(iii)

This repository accompanies Dillon MacKenzie's preprint [The large-prime threshold in Erdős Problem 770(iii)](https://doi.org/10.5281/zenodo.24409350).

## Reproduce the check

Install [Lean via elan](https://lean-lang.org/install/). From this directory, run:

```sh
lean --version
lean Erdos770.lean
```

The pinned toolchain is Lean 4.19.0. The file imports only core Lean. Its final command reports the axioms of `Erdos770Reduction.threshold`: `propext`, `Classical.choice`, and `Quot.sound`.

## What the theorem checks

For a positive integer `n` and the largest prime `p` with `p - 1 ∣ n`, the theorem concludes that `p` is the first cutoff at which the collective gcd of the values `a^n - 1` is one. It takes four inputs:

- Fermat's congruence for bases from 2 through `p - 1`.
- A small primitive root for each prime `r` with `p < r ≤ n^2`.
- A supply of more than `n` distinct products of small factors, each at most `n^2`.
- The degree bound for the number of roots over a prime field.

The preprint supplies the paper argument connecting these inputs to the eventual statement for every positive exponent, using a least prime primitive root bound under Dirichlet GRH. The Lean theorem formalizes the arithmetic deduction from the listed inputs. See the preprint for citations and acknowledgments, including Samuel Korsky's earlier GRH implication.
