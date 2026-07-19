# EchoKit-Inspired Rust Edge Architecture

## Overview

Inspired by EchoKit (second-state), qwen3_tts_rs, and the Rust AI infrastructure thesis.
The edge deployment evolves from a monolithic Flutter app into a **client-server split**:
lightweight voice peripherals (ESP32) + powerful Rust AI server on SBC.

## Three-Tier Edge Architecture

```mermaid
graph TB
    subgraph TIER1["TIER 1: VOICE PERIPHERALS (ESP32-S3)"]
        direction LR
        KITCHEN_DEV["Kitchen EchoKit<br/>ESP32-S3<br/>Mic + Speaker + OLED"]
        BEDROOM_DEV["Bedroom EchoKit<br/>ESP32-S3<br/>Mic + Speaker"]
        DESK_DEV["Kid's Desk EchoKit<br/>ESP32-S3<br/>Mic + Speaker + Button"]
        SENIOR_DEV["Senior's Bedside<br/>ESP32-S3<br/>Mic + Speaker + SOS btn"]
    end

    subgraph TIER2["TIER 2: AI SERVER (SBC / Mini PC)"]
        direction TB
        subgraph RUST_SERVER["RUST AI SERVER (echokit_server pattern)"]
            WS["WebSocket Server<br/>(device connections)"]
            REST["REST/GraphQL API<br/>(mobile/web clients)"]

            subgraph PIPELINE["AI PIPELINE (all Rust-native)"]
                ASR["ASR Engine<br/>whisper.cpp / whisper-rs<br/>on-device speech recognition"]
                LLM_ENGINE["LLM Engine<br/>Bonsai 27B via<br/>llama.cpp-rs / candle"]
                TTS_ENGINE["TTS Engine<br/>qwen3_tts_rs<br/>0.6B model<br/>voice cloning for companion"]
            end

            subgraph AGENT["AGENT CORE (Rust)"]
                SKILL_ROUTER["Skill Router<br/>(Two-Tower)"]
                MEMORY_MGR["Context Memory<br/>(HNSW + SQLite)"]
                REMINDER_ENGINE["Reminder<br/>Prioritization<br/>(L1→L2 + PID)"]
                FEATURE_STORE["User Behavior<br/>Feature Store"]
            end

            subgraph SKILLS_R["SKILLS (Rust plugins)"]
                SK_EXTRACT["Extraction &<br/>Reminder"]
                SK_FINANCE["Financial<br/>Intelligence"]
                SK_CALENDAR["Calendar &<br/>Contacts"]
                SK_SEARCH["Web Search<br/>(premium)"]
                SK_ORDERS["Orders &<br/>Tracking (premium)"]
                SK_TRIP["Trip Planner<br/>(premium)"]
            end
        end

        subgraph DATA_R["DATA LAYER"]
            SQLITE["SQLite<br/>(rusqlite)"]
            VECTORS["Vector Store<br/>(HNSW)"]
            BACKUP_R["Encrypted<br/>Backup (AES-256)"]
        end
    end

    subgraph TIER3["TIER 3: RICH CLIENTS"]
        direction LR
        FLUTTER_MOBILE["Flutter Mobile App<br/>(Android/iOS)<br/>Can run Bonsai on-device<br/>OR connect to server"]
        FLUTTER_DESKTOP["Flutter Desktop<br/>(Win/Mac/Linux)<br/>Full GUI companion"]
        WEB_APP["Web App<br/>(Flutter Web)<br/>Full AI via server API"]
        TOUCH_KIOSK["Touchscreen Kiosk<br/>(Flutter on SBC display)<br/>Mode 4: Full-screen avatar"]
    end

    KITCHEN_DEV -->|"WebSocket<br/>(Wi-Fi)"| WS
    BEDROOM_DEV -->|"WebSocket"| WS
    DESK_DEV -->|"WebSocket"| WS
    SENIOR_DEV -->|"WebSocket"| WS

    FLUTTER_MOBILE -->|"REST API<br/>(LAN)"| REST
    FLUTTER_DESKTOP -->|"REST API"| REST
    WEB_APP -->|"REST API"| REST
    TOUCH_KIOSK -->|"REST API"| REST

    WS --> ASR
    ASR --> LLM_ENGINE
    LLM_ENGINE --> TTS_ENGINE

    LLM_ENGINE --> AGENT
    AGENT --> SKILLS_R
    SKILLS_R --> DATA_R

    style TIER1 fill:#E74C3C,color:#fff
    style TIER2 fill:#2C3E50,color:#fff
    style TIER3 fill:#27AE60,color:#fff
    style RUST_SERVER fill:#E67E22,color:#fff
    style PIPELINE fill:#3498DB,color:#fff
```

## Voice Peripheral Detail (ESP32-S3)

```mermaid
graph TB
    subgraph ESP32["ESP32-S3 VOICE PERIPHERAL"]
        direction TB
        subgraph HW["HARDWARE"]
            MCU["Dual-core Xtensa LX7<br/>240MHz, 512KB SRAM"]
            MIC_HW["I2S MEMS Microphone<br/>(INMP441 / MSM261)"]
            SPEAKER_HW["I2S DAC + Speaker<br/>(MAX98357A)"]
            DISPLAY["OLED/LCD Display<br/>(SSD1306 / ST7789)"]
            BUTTONS["Buttons<br/>Wake / SOS / Action"]
            WIFI_HW["Wi-Fi 802.11 b/g/n"]
            BLE_HW["Bluetooth 5 LE"]
        end

        subgraph FW["FIRMWARE (Embedded Rust)"]
            AUDIO_DRV["Audio Driver<br/>(I2S + esp-opus codec)"]
            WAKE_WORD["Wake Word Detector<br/>(esp-sr / TFLite Micro)"]
            WS_CLIENT["WebSocket Client<br/>(connects to AI server)"]
            UI_DRV["Display Driver<br/>(avatar expressions,<br/>scrolling text)"]
            BTN_HANDLER["Button Handler<br/>(wake, SOS, dismiss)"]
            BLE_MGR["BLE Manager<br/>(setup, pairing)"]
            OTA["OTA Update<br/>(firmware updates<br/>from server)"]
        end
    end

    subgraph FLOW["VOICE INTERACTION FLOW"]
        LISTEN["Always Listening<br/>(low-power wake word)"]
        DETECT["Wake Word Detected<br/>'Hey Plnner'"]
        RECORD["Record Audio<br/>(opus-encoded)"]
        SEND["Send via WebSocket<br/>to AI Server"]
        RECEIVE["Receive TTS Audio<br/>(streaming)"]
        PLAY["Play through Speaker<br/>+ Show Avatar Expression<br/>+ Scroll Text"]

        LISTEN --> DETECT
        DETECT --> RECORD
        RECORD --> SEND
        SEND -->|"ASR→LLM→TTS<br/>on server"| RECEIVE
        RECEIVE --> PLAY
        PLAY --> LISTEN
    end

    style ESP32 fill:#E74C3C,color:#fff
    style FW fill:#E67E22,color:#fff
    style FLOW fill:#3498DB,color:#fff
```

## Rust AI Server Pipeline Detail

```mermaid
graph LR
    subgraph ASR_STAGE["ASR STAGE (<500ms)"]
        AUDIO_IN["Opus Audio<br/>(from ESP32)"]
        DECODE["Opus Decode"]
        WHISPER["whisper-rs<br/>(whisper.cpp Rust bindings)<br/>small.en model<br/>~300ms for 5s audio"]
        TEXT_OUT["Transcribed Text"]

        AUDIO_IN --> DECODE --> WHISPER --> TEXT_OUT
    end

    subgraph LLM_STAGE["LLM STAGE (<500ms)"]
        INPUT_PIPE["Input Understanding<br/>Pipeline"]
        SKILL_ROUTE["Skill Router<br/>(Two-Tower)"]
        BONSAI_INF["Bonsai 27B<br/>Inference<br/>(llama.cpp-rs)"]
        CONTEXT["Context Memory<br/>Retrieval (HNSW)"]
        RESPONSE["Generated<br/>Response Text"]

        TEXT_OUT --> INPUT_PIPE
        INPUT_PIPE --> SKILL_ROUTE
        SKILL_ROUTE --> BONSAI_INF
        CONTEXT --> BONSAI_INF
        BONSAI_INF --> RESPONSE
    end

    subgraph TTS_STAGE["TTS STAGE (<500ms)"]
        PERSONA["Companion Persona<br/>Selection<br/>(age-group voice)"]
        QWEN_TTS["qwen3_tts_rs<br/>0.6B CustomVoice<br/>1.76x real-time"]
        STREAM["Streaming Audio<br/>(PCM/Opus)"]
        WS_OUT["WebSocket Stream<br/>to ESP32"]

        RESPONSE --> PERSONA
        PERSONA --> QWEN_TTS
        QWEN_TTS --> STREAM
        STREAM --> WS_OUT
    end

    style ASR_STAGE fill:#3498DB,color:#fff
    style LLM_STAGE fill:#E67E22,color:#fff
    style TTS_STAGE fill:#27AE60,color:#fff
```

## Companion Voice with Qwen3 TTS

```mermaid
graph TB
    subgraph VOICE_SYSTEM["COMPANION VOICE SYSTEM (qwen3_tts_rs)"]
        subgraph PRESETS["AGE-GROUP VOICE PRESETS"]
            V_TODDLER["Toddler (2-5)<br/>Warm, animated, slow<br/>Preset: 'Vivian'"]
            V_KIDS["Kids (6-9)<br/>Friendly, playful<br/>Preset: 'Serena'"]
            V_TWEENS["Tweens (10-12)<br/>Encouraging, clear<br/>Preset: 'Dylan'"]
            V_TEENS["Teens (13-17)<br/>Casual, modern<br/>Preset: 'Aiden'"]
            V_YOUNG["Young Adults (18-25)<br/>Professional, upbeat<br/>Preset: 'Ryan'"]
            V_ADULT["Adults (26-45)<br/>Clear, efficient<br/>Preset: 'Eric'"]
            V_MIDDLE["Middle Age (46-64)<br/>Calm, trustworthy<br/>Preset: 'Ryan'"]
            V_SENIOR["Seniors (65+)<br/>Slow, gentle, warm<br/>Preset: 'Vivian' (slow)"]
        end

        subgraph CLONE["VOICE CLONING (0.6B Base model)"]
            REF_AUDIO["Reference Audio<br/>(caregiver records<br/>30s sample)"]
            ICL["In-Context Learning<br/>(no fine-tuning needed)"]
            CUSTOM_VOICE["Custom Cloned Voice<br/>(sounds like caregiver)"]

            REF_AUDIO --> ICL --> CUSTOM_VOICE
        end

        subgraph STYLE["STYLE INSTRUCTIONS (1.7B model)"]
            URGENT["'Speak urgently'<br/>(overdue reminders)"]
            GENTLE["'Speak gently'<br/>(bedtime reminders)"]
            EXCITED["'Speak excitedly'<br/>(achievements, goals met)"]
            CONCERNED["'Speak with concern'<br/>(missed medications)"]
        end

        subgraph FEATURES_V["CAPABILITIES"]
            MULTI_LANG["Multi-language:<br/>EN, ZH, JA, KO + auto-detect"]
            STREAMING_V["Server-Sent Events<br/>for real-time audio"]
            FORMATS["Output: WAV, PCM,<br/>MP3, FLAC, Opus"]
            RT["Performance:<br/>0.6B: 1.76x real-time<br/>1.7B: 3.05x real-time"]
        end
    end

    style PRESETS fill:#8E44AD,color:#fff
    style CLONE fill:#E67E22,color:#fff
    style STYLE fill:#E74C3C,color:#fff
    style FEATURES_V fill:#27AE60,color:#fff
```

## Zephyr RTOS: Ultra-Low-Power Wake Word Detection

```mermaid
graph TB
    subgraph ZEPHYR["ZEPHYR RTOS ON ESP32-S3"]
        subgraph TFLITE["TFLite Micro Runtime"]
            WAKE_MODEL["Wake Word Model<br/>~20KB neural network<br/>Detects 'Hey Plnner'"]
            KWS["Keyword Spotting<br/>Always-on, <1mW"]
        end

        subgraph POWER["POWER STATES"]
            DEEP_SLEEP["Deep Sleep<br/>(wake word listening only)<br/>~10mA"]
            ACTIVE["Active<br/>(recording + streaming)<br/>~150mA"]
            IDLE["Idle<br/>(display on, listening)<br/>~50mA"]

            DEEP_SLEEP -->|"Wake word<br/>detected"| ACTIVE
            ACTIVE -->|"Conversation<br/>complete"| IDLE
            IDLE -->|"Timeout<br/>30s"| DEEP_SLEEP
        end
    end

    NOTE["Key insight: TFLite Micro enables<br/>wake word detection on the ESP32<br/>without sending audio to the server<br/>until the user actually speaks.<br/>Privacy-preserving + power-efficient."]

    style ZEPHYR fill:#3498DB,color:#fff
    style TFLITE fill:#E67E22,color:#fff
    style POWER fill:#27AE60,color:#fff
```

## Full Family Deployment with EchoKit Peripherals

```mermaid
graph TB
    ROUTER["Wi-Fi Router"]

    subgraph PERIPHERALS["ESP32 VOICE PERIPHERALS (~$15-25 each)"]
        K_ECHO["Kitchen EchoKit<br/>Mic + Speaker + OLED<br/>Family reminder station"]
        B_ECHO["Bedroom EchoKit<br/>Mic + Speaker<br/>Senior medication alerts"]
        D_ECHO["Desk EchoKit<br/>Mic + Speaker + Button<br/>Kid's homework helper"]
        E_ECHO["Entryway EchoKit<br/>Mic + Speaker<br/>'Don't forget your lunch!'"]
    end

    subgraph SERVER["RUST AI SERVER (SBC)"]
        direction TB
        HW_SERVER["Hardware Options:<br/>• Raspberry Pi 5 (8GB): $80<br/>• Orange Pi 5 Plus: $120<br/>• Jetson Orin Nano: $250"]

        subgraph STACK["FULL RUST STACK"]
            WHISPER_S["whisper-rs (ASR)"]
            BONSAI_S["Bonsai 27B (LLM)"]
            QWEN_S["qwen3_tts_rs (TTS)"]
            AGENT_S["Agent Core<br/>(skills, memory,<br/>ranking, pacing)"]
            DB_S["SQLite + HNSW"]
        end
    end

    subgraph CLIENTS["RICH CLIENTS"]
        PHONES["Family Phones<br/>(Flutter app)<br/>On-device OR server API"]
        KIOSK_C["Kitchen Touchscreen<br/>(Flutter kiosk)<br/>Avatar + ticker"]
        WEB_C["Any Browser<br/>http://plnner.local<br/>Full AI via server"]
    end

    K_ECHO -->|WebSocket| SERVER
    B_ECHO -->|WebSocket| SERVER
    D_ECHO -->|WebSocket| SERVER
    E_ECHO -->|WebSocket| SERVER

    PHONES -->|REST API| SERVER
    KIOSK_C -->|REST API| SERVER
    WEB_C -->|REST API| SERVER

    ROUTER --> PERIPHERALS
    ROUTER --> SERVER
    ROUTER --> CLIENTS

    COST["Total Family Setup Cost:<br/>Server (Pi 5): $80<br/>4x EchoKit DIY: $100<br/>Touchscreen: $50<br/>────────────────<br/>Total: ~$230<br/>(one-time, no subscriptions)"]

    style PERIPHERALS fill:#E74C3C,color:#fff
    style SERVER fill:#2C3E50,color:#fff
    style STACK fill:#E67E22,color:#fff
    style CLIENTS fill:#27AE60,color:#fff
    style COST fill:#F1C40F,color:#000
```

## Architecture Decision: Rust vs Flutter for Edge

```mermaid
graph TB
    subgraph DECISION["ARCHITECTURE SPLIT"]
        subgraph RUST_DOMAIN["RUST DOMAIN (Server + Firmware)"]
            R1["AI Inference<br/>(Bonsai 27B via llama.cpp-rs)"]
            R2["ASR (whisper-rs)"]
            R3["TTS (qwen3_tts_rs)"]
            R4["Agent Core<br/>(skills, memory, ranking)"]
            R5["WebSocket Server<br/>(device connections)"]
            R6["REST API Server<br/>(client connections)"]
            R7["ESP32 Firmware<br/>(embedded Rust)"]
            R8["Data Layer<br/>(rusqlite + HNSW)"]
        end

        subgraph FLUTTER_DOMAIN["FLUTTER DOMAIN (UI Clients)"]
            F1["Mobile App<br/>(Android + iOS)"]
            F2["Desktop App<br/>(Win + Mac + Linux)"]
            F3["Web App<br/>(Browser)"]
            F4["Kiosk Display<br/>(Touchscreen on SBC)"]
            F5["Companion Avatar<br/>(Skia rendering)"]
            F6["Age-Adaptive UI<br/>(8 themes)"]
        end
    end

    subgraph WHY["WHY THIS SPLIT"]
        W1["Rust: 7-10x faster inference<br/>Memory safety without GC<br/>Zero-cost abstractions<br/>Native ARM64 + x64<br/>WASM compilation<br/>Real-time audio processing"]
        W2["Flutter: Best cross-platform UI<br/>Rich animation (Skia)<br/>Hot reload development<br/>Single codebase for 6 platforms<br/>Widget ecosystem<br/>Accessibility built-in"]
    end

    RUST_DOMAIN --> |"REST + WebSocket<br/>API boundary"| FLUTTER_DOMAIN

    style RUST_DOMAIN fill:#E67E22,color:#fff
    style FLUTTER_DOMAIN fill:#3498DB,color:#fff
    style WHY fill:#27AE60,color:#fff
```

## Latency Budget (EchoKit-style Pipeline)

```mermaid
graph LR
    subgraph LATENCY["END-TO-END VOICE INTERACTION"]
        L1["Wake Word<br/>Detection<br/>(on ESP32)<br/><50ms"]
        L2["Audio Capture<br/>+ WebSocket<br/>Send<br/>~100ms"]
        L3["ASR<br/>(whisper-rs)<br/><500ms"]
        L4["Input Pipeline<br/>+ Skill Route<br/><50ms"]
        L5["LLM Inference<br/>(Bonsai 27B)<br/><500ms<br/>(first token)"]
        L6["TTS<br/>(qwen3_tts_rs)<br/>streaming<br/>~200ms to<br/>first audio"]
        L7["WebSocket<br/>Stream to<br/>ESP32<br/><50ms"]

        L1 --> L2 --> L3 --> L4 --> L5 --> L6 --> L7
    end

    TOTAL["Total to first audio:<br/>~1.0-1.5s<br/>(conversational)"]

    L7 --> TOTAL

    style L1 fill:#27AE60,color:#fff
    style L3 fill:#3498DB,color:#fff
    style L5 fill:#E67E22,color:#fff
    style L6 fill:#8E44AD,color:#fff
    style TOTAL fill:#2ECC71,color:#fff
```
