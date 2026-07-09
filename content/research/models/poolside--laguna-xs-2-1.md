---
title: "poolside/Laguna-XS-2.1"
org: poolside
model_id: poolside/Laguna-XS-2.1
date: 2026-07-10
tags:
  - huggingface
  - text-generation
  - coding
  - agentic
  - moe
  - openmdw
downloads: 6343
likes: 113
license: openmdw-1.1
pipeline: text-generation
source: https://huggingface.co/poolside/Laguna-XS-2.1
params: 3B active (33B total)
context: 262144
architecture: moe
---

# poolside/Laguna-XS-2.1

**One-line:** 33B MoE (3B active) agentic coding model with SWE-bench Verified 70.9% — purpose-built for local agent loops.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | — |
| HumanEval+ | — | — |
| MBPP | — | — |
| LiveCodeBench | — | — |
| Aider polyglot | — | — |
| SWE-bench Verified | 70.9% | poolside (lab-reported, Harbor Framework) |
| SWE-bench Multilingual | 63.1% | poolside (lab-reported, Harbor Framework) |
| SWE-bench Pro | 47.6% | poolside (lab-reported) |
| Terminal-Bench 2.0 | 37.5% | poolside (lab-reported) |

## Agentic / tool-use benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| BFCL | — | — |
| τ-Bench | — | — |
| ToolACE | — | — |
| GAIA | — | — |
| WebArena / Mind2Web | — | — |

## Reasoning (context only)

| Benchmark | Score | Source |
|:---|---:|:---|
| MMLU / MMLU-Pro | — | — |
| GPQA Diamond | — | — |
| MATH | — | — |
| AIME 2025 | — | — |

## Efficiency

- **Active params:** 3B (total 33B MoE: 256 experts + 1 shared)
- **Context length:** 262,144 tokens
- **VRAM (fp16 rough):** ~6 GB (active weights only)

## What makes it notable

Laguna XS 2.1 is poolside's second-gen 3B-active MoE explicitly designed for *agentic coding on local hardware* — 33B total params, 262K context, FP8 KV cache, mixed SWA/global attention (3:1 across 40 layers), native reasoning with interleaved thinking between tool calls. Beats its predecessor Laguna XS.2 by +5.4pp on SWE-bench Multilingual (63.1% vs 57.7%) and leads all open-weight models <70B on SWE-bench Verified (70.9%) per the lab's Harbor Framework runs (mean pass@1 over 4 attempts). Launch-day support in vLLM, SGLang, Transformers, TRT-LLM, llama.cpp, Ollama. OpenMDW-1.1 license (commercial-friendly). The DFlash 5-layer speculator (~70% acceptance on coding) is available for speculative decoding. This is the strongest open-weight *agentic coding* model in the 1B–70B active-param range for local deployment.

## See also

- [[welcome]]
- Source: https://huggingface.co/poolside/Laguna-XS-2.1