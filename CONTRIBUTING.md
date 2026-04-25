# Contributing

## Report errors
Errors, typos, inaccuracies, etc. can be reported by opening an issue with [this issue template](https://github.com/luciano-spettoli/template_latex/issues/new?template=error_report.yml).

## Report code issues
Bugs in the source code can be reported via [this issue template](https://github.com/luciano-spettoli/template_latex/issues/new?template=bug_report.yml).

## Suggest improvements
Suggestions for improvements in the wording, phrasing, grammar, etc.
can be made by opening an issue with [this issue template](https://github.com/luciano-spettoli/template_latex/issues/new?template=proposal.yml), or by opening a pull request.

## Code contributions
Suggestions for improvements in the LaTeX source code or in the project structure
can be made by opening an issue or a pull request.

<!--
Particularly, help is needed for the following:
- making the MathML via "Structured Elements" (`mathml-SE`) work;
- making EPUB generation work correctly for MathML, SVG and PNG Math rendering.
-->


# Documentation
Here, the project structure is documented.

The `src` directory is where the LaTeX source code is contained:
- the `latexmkrc` file contains the configuration for generating the PDF; it sets `lualatex` as the default compiler
- the `main.tex` file is the root file
- the `pdfinfo.tex` file contains the settings for generating a tagged PDF or PDF/A, and metadata information
- the `assets` directory is for files like images, etc.
- the `references` directory contains the references, in `.bib` format
- the `preamble` directory contains the document preamble:
    - `preamble.tex` is the root file
    - `references.tex` sets the settings for the references
    - `typography.tex` sets the font and typographical settings
    - `metadata.tex` is for setting up hyperlinks, bookmarks, and some metadata
    - `custom_sections.tex` contains definitions of sectioning commands and associated counters
    - the subdirectory `maths` is for loading packages and definitions related to typesetting of mathematical content:
        - `maths.tex` is the root file; it loads the main Mathematics packages
        - `environments.tex` defines theorem environments
        - `scalemath.tex` contains a placeholder implementation for commands that typeset mathematical expressions in an intermediate size;
          in particular, it defines `\mfrac` and `\mbinom` for medium-sized fractions and binomial coefficients
        - `delimiters.tex` contains definitions of delimiters using `\DeclarePairedDelimiter` provided by `mathtools`;
          it also loads the `mleftright` package for fixing the spacing between operators and delimiters
        - `operators.tex` contains definitions of operators via `\DeclareMathOperator`
        - `relations.tex` defines some binary relation symbols
        - `binary_ops.tex` defines some binary operators
- the `sections` directory contains the `.tex` files for the introduction and for each section of the document
