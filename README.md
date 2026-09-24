# Amazon Fake Review Detection in the LLM Era

Code accompanying my master's thesis, which looks at whether the rate and detectability of fake Amazon reviews changed after large language models became widely available. The project brings together an official historical dataset and data I collected myself, adds a synthetic gold-standard set, and compares four classifiers across three research questions.

## What's in this repo

| File | What it does |
|---|---|
| `batch1_scraper.ipynb` | Playwright scraper for Amazon.de "All Beauty" reviews (batch 1), including language detection and translation to English |
| `batch2_scraper.ipynb` | Same scraper, run again for batch 2 (different products, no overlap with batch 1) |
| `r1r2r3all.ipynb` | Everything downstream: merging both batches with the McAuley dataset, computing weak-supervision labels, the RQ1 MLE trend analysis with logistic-regression robustness checks, generating the synthetic gold-standard set, and the RQ2/RQ3 classifier comparison (TF-IDF+SVM vs. three zero-shot LLMs, the cross-lingual test, and the generator comparison) |

## Data

This repo doesn't include any raw data.

The official McAuley Amazon Reviews 2023 dataset is publicly available at [huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023](https://huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023). I only used the "All Beauty" category, from 2000 through September 2023. The 2024–2026 data, which I collected myself with `batch1_scraper.ipynb` and `batch2_scraper.ipynb`, isn't shared here, following the data-handling approach described in the thesis. Worth noting: Amazon reviewer account identifiers in any sample outputs from the raw scraper data have been masked or removed before being published in this repo.

## Requirements

Python 3.10+. Main dependencies: `playwright`, `pandas`, `numpy`, `langdetect`, `deep-translator`, `openai`, `ollama`, `statsmodels`, `matplotlib`.

## More context

The full methodology, results, and discussion are in the thesis itself: *Fake Reviews in the LLM Era: A Temporal and Cross-Lingual Analysis of Amazon Product Reviews* (Gisma University of Applied Sciences, 2026).
