# Data Centres in Space: Key Statistics and Data

**Last Updated:** July 2026

---

## 1. FCC Filings for Orbital Data Centre Constellations

| Company | Satellites | Filing Date | Altitude (km) | Orbit Type | Compute/Satellite |
|---------|-----------|-------------|---------------|------------|-------------------|
| SpaceX (Starmind) | 1,000,000 | Jan 30, 2026 | 500-2,000 | NGSO | 150 kW (AI1) |
| Orbital Inc | 100,000 | Jun 24, 2026 | 500-850 | Sun-synchronous | 100 kW |
| Starcloud | 88,000 | Mar 13, 2026 | 600-850 | Sun-synchronous | TBD |
| Blue Origin (Sunrise) | 51,600 | Mar 19, 2026 | 500-1,800 | Sun-synchronous | TBD |
| **Total proposed** | **~1,239,600** | | | | |

**Context:** Total active satellites in orbit (mid-2026): ~14,500. Proposed orbital DCs represent 85x current population.

---

## 2. Funding and Valuations

| Company | Total Raised | Valuation | Lead Investors |
|---------|-------------|-----------|----------------|
| Starcloud | $200M+ | $1.1B (Mar 2026) | Benchmark, EQT Ventures |
| Aetherflux | $60M | Undisclosed | Robinhood co-founder Baiju Bhatt |
| Orbital Inc | $5M | Undisclosed | a16z Speedrun |
| Lonestar Data | $5M | Undisclosed | Various |
| China (state funding) | $8.4B (credit lines) | N/A | State-directed |
| ESA ASCEND | 300M EUR | N/A | European Commission |

---

## 3. Hardware in Orbit (as of July 2026)

| Date | Company | Hardware | Significance |
|------|---------|----------|-------------|
| Nov 2, 2025 | Starcloud | NVIDIA H100 GPU (60 kg satellite) | First consumer GPU in orbit |
| Jan 11, 2026 | Kepler | 40 NVIDIA Jetson Orin modules (10 satellites) | First distributed cloud in orbit |
| Jan 11, 2026 | Axiom Space | 2 ODC nodes | First dedicated ODC nodes in LEO |
| May 14, 2025 | China (Zhejiang Lab) | 12 AI satellites (5 POPS) | Largest orbital AI deployment |
| Mar 16, 2026 | NVIDIA | Space-1 Vera Rubin Module announced | 25x H100 for space inference |

---

## 4. Satellite Specifications

### SpaceX AI1

| Parameter | Value |
|-----------|-------|
| Wingspan | 70 meters (230 ft) tip-to-tip |
| Height (deployed) | 20 meters (66 ft) |
| Peak compute power | 150 kW |
| Average compute | 120 kW |
| Solar panel rating | 150 kW |
| Output density | 250 W/m^2 |
| Chips | Custom xAI (Grok models) |

### Orbital Inc

| Parameter | Value |
|-----------|-------|
| Dry mass | 1.5-2.5 metric tons (~2 tons nominal) |
| Total span | ~100 meters tip-to-tip |
| Solar array power | 100 kW |
| Solar array size | ~tennis court |
| GPU | NVIDIA Space-1 Vera Rubin (full); single Blackwell (pathfinder) |
| Cooling | Passive radiative |

### Starcloud-1

| Parameter | Value |
|-----------|-------|
| Mass | 60 kg |
| GPU | Single NVIDIA H100 |
| Claimed performance | 100x more powerful than previous space computers |
| Demo | Ran Google Gemini in orbit |

---

## 5. Space Environment Data

### Solar Power in LEO

| Parameter | Value |
|-----------|-------|
| Solar irradiance (LEO) | 1,361 W/m^2 |
| vs ground solar (peak) | ~5x more energy dense |
| Typical solar panel efficiency | 30-35% (space-grade triple-junction) |
| Effective power | ~410-475 W/m^2 |

### Space Debris (mid-2026)

| Category | Count |
|----------|-------|
| Tracked objects (>10 cm) | ~43,000 |
| Active payloads | ~11,000 |
| Estimated objects 1-10 cm | ~1.2 million |
| Estimated objects <1 cm | >140 million |
| Total debris mass | ~12,400 tonnes |
| Starlink collision avoidance manoeuvres (2025) | ~300,000 |
| CRASH Clock safety margin (2025) | 5.5 days (vs 164 days in 2018) |
| LEO collision probability YoY increase (2026) | +20% |

### Thermal Management

| Parameter | Value |
|-----------|-------|
| Background temperature (space) | ~3 K (-270 C) |
| H100 GPU thermal design power | 350 W |
| Radiator area per H100 | ~1.1 m^2 |
| 10 MW orbital DC radiator mass | 200,000-1,000,000 kg |
| Radiator cost (10 MW DC) | $20-100M |

---

## 6. Terrestrial Data Centre Statistics

### Energy Consumption

| Year | Consumption | Growth |
|------|-------------|--------|
| 2024 | ~380-400 TWh | Baseline |
| 2025 | ~460-490 TWh | +17% YoY |
| 2026 (projected) | ~565 TWh | +26% YoY |
| 2030 (projected) | ~945 TWh | ~2x from 2025 |

### AI Training Energy

| Model | Training Energy | Equivalent |
|-------|----------------|------------|
| GPT-3 (175B) | ~1,287 MWh | ~120 US homes for 1 year |
| GPT-4 (~280B+) | ~50,000 MWh | San Francisco for ~3 days |
| Llama 3.1 (8B/70B/405B) | ~30,000 MWh | 39.3M GPU-hours on H100s |

### Water Consumption

| Metric | Value |
|--------|-------|
| Medium DC daily usage | Up to 300,000 gallons/day |
| Large DC daily usage | Up to 5 million gallons/day |
| Google 2024 total | 6.1 billion gallons |
| AI DC vs traditional DC | 10-50x more cooling water |
| Texas projected 2030 | 399 billion gallons |

### Community Opposition (mid-2026)

| Metric | Value |
|--------|-------|
| Active opposition groups | 833 (49 US states) |
| Growth rate | 396 (end 2025) to 833 (Mar 2026) |
| Projects delayed/cancelled Q1 2026 | 75+ ($130B+ value) |
| States with moratoriums | ~12 |

---

## 7. Launch Cost Trajectory

| Era | Cost ($/kg to LEO) | Vehicle |
|-----|-------------------|---------|
| 1960s (Saturn V) | ~$54,500 | Saturn V |
| 1980s (Space Shuttle) | ~$54,500 | Space Shuttle |
| 2010s (Falcon 9 early) | ~$5,000 | Falcon 9 v1.0 |
| 2025 (Falcon 9 reusable) | ~$2,700 | Falcon 9 Block 5 |
| 2025 (industry average) | ~$3,868 | Various |
| Target (Starship V3) | $100-200 | Starship (fully reusable) |
| Required for DC cost parity | <$100 | Hypothetical |

**96% cost reduction** from historical average to 2025 average.

---

## 8. Market Projections

| Metric | Value | Source |
|--------|-------|--------|
| In-orbit DC market 2029 | $1.77B | ResearchAndMarkets |
| In-orbit DC market 2035 | $39.09B | ResearchAndMarkets |
| CAGR (2029-2035) | 67.4% | ResearchAndMarkets |
| Space compute cost premium (current) | >4x terrestrial | Luminix |
| Space compute cost premium (early 2030s) | ~30% | Luminix (projected) |
| Total satellite launch vehicle market 2026 | $22.74B | SIA |
| Global space economy | $469B (2024) | SIA |
| Hyperscaler CapEx 2026 | $660-690B | Axis Intelligence |

---

## 9. Regulatory Framework

| Authority | Requirement | Status |
|-----------|-------------|--------|
| FCC (US) | 5-year post-mission disposal | Active since Sep 2022 |
| FCC (US) | 50% deployment in 6 years, 100% in 9 | Standard milestone |
| ITU | 10% in 2yr, 50% in 5yr, 100% in 7yr | NGSO spectrum retention |
| ESA Zero Debris Charter | No new debris by 2030 | Voluntary (Nov 2023) |
| Outer Space Treaty (1967) | Space as "province of all mankind" | Binding international law |
| Liability Convention (1972) | Absolute liability for ground damage | Binding; state-to-state claims |
| EU Space Act | First comprehensive EU space regulation | Draft published Jun 2025 |

---

## 10. Historical Computing in Space Milestones

| Year | Milestone | Hardware |
|------|-----------|---------|
| 1998-present | ISS computing (MDM units) | Honeywell MDMs, MIL-STD-1553 bus |
| 2012/2021 | Curiosity/Perseverance rovers | BAE RAD750 (200 MHz, 10.4M transistors) |
| 2017 | HPE Spaceborne Computer-1 | COTS supercomputer (657 days on ISS) |
| 2019 | ESA OPS-SAT | 10x more powerful than any ESA spacecraft |
| 2020 | ESA PhiSat-1 | Intel Movidius Myriad 2 VPU (first AI chip in orbit) |
| 2021 | HPE Spaceborne Computer-2 | GPUs + AI processing (first LLM in space) |
| 2023 | Caltech SSPD-1 | First wireless power transmission from space |
| 2025 | Starcloud-1 | NVIDIA H100 (first consumer GPU in orbit) |
| 2026 | NVIDIA Space-1 | Purpose-built space GPU (25x H100 for inference) |
