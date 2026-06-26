---
title: "DeepSeek-V4-Flash"
org: deepseek-ai
model_id: deepseek-ai/DeepSeek-V4-Flash
date: 2026-06-26
tags:
  - huggingface
  - text-generation
  - coding
  - agentic
  - moe
  - deepseek-v4
  - mla
  - fp8
  - fp4
  - million-token-context
  - reasoning
  - instruct
downloads: 2146642
likes: 1597
license: mit
pipeline: text-generation
source: https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash
params: "13B active / 284B total (MoE, top-6 of 256 routed + 1 shared)"
context: "1M tokens"
architecture: moe
---

# DeepSeek-V4-Flash

**One-line:** Compact 13B-active MoE variant of the DeepSeek-V4 line — hits 79.0 SWE-bench Verified (Flash-Max) and 91.6 LiveCodeBench while only activating 13B per token; weights are FP4+FP8 mixed and require custom inference.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | not published for this variant |
| HumanEval+ | — | not published |
| MBPP | — | not published for this variant |
| LiveCodeBench | 91.6 | lab (V4-Flash Max mode) |
| Aider polyglot | — | not published |
| SWE-bench Verified | 79.0 | lab (V4-Flash Max mode) |
| SWE-bench Multilingual | 73.3 | lab (V4-Flash Max mode) |
| Codeforces (rating) | 3052 | lab (V4-Flash Max mode) |

*LiveCodeBench rises sharply across reasoning modes: Non-Think 55.2 → Think High 88.4 → Think Max 91.6 — at High mode Flash already approaches Opus-4.6 Max (88.8) and Gemini-3.1-Pro High (91.7).*

## Agentic / tool-use benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| BFCL | — | not published for this variant |
| τ-Bench | — | not published |
| ToolACE | — | not published |
| GAIA | — | not published |
| Terminal Bench 2.0 | 56.9 | lab (V4-Flash Max mode) |
| SWE Pro | 52.6 | lab (V4-Flash Max mode) |
| BrowseComp | 73.2 | lab (V4-Flash Max mode) |
| MCPAtlas (Public) | 69.0 | lab (V4-Flash Max mode) |
| Toolathlon | 47.8 | lab (V4-Flash Max mode) |

*Agentic scores are competitive with much larger open-weight peers; SWE Pro at 52.6 is strong for a 13B-active model. BFCL not published separately — when running locally, tool-calling capability should be smoke-tested against your own function schemas before deploying.*

## Reasoning (context only)

| Benchmark | Score | Source |
|:---|---:|:---|
| MMLU-Pro | 86.2 | lab (V4-Flash Max mode) |
| GPQA Diamond | 88.1 | lab (V4-Flash Max mode) |
| MATH | — | not published for this variant |
| AIME 2025 | — | not published; HMMT 2026 Feb = 94.8 |
| HLE | 34.8 | lab (V4-Flash Max mode) |

## Efficiency

- **Active params:** 13B (per token — top-6 of 256 routed + 1 shared)
- **Total params:** 284B (full disk-resident weight footprint)
- **Context length:** 1,048,576 tokens (1M) via YaRN rope scaling; recommend ≥384K context for Think Max mode
- **VRAM (fp16 rough):** ~26 GB active-params equivalent at runtime; full weights ~284 GB on disk (FP4 experts + FP8 other)
- **Precision:** MoE expert weights are FP4, most other parameters are FP8 — requires DeepSeek's custom `encoding` + `inference` scripts (vLLM/SGLang/TensorRT-LLM support is preliminary at release time)
- **Architecture:** Hybrid attention — Compressed Sparse Attention (CSA) + Heavily Compressed Attention (HCA); Manifold-Constrained Hyper-Connections (mHC); Muon optimizer in pretraining

## What makes it notable

DeepSeek-V4-Flash is the smaller of two MoE siblings in the V4 line and is the first open-weight release where the Flash-Max mode pushes **SWE-bench Verified to 79.0** at only **13B active params per token** — within ~2 points of Opus-4.6 Max (80.8) and ahead of GPT-5.4 (not published), Gemini-3.1-Pro High (80.6), and K2.6 Thinking (80.2). LiveCodeBench at 91.6 actually beats all closed-source peers in the table, including Gemini-3.1-Pro High (91.7 — virtually tied). The 1M-token context with hybrid CSA+HCA attention keeps long-context inference cheap: 27% of single-token FLOPs and 10% of KV cache vs DeepSeek-V3.2. Practical caveat — full weights are ~284 GB on disk and the FP4-expert quantization means you cannot use stock vLLM yet; budget for the official `inference/` scripts and a multi-GPU host (8× H100 80GB minimum for comfortable inference, 4× H100 only at low concurrency).

## See also

- [[welcome]]
- Sibling: [[deepseek-ai--DeepSeek-V4-Pro]]
- Source: https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash
