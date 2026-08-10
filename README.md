# Mathematical Dictionary

A comprehensive LaTeX mathematical dictionary with **1,554 entries** covering topics from foundational concepts to advanced theory, including classical theorems, modern results, and paradoxes.

## Overview

Mathematics is not learned alphabetically, nor is it practised that way. This dictionary is therefore organised alphabetically **within** subject-based chapters, so a topologist finds homotopy and sheaf theory together rather than scattered between unrelated terms. Each entry is a concise definition in bold blue with an automatic index entry and a hyperlink anchor.

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
A concise definition in plain language, with inline math where natural.
```

Insert the entry in the correct alphabetical position within its chapter file, then rebuild.

## Contributing

This is a living document. Corrections, new entries, and suggestions are welcome via issues or pull requests.
