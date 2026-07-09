---
title: "metaresearch/PapersRAG-1.5B"
org: metaresearch
model_id: metaresearch/PapersRAG-1.5B
date: 2026-07-10
tags:
  - huggingface
  - text-generation
  - rag
  - question-answering
  - scientific-literature
  - apache-2.0
downloads: 5603
likes: 0
license: apache-2.0
pipeline: text-generation
source: https://huggingface.co/metaresearch/PapersRAG-1.5B
params: 1.5B (dense)
context: unknown
architecture: dense
---

# metaresearch/PapersRAG-1.5B

**One-line:** RAG system (Qwen2.5-1.5B + FAISS index of arXiv cs.CL abstracts) — NOT a general-purpose coding/agent model.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | — |
| HumanEval+ | — | — |
| MBPP | — | — |
| LiveCodeBench | — | — |
| Aider polyglot | — | — |
| SWE-bench Verified | — | — |
| SWE-bench Multilingual | — | — |

## Agentic / tool-use benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| BFCL | — | — |
| τ-Bench | — | — |
| ToolACE | — | — |
| GAIA | — | — |

## Reasoning (context only)

| Benchmark | Score | Source |
|:---|---:|:---|
| MMLU / MMLU-Pro | — | — |
| GPQA Diamond | — | — |
| MATH | — | — |
| AIME 2025 | — | — |

## Efficiency

- **Active params:** 1.5B (Qwen2.5-1.5B base)
- **Context length:** Not specified (depends on retrieval pipeline)
- **VRAM (fp16 rough):** ~3 GB for LM alone; + index memory

## What makes it notable

PapersRAG-1.5B is a **retrieval-augmented generation pipeline**, not a standalone model. It pairs Qwen2.5-1.5B with a daily-updated FAISS index of arXiv cs.CL abstracts (dense bi-encoder retrieval + cross-encoder re-ranking). The model card explicitly states: *"It is not a general-purpose chatbot"* and *"No coding benchmarks published."* It refuses to answer when retrieval confidence is low. For an agent-loop user piping models into Aider/Codex/Claude Code, this is the wrong tool — it's a vertical research assistant for NLP paper QA, updated daily via automated pipeline. Skip for coding/agent tracking.

## See also

- [[welcome]]
- Source: https://huggingface.co/metaresearch/PapersRAG-1.5B