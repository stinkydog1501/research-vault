---
title: "MetaResearch PapersRAG 1.5B"
org: metaresearch
model_id: metaresearch/PapersRAG-1.5B
date: 2026-07-05
tags:
  - huggingface
  - text-generation
  - rag
  - research-tool
  - scientific-literature
downloads: 1602
likes: 0
license: apache-2.0
pipeline: text-generation
source: https://huggingface.co/metaresearch/PapersRAG-1.5B
params: 1.5B
context: 2048
architecture: dense
---

# MetaResearch PapersRAG 1.5B

**One-line:** Retrieval-augmented generation system for querying recent scientific literature with daily auto-updates from arXiv cs.CL.

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
- **Context length:** 2048 tokens (base model default)
- **VRAM (fp16 rough):** ~3 GB (1.5B params × 2 bytes)
- **Architecture:** Dense transformer with RAG pipeline (bi-encoder retrieval + cross-encoder re-ranking + LM generation)

## What makes it notable

PapersRAG-1.5B is a specialized RAG system rather than a general-purpose coding model. It pairs Qwen2.5-1.5B with a FAISS index of arXiv cs.CL paper abstracts, updated daily via automated pipeline. The system uses dense retrieval + cross-encoder re-ranking to provide citation-backed answers. While not designed for coding tasks, it could serve as a research assistant component in agentic loops that need scientific literature context. The Apache-2.0 license and small size make it suitable for local deployment. However, it lacks coding/agentic benchmarks and is limited to English-language cs.CL papers only.

## See also

- [[welcome]]
- Source: https://huggingface.co/metaresearch/PapersRAG-1.5B
