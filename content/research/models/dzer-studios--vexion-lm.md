---
title: "DZER-Studios/Vexion-LM"
org: DZER-Studios
model_id: DZER-Studios/Vexion-LM
date: 2026-07-10
tags:
  - huggingface
  - text-generation
  - coding
  - agentic
  - custom-architecture
  - moe
  - apache-2.0
downloads: 2502
likes: 0
license: apache-2.0
pipeline: text-generation
source: https://huggingface.co/DZER-Studios/Vexion-LM
params: ~850M (V2)
context: 1024
architecture: moe
---

# DZER-Studios/Vexion-LM

**One-line:** Custom-architecture MoE (4 experts) built from scratch in PyTorch — no HF Transformers support; agent-loop suitability unknown.

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

- **Active params:** ~850M (V2, 4 experts with routing)
- **Context length:** 1,024 tokens (sliding window 512)
- **VRAM (fp16 rough):** ~2 GB
- **Note:** Custom PyTorch architecture — requires repo's `generate.py`, not compatible with `AutoModelForCausalLM`, vLLM, Ollama, llama.cpp, etc.

## What makes it notable

Vexion-LM is a from-scratch research project: custom transformer with MoE (4 experts), GQA, SwiGLU, RMSNorm, FlashAttention-2, hand-written RoPE, 40K-token BPE vocab (multiple of 64 for tensor-core efficiency), trained on 1×RTX 3060 Ti (8GB) with 8-bit AdamW. **Critical limitation:** it does NOT work with Hugging Face Transformers, vLLM, Ollama, llama.cpp, or any standard inference stack — you must use the repo's `model.py` / `generate.py` directly. No coding/agentic benchmarks published. For an agent-loop practitioner, this is a research curiosity, not a drop-in model. The LoRA-adapted conversational versions exist but share the same inference constraint.

## See also

- [[welcome]]
- Source: https://huggingface.co/DZER-Studios/Vexion-LM