**Author:** Lakshita Banothe  
**Institution:** IIIT Pune  
**Project Type:** B.Tech Research Project

## Highlights

- Developed an adaptive hallucination detection framework for Hindi QA.
- Evaluated hallucination behavior across BLOOM and Gemini.
- Introduced adaptive thresholding based on semantic consistency.
- Analyzed hallucination categories through manual taxonomy.
- Investigated RAG as a mitigation strategy.

- 
# THE FLUENCY TRAP

## Adaptive Consistency-Based Detection and RAG Mitigation of Hallucinations in Multilingual LLMs on Hindi QA

### Overview

Large Language Models (LLMs) often generate responses that are fluent and convincing but factually incorrect. This phenomenon, known as hallucination, becomes particularly challenging in low-resource languages such as Hindi, where evaluation resources are limited.

This project investigates hallucination behavior in multilingual LLMs on Hindi Question Answering tasks through consistency-based detection and Retrieval-Augmented Generation (RAG) mitigation. The study introduces an adaptive thresholding approach that adjusts hallucination detection according to model behavior rather than relying on fixed thresholds.

The central hypothesis of this work is that fluent responses are not necessarily reliable, leading to what we call the "Fluency Trap."

---

## Problem Statement

Traditional hallucination detection methods often rely on fixed thresholds and are primarily evaluated on English datasets. These approaches may not generalize effectively to Hindi and other low-resource languages.

This project aims to:

* Detect hallucinations in Hindi QA systems.
* Compare hallucination behavior across multilingual LLMs.
* Develop an adaptive consistency-based detection mechanism.
* Evaluate Retrieval-Augmented Generation (RAG) as a mitigation strategy.

---

## Research Questions

**RQ1:** Can semantic consistency be used to detect hallucinations in Hindi QA?

**RQ2:** How does hallucination behavior vary across different multilingual LLMs?

**RQ3:** Does Retrieval-Augmented Generation (RAG) improve reliability and reduce hallucinations?

---

## Models Evaluated

* BLOOM
* Gemini

Future work:

* Sarvam-1
* OpenHathi
* Other Indic language models

---
## Tech Stack

- Python
- Transformers
- Sentence Transformers (SBERT)
- Scikit-learn
- NumPy
- Pandas
- Matplotlib
- Google Gemini API
- Retrieval-Augmented Generation (RAG)

  ## Related Work

Hallucination detection has been studied through benchmarks such as TruthfulQA and HaluEval. Retrieval-Augmented Generation (RAG) has emerged as a common mitigation strategy for grounding model outputs. However, most existing evaluations focus on English-language models, leaving Hindi and other low-resource languages comparatively underexplored.

## Methodology

### Hallucination Detection Pipeline

Question
→ Multiple Response Generation
→ Sentence Embedding Extraction
→ Cosine Similarity Computation
→ Adaptive Threshold Calculation
→ Hallucination Classification

### Similarity Measurement

Semantic similarity is computed using sentence embeddings and cosine similarity.

Cosine Similarity:

Similarity(A,B) = (A · B) / (||A|| ||B||)

Higher similarity indicates greater consistency between independently generated responses.

---

## Adaptive Threshold

Instead of using a fixed threshold, this project uses:

Threshold = Mean Similarity − 0.5 × Standard Deviation

This allows the detection mechanism to adapt to the behavior of each model.

---

## Mitigation Strategy

Retrieval-Augmented Generation (RAG) is used to ground model responses using external information before generation.

Pipeline:

Question
→ Retrieval
→ Context Injection
→ Response Generation
→ Evaluation

---

## Results

### Model Consistency

| Model  | Mean Similarity |
| ------ | --------------- |
| BLOOM  | 0.288           |
| Gemini | 0.707           |

### Hallucination Detection

| Method             | Hallucination Rate |
| ------------------ | ------------------ |
| Fixed Threshold    | ~90%               |
| Adaptive Threshold | ~34%               |

### Adaptive Threshold Statistics (BLOOM)

| Metric             | Value  |
| ------------------ | ------ |
| Mean Similarity    | 0.2888 |
| Standard Deviation | 0.1743 |
| Adaptive Threshold | 0.2017 |

---
## Similarity Distribution

![BLOOM Similarity Distribution](graphs/bloom_similarity_graph.png)

## Hallucination Taxonomy

Detected hallucinations were manually classified into:

| Type                | Count |
| ------------------- | ----- |
| Fabrication         | 11    |
| Incomplete Response | 5     |
| Factual Error       | 1     |

Observation:

Most hallucinations were fabrications rather than minor factual mistakes, indicating that weaker multilingual models often generate unrelated or unsupported information.

---

## Key Findings

* Fixed thresholds significantly overestimate hallucination rates.
* Adaptive thresholding provides more realistic detection.
* Stronger models exhibit higher response consistency.
* Most hallucinations are fabrications.
* RAG effectiveness depends on model capability.
* Hindi hallucination evaluation remains underexplored.

---

## Repository Structure

Hindi-LLM-Hallucination-Detection/
└── git hallucination_trap/
    ├── data/
    ├── graphs/
    ├── notebook/
    ├── report/
    ├── result/
    └── requirements.txt

    
## Limitations

* Small evaluation dataset.
* Limited Gemini sample size due to API constraints.
* Adaptive threshold is heuristic-based.
* Human evaluation was not performed.

---

## Future Work

* Evaluate Sarvam-1 and OpenHathi.
* Expand Hindi QA datasets.
* Perform human evaluation studies.
* Explore advanced hallucination mitigation methods.
* Extend analysis to additional Indic languages.

---

## Conclusion

This project demonstrates that hallucination detection should be model-aware and data-driven rather than based on fixed thresholds. Through adaptive consistency analysis and RAG-based mitigation, the study provides insights into the reliability of multilingual LLMs on Hindi Question Answering tasks and highlights the challenges of deploying such systems in low-resource language settings.
