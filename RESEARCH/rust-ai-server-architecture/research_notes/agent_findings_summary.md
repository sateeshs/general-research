# Agent Findings Summary

## Agent 1: Rust AI Frameworks, PrismML, Benchmarks, History

**Key Findings:**
- Candle (HuggingFace, 20.7k stars): 55% faster LLM inference than PyTorch, pure Rust, WASM support
- Burn (Tracel AI, 15.4k stars): Only Rust framework with training + inference, 98% PyTorch CPU perf
- llama-cpp-rs: Production-ready, tracks upstream llama.cpp with TurboQuant and speculative decoding
- tract (Sonos): Production-proven at Sonos for wake-word, zero external deps, ideal for embedded
- ort: ONNX Runtime wrapper, 3-5x faster than Python, broadest hardware support
- ggml-rs: DEPRECATED — do not use for new projects
- PrismML Bonsai 27B: 3.9GB (1-bit) / 5.9GB (ternary), 89.5-94.6% FP16 quality retention
- Historical timeline: 2019 foundations → 2023 framework explosion → 2025 enterprise adoption → 2026 convergence
- Rust Foundation position statement (May 2025): official endorsement of Rust for AI

**Sources:** 35+ sources, 1 Rating A, 18 Rating B, 14 Rating C, 2 Rating D

---

## Agent 2: EchoKit, qwen3_tts_rs, Pulsar, "Rust for AGI"

**Key Findings:**
- EchoKit: Full-stack Rust voice AI agent — ESP32 hardware + Rust WebSocket server + ASR/LLM/TTS pipeline
- Built by Michael Yuan (juntao) — PhD astrophysics, founder of WasmEdge (10.7k stars), Second State
- qwen3_tts_rs: Three CLI tools (tts, voice_clone, api_server), dual backends (libtorch + MLX)
- Voice cloning fix: Transitioned from X-vector embeddings to ICL-only with zero-embedding fallback
- Claude Opus 4.6/4.7 co-authored commits on qwen3_tts_rs (verified in commit history)
- Pulsar: Runs 1T parameter models on 2x 16GB consumer GPUs via NVMe streaming
- Pulsar uses io_uring + O_DIRECT for zero-copy disk I/O, four-tier expert hierarchy
- "Rust for AGI" tweet could not be fetched; argument reconstructed from public projects

**Sources:** 12+ sources, 0 Rating A, 1 Rating B, 6 Rating C, 1 Rating D

---

## Agent 3: Flutter ↔ Rust Patterns, Edge Server Architecture

**Key Findings:**
- flutter_rust_bridge (4k+ stars): Best for on-device mobile FFI, StreamSink for token streaming
- REST + SSE: Best for LAN client-server (OpenAI API pattern for token streaming)
- WebSocket: Best for ESP32 bidirectional audio streaming
- gRPC (tonic, 10k+ stars): Future consideration for structured multi-model API
- axum confirmed as correct choice: native tokio, Tower middleware, built-in SSE/WebSocket, 20k+ stars
- Production Flutter+Rust apps: AppFlowy (58k stars), RustDesk (80k stars) validate the stack
- Inference queue: Semaphore-guarded (max 1 concurrent) with priority queue (P0 emergency → P4 background)
- Multi-model serving: Time-sliced on edge (one model at a time), pipeline parallelism as optimization
- Memory management: mmap for model loading, memory pressure monitoring with graceful degradation
- Hardware acceleration: Priority probe CUDA > RKNN NPU > Vulkan > OpenCL > CPU NEON > CPU AVX
- API surface: REST for CRUD, SSE for streaming, WebSocket for voice, mDNS for discovery

**Sources:** 15+ sources, 0 Rating A, 12 Rating B, 3 Rating C

---

## Agent 4: AI-Assisted Development, Second State, Open-Source Hardware

**Status:** Still completing at time of synthesis. Partial findings incorporated from available data.

**Expected Coverage:**
- Claude Code + Rust compiler feedback loop patterns
- Python → Rust ML porting challenges
- Second State / WasmEdge ecosystem details
- RISC-V AI accelerators and open-source hardware
- ESP32 + AI coprocessor combinations

---

## Agent 5: Cross-Reference & Fact-Checking

**Claim Verification Results:**

| Claim | Verdict | Key Evidence |
|-------|---------|-------------|
| "Rust ~100x faster" | **Partially confirmed** | 100x for pure loops only. AI inference: 7-10x. Same ONNX backend: 1.29x |
| "Memory safety eliminates bug classes" | **Confirmed** | 70% of MS/Google CVEs are memory safety (3 Rating A sources) |
| "Phone-ready LLMs at ~3.9GB" | **Confirmed** | 3-4B models Q4 fit in 2-3GB, 14-32 tok/s on flagships |
| "Rust AI ecosystem production-ready" | **Partially confirmed** | Yes for inference. Major gaps in training and model zoo |
| "WASM viable for AI inference" | **Partially confirmed** | WasmEdge AOT 1.74x native. No LLM-specific benchmarks |

**Recommendation:** Update project memory "~100x" claim to "7-10x for inference serving."

**Sources:** 20+ sources, 3 Rating A, 7 Rating B, 5 Rating C
