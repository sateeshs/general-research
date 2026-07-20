# Large Reasoning Models (LRMs) — Deep Research

**Research Date:** July 19-20, 2026  
**Purpose:** Understanding what LLMs and RLHF miss in reasoning, based on Kambhampati's 4 identified failures  
**Scope:** LRM architectures, training methods, reasoning limitations, neuro-symbolic solutions, practical implications

## Research Question

What are Large Reasoning Models (LRMs), how do they differ from standard LLMs, and what fundamental reasoning gaps remain? Specifically: what does RLHF miss, why do reasoning traces sometimes fail, and what does this mean for edge AI systems like Plnner?

## Documents

| Document | Description |
|----------|-------------|
| [Executive Summary](executive_summary.md) | 2-page key findings and recommendations |
| [Full Report](full_report.md) | Complete 9-section analysis |
| [Data & Statistics](data/statistics.md) | Benchmarks, performance numbers, comparisons |
| [Source Quality Table](sources/source_quality_table.md) | A-E rated source inventory |
| [Bibliography](sources/bibliography.md) | Complete source list with URLs |
| [Agent Findings Summary](research_notes/agent_findings_summary.md) | Raw outputs from 5 research agents |
| [Methodology](appendices/methodology.md) | Research methods and agent deployment |
| [Limitations](appendices/limitations.md) | Known gaps and caveats |

## Report Sections

1. **What Are LRMs?** — Definition, key players (o1/o3, DeepSeek-R1, QwQ, Claude, Gemini, Llama 4)
2. **Training Methods** — GRPO, RLVR, Process Reward Models, self-play
3. **Test-Time Compute Scaling** — When more thinking helps (and hurts)
4. **Benchmarks** — AIME, FrontierMath, ARC-AGI, PlanBench saturation
5. **The RLHF Gap** — Why human feedback fails for reasoning; alternatives
6. **Kambhampati's Critique** — Four failures: no guarantees, fake traces, distribution vs complexity, jagged intelligence
7. **Neuro-Symbolic Approaches** — AlphaProof, theorem provers, SMT integration, PRMs, System 2
8. **Reasoning Trace Faithfulness** — Evidence for and against genuine computation; overthinking
9. **Practical Implications for Plnner** — Distillation, GBNF constraints, recommended architecture

## Research Agents Deployed

| Agent | Focus | Sources Found |
|-------|-------|---------------|
| Agent 1 | Kambhampati's critique, LLM-Modulo, PlanBench | 12+ sources |
| Agent 2 | LRM architectures, training methods, benchmarks, RLHF gap | 45+ sources |
| Agent 3 | Neuro-symbolic approaches, formal verification, System 2 | 40+ sources |
| Agent 4 | Reasoning trace faithfulness, jagged intelligence | Rate-limited |
| Agent 5 | Practical implications, distillation, Plnner architecture | 20+ sources |
