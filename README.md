# Multi-Class News Classification Engine

A high-accuracy, cost-efficient NLP pipeline utilizing fine-tuned transformer models (**DeBERTa** and **XLM-RoBERTa**) to classify real-world news content into 6 distinct topical categories with **96.7% accuracy**. 

This repository contains the training, optimization, and validation workflows designed to power automated, live data streams.

---

## 🚀 Overview & Engineering Strategy

In modern NLP applications, relying on massive generative LLM APIs (like GPT-4) for classification tasks introduces unnecessary latency, high operational costs, and non-deterministic outputs. 

This project takes a **production-first engineering approach** by fine-tuning highly efficient, task-specific bidirectional encoder models. By optimizing smaller architectures, this classification engine achieves near-perfect accuracy while remaining highly cost-effective, offering ultra-low inference latency, and running seamlessly in a localized automated data pipeline.

### Key Metrics
* **Accuracy:** 96.7% across 6 categories.
* **Architecture:** DeBERTa (for optimal English context understanding) & XLM-RoBERTa (for cross-lingual stability).
* **Efficiency:** Localized encoder inference, bypassing expensive external API overhead.

---

## 🛠️ Tech Stack & Key Libraries

* **Core Framework:** PyTorch
* **Model Hub & Pipeline:** Hugging Face (Transformers, Datasets, Accelerate)
* **Optimization:** AdamW optimizer with a linear learning rate scheduler and weight decay.
* **Tracking & Logging:** Hugging Face Notebook Weights & Biases / Progress Widgets.

---

## 📊 Model Selection & Rationale

| Model | Primary Use Case | Why It Was Chosen |
| :--- | :--- | :--- |
| **DeBERTa** | English Content Classification | Utilizes a disentangled attention mechanism, significantly outperforming standard BERT/RoBERTa variants on token-level and sequence-level context modeling. |
| **XLM-RoBERTa** | Cross-Lingual & Multi-Source Stability | Pre-trained on a massive multi-lingual corpus, ensuring the classification pipeline remains robust when digesting international news sources and varied syntax. |

---

## 🔧 Training & Optimization Workflow

To achieve **96.7% accuracy**, the training pipeline implemented strict data hygiene and optimization guardrails:

1. **Data Preprocessing & Tokenization:** Handled text normalization, context truncation, and dynamic padding using specialized Hugging Face tokenizers (`tokenizer_config.json`).
2. **Overfitting Mitigation:** Integrated strict weight decay (`weight_decay`) and a linear learning rate warmup schedule to prevent the model from memorizing training data.
3. **Loss Tracking:** Monitored cross-entropy loss across training and validation splits to guarantee stable convergence.

---

## 🚀 How It Fits Into the Pipeline

This repository acts as the standalone core intelligence module for a broader news aggregation system.
