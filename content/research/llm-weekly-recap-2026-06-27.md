---
title: "Open-weight LLM Weekly Recap — week of 2026-06-22–2026-06-28"
date: 2026-06-27
week_start: 2026-06-22
week_end: 2026-06-28
release_count: 1
tracker_total: 1
tags: [research, llm, open-weight, weekly-recap]
source: /home/pi/projects/llm-tracker/releases.md
---

# Open-weight LLM Weekly Recap — week of 2026-06-22–2026-06-28

🗓 **Open-weight LLM week of 2026-06-22–2026-06-28** (1 release)

**🏆 Headline:** Alibaba's Qwen team shipped **Qwen-AgentWorld-35B-A3B** — a 35B-parameter (3B active) MoE that is being framed as the first "language world model" unifying seven agent domains (MCP, Search, Terminal, SWE, Android, Web, OS) in a single training stack (CPT→SFT→RL, 262K ctx). On the **AgentWorldBench Overall** it posts **56.39**, beating Qwen3.5-35B-A3B base (47.73), DeepSeek-V4-Pro (52.97), Kimi K2.6 (53.42), and GLM-5.1 (51.31). The bigger **397B-A17B** sister variant climbs to **58.71** — the first open-weight model I've seen cleanly clear GPT-5.4 (58.25) and Claude Opus 4.8 (56.59) on an agentic benchmark.

## 📊 Releases (ranked by impact)

───────────────
**Alibaba Qwen-AgentWorld-35B-A3B** (35B params, 3B active MoE, Apache 2.0, 2026-06-23)
- Key: AgentWorldBench Overall **56.39** · AgentWorldBench@397B-A17B **58.71** · 262K ctx
- Beats: Qwen3.5-35B-A3B base (47.73), DeepSeek-V4-Pro (52.97), Kimi K2.6 (53.42), GLM-5.1 (51.31) on AgentWorldBench Overall; the 397B sister variant beats GPT-5.4 (58.25) and Claude Opus 4.8 (56.59)
- Loses to: n/a within the open-weight cohort — leads the field
- Why it matters: First open-weight release to frame "language world model" as a unifying pretraining objective across 7 agent domains, with the larger variant becoming the first open-weight model to top GPT-5.4 and Claude Opus 4.8 on a published agentic benchmark
- 🔗 [HF: Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B) · [Blog](https://qwen.ai/blog?id=qwen-agentworld) · [arXiv 2606.24597](https://arxiv.org/abs/2606.24597)

## 📈 Trends this week

- **MoE continues to dominate the open-weight frontier:** the week's only release is a 3B-active MoE, and the leaderboard slots it touches (Qwen3.5-35B-A3B, DeepSeek-V4-Pro, Kimi K2.6, GLM-5.1) are all MoE — five-for-five on the top of AgentWorldBench.
- **Apache 2.0 wins again:** Qwen's choice keeps the Qwen family at the most permissive end of the open-weight spectrum, ahead of Llama Community-style restrictions.
- **Chinese labs collectively own the agentic-benchmark leaderboard:** Qwen (35B + 397B), DeepSeek-V4-Pro, Kimi K2.6, GLM-5.1 — all from PRC orgs, all beating Western closed-API comparators on at least one agentic axis.

## 🔭 Looking ahead

The 397B-A17B sister variant is the one to watch — if Alibaba releases it under Apache 2.0 on the same schedule, this becomes the first genuinely open-weight model that beats GPT-5.4 and Claude Opus 4.8 on a public agentic benchmark. Worth re-checking the Qwen HF org next week for a separate model card and a v2 AgentWorldBench leaderboard.

**Tracker:** 1 total cumulative release in file · file at /home/pi/projects/llm-tracker/releases.md

## See also

- [[welcome|Welcome to the Vault]]
- [[index|Research Vault home]]
- Tracker: `/home/pi/projects/llm-tracker/releases.md`
