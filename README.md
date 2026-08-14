# Clarkson-Shor Random Sampling Methods in Lean 4

[![CI](https://img.shields.io/github/actions/workflow/status/OliverNicolau/clarkson-shor-lean/lean_action_ci.yml?branch=main)](https://github.com/OliverNicolau/clarkson-shor-lean/actions)
[![Docs](https://img.shields.io/badge/docs-blue.svg)](https://OliverNicolau.github.io/clarkson-shor-lean/blueprint/)
[![License](https://img.shields.io/github/license/OliverNicolau/clarkson-shor-lean.svg)](LICENSE)

A Lean 4 / mathlib formalization of Clarkson & Shor’s random sampling technique, focusing on Lemma 2.1 and Theorem 3.1 in [Clarkson & Shor (1989)](https://link.springer.com/article/10.1007/BF02187740).

## Overview

The Clarkson–Shor technique is a cornerstone of random incremental algorithms in computational geometry and many bounds in combinatorial geometry. This project’s first goal is to formalize **Lemma 2.1** and **Theorem 3.1** from the original paper.

## Documentation

We use the ubiquitous [`leanblueprint`](https://github.com/PatrickMassot/leanblueprint):

- **[Blueprint (HTML)](https://OliverNicolau.github.io/clarkson-shor-lean/blueprint/)** — Interactive web version with dependency graph
- **[Blueprint PDF](https://OliverNicolau.github.io/clarkson-shor-lean/blueprint.pdf)** — Printable reference
- **[API Docs](https://OliverNicolau.github.io/clarkson-shor-lean/docs/)** — Auto-generated Lean docs

## Quick Start

### Prerequisites
- `elan` (recommended) to manage Lean toolchains
- **Lean 4.33.0**
- **Lake** (comes with Lean)

### Installation (recommended)

```bash
# Install elan (if not installed)
curl -sL https://raw.githubusercontent.com/leanprover/elan/master/elan-init.sh | sh

# Install and select the pinned toolchain
elan toolchain install 4.33.0
elan default 4.33.0

# Fetch dependencies and build the project
lake update
lake build
```

## Related Work

- **Clarkson & Shor (1989):** "Applications of Random Sampling in Computational Geometry, II"
- **Mulmuley (1994):** "Computational Geometry: An Introduction Through Randomized Algorithms"
- **Sharir (2003):** "The Clarkson--Shor Technique Revisited and Extended"
- **Har-Peled (2011):** "Geometric Approximation Algorithms"
- **Bae, Oliver, Papadopoulou (2025):** "Higher-Order Color Voronoi Diagrams and the Colorful Clarkson-Shor Framework"

## License

Apache License 2.0 — see [LICENSE](LICENSE)
