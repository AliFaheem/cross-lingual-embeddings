# Cross-Lingual Embedding Alignment for Urdu-English Retrieval

This repository contains code and artifacts for our LREC 2026 work on post-hoc Procrustes alignment for Urdu-English cross-lingual retrieval and QA.

## Overview
We evaluate multilingual embedding models before and after Procrustes alignment on three axes:
- Geometric alignment (cosine distance between parallel sentence pairs)
- Cross-lingual retrieval (Recall@1/3/5)
- Downstream QA quality (RAGAS + EM/F1)

## Repository Contents
- `pipeline.ipynb`: Main experiment pipeline (data prep, alignment, retrieval)
- `pipeline_2.ipynb`: Extended experiments (RAGAS + generation evaluation)
- `Cross_Lingual_Embeddings_LREC_2026.pdf`: Paper draft
- `data/README.md`: Dataset access and preparation notes
- `results/`: Structured metric exports for tables/figures

## Dataset Summary (reported run)
- SQuAD train rows: 87,599
- UQA train rows: 124,745
- Aligned intersection pairs: 83,018
- Unique English contexts indexed: 18,857
- Urdu query pool: 18,828
- Procrustes split (alignment): 15% train / 85% test
- Retrieval split: 70% train / 30% test

## Key Reported Results
- MiniLM retrieval Recall@1: 0.3871 -> 0.4059 (after alignment)
- LaBSE retrieval Recall@1: 0.3024 -> 0.4273 (after alignment)
- RAGAS faithfulness/context metrics improve across evaluated models
- Generation EM/F1 gains are strongest for weaker pre-alignment models

## Reproducibility
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Run notebooks in order:
   1. `pipeline.ipynb`
   2. `pipeline_2.ipynb`
3. Export tables to `results/` as CSV for paper-ready artifacts.

## Notes
- `Squad.csv` is intentionally excluded from git due GitHub size limits (>100MB).
- Do not commit secrets (`.env`, API keys, tokens).
- Some RAGAS runs may log `LLMDidNotFinishException`; report this in limitations.

## Citation
See `CITATION.cff`.
