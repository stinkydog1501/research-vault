---
title: "Open-weight LLM Weekly Recap — week of 2026-06-22–2026-06-28 (DRY-RUN)"
date: 2026-06-27
week_start: 2026-06-22
week_end: 2026-06-28
release_count: 1
tracker_total: 1
tags: [research, llm, open-weight, weekly-recap, DRY-RUN]
source: /home/pi/projects/llm-tracker/releases.md
---

# Open-weight LLM Weekly Recap — week of 2026-06-22–2026-06-28 (DRY-RUN TEST NOTE — will be deleted)

🗓 **Open-weight LLM week of 2026-06-22–2026-06-28** (1 release)

**🏆 Headline:** Alibaba's Qwen-AgentWorld family debuted this week — the first open-weight "language world model" unifying 7 agent domains in a single model, with both a 35B-A3B and a 397B-A17B variant. The flagship sister variant edged past GPT-5.4 and Claude Opus 4.8 on AgentWorldBench Overall.

**📊 Releases (ranked by impact):**

───────────────────
**Alibaba Qwen-AgentWorld-35B-A3B** (35B / 3B active MoE, Apache 2.0, 2026-06-23)
• Key: AgentWorldBench Overall 56.39 · 397B sister variant hits 58.71
• Beats: Qwen3.5-35B-A3B base (47.73), DeepSeek-V4-Pro (52.97), Kimi K2.6 (53.42), GLM-5.1 (51.31)
• Loses to: GPT-5.4 (58.25) and Claude Opus 4.8 (56.59) on the flagship 397B-A17B variant, but only by 0.46 and 2.12 points respectively
• Why it matters: First model to unify 7 agent domains (MCP/Search/Terminal/SWE/Android/Web/OS) with native CPT→SFT→RL training; 262K context window
🔗 [HF](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B) · [Blog](https://qwen.ai/blog?id=qwen-agentworld) · [arXiv 2606.24597](https://arxiv.org/abs/2606.24597)

**📈 Trends this week:**
• Chinese labs dominated the only major release of the week — Alibaba's Qwen team continues to ship faster than Western counterparts on agent-capable open-weight models
• MoE architectures: the 35B variant runs at 3B active, keeping inference cost manageable despite the 35B total footprint

**🔭 Looking ahead:** Rumors of an InternVL3 follow-up from OpenGVLab by month-end; Meta's Llama-4 successor still no public timeline despite hints from the FAIR team in May.

**Tracker:** 1 total · file at /home/pi/projects/llm-tracker/releases.md

## See also

- [[welcome]]
- Source tracker: `/home/pi/projects/llm-tracker/releases.md`
