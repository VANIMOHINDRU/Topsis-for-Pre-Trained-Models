# TOPSIS-Based Selection of Pre-trained Conversational Models

## 1. Project Overview

This project performs a comparative analysis of multiple pre-trained **conversational AI models** available on Hugging Face and selects the most suitable model using the **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)** multi-criteria decision-making method.

Conversational models vary in terms of response richness, linguistic diversity, efficiency, and stability. Since training or deeply benchmarking large language models is computationally expensive, this project adopts a **lightweight empirical evaluation strategy** combined with TOPSIS to make an informed and justifiable selection.

---

## 2. Objective

The objectives of this project are:

- To analyze multiple text conversational models
- To empirically evaluate them using quantitative proxy-based metrics
- To apply the TOPSIS methodology for multi-criteria ranking
- To identify the best-performing conversational model

---

## 3. Models Evaluated

Five conversational models were selected to ensure diversity in architecture and capability while remaining feasible for CPU-based evaluation.

| Model Name | Architecture | Description |
|----------|-------------|-------------|
| DialoGPT-small | Causal LM | Lightweight conversational model |
| DialoGPT-medium | Causal LM | Improved dialogue quality |
| BlenderBot-400M-distill | Seq2Seq | Dialogue-focused conversational model |
| Flan-T5-small | Seq2Seq | Instruction-tuned conversational model |
| Flan-T5-base | Seq2Seq | Higher-capacity instruction-tuned model |

Each model was instantiated using a **task-appropriate Hugging Face pipeline** to ensure architectural compatibility during text generation.

---

## 4. Evaluation Methodology

### 4.1 Prompt Design

All models were evaluated using the same set of conversational prompts to ensure fairness and reproducibility:

- Explain artificial intelligence in simple words.
- Why is data security important?
- What is machine learning?
- How does AI help in healthcare?
- Explain cloud computing briefly.

---

### 4.2 Proxy-Based Evaluation Rationale

Conversational models generate free-form text and do not have a single ground-truth output. Therefore, traditional metrics such as accuracy, BLEU, or ROUGE are not suitable.

Instead, this project uses **proxy-based quantitative metrics** extracted directly from generated responses. These metrics are:

- Automatically computed
- Reproducible
- Derived from actual model behavior
- Suitable for multi-criteria decision-making

---

## 5. Evaluation Parameters (Criteria)

Five empirical parameters were computed for each model:

| Parameter | Type | Description |
|---------|------|------------|
| Average Response Length | Benefit | Indicates informativeness |
| Maximum Response Length | Benefit | Captures context handling |
| Vocabulary Richness | Benefit | Measures linguistic diversity |
| Repetition Rate | Cost | Measures redundancy |
| Response Time (seconds) | Cost | Measures inference efficiency |

**Benefit criteria** → higher values are better  
**Cost criteria** → lower values are better  

---

## 6. Decision Matrix Construction

For each model:
1. Responses were generated for all prompts.
2. Text-based metrics (length, vocabulary diversity, repetition) were extracted.
3. Response time was measured using execution latency.
4. Mean values across prompts were used to construct the decision matrix.

This matrix serves as the input to the TOPSIS algorithm.

### 📸 Features Used

![Matrix](images/pred2(1)(1).png)

---

## 7. TOPSIS Methodology

TOPSIS ranks alternatives based on their distance from an **ideal best** and an **ideal worst** solution.

The following steps were followed:

1. Normalize the decision matrix  
2. Apply criterion weights  
3. Identify ideal best and ideal worst solutions  
4. Compute distances from ideal solutions  
5. Calculate TOPSIS scores  
6. Rank models based on closeness to the ideal solution  

### Criteria Weights

| Criterion | Weight |
|---------|--------|
| Avg Response Length | 0.25 |
| Max Response Length | 0.20 |
| Vocabulary Richness | 0.20 |
| Repetition Rate | 0.15 |
| Response Time | 0.20 |

---
### 📸 Final Results

![TOPSIS Execution](images/pred2(1)(2).png)

## 8. Results and Ranking

Each model receives:
- A TOPSIS score
- A rank based on multi-criteria performance

The model with the highest TOPSIS score is selected as the **most suitable conversational model** under the chosen criteria.

A bar chart visualization is generated to compare model performance.

### 📸 Bar Chart

![Bar Chart](images/pred2(1)(3).png)

---

## 9. Key Observations

- Instruction-tuned models generally provide richer and more diverse responses.
- Smaller models respond faster but often produce shorter outputs.
- Lower repetition rates indicate more natural conversational behavior.
- TOPSIS effectively balances quality and efficiency across models.

---

## 10. Conclusion

This project demonstrates that TOPSIS is an effective decision-making tool for selecting conversational AI models when multiple qualitative and quantitative factors must be considered simultaneously.

By combining empirical proxy-based evaluation with multi-criteria decision analysis, the approach avoids subjective scoring while remaining computationally feasible.

---

## 11. Project Structure

