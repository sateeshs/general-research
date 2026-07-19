# Data & Statistics

## Performance Benchmarks

### Rust vs Python AI Inference

| Metric | Value | Context | Source |
|--------|-------|---------|--------|
| Pure CPU computation | 100x faster | 1B integer sum, no C extensions | github.com/Paulescu/why-rust |
| AI inference throughput | 7-10x higher | ONNX serving, request/sec | dasroot.net, Feb 2026 |
| ONNX serving throughput | 9.23x | 328.94 vs 35.62 req/sec | Substack, M. Subonis |
| Same ONNX backend | 1.29x | Rust vs Python wrapper only | Same source |
| Recommendation system | 8x latency reduction | 145ms → 18ms | Medium, 2025 |
| Memory reduction | 60-80% | ort vs Python ONNX Runtime | Calmops, 2025 |
| Tokenization | 10-100x | HF tokenizers (Rust) | Andrew Odendaal |

### Rust AI Framework Performance

| Framework | Benchmark | Result | Source |
|-----------|-----------|--------|--------|
| Candle | LLM inference | 128.3 tok/s (vs PyTorch 82.7) | Markaicode |
| Candle | BERT inference | 47% faster than PyTorch | Markaicode |
| Candle | Edge inference | 3.5x faster than Python | Markaicode |
| Burn | CPU training | 98% of PyTorch perf | Calmops |
| Burn | GPU training | 92% of PyTorch perf | Calmops |
| mistral.rs | Mistral 7B Q4_K_M (RTX 3090) | 120 tok/s | Zylos Research |
| ShaktiCore | ResNet-50 (RTX 3060) | 168x vs TensorFlow | DEV Community |

### PrismML Bonsai 27B

| Metric | Ternary (5.9 GB) | 1-Bit (3.9 GB) |
|--------|-------------------|-----------------|
| Bits per weight | 1.71 bpw | 1.125 bpw |
| FP16 quality retention | 94.6% | 89.5% |
| MATH-500 | 99.20 | — |
| AIME 2025 | 90.84 | — |
| HumanEval+ | 93.90 | — |
| iPhone 17 Pro speed | ~11 tok/s | ~11 tok/s |
| Memory savings vs FP16 | 10-15x | 10-15x |
| Energy savings vs FP16 | 3-6x | 3-6x |

### Phone LLM Inference Speeds

| Model | Device | Tokens/sec | Type |
|-------|--------|-----------|------|
| RedPajama-3B Q4 | iPhone 13 Pro Max | 14.3 decode, 81.8 prefill | Benchmark |
| RedPajama-3B Q4 | Xiaomi 13 | 16.3 decode, 88.1 prefill | Benchmark |
| Qwen 2.5 | iPhone 17 Pro | 24-32 | Benchmark |
| Qwen 2.5 1.5B | OnePlus 12 | 19.7 | Android |
| Bonsai 27B | iPhone 17 Pro | ~11 | Vendor claim |

### Pulsar — Large Model Inference on Consumer Hardware

| Model | Parameters | Tokens/sec | Hardware |
|-------|-----------|-----------|----------|
| Qwen3.6-35B-A3B | 35B | 51.8 | 2x 16GB GPU |
| Gemma 4 26B-A4B | 26B | 41.0 | 2x 16GB GPU |
| DeepSeek-V4-Flash | 284B | 8.2 (11.3 w/ CPU) | 2x 16GB GPU |
| GLM-5.2 | 743B | 1.7 (2.4 w/ CPU) | 2x 16GB GPU |
| Kimi K2.7 | 1T | 1.3 | 2x 16GB GPU |

### WASM AI Inference Overhead

| Runtime | Mode | Overhead vs Native |
|---------|------|-------------------|
| WasmEdge | AOT | 1.74x |
| WasmEdge | Interpreter | 10-50x |
| Wasmtime | AOT | 1.3-1.5x |
| Browser WASM | General | 2-5x |

## Ecosystem Growth

### GitHub Stars (mid-2026)

| Project | Stars | Corporate Backing |
|---------|-------|-------------------|
| llama.cpp | 100k+ | Community |
| RustDesk | 80k+ | Community |
| AppFlowy | 58k+ | AppFlowy Inc |
| Polars | 30k+ | Polars Inc |
| Candle | 20.7k | HuggingFace |
| actix-web | 22k+ | Community |
| axum | 20k+ | Tokio team |
| Burn | 15.4k | Tracel AI |
| WasmEdge | 10.7k | Linux Foundation |
| tonic | 10k+ | Tokio ecosystem |
| Rig | ~6.7k | Community |
| flutter_rust_bridge | 4k+ | Community |

### Memory Safety Statistics

| Organization | Memory Safety Bugs % | Source Rating |
|-------------|---------------------|--------------|
| Microsoft | ~70% of CVEs | A |
| Google Chrome | ~70% of serious bugs | A |
| Android | ~70% (50% use-after-free) | A |

## Quantization Format Comparison

| Technique | Best For | Quality Loss | Speed | Compatibility |
|-----------|---------|-------------|-------|--------------|
| GGUF Q4_K_M | CPU, mobile, edge | 1-3% perplexity | Good | llama.cpp, Ollama |
| AWQ | GPU inference | ~1% perplexity | Fastest GPU | vLLM, TRT-LLM |
| GPTQ | GPU inference | 1-2% perplexity | Fast GPU | HF, vLLM |
| MLX 4-bit | Apple Silicon | ≈GGUF Q4 | Faster on Apple | Apple only |
| Bonsai QAT (ternary) | Phone/edge | 5.4% quality loss | Fast CPU | Custom |
| Bonsai QAT (1-bit) | Phone/edge | 10.5% quality loss | Fastest CPU | Custom |
