# Executive Summary: Rust AI Server Architecture for Plnner

**Research Date:** July 19, 2026

---

## The Verdict

Rust is production-ready for edge AI inference serving in 2026. The ecosystem has crossed a meaningful threshold — candle (20.7k stars), burn (15.4k stars), and llama-cpp-rs provide mature inference capabilities. PrismML's Bonsai 27B (3.9GB, 1-bit quantization retaining 89.5% of FP16 quality) makes 27B-parameter models viable on phones and SBCs. The Plnner architecture's choice of Rust + axum + llama.cpp-rs is well-validated by the ecosystem.

---

## Key Findings

### 1. Framework Selection: Validated

The Rust AI inference ecosystem has consolidated around clear winners:

| Use Case | Framework | Maturity |
|----------|-----------|----------|
| LLM inference (Plnner primary) | **llama-cpp-rs** | Production-ready, tracks upstream |
| Pure Rust inference | **candle** | High, HuggingFace-backed |
| Training + inference | **burn** | Medium, growing fast |
| Embedded/IoT (ESP32-class) | **tract** | Production-proven at Sonos |
| ONNX model serving | **ort** | Production-ready |

**Recommendation:** llama-cpp-rs for Bonsai 27B inference, tract for lightweight on-device models (wake word, engagement scoring), candle as a fallback if llama.cpp quantization formats don't support 1-bit Bonsai.

### 2. PrismML Bonsai 27B: Game-Changer for Plnner

Released July 14, 2026. Key numbers:

- **1-bit variant:** 3.9 GB, 89.5% of FP16 quality, 1.125 bits per weight
- **Ternary variant:** 5.9 GB, 94.6% of FP16 quality, 1.71 bits per weight
- **iPhone 17 Pro:** ~11 tokens/second
- **MATH-500:** 99.20 (ternary), near full-precision
- **HumanEval+:** 93.90 (ternary), strong code generation

This is the model Plnner should target. The 3.9GB 1-bit variant fits comfortably on 8GB devices with room for ASR + TTS models.

### 3. Performance Reality Check

The "~100x faster than Python" claim is a microbenchmark. Real-world numbers:

| Scenario | Rust Advantage |
|----------|---------------|
| Pure CPU computation (no C extensions) | 50-100x |
| AI inference serving (throughput) | 7-10x |
| AI inference with CUDA backends | 1.3-3x |
| Memory usage reduction | 60-80% |
| GC pause elimination | Total (zero pauses) |

**For Plnner's CPU-only edge inference**, the advantage skews toward 7-10x — highly significant for responsiveness.

### 4. Architecture Patterns: EchoKit as Blueprint

EchoKit (by juntao/Second State) is the closest existing implementation to Plnner's architecture:

- ESP32 hardware → WebSocket → Rust server → ASR → LLM → TTS → audio back
- Same three-tier pattern Plnner uses
- Same voice pipeline architecture
- Open source, Apache-2.0 licensed

**Pulsar** demonstrates Rust can scale to trillion-parameter MoE models on consumer hardware via SSD streaming — relevant for future Plnner scaling.

### 5. Communication Patterns: Updated with WebRTC

| Client | Protocol | Why |
|--------|----------|-----|
| Flutter Mobile (on-device) | flutter_rust_bridge (FFI) | Zero overhead, direct memory |
| Flutter clients (LAN) | REST + SSE | SSE for token streaming, REST for CRUD |
| ESP32 peripherals | **WebRTC (esp_peer + str0m)** | Industry standard for voice AI; built-in AEC/AGC/VAD; UDP resilience |
| ESP32 (MVP fallback) | WebSocket | Simpler for initial development, acceptable on LAN |
| Kiosk (same SBC) | REST or Unix domain socket | Co-located, low latency |

**Key finding:** Espressif has an **official first-party WebRTC stack** (`esp-webrtc-solution`, 376 stars, 13 demo projects). WebRTC on ESP32-S3 is feasible — uses ~196KB/512KB internal SRAM and ~370KB/8MB PSRAM for audio-only. CPU for Opus encoding (~70% one core) is the constraint. Voice AI industry (OpenAI, LiveKit, Cloudflare) has converged on WebRTC as standard transport.

axum + str0m (Sans-I/O Rust WebRTC) is the recommended server stack. Production-validated by AppFlowy (58k stars) and RustDesk (80k stars) for Flutter + Rust architectures.

### 6. AI-Assisted Rust Development: Proven

The qwen3_tts_rs project demonstrates Claude Code co-authoring production Rust with Michael Yuan. The compiler-as-feedback-loop pattern (write → compile → fix → iterate) makes Rust uniquely suited for AI-assisted development — the type system catches entire categories of bugs that would silently pass in Python.

---

## Risks and Gaps

| Risk | Severity | Mitigation |
|------|----------|------------|
| Bonsai 27B 1-bit format may not be supported by llama.cpp | **HIGH** | Verify GGUF compatibility; fallback to candle |
| Rust AI ecosystem still immature for training | **MEDIUM** | Train in Python, serve in Rust (hybrid approach) |
| Limited pre-trained model zoo vs Python | **MEDIUM** | Use ONNX export or safetensors import |
| WASM overhead (~1.7x native) if targeting browser | **LOW** | Use native compilation for primary targets |
| ESP32 firmware in Rust requires embedded expertise | **MEDIUM** | Follow EchoKit patterns, use esp-rs ecosystem |

---

## Recommended Next Steps

1. **Validate Bonsai 27B with llama-cpp-rs** — Download the 1-bit GGUF, run inference benchmarks on target hardware (Pi 5, Jetson)
2. **Prototype the axum + str0m server** — REST + SSE + WebRTC endpoints, model loading, inference queue
3. **ESP32 WebRTC MVP** — Use Espressif's `esp_peer` with Opus 16kHz mono; start with WebSocket fallback, migrate to WebRTC
4. **Benchmark communication overhead** — flutter_rust_bridge FFI vs REST vs WebRTC on target devices
5. **Set up CI with Claude Code** — Leverage the compiler feedback loop for rapid Rust development
6. **Evaluate ESP32-P4** — 400MHz RISC-V with hardware CNN accelerator; requires companion chip for WiFi but reduces Opus CPU to ~42%
