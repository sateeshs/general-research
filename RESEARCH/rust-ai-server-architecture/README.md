# Rust AI Server Architecture — Deep Research

**Research Date:** July 19, 2026  
**Purpose:** Architectural decision-making for Plnner companion app  
**Scope:** Historical evolution, current state, near-term trajectory

## Research Question

What are the proven Rust AI inference server architectures, client-server communication patterns, and real-world implementations relevant to building a privacy-first edge AI server for the Plnner companion app?

## Documents

| Document | Description |
|----------|-------------|
| [Executive Summary](executive_summary.md) | 2-page key findings and recommendations |
| [Full Report](full_report.md) | Complete 40+ page analysis |
| [Data & Statistics](data/statistics.md) | Benchmarks, performance numbers, comparisons |
| [Source Quality Table](sources/source_quality_table.md) | A-E rated bibliography |
| [Bibliography](sources/bibliography.md) | Complete source list with URLs |
| [Agent Findings Summary](research_notes/agent_findings_summary.md) | Raw outputs from 5 research agents |
| [WebRTC ESP32 Feasibility](../esp32-webrtc-feasibility/full_report.md) | WebRTC vs WebSocket analysis for ESP32 voice pipeline |
| [Methodology](appendices/methodology.md) | Research methods and agent deployment |
| [Limitations](appendices/limitations.md) | Known gaps and caveats |

## Key Projects Researched

- **Candle** (Hugging Face) — Pure Rust ML inference framework
- **Burn** (Tracel AI) — Rust-native training + inference
- **PrismML Bonsai 27B** — 3.9GB phone-ready 27B parameter LLM
- **EchoKit** — ESP32 + Rust voice AI agent platform
- **qwen3_tts_rs** — Rust TTS implementation with AI-assisted development
- **Pulsar** — SSD-streaming engine for trillion-parameter MoE models
- **tract** (Sonos) — Production edge inference with zero dependencies
- **ort** — ONNX Runtime Rust bindings

## Research Agents Deployed

| Agent | Focus | Sources Found |
|-------|-------|---------------|
| Agent 1 | Rust AI frameworks, PrismML, benchmarks, history | 35+ sources |
| Agent 2 | EchoKit, qwen3_tts_rs, Pulsar, "Rust for AGI" | 12+ sources |
| Agent 3 | Flutter ↔ Rust patterns, edge server architecture | 15+ sources |
| Agent 4 | AI-assisted Rust dev, Second State, open-source HW | 15+ sources |
| Agent 5 | Cross-reference & fact-checking | 20+ sources |
