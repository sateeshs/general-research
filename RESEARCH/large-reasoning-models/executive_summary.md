# Executive Summary: Large Reasoning Models (LRMs)

## What Are LRMs?

Large Reasoning Models (LRMs) are a distinct class of AI systems that extend conventional LLMs with explicit multi-step deliberation, chain-of-thought reasoning, and reinforcement-learning-driven problem solving. Unlike standard LLMs that predict the next token in a single forward pass, LRMs generate, revise, and select reasoning chains before answering -- they "think in public" before responding.

The defining innovations are: (1) reinforcement learning on reasoning quality rather than just human preference, (2) test-time compute scaling where models can spend variable compute during inference, and (3) process-level supervision that rewards correct reasoning steps, not just correct final answers.

## Key Players and Approaches

- **OpenAI o-series (o1, o3, o4-mini)**: Pioneered the category in September 2024. Uses RL to train internal chain-of-thought reasoning. Performance improves with both train-time and test-time compute. Architecture details remain proprietary.
- **DeepSeek-R1**: Open-source 671B MoE model (37B active). Demonstrated that reasoning emerges from pure RL (GRPO algorithm) without human-annotated reasoning data. Built for $5.58M vs OpenAI's estimated $6B+. Four-stage training pipeline.
- **Qwen QwQ-32B / Qwen3**: 32.5B parameter model using multi-stage RL on Qwen2.5 architecture. Supports both "thinking" and "non-thinking" modes.
- **Claude (Anthropic)**: Extended/adaptive thinking approach. Serial test-time compute with interleaved thinking for agentic workflows. Accuracy improves logarithmically with thinking tokens.
- **Gemini 2.5 Pro (Deep Think)**: Sparse MoE transformer with parallel chain-of-thought exploration. Generates multiple solution paths simultaneously before converging.
- **Meta Llama 4**: MoE architecture (17B active, up to 128 experts). Focuses on multimodal reasoning rather than a dedicated "reasoning mode."

## Critical Findings

1. **Test-time compute scaling is not universally beneficial.** While longer reasoning improves math/coding tasks, it can hurt knowledge-intensive tasks and cause "overthinking" where models second-guess correct initial intuitions.

2. **RLHF is fundamentally limited for reasoning.** Human evaluators cannot verify complex mathematical proofs. Reward hacking produces correct-sounding but logically unsound reasoning. RLVR (Reinforcement Learning with Verifiable Rewards) addresses this by using rule-based verification.

3. **Process Reward Models (PRMs) outperform Outcome Reward Models (ORMs)** on simpler tasks but can reduce performance on complex ones. The optimal approach depends on task difficulty.

4. **Benchmarks are rapidly saturating.** MMLU, GSM8K, and HumanEval no longer differentiate frontier models. FrontierMath went from <2% (Nov 2024) to 52.4% (Apr 2026) on Tier 1-3 problems. AIME 2025 sees scores above 95%.

5. **DeepSeek-R1's training efficiency** is a paradigm shift: achieving competitive reasoning at ~1/1000th the cost of OpenAI, with full transparency into methodology.

6. **Kambhampati's critique remains empirically grounded.** PlanBench shows near-zero LLM planning accuracy vs. 100% for classical planners. The "approximate retrieval engine" framing explains jagged intelligence, distribution sensitivity, and unfaithful traces in a unified framework. His LLM-Modulo architecture (LLM + external verifier) is validated by AlphaProof's IMO results.

7. **Neuro-symbolic integration is production-ready in key domains.** AlphaProof solved 4/6 IMO problems with Lean-verified proofs (Nature, Nov 2025). HERALD achieves 96.7% autoformalization accuracy. The generator + verifier pattern dominates across math, planning, code, and program verification.

8. **Reasoning traces can be unfaithful.** Replacing CoT with incorrect but syntactically correct steps yields comparable performance. Models sometimes "know" answers before completing the chain of thought. The overthinking problem shows more thinking can hurt on knowledge-intensive tasks.

9. **For Plnner specifically:** Reminder extraction is not a hard reasoning problem. Bonsai 27B dramatically exceeds requirements. The recommended architecture is GBNF-constrained generation + Rust rule validator + confidence gating, with a regex fast-path for simple inputs. Expected accuracy: 95-99%.
