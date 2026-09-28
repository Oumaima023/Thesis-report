# Windows Setup For This Thesis

This thesis must be compiled with XeLaTeX, not pdfLaTeX.

## 1. Install TeX Live

Download TeX Live for Windows:

https://tug.org/texlive/windows.html

Run:

- `install-tl-windows.exe`

Recommended:

- Keep the default full installation.

## 2. Check That The Required Tools Exist

Open `Command Prompt` and run:

```bat
xelatex --version
biber --version
makeglossaries --version
latexmk --version
```

All four commands should return a version.

## 3. Install VS Code

Download VS Code:

https://code.visualstudio.com/

## 4. Install The LaTeX Extension

In VS Code, install:

- `LaTeX Workshop`

## 5. Install The Required Fonts

This thesis uses these fonts:

- `Amiri`
- `Times New Roman`

`Times New Roman` is usually already installed on Windows.

If `Amiri` is missing, download it here:

https://fonts.google.com/specimen/Amiri

Then:

- Extract the font files.
- Select the `.ttf` files.
- Right-click.
- Choose `Install for all users`.

## 6. Copy The Thesis Folder

Copy the full thesis folder to the Windows laptop.

Important source files include:

- `main.tex`
- `Abstract.tex`
- `chapter1.tex`
- `chapter1_stateoftheart.tex`
- `chapter2.tex`
- `chapter3.tex`
- `chapter4.tex`
- `general_conclusion.tex`
- `references.bib`
- `images/`

Best practice:

- Compress the folder into a zip file before moving it.
- Extract it on the new laptop.

## 7. Open The Project In VS Code

- Open the thesis folder.
- Open `main.tex`.
- Make sure builds use `XeLaTeX`.

## 8. First Full Build

Open a terminal in the thesis folder and run:

```bat
xelatex -interaction=nonstopmode -file-line-error main.tex
biber main
makeglossaries main
xelatex -interaction=nonstopmode -file-line-error main.tex
xelatex -interaction=nonstopmode -file-line-error main.tex
```

This is the correct full build flow for this project.

## 9. Quick Rebuild After Small Edits

```bat
latexmk -xelatex -synctex=1 -interaction=nonstopmode -file-line-error main.tex
```

## 10. If A Command Is Not Recognized

The TeX Live binary folder may be missing from `PATH`.

Typical path:

```text
C:\texlive\2026\bin\windows
```

To fix it:

- Search for `Environment Variables` in Windows.
- Open `Edit the system environment variables`.
- Open `Environment Variables`.
- Edit `Path`.
- Add the TeX Live `bin\windows` folder.
- Close and reopen the terminal.

## 11. Final Check

After building, verify that:

- `main.pdf` is generated
- citations appear correctly
- the acronym list appears correctly
- images are displayed correctly
