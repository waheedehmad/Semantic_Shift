```markdown
# Project README: Semantic Drift & Validation Pipeline

## Overview
This notebook implements a robust pipeline for detecting and validating **semantic drift** in specialized corpora (specifically combined ArXiv metadata and general text genres). It focuses on tracking how the meaning and context of a specific `SEED_WORD` (e.g., "cloud") changes over time relative to a fixed `ANCHOR_DEFINITION`.

## 1. Data Processing
- **Corpus Loading**: Merges `.txt` files from specific genres (Academic, Fiction, etc.) with ArXiv metadata JSONL files.
- **Temporal Alignment**: Organizes documents by year to create time-series slices for analysis.
- **Preprocessing**: Implements `simple_clean` to remove stopwords, handle lowercasing, and tokenize text.

2. Semantic Drift Methods
Word2Vec (W2V) Drift
- **Training**: Individual W2V models are trained per year.
- **Alignment**: Uses **Orthogonal Procrustes** to align yearly vector spaces to a `REFERENCE_YEAR` baseline.
- **Metrics**: Calculates **Positional Change** (Cosine Distance) and **Neighborhood Overlap** between the anchor definition and the seed word's trajectory.

### BERT Drift
- **Centroids**: Calculates the mean embedding (using `sentence-transformers`) for all sentences containing the seed word within a given year.
- **Sentence-Index Overlap**: A novel approach that tracks semantic stability by monitoring the overlap of the top-K most similar sentences across time.

## 3. Validation Pipeline
To verify if the detected drift is a true semantic shift or just noise, the pipeline uses two additional methods focused on a specific `analysis_span`:

- **Masked Language Modeling (MLM)**: Uses `bert-base-uncased` to predict replacements for the masked seed word. It calculates **Jensen-Shannon Divergence (JSD)** and **Rank Overlap** between adjacent years, supported by **Bootstrap Resampling** to provide confidence intervals.
- **BERTopic Reorganization**: Trains topic models on documents containing the seed word before and after a midpoint. It identifies **Emergent** and **Fading** topics to characterize the nature of the shift.

## 4. Directory & Output Structure
All outputs are saved to the `OUTPUT_BASE_DIR` defined in the first cell:

- `/plots/`: PNG visualizations of W2V and BERT drift metrics.
- `/drift_json/`: Detailed JSON files containing year-by-year metrics, fuzziness scores, and membership categories (Stable/Transitional/Unstable).
- `/topic_models/`: CSV and JSON summaries of the BERTopic clusters found during validation.
- `/validation_reports/`: The final integrated `semanticChangeReport` which combines MLM and Topic Modeling evidence into a single assessment (e.g., "Strong evidence for semantic shift").

## 5. Key Parameters
- `REFERENCE_YEAR`: The baseline year for W2V comparison.
- `analysis_span`: The specific years targeted for deep validation (e.g., 2008-2011).
- `fuzziness_score`: A metric derived from neighborhood overlap used to categorize the stability of the word's meaning.
```
