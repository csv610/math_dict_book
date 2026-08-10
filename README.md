# Mathematical Dictionary

A comprehensive LaTeX mathematical dictionary with **1,788 entries** covering topics from foundational concepts to advanced theory, including classical theorems, modern results, and paradoxes. Although some terms are graduate-level, explanations are written for undergraduates without becoming superficial: they explain the main idea, define essential vocabulary, retain important assumptions and formulas, and describe applications in science, engineering, computing, or data analysis.

## Overview

Mathematics is not learned alphabetically, nor is it practised that way. This dictionary is organised alphabetically by letter for quick lookup. Each entry aims to give an undergraduate-friendly explanation with enough mathematical substance to be useful: definition, intuition, assumptions, formula or example, and application where appropriate. Terms that require advanced background should still make their purpose and importance clear.

## Features

- 26 chapter files (`dict_a.tex` – `dict_z.tex`), each containing an alphabetical run of `\term{...}` entries
- Full coverage of algebra, analysis, geometry, topology, number theory, and applied mathematics
- Named theorems (e.g. Banach–Tarski, Hahn–Banach, Sylow, Seifert–van Kampen) and paradoxes (Monty Hall, Bertrand, Russell's, Zeno's)
- Generated index and internal hyperlinks
- Two-column book layout with running headers

## Building

Requires a TeX distribution (TeX Live recommended) and `latexmk`:

```bash
latexmk -pdf math_dictionary.tex
```

The output is `math_dictionary.pdf` (approximately 130 pages).

## Project structure

```
math_dictionary.tex      Main document (preamble, front matter, chapter inputs)
chapters/dict_a.tex      Chapter files, one per letter A–Z
```

## Adding an entry

Each entry follows this format (no blank line between the term and its definition; one blank line between entries):

```latex
\term{Term Name}
A clear but substantive definition in plain language, with inline math where natural. Explain technical words briefly, preserve important hypotheses, include a formula, example, or consequence when useful, and add an `Applications:` sentence describing the term's practical importance.
```

Insert the entry in the correct alphabetical position within its chapter file, then rebuild.

## Contributing

This is a living document. Corrections, new entries, and suggestions are welcome via issues or pull requests.
