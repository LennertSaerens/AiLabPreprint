# VUB AI research preprint template

A single-column LaTeX template with a left-aligned, rounded title panel and a
justified abstract underneath. Libertinus Serif and Libertinus Math are preserved. The VUB palette
informs the layout; an optional orange VUB triangle sits to the left of the title. This is a lab research template, not an
official corporate document class.

## Start in Overleaf

1. Upload `output/ailab-preprint-overleaf.zip` using **New project > Existing project (.zip)**.
2. In project **Settings > Compiler**, select **LuaLaTeX** and a recent TeX Live
   version. Local validation uses TeX Live 2025.
3. Compile `main.tex` to read the illustrated guide.
4. To write a paper, replace `main.tex` with the contents of `starter.tex`.
   Keep a separate copy of the guide for reference. Edit the title, authors,
   affiliations, abstract, and sections. No style-file changes are necessary.
5. Add your BibTeX entries to `references.bib`, cite them, and uncomment the two
   bibliography commands in the starter. Overleaf handles BibTeX automatically.

If you keep both documents and compile `starter.tex` directly, select it as the
project's **Main document** in Settings. The ZIP contains the guide plus the clean
starter; the supplied brand PDF and EPS are reference materials, not dependencies.

Official Overleaf instructions: [uploading a project](https://docs.overleaf.com/managing-projects-and-files/uploading-a-project)
and [choosing the compiler](https://docs.overleaf.com/getting-started/recompiling-your-project/selecting-a-tex-live-version-and-latex-compiler).

## Files

- `main.tex`: self-documenting showcase, including table and math examples.
- `starter.tex`: clean manuscript skeleton.
- `ailab-preprint.sty`: shared typography, front matter, colors, and packages.
- `references.bib`: example references; replace for your paper.
- `example-table-rows.tex`: synthetic rows used only by the guide's long table.
- `.latexmkrc`: selects LuaLaTeX for local builds.
- `output/pdf/main.pdf`: compiled guide for review.

## Local build

With a full TeX Live installation (2025 tested):

```sh
latexmk main.tex
latexmk starter.tex
```

Without latexmk, run `lualatex main`, `bibtex main`, then `lualatex main` twice.
No shell escape, Biber, or logo conversion is needed. The official title font
requires the font file described below; the fallback is bundled with TeX Live.
PDF output is produced in the current directory by these commands.

## Author interface

Use `\title`, `\author`, `\affiliations`, and `\preprintabstract` before
`\begin{document}`, then call `\maketitle` once. `\affil{1,2}` adds author or
institution superscripts. Optional `\keywords`, `\preprintnote`, and `\date` fields disappear when omitted. The date is blank
by default. Put shared-contribution notes in `\preprintnote` rather than title
footnotes. Very long front matter can break across pages.

Loaded tools include natbib (author–year), cleveref, amsthm, unicode-math,
algorithm2e, graphicx/subcaption, booktabs, tabularx, longtable, and siunitx.
Do not reload these with incompatible options. Use `\symbf` for bold math;
avoid legacy math-font packages and competing algorithm packages. Load any
additional package after `ailab-preprint` and check for conflicts.

Tables use captions above, no vertical rules, numeric `S` columns, and explicit
uncertainty definitions. Use `Y` columns in tabularx for wrapping descriptions;
use longtable outside a float for repeated headings across pages. See the guide
for source examples. Figure guidelines are intentionally left for later.

## Title font and triangle

Enable the triangle with `\usepackage[triangle]{ailab-preprint}`. Omit the option
(or use `[notriangle]`) for collaborations that prefer no institutional mark.
The guide enables it; the clean starter leaves it off. The triangle is drawn in
LaTeX using the guide's geometry, without loading the full VUB logo or EPS.

Upload the licensed ITC Avant Garde Gothic Pro Bold OTF file as
`fonts/ITCAvantGardePro-Bold.otf`. The style automatically uses that project file
on local builds and Overleaf. See `fonts/README.md`. **The font binary has not
been supplied yet**, so the current preview uses TeX Gyre Adventor Bold as a
clearly identified substitute. No substitute is labelled as the official font.

## Design references

The supplied VUB guide, PDF page 13 (printed page 18), specifies primary blue
`#003399`, orange `#FF6600`, and secondary gray-blue `#E8EBF1`. The style uses the
printed HEX values; secondary RGB values in that guide differ from its HEX
values. The panel is a lighter tint of gray-blue. Body text and math retain
Libertinus; the title is configured for the official ITC Avant Garde Gothic font.
The supplied EPS is not loaded or included in the Overleaf bundle.
