# Thierry-Places-Conflation
Project C: Places conflation with scalable language models.
Team members: Thierry Nguyen

Comparing the performance of various language models against traditional methods for matching duplicate place records.

# OKRs
O1: Achieve High Accuracy with a Baseline LLM Methodology.

KR 1.1: Develop curated datasets, labeling records with missing data and foreign cases for future and current use with ≥300 records each.

KR 1.2: Achieve a macro F1​-Score of ≥0.8 and a PR-AUC score of ≥0.9 with a selected baseline methodology on the general dataset (All records mixed together).

KR 1.3: Score an F1​-Score of ≥0.7 and a PR-AUC score of ≥0.8 using a single or multiple baseline methodologies in the two separate test segments: missing data and foreign cases.

O2: Establish a Favorable Price-to-Performance Ratio.

KR 2.1: Fine-tune/improve a chosen methodology for each test segment to achieve an F1​-Score that is ≥0.01 percentage points higher than the current Overture matcher’s scores. Test segments: General, missing data, foreign

KR 2.2: Validate the methodologies in KR 2.1 with the PR-AUC metric to score ≥0.95 on each test segment.

KR 2.3: Tweak the final methodologies to deliver a Price-to-Performance (Metric/Cost) Ratio ≥5% higher than the current Overture matcher's ratio.

# Methodology
XGBoost Classifier with the following features:
- Embedding cosine similarities for: Name, Normalized Address, Category
- Normalized phone match (binary)
- Normalized website match (binary)
- Exact category string match (binary)
- Token ratio for: Name, Normalized Address
- Partial ratio for: Name, Normalized Address
- Difference in name string length
- Difference in name word count

# Results
|Model Name                                                 |F1-Score|F1-Score (Non-US) |F1-Score (Missing Data)|Average F1 CV Scores|Accuracy|Accuracy (Non-US)|Accuracy (Missing Data)|PR-AUC|PR-AUC (Missing Data)|PR-AUC (Non-US Data)|Total Test Time|Parameters|
|-----------------------------------------------------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|----|
|intfloat/multilingual-e5-base                              |0.898|0.887|0.736|0.896|0.873|0.873|0.839|0.968|0.787|0.913|1.496|300M|
|BAAI/bge-m3                                                |0.904|0.902|0.8  |0.898|0.882|0.889|0.871|0.971|0.832|0.921|4.782|560M|
|sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2|0.9  |0.885|0.667|0.892|0.877|0.87 |0.806|0.967|0.74 |0.91 |1.219|100M|
|Alibaba-NLP/gte-multilingual-base                          |0.901|0.892|0.778|0.896|0.877|0.879|0.871|0.968|0.836|0.917|2.055|300M|
|google/embeddinggemma-300m                                 |0.893|0.876|0.737|0.899|0.87 |0.863|0.839|0.969|0.787|0.909|5.622|300M|
|Qwen/Qwen3-Embedding-0.6B                                  |0.897|0.888|0.737|0.893|0.872|0.873|0.839|0.968|0.787|0.912|9.271|600M|
|intfloat/multilingual-e5-large                             |0.899|0.896|0.8  |0.898|0.875|0.883|0.871|0.965|0.832|0.919|4.815|600M|
|Mixed (gte-multilingual-base + embeddinggemma-300m)        |0.913|0.915|0.9  |0.891|0.893|0.905|0.935|0.972|0.916|0.93 |4.395|300M + 300M|

# Running the Notebook
Run all cells in pipeline_classifier.ipynb

Notes:
- The last cell (large models) may require a high-resource GPU to run.
- Results may change depending on the GPU. Results were obtained using an L4 GPU on Colab.
- Large model results are not kept as they required too much compute power for little return.

# Presentation Slides
https://docs.google.com/presentation/d/1txU15XmII2ghk9K_GLlG7TYuxs73wtAh-FUAtyd2Yeg/edit?usp=sharing
