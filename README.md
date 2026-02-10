# Sentence Similarity Model Selection using TOPSIS

---

## Project Overview

With the increasing availability of pre-trained NLP models for sentence similarity tasks, selecting the most suitable model becomes a multi-criteria decision-making problem. Different models offer trade-offs between semantic accuracy, inference speed, model size, and deployment feasibility.

This project applies **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** to systematically evaluate and rank multiple pre-trained sentence similarity models using both quantitative and qualitative criteria.

All generated results, rankings, and visualizations are stored inside:

Outputs/

---

## Objective

To identify the **most suitable pre-trained sentence similarity model** by:

- Evaluating multiple models on real sentence pairs  
- Considering both performance and deployment-related criteria  
- Applying the TOPSIS decision-making framework to rank models objectively  

---

## Models Considered

The following pre-trained models from the Sentence Transformers library were evaluated:

| Model ID | Model Name |
|-----------|-------------------------------|
| M1 | all-MiniLM-L6-v2 |
| M2 | all-mpnet-base-v2 |
| M3 | paraphrase-MiniLM-L12-v2 |
| M4 | distilbert-base-nli-stsb-mean-tokens |
| M5 | roberta-base-nli-stsb-mean-tokens |

---

## Dataset

Sentence pairs used for similarity evaluation are stored in:

data/sentence_pairs.csv

Each row contains:

- `sentence1`
- `sentence2`

Using a CSV-based dataset ensures reproducibility and allows easy scaling to larger evaluation datasets.

---

## Evaluation Criteria

Each model was evaluated using the following criteria:

| Criterion | Type | Description |
|------------|--------|-------------------------------|
| STS Score | Benefit ↑ | Average cosine similarity score |
| Inference Time (ms) | Cost ↓ | Time taken to compute embeddings |
| Model Size (MB) | Cost ↓ | Storage and deployment overhead |
| Embedding Dimension | Cost ↓ | Memory consumption |
| Deployment Ease | Benefit ↑ | Practical usability score (1–5) |

Benefit criteria are maximized, while cost criteria are minimized during TOPSIS computation.

---

## Criteria Weights

The relative importance of each criterion is defined as:

| Criterion | Weight |
|------------|--------|
| STS Score | 0.35 |
| Inference Time | 0.20 |
| Model Size | 0.15 |
| Embedding Dimension | 0.10 |
| Deployment Ease | 0.20 |

Semantic performance is prioritized, followed by speed and deployment feasibility.

---

## Methodology

The following steps were performed:

1. Generated sentence embeddings for each sentence pair using all models  
2. Computed cosine similarity scores  
3. Constructed a decision matrix using all evaluation criteria  
4. Normalized the decision matrix  
5. Applied weights to the normalized matrix  
6. Identified Positive Ideal Solution (best case) and Negative Ideal Solution (worst case)  
7. Computed Euclidean distances from ideal solutions  
8. Calculated TOPSIS closeness coefficients  
9. Ranked models based on TOPSIS scores  

---

## TOPSIS Formula

The closeness coefficient for each alternative is computed as:

CC_i = D_i^- / (D_i^+ + D_i^-)

Where:

- D_i^+ = Distance from the ideal best solution  
- D_i^- = Distance from the ideal worst solution  

A higher closeness coefficient indicates a better alternative.

---

## Results

The final TOPSIS rankings are stored in:

Outputs/ranking.csv

Key visualizations available in:

Outputs/

### TOPSIS Score Comparison

Outputs/topsis_scores.png

### Normalized Decision Matrix Heatmap

Outputs/normalized_heatmap.png

These visualizations provide a clear comparison of model rankings and the relative contribution of each evaluation criterion.

---

## Final Conclusion

Based on the TOPSIS analysis, **all-MiniLM-L6-v2** emerged as the most suitable model for sentence similarity tasks.

It achieves a strong balance between:

- High semantic similarity performance  
- Fast inference time  
- Compact model size  
- Ease of deployment  

This demonstrates the effectiveness of multi-criteria decision-making techniques in practical NLP model selection.

---

---

## Reproducibility

- All experiments were conducted using Google Colab  
- The notebook can be executed end-to-end  
- Fixed criteria weights ensure consistent ranking  
- Dataset stored in CSV format for reproducibility  

---

## Future Scope

This framework can be extended to:

- Larger benchmark datasets (STS Benchmark, Quora Question Pairs)  
- Other NLP tasks such as text classification or summarization  
- Alternative decision-making methods (AHP, VIKOR, ELECTRE)  
- Automated weight optimization strategies  

---

## Author

**Tanish Ahuja**
