# Visual Descriptions for Data Centres in Space Research

These are descriptions for charts and diagrams that would accompany this research.

---

## 1. Orbital Data Centre Race Timeline (Gantt Chart)

**Type:** Horizontal timeline / Gantt chart
**X-axis:** 2017 to 2040
**Y-axis:** Companies/Programs

Shows key milestones for each player:
- HPE Spaceborne Computer (2017-present)
- ESA PhiSat-1 (2020)
- Caltech SSPD-1 (2023)
- Starcloud founding to H100 in orbit (2024-2025) to 88K filing (2026)
- China Three-Body constellation (2025-2035)
- Axiom ODC nodes (2025-2030)
- SpaceX Starmind filing (Jan 2026) to AI1 prototype (2027) to commercial ops (2028)
- Orbital Inc filing (Jun 2026) to pathfinder (2027) to Orbital-1 (2028)
- Blue Origin Sunrise filing (Mar 2026)
- Google Suncatcher demo (2027)
- Cost parity milestone (~2040, speculative)

---

## 2. Satellite Count Comparison (Bar Chart)

**Type:** Horizontal bar chart (logarithmic scale)
**Data:**

| Entity | Satellites |
|--------|-----------|
| Current active (all) | 14,500 |
| Starlink (active) | 10,759 |
| Amazon Leo (authorized) | 7,727 |
| Blue Origin Sunrise | 51,600 |
| Starcloud | 88,000 |
| Orbital Inc | 100,000 |
| SpaceX Starmind | 1,000,000 |

Color coding: Currently in orbit (green), FCC filed (blue), Proposed (gray)

---

## 3. Cost to LEO Over Time (Line Chart)

**Type:** Line chart with logarithmic Y-axis
**X-axis:** 1960-2030 (projected)
**Y-axis:** $/kg to LEO

Key data points:
- 1960s: $54,500/kg (Saturn V)
- 1980s: $54,500/kg (Space Shuttle)
- 2010: ~$5,000/kg (Falcon 9 early)
- 2025: ~$2,700/kg (Falcon 9 Block 5)
- Target: $100-200/kg (Starship)
- Break-even: <$100/kg (for DC cost parity)

Annotation line at $100/kg showing "Orbital DC Cost Parity Threshold"

---

## 4. Environmental Trade-Off Comparison (Sankey/Flow Diagram)

**Type:** Two-column comparison or Sankey diagram

Left column: Terrestrial DC Impacts
- Water: billions of gallons/year
- Energy: 460+ TWh from grid
- Land: community opposition (833 groups)
- E-waste: partially recyclable

Right column: Orbital DC Impacts
- Atmospheric: aluminium oxide, ozone depletion
- Launch emissions: CO2, black carbon
- Orbital: debris risk, Kessler threshold
- Light: astronomy interference

Center: Arrows showing what each "solves" and what new problem it creates

---

## 5. Data Centre Energy Growth (Area Chart)

**Type:** Stacked area chart
**X-axis:** 2020-2030
**Y-axis:** TWh

Layers:
- Traditional data centre workloads
- AI training workloads
- AI inference workloads
- Projected growth (shaded uncertainty band)

Key annotations:
- 2024: ~380 TWh
- 2025: ~460 TWh (+17% YoY)
- 2026: ~565 TWh (+26% YoY)
- 2030: ~945 TWh (~2x from 2025)

---

## 6. Funding Landscape (Bubble Chart)

**Type:** Bubble chart
**X-axis:** Time of first announcement/filing
**Y-axis:** Total funding raised
**Bubble size:** Proposed satellite count

Companies plotted:
- SpaceX (largest bubble, internal funding)
- China programs ($8.4B, state)
- ESA ASCEND (300M EUR)
- Starcloud ($200M+)
- Aetherflux ($60M)
- Orbital Inc ($5M)
- Lonestar ($5M)

---

## 7. Space Debris Growth Projection (Line Chart)

**Type:** Line chart with uncertainty bands
**X-axis:** 2000-2040
**Y-axis:** Number of tracked objects in LEO

Lines:
- Historical tracked objects (solid)
- Projected with current constellation plans (dashed)
- Projected with orbital DC constellations (dotted, with wide uncertainty band)

Annotations:
- 2007: Chinese ASAT test (+2,087 debris pieces)
- 2009: Cosmos-Iridium collision (+2,300 pieces)
- 2021: Russian ASAT test (+1,500 pieces)
- Kessler threshold line
- CRASH Clock metric overlay

---

## 8. Geopolitical Competition Map (World Map)

**Type:** Annotated world map

Regions:
- **US (West Coast):** SpaceX (Hawthorne), Orbital Inc (LA), Google (Mountain View), Starcloud (Redmond), Blue Origin (Kent)
- **US (Texas):** SpaceX Starbase
- **US (Houston):** Axiom Space
- **China:** Zhejiang Lab, ADAspace, CASC, Beijing coordination committee
- **Europe:** ESA ASCEND (Thales Alenia Space), ReOrbit (Finland)
- **Japan:** JAXA OHISAMA
- **India:** ISRO AI Data Centre concept

Inset: Pie chart of global investment by bloc (US private, China state, EU agency)
