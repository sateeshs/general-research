# Executive Summary: LLM Reasoning Limitations for Edge AI

## Key Findings

### 1. Reasoning CAN be distilled to small models
DeepSeek-R1 proved that supervised fine-tuning on reasoning data from large models produces better small-model reasoning than training from scratch with RL. A 32B distilled model beats OpenAI o1-mini. Microsoft's Phi-4-reasoning (14B) beats DeepSeek-R1-Distill-70B. Reasoning is not strictly emergent -- it transfers.

### 2. Structured extraction is NOT a hard reasoning problem
Reminder/task extraction is primarily intent classification + entity extraction + temporal parsing. These are well within 7B+ model capabilities. Bonsai 27B (Qwen3.6-based) dramatically exceeds the reasoning requirements for this use case.

### 3. The dominant production pattern is LLM + deterministic verifier
Every successful production AI system (Cursor, Claude Code, Devin, Guardrails, Instructor, Outlines) uses the same pattern: LLM generates flexible output, deterministic system validates and normalizes. This is the recommended architecture for Plnner.

### 4. Constrained decoding eliminates parsing failures
Libraries like Outlines and llama.cpp's GBNF grammars guarantee valid structured output during generation, not post-hoc. This should be Plnner's primary reliability mechanism.

### 5. 95%+ accuracy is achievable and acceptable
With a three-tier pipeline (constrained generation + rule validation + confidence gating), Plnner can achieve >95% extraction accuracy. Users tolerate this level when given easy correction mechanisms.

## Recommendation for Plnner

Use Bonsai 27B with GBNF-constrained extraction, backed by a Rust rule validator (chrono for dates, schema validation for structure), with a regex fast-path for simple inputs and confidence-based UX gating. Reserve thinking mode for ambiguous inputs only.
