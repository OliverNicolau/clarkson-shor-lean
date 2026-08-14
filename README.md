# Clarkson-Shor Random Sampling Methods in Lean 4

A formal verification project formalizing the **Clarkson-Shor random sampling techniques** (Clarkson & Shor, 1989) in Lean 4 using Mathlib.

## Overview

The Clarkson-Shor technique is a cornerstone of computational and combinatorial geometry, enabling elegant algorithmic solutions through random sampling. This project formalizes the main combinatorial lemma and theorems from the original paper:

- **Lemma 2.1** (Probability of Zero Weight)
- **Theorem 3.1** (Clarkson-Shor Main Lemma / Exact Discrete Double-Counting Identity)

The formalization combines two parallel workflows:
1. **Lean 4 formal proofs** (`ClarksonShor/Main.lean`)
2. **Mathematical blueprint** (`blueprint/src/content.tex`) — hand-written proofs with automatic code/proof linking

## Documentation

- 📄 **[Blueprint (HTML)](https://OliverNicolau.github.io/clarkson-shor-lean/blueprint/)** — Interactive web version with dependency graph
- 📕 **[Blueprint PDF](https://OliverNicolau.github.io/clarkson-shor-lean/blueprint.pdf)** — Printable mathematical reference
- 📚 **[API Docs](https://OliverNicolau.github.io/clarkson-shor-lean/docs/)** — Generated Lean documentation

## Quick Start

### Prerequisites
- **Lean 4.33.0** (or use `elan` to auto-download)
- **Lake** (comes with Lean)

### Build

```bash
lake build
```

This compiles all Lean files and checks the formalization.

### View Documentation Locally

```bash
# Requires latex, plasTeX, and Ruby (see dependencies below)
cd blueprint/src
latexmk -pdf print.tex              # Generate PDF → ../print/print.pdf
plasTeX content.tex                 # Generate HTML → ../web/
```

Then open `blueprint/web/content.html` in your browser.

## Project Status

### Proof Completion

| Lemma/Theorem | Status | Lean File | Blueprint |
|---------------|--------|-----------|-----------|
| Def: CS-structure | ✅ Sketched | `Main.lean` line 14–22 | § 1.1 |
| Def: Weights | ✅ Sketched | `Main.lean` line 27–37 | § 1.2 |
| Lemma 2.1 | ⏳ Todo | `Main.lean` line 44 | § 2.1, lines 63–83 |
| Lemma 2.2 | ⏳ Todo | `Main.lean` line 49 | § 2.2, lines 85–123 |
| Theorem 3.1 | ⏳ Todo | `Main.lean` line 54 | § 3, lines 125–150 |

**Current:** All three main theorems are stubbed with `sorry`. See `ClarksonShor/Main.lean` for proof placeholders.

## Repository Structure

```
ClarksonShor/
  Main.lean                  Core CS-structure definitions & proof stubs

blueprint/                   Mathematical blueprint (TeX + PlasTeX)
  src/
    content.tex              Main document: definitions, lemmas, proofs
    print.tex                PDF document template
    web.tex                  Web HTML template
    references.bib           Bibliography (Clarkson89, HarPeled11, Sharir03, etc.)
    plastex.cfg              PlasTeX config
    latexmkrc                LaTeX build config
    macros/
      common.tex             Shared macros
      print.tex              PDF-specific (dummy \lean, \discussion, etc.)
      web.tex                Web-specific

home_page/                   GitHub Pages site (Jekyll)
  _config.yml
  index.md
  
.github/workflows/
  lean_action_ci.yml         Lean build + doc-gen on every push
  blueprint.yml              Blueprint compilation → GitHub Pages
  
lakefile.toml                Lake project manifest
lean-toolchain               Lean version (v4.33.0)
```

## Dependencies

### Lean / Mathlib
- **Lean:** 4.33.0
- **Mathlib:** v4.33.0
- **Other packages:** doc-gen4, checkdecls, ProofWidgets4

### Blueprint (TeX/PlasTeX)
- `pdflatex` or `latexmk`
- `plasTeX` (for HTML generation)
- Ruby + Jekyll (for homepage)

## Getting Started with Formalization

### Understand the Framework

Read the blueprint first:
1. § Introduction: motivation and context
2. § 1: Formal CS-structure definition
3. § 2–3: Lemmas and main theorem (with hand proofs)

Open the corresponding Lean file and see how definitions map to TeX:

```lean
-- ClarksonShor/Main.lean, line 14
structure ClarksonShorStructure (α β : Type*) where
  -- Maps to content.tex line 17-31, definition [CS-structure]
```

### Contribute a Proof

To complete one of the three main theorems:

1. **Pick a lemma** — start with Lemma 2.1 (simplest)
2. **Read the hand proof** in `blueprint/src/content.tex`
3. **Identify Mathlib lemmas** for combinatorics (e.g., `Nat.choose`, `Finset` operations)
4. **Translate to Lean** — replace `sorry` with `by`
5. **Iterate** until `lake build` succeeds
6. **Update blueprint** — add `\leanok` tag once Lean proof is verified

Example stub (Lean):
```lean
theorem prob_isZeroWeight_eq (σ : β) (hσ : σ ∈ CS.C) (r : ℕ) (hr : r ≤ CS.S.card) :
    True := by
  sorry  -- Replace with proof
```

Example blueprint reference (TeX):
```tex
\begin{lemma}[Probability of Zero Weight in $R$]
\label{lem:prob_zero_weight}
\lean{ClarksonShorStructure.prob_isZeroWeight_eq}
...
```

## Related Work

- **Clarkson & Shor (1989):** "Applications of Random Sampling in Computational Geometry, II" — foundational paper
- **Mulmuley (1994):** Computational Geometry textbook with modern exposition
- **Har-Peled (2011):** "Geometric Approximation Algorithms" — standard reference with uniform notation
- **Sharir (2003):** Extended overview of the technique
- **Bae, Oliver, Papadopoulou (2025):** "Higher-Order Color Voronoi Diagrams and the Colorful Clarkson-Shor Framework" — recent application

## License

Apache License 2.0 — see [LICENSE](LICENSE)

## Citation

```bibtex
@misc{ClarksonShorLean2026,
  author = {Oliver, Nicolau},
  title  = {Clarkson-Shor Random Sampling Methods in Lean 4},
  year   = {2026},
  url    = {https://github.com/OliverNicolau/clarkson-shor-lean}
}
```

## Contacts & Community

- Report issues or ask questions on [GitHub Issues](https://github.com/OliverNicolau/clarkson-shor-lean/issues)
- Discuss Lean formalization on [Lean Zulip](https://leanprover.zulipchat.com/)
- Join the Mathlib community: [mathlib4](https://github.com/leanprover-community/mathlib4)
