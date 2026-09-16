# Scholarship & Mobility Advisor — RAG System

A Retrieval-Augmented Generation (RAG) system that answers questions about worldwide
scholarship and student mobility programs (Erasmus, Mevlana, Fulbright, DAAD, Chevening,
MEXT, and more), demonstrating how grounding an LLM's answers in retrieved context
reduces hallucination compared to the model answering from its own knowledge alone.

## How it works
- **Knowledge base:** 70 documents covering scholarship requirements, grants, and
  eligibility criteria, generated with LLM assistance.
- **Retrieval:** documents embedded with `sentence-transformers/all-MiniLM-L6-v2`,
  indexed with FAISS for fast semantic search.
- **Generation:** retrieved context is passed to `google/flan-t5-small`, with a prompt
  that restricts the model to only use the provided context — no invented numbers,
  thresholds, or deadlines.
- **Evaluation:** compares answers generated with no retrieval versus RAG at top_k=3
  and top_k=5, showing how grounding improves answer accuracy and reduces fabrication.

## Setup
```bash
pip install sentence-transformers faiss-cpu transformers torch
```

## Usage
Open `ScholarshipAdvisorRAG.ipynb` and run all cells. Modify the `query` variable
in the comparison section to ask your own scholarship-related questions.

## Tech stack
Python, Sentence-Transformers, FAISS, Hugging Face Transformers (FLAN-T5)
