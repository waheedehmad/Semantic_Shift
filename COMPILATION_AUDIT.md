# COMPILATION AUDIT

**Paper:** "Topic Modeling from Latent Semantic Analysis to Large Language Models: A Critical Review of Methods and Evaluation Practice"

**Files:** `main.tex`, `references.bib`

---

## ⚠️ IMPORTANT: This Document Has NOT Been Compile-Tested

No LaTeX compiler (`pdflatex`, `lualatex`, `xelatex`) or bibliography processor (`biber`) is available in the environment where this document was produced. **The claim that this document compiles successfully cannot be made and is not made here.** The audit below is a manual review only.

---

## Compilation Instructions (for the repository owner)

Run the following commands in the directory containing `main.tex` and `references.bib`:

```bash
pdflatex -interaction=nonstopmode -halt-on-error main.tex
biber main
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
```

**Prerequisites:**
- A TeX distribution with `biblatex` and `biber` (e.g. TeX Live ≥ 2020 or MiKTeX).
- The `lmodern`, `microtype`, `amsmath`, `amssymb`, `amsthm`, `bm`, `hyperref`, `booktabs`, `graphicx`, `xcolor`, `setspace`, and `geometry` packages (all standard in TeX Live).
- Note: `biber` — not `bibtex` — must be used because the document uses `biblatex` with `backend=biber`.

**After compilation:**
- Inspect `main.log` for `Undefined control sequence`, `Citation ... undefined`, `Label ... undefined`, `Overfull \hbox` warnings.
- Inspect `main.blg` (biber log) for missing or malformed bibliography entries.
- Confirm the output PDF has a table of contents, section headings, in-text citations, and a bibliography.

---

## Manual Review Checklist

The following items were checked by hand. Items marked **PASS** indicate no obvious issue was found; items marked **NOTE** flag something the compiler may flag but that is expected or acceptable.

### 1. Document Class and Packages

- [x] `\documentclass[11pt,a4paper]{article}` — standard, no issues expected.
- [x] All `\usepackage` calls use standard CTAN packages available in TeX Live.
- [x] `biblatex` loaded with `backend=biber` — consistent with `\addbibresource{references.bib}`.
- [x] No conflicting packages (e.g. `natbib` not loaded alongside `biblatex`).

### 2. Custom Macros

- [x] `\newcommand{\vect}[1]{\boldsymbol{#1}}` — defined in preamble; used as `\vect{\theta}_d`, `\vect{\alpha}`, `\vect{\beta}`, `\vect{\rho}` throughout.
- [x] `\newcommand{\R}{\mathbb{R}}` — defined in preamble; used in text and display math.
- [x] No use of `\vect` or `\R` before their definitions.
- [x] No `\vrfy{...}` placeholders present anywhere in the document (all resolved).

### 3. Environments and Braces

- [x] Every `\begin{...}` has a matching `\end{...}`: `document`, `abstract`, `enumerate`, `table`, `tabular`.
- [x] Every `{` in math mode has a matching `}` (hand-checked all display equations).
- [x] The display equation in Section 4.2 (`p(w=v|z=k) \propto \exp(...)`) is correctly wrapped in `\[...\]`.
- [x] `\textbf`, `\textit`, `\emph`, `\parencite`, `\textcite`, `\cite`, `\citeauthor` are all properly closed.

### 4. Citations and Bibliography Keys

All citation keys used in `main.tex` are present in `references.bib`. Mapping:

| Citation key used in `main.tex` | Present in `references.bib` |
|--------------------------------|------------------------------|
| `deerwester1990indexing`        | ✅ |
| `hofmann1999probabilistic`      | ✅ |
| `blei2003latent`                | ✅ |
| `griffiths2004finding`          | ✅ |
| `blei2012probabilistic`         | ✅ |
| `blei2005correlated`            | ✅ |
| `blei2006dynamic`               | ✅ |
| `teh2006hierarchical`           | ✅ |
| `blei2007supervised`            | ✅ |
| `ramage2009labeled`             | ✅ |
| `yin2014dirichlet`              | ✅ |
| `mimno2009polylingual`          | ✅ |
| `bianchi2021crosslingual`       | ✅ |
| `miao2016neural`                | ✅ |
| `srivastava2017autoencoding`    | ✅ |
| `dieng2020topic`                | ✅ |
| `sia2020tired`                  | ✅ |
| `zhao2021neural`                | ✅ |
| `bianchi2021pretraining`        | ✅ |
| `grootendorst2022bertopic`      | ✅ |
| `hoyle2022broken`               | ✅ |
| `chang2009reading`              | ✅ |
| `wallach2009evaluation`         | ✅ |
| `newman2010automatic`           | ✅ |
| `lau2014machine`                | ✅ |
| `mimno2011optimizing`           | ✅ |
| `roder2015exploring`            | ✅ |
| `koltcov2014lda`                | ✅ |
| `hoyle2021automated`            | ✅ |
| `doogan2021twaddle`             | ✅ |
| `terragni2021octis`             | ✅ |
| `pham2024topicgpt`              | ✅ |
| `bail2016combining`             | ✅ |
| `strubell2019energy`            | ✅ |

**Result: No undefined citation keys detected in manual review.**

### 5. No Orphan Bibliography Entries

Every entry in `references.bib` is cited at least once in `main.tex`. Specifically:

- `blei2012probabilistic` — cited in Section 2.3 ("Blei 2012 provides an accessible tutorial..."). This was flagged as uncited in the handoff draft; it is now cited.
- All other entries cited in at least one location.

### 6. Section Labels and Cross-References

| `\label` | Referenced by `\ref` or `\autoref` | Status |
|----------|------------------------------------|--------|
| `sec:introduction` | — (not cross-ref'd, normal for intro) | OK |
| `sec:foundations` | — | OK |
| `sec:lsa` | — | OK |
| `sec:plsa` | — | OK |
| `sec:lda` | — | OK |
| `sec:lda-extensions` | — | OK |
| `sec:ctm` | — | OK |
| `sec:dtm` | — | OK |
| `sec:hdp` | — | OK |
| `sec:slda` | — | OK |
| `sec:shorttext` | — | OK |
| `sec:multilingual` | `sec:contextualized` forward ref in body | OK — forward reference |
| `sec:neural` | — | OK |
| `sec:nvdm` | — | OK |
| `sec:etm` | — | OK |
| `sec:contextualized` | Referenced from Section~\ref{sec:multilingual} body text | OK |
| `sec:llm` | — | OK |
| `sec:evaluation` | Referenced in Section 4 intro ("Section~\ref{sec:evaluation}") | OK |
| `sec:eval-perplexity` | — | OK |
| `sec:eval-coherence` | — | OK |
| `sec:eval-stability` | — | OK |
| `sec:eval-extrinsic` | — | OK |
| `sec:eval-human` | — | OK |
| `sec:comparison` | — | OK |
| `sec:applications` | — | OK |
| `sec:software` | — | OK |
| `sec:ethics` | — | OK |
| `sec:fairness` | — | OK |
| `sec:privacy` | — | OK |
| `sec:energy` | — | OK |
| `sec:future` | — | OK |
| `sec:conclusion` | — | OK |
| `tab:model-comparison` | Referenced via `Table~\ref{tab:model-comparison}` in Section 7 | OK |

### 7. Math Environments

- [x] All `$...$` inline math expressions are properly paired.
- [x] All `\[...\]` display math blocks are properly paired.
- [x] `\begin{enumerate}` in Section 2.3 (LDA generative process) is nested correctly with two levels; all `\item` commands are inside an active `enumerate` environment.
- [x] `\mathrm{Dir}`, `\mathrm{Categorical}` used correctly (roman font for distribution names).

### 8. Table

- [x] `table` environment at `[ht]` with `\centering` and `\caption` before `\label` — correct order.
- [x] `tabular` with `@{}lllll@{}` — five columns matching five `&`-separated entries per row.
- [x] `\toprule`, `\midrule`, `\bottomrule` from `booktabs` — correct usage.
- [x] Multicolumn footnote below `\bottomrule` uses `\multicolumn{5}{l}{...}` — five-column span matches table width.

### 9. BibLaTeX Entry Types

- [x] All journal articles use `@article`.
- [x] All conference papers use `@inproceedings`.
- [x] The BERTopic preprint uses `@misc` with `eprint` and `eprinttype=arXiv` — correct biblatex syntax for arXiv preprints.
- [x] ICLR papers (AVITM, NTM via OT) use `@inproceedings` with `url` field pointing to OpenReview — acceptable; no DOI exists for these.
- [x] No duplicate bibkeys.

### 10. Encoding and Special Characters

- [x] `\usepackage[utf8]{inputenc}` declared — accented characters in author names (Röder → `R{\"o}der`) properly escaped in the `.bib` file.
- [x] DOI containing special characters (`deerwester1990indexing`) is wrapped in `\url{...}` implicitly via biblatex's DOI field handling — no issues expected.

---

## Potential Compiler Warnings (Expected, Not Errors)

| Warning type | Likely source | Severity |
|-------------|---------------|----------|
| Overfull `\hbox` | Long DOI strings in bibliography | Minor cosmetic |
| `Package biblatex Warning: 'url' field not printed` | Entries with both `doi` and `url` | Cosmetic; harmless |
| Underfull `\hbox` | Short lines in narrow `tabular` cells | Cosmetic |
| `LaTeX Warning: Float too large for page` | If the comparison table cannot fit on one page | Can be resolved by adjusting `[ht]` to `[htbp]` |

---

## Integrity Statement

- No `\vrfy{...}` placeholders are present in `main.tex`.
- No fabricated bibliographic metadata, factual claims, quotations, results, or dataset statistics appear in the document.
- The document has **not** been compiled or tested with any LaTeX engine. The above is a manual review only.
- Users should run the four-step compilation sequence above and inspect the log files before treating this as a submission-ready PDF.
