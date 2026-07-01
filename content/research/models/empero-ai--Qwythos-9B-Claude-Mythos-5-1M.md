---
title: "Empero/Qwythos-9B-Claude-Mythos-5-1M"
org: empero-ai
model_id: empero-ai/Qwythos-9B-Claude-Mythos-5-1M
date: 2026-06-19
tags:
  - huggingface
  - text-generation
  - coding
  - agentic
  - tool-use
  - function-calling
  - reasoning
  - long-context
  - 1m-context
  - full-fine-tune
  - uncensored
  - qwen3.5
  - dense
downloads: 52492
likes: 521
license: apache-2.0
pipeline: text-generation
source: https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M
params: 9B (dense, hybrid Gated-DeltaNet + Gated full attention, 3:1 ratio)
context: 1048576
architecture: dense
---

# Empero/Qwythos-9B-Claude-Mythos-5-1M

**One-line:** Full-parameter community post-training of Qwen3.5-9B on 500M+ tokens of Claude Mythos / Fable reasoning traces, with YaRN-baked 1M-token context and verified native tool-use.

> ⚠ No published SWE-bench / Aider / BFCL numbers — agent-loop suitability inferred from the lab's own 7/7 tool-use harness (Python + web_search). Treat coding/agentic claims as **lab-reported, single-trainer verified** until independent eval lands.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | not published |
| HumanEval+ | — | not published |
| MBPP | — | not published |
| LiveCodeBench | — | not published |
| Aider polyglot | — | not published |
| SWE-bench Verified | — | not published |
| SWE-bench Multilingual | — | not published |

## Agentic / tool-use benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| BFCL | — | not published |
| τ-Bench | — | not published |
| ToolACE | — | not published |
| GAIA | — | not published |
| Tool-use harness (7 prompts, math + facts) | **7/7** | *lab-reported* — Python executor + DuckDuckGo web_search, lm-eval-harness |

The lab's tool-use harness mixes a Python executor with a web search tool and runs 7 prompts spanning math (sin(π/7)×cos(π/11), primes below 100k), latest-version lookup (CPython 3.14.6), and 4 deliberately hard factual-recall prompts (Kerberos TGS-REP hashcat mode, CVE-2021-34527, physostigmine pharmacology, semaglutide cleavage site). All 7 succeeded with sensible tool selection. Transcripts are in `evals/tool_test_outputs.md` per the card.

## Reasoning (context only)

| Benchmark | Score | Source |
|:---|---:|:---|
| MMLU (mean, 57 subjects) | **0.575** (+0.343 vs base) | *lab-reported* — lm-eval-harness, Qwen3.5 sampling, `--limit 100` |
| gsm8k (flexible) | **0.860** (+0.190) | *lab-reported* |
| gsm8k (strict) | **0.810** (+0.300) | *lab-reported* |
| ARC-Challenge | 0.490 (+0.020) | *lab-reported* |
| GPQA Diamond (CoT, 0-shot) | 0.580 (−0.050 vs base) | *lab-reported* |

**Read the deltas, not the absolutes.** Qwen3.5-9B's headline MMLU of 0.232 here is unusually low vs other 9B numbers reported elsewhere — that's a harness/template artifact, not a real capability ceiling. The +34 pp lift is the honest signal under matched conditions.

## Efficiency

- **Active params:** ~9.4B (total 9.4B — dense, not MoE; safetensors total 9,409,813,744 bytes of FP16 weights ≈ 9.41B params)
- **Architecture:** Qwen3.5-9B base — hybrid Gated-DeltaNet (linear attention) + Gated full attention at 3:1 ratio. Dense, no MoE.
- **Context length:** **1,048,576 tokens (≈1M)**, YaRN rope-scaling baked into `config.json` (factor 4.0 from native 262k). vLLM / SGLang recipes provided.
- **VRAM (fp16 rough):** ~19 GB at native context; KV-cache grows fast at 1M — single H100/H200 comfortable at 256k–512k, full 1M needs TP + offload.
- **Multimodal:** Inherited from Qwen3.5 base (vision tower frozen during post-training — vision behavior untuned per the card).

## What makes it notable

**The 1M-context + native tool-use combination is the actual pitch.** Most 9B-class open-weight models either give you long context *or* clean function-calling, rarely both. Qwythos ships YaRN-baked 1M in `config.json` (no runtime flag needed), and the card claims — with reproducible transcripts — that the model picks the right tool (Python for math, search for facts) and integrates results. If the lab's tool-use numbers hold up under independent re-eval (Aider polyglot, BFCL, τ-Bench would be the right benchmarks), this is a meaningful step up over the base Qwen3.5-9B for whole-codebase reasoning agents.

**The "uncensored" framing is a positioning choice, not a capability claim.** The card is explicit about engaging seriously with cybersecurity red-team methodology and clinical pharmacology rather than refusing. That's an open-weight design preference, not a benchmark edge — but it does mean the model is less likely to bail out of multi-step tool trajectories with a safety disclaimer mid-task.

**Caveats to weigh:**
- All numeric benchmarks are lab-reported on a `--limit 100` lm-eval-harness subset. Independent eval needed.
- No SWE-bench, no Aider polyglot, no BFCL — the agent-loop scorecard is empty.
- Base model is Qwen3.5-9B (not Qwen3-Coder), so pure code-completion strength is unproven.
- High like-count (521) and downloads (52k in ~10 days) are a real signal of community traction but don't substitute for benchmark coverage.

**Bottom line:** If you're already running Qwen3.5-9B locally and want a fine-tune that pushes the long-context envelope and adds verifiable tool-use, this is worth a side-by-side. Don't replace Qwen3-Coder-Next or GLM-4.7-Flash on the strength of these numbers alone.

## See also

- [[welcome]]
- Base: [Qwen/Qwen3.5-9B](https://huggingface.co/Qwen/Qwen3.5-9B)
- Eval harness recipe: `evals/lm_eval_results.md`, `evals/tool_test_outputs.md` in the repo
- Source: https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M
