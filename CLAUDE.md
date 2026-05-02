# CLAUDE.md — Project Guide for AI Assistants

## Project Overview

**Engenharia de Redes Neurais Artificiais** is a graduate-level course book (in Brazilian Portuguese) for the "Engenharia de Redes Neurais Artificiais" course at Pontifícia Universidade Católica do Paraná (PUCPR). It covers neural networks from fundamentals to advanced topics, published as both an interactive website and a PDF book using MyST (Markedly Structured Text) / Jupyter Book.

- **Live site**: https://vhrique.github.io/anne_ptbr/
- **Author**: Dr. Victor Henrique Alves Ribeiro
- **Language**: Brazilian Portuguese

---

## Repository Structure

```
anne_ptbr/
├── myst.yml                     # Main project config: TOC, PDF export, bibliography
├── CLAUDE.md                    # This file
├── README.md                    # Course overview and links
├── references.bib               # BibTeX bibliography
│
├── Content files (Markdown):
│   ├── 00a_Prefacio.md          # Preface (root/frontmatter)
│   ├── 00b_Introducao.md        # Introduction to Neural Networks
│   ├── 01_Fundamentos.md        # Chapter header: Fundamentals
│   ├── 02_Componentes.md        # Chapter header: Components
│   ├── 03_Paradigmas.md         # Chapter header: Learning Paradigms
│   ├── 04_Aspectos.md           # Chapter header: Practical Aspects
│   ├── 05_Topicos.md            # Chapter header: Special Topics
│   └── 06_Conteudos.md          # Chapter header: Additional Content
│
├── Content files (Jupyter Notebooks):
│   ├── Perceptron.ipynb
│   ├── Perceptron_Multicamadas.ipynb
│   ├── Otimizacao_Redes_Neurais.ipynb
│   ├── Camadas_Lineares_Ativacao.ipynb
│   ├── 03_Redes_Neurais_Convolucionais.ipynb
│   ├── 04a_Redes_Neurais_Recorrentes.ipynb
│   ├── 04b_Transformers.ipynb
│   ├── Regularizacao.ipynb
│   ├── Aprendizagem_Supervisionada.ipynb
│   ├── 05a_Aprendizagem_de_Metricas.ipynb
│   ├── 05b_Aprendizagem_Auto_Supervisionado.ipynb
│   ├── 05c_Aprendizagem_Nao_Supervisionada.ipynb
│   ├── Aprendizagem_Multitarefas.ipynb
│   ├── Modelos_Multimodais.ipynb
│   ├── Aprendizagem_Joint_Embedding.ipynb
│   ├── Transfer_Learning.ipynb
│   ├── Reducao_Modelos.ipynb
│   ├── Adaptacao_Dominio.ipynb
│   ├── Receita_Treino_ANN.ipynb
│   ├── 08a_Novas_Fronteiras.ipynb
│   ├── 08b_Topicos_Especiais.ipynb
│   ├── A01_Fundamentos_de_Pytorch.ipynb
│   └── A03_Visao_Computacional.ipynb
│
├── figures/                     # 130+ images referenced in notebooks (PNG, JPG, SVG)
├── data/                        # Dataset files used in examples
├── projetos/                    # Final project templates and datasets
│
└── .github/workflows/
    ├── deploy.yml               # Build and deploy HTML to GitHub Pages
    └── pdf.yml                  # Build and upload PDF artifact
```

---

## Key Configuration: `myst.yml`

This is the single most important file. It controls:

### TOC Structure
The book is organized as:
- `00a_Prefacio.md` — frontmatter preface (standalone, no children)
- `01_Fundamentos.md` (Chapter 1) + children notebooks
- `02_Componentes.md` (Chapter 2) + children notebooks
- `03_Paradigmas.md` (Chapter 3) + children notebooks
- `04_Aspectos.md` (Chapter 4) + children notebooks
- `05_Topicos.md` (Chapter 5) + children notebooks
- `06_Conteudos.md` (Chapter 6) + children notebooks

**Important**: Chapter header files (`01_Fundamentos.md` through `06_Conteudos.md`) use `file:` (not `title:`) at depth-0 in the TOC. This is required for correct LaTeX chapter numbering in the PDF — `title:`-only entries produce `\section{}` which puts everything in "chapter 0", causing `0.x.y` section numbers instead of `x.y`.

### PDF Export
```yaml
exports:
  - format: pdf
    template: plain_latex_book
    output: exports/book.pdf
```
Uses the `plain_latex_book` template from MyST/jtex. Produces a LaTeX-compiled PDF.

### HTML Site
```yaml
site:
  template: book-theme
```
The HTML site uses the `book-theme` template, deployed to GitHub Pages.

---

## Build System

The project uses **MyST** (via `jupyter-book` npm package). Notebooks are not executed at build time (`execute_notebooks: off` in the old config; MyST 1.x handles this via cell metadata).

### PDF Build (GitHub Actions)
`.github/workflows/pdf.yml` installs:
- Node.js + `jupyter-book` (npm)
- TeX Live with XeLaTeX (`texlive-latex-extra`, `texlive-fonts-recommended`, `texlive-fonts-extra`, `texlive-lang-portuguese`, `texlive-xetex`, `latexmk`)

Then runs: `jupyter-book build --pdf`

### HTML Build (GitHub Actions)
`.github/workflows/deploy.yml` builds the HTML site and deploys to GitHub Pages.

---

## Image Handling in PDF

Images in notebooks use MyST directives. For PDF compatibility, image widths should be specified as percentages (not pixels), because pixel values are not valid in LaTeX:

```markdown
:::{figure} figures/image.png
:width: 80%
:::
```

Avoid specifying widths in pixels (`px`) — they cause LaTeX compilation errors.

---

## Common Tasks

### Adding a new notebook to the book
1. Add the `.ipynb` file to the repo root
2. Add `- file: notebook_name.ipynb` under the appropriate chapter's `children:` in `myst.yml`

### Adding a new chapter
1. Create a minimal `XX_ChapterTitle.md` with just `# Chapter Title`
2. Add `- file: XX_ChapterTitle.md` at depth-0 in the TOC in `myst.yml`
3. Add the chapter's notebook files as `children:` under it

### Fixing PDF image issues
- Replace pixel widths with percentages in `{figure}` directives
- Use `figures/` directory for all images

### Adding references
- Add BibTeX entries to `references.bib`
- Cite in notebooks with `{cite}\`key\``

---

## Notebooks Structure

Each notebook follows a consistent pattern:
- H1 (`#`) — notebook/section title (becomes `\section{}` in PDF)
- H2 (`##`) — subsections within the topic (becomes `\subsection{}`)
- H3 (`###`) — deeper subsections
- Code cells — Python examples (PyTorch, NumPy, scikit-learn, matplotlib)
- `## Referências` — references section at the end

Notebooks use Portuguese throughout. Code comments and variable names may be in English.
