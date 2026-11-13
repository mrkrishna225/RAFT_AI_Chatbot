# RAFT AI Engine — Retrieval-Augmented Fine-Tuning Pipeline

An end-to-end implementation of the Retrieval-Augmented Fine-Tuning (RAFT) methodology. It bridges domain RAG context with Supervised Fine-Tuning (SFT) to teach language models how to reason over external documentation and filter distractor information.

### 🛠️ Tech Stack & Topics
`raft` `rag` `fine-tuning` `databricks` `nvidia-nim` `llm` `python` `data-engineering`

---

### 📊 Pipeline Stages
1. **Data Ingestion & Cleaning:** Bronze lakehouse ingestion using PySpark on Databricks.
2. **Chunking & Question Generation:** Silver layer semantic splitting and synthetic question synthesis.
3. **Golden Chunk & Distractor Pairing:** Gold layer dataset preparation for fine-tuning.
4. **Answer Generation & Training:** NVIDIA NIM API integration for dataset curation and LoRA fine-tuning.

---

### 🚀 Getting Started
```bash
git clone https://github.com/mrkrishna225/RAFT_AI_Chatbot.git
cd RAFT_AI_Chatbot
```

<div align="center">
  <sub>Maintained by <a href="https://github.com/mrkrishna225"><b>mrkrishna225</b></a></sub>
</div>
