---
title: "DeepSeek-V4-Pro"
org: deepseek-ai
model_id: deepseek-ai/DeepSeek-V4-Pro
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
downloads: 1878217
likes: 5061
license: mit
pipeline: text-generation
source: https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro
params: "49B active / 1.6T total (MoE, top-6 of 256 routed + 1 shared)"
context: "1M tokens"
architecture: moe
---

# DeepSeek-V4-Pro

**One-line:** Flagship 49B-active MoE from DeepSeek's V4 line — Pro-Max hits 80.6 SWE-bench Verified and 93.5 LiveCodeBench (both at-or-above Opus-4.6 Max) while still shipping under MIT; 1.6T total params make this a server-class release only.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | not published for this variant |
| HumanEval+ | — | not published |
| MBPP | — | not published for this variant |
| LiveCodeBench | 93.5 | lab (V4-Pro Max mode) |
| Aider polyglot | — | not published |
| SWE-bench Verified | 80.6 | lab (V4-Pro Max mode) |
| SWE-bench Multilingual | 76.2 | lab (V4-Pro Max mode) |
| Codeforces (rating) | 3206 | lab (V4-Pro Max mode) |

*In the frontier comparison table the lab positions V4-Pro-Max as the best open-source model on LiveCodeBench (93.5 vs Gemini-3.1-Pro High 91.7, Opus-4.6 Max 88.8) and Codeforces (3206 vs GPT-5.4 xHigh 3168). SWE-bench Verified 80.6 ties Gemini-3.1-Pro High (80.6) and is within 0.2 of Opus-4.6 Max (80.8).*

## Agentic / tool-use benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| BFCL | — | not published for this variant |
| τ-Bench | — | not published |
| ToolACE | — | not published |
| GAIA | — | not published |
| Terminal Bench 2.0 | 67.9 | lab (V4-Pro Max mode) |
| SWE Pro | 55.4 | lab (V4-Pro Max mode) |
| BrowseComp | 83.4 | lab (V4-Pro Max mode) |
| HLE w/ tools | 48.2 | lab (V4-Pro Max mode) |
| MCPAtlas (Public) | 74.2 | lab (V4-Pro High mode) |
| Toolathlon | 51.8 | lab (V4-Pro Max mode) |
| GDPval-AA (Elo) | 1554 | lab (V4-Pro Max mode) |

*MCPAtlas (74.2 in Pro High) is the best non-Opus tool-use number in the table; Toolathlon 51.8 is competitive with Gemini-3.1-Pro High (48.8) and approaches Opus-4.6 Max (47.2) and Toolathlon-leader GPT-5.4 (54.6). BFCL is conspicuously absent — verify function-calling reliability on your own schemas before deploying in agent loops.*

## Reasoning (context only)

| Benchmark | Score | Source |
|:---|---:|:---|
| MMLU-Pro | 87.5 | lab (V4-Pro Max mode) |
| GPQA Diamond | 90.1 | lab (V4-Pro Max mode) |
| MATH | — | not published for this variant |
| AIME 2025 | — | not published; HMMT 2026 Feb = 95.2 |
| HLE | 37.7 | lab (V4-Pro Max mode) |

## Efficiency

- **Active params:** 49B (per token — top-6 of 256 routed + 1 shared)
- **Total params:** 1.6T (full disk-resident weight footprint)
- **Context length:** 1,048,576 tokens (1M) via YaRN rope scaling; recommend ≥384K context for Think Max mode
- **VRAM (fp16 rough):** ~98 GB active-params equivalent at runtime; full weights ~1.6 TB on disk (FP4 experts + FP8 other)
- **Precision:** MoE expert weights are FP4, most other parameters are FP8 — requires DeepSeek's custom `encoding` + `inference` scripts
- **Architecture:** Hybrid attention — Compressed Sparse Attention (CSA) + Heavily Compressed Attention (HCA); Manifold-Constrained Hyper-Connections (mHC); Muon optimizer in pretraining

## What makes it notable

DeepSeek-V4-Pro is the open-weight flagship of this release and currently sets the high-water mark for open-source coding/agentic performance on the lab's own benchmarks: SWE-bench Verified 80.6, LiveCodeBench 93.5, BrowseComp 83.4, and Codeforces rating 3206 — the lab's own table positions Pro-Max ahead of Opus-4.6 Max on LiveCodeBench, tied on SWE-bench Verified, and within striking distance on MMLU-Pro (87.5 vs 89.1) and GPQA Diamond (90.1 vs 91.3). Like its Flash sibling it ships under MIT and uses hybrid CSA+HCA attention to keep long-context compute bounded (27% of V3.2 single-token FLOPs at 1M context). The cost is brutal — **1.6 TB of weights on disk, ~98 GB active VRAM at runtime** — this is a multi-node release, not something you run on a workstation. Tool-use benchmark coverage is unusually deep (Terminal Bench, MCPAtlas, BrowseComp, Toolathlon, HLE w/ tools, GDPval-AA) but BFCL is missing, so for production agent loops benchmark your own tool-calling accuracy before trusting it.

## See also

- [[welcome]]
- Sibling: [[deepseek-ai--DeepSeek-V4-Flash]]
- Source: https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro
