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
- Name embedding cosine similarity
- Normalized address embedding cosine similarity
- Category embedding cosine similarity
- Normalized phone match (binary)
- Exact category string match (binary)
- Difference in name string length
- Difference in name word count

# Results
