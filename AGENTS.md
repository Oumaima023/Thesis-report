# AGENTS.md

## Project Scope
- This repository is a LaTeX thesis project built around main.tex.
- Treat this as a document-editing workspace, not an application codebase.

## Source Of Truth
- Main entry point: main.tex
- Included chapter files: chapter1.tex, chapter2.tex, chapter3.tex, chapter4.tex
- Arabic/final abstract section file: Abstract.tex
- Bibliography database: references.bib
- Assets: images/
- VS Code LaTeX recipe settings: .vscode/settings.json

## Build And Preview
- Preferred in VS Code: use LaTeX Workshop recipe latexmk (xelatex).
- Terminal build (full reliable flow when bibliography/acronyms changed):
  1. xelatex -interaction=nonstopmode -file-line-error main.tex
  2. biber main
  3. makeglossaries main
  4. xelatex -interaction=nonstopmode -file-line-error main.tex
  5. xelatex -interaction=nonstopmode -file-line-error main.tex
- Quick rebuild after minor text edits can use:
  - latexmk -xelatex -synctex=1 -interaction=nonstopmode -file-line-error main.tex

## Editing Rules For Agents
- Edit only source files: main.tex, chapter*.tex, Abstract.tex, references.bib, and optionally .vscode/settings.json when explicitly requested.
- Do not edit generated artifacts such as *.aux, *.acn, *.acr, *.alg, *.bcf, *.blg, *.bbl, *.glo, *.gls, *.glg, *.ist, *.lof, *.lot, *.lol, *.toc, *.xdv, *.out, *.run.xml, *.synctex.gz, or main.pdf.
- Preserve current LaTeX engine compatibility with XeLaTeX (fontspec/polyglossia are in use).
- Keep chapter structure stable unless asked: main.tex uses input statements for chapter files.
- Prefer minimal localized edits and avoid broad formatting rewrites.

## Project-Specific Conventions
- Bibliography is managed with biblatex using backend=biber and style=ieee.
- Acronyms are defined in main.tex via glossaries and rendered with printacronyms.
- The document uses custom Arabic handling with TeXXeTstate and artext helper; avoid replacing this with bidi/polyglossia Arabic changes unless explicitly requested.

## Common Pitfalls
- Running pdflatex can fail because fontspec requires XeLaTeX or LuaLaTeX; default to XeLaTeX.
- Single-pass compile often leaves unresolved references; run the full build sequence when references, glossary, TOC, or citations changed.
- Existing generated files in the repository can be stale; rely on fresh compilation results, not on artifact timestamps alone.

## What To Check After Changes
- No new LaTeX errors in compile log.
- Citations resolve after biber run.
- Acronyms/glossary render correctly after makeglossaries.
- main.pdf updates successfully.
