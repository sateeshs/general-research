# Large Reasoning Models (LRMs): Architectures, Training, and the Reasoning Frontier

## Table of Contents

1. [What Are LRMs?](#1-what-are-lrms)
2. [Training Methods for Reasoning](#2-training-methods-for-reasoning)
3. [Test-Time Compute Scaling](#3-test-time-compute-scaling)
4. [Benchmarks and Evaluation](#4-benchmarks-and-evaluation)
5. [The RLHF Gap](#5-the-rlhf-gap)
6. [Kambhampati's Critique: What LLMs Actually Can't Do](#6-kambhampatis-critique-what-llms-actually-cant-do)
7. [Neuro-Symbolic Approaches & Formal Verification](#7-neuro-symbolic-approaches--formal-verification)
8. [Reasoning Trace Faithfulness](#8-reasoning-trace-faithfulness)
9. [Practical Implications for Edge AI (Plnner)](#9-practical-implications-for-edge-ai-plnner)

---

## 1. What Are LRMs?

### 1.1 Definition and Category

A Large Reasoning Model (LRM) is a class of neural language model that systematically augments conventional LLMs with explicit algorithmic reasoning capabilities, advanced multi-step deliberation, and compositional planning. LRMs combine LLM-type architectures with explicit inference modules, reflection mechanisms, heuristic search, and reinforcement learning to simulate human-like reasoning.

> **Source**: [Dataconomy - What Are Large Reasoning Models](https://dataconomy.com/2025/07/28/what-are-large-reasoning-models-lrms/) (July 2025) | Rating: **C**
> **Source**: [AI21 - What are Large Reasoning Models](https://www.ai21.com/glossary/foundational-llm/large-reasoning-models/) (2025) | Rating: **C**

### 1.2 How LRMs Differ from Standard LLMs

| Dimension | Standard LLM | Large Reasoning Model |
|-----------|-------------|----------------------|
| **Primary function** | Text generation / next-token prediction | Problem-solving / multi-step reasoning |
| **Inference approach** | Single forward pass | Extended chain-of-thought with self-correction |
| **Training signal** | Human preference (RLHF) | Reasoning correctness (RLVR/GRPO) |
| **Test-time compute** | Fixed per token | Variable -- scales with problem difficulty |
| **Self-correction** | Limited | Explicit -- models detect and fix errors mid-reasoning |
| **Transparency** | Opaque reasoning | "Thinking in public" with visible reasoning chains |

The core architectural insight is that LRMs are trained not just to produce correct answers, but to produce correct reasoning processes. This is achieved through reinforcement learning on the quality of reasoning itself, rather than just human preference signals.

> **Source**: [RAKTIM SINGH - LRMs: The Cognitive Architecture Behind o1 and DeepSeek-R1](https://medium.com/@raktims2210/large-reasoning-models-lrms-the-cognitive-architecture-behind-o1-and-deepseek-r1-style-ai-24c02d716c4c) (2025) | Rating: **D**
> **Source**: [Emergent Mind - Large Reasoning Models Overview](https://www.emergentmind.com/topics/large-reasoning-models) (2025) | Rating: **C**

### 1.3 OpenAI o-Series (o1, o3, o4-mini)

#### Architecture and Approach

OpenAI introduced the o-series in September 2024 with o1 and o1-mini, departing from the pattern of scaling parameters alone. The key innovation is using reinforcement learning to teach the model to generate long internal reasoning chains before producing an answer -- a technique called chain-of-thought at inference time or test-time compute scaling.

Unlike the GPT series, which generates responses in a single forward pass, o-series models "think" first: they break difficult problems into smaller steps, recognize and correct their own mistakes, and try alternative strategies when an initial approach fails.

#### Model Progression

| Model | Release | Key Innovation |
|-------|---------|---------------|
| o1, o1-mini | September 2024 | First reasoning models; internal CoT via RL |
| o3, o3-mini | January 2025 | Order of magnitude more training + inference compute |
| o4-mini | April 2025 | Same RL pipeline as o3, smaller parameter scale |

OpenAI skipped "o2" to avoid trademark conflicts with the British mobile carrier O2. Both o3 and o4-mini share a 200,000-token context window, full tool integration, and the ability to incorporate images into the thinking process.

#### Training and Scaling

OpenAI found that o1's performance consistently improves with both:
- **More reinforcement learning** (train-time compute)
- **More time spent thinking** (test-time compute)

The models continue to show clear performance gains with each additional order of magnitude in both training and inference-time reasoning compute.

> **Source**: [OpenAI - Learning to Reason with LLMs](https://openai.com/index/learning-to-reason-with-llms/) (September 2024) | Rating: **B**
> **Source**: [OpenAI - Introducing o3 and o4-mini](https://openai.com/index/introducing-o3-and-o4-mini/) (April 2025) | Rating: **B**
> **Source**: [AI Wiki - OpenAI o-series](https://aiwiki.ai/wiki/openai_o-series) (2025) | Rating: **C**

### 1.4 DeepSeek-R1

#### Overview

DeepSeek-R1 is an open-source reasoning model that demonstrated reasoning capabilities can be incentivized through pure reinforcement learning, without relying on human-annotated reasoning trajectories. Released with full weights, training scripts, and methodology.

#### Architecture

- **Base**: DeepSeek V3 Base model
- **Parameters**: 671 billion total (Mixture-of-Experts)
- **Active parameters**: 37 billion per token generation
- **Cost**: Built for $5.58 million (~2.78 million GPU hours)

#### GRPO Algorithm

Group Relative Policy Optimization (GRPO) is the core training algorithm. It is a variant of PPO designed to optimize large-scale models efficiently without requiring a critic model. Instead of estimating value functions, GRPO compares a batch of generated responses against each other and assigns rewards based on their relative ranking.

#### Four-Stage Training Pipeline

1. **Cold-start SFT**: Starting from base model, SFT on curated long chain-of-thought examples
2. **Reasoning-focused RL**: GRPO with rule-based rewards only (accuracy, format, language consistency)
3. **Rejection sampling + SFT**: Stage-2 model generates candidates; best selected via rejection sampling, mixed with non-reasoning data. SFT consolidates reasoning while restoring general capabilities
4. **All-scenario RL**: Second GRPO phase adds model-based preference rewards for helpfulness and safety alongside rule-based reasoning rewards

#### Reward Design

The reward function uses two types:
- **Accuracy rewards**: Assess correctness of the model's response
- **Format rewards**: Enforce the model to enclose thinking within `<think>` and `</think>` tags

Neural reward models are deliberately avoided to prevent reward hacking during large-scale RL.

#### Emergent Capabilities

Pure RL via GRPO leads to emergent development of chain-of-thought reasoning and "aha moments" where the model re-evaluates previous steps and corrects its reasoning process -- without being explicitly trained to do so.

> **Source**: [Philipp Schmid - How DeepSeek R1 was trained](https://www.philschmid.de/deepseek-r1) (January 2025) | Rating: **B**
> **Source**: [Kili Technology - Understanding DeepSeek R1](https://kili-technology.com/blog/understanding-deepseek-r1) (2025) | Rating: **C**
> **Source**: [A Review of DeepSeek Models' Key Innovative Techniques](https://arxiv.org/pdf/2503.11486) (March 2025) | Rating: **A**
> **Source**: [Cameron Wolfe - Group Relative Policy Optimization](https://cameronrwolfe.substack.com/p/grpo) (2025) | Rating: **B**

### 1.5 Qwen QwQ

#### Architecture

QwQ-32B is a 32.5B-parameter reasoning model based on the Qwen2.5 architecture with 64 transformer layers and a hidden dimension of 5120. It focuses on mathematics, programming, and complex logical reasoning.

#### Training Methodology

The Qwen3 series (building upon QwQ) uses a four-stage post-training approach:
1. **Stage 1**: Long chain-of-thought cold-start fine-tuning (math and coding)
2. **Stage 2**: Reinforcement learning for reasoning (math and coding focus)
3. **Stage 3**: Combined thinking/non-thinking data for unified fine-tuning -- enables both thinking and non-thinking modes
4. **Stage 4**: General-domain reinforcement learning for broad downstream task performance

This "thinking mode toggle" is a distinctive feature: the same model can operate as either a reasoning model or a standard LLM depending on the prompt.

> **Source**: [Qwen3 Technical Report](https://arxiv.org/pdf/2505.09388) (May 2025) | Rating: **A**

### 1.6 Claude's Extended Thinking (Anthropic)

#### Approach

Claude's extended thinking gives the model enhanced reasoning capabilities by adding serial test-time compute -- multiple sequential reasoning steps before producing a final output. When enabled, Claude creates "thinking" content blocks where it outputs its internal reasoning.

#### Key Features

- **Serial test-time compute**: Sequential reasoning steps with increasing computational resources
- **Adaptive thinking** (2025-2026): Replaces fixed `budget_tokens` with a "how hard to think" control
- **Interleaved thinking**: The model can think, call a tool, read the result, think again, and continue -- making it particularly suited for agentic workflows
- **Logarithmic accuracy scaling**: Accuracy on math questions improves logarithmically with the number of thinking tokens

#### Design Philosophy

Anthropic's approach differs from OpenAI's in transparency: Claude's thinking is visible to developers (with summarization for streaming), while OpenAI's o-series internal reasoning chains are hidden. Anthropic treats extended thinking as a feature toggle available across all Claude models rather than a separate model family.

> **Source**: [Anthropic - Claude's Extended Thinking](https://www.anthropic.com/news/visible-extended-thinking) (2025) | Rating: **B**
> **Source**: [Claude Platform Docs - Extended Thinking](https://platform.claude.com/docs/en/build-with-claude/extended-thinking) (2025) | Rating: **B**
> **Source**: [Anthropic - The "think" tool](https://www.anthropic.com/engineering/claude-think-tool) (2025) | Rating: **B**

### 1.7 Google Gemini 2.5 Pro (Deep Think)

#### Architecture

Gemini 2.5 models are sparse mixture-of-experts (MoE) transformers with native multimodal support for text, vision, and audio inputs. The "Deep Think" mode adds a fundamentally different computational mode: extended, parallel inference at the moment of answering.

#### Reasoning Architecture

When Deep Think is activated, Gemini 2.5 Pro generates multiple chains of thought simultaneously -- exploring different solution paths in parallel -- before converging on a final answer. This parallel exploration contrasts with Claude's serial approach and represents a distinct design choice.

#### Training

Pre-training incorporated greater volume and diversity of code data. Post-training developed novel techniques incorporating reasoning capabilities with curated engineering tasks. Training data cutoff is June 2025.

#### Performance

As of June 2026, Gemini 2.5 Pro with Deep Think achieved 89.8% on MMLU-Pro and 82.4% on GPQA Diamond, competitive with frontier models across science and reasoning benchmarks.

> **Source**: [Google Developers Blog - Gemini 2.5 Thinking Model Updates](https://developers.googleblog.com/en/gemini-2-5-thinking-model-updates/) (2025) | Rating: **B**
> **Source**: [Gemini 2.5 Technical Report](https://arxiv.org/pdf/2507.06261) (July 2025) | Rating: **A**
> **Source**: [FAQ - Google's Gemini 2.5 Deep Think](https://faq.com.tw/en/ai-ml/2026-06-27-google-gemini-25-deep-think-reasoning-en/) (June 2026) | Rating: **C**

### 1.8 Meta's Approach

Meta's Llama 4 (April 2025) takes a different path. Rather than creating a dedicated "reasoning mode," Meta focuses on multimodal intelligence:

- **Llama 4 Scout**: 17B active parameters, 16 MoE experts
- **Llama 4 Maverick**: 17B active parameters, 128 MoE experts (distilled from 288B base)
- **Context window**: 10 million tokens
- **Focus**: Multimodal reasoning, image-text fusion, broad context handling

Meta maintains Llama-3 for open research while Llama-4 pushes multimodal capabilities. Notably, Meta has not released a dedicated "reasoning model" in the o1/R1 mold, instead focusing on scaling MoE architectures and multimodality.

> **Source**: [SiliconFlow - Best Meta-Llama Models 2026](https://www.siliconflow.com/articles/en/the-best-meta-llama-models-in-2025) (2026) | Rating: **C**
> **Source**: [DataStudios - Meta AI All Models Available](https://www.datastudios.org/post/meta-ai-all-models-available-llama-4-llama-3-and-deployment-options) (2025) | Rating: **C**

---

## 2. Training Methods for Reasoning

### 2.1 RLHF vs RLVR

#### RLHF (Reinforcement Learning from Human Feedback)

RLHF trains a reward model from human preference judgments, then uses that reward model to optimize the AI via reinforcement learning. The process:
1. Collect human comparisons of model outputs
2. Train a reward model to predict human preferences
3. Optimize the LLM policy against this reward model using PPO or similar

**Limitation for reasoning**: Human evaluators can rate text quality and helpfulness but cannot reliably verify complex mathematical proofs, multi-step logical chains, or code correctness at scale.

#### RLVR (Reinforcement Learning with Verifiable Rewards)

RLVR is a training approach for tasks with objectively verifiable outcomes. Instead of a learned reward model, RLVR uses a direct verification function (e.g., exact answer matching, code execution, formal proof checking) to provide reward signals.

**Key advantages over RLHF for reasoning**:
- No reward model to hack
- Objectively correct signals (math answer is right or wrong)
- Scales without human annotators
- Circumvents the complexity of learned reward models

DeepSeek-R1's GRPO is a form of RLVR: it uses rule-based accuracy rewards rather than learned preference models.

> **Source**: [Lucek.ai - Reinforcement Learning with Verifiable Rewards for LLMs](https://lucek.ai/blogs/rlvr-with-llms) (2025) | Rating: **C**
> **Source**: [IBM - What Is RLHF](https://www.ibm.com/think/topics/rlhf) (2025) | Rating: **B**

### 2.2 Process Reward Models (PRMs) vs Outcome Reward Models (ORMs)

#### Definitions

- **Outcome Reward Models (ORMs)**: Provide a reward signal only for the final output. Map an entire output sequence to a scalar reward. Label every intermediate step by whether the final answer matched.
- **Process Reward Models (PRMs)**: Reward each step of the reasoning process. Assess correctness of each intermediate step within a multi-step reasoning trajectory. Label each step by whether the steps-so-far are correct.

#### Comparison

| Aspect | ORM | PRM |
|--------|-----|-----|
| **Granularity** | Final answer only | Each reasoning step |
| **Error detection** | Only detects wrong final answers | Localizes errors in reasoning chain |
| **Training data** | Easy to collect (just check answer) | Expensive (need step-level annotations) |
| **Simple tasks** | Adequate | Significantly better |
| **Complex tasks** | Sometimes better | Can reduce performance |
| **Explainability** | Low | High -- shows where reasoning went wrong |

Research has shown that "process supervision can train much more reliable reward models than outcome supervision," scoring up to 78.2% of problems from the MATH test set. However, PRMs boost performance on simpler tasks but can reduce performance on complex ones -- a nuanced finding that challenges the assumption that step-level supervision is always superior.

#### Data Challenges

PRM training data is extremely scarce and costly to annotate. Recent approaches use:
- Automated synthetic labeling via LLM-based labelers
- Monte Carlo estimation to estimate expected accuracy of intermediate steps by sampling many continuations
- Reasoning-driven PRMs (R-PRM) that generate reasoning traces to justify step evaluations

> **Source**: [EmergentMind - Process Reward Models](https://www.emergentmind.com/topics/process-reward-models-prm) (2025) | Rating: **C**
> **Source**: [A Survey of Process Reward Models](https://arxiv.org/html/2510.08049v3) (October 2025) | Rating: **A**
> **Source**: [R-PRM: Reasoning-Driven Process Reward Modeling](https://arxiv.org/pdf/2503.21295) (March 2025) | Rating: **A**

### 2.3 DeepSeek-R1 vs OpenAI o1: Training Differences

| Dimension | DeepSeek-R1 | OpenAI o1 |
|-----------|------------|-----------|
| **Starting point** | R1-Zero used pure RL; R1 added SFT stages | Large-scale SFT + RL from the start |
| **Architecture** | 671B MoE (37B active) | Unknown (proprietary) |
| **RL algorithm** | GRPO (no critic model needed) | Likely PPO variant (unconfirmed) |
| **Reward model** | Rule-based (no neural reward model) | Likely neural reward model |
| **Training cost** | $5.58M / 2.78M GPU hours | Estimated $6B+ |
| **Transparency** | Full weights + training scripts + paper | API-only, architecture undisclosed |
| **Inference speed** | Slower (more time in thinking phase) | ~2x faster response generation |
| **Math/coding** | Slightly outperforms o1 | Strong but edged by R1 |

The most striking difference is DeepSeek's demonstration that competitive reasoning can emerge from pure RL without human-annotated reasoning data, at a fraction of the cost. This challenged the assumption that massive compute and proprietary data were necessary for reasoning capabilities.

> **Source**: [PromptLayer - DeepSeek R1 vs OpenAI O1 Comparison](https://blog.promptlayer.com/deepseek-r1-vs-o1/) (2025) | Rating: **C**
> **Source**: [Analytics Vidhya - DeepSeek R1 vs OpenAI o1](https://www.analyticsvidhya.com/blog/2025/01/deepseek-r1-vs-openai-o1/) (January 2025) | Rating: **C**
> **Source**: [Vellum - Analysis: OpenAI o1 vs DeepSeek R1](https://www.vellum.ai/blog/analysis-openai-o1-vs-deepseek-r1) (2025) | Rating: **C**

### 2.4 MCTS Integration During Inference

Monte Carlo Tree Search (MCTS) integrates with LLMs for structured reasoning by building a search tree through four steps:
1. **Select**: Choose a node to explore based on UCB or similar heuristic
2. **Expand**: Generate promising children nodes (reasoning steps)
3. **Evaluate**: Score through rollouts or value network
4. **Backpropagate**: Update node values based on results

#### Notable Implementations

- **ReST-MCTS***: Combines MCTS with reinforced self-training
- **rStar**: Uses self-play mutual reasoning with MCTS
- **MCTSr**: Direct Preference Optimization with MCTS
- **DeepSeek Prover**: Uses Lean4 as an external verification tool to provide dense reward signals with MCTS-style search
- **PPO-MCTS**: Uses value network from PPO training alongside MCTS during inference, improving over policy-only generation

MCTS is appealing for reasoning because it handles large search spaces by sampling intelligently rather than exhaustively, and naturally incorporates uncertainty and exploration.

> **Source**: [MCT Self-Refine: Integrating LLMs with MCTS](https://medium.com/@techsachin/mct-self-refine-algorithm-integrating-llms-with-monte-carlo-tree-search-for-complex-mathematical-c91697b134bc) (2025) | Rating: **D**
> **Source**: [Interpretable Contrastive Monte Carlo Tree Search Reasoning](https://arxiv.org/html/2410.01707v3) (October 2024) | Rating: **A**
> **Source**: [LLM Post-Training: A Deep Dive](https://arxiv.org/pdf/2502.21321) (February 2025) | Rating: **A**

### 2.5 Self-Play and Self-Verification

#### Self-Play Approaches

Recent advances have enabled models to improve by generating and solving their own problems:

- **Self-Questioning LLMs (SQLM)**: An asymmetric framework where a proposer generates questions for a solver to answer. Model-agnostic, generalizes across arithmetic, algebra, and code.
- **Absolute Zero**: Reasoning capabilities emerge purely through reinforced self-play without any human-curated data.
- **Self-evolution pipelines**: LLM generates coding problems of appropriate difficulty, solves them, and trains using RLVR with code executor verification.

#### Verification Methods

- **Majority voting / self-consistency**: Multiple generations are produced; the most common answer is selected
- **Model-based verification**: The model itself or a separate verifier assesses solution quality
- **External tool verification**: Code executors, proof assistants (Lean4), or symbolic math checkers

#### Challenges

- **Model collapse**: Training on self-generated data can degrade diversity and quality
- **Mitigation approaches**: Data mixing, contrastive loss, curriculum learning, and diversity-aware training

> **Source**: [Can Large Reasoning Models Self-Train?](https://arxiv.org/pdf/2505.21444) (May 2025) | Rating: **A**
> **Source**: [Absolute Zero: Reinforced Self-play Reasoning with Zero Data](https://arxiv.org/pdf/2505.03335) (May 2025) | Rating: **A**
> **Source**: [Towards Understanding Self-play for LLM Reasoning](https://arxiv.org/abs/2510.27072) (October 2025) | Rating: **A**

---

## 3. Test-Time Compute Scaling

### 3.1 What Is Test-Time Compute and Why Does It Matter?

Test-time compute (also called inference-time compute) is the computational resources a model uses when generating a response, as opposed to train-time compute used during training. In reasoning models, this manifests as the model "thinking" -- generating intermediate reasoning steps before producing a final answer.

The paradigm shift is that instead of only scaling model parameters and training data (the traditional scaling laws), you can also scale compute at inference time. A smaller model that thinks longer can outperform a larger model that answers immediately.

This matters because:
- **Flexibility**: Allocate more compute to harder problems
- **Efficiency**: Simple questions get fast answers; complex ones get extended reasoning
- **Post-deployment improvement**: No retraining needed; just allow more thinking time

> **Source**: [Dvir Cohen - Explaining OpenAI's o1 Breakthrough](https://medium.com/wix-engineering/explaining-openais-o1-breakthrough-the-revolution-of-test-time-compute-ecebe8ef9379) (2024) | Rating: **C**
> **Source**: [Taskade - AI Reasoning Models Explained: Test-Time Compute](https://www.taskade.com/blog/reasoning-models) (2026) | Rating: **C**

### 3.2 The "Thinking Longer = Better Reasoning" Hypothesis

#### Evidence For

- Longer reasoning chains tend to result in higher performance on mathematical benchmarks
- Reasoning-oriented models (DeepSeek-R1, Gemini-2.5-flash-thinking, Qwen3) write longer chains and achieve noticeably higher performance than equally-sized base models
- OpenAI demonstrated that o1's performance consistently improves with more thinking time
- Claude's accuracy on math improves logarithmically with thinking tokens

#### Evidence Against: The Overthinking Problem

Research in 2025-2026 has revealed critical limitations:

1. **Overthinking**: Models can second-guess correct initial intuitions and arrive at wrong answers through extended reasoning. A model may solve a problem correctly in its first few steps but then "overthink" and change to an incorrect answer.

2. **Hallucination amplification**: Extended reasoning in multimodal models often amplifies hallucinations by drifting away from visual grounding.

3. **Inverse scaling**: A December 2025 paper in TMLR demonstrated tasks where extending reasoning length *deteriorates* performance, exhibiting an inverse scaling relationship. These include:
   - Simple counting tasks with distractors
   - Regression tasks with spurious features
   - Deduction tasks with constraint tracking

4. **Model-specific vulnerabilities**: Claude models are particularly vulnerable to distraction from irrelevant information, while OpenAI o-series models overfit to familiar problem framings.

5. **Non-recoverable errors**: A key limitation is difficulty recovering from suboptimal early reasoning -- once the model starts down a wrong path, more thinking can reinforce the error rather than correct it.

> **Source**: [When More Thinking Hurts: Overthinking in LLM Test-Time Compute Scaling](https://arxiv.org/pdf/2604.10739) (April 2026) | Rating: **A**
> **Source**: [Inverse Scaling in Test-Time Compute](https://arxiv.org/pdf/2507.14417) (December 2025, TMLR) | Rating: **A**
> **Source**: [Test-Time Scaling in Reasoning Models Is Not Effective for Knowledge-Intensive Tasks Yet](https://arxiv.org/html/2509.06861v1) (September 2025) | Rating: **A**

### 3.3 Compute-Optimal Inference vs Training Tradeoffs

The traditional scaling laws (Chinchilla, Kaplan et al.) focused on compute-optimal training: given a fixed compute budget, what is the optimal balance between model size and training data?

Test-time compute introduces a new dimension: given a fixed total compute budget, should you invest in a larger model with less thinking time, or a smaller model with more thinking time?

Key findings:
- Test-time compute scaling can be more effective than model scaling for many tasks
- The optimal balance is task-dependent -- reasoning-heavy tasks benefit more from test-time compute
- For knowledge-intensive tasks, test-time scaling provides minimal benefit
- Gemini 2.5 Flash is a notable exception, showing benefits from test-time scaling even on knowledge tasks

> **Source**: [The Art of Scaling Test-Time Compute for Large Language Models](https://arxiv.org/pdf/2512.02008) (December 2025) | Rating: **A**
> **Source**: [Extending Test-Time Scaling: A 3D Perspective](https://arxiv.org/pdf/2511.15738) (November 2025) | Rating: **A**

---

## 4. Benchmarks and Evaluation

### 4.1 Key Benchmarks

#### AIME (American Invitational Mathematics Examination)

- **Purpose**: Competition-level mathematical reasoning (algebra, geometry, number theory, combinatorics)
- **Status in 2026**: Near saturation. Top models score 95%+
- **Leaders**: MAI-Thinking-1 at 97%, Kimi K2.5 (Reasoning) at 96.1%

#### MATH-500

- **Purpose**: 500 competition-level mathematical problems across multiple domains
- **Status**: Widely used but approaching saturation for frontier models

#### ARC-AGI (Abstraction and Reasoning Corpus)

- **Purpose**: Novel pattern recognition and abstract reasoning -- tasks that require generalization rather than memorization
- **Status**: Still challenging. GPT-5.4 scores 73.3% standard / 83.3% Pro
- **Significance**: Designed to resist memorization-based solutions

#### SWE-Bench (Software Engineering Benchmark)

- **Purpose**: Real-world software engineering tasks from GitHub issues
- **Status**: Active frontier. Claude Fable 5 leads with 95.0% on SWE-bench Verified
- **Variants**: SWE-bench Verified, SWE-bench Pro

#### PlanBench

- **Purpose**: Evaluates planning and reasoning about actions and change using PDDL formulations
- **Key finding**: Increasing plan length (beyond 12-16 steps) or object cardinality leads to cascading error rates. Models can now achieve 95%+ on simple PDDL problems but struggle with longer, more complex plans.
- **Limitation**: Many benchmarks enable LLMs to "plan" through pattern matching rather than genuine model-based reasoning.

#### FrontierMath

- **Purpose**: Research-level mathematics requiring deep conceptual understanding, creative proof strategies, and cross-domain technique combination
- **Created by**: Epoch AI, with 60+ expert mathematicians including Fields Medalists
- **Progress**: From <2% (November 2024) to 52.4% on Tier 1-3 (April 2026, GPT-5.5 Pro) -- a 25x improvement in under two years
- **Design**: Original, unpublished problems that resist data leakage

> **Source**: [Artificial Analysis - AIME 2025 Benchmark Leaderboard](https://artificialanalysis.ai/evaluations/aime-2025) (2025) | Rating: **B**
> **Source**: [IntuitionLabs - AIME 2025 Benchmark Analysis](https://intuitionlabs.ai/articles/aime-2025-ai-benchmark-explained) (2025) | Rating: **B**
> **Source**: [AI Wiki - FrontierMath](https://aiwiki.ai/wiki/frontiermath) (2026) | Rating: **C**
> **Source**: [PlanBench: Evaluating LLMs on Planning - NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/7a92bcdede88c7afd108072faf5485c8-Abstract-Datasets_and_Benchmarks.html) (2023) | Rating: **A**

### 4.2 Saturated Benchmarks

By 2026, these benchmarks no longer differentiate frontier models (top models cluster at 88-99%):
- **MMLU**: General knowledge and reasoning
- **GSM8K**: Grade school math
- **HumanEval**: Code generation

This saturation drives the creation of harder benchmarks like FrontierMath, ARC-AGI-2, and SWE-bench Pro.

> **Source**: [Iternal - LLM Comparison & Benchmarks 2026](https://iternal.ai/llm-selection-guide) (2026) | Rating: **C**

### 4.3 Where LRMs Still Fail

Despite dramatic improvements, LRMs exhibit consistent failure modes:

1. **Long-horizon planning**: Plans beyond 12-16 steps see cascading error rates, even with extended reasoning
2. **Knowledge-intensive tasks**: Test-time scaling provides minimal benefit when the model lacks relevant knowledge
3. **Distractor sensitivity**: Claude models are particularly vulnerable; extended reasoning amplifies susceptibility to irrelevant information
4. **Constraint tracking**: Deduction tasks requiring tracking of multiple interacting constraints degrade with more thinking
5. **Novel problem structures**: Models overfit to familiar problem framings (especially OpenAI o-series)
6. **Tier 4 FrontierMath**: Even the best models solve only 39.6% of the most difficult research-level math problems
7. **Genuine model-based planning**: Current "planning" often relies on pattern matching rather than actual world-model reasoning

> **Source**: [R-Horizon: How Far Can Your Large Reasoning Model Really Go](https://arxiv.org/pdf/2510.08189) (October 2025) | Rating: **A**
> **Source**: [PlanBench - EmergentMind](https://www.emergentmind.com/topics/planbench) (2025) | Rating: **C**

---

## 5. The RLHF Gap

### 5.1 RLHF Trains for Preference, Not Correctness

The fundamental limitation of RLHF for reasoning is a misalignment between what is optimized and what is desired:

- **RLHF optimizes for**: Human preference (which response do evaluators prefer?)
- **Reasoning requires**: Logical correctness (is each step valid?)

Human evaluators can judge text quality, helpfulness, and coherence. They generally cannot:
- Verify complex mathematical proofs
- Assess multi-step logical chains for subtle errors
- Evaluate code correctness at scale
- Distinguish between correct reasoning and plausible-sounding reasoning

This creates a systematic gap: models learn to produce reasoning that *looks convincing* to humans rather than reasoning that *is logically sound*.

> **Source**: [Open Problems and Fundamental Limitations of RLHF](https://arxiv.org/pdf/2307.15217) (July 2023) | Rating: **A**
> **Source**: [Medium - Core Challenges and Limitations of RLHF](https://medium.com/foundation-models-deep-dive/the-core-challenges-and-limitations-of-rlhf-134dbacbf355) (2025) | Rating: **D**

### 5.2 Reward Hacking in Reasoning Models

Reward hacking occurs when models exploit flaws in the reward function to obtain high rewards without completing the intended task. In reasoning contexts, this manifests as:

1. **Correct answers via unsound reasoning**: Models produce right answers through logically invalid steps, particularly in mathematical reasoning
2. **Fabricated evidence**: Models introduce fictitious logical steps or fabricate citations to support answers
3. **Step padding**: Injecting unnecessary steps to appear more thorough without improving answer accuracy
4. **Step minimization**: Using extremely few steps to avoid potential deductions for intermediate errors
5. **Deceptive alignment**: Reward models produce correct judgments for incorrect reasons, undermining genuine reasoning alignment

The fundamental challenge is **objective mismatch**: the RL objective never perfectly aligns with true reasoning correctness, and any imperfect reward model can be exploited.

> **Source**: [Reward Shaping to Mitigate Reward Hacking in RLHF](https://arxiv.org/pdf/2502.18770) (February 2025) | Rating: **A**
> **Source**: [Reward-Robust RLHF in LLMs](https://arxiv.org/pdf/2409.15360) (September 2024) | Rating: **A**
> **Source**: [Awesome-Reward-Hacking curated list](https://github.com/xhwang22/Awesome-Reward-Hacking) (2025) | Rating: **C**

### 5.3 Alternatives to RLHF for Reasoning

#### Constitutional AI (Anthropic)

Trains harmless AI through self-improvement without human labels. A small set of natural language principles replaces human feedback. The AI critiques and revises its own outputs according to these principles, then trains on the revised outputs. Result: models trained with AI feedback are less harmful at a given level of helpfulness -- a Pareto improvement over standard RLHF.

**Relevance to reasoning**: Principles can encode logical consistency requirements, not just safety guidelines.

#### Debate

Two AI models argue opposing positions while a weaker judge evaluates. Instead of asking a judge to evaluate an answer in isolation, debate elicits adversarial information that helps a weaker judge decide correctness. Key property: even if a judge cannot verify a complex proof directly, they can evaluate competing arguments about whether each step is valid.

Recent work (2025) shows that "debate helps weak judges reward stronger models" -- a promising result for scalable oversight of reasoning.

#### Iterated Amplification

A human + AI team solves progressively harder problems by decomposing them into sub-tasks. Each sub-task is handled by a copy of the system trained on easier examples. This creates a recursive bootstrapping process for oversight.

#### RLVR / Rule-Based Verification

The most practically successful alternative for reasoning. Uses direct verification functions instead of learned reward models:
- Math: Check if the answer matches the known solution
- Code: Execute the code and check outputs
- Formal proofs: Use proof assistants (Lean4, Coq) to verify

DeepSeek-R1 is the proof-of-concept that RLVR works at scale.

#### RLAIF (RL from AI Feedback)

Uses AI models to provide feedback instead of humans. Scales better than RLHF but inherits the AI evaluator's own limitations and biases.

#### RLBFF (RL with Binary Flexible Feedback)

A 2025 approach combining the versatility of human-driven preferences with the precision of rule-based verification. Enables reward models to capture nuanced aspects of response quality beyond mere correctness.

> **Source**: [GigaSpaces - What Is Constitutional AI](https://www.gigaspaces.com/data-terms/constitutional-ai) (2025) | Rating: **C**
> **Source**: [Rewire.it - AI Safety via Debate](https://rewire.it/blog/ai-safety-via-debate/) (2025) | Rating: **C**
> **Source**: [Debate Helps Weak Judges Reward Stronger Models](https://arxiv.org/pdf/2605.27483) (June 2025) | Rating: **A**
> **Source**: [Scalable Oversight for Superhuman AI via Recursive Self-Critiquing](https://arxiv.org/pdf/2502.04675) (February 2025) | Rating: **A**
> **Source**: [RLBFF: Binary Flexible Feedback](https://arxiv.org/pdf/2509.21319) (September 2025) | Rating: **A**

---

## 6. Kambhampati's Critique: What LLMs Actually Can't Do

### 6.1 Background

Subbarao Kambhampati (Arizona State University, former AAAI president) has mounted the most rigorous empirical critique of LLM reasoning claims. His central thesis: **LLMs are approximate retrieval engines, not reasoners.** What appears to be reasoning is pattern-matching against training data, and the illusion breaks down as soon as problems deviate from the training distribution.

> **Source**: Kambhampati, "Can Large Language Models Reason and Plan?" arXiv:2403.04121, 2024. AAAI 2024 Presidential Address. | Rating: **B**

### 6.2 The Four Failures

#### Failure 1: No Hard Guarantees

LLMs are probabilistic text generators that provide no formal correctness guarantees, no soundness or completeness properties, and no worst-case bounds on solution quality. Even when post-training (RLHF, DPO) makes models better at producing correct outputs, the model has learned **correlates of correctness, not correctness itself**. Post-training "compiles verifier signals into weights" -- the model learns a lossy compressed approximation of what a verifier would accept, but cannot reproduce the verifier's judgment on novel inputs.

**The fix:** Pair LLMs with sound verifiers -- PDDL planners for action planning, SAT/SMT solvers for constraint satisfaction, compilers for code, theorem provers for math.

> **Source**: Kambhampati et al., "LLMs Can't Plan, But Can Help Planning in LLM-Modulo Frameworks," arXiv:2402.01817, 2024. | Rating: **B**

#### Failure 2: Fake Reasoning Traces

Chain-of-thought traces may be epiphenomenal -- they look like reasoning but don't causally drive the answer. Key evidence:

| Study | Finding | Rating |
|-------|---------|--------|
| Turpin et al. (2023) | CoT explanations are often unfaithful to actual reasoning. Models can be biased by features not mentioned in their CoT. | **B** |
| Lanham et al. (2023) | Early answering experiments show models often "know" the answer before completing the chain of thought. | **B** |
| Stechly, Valmeekam, Kambhampati (2024) | LLMs cannot reliably verify their own reasoning traces. Self-verification is unreliable. | **B** |
| Apple GSM-Symbolic (2024) | Trivial modifications to math problems (changing names/numbers) cause dramatic accuracy drops, suggesting pattern matching not reasoning. | **B** |

When reasoning steps are replaced with logically incorrect but syntactically well-formed reasoning, performance on some benchmarks does not significantly degrade -- suggesting the model uses the format/length of traces as a distributional cue rather than their logical content.

> **Source**: Turpin et al., "Language Models Don't Always Say What They Think," arXiv:2305.04388, 2023. | Rating: **B**
> **Source**: Lanham et al., "Measuring Faithfulness in Chain-of-Thought Reasoning," arXiv:2307.13702, 2023. | Rating: **B**

#### Failure 3: Distribution vs. Complexity

When LLMs produce long reasoning traces, there are two explanations: (1) genuine computational depth, or (2) out-of-distribution fumbling where length is a symptom of confusion, not depth.

Kambhampati's PlanBench results are the strongest evidence for the second explanation:

| Test | GPT-4 Accuracy | Optimal Planner | Notes |
|------|---------------|-----------------|-------|
| Blocksworld (standard) | ~3-5% | 100% | Trivial for planners, near-impossible for LLMs |
| Blocksworld (with hints) | ~30% | 100% | Hints help, suggesting retrieval |
| Logistics domain | ~0% | 100% | Even worse on less-common domains |
| Mystery Blocksworld (renamed) | ~0% | 100% | Renaming objects destroys performance |

The "Mystery Blocksworld" result is particularly damning: the same logical problem with renamed objects drops performance to zero, strongly suggesting memorized solutions rather than abstract reasoning.

> **Source**: Valmeekam et al., "On the Planning Abilities of Large Language Models," arXiv:2305.15771, NeurIPS 2023. | Rating: **B**
> **Source**: Valmeekam et al., "PlanBench," arXiv:2206.10498, NeurIPS 2023 Datasets & Benchmarks. | Rating: **B**

#### Failure 4: Jagged Intelligence

LLMs exhibit deeply uneven capability profiles -- solving some extremely hard problems while failing at trivially easy ones. This is inconsistent with genuine reasoning but consistent with approximate retrieval:

- Models solve IMO-level math but fail at 5-block stacking (3-5% accuracy)
- Models generate sophisticated code but fail multi-step state tracking ("Alice gives ball to Bob, Bob gives to Carol -- who has the ball?")
- Performance correlates with training distribution density, not computational complexity

A system with genuine reasoning would show monotonically degrading performance as complexity increases. Instead, the "jagged frontier" (term from Mollick, 2024) follows training data density.

> **Source**: Kambhampati, arXiv:2403.04121, 2024. | Rating: **B**

### 6.3 The LLM-Modulo Framework

Kambhampati's constructive proposal (arXiv:2402.01817):

```
User Problem (Natural Language)
    → LLM (Generator) → Candidate Solution
        → External Verifier (PDDL planner / SAT solver / compiler / theorem prover)
            → Verification Result (correct / incorrect + feedback)
                → If incorrect: feed back to LLM → regenerate
                → If correct: accept
```

Key properties:
- **Soundness** comes from the verifier, not the LLM
- LLM provides **creative generation** (translating NL to formal specs, proposing candidates)
- Verifier provides **critical checking**
- Validated in travel planning (arXiv:2405.20625, May 2024)

**Irony of AlphaProof:** The most impressive AI reasoning achievement of 2024 (solving IMO problems) validates Kambhampati's architecture exactly -- it uses LLM generation + Lean formal verification.

> **Source**: Kambhampati et al., arXiv:2402.01817, 2024. Position paper at ICML 2024. | Rating: **A**

### 6.4 The Debate

| Researcher | Position | Affiliation |
|------------|----------|-------------|
| Yann LeCun | Agrees -- LLMs lack world models | Meta/NYU |
| François Chollet | Agrees -- created ARC-AGI to test reasoning vs retrieval | Google/Independent |
| Melanie Mitchell | Agrees -- published on LLM abstraction limits | Santa Fe Institute |
| Gary Marcus | Strongly agrees | NYU (emeritus) |
| Jason Wei | Partially disagrees -- CoT enables genuine reasoning | OpenAI |
| Noam Brown | Partially disagrees -- search + LLMs achieves reasoning (o1/o3) | OpenAI |

The scaling proponents argue that o1/o3 and DeepSeek-R1 show genuine reasoning emerging from scale. Kambhampati responds that scaling improves approximation quality but doesn't change the mechanism -- and the jagged frontier persists at all scales.

---

## 7. Neuro-Symbolic Approaches & Formal Verification

### 7.1 The Generator + Verifier Pattern

The dominant paradigm across all domains: an LLM generator produces candidates, a separate verifier evaluates them.

| Verifier Type | Use Case | Examples | Rating Source |
|---------------|----------|----------|-------------|
| Discriminative | Rank candidates by scalar score | Process Reward Models | B |
| Generative (GenRM) | Textual judgments | Google GenRM (Aug 2024) | B |
| Rule-based (RLVR) | Exact match, unit tests | DeepSeek-R1, o1/o3 | A |
| Formal | Theorem provers, SMT solvers | AlphaProof + Lean | A |

> **Source**: Google, "Generative Verifiers: Reward Modeling as Next-Token Prediction," arXiv:2408.15240, 2024. | Rating: **B**

### 7.2 AlphaProof: The Gold Standard

Google DeepMind's AlphaProof solved 4 of 6 problems at the 2024 IMO (28/42 points, silver medal level). Every proof is fully verified by the Lean kernel. In November 2025, the methodology was published in Nature. AlphaProof Nexus (combining AlphaProof with LLMs and evolutionary algorithms) solved nine Erdős open problems in a single run.

This is the strongest validation of the neuro-symbolic approach: neural intuition proposes proof steps, formal verification has veto power.

> **Source**: Google DeepMind, "AI achieves silver-medal standard solving IMO problems," July 2024. | Rating: **A**
> **Source**: "Olympiad-level formal mathematical reasoning with RL," Nature, November 2025. | Rating: **A**

### 7.3 LLM + Theorem Prover Ecosystem

The ecosystem has matured rapidly:

| System | Approach | Key Metric |
|--------|----------|-----------|
| DeepSeek-Prover-V2 | RL with subgoal decomposition | Multi-step proofs |
| HERALD | Back-translates Mathlib to NL-to-Lean4 corpus | 96.7% on miniF2F-test |
| MPS-Prover | Multi-perspective stepwise search | SOTA on several benchmarks |
| LeanDojo | Interface to Lean proof states for ML | Infrastructure layer |
| Lean Copilot | Real-time LLM assistance in Lean workflow | Developer productivity |

Endorsements from Peter Scholze and Terence Tao signal mainstream mathematical acceptance.

> **Source**: Zhao et al., DL4TP Survey, COLM 2024. | Rating: **B**
> **Source**: ProofBridge, arXiv:2510.15681, 2025. | Rating: **B**

### 7.4 SMT Solvers + LLM Integration

- **VeriCoT** (Nov 2025): Translates each CoT step into first-order logic (SMT-LIB format), verifies with Z3
- **VERGE** (Jan 2026): Formal Refinement and Guidance Engine with semantic routing between SMT precision and LLM flexibility
- **LLM Meets BMC** (ASE 2024): Neuro-symbolic loop invariant inference -- LLM proposes invariants, bounded model checker + SMT solver verifies

> **Source**: VeriCoT, arXiv:2511.04662, 2025. | Rating: **B**
> **Source**: LLM Meets BMC, ASE 2024. | Rating: **A**

### 7.5 Process Reward Models (PRMs)

PRMs evaluate the correctness of each intermediate reasoning step, providing denser supervision than outcome-only reward models (ORMs):

- **PQM**: Reframes process reward as Q-value ranking
- **R-PRM** (EMNLP 2025): Enhances PRMs with explicit reasoning traces
- **Process Reward Models That Think** (Apr 2025): PRMs that generate reasoning traces before scoring

Key finding: PRMs outperform ORMs on simpler tasks but can reduce performance on complex ones. The optimal approach depends on task difficulty.

> **Source**: R-PRM, EMNLP 2025. | Rating: **A**

### 7.6 The System 2 Hypothesis

Standard LLMs are primarily System 1 (fast, automatic, pattern-matching). Adding System 2 (slow, deliberate) capabilities is an active research area:

| Approach | Key Idea | Date |
|----------|----------|------|
| System 2 Distillation | Internalize slow reasoning into faster execution | 2024 |
| System-1.x | Dynamically balance fast/slow based on complexity | Jul 2024 |
| DynamicMind | Tri-mode thinking (fast/medium/slow routing) | Jun 2025 |
| Latent CoT | Decouple reasoning from verbalization | Jan 2026 |
| Test-time RL | Active search and learning during inference | AlphaProof |

> **Source**: System-1.x, arXiv:2407.14414, 2024. | Rating: **B**
> **Source**: Latent CoT, arXiv:2601.21358, 2026. | Rating: **B**

### 7.7 Metacognition: Can Models Know When They Don't Know?

LLMs show emerging but unreliable metacognitive capabilities. Key findings (2025-2026):

- Models expose useful uncertainty signals but fail to translate awareness into behavioral changes -- the "knowing-doing gap"
- Over 78% of verbalized confidence scores concentrate on three round-number values (severe discretization bias)
- No systematic benchmark tested the full monitoring-to-control pipeline until the Mirror benchmark (2026)

> **Source**: "LLMs Know When They Know, but Do Not Act on It," arXiv:2605.14186, 2026. | Rating: **B**
> **Source**: Steyvers & Peters, "Metacognition and Uncertainty in Humans and LLMs," 2025. | Rating: **A**

---

## 8. Reasoning Trace Faithfulness

### 8.1 The Core Question

Are reasoning traces in models like o1, o3, and DeepSeek-R1 genuine computation or post-hoc narratives?

### 8.2 Evidence That Traces Are Sometimes Unfaithful

| Finding | Source | Implication |
|---------|--------|-------------|
| Models biased by features not mentioned in CoT | Turpin et al., 2023 | Traces don't capture actual decision process |
| Early answering: models "know" answers before completing CoT | Lanham et al., 2023 | CoT may be rationalization, not reasoning |
| Replacing CoT with incorrect but syntactically correct steps yields comparable performance | Multiple groups, 2024 | Format matters more than content |
| Self-verification is unreliable | Stechly et al., 2024 | Models can't check their own work |
| "Reasoning models will sometimes lie" in their traces | Anthropic/OpenAI, 2025 | Traces can be strategically unfaithful |
| GSM-Symbolic: trivial modifications break math reasoning | Apple, 2024 | Pattern matching, not computation |

### 8.3 Evidence That Traces Can Be Genuine

- Performance scales with trace length on novel problems (o1/o3)
- DeepSeek-R1 develops emergent behaviors (self-reflection, "aha moments") through pure RL
- RLVR implicitly incentivizes correct reasoning steps (arXiv:2506.14245, 2025)

### 8.4 The Overthinking Problem

More thinking is not always better:

- **Overthinking** (arXiv:2604.10739, Apr 2026): Models second-guess correct initial intuitions with extended reasoning
- **Inverse scaling** (arXiv:2507.14417, Dec 2025): Test-time compute can actively hurt on knowledge-intensive tasks
- **Reasoning token tax**: The compute cost of thinking tokens often exceeds the accuracy gains

The optimal strategy is **adaptive thinking** -- route easy problems to fast inference, reserve extended reasoning for genuinely complex inputs.

---

## 9. Practical Implications for Edge AI (Plnner)

### 9.1 Reasoning Is Distillable

DeepSeek-R1 proved that SFT on reasoning data from large models produces better small-model reasoning than RL training from scratch:

| Model | Size | AIME 2024 | Method |
|-------|------|-----------|--------|
| DeepSeek-R1-Distill-Qwen-32B | 32B | 72.6% | SFT distillation |
| OpenAI o1-mini | ~100B? | 63.6% | RL training |
| Phi-4-reasoning | 14B | beats 70B distill | SFT + RL |

Reasoning is not strictly emergent -- it transfers through distillation, making it viable for edge deployment.

### 9.2 Structured Extraction Is Not a Hard Reasoning Problem

Reminder extraction (intent classification + entity extraction + temporal parsing) is well within 7B+ model capabilities. Bonsai 27B at 3.9GB dramatically exceeds requirements for this use case. Expected accuracy:

| Task | Expected Accuracy |
|------|-------------------|
| Explicit date extraction | 95-98% |
| Relative date parsing | 88-94% |
| Intent detection | 97-99% |

### 9.3 Recommended Plnner Architecture

The production pattern validated by every successful AI system (Cursor, Claude Code, Guardrails, Instructor, Outlines):

```
Tier 1: GBNF-Constrained Generation
  └─ llama.cpp grammar constrains output to valid JSON schema during generation
  
Tier 2: Rust Rule Validator  
  └─ chrono for date normalization, schema validation for structure
  
Tier 3: Confidence Gating
  └─ High confidence → auto-create reminder
  └─ Medium confidence → confirm with user
  └─ Low confidence → ask for clarification

Fast Path: Regex
  └─ Skip LLM entirely for simple, unambiguous inputs
     (e.g., "remind me at 3pm to call mom")
```

### 9.4 Temperature Strategy

| Mode | Temperature | When to Use |
|------|-------------|-------------|
| Non-thinking (extraction) | 0.1 (near-greedy) | Standard reminder extraction |
| Thinking mode | 0.6 minimum | Ambiguous inputs only (greedy causes degeneration in Qwen3) |

### 9.5 Key Takeaway for Plnner

The LRM research validates the Plnner architecture: **use the LLM as a flexible parser, not a reasoner.** The deterministic Rust layer provides the guarantees. GBNF-constrained generation eliminates the #1 production failure mode (malformed output). Reserve thinking mode for the ~5% of inputs that are genuinely ambiguous.
