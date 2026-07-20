# Research Methodology

## Research Approach

This report was compiled through systematic web research conducted in July 2026, covering sources from 2023 through mid-2026.

## Multi-Agent Research Strategy

Five parallel research agents were deployed, each with a distinct focus area:

| Agent | Focus | Searches | Duration |
|-------|-------|----------|----------|
| Agent 1 | Kambhampati's critique, LLM-Modulo, PlanBench | Training data knowledge | ~3 min |
| Agent 2 | LRM architectures, training, benchmarks, RLHF gap | 19 web searches | ~8 min |
| Agent 3 | Neuro-symbolic approaches, formal verification, System 2 | 18 web searches | ~5 min |
| Agent 4 | Reasoning trace faithfulness, jagged intelligence | 22 web searches | Rate-limited |
| Agent 5 | Practical implications, distillation, Plnner architecture | 44 web searches | ~7 min |

## Search Strategy

1. **Definitional queries**: Established what LRMs are and how they differ from LLMs using industry glossaries, vendor documentation, and survey papers
2. **Model-specific queries**: Targeted searches for each major model (o1/o3/o4-mini, DeepSeek-R1, Qwen QwQ, Claude, Gemini 2.5 Pro, Meta Llama 4) focusing on architecture, training methodology, and published technical details
3. **Training methodology queries**: Searched for RLHF vs RLVR, process vs outcome reward models, GRPO, MCTS integration, and self-play approaches
4. **Test-time compute queries**: Searched for evidence both supporting and contradicting the "thinking longer = better" hypothesis, including inverse scaling and overthinking research
5. **Benchmark queries**: Targeted AIME, MATH-500, ARC-AGI, SWE-Bench, PlanBench, and FrontierMath for latest performance data and saturation analysis
6. **RLHF limitations queries**: Searched for reward hacking, alternatives (Constitutional AI, debate, amplification, RLVR), and scalable oversight
7. **Kambhampati critique queries**: Papers, AAAI Presidential Address, the 4 failures, LLM-Modulo framework, counterarguments
8. **Neuro-symbolic queries**: AlphaProof, theorem provers (Lean, Coq, Isabelle), SMT solver integration, PRMs, System 2 hypothesis, metacognition
9. **Reasoning trace queries**: CoT faithfulness, GSM-Symbolic, overthinking, unfaithful traces
10. **Practical implication queries**: Distillation, constrained decoding, GBNF grammars, edge AI deployment

## Source Prioritization

1. Peer-reviewed papers and technical reports (arXiv with venue acceptance preferred)
2. Official vendor documentation and announcements
3. Well-regarded ML researcher blogs (e.g., Philipp Schmid, Cameron Wolfe)
4. Industry analysis platforms (Artificial Analysis, IntuitionLabs)
5. General tech journalism and blog posts (used sparingly, cross-referenced)

## Quality Assurance

- Cross-referenced claims across multiple independent sources
- Prioritized primary sources (original papers) over secondary summaries
- Noted when information was from a single source or vendor-only
- Included both supporting and contradicting evidence for key claims (especially test-time compute scaling)
- Applied A-E quality ratings to all citations

## Limitations of Methodology

- Web search may miss paywalled academic publications
- Some vendor claims (especially OpenAI) cannot be independently verified due to proprietary architectures
- Benchmark leaderboards change frequently; numbers reflect July 2026 snapshot
- Medium and blog posts were used when primary sources were unavailable but rated accordingly
