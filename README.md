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
|Model Name                                                 |F1-Score          |F1-Score (Non-US) |F1-Score (Missing Data)|Average F1 CV Scores|Accuracy          |Accuracy (Non-US) |Accuracy (Missing Data)|PR-AUC            |PR-AUC (Missing Data)|PR-AUC (Non-US Data)|Total Test Time   |
|-----------------------------------------------------------|------------------|------------------|-----------------------|--------------------|------------------|------------------|-----------------------|------------------|---------------------|--------------------|------------------|
|intfloat/multilingual-e5-base                              |0.8981233243967829|0.8870056497175142|0.7368421052631579     |0.8960889383534678  |0.8733333333333333|0.873015873015873 |0.8387096774193549     |0.9675653822503054|0.7872759856630824   |0.9128557082889149  |1.4958824889995412|
|BAAI/bge-m3                                                |0.9044414535666218|0.9019607843137255|0.8                    |0.8983874888259988  |0.8816666666666667|0.8888888888888888|0.8709677419354839     |0.9706213489039863|0.832258064516129    |0.9218655381227635  |4.782108159000018 |
|sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2|0.9               |0.8851540616246498|0.6666666666666666     |0.8917712531925691  |0.8766666666666667|0.8698412698412699|0.8064516129032258     |0.9673344093650141|0.739516129032258    |0.909804748740411   |1.2189561959999082|
|Alibaba-NLP/gte-multilingual-base                          |0.9005376344086021|0.8920454545454546|0.7777777777777778     |0.8956326509928422  |0.8766666666666667|0.8793650793650793|0.8709677419354839     |0.9683572449097698|0.8358870967741936   |0.917701536863871   |2.0550105600004827|
|google/embeddinggemma-300m                                 |0.8934426229508197|0.8760806916426513|0.7368421052631579     |0.898777603074203   |0.87              |0.8634920634920635|0.8387096774193549     |0.9689751868611981|0.7872759856630824   |0.9094213009102385  |5.6222821879996445|
|Qwen/Qwen3-Embedding-0.6B                                  |0.897196261682243 |0.8876404494382022|0.7368421052631579     |0.8927840838354945  |0.8716666666666667|0.873015873015873 |0.8387096774193549     |0.9684011187607866|0.7872759856630824   |0.9121509117244927  |9.271167318000153 |
|intfloat/multilingual-e5-large                             |0.8990578734858681|0.895774647887324 |0.8                    |0.8981477798843057  |0.875             |0.8825396825396825|0.8709677419354839     |0.965165143765579 |0.832258064516129    |0.9185729812897443  |4.815060227999766 |
|Mixed                                                      |0.9130434782608695|0.9147727272727273|0.9                    |0.8907165300712008  |0.8933333333333333|0.9047619047619048|0.9354838709677419     |0.9723142012886452|0.9161290322580645   |0.934086208513825   |4.395108143000016 |


