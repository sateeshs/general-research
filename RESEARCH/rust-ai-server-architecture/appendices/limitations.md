# Research Limitations

## Known Gaps

### 1. Twitter/X Content Not Fetched
The tweet at https://x.com/juntao/status/2016602181474882045 ("Rust is the language of AGI") could not be directly fetched due to platform restrictions. The argument in Section 5.1 of the full report is reconstructed from juntao's public projects and profile, not from the tweet itself.

### 2. Bonsai 27B Format Compatibility Unknown
Whether Bonsai 27B's 1-bit/ternary QAT format is directly compatible with llama.cpp's GGUF format has not been verified. PrismML may use a custom format requiring a specific inference engine. **This is the highest-priority gap to close before implementation.**

### 3. No First-Party Benchmarks Run
All performance numbers are from third-party sources. No benchmarks were run on Plnner's target hardware (Pi 5, Jetson Orin Nano). Real-world performance may differ due to thermal throttling, memory contention, and OS overhead.

### 4. WasmEdge LLM-Specific Benchmarks Missing
No WasmEdge wasi-nn benchmarks specifically comparing LLM inference performance against native llama.cpp were found. The 1.74x overhead figure is for general compute, not AI inference specifically.

### 5. Limited Academic Sources
Most sources are engineering blogs, GitHub repositories, and tech news sites (Rating B-C). Only 5 sources achieved Rating A (peer-reviewed/authoritative). The Rust AI ecosystem is too new for extensive academic literature.

### 6. Agent 4 Data
Agent 4 (AI-assisted development, Second State, open-source hardware) was still completing when synthesis began. Its findings were partially incorporated. The open-source hardware section is less comprehensive than other sections.

### 7. Rust Training Ecosystem
Research focused primarily on inference. The Rust training ecosystem (burn for on-device fine-tuning) was not deeply investigated. This is relevant for Plnner's weekly engagement model retraining.

### 8. ESP32 Rust Firmware Details
The embedded Rust (esp-rs) ecosystem for ESP32 firmware was not deeply researched. EchoKit uses Rust on ESP32, but the specific firmware architecture patterns were not analyzed in detail.

## Confidence Levels

| Section | Confidence | Reason |
|---------|-----------|--------|
| Framework comparison | **High** | Multiple corroborating sources, GitHub data |
| PrismML Bonsai 27B | **High** | Multiple reputable sources, recent release |
| Performance benchmarks | **Medium-High** | Third-party only, no first-party validation |
| Communication patterns | **High** | Well-established patterns, production examples |
| Edge architecture | **High** | Validated by EchoKit, llama.cpp patterns |
| AI-assisted development | **Medium** | Limited to one case study (qwen3_tts_rs) |
| Open-source hardware | **Medium** | Less thoroughly researched |
| WASM for AI | **Medium** | Sparse LLM-specific benchmarks |

## Recommendations for Follow-Up

1. **Validate Bonsai 27B format** — Download model, test with llama-cpp-rs
2. **Run first-party benchmarks** — Bonsai on Pi 5, measure tokens/sec, memory, thermals
3. **Deep-dive ESP32 Rust firmware** — esp-rs ecosystem, audio codec support
4. **Investigate burn for training** — On-device fine-tuning feasibility
5. **Fetch the juntao tweet** — Use Twitter API or visit directly
