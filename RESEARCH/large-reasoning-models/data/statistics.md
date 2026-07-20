# Data & Statistics: Large Reasoning Models

## LRM Model Comparison

| Model | Parameters | Active Params | Training Cost | Release |
|-------|-----------|--------------|---------------|---------|
| OpenAI o1 | Undisclosed | Undisclosed | Est. $6B+ | Sep 2024 |
| OpenAI o3 | Undisclosed | Undisclosed | Undisclosed | Jan 2025 |
| OpenAI o4-mini | Undisclosed | Undisclosed | Undisclosed | Apr 2025 |
| DeepSeek-R1 | 671B (MoE) | 37B | $5.58M | Jan 2025 |
| Qwen QwQ-32B | 32.5B | 32.5B | Undisclosed | 2025 |
| Claude (ext. thinking) | Undisclosed | Undisclosed | Undisclosed | 2025 |
| Gemini 2.5 Pro | Sparse MoE | Undisclosed | Undisclosed | 2025 |
| Meta Llama 4 | MoE (128 experts) | 17B | Undisclosed | 2025 |

## Benchmark Performance

### AIME 2025 (Math Reasoning)

| Model | Score | Notes |
|-------|-------|-------|
| o4-mini (high) | 95%+ | Top performer |
| o3 | 95%+ | Comparable to o4-mini |
| DeepSeek-R1 | ~80% | Open-source leader |
| Claude 3.5 Sonnet | ~50% | Non-reasoning model baseline |

### FrontierMath (Hard Math)

| Date | Best Score | Model |
|------|-----------|-------|
| Nov 2024 | <2% | All models |
| Apr 2026 | 52.4% (Tier 1-3) | Frontier reasoning models |

### PlanBench (Planning - Kambhampati)

| Test | GPT-4 | Optimal Planner |
|------|-------|-----------------|
| Blocksworld (standard) | 3-5% | 100% |
| Blocksworld (with hints) | ~30% | 100% |
| Logistics domain | ~0% | 100% |
| Mystery Blocksworld (renamed) | ~0% | 100% |

### AlphaProof (Formal Math)

| Metric | Value |
|--------|-------|
| IMO 2024 score | 28/42 (silver medal) |
| Problems solved | 4 of 6 |
| Erdős open problems solved (Nexus) | 9 in single run |
| Verification method | Lean kernel (100% formal) |

### Reasoning Distillation

| Model | Size | AIME 2024 | Method |
|-------|------|-----------|--------|
| DeepSeek-R1-Distill-Qwen-32B | 32B | 72.6% | SFT distillation |
| OpenAI o1-mini | ~100B? | 63.6% | RL training |
| Phi-4-reasoning | 14B | Beats 70B distill | SFT + RL |

## Training Method Comparison

| Method | Signal Source | Scalability | Correctness Guarantee | Used By |
|--------|-------------|-------------|----------------------|---------|
| RLHF | Human preference | Poor (costly) | None | GPT-4, Claude |
| RLVR | Rule-based verification | Excellent | For verifiable tasks | o1/o3, R1 |
| GRPO | Group relative ranking | Excellent | None directly | DeepSeek-R1 |
| PRM supervision | Step-level human/model labels | Medium | Learned approximation | Various |
| Formal verification | Theorem provers | Domain-limited | Mathematical certainty | AlphaProof |

## Test-Time Compute Scaling

| Task Type | Effect of More Thinking | Evidence |
|-----------|------------------------|----------|
| Math/competition problems | Strong positive | o1/o3 benchmarks |
| Code generation | Moderate positive | HumanEval scaling |
| Knowledge-intensive tasks | Neutral to negative | arXiv:2509.06861 |
| Simple factual questions | Negative (overthinking) | arXiv:2604.10739 |

## Neuro-Symbolic Maturity Assessment

| Area | Maturity | Production-Ready? |
|------|----------|-------------------|
| LLM + theorem provers (Lean) | High | Yes, for math research |
| LLM + classical planners (PDDL) | Medium | Yes, with oversight |
| Process Reward Models | Medium-High | Yes, in o1/o3/R1 |
| LLM + SMT solvers | Medium | Emerging |
| Metacognitive monitoring | Low | No |
| System 2 thinking | Medium | Partially (CoT/TTC) |

## Plnner Expected Performance

| Task | Expected Accuracy |
|------|-------------------|
| Explicit date extraction | 95-98% |
| Relative date parsing | 88-94% |
| Intent detection | 97-99% |
| Overall with GBNF + validator | >95% |
