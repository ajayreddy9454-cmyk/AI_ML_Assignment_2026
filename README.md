# AI / ML Internship Assignment

This repository contains implementations for three assignment tasks.

## Folder structure

- `Task_1_Fine_Tuning/` — Qwen2.5-0.5B-Instruct LoRA fine-tuning notebook and adapter archive.
- `Task_2_RAG/` — RAG implementation notebook, NIST AI RMF source PDF, evaluation CSV, and task report.
- `Task_3_Local_Optimization/` — FP16 vs 4-bit NF4 benchmark notebook and CSV results.
- `Final_Submission/` — final four-page technical report.

## Task summaries

### Task 1 — LoRA fine-tuning
Qwen2.5-0.5B-Instruct was fine-tuned with LoRA for JSON extraction. The held-out exact JSON match increased from 2% to 56% on 50 test examples. The adapter is included as `qwen_json_lora_adapter.zip`.

### Task 2 — RAG
A RAG pipeline was built over the 48-page NIST AI Risk Management Framework using PyMuPDF, all-MiniLM-L6-v2 embeddings, FAISS and Groq generation. Page-level Recall@5 was 100% for 500-character chunks and 93.33% for 1,000-character chunks on 15 questions.

### Task 3 — Local optimization
Qwen2.5-0.5B-Instruct was benchmarked on a Tesla T4. FP16 achieved 20.52 tokens/s and 0.932 GB peak allocated memory; 4-bit NF4 achieved 8.93 tokens/s and 0.438 GB. The 4-bit setup reduced memory but was slower in this test.

## Reproduction

1. Open the relevant `.ipynb` notebook in Google Colab.
2. Select a GPU runtime.
3. Run notebook cells in order.
4. For Task 2, enter your own Groq API key securely when prompted. Never commit API keys or secrets.
5. Review the final report for metric definitions and limitations.

## Important limitations

- Task 1 evaluation used 50 held-out examples.
- Task 2 Recall@5 is page-level, not exact-passage-level; the evaluation set had 15 questions.
- Task 3 was measured on a Tesla T4; the 24 GB / 20-user result is a simplified estimate, not a live concurrency test.
- BM25 and reranking were explained as potential RAG improvements but were not implemented or benchmarked.
