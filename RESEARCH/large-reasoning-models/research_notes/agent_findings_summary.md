# Agent Findings Summary

## Agent 1: Kambhampati's LLM Reasoning Critique

**Focus:** Subbarao Kambhampati's (ASU, former AAAI president) published critique of LLM reasoning capabilities.

**Key Findings:**
- Identified 6 primary papers and the AAAI 2024 Presidential Address
- Documented all 4 failures: no hard guarantees, fake reasoning traces, distribution vs complexity confusion, jagged intelligence
- PlanBench results: GPT-4 achieves 3-5% on Blocksworld vs 100% for classical planners
- Mystery Blocksworld (renamed objects) drops to 0% -- strongest evidence for retrieval vs reasoning
- LLM-Modulo framework proposed as solution: LLM generates, formal verifier checks
- AlphaProof validates this architecture (LLM + Lean verification)
- 12 Quality B sources (peer-reviewed conference papers and position papers)

**Limitation:** WebFetch and Bash denied; findings drawn from training data knowledge (through May 2025)

---

## Agent 2: LRM Architectures, Training, and Benchmarks

**Focus:** LRM definition, key players, training methods, test-time compute scaling, benchmarks, RLHF gap.

**Key Findings:**
- LRMs differ from LLMs in training signal (reasoning correctness via RL), inference (variable test-time compute), and self-correction
- DeepSeek-R1 paradigm shift: competitive reasoning from pure RL (GRPO) at ~1/1000th OpenAI's cost
- GRPO algorithm: group relative policy optimization without critic model, 4-stage training pipeline
- Test-time compute scaling helps math/coding but hurts knowledge-intensive tasks (overthinking problem)
- RLHF fundamentally limited for reasoning: human evaluators can't verify complex proofs, reward hacking produces correct-sounding but logically unsound reasoning
- RLVR (Reinforcement Learning with Verifiable Rewards) is the practical alternative
- PRMs outperform ORMs on simple tasks but can hurt on complex ones
- Benchmarks saturating: FrontierMath from <2% to 52.4% in under two years
- 45 sources found, 23 rated A, 12 rated B

**Output Files:** Wrote full report structure to RESEARCH/large-reasoning-models/

---

## Agent 3: Neuro-Symbolic Approaches & Formal Verification

**Focus:** Neuro-symbolic AI, AlphaProof/AlphaGeometry, theorem provers, LLM-Modulo, System 2 hypothesis, metacognition.

**Key Findings:**
- Survey of 178 papers (2020-2025) established first comprehensive taxonomy of neuro-symbolic agent architectures
- AlphaProof: 4/6 IMO problems, 28/42 points (silver medal), Nature publication Nov 2025, Nexus solved 9 Erdős problems
- HERALD: 96.7% autoformalization accuracy on miniF2F-test
- LLM + SMT integration maturing: VeriCoT, VERGE, LLM Meets BMC (ASE 2024)
- PAL (Program-Aided Language Models): code-as-reasoning eliminates arithmetic errors but can't handle declarative reasoning
- System 2 approaches: System-1.x, DynamicMind, Latent CoT
- Metacognition: "knowing-doing gap" -- models know when they don't know but don't act on it
- Generator + verifier pattern dominates across ALL domains (math, planning, code, verification)
- 40+ sources, including 5 rated A (IJCAI 2025, PAL ICML 2023, ASE 2024, Nature, DeepMind)

---

## Agent 4: Reasoning Trace Faithfulness

**Focus:** Faithful CoT, jagged intelligence, pattern matching debate.

**Status:** Hit rate limit during research. Minimal output.

**Findings incorporated from other agents and training knowledge:**
- Turpin et al. (2023): CoT explanations unfaithful to actual reasoning
- Lanham et al. (2023): Early answering shows models know answers before completing CoT
- GSM-Symbolic (Apple, 2024): Trivial modifications break math reasoning
- Overthinking problem documented (arXiv:2604.10739, arXiv:2507.14417)

---

## Agent 5: Practical Implications for Edge AI (Plnner)

**Focus:** Small model reasoning, distillation, structured extraction, Plnner-specific architecture.

**Key Findings:**
- Reasoning is distillable: 32B distilled model beats o1-mini (72.6% vs 63.6% on AIME 2024)
- Phi-4-reasoning at 14B beats the 70B distilled model
- Reminder extraction is NOT a hard reasoning problem -- intent classification + entity extraction + temporal parsing
- Bonsai 27B dramatically exceeds Plnner's reasoning requirements
- Production pattern: LLM + deterministic verifier (used by Cursor, Claude Code, Guardrails, Instructor, Outlines)
- GBNF grammars in llama.cpp eliminate parsing failures via constrained decoding
- Recommended 3-tier pipeline: GBNF-constrained generation → Rust validator → confidence gating
- Regex fast-path for simple, unambiguous inputs
- Temperature: 0.1 for extraction, 0.6 minimum for Qwen3 thinking mode
- Expected accuracy: 95-99% with full pipeline
- 20+ sources

**Output Files:** Wrote to RESEARCH/llm-reasoning-limitations/
