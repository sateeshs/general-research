# Research Limitations and Unknowns

## Known Unknowns

### OpenAI Architecture Details
OpenAI has not disclosed the architecture, parameter counts, or training data for the o-series models. All claims about o1/o3/o4-mini internals are inferred from published papers, API behavior, and vendor blog posts. The actual RL algorithm, reward model design, and training infrastructure remain proprietary.

### Training Cost Comparisons
DeepSeek's $5.58M training cost is well-documented, but OpenAI's estimated "$6B+" is speculative industry analysis. The comparison is illustrative but not precisely apples-to-apples (different architectures, different capability profiles, different infrastructure).

### Benchmark Gaming
It is unclear to what extent frontier models have been specifically optimized for popular benchmarks. Data contamination (training on benchmark problems) remains a concern, especially for older benchmarks like MMLU and GSM8K. FrontierMath was designed to resist this but is still relatively new.

### Meta's Reasoning Strategy
Meta has not released a dedicated "reasoning model" comparable to o1 or R1. It is unclear whether this reflects a strategic choice (reasoning via multimodal MoE instead) or a gap that will be addressed in future Llama releases.

### Long-Term Scaling Trajectories
Whether test-time compute scaling will continue to yield improvements or plateau is unknown. Current evidence is mixed, and the overthinking/inverse scaling findings are relatively recent (2025-2026).

## Gaps in This Report

1. **Proprietary model internals**: Cannot verify OpenAI's or Google's exact training methodologies
2. **Cost-performance frontiers**: Lack of standardized cost-per-benchmark-point comparisons across all models
3. **Real-world deployment data**: Limited information on how LRMs perform in production (vs benchmark) settings
4. **Safety and alignment**: This report focuses on capabilities; safety implications of reasoning models (e.g., deceptive alignment via extended thinking) are not deeply covered
5. **Emerging models**: New reasoning models are released frequently; this report reflects a July 2026 snapshot
6. **Formal verification integration**: Partially addressed via Agent 3's neuro-symbolic research, but production deployment details remain limited
7. **Hardware-specific optimizations**: How different hardware (GPU, TPU, custom silicon) affects test-time compute efficiency is not addressed
8. **Agent 4 rate-limited**: Reasoning trace faithfulness research was incomplete due to API rate limiting. Findings were supplemented from other agents and training knowledge.
9. **Kambhampati's latest work**: Agent 1 relied on training data (through May 2025) rather than live web access. Post-May 2025 publications from Kambhampati's group are not covered.
10. **Plnner accuracy estimates**: The 95-99% extraction accuracy claims for the recommended architecture are projections based on comparable systems, not benchmarked on Plnner-specific data.
