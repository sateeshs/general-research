# Plnner and Reminder — Design Specification

**Date:** 2026-07-18
**Status:** Draft — Pending User Approval
**App Name:** Plnner and Reminder
**Tagline:** "Your personal AI companion that remembers, plans, and acts — all on your device."

---

## 1. Core Concept & Product Identity

### Value Proposition

A privacy-first mobile app with an AI companion character powered by Bonsai 27B (PrismML's 1-bit quantized Qwen3.6 27B). Automatically extracts Todos, Activities, and Notes from text, calendar, conversations, and screenshots — all on-device. Adapts its entire experience to 8 age groups. Premium agent skills unlock web search, ordering, and trip planning.

### Four Pillars

1. **Smart Extraction** — paste text, share from any app, or upload screenshots. AI identifies and categorizes actionable items.
2. **Age-Adaptive Experience** — UI, content, character personality, and voice adapt across 8 age groups (Toddler to Senior).
3. **Private by Design** — base app is fully offline. No cloud. No tracking. You own your data.
4. **Agent Skills (Premium)** — web search, knowledge updates, order placement & tracking, trip planning & optimization. Internet access only when user explicitly enables it.

### Two-Tier Model (Single Purchase)

| Feature | Base | Premium (one-time unlock) |
|---|---|---|
| AI extraction (text, calendar, screenshots) | Yes | Yes |
| AI companion character with memory | Yes | Yes |
| Age-adaptive UI & content | Yes | Yes |
| Voice-over reminders with scrolling text | Yes | Yes |
| Encrypted backup & caregiver sharing | Yes | Yes |
| Financial intelligence (grocery, bank, duplicate detection) | Yes | Yes |
| Web search & knowledge upgrade | -- | Yes |
| Order placement & tracking | -- | Yes |
| Trip planning & optimization | -- | Yes |
| Internet access | Never | User opt-in |

### Monetization

One-time purchase on App Store / Play Store. Web version free (lightweight companion — view/edit data, manage settings, no on-device AI).

---

## 2. Target Platforms

### Platform Matrix

| Platform | Framework | AI Model | Status |
|----------|-----------|----------|--------|
| Android (ARM64) | Flutter Mobile | Bonsai 27B 1-bit (3.9GB) | Launch |
| iOS (ARM64) | Flutter Mobile | Bonsai 27B 1-bit (3.9GB) | Launch |
| Web (Browser) | Flutter Web | Rule-based fallback (no on-device AI) | Launch |
| Windows (x64) | Flutter Desktop | Bonsai 27B ternary (5.9GB) | Launch |
| macOS (ARM64 / x64) | Flutter Desktop | Bonsai 27B ternary (5.9GB) | Launch |
| Linux (x64 / ARM64) | Flutter Desktop | Bonsai 27B ternary (5.9GB) | Launch |
| Smart TV / IoT (ARM) | Flutter Embedded (future) | Bonsai 27B 1-bit (3.9GB) | Future |
| Wearables (ARM) | Companion app (future) | Notification relay only | Future |

### Architecture Targets

Flutter compiles to native code per platform. Bonsai 27B via llama.cpp supports both architectures:

| Architecture | Bonsai Variant | Performance | Devices |
|---|---|---|---|
| **ARM64** | 1-bit (3.9GB) | ~11 tok/s on flagship phones, ~15 tok/s on M-series Macs | Phones, tablets, Apple Silicon Macs, Raspberry Pi 5, ARM laptops |
| **x64** | Ternary (5.9GB) | ~20-30 tok/s on modern desktop CPUs | Windows PCs, Intel/AMD Macs, Linux workstations |
| **ARM64 + GPU** | Ternary (5.9GB) | ~25-40 tok/s with Metal/Vulkan acceleration | Apple Silicon Macs, high-end Android tablets |
| **x64 + GPU** | Ternary (5.9GB) | ~30-50 tok/s with CUDA/Vulkan acceleration | Gaming PCs, workstations with discrete GPU |

### Platform-Specific Adaptations

```
PLATFORM ADAPTATION LAYER
│
├── Mobile (ARM64) — Primary
│   ├── Bonsai 1-bit (3.9GB) — optimized for memory-constrained devices
│   ├── Resource governor: CPU/RAM/battery limits
│   ├── Background processing limits (OS-enforced)
│   ├── Touch-first UI with gesture navigation
│   ├── Camera, Share Sheet, system TTS/STT
│   └── Push notifications (local)
│
├── Desktop (x64 / ARM64)
│   ├── Bonsai ternary (5.9GB) — higher accuracy (95% vs 90%)
│   ├── More RAM available → larger context windows, bigger feature store
│   ├── Keyboard + mouse UI adaptations
│   │   ├── Keyboard shortcuts for power users
│   │   ├── Resizable companion window (dockable sidebar or floating)
│   │   ├── Multi-window support (companion + main view)
│   │   └── System tray / menu bar presence
│   ├── File drag-and-drop for screenshots, receipts, bank statements
│   ├── Clipboard monitoring (opt-in): detect copied text for extraction
│   ├── Desktop notifications (system native)
│   └── Companion as desktop widget or overlay
│
├── Web (Browser) — Lightweight Companion
│   ├── No AI processing (Bonsai can't run in browser)
│   ├── Rule-based extraction (regex + keyword matching)
│   ├── View/edit todos, reminders, financial data
│   ├── Manage settings and companion preferences
│   ├── Data sync via encrypted file import/export
│   └── Responsive layout (works on any screen size)
│
├── Edge: Three-Tier Architecture (EchoKit-inspired)
│   ├── TIER 1: ESP32-S3 Voice Peripherals (embedded Rust firmware)
│   │   ├── Wake word detection (Zephyr RTOS + TFLite Micro, ~20KB model)
│   │   ├── Audio I/O (I2S MEMS mic + DAC speaker)
│   │   ├── WebSocket client → AI server
│   │   ├── Optional OLED/LCD for avatar expressions + scrolling text
│   │   └── ~$15-25 per unit, battery or USB-C powered
│   ├── TIER 2: Rust AI Server (SBC / Mini PC)
│   │   ├── ASR: whisper-rs (whisper.cpp Rust bindings, ~300ms for 5s audio)
│   │   ├── LLM: Bonsai 27B via llama.cpp-rs / candle
│   │   ├── TTS: qwen3_tts_rs (Qwen3 TTS, voice cloning, 8 age-group presets)
│   │   ├── Agent Core: skills, memory (HNSW), ranking (L1→L2), PID pacing
│   │   ├── Data: rusqlite + HNSW vector store
│   │   ├── WebSocket server (ESP32 peripherals)
│   │   └── REST/GraphQL API (Flutter clients + web)
│   └── TIER 3: Flutter Rich Clients (mobile, desktop, web, kiosk)
│       ├── Mobile: can run Bonsai on-device OR connect to Tier 2 server
│       ├── Desktop/Web/Kiosk: connect to Tier 2 server for full AI
│       └── All share REST API interface to Rust server
│
└── Future: Additional Smart Devices
    ├── Smart displays: companion avatar on screen, voice-first interaction
    ├── Wearables: notification relay + quick voice capture
    └── IoT hubs: central family dashboard for caregiver view

### Open-Source ARM & x64 Hardware Targets

The app runs anywhere Flutter + llama.cpp compile. Bonsai 27B via llama.cpp compiles natively for ARM64 and x64, enabling deployment on open-source single-board computers as dedicated home hubs or family stations.

#### Supported Hardware Matrix

| Device | Architecture | RAM | AI Capability | Bonsai Variant | Est. Performance | Use Case |
|--------|-------------|-----|---------------|----------------|-----------------|----------|
| **Raspberry Pi 5** (8GB) | ARM64 (Cortex-A76) | 8GB | CPU only | 1-bit (3.9GB) | ~3-5 tok/s | Home hub, family station, kiosk |
| **Raspberry Pi 5** (16GB) | ARM64 (Cortex-A76) | 16GB | CPU only | Ternary (5.9GB) | ~4-6 tok/s | Better accuracy home hub |
| **Orange Pi 5 Plus** | ARM64 (RK3588) | 16-32GB | 6 TOPS NPU | Ternary (5.9GB) | ~8-12 tok/s | Performance home hub |
| **Rockchip RK3588 boards** (Radxa Rock 5C, Kickpi K8) | ARM64 | 8-32GB | 6 TOPS NPU | Ternary (5.9GB) | ~8-12 tok/s | Edge AI station |
| **NVIDIA Jetson Orin Nano** | ARM64 | 8GB | 40 TOPS GPU | Ternary (5.9GB) | ~15-25 tok/s | High-performance edge device |
| **Intel NUC / Mini PC** | x64 | 16-32GB | CPU + optional GPU | Ternary (5.9GB) | ~20-30 tok/s | Desktop companion hub |
| **Old laptop/desktop** | x64 | 8GB+ | CPU | 1-bit (3.9GB) | ~10-20 tok/s | Repurposed hardware |

#### Deployment Modes for SBC/Edge Devices

```
DEPLOYMENT MODE SELECTION (at install time)
│
├── MODE 1: Standalone Hub (headless)
│   ├── Runs as a background service on SBC
│   ├── Web UI accessible from any device on local network
│   ├── Voice-first interaction via USB microphone + speaker
│   ├── Companion avatar on connected display (HDMI)
│   ├── Serves as family reminder station (kitchen, hallway)
│   └── Ideal for: Raspberry Pi with screen, Orange Pi kiosk
│
├── MODE 2: Desktop App (GUI)
│   ├── Full Flutter desktop app with companion sidebar
│   ├── Keyboard + mouse interaction
│   ├── System tray / menu bar integration
│   └── Ideal for: Linux desktop on SBC, Intel NUC, mini PC
│
├── MODE 3: Network Companion (future)
│   ├── SBC runs Bonsai inference as a local network service
│   ├── Mobile/web apps offload AI processing to SBC over LAN
│   ├── Keeps data on local network (never reaches internet)
│   ├── Solves the "web version has no AI" problem
│   └── Ideal for: Jetson Orin Nano as family AI server
│
└── MODE 4: Kiosk / Display Mode
    ├── Full-screen companion avatar
    ├── Always-listening mode with wake word
    ├── Scrolling reminder ticker on screen
    ├── Touch or voice interaction only
    └── Ideal for: Kitchen display, senior's bedside, kid's desk
```

#### SBC-Specific Considerations

- **Thermal management:** Active cooling required for sustained inference (Pi 5 throttles 20-30% without cooling)
- **Storage:** Minimum 16GB SD card / 32GB recommended. NVMe preferred for faster model loading on RK3588 boards
- **NPU acceleration:** RK3588 boards (Orange Pi 5 Plus, Rock 5C) can use RKNN-Toolkit2 for accelerated inference if model is converted to RKNN format
- **GPU acceleration:** Jetson Orin Nano uses CUDA, making it the fastest SBC option by far
- **Auto-start:** systemd service for headless mode, desktop autostart for GUI mode
- **Power:** Most SBCs run on 5V/3A USB-C — can be powered by a phone charger
```

#### ESP32-S3 Voice Peripherals (EchoKit-inspired)

Low-cost voice endpoints that connect to the Rust AI server over Wi-Fi WebSocket. No AI processing on the peripheral — all inference happens on Tier 2 server.

| Component | Spec | Cost |
|-----------|------|------|
| MCU | ESP32-S3 dual-core Xtensa LX7, 240MHz, 512KB SRAM | $5-8 |
| Microphone | I2S MEMS (INMP441 / MSM261) | $2-3 |
| Speaker | I2S DAC (MAX98357A) + small speaker | $3-5 |
| Display (opt) | OLED SSD1306 / LCD ST7789 for avatar + text | $3-5 |
| Buttons | Wake / SOS / Action | $1 |
| **Total per unit** | | **~$15-25** |

**Firmware stack:** Embedded Rust with esp-hal, Zephyr RTOS for wake word detection (TFLite Micro, ~20KB neural network model), I2S audio driver with Opus codec, WebSocket client, OTA firmware updates from server.

**Voice interaction latency budget:**

| Stage | Where | Budget |
|-------|-------|--------|
| Wake word detection | ESP32 (TFLite Micro) | <50ms |
| Audio capture + WebSocket send | ESP32 → Server | ~100ms |
| ASR (whisper-rs) | Server | <500ms |
| Input pipeline + skill routing | Server | <50ms |
| LLM inference (first token) | Server | <500ms |
| TTS (qwen3_tts_rs, streaming) | Server | ~200ms to first audio |
| WebSocket stream to ESP32 | Server → ESP32 | <50ms |
| **Total to first audio** | | **~1.0-1.5s** |

**Family deployment cost example:**

```
Rust AI Server (Pi 5 8GB):     $80
4x ESP32 Voice Peripherals:    $100
Touchscreen Kiosk (7" DSI):    $50
──────────────────────────────
Total:                         ~$230 (one-time, no subscriptions)
```

#### Rust AI Server Stack

The edge server is a pure Rust stack inspired by EchoKit's echokit_server architecture and the "Rust is the language of AGI" thesis. Rust provides memory safety without garbage collection, zero-cost abstractions, and native ARM64/x64 compilation — critical for real-time audio + LLM inference on constrained hardware.

```
RUST AI SERVER (runs on SBC)
│
├── Network Layer
│   ├── WebSocket server (tokio + tungstenite) — ESP32 peripheral connections
│   ├── REST API server (axum / actix-web) — Flutter client connections
│   └── mDNS discovery (avahi) — plnner-ai.local
│
├── AI Pipeline (all Rust-native)
│   ├── ASR: whisper-rs (Rust bindings to whisper.cpp)
│   │   └── small.en model, ~300ms for 5s audio
│   ├── LLM: Bonsai 27B via llama.cpp-rs or candle
│   │   └── Auto-selects 1-bit or ternary per device capability
│   └── TTS: qwen3_tts_rs (Qwen3 TTS in Rust)
│       ├── 0.6B CustomVoice model (voice cloning, 1.76x real-time)
│       ├── 1.7B model with style instructions (3.05x real-time)
│       ├── 9 preset voices, 8 mapped to age groups
│       ├── Voice cloning: caregiver records 30s sample → companion sounds like them
│       ├── Style instructions: urgent, gentle, excited, concerned
│       └── Multi-language: EN, ZH, JA, KO + auto-detect
│
├── Agent Core (Rust)
│   ├── Skill Router (Two-Tower ANN matching)
│   ├── Context Memory Manager (HNSW + rusqlite)
│   ├── Reminder Prioritization (L1→L2 + PID pacing)
│   ├── Engagement Prediction (lightweight DLRM)
│   └── User Behavior Feature Store
│
├── Skills Layer (Rust plugins)
│   ├── Base: Extraction, Calendar, Financial Intelligence
│   └── Premium: Web Search, Orders, Trip Planner
│
└── Data Layer
    ├── rusqlite (SQLite)
    ├── HNSW vector store (in-process)
    └── Encrypted backup (AES-256)
```

**Architecture split rationale:**

| Domain | Language | Why |
|--------|----------|-----|
| AI Server + Firmware | **Rust** | 7-10x faster inference, memory safety without GC, zero-cost abstractions, native ARM64/x64, real-time audio processing, WASM compilation |
| UI Clients | **Flutter** | Best cross-platform UI framework, rich animation (Skia), hot reload, single codebase for 6 platforms, widget ecosystem, accessibility built-in |

### Cross-Platform Data Sync

Data stays local per device. Cross-device transfer via encrypted backup files:

```
Device A                          Device B
   │                                 │
   ├── Export encrypted backup ──►  │
   │   (AES-256, user password)     ├── Import & decrypt
   │                                │
   │   Transfer via:                │
   │   ├── USB drive               │
   │   ├── AirDrop / Nearby Share  │
   │   ├── Cloud storage (manual)  │
   │   └── QR-code initiated       │
   │       local Wi-Fi transfer    │
```

### AI Model Selection (per device capability)

```
APP STARTUP
    │
    ├── Detect: architecture (ARM64 / x64)
    ├── Detect: available RAM
    ├── Detect: GPU availability (Metal / Vulkan / CUDA)
    ├── Detect: storage space
    │
    ├── IF ARM64 + RAM < 6GB → Bonsai 1-bit (3.9GB)
    ├── IF ARM64 + RAM >= 6GB → offer ternary upgrade (5.9GB)
    ├── IF x64 + RAM >= 8GB → Bonsai ternary (5.9GB) default
    ├── IF x64 + RAM < 8GB → Bonsai 1-bit (3.9GB) fallback
    ├── IF GPU detected → enable GPU acceleration layer
    └── IF storage < 5GB → prompt user to free space before model download
```

### AI Model Details

- **Bonsai 27B** (PrismML, Apache 2.0)
  - Base: Qwen3.6 27B, quantized to 1-bit (3.9GB) and ternary (5.9GB)
  - Multimodal: text + vision (screenshot OCR built-in)
  - 262K context window
  - Runs via llama.cpp (C/C++ backend, compiles for ARM64 and x64 natively)
  - Flutter bindings via FFI (Foreign Function Interface) to llama.cpp shared library
  - GPU acceleration: Metal (Apple), Vulkan (Android/Linux/Windows), CUDA (NVIDIA desktop)

---

## 3. Age Groups (8 Tiers)

| # | Group | Age | UI Characteristics | Content Focus |
|---|-------|-----|--------------------|---------------|
| 1 | Toddler | 2-5 | Large icons, bright colors, minimal text | Caregiver-managed only |
| 2 | Kids | 6-9 | Playful, illustrated, simple navigation | Homework, chores, practice, playdates |
| 3 | Tweens | 10-12 | Semi-structured, gamified elements | School, hobbies, responsibilities |
| 4 | Teens | 13-17 | Modern, minimal, social-app-familiar | School, social, hobbies, part-time work |
| 5 | Young Adults | 18-25 | Sleek, productivity-focused | College, career, lifestyle, budgeting |
| 6 | Adults | 26-45 | Professional, dense information | Work, family, health, finance, home |
| 7 | Middle Age | 46-64 | Clear, health-aware, balanced | Health, planning, family care, finance |
| 8 | Seniors | 65+ | Large text, high contrast, simplified | Medication, appointments, family, safety |

### Onboarding

1. **Face scan** — camera estimates age group using on-device ML
2. **8-section age menu** — user confirms or selects correct group
3. **DOB entry** — precise age tracking, auto-transitions between groups over time
4. **Caregiver setup mode** — for Toddlers, Kids, and Seniors, a caregiver can set up and configure the app

---

## 4. Input Sources

### A. Text Input (Base)
- User types or dictates free-form notes
- Bonsai auto-classifies as Todo / Activity / Note
- Priority and deadline inference from natural language

### B. Calendar & Contacts (Base)
- Reads device calendar events
- Suggests preparation tasks before events
- Detects scheduling conflicts
- Creates follow-up reminders after meetings
- Uses contact context ("Meeting with John" → knows John is your dentist)
- Birthday/anniversary reminders from contact data

### C. Conversations (Base)
- **Manual paste** — user copies conversation text, AI extracts tasks
- **Share sheet** — user shares text from any chat app (WhatsApp, iMessage, etc.) via OS share sheet
- **Screenshot upload** — user uploads conversation screenshots, Bonsai vision extracts action items via OCR

---

## 5. System Architecture

### High-Level Layer Diagram

```
PRESENTATION LAYER
    Age-Adaptive UI Shell (8 themes)
    AI Companion Avatar & Chat View
    Scrolling Text + Voice Reminders
        |
AGENT CORE
    Bonsai 27B Runtime
    Context Memory Manager
    Skill Router & Agent Orchestrator
        |
SKILLS LAYER
    Base Skills (offline)
    Premium Skills (internet, unlocked)
        |
DATA LAYER
    SQLite (drift ORM)
    Encrypted Backup Manager
    Age-Group Profile Store
        |
PLATFORM LAYER
    Camera & Face API | Share Sheet | TTS | STT | Notifications
```

### 5.0 ML-Inspired Architecture Patterns (from Meta Ad Auction & Airbnb Semantic Search Research)

The Agent Core and Skills Layer incorporate proven patterns from Meta's real-time ad auction system and Airbnb's semantic search architecture, adapted for on-device execution via Bonsai 27B.

#### Pattern 1: Two-Tower Architecture → Skill Router (Intent Matching)

Adapted from Meta's Two-Tower ANN candidate retrieval and Airbnb's query-listing matching.

```
┌──────────────────────┐    ┌──────────────────────┐
│    INPUT TOWER        │    │    SKILL TOWER        │
│                      │    │                      │
│  User text/voice     │    │  Skill capability    │
│  Screenshot content  │    │  descriptions        │
│  Shared content      │    │  Input type specs    │
│  Calendar context    │    │  Age-group support   │
│         │            │    │         │            │
│    ┌────▼────┐       │    │    ┌────▼────┐       │
│    │ Bonsai  │       │    │    │Precomp. │       │
│    │Encoder  │       │    │    │Skill    │       │
│    │(on-fly) │       │    │    │Embeddings│      │
│    └────┬────┘       │    │    └────┬────┘       │
│         │            │    │         │            │
│    128-dim vector    │    │    128-dim vector    │
└─────────┬────────────┘    └─────────┬────────────┘
          │         Dot Product        │
          └───────────┬────────────────┘
                      │
              ┌───────▼───────┐
              │  Top-K Skill  │
              │  Candidates   │
              │  (ranked)     │
              └───────────────┘
```

**How it works:**
- **Input Tower:** Encodes user input (text, OCR'd screenshot, shared content) into a 128-dim embedding at request time using Bonsai 27B
- **Skill Tower:** Each skill has a precomputed 128-dim embedding representing its capabilities, generated offline during app initialization
- **Matching:** Dot product between input and skill embeddings produces ranked skill candidates
- **Advantage over keyword matching:** Handles ambiguous inputs like "I spent too much on Uber this month" → routes to Financial Intelligence, not Trip Planner
- **Fallback:** Keyword matching for speed when input is unambiguous (e.g., explicit "set a reminder")

#### Pattern 2: Multi-Stage Ranking → Reminder Prioritization Pipeline

Adapted from Airbnb's Two-Stage Ranking (L1 Fast Ranker 2000→200, L2 Personalized Rerank 200→40).

```
ALL PENDING REMINDERS & ITEMS
          │
    ┌─────▼──────────────────────────────┐
    │  STAGE 1: L1 Fast Filter           │
    │  (Lightweight, <5ms)               │
    │                                    │
    │  • Due date proximity scoring      │
    │  • Priority level weighting        │
    │  • Category relevance              │
    │  • Overdue boost factor            │
    │  • Simple feature-based ranking    │
    │                                    │
    │  All items → Top 50 candidates     │
    └─────┬──────────────────────────────┘
          │
    ┌─────▼──────────────────────────────┐
    │  STAGE 2: L2 Personalized Rerank   │
    │  (Bonsai-powered, <20ms)           │
    │                                    │
    │  • User engagement history         │
    │    (does user act on this category?)│
    │  • Time-of-day preference          │
    │    (user responds to finance items  │
    │     in morning, social in evening)  │
    │  • Interaction recency             │
    │    (last time user engaged)        │
    │  • Contextual signals              │
    │    (just uploaded receipt →         │
    │     boost financial reminders)     │
    │  • Age-group relevance scoring     │
    │                                    │
    │  50 candidates → Top 5 to deliver  │
    └─────┬──────────────────────────────┘
          │
    ┌─────▼──────────────────────────────┐
    │  NOTIFICATION PACING CONTROLLER    │
    │  (PID-inspired, from Meta Budget   │
    │   Pacing)                          │
    │                                    │
    │  • Proportional: current reminder  │
    │    load vs. user tolerance         │
    │  • Integral: cumulative reminders  │
    │    delivered today vs. daily cap   │
    │  • Derivative: rate of reminder    │
    │    generation (spike detection)    │
    │                                    │
    │  Prevents notification fatigue by  │
    │  spacing deliveries like Meta      │
    │  paces ad budget spend             │
    │                                    │
    │  Age-adjusted caps:                │
    │    Kids: max 5/day                 │
    │    Teens: max 10/day               │
    │    Adults: max 15/day              │
    │    Seniors: max 8/day (gentle)     │
    └─────┬──────────────────────────────┘
          │
    DELIVER via Companion (voice + scroll)
```

#### Pattern 3: Query Understanding Service → Input Understanding Pipeline

Adapted from Airbnb's Query Understanding Service (structured query extraction from natural language).

```
RAW USER INPUT (text / voice / screenshot / share)
          │
    ┌─────▼──────────────────────────────┐
    │  STAGE 1: Input Normalization      │
    │  (<5ms)                            │
    │                                    │
    │  • Text: clean, normalize          │
    │  • Voice: STT → text              │
    │  • Screenshot: Bonsai Vision → text│
    │  • Share sheet: extract payload    │
    └─────┬──────────────────────────────┘
          │
    ┌─────▼──────────────────────────────┐
    │  STAGE 2: Entity Extraction        │
    │  (Bonsai NLP, <30ms)              │
    │                                    │
    │  Structured output:                │
    │  {                                 │
    │    "items": [                      │
    │      {                             │
    │        "text": "buy milk",         │
    │        "type": "todo",             │
    │        "priority": "medium",       │
    │        "deadline": "2026-07-19",   │
    │        "category": "grocery",      │
    │        "people": ["neighbor"],     │
    │        "amount": null,             │
    │        "recurrence": "weekly"      │
    │      }                             │
    │    ],                              │
    │    "financial_entities": [          │
    │      {                             │
    │        "item": "milk",             │
    │        "amount": 4.99,             │
    │        "merchant": "Walmart",      │
    │        "date": "2026-07-18"        │
    │      }                             │
    │    ],                              │
    │    "calendar_entities": [           │
    │      {                             │
    │        "event": "dentist",         │
    │        "date": "2026-07-20",       │
    │        "time": "14:00",            │
    │        "person": "Dr. Smith"       │
    │      }                             │
    │    ],                              │
    │    "confidence": 0.92              │
    │  }                                 │
    └─────┬──────────────────────────────┘
          │
    ┌─────▼──────────────────────────────┐
    │  STAGE 3: Skill Routing            │
    │  (Two-Tower match, <10ms)          │
    │                                    │
    │  Route entities to skills:         │
    │  • todo items → Extraction Skill   │
    │  • financial → Financial Intel     │
    │  • calendar → Calendar Skill       │
    │  • multi-skill → Agent Orchestrator│
    └─────────────────────────────────────┘
```

#### Pattern 4: DLRM → Companion Engagement Prediction

Adapted from Meta's DLRM (Deep Learning Recommendation Model) for predicting user engagement with ads. Applied to predict which reminder delivery style will get the best user response.

```
ENGAGEMENT PREDICTION MODEL (on-device, lightweight)
│
├── Input Features (per reminder):
│   ├── Categorical: age_group, category, priority, day_of_week
│   ├── Continuous: time_of_day, days_overdue, past_response_rate
│   ├── Interaction: user_category_affinity, time_preference_score
│   └── Contextual: recent_activity_type, device_state (locked/active)
│
├── Embedding Layer:
│   ├── age_group → 16-dim embedding
│   ├── category → 32-dim embedding
│   ├── day_of_week → 8-dim embedding
│   └── Combined with continuous features
│
├── Prediction Outputs:
│   ├── P(acknowledge) — will user tap/respond to this reminder?
│   ├── P(complete) — will user actually do the task?
│   ├── optimal_delivery_time — best time to deliver
│   └── delivery_style — voice emphasis, urgency tone, casual/formal
│
└── Training Data (on-device, privacy-preserving):
    ├── User's own interaction history only
    ├── Retrained weekly from local data
    └── No data shared across devices
```

#### Pattern 5: Semantic Search + Embeddings → Context Memory Retrieval

Adapted from Airbnb's BERT-based semantic search with ANN indexing. Powers the companion's ability to recall relevant memories.

```
CONTEXT MEMORY RETRIEVAL (Local RAG)
│
├── Embedding Store (SQLite + on-device vector index)
│   ├── Episodic memories → 128-dim embeddings
│   ├── Purchase history → 128-dim embeddings
│   ├── Conversation summaries → 128-dim embeddings
│   ├── Knowledge nodes (premium) → 128-dim embeddings
│   └── ANN index (HNSW) for fast similarity search
│
├── Query Flow:
│   1. User says: "What did I buy at Walmart last week?"
│   2. Bonsai encodes query → 128-dim vector
│   3. HNSW ANN search over purchase embeddings
│   4. Top-K results retrieved (<10ms)
│   5. Bonsai generates natural language response from results
│
├── Hybrid Retrieval (inspired by Airbnb's fusion approach):
│   ├── Semantic similarity: cosine(query_emb, memory_emb) × 0.6
│   ├── Recency score: decay_function(days_ago) × 0.25
│   ├── Relevance boost: category_match_score × 0.15
│   └── Final score = weighted combination
│
└── Memory Lifecycle:
    ├── New memories embedded on creation
    ├── Index rebuilt nightly (background, low-battery aware)
    ├── Decay scoring prevents unbounded growth
    └── User can pin important memories (exempt from decay)
```

#### Pattern 6: Geospatial Service → Location-Aware Intelligence

Adapted from Airbnb's Elasticsearch-based geospatial service. Powers Trip Planner and location-based reminders.

```
GEOSPATIAL ENGINE (Premium Skill)
│
├── Local Spatial Index (SQLite R-Tree extension)
│   ├── Saved locations (home, work, gym, stores)
│   ├── Frequently visited places (learned from history)
│   └── Trip waypoints and POIs
│
├── Route Optimization (adapted from geospatial query patterns)
│   ├── Multi-stop errand routing:
│   │   Input: [grocery_store, pharmacy, post_office, home]
│   │   Process:
│   │     1. Geocode all destinations
│   │     2. Build distance matrix (on-device or via API)
│   │     3. TSP solver (nearest-neighbor heuristic for speed)
│   │     4. Return optimized route with time estimates
│   │
│   ├── Location-triggered reminders:
│   │   • Geofencing via device location services
│   │   • "Remind me to buy milk when near Walmart"
│   │   • Spatial query: items WHERE geo_distance(user, store) < 500m
│   │
│   └── Trip itinerary spatial planning:
│       • Cluster activities by geographic proximity
│       • Minimize travel time between daily activities
│       • Integrate with Maps API for real-time routing
│
└── Caching Strategy (from Airbnb research):
    ├── Frequently queried locations cached in-memory
    ├── Route calculations cached with TTL (stale after traffic changes)
    └── POI data cached locally for offline access
```

#### Pattern 7: Feature Store → User Behavior Feature Store

Adapted from Meta/Airbnb's feature engineering and precomputation pipelines. Runs entirely on-device.

```
USER BEHAVIOR FEATURE STORE (SQLite)
│
├── Precomputed Features (updated nightly):
│   ├── spending_pattern_weekly — avg spend per category per week
│   ├── reminder_response_rate — % of reminders acknowledged per category
│   ├── peak_activity_hours — when user is most responsive (histogram)
│   ├── category_affinity_scores — which categories user engages with most
│   ├── purchase_frequency — per-item purchase cycle (e.g., milk every 5 days)
│   ├── waste_risk_score — items frequently bought but not consumed
│   ├── companion_interaction_depth — avg conversation turns per session
│   └── task_completion_rate — % of todos marked complete per category
│
├── Real-Time Features (computed on each interaction):
│   ├── time_since_last_interaction
│   ├── current_pending_reminder_count
│   ├── today_notification_count (for PID pacing)
│   ├── active_context_category (what user was just doing)
│   └── device_state (battery, connectivity, screen state)
│
├── Age-Group Aggregate Features:
│   ├── Default baselines per age group (bootstrapping new users)
│   ├── Gradually overridden by user's actual behavior
│   └── Cold-start mitigation: use age-group defaults until 50+ interactions
│
└── Feature Access Pattern:
    ├── Skills query feature store for personalized behavior
    ├── Reminder ranker uses features for L2 personalized rerank
    ├── Companion uses features to adapt conversation style
    └── Financial Intelligence uses features for spending alerts
```

### 5.1 Presentation Layer

#### Age-Adaptive UI Shell
- **ThemeEngine** — 8 theme profiles controlling colors, fonts, spacing, icon style, animation level
- **NavigationAdapter** — adjusts navigation complexity per age group
  - Toddler/Kids: bottom tab with 2-3 large icons
  - Teens/Young Adults: bottom tab with 4-5 tabs
  - Adults/Seniors: configurable drawer + bottom tab
- **ContentFilter** — shows/hides features by age appropriateness

#### AI Companion View
- **AvatarRenderer** — animated character with expressions
  - Default characters per age group (e.g., friendly animal for kids, professional assistant for adults)
  - Customization system: face, colors, accessories, voice style
  - Emotion states: happy, thinking, concerned, celebrating
- **ChatInterface** — conversation with the companion
  - Voice input (STT) → Bonsai processing → Voice output (TTS)
  - Text input as fallback
  - Context-aware responses using Memory Manager
- **PersonalityEngine**
  - Age-appropriate speaking style and vocabulary
  - Evolving personality traits based on interactions over time
  - Relationship memory (remembers user preferences, jokes, tone)

#### Reminder Delivery
- **ScrollingTextOverlay** — ticker-style text on screen
- **VoiceOverController** — companion speaks the reminder in character
- **InteractionHandler** — listens for user response via STT
- **ContextUpdater** — updates reminder state based on user response and saves for next notification

### 5.2 Agent Core

#### Bonsai 27B Runtime
- **ModelLoader**
  - Progressive download with resume capability
  - Model integrity verification (SHA-256)
  - Storage management (check space, cleanup old versions)
- **InferenceEngine** — runs model via llama.cpp / mlc-llm bindings
  - Text processing pipeline
  - Vision pipeline (screenshot OCR, receipt scanning)
  - Token streaming for real-time responses
  - Resource governor (CPU/RAM/battery limits per device tier)
- **PromptManager**
  - System prompts per age group and personality
  - Skill-specific prompt templates
  - Context window management (262K tokens)

#### Context Memory Manager (with Semantic Search — see Pattern 5 in Section 5.0)
- **ShortTermMemory** — current conversation context
- **LongTermMemory** — user preferences, past interactions, learned patterns
  - Stored in SQLite, indexed for retrieval
  - Companion personality evolution log
  - User behavior patterns (when they check reminders, response habits)
- **EpisodicMemory** — specific past events the companion remembers
  - E.g., "Last time you forgot your groceries on Thursday"
  - "You usually go to the gym on Mondays"
  - Decay/relevance scoring to prevent unbounded growth
  - Each memory stored with 128-dim Bonsai embedding for semantic search
- **ContextRetriever** — Local RAG with hybrid retrieval (adapted from Airbnb semantic search)
  - **HNSW ANN Index** — approximate nearest neighbor search over memory embeddings (<10ms)
  - **Hybrid scoring** (adapted from Airbnb's BM25 + semantic fusion):
    - Semantic similarity: cosine(query_emb, memory_emb) × 0.6
    - Recency score: decay_function(days_ago) × 0.25
    - Relevance boost: category_match_score × 0.15
  - Index rebuilt nightly (background, battery-aware)
  - User can pin important memories (exempt from decay)

#### Skill Router & Agent Orchestrator
- **SkillRegistry** — discovers and manages available skills
  - Base skills (always available, offline)
  - Premium skills (unlocked via purchase, require internet)
  - Skill capability declarations (inputs, outputs, permissions)
- **IntentClassifier** — Two-Tower architecture (see Pattern 1 in Section 5.0)
  - Input Tower: Bonsai encodes user input into 128-dim vector
  - Skill Tower: Precomputed skill embeddings (generated at app init)
  - Dot product matching for ranked skill candidates
  - Falls back to keyword matching for unambiguous inputs
  - Multi-skill orchestration for complex requests
- **AgentLoop** (ReAct pattern)
  - Reason: analyze user request + context
  - Act: invoke appropriate skill
  - Observe: evaluate skill output
  - Loop or respond to user
- **PermissionGate**
  - Checks internet permission before premium skills
  - Checks caregiver permissions for dependent accounts
  - Age-appropriate skill filtering

#### Input Understanding Pipeline (adapted from Airbnb Query Understanding — see Pattern 3)
- **InputNormalizer** — unifies all input types to text (<5ms)
  - Text passthrough, STT transcription, Bonsai Vision OCR, share sheet extraction
- **EntityExtractor** — Bonsai NLP structured extraction (<30ms)
  - Outputs: items (todos/activities/notes), financial entities, calendar entities, people
  - Confidence scoring per extraction
- **SkillDispatcher** — routes extracted entities to appropriate skills via Two-Tower match (<10ms)

#### Reminder Prioritization Engine (adapted from Airbnb Two-Stage Ranking — see Pattern 2)
- **L1 Fast Filter** — lightweight scoring, all reminders → top 50 (<5ms)
  - Due date proximity, priority level, overdue boost, category relevance
- **L2 Personalized Rerank** — Bonsai-powered, top 50 → top 5 (<20ms)
  - User engagement history, time-of-day preference, contextual signals
  - Queries User Behavior Feature Store for personalized features
- **NotificationPacingController** — PID-inspired (from Meta Budget Pacing — see Pattern 2)
  - Proportional/Integral/Derivative control on notification frequency
  - Age-adjusted daily caps (Kids: 5, Teens: 10, Adults: 15, Seniors: 8)

#### Engagement Prediction Model (adapted from Meta DLRM — see Pattern 4)
- Lightweight on-device model predicting P(acknowledge), P(complete), optimal delivery time
- Trained on user's own interaction history (privacy-preserving)
- Retrained weekly from local data
- Powers companion delivery style adaptation

#### User Behavior Feature Store (adapted from Meta/Airbnb Feature Pipelines — see Pattern 7)
- **Precomputed features** — updated nightly in background
  - spending_pattern_weekly, reminder_response_rate, peak_activity_hours, category_affinity_scores, purchase_frequency, waste_risk_score
- **Real-time features** — computed per interaction
  - time_since_last_interaction, pending_reminder_count, today_notification_count, device_state
- **Cold-start mitigation** — age-group default baselines until 50+ interactions

#### Latency Budget (End-to-End Input Processing)

| Stage | Budget | Description |
|-------|--------|-------------|
| Input Normalization | <5ms | Text cleanup, STT, OCR routing |
| Entity Extraction (Bonsai NLP) | <30ms | Structured entity extraction |
| Two-Tower Skill Matching | <10ms | Intent → skill routing |
| Skill Execution | <50ms | Skill-specific processing |
| Memory Retrieval (ANN search) | <10ms | Context retrieval from episodic memory |
| Companion Response Generation | <200ms | Bonsai generates natural language response |
| **Total P95** | **<305ms** | **End-to-end from input to companion response** |

### 5.3 Skills Layer (Plugin Architecture)

#### Skill Interface

All skills implement a common interface:
- `name`, `description`, `icon`
- `tier`: base | premium
- `requiresInternet`: bool
- `supportedAgeGroups`: List of age groups
- `inputTypes`: List of input types (text, image, file, calendar, etc.)
- `execute(context, input)` → SkillResult
- `getPromptTemplate()` → String

#### Base Skills (Offline, Included)

**1. Extraction & Reminder Skill**
- TextExtractor — NLP extraction from pasted/shared text
  - Todo detection ("need to", "must", "don't forget")
  - Activity detection (events, meetings, appointments)
  - Note detection (observations, ideas, references)
  - Priority & deadline inference
- ScreenshotExtractor — vision-based OCR extraction
  - Chat screenshot → action items
  - Receipt screenshot → purchase record
  - Document screenshot → notes/todos
  - Multi-language support
- ReminderScheduler
  - Smart timing based on user patterns
  - Recurring reminder support
  - Escalation rules (gentle → persistent → caregiver)
  - Age-appropriate reminder framing
- CategoryManager
  - Age-specific default categories per group
  - User-custom categories

**2. Calendar & Contacts Skill**
- CalendarScanner — reads device calendar events
  - Suggests preparation tasks before events
  - Detects scheduling conflicts
  - Creates follow-up reminders after meetings
- ContactContextualizer — uses contacts for context
  - "Meeting with John" → knows John is your dentist
  - Birthday/anniversary reminders from contact data

**3. Financial Intelligence Skill**
- GroceryListManager
  - Upload grocery list (photo/text) → structured list
  - Track purchased vs. pending items
  - Suggest recurring grocery items based on patterns
  - Price comparison memory (track price trends)
- BankStatementAnalyzer
  - Upload statement (photo/PDF/text) → parsed transactions
  - Auto-categorize spending (food, transport, bills, etc.)
  - Monthly spending summaries and trends
  - All processing on-device — bank data never leaves phone
- DuplicatePurchaseDetector
  - Cross-references new purchases against purchase history
  - Alerts: "You bought olive oil 3 days ago, still need more?"
  - Detects subscription overlaps
  - Identifies wasteful patterns ("You've thrown away X 3 times")
- WastePreventionAdvisor
  - Tracks expiry-prone purchases (groceries, subscriptions)
  - Reminds before items expire or go to waste
  - Monthly waste report with savings suggestions
  - Age-appropriate advice framing

#### Premium Skills (Internet Required, Unlocked via Purchase)

**4. Web Search & Browse Skill**
- SearchAgent — queries web for information
- ContentSummarizer — Bonsai summarizes results locally
- FactVerifier — cross-references multiple sources
- SafeSearch — age-appropriate content filtering

**5. Knowledge Upgrade Skill**
- TopicLearner — user asks to learn about a topic
- LocalKnowledgeStore — saves learned info to SQLite
- KnowledgeGraph — connects related knowledge nodes
- QuizGenerator — generates review quizzes (great for kids/students)

**6. Orders & Tracking Skill**
- ProductSearchAgent — searches products across retailers
- PriceComparator — compares prices from multiple sources
- OrderPlacer — places orders via retailer APIs/deep links
  - Amazon, grocery delivery, food delivery APIs
  - Confirmation capture and storage
  - Parental approval gate for kids/teens
- OrderTracker
  - Extracts tracking info from confirmation emails/screenshots
  - Polls tracking APIs for delivery status
  - Delivery reminders ("Your package arrives today")
  - Integrates with Financial Intelligence for spend tracking

**7. Trip Planner & Optimizer Skill** (with Geospatial Engine — see Pattern 6 in Section 5.0)
- ItineraryBuilder
  - Search flights, hotels, activities via APIs
  - Day-by-day plan generation
  - Budget tracking per trip
  - Age-appropriate activity suggestions
  - Spatial clustering of activities by geographic proximity (minimize travel time)
- RouteOptimizer (adapted from Airbnb Geospatial Service)
  - Local spatial index via SQLite R-Tree extension
  - Multi-stop errand routing (TSP nearest-neighbor heuristic)
  - Daily commute suggestions
  - Real-time traffic awareness via Maps API
  - Walking/transit/driving mode selection
  - Cached route calculations with TTL for traffic freshness
- LocationReminders (geofencing)
  - Saved locations (home, work, stores) in R-Tree index
  - Geofence triggers: "Remind me to buy milk when near Walmart"
  - Spatial query: items WHERE geo_distance(user, location) < threshold
  - Frequently visited places learned from history
- TripMemory
  - Saves past trip data with 128-dim embeddings for semantic recall
  - "Last time in Paris you liked X restaurant" via ANN search
  - Packing list generator based on destination + age
  - POI data cached locally for offline access

### 5.4 Data Layer

#### SQLite Database (via drift ORM)

**Core Tables:**
- `users` — profile, DOB, age_group, preferences
- `items` — todos, activities, notes (type, status, priority, due_date)
- `reminders` — scheduled reminders linked to items
- `categories` — age-specific + custom categories
- `extractions` — raw input → extracted items audit trail

**Companion Tables:**
- `companion_profile` — name, avatar config, personality traits
- `companion_memory` — episodic memories, relationship context
- `conversations` — chat history with the companion
- `personality_evolution` — trait changes over time

**Financial Tables:**
- `purchases` — all tracked purchases with amounts, dates
- `grocery_lists` — lists with item status
- `bank_transactions` — parsed statement data
- `spending_categories` — categorized spend summaries

**Premium Tables:**
- `orders` — placed orders with tracking info
- `trips` — itineraries, bookings, routes
- `knowledge_nodes` — learned information graph
- `web_cache` — cached search results

**ML & Vector Tables (from Research Patterns):**
- `embeddings` — 128-dim vectors for memories, purchases, knowledge nodes (ANN-indexed via HNSW)
- `user_features` — precomputed behavior features (updated nightly by Feature Store)
- `engagement_log` — reminder interaction history for DLRM-style engagement model training
- `skill_embeddings` — precomputed skill capability vectors for Two-Tower matching
- `spatial_index` — R-Tree indexed locations for geofencing and route optimization
- `notification_pacing_state` — PID controller state (proportional, integral, derivative values)

**System Tables:**
- `skills_registry` — installed skills and their state
- `permissions` — age-group and caregiver permissions
- `sync_log` — backup/restore tracking

#### Encrypted Backup Manager
- AES-256 encryption for all exports
- Export to file → user saves to Drive/iCloud manually
- Import with integrity verification
- Selective backup (choose what to include)

#### Age-Group Profile Store
- UI theme configuration per group
- Content category mappings
- Companion personality templates
- Permission and restriction rules

### 5.5 Platform Layer

- **Camera & Face API** — face detection for age estimation via google_mlkit_face_detection (~10MB model)
- **Share Sheet API** — receive_sharing_intent package, accepts text/images/files, routes to appropriate Skill
- **TTS Engine** — flutter_tts (system voices), speed/pitch per age group, companion character persona
- **STT Engine** — speech_to_text (on-device), voice commands, conversation capture
- **Notifications** — flutter_local_notifications, scheduled local notifications, custom sounds per age group, full-screen reminder overlay

---

## 6. Data Flow Example

### Grocery Receipt Upload

```
User uploads grocery receipt screenshot
    |
PLATFORM: Camera/Gallery API picks image
    |
AGENT CORE: Skill Router detects → Financial Intelligence Skill
    |
BONSAI VISION: OCR extracts items + prices from receipt image
    |
FINANCIAL INTELLIGENCE SKILL:
    ├── Parses items into grocery_list + purchases tables
    ├── DuplicatePurchaseDetector: "You bought milk 2 days ago"
    ├── WastePreventionAdvisor: "Bananas from last week — eaten?"
    └── CategoryManager: auto-categorizes spending
    |
CONTEXT MEMORY: Updates user spending patterns
    |
COMPANION: Avatar appears with scrolling text + voice:
    "Hey! I noticed you bought milk again — you got some on
     Tuesday. Also, those bananas from last week — did you
     finish them? I don't want them going to waste!"
    |
USER RESPONDS: "Oh yeah, the milk is for my neighbor"
    |
BONSAI: Understands context, updates memory
    └── Companion: "Got it! I'll remember that. Should I add
        'deliver milk to neighbor' to your todos?"
    |
DATA LAYER: Saves updated context, todo, purchase justification
```

---

## 7. Caregiver & Family Features

- **Caregiver Setup Mode** — for Toddlers, Kids, and Seniors
  - Caregiver sets up the app on the dependent's device
  - Configures permissions, character, content categories
  - Sets escalation rules (if reminder not acknowledged → notify caregiver)
- **Caregiver Dashboard** — view dependent's reminders, todos, and activity summaries
- **Parental Approval Gate** — required for premium skills (ordering, web search) on kids/teen accounts
- **Encrypted Sharing** — caregiver can view data via encrypted export, not cloud sync

---

## 8. Web Version (Free Companion)

- View and edit todos, activities, notes
- Manage settings and companion preferences
- No AI processing (Bonsai doesn't run in browser)
- Lightweight rule-based extraction (regex + keyword matching) as fallback
- Data sync via encrypted file import/export (not live sync)

---

## 9. Key Technical Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Framework | Flutter (Mobile + Desktop + Web) | Single codebase for Android, iOS, Windows, macOS, Linux, Web |
| AI Model | Bonsai 27B (1-bit 3.9GB / ternary 5.9GB) | Multimodal, on-device, Apache 2.0, auto-selects variant per device capability |
| AI Runtime | llama.cpp via FFI | Native ARM64 + x64 compilation, GPU accel (Metal/Vulkan/CUDA), proven performance |
| Database | SQLite via drift | Type-safe, reactive queries, offline-first, works on all Flutter platforms |
| Vector Index | HNSW (in-process) | ANN search for semantic memory retrieval, no external dependency |
| Spatial Index | SQLite R-Tree extension | Geofencing, route optimization, built into SQLite |
| Face Detection | google_mlkit_face_detection (mobile) / camera + ML model (desktop) | On-device, platform-adaptive |
| TTS (Mobile) | flutter_tts (system voices) | Free, offline, per-platform voice selection |
| TTS (Edge Server) | qwen3_tts_rs (Qwen3 TTS in Rust) | Voice cloning, 8 age-group presets, style instructions, 1.76x real-time, Apache 2.0 |
| ASR (Edge Server) | whisper-rs (whisper.cpp Rust bindings) | On-device speech recognition, ~300ms for 5s audio, no cloud |
| STT (Mobile) | speech_to_text | On-device recognition, no cloud dependency |
| Edge Server | Rust (tokio + axum + llama.cpp-rs) | Memory safety, zero-cost abstractions, real-time audio + LLM on constrained SBC hardware |
| Voice Peripheral | ESP32-S3 + embedded Rust + Zephyr RTOS | ~$15-25/unit, TFLite Micro wake word, WebSocket to server, privacy-preserving |
| Encryption | AES-256 | Industry standard for local backup encryption |
| Architecture Pattern | Clean Architecture + Skills Plugin + Platform Adaptation Layer | Separation of concerns, extensible skills, platform-specific adaptations |
| State Management | Riverpod or Bloc | Mature Flutter state management with reactive patterns |
| Target Architectures | ARM64 (mobile, Apple Silicon, embedded) + x64 (Windows, Linux, Intel Mac) | llama.cpp compiles natively for both |

---

## 10. Privacy & Security

- All base AI processing happens on-device via Bonsai 27B
- No telemetry, analytics, or tracking in base app
- Bank statements and financial data never leave the device
- Premium internet features require explicit user opt-in
- Caregiver access via encrypted file sharing, not cloud
- Face scan data processed locally, never stored or transmitted
- AES-256 encrypted backups
- No user accounts required for base functionality

---

## 11. Open Questions

1. What specific retailer APIs should the Orders & Tracking skill support at launch?
2. Should the Trip Planner integrate with specific booking platforms (Booking.com, Expedia, etc.)?
3. What voice persona options should ship as defaults for each age group?
4. Should the web version support importing data from competing todo/reminder apps?
5. What is the target price point for base and premium tiers?

---

## 12. Architectural Pattern Mapping Summary

| Source Pattern | Source System | Application in Plnner & Reminder | Component |
|---|---|---|---|
| Two-Tower ANN | Meta Ad Auction & Airbnb Retrieval | Input Tower + Skill Tower for intent matching | Skill Router |
| Multi-Stage Ranking (L1→L2) | Airbnb Ranking Service | L1 fast filter + L2 personalized rerank of reminders | Reminder Prioritization |
| PID Budget Pacing | Meta Ad Auction | Notification frequency pacing to prevent fatigue | Notification Pacing Controller |
| Query Understanding Service | Airbnb Semantic Search | Input normalization → entity extraction → routing | Input Understanding Pipeline |
| DLRM | Meta Ad Auction | Predict user engagement per reminder, optimize delivery | Companion Engagement Prediction |
| BERT Semantic Search + ANN | Airbnb Semantic Search | Embedding-based memory retrieval (local RAG) | Context Memory Retrieval |
| Geospatial Service | Airbnb Semantic Search | R-Tree spatial index, route optimization, geofencing | Trip Planner & Location Reminders |
| Feature Store & Precomputation | Meta/Airbnb Data Pipeline | User behavior features precomputed nightly for fast inference | User Behavior Feature Store |
| Hybrid Retrieval (BM25 + semantic) | Airbnb Semantic Search | Weighted fusion of semantic similarity + recency + relevance | Memory Retrieval Scoring |
| Model Quantization & Distillation | Meta/Airbnb Serving | Bonsai 27B is already 1-bit quantized; lightweight feature models further distilled | On-Device Performance |

---

## 13. Research Sources

### Internal Research (Meta Ad Auction & Airbnb Semantic Search)
- `reserch-topics/system-design/meta-ad-auction-system.md` — Two-Tower ANN, DLRM, PID Budget Pacing
- `reserch-topics/system-design/system-design.md` — End-to-end semantic search pipeline
- `reserch-topics/system-design/ranking-service.md` — Two-stage ranking (L1/L2) with LightGBM
- `reserch-topics/system-design/semantic-search-service.md` — BERT encoders, similarity scoring, personalization
- `reserch-topics/system-design/query-understanding-service.md` — Transformer NLP, entity extraction, structured query output
- `reserch-topics/system-design/geospatial-service/README.md` — Elasticsearch spatial indexing, caching strategies
- `reserch-topics/system-design/airbnb-semantic-search.md` — Full system overview with latency budgets
- `reserch-topics/system-design/research-details.md` — Implementation details, data pipelines

### Edge Architecture Research (EchoKit, Rust AI, Zephyr RTOS)
- [EchoKit 30 Days: ChatGPT Integration](https://echokit.dev/docs/dev/echokit-30-days-day-9-chatgpt/) — ESP32-S3 voice peripheral client-server pattern
- [echokit_server (GitHub)](https://github.com/second-state/echokit_server) — Rust AI server for EchoKit devices (WebSocket + whisper + LLM + TTS)
- [qwen3_tts_rs (GitHub)](https://github.com/second-state/qwen3_tts_rs) — Qwen3 TTS in Rust, voice cloning, 0.6B/1.7B models, Apache 2.0
- [Zephyr RTOS TFLite Micro](https://docs.zephyrproject.org/latest/samples/modules/tflite-micro/hello_world/README.html) — Wake word detection on ESP32 with ~20KB neural network
- [Rust is the language of AGI](https://x.com/juntao/status/2016602181474882045) — Thesis on Rust for AI infrastructure
- [Why Rust for AI/ML Engineers](https://github.com/Paulescu/why-rust) — ~100x faster than Python (0.3s vs 36.7s benchmark), powers Polars + tokenizers, ideal for feature engineering, training, and inference on constrained hardware

### External Research

- [PrismML Releases Bonsai 27B](https://www.marktechpost.com/2026/07/14/prismml-releases-bonsai-27b-1-bit-and-ternary-builds-of-qwen3-6-27b-that-run-on-laptops-and-phones/)
- [What Is Bonsai 27B?](https://kie.ai/blog/what-is-bonsai-27b)
- [Bonsai 27B: First 27B AI Model on a Phone](https://aijourn.com/prismml-announces-1-bit-bonsai-27b-the-first-27b-model-to-run-on-a-phone/)
- [Flutter + On-Device AI: Running Small LLMs 2026](https://thejenildgohel.medium.com/flutter-on-device-ai-running-small-llms-without-a-cloud-backend-2026-edition-4fbd568b585f)
- [Building Agentic Apps with Flutter](https://flutternest.com/blog/agentic-apps-with-flutter)
- [Flutter AI Agents: Building Autonomous Workflows](https://flutterexperts.com/flutter-ai-agents-building-autonomous-workflows-in-mobile-apps-with-code-samples/)
- [On-Device SLMs: 2026 Guide to Gemini Nano](https://devin-rosario.medium.com/implementing-on-device-slms-a-2026-guide-to-gemini-nano-911da096a471)
- [Small Language Models: Comprehensive Guide 2026](https://cogitx.ai/blog/small-language-models-slms-comprehensive-guide-2026)
- [On-Device AI: Complete Guide 2026](https://www.f22labs.com/blogs/what-is-on-device-ai-a-complete-guide/)
- [On-Device LLMs: Keep App Intelligence Local](https://www.dogtownmedia.com/on-device-llms-why-your-mobile-apps-intelligence-should-stay-in-the-users-pocket-not-the-cloud/)
- [Offline-First Flutter App With SQLite](https://gtstu.com/offline-first-flutter-app-sqlite/)
- [Building Offline-First React Native Apps 2026](https://reactnativerelay.com/article/building-offline-first-react-native-apps-2026-expo-sqlite-drizzle-orm-sync-strategies)
- [Best AI To-Do List Apps 2026](https://www.saner.ai/blogs/best-ai-to-do-list)
- [Senior-Friendly Reminder Apps 2026](https://memoryboard.com/blogs/news/the-best-senior-friendly-reminder-apps-to-stay-organized-and-connected-2026)
- [Mobile App Development Trends 2026](https://saigontechnology.com/blog/mobile-app-development-trends/)
- [AI Personal Finance Apps 2026](https://www.smallworldfs.com/blog/2026/03/24/personal-finance-apps-now-use-ai-to-track-spending-savings-and-bills/)
- [Best Grocery Tracking Apps 2026](https://grocerytrack.food/blog/best-grocery-tracking-apps-2026)
