---
title: "Olmo-3-7B-Instruct"
org: allenai
model_id: allenai/Olmo-3-7B-Instruct
date: 2026-06-26
tags:
  - huggingface
  - text-generation
  - coding
  - agentic
  - dense
  - olmo3
  - instruct
  - 7b
  - chat-template
  - function-calling
downloads: 122429
likes: 134
license: apache-2.0
pipeline: text-generation
source: https://huggingface.co/allenai/Olmo-3-7B-Instruct
params: "7B (dense)"
context: "65,536 tokens (64k)"
architecture: dense
---

# Olmo-3-7B-Instruct

**One-line:** AllenAI's fully open (Apache-2.0) 7B instruction-tuned model — ships with an explicit function-calling chat template, BFCL 49.8 and HumanEvalPlus 77.2, runs in ~14 GB VRAM, and is the most locally-usable of the new Olmo-3 drop.

## Coding benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| HumanEval | — | not published; HumanEvalPlus = 77.2 |
| HumanEval+ | 77.2 | lab |
| MBPP | — | not published; MBPP+ = 60.2 |
| MBPP+ | 60.2 | lab |
| LiveCodeBench | 29.5 | lab (LiveCodeBench v3) |
| Aider polyglot | — | not published |
| SWE-bench Verified | — | not published |
| SWE-bench Multilingual | — | not published |

*Olmo-3-7B-Instruct does not run SWE-bench Verified in the lab's evaluation table — its LiveCodeBench v3 score (29.5) is below Qwen3-8B (53.2) and Qwen2.5-7B (34.5). Coding is reasonable for a 7B dense model but not where Olmo-3 shines.*

## Agentic / tool-use benchmarks

| Benchmark | Score | Source |
|:---|---:|:---|
| BFCL | 49.8 | lab |
| τ-Bench | — | not published |
| ToolACE | — | not published |
| GAIA | — | not published |
| MCPAtlas | — | not published |
| Toolathlon | — | not published |

*BFCL 49.8 is a clear signal that function calling is in scope; the default system prompt literally identifies the model as "a helpful function-calling AI assistant." This is one of the few open 7B models where the chat template is wired for `<functions></functions>` out of the box.*

## Reasoning (context only)

| Benchmark | Score | Source |
|:---|---:|:---|
| MMLU | 69.1 | lab |
| MMLU-Pro | — | not published |
| GPQA Diamond | — | not published; GPQA = 40.4 |
| MATH | 87.3 | lab (reasoning category: MATH) |
| AIME 2024 | 44.3 | lab |
| AIME 2025 | 32.5 | lab |
| IFEval | 85.6 | lab |

*Note: the lab's MATH entry (87.3) is unusually high for a 7B — likely a different MATH cut than the standard MATH-500. Reasoning is Olmo-3's strength (AIME 2024 = 44.3 puts it ahead of Qwen3-8B's 26.2 and Granite-3.3-8B's 7.3 in the same table).*

## Efficiency

- **Active params:** 7B (dense)
- **Total params:** 7B (dense)
- **Context length:** 65,536 tokens (64K)
- **VRAM (fp16 rough):** ~14 GB
- **Precision:** bfloat16 weights; safetensors
- **Architecture:** Standard dense transformer (Olmo3ForCausalLM); 32 layers, hidden_size 4096, 32 heads, RoPE (rope_theta 500000), grouped-query attention with sliding window

## What makes it notable

Olmo-3-7B-Instruct is the production-friendly face of AllenAI's full Olmo-3 drop (which dropped 2026-06-25 in a coordinated release of seven variants). The pitch is "fully open" — Apache-2.0 license, all training data public (`allenai/Dolci-Instruct-RL-7B`), and a chat template that **explicitly supports function-calling** via a `<functions></functions>` block in the system prompt (rare for 7B dense open-weight models). BFCL 49.8 puts it in the same neighborhood as Qwen2.5-7B (55.8) and below Qwen3-8B (60.2) on tool-use. Reasoning numbers (AIME 2024 = 44.3, MATH = 87.3) are surprisingly strong for the size class. The downside: SWE-bench Verified is not run, LiveCodeBench v3 at 29.5 is mediocre, and 64K context is shorter than Qwen3-8B's 128K. Practical verdict — solid local agent-loop backbone if you need a fully open (Apache-2.0, weights + data + code) 7B; reach for Qwen3-Coder or DeepSeek-Coder families for serious code generation.

## See also

- [[welcome]]
- Source: https://huggingface.co/allenai/Olmo-3-7B-Instruct
