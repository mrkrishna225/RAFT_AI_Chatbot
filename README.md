# RAFT AI Chatbot

Implementation of the [RAFT paper](https://arxiv.org/abs/2403.10131) — Retrieval-Augmented Fine-Tuning.
The idea is to teach an LLM to answer questions using retrieved context by fine-tuning it on
(question, context, answer) triples where some of the context chunks are distractors.

## Pipeline

The pipeline follows a lakehouse pattern on Databricks:

1. **Bronze** — Raw documents ingested and landed
2. **Silver** — Documents chunked, questions generated from each chunk
3. **Gold** — Each question paired with its golden chunk + distractor chunks, answers generated via NVIDIA NIM API
4. **Training** — Fine-tune a base model (LoRA) on the gold dataset

## What you need

- Databricks workspace (or run the notebooks locally with PySpark)
- NVIDIA API key for answer generation
- HuggingFace token if pushing the fine-tuned model
- GPU compute for training (Kaggle/Colab free tier works for small runs)

## Structure

```
data_ingestion/    — Bronze layer notebooks
chunking/          — Silver layer: splitting + question gen
dataset_prep/      — Gold layer: distractor pairing + answer gen
training/          — LoRA fine-tuning notebooks
```

See the notebooks for detailed step-by-step instructions.
