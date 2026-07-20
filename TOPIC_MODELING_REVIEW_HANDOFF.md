# Topic-Modeling Review: Conversation Handoff

## Purpose

Use this file as context when continuing the topic-modeling review in a new chat. The review is a critical academic paper currently scoped under the working title:

> **Topic Modeling from Latent Semantic Analysis to Large Language Models: A Critical Review of Methods and Evaluation Practice**

The title was narrowed from the original, broader proposal because the sources gathered so far support the historical/methodological and evaluation-critical threads better than a fully comprehensive survey of every application, fairness, privacy, environmental, multilingual, and reproducibility issue.

## Original Request

The user requested a publication-quality LaTeX review of topic modeling with:

- critical synthesis rather than an annotated bibliography;
- a reproducible search protocol;
- verified references only;
- `main.tex` using `biblatex` and a separate `references.bib`;
- a per-reference verification log;
- a compilation audit;
- no fabricated bibliographic metadata, factual claims, quotations, results, or datasets.

The requested coverage includes foundations, historical development, model families, evaluation, comparative analysis, applications, datasets/software/reproducibility, ethics, research gaps, and future directions.

## Integrity Constraints

The previous assistant had general web-search access but **did not have** a LaTeX compiler, direct Crossref/DBLP APIs, or direct DOI-resolution tooling. Therefore:

1. Do not claim the paper was compile-tested.
2. Do not call the source inventory fully verified until every entry is checked on an authoritative scholarly record (publisher, ACL Anthology, OpenReview, DBLP, Crossref, JMLR, etc.).
3. Do not silently repair uncertain metadata or invent missing references.
4. Treat any prior manuscript as a scaffold, not as submission-ready work.

## Earlier LaTeX Issue

The earlier draft used `\vect{...}` and `\R` without defining them. Add these to the preamble:

```latex
\newcommand{\vect}[1]{\boldsymbol{#1}}
\newcommand{\R}{\mathbb{R}}
```

Prefer `\vect{\theta}_d` rather than `\vect\theta_d`.

Other known issues in the earlier draft:

- It was never compilation-tested.
- It intentionally contained `\vrfy{...}` placeholders.
- `blei2012probabilistic` appeared in the bibliography but was initially uncited; cite it or remove it.
- `wallach2009evaluation` requires direct confirmation of author order from the official proceedings.
- The OCTIS record initially surfaced with two IDs; a follow-up search established that **`2021.eacl-demos.31`** is the correct ACL Anthology ID.
- The initial bibliography was too small to support an 8,000--12,000-word comprehensive review.

## Best-Effort Candidate Reference Inventory

The following were gathered via targeted web searches. They are useful candidates, but must be checked directly against authoritative records before submission.

### Foundations and classical probabilistic models

- `deerwester1990indexing` — Deerwester et al., *Indexing by Latent Semantic Analysis* (1990).
- `hofmann1999probabilistic` — Hofmann, *Probabilistic Latent Semantic Indexing* (SIGIR 1999), DOI reported: `10.1145/312624.312649`.
- `blei2003latent` — Blei, Ng, and Jordan, *Latent Dirichlet Allocation* (JMLR 2003).
- `griffiths2004finding` — Griffiths and Steyvers, *Finding Scientific Topics* (PNAS 2004), DOI reported: `10.1073/pnas.0307752101`.
- `blei2012probabilistic` — Blei, *Probabilistic Topic Models* (Communications of the ACM 2012), DOI reported: `10.1145/2133806.2133826`.

### Structured, temporal, supervised, short-text, and multilingual models

- `blei2006correlated` — Blei and Lafferty, *Correlated Topic Models* (NIPS/NeurIPS proceedings; handle conference/proceedings year carefully).
- `blei2006dynamic` — Blei and Lafferty, *Dynamic Topic Models* (ICML 2006), DOI reported: `10.1145/1143844.1143859`.
- `teh2006hierarchical` — Teh et al., *Hierarchical Dirichlet Processes* (JASA 2006), DOI reported: `10.1198/016214506000000302`.
- `blei2007supervised` — Blei and McAuliffe, *Supervised Topic Models* (NIPS 2007).
- `ramage2009labeled` — Ramage et al., *Labeled LDA: A supervised topic model for credit attribution in multi-labeled corpora* (EMNLP 2009).
- `yin2014dirichlet` — Yin and Wang, *A Dirichlet Multinomial Mixture Model-Based Approach for Short Text Clustering* (KDD 2014), DOI reported: `10.1145/2623330.2623715`.
- `mimno2009polylingual` — Mimno et al., *Polylingual Topic Models* (EMNLP 2009).
- `bianchi2021crosslingual` — Bianchi et al., *Cross-lingual Contextualized Topic Models with Zero-shot Learning* (EACL 2021), ACL Anthology reported: `2021.eacl-main.143`.

### Neural, embedding-based, and contextualized topic modeling

- `miao2016neural` — Miao, Yu, and Blunsom, *Neural Variational Inference for Text Processing* (ICML 2016).
- `srivastava2017autoencoding` — Srivastava and Sutton, *Autoencoding Variational Inference for Topic Models* (ICLR 2017; OpenReview ID reported: `HkwzHslxg`).
- `dieng2020topic` — Dieng, Ruiz, and Blei, *Topic Modeling in Embedding Spaces* (TACL 2020), DOI reported: `10.1162/tacl_a_00325`.
- `sia2020tired` — Sia, Dalmia, and Mielke, *Tired of Topic Models? Clusters of Pretrained Word Embeddings Make for Fast and Good Topics too!* (EMNLP 2020), ACL Anthology reported: `2020.emnlp-main.135`.
- `zhao2021neural` — Zhao et al., *Neural Topic Model via Optimal Transport* (ICLR 2021; OpenReview ID reported: `Oos98K9Lv-k`).
- `bianchi2021pretraining` — Bianchi, Terragni, and Hovy, *Pre-training is a Hot Topic: Contextualized Document Embeddings Improve Topic Coherence* (ACL 2021).
- `grootendorst2022bertopic` — Grootendorst, *BERTopic: Neural Topic Modeling with a Class-based TF-IDF Procedure* (arXiv:2203.05794). **Preprint; do not call it peer reviewed unless a later publication is confirmed.**
- `hoyle2022broken` — Hoyle et al., *Are Neural Topic Models Broken?* (Findings of EMNLP 2022), ACL Anthology reported: `2022.findings-emnlp.177`.

### Evaluation, coherence, interpretability, stability, and tooling

- `chang2009reading` — Chang et al., *Reading Tea Leaves: How Humans Interpret Topic Models* (NeurIPS 2009).
- `wallach2009evaluation` — Wallach et al., *Evaluation Methods for Topic Models* (ICML 2009). **Verify author order directly.**
- `newman2010automatic` — Newman et al., *Automatic Evaluation of Topic Coherence* (NAACL-HLT 2010).
- `lau2014machine` — Lau, Newman, and Baldwin, *Machine Reading Tea Leaves: Automatically Evaluating Topic Coherence and Topic Model Quality* (EACL 2014).
- `roder2015exploring` — Röder, Both, and Hinneburg, *Exploring the Space of Topic Coherence Measures* (WSDM 2015), DOI reported: `10.1145/2684822.2685324`.
- `koltcov2014lda` — Koltcov, Koltsova, and Nikolenko, *Latent Dirichlet Allocation: Stability and Applications to Studies of User-generated Content* (WebSci 2014), DOI reported: `10.1145/2615569.2615686`.
- `hoyle2021automated` — Hoyle et al., *Is Automated Topic Model Evaluation Broken? The Incoherence of Coherence* (NeurIPS 2021; arXiv:2107.02173 surfaced as a version record).
- `doogan2021twaddle` — Doogan and Buntine, *Topic Model or Topic Twaddle? Re-evaluating Semantic Interpretability Measures* (NAACL 2021), DOI reported: `10.18653/v1/2021.naacl-main.300`.
- `terragni2021octis` — Terragni, Fersini, Galuzzi, Tropeano, and Candelieri, *OCTIS: Comparing and Optimizing Topic models is Simple!* (EACL 2021 System Demonstrations), ACL Anthology: `2021.eacl-demos.31`.

### LLM-assisted topic discovery, applications, and cost

- `pham2024topicgpt` — Pham et al., *TopicGPT: A Prompt-based Topic Modeling Framework* (NAACL 2024), DOI reported: `10.18653/v1/2024.naacl-long.164`. Prefer this peer-reviewed version rather than the arXiv version.
- `bail2016combining` — Bail, *Combining natural language processing and network analysis to examine how advocacy organizations stimulate conversation on social media* (PNAS 2016), DOI reported: `10.1073/pnas.1607151113`.
- `strubell2019energy` — Strubell, Ganesh, and McCallum, *Energy and Policy Considerations for Deep Learning in NLP* (ACL 2019), ACL Anthology reported: `P19-1355`. It supports general deep-NLP cost discussion, not topic-model-specific environmental claims by itself.

## Recommended Continuation Workflow

1. State in the new chat that this file is the handoff context.
2. Start with a source-verification table; do not begin drafting until the key citations are directly checked.
3. For every source, verify exact title, author ordering, venue/year/pages, DOI resolution, official URL, peer-review status, and preferred version.
4. Write or revise `main.tex` and `references.bib` only after the audit.
5. Add verified coverage for remaining weak sections:
   - applications and benchmark datasets;
   - topic diversity and extrinsic evaluation;
   - software and reproducibility;
   - multilingual and cross-lingual work;
   - stability;
   - fairness, privacy, and energy;
   - independent evaluation of LLM-assisted topic modeling.
6. Remove every `\vrfy{...}` marker before submission.
7. Compile locally:

```bash
pdflatex -interaction=nonstopmode -halt-on-error main.tex
biber main
pdflatex -interaction=nonstopmode -halt-on-error main.tex
pdflatex -interaction=nonstopmode -halt-on-error main.tex
```

8. Inspect logs for undefined citations and references, duplicate labels, BibLaTeX warnings, missing glyphs, and overfull boxes.

## Scope Recommendation

Do not submit the old draft as a comprehensive review. Until substantially more directly verified literature is added, retain the narrower title and frame the paper as a critical review of:

- the progression from LSA/pLSA/LDA to neural, contextualized, and LLM-assisted methods; and
- the reliability and limits of topic-model evaluation.

## Repository State

The repository already contained a `README.md` describing a semantic-drift notebook. This handoff is deliberately stored separately so it does not overwrite that project documentation.
