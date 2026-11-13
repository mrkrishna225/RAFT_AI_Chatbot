# RAFT AI Chatbot

Implementation of the [RAFT paper](https://arxiv.org/abs/2403.10131) (Retrieval-Augmented Fine-Tuning).

The idea: teach an LLM to answer questions using retrieved context by fine-tuning it on
(question, context, answer) triples where some of the context chunks are intentionally
irrelevant distractors. This forces the model to learn which chunks actually matter.

## Pipeline

Follows a lakehouse pattern (Bronze / Silver / Gold):

1. **Bronze** — Raw documents ingested into storage
2. **Silver** — Documents chunked into passages, synthetic questions generated per chunk
3. **Gold** — Each question paired with its golden chunk + distractor chunks.
   Answers generated using NVIDIA NIM API
4. **Training** — Fine-tune a base model with LoRA on the gold `.jsonl` dataset

## Prerequisites

- Databricks workspace (or run notebooks locally with PySpark)
- NVIDIA API key (for answer generation in the Gold step)
- HuggingFace token (for downloading base models / pushing fine-tuned models)
- GPU compute for training — Kaggle or Colab free tier works for small experiments

## Notebooks

The pipeline is a series of Jupyter/Databricks notebooks. Each one is self-contained
with instructions at the top. Run them in order:

```
1. data_ingestion    -> land raw docs (Bronze)
2. chunking          -> split + generate questions (Silver)
3. dataset_prep      -> pair chunks + generate answers (Gold)
4. training          -> LoRA fine-tuning
```

## Security note

Don't hardcode API keys in notebook cells. Use environment variables, Databricks secret
scopes, or Azure Key Vault.
