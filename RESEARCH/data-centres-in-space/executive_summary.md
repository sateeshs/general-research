# Data Centres in Space: Executive Summary

**Research Date:** July 2026 | **Sources:** 100+ citations | **Quality:** Peer-reviewed, government, industry

---

## The Phenomenon

Between January and June 2026, four companies filed FCC applications to launch a combined **1.24 million satellites** designed to function as orbiting data centres for AI computation. This represents **85x the entire current active satellite population** of ~14,500. The filings were triggered by converging pressures: insatiable AI compute demand, terrestrial power grid constraints, community opposition to ground-based data centres, and dramatically falling launch costs.

## Who Is Building

| Company | Satellites | Status | Funding |
|---------|-----------|--------|---------|
| **SpaceX (Starmind)** | 1,000,000 | FCC filed Jan 2026 | Internal ($350B+ valuation) |
| **Orbital Inc** | 100,000 | FCC filed Jun 2026 | $5M pre-seed (a16z) |
| **Starcloud** | 88,000 | FCC filed Mar 2026; H100 in orbit Nov 2025 | $200M+ ($1.1B valuation) |
| **Blue Origin (Sunrise)** | 51,600 | FCC filed Mar 2026 | Internal (Bezos) |
| **Google (Suncatcher)** | 81 | R&D; 2027 demo planned | Internal |
| **Axiom Space** | Modular | ODC nodes in orbit Jan 2026 | Private |
| **China (Three-Body)** | 2,800 target | 12 sats launched May 2025 | $8.4B state funding |
| **ESA (ASCEND)** | Demo | 2026 demo planned | 300M EUR |

**Already in orbit**: Starcloud (NVIDIA H100, Nov 2025), Axiom Space (ODC nodes, Jan 2026), Kepler Communications (40 Jetson Orin modules across 10 satellites, Jan 2026), China Three-Body (12 AI satellites, May 2025).

## The Technical Case

**Advantages:**
- Solar irradiance in LEO: 1,361 W/m^2 (continuous, no weather/night in sun-sync orbits)
- Passive radiative cooling into ~3K vacuum (eliminates 30-40% energy overhead of terrestrial cooling)
- No water consumption, no grid connection, no land acquisition
- NVIDIA has purpose-built Space-1 Vera Rubin GPUs (25x more AI compute than H100 for space)

**Challenges:**
- **Thermal "physics wall"**: Heat can only radiate in vacuum; a single H100 (350W) needs ~1.1 m^2 of radiator
- **Radiation**: SEUs degrade electronics; rad-hardened chips sacrifice performance; software mitigation adds overhead
- **Latency**: LEO adds 10-30ms minimum round-trip; unsuitable for real-time interactive workloads
- **Maintenance**: No physical servicing; failed satellites become uncontrollable debris
- **Bandwidth**: Downlink capacity limits total data throughput
- **Launch cost**: Current ~$2,700/kg; need <$100/kg for cost parity with terrestrial DCs

## The Economic Case

- **Current cost gap**: Space compute is **4x+ terrestrial cost**; projected to narrow to ~30% premium by early 2030s
- **Terrestrial DC opposition**: 833 opposition groups across 49 US states; $130B+ in projects delayed/cancelled in Q1 2026
- **Market projection**: In-orbit DC market valued at **$1.77B by 2029**, **$39.09B by 2035** (67.4% CAGR)
- **Break-even**: Requires launch costs dropping 27x from current Falcon 9 rates
- **Near-term viability**: Edge computing and Earth observation preprocessing (processing before downlink) is economically viable now

## The Environmental Trade-Off

Space data centres **do not solve** terrestrial environmental problems; they **redistribute** them:

| Terrestrial Problem | Space "Solution" | New Problem Created |
|--------------------|-----------------|--------------------|
| Water consumption (billions of gallons/year) | Eliminated | Atmospheric metal oxide pollution from satellite reentry |
| Grid strain (460+ TWh/year) | Solar-powered in orbit | Rocket launch emissions (CO2, black carbon, ozone depletion) |
| Community opposition (833 groups) | No local residents | Light pollution, debris risk to all humanity |
| E-waste (partially recyclable) | N/A | Permanently destroyed in atmosphere (no mineral recovery) |
| Land use conflicts | No land needed | Orbital space physically constrained (Kessler risk) |

**Critical risks:**
- Kessler Syndrome threshold already exceeded at 520-1000km altitudes; adding 1.2M satellites is unprecedented
- 360 tonnes/year of aluminium oxide from satellite reentries could delay ozone recovery
- CRASH Clock orbital safety margin: 5.5 days (2025) vs 164 days (2018)
- Regulatory frameworks written for dozens of satellites, not millions

## The Geopolitical Dimension

A three-way competition is emerging:

- **US**: Private-led (SpaceX, Starcloud, Orbital, Google) with $200M+ VC and corporate investment
- **China**: State-directed with $8.4B in credit lines, 100+ organizations unified under Beijing committee, tied to 15th Five-Year Plan
- **Europe**: Government R&D through ESA ASCEND (300M EUR) and Horizon Europe, focused on data sovereignty

## Conclusions

1. **The technology works at prototype scale.** GPU computing in orbit is proven (Starcloud, Axiom, HPE Spaceborne Computer).

2. **The economics don't work yet.** Space compute costs 4x+ terrestrial. Near-term viability is limited to edge computing niches where processing before downlink saves bandwidth.

3. **The environmental argument is misleading.** Moving data centres to space trades known, local, manageable impacts for novel, global, potentially irreversible ones (Kessler Syndrome, ozone depletion, atmospheric contamination).

4. **Regulatory frameworks are dangerously inadequate.** The FCC accepted a million-satellite filing within 5 days without an environmental assessment. The Outer Space Treaty was written for a world of dozens of satellites.

5. **The scale proposed is unprecedented and physically constrained.** 1.24 million data centre satellites plus existing/planned communications constellations could render LEO unusable.

6. **The most realistic near-term use case is in-orbit edge processing** — satellites processing Earth observation data before downlink, not replacing terrestrial hyperscale data centres.

7. **Full cost parity with terrestrial DCs is speculative** (projected ~2040), contingent on launch costs dropping to <$100/kg and solving the thermal management "physics wall."

---

*This research was conducted using a multi-agent deep research framework with 5 parallel research agents, cross-reference validation, and citation quality verification. See [appendices/methodology.md](appendices/methodology.md) for details.*
