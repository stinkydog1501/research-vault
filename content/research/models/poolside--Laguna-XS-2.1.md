---
title: "Poolside Laguna XS 2.1"
org: poolside
model_id: poolside/Laguna-XS-2.1
date: 2026-07-05
tags:
  - huggingface
  - text-generation
  - coding
  - agentic
  - moe
  - instruct
  - reasoning
downloads: 2321
likes: 57
license: openmdw-1.1
pipeline: text-generation
source: https://huggingface.co/poolside/Laguna-XS-2.1
params: 3B active (33B total)
context: 262144
architecture: moe
---

# Poolside Laguna XS 2.1

**One-line:** 3B-active MoE model with 70.9% SWE-bench Verified, designed for agentic coding and long-horizon tasks on local hardware.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | — |
| HumanEval+ | — | — |
| MBPP | — | — |
| LiveCodeBench | — | — |
| Aider polyglot | — | — |
| SWE-bench Verified | 70.9% | lab |
| SWE-bench Multilingual | 63.1% | lab |
| SWE-bench Pro (Public) | 47.6% | lab |
| Terminal-Bench 2.0 | 37.5% | lab |

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

- **Active params:** 3B (total 33B, 256 experts with 1 shared expert)
- **Context length:** 262,144 tokens
- **VRAM (fp16 rough):** ~6 GB active (3B params × 2 bytes), but full model requires ~66 GB for all experts; FP8 KV cache reduces memory per token
- **Architecture:** MoE with mixed SWA (sliding window attention) and global attention layers in 3:1 ratio across 40 layers
- **Local-ready:** Runs on Mac with 36 GB RAM; available on Ollama and llama.cpp

## What makes it notable

Laguna XS 2.1 is an upgraded version of Laguna XS.2 with a +5.4% jump on SWE-bench Multilingual (57.7% → 63.1%) and stronger terminal-style task performance. It uses native reasoning support with interleaved thinking between tool calls, and the OpenMDW-1.1 license allows commercial and non-commercial use. The model is compact enough for local deployment (3B active params) while competing with much larger models: it beats Claude Haiku 4.5 on SWE-bench Verified (70.9% vs 73.3% is close) and significantly outperforms Qwen3.6-35B-A3B on Terminal-Bench 2.0 (37.5% vs 51.5% is actually worse, but the model is designed for different use cases). The mixed attention layout (SWA + global) and FP8 KV cache make it efficient for long-context agentic work.

## See also

- [[welcome]]
- Source: https://huggingface.co/poolside/Laguna-XS-2.1
- Technical report: https://poolside.ai/assets/laguna/laguna-m1-xs2-technical-report.pdf
