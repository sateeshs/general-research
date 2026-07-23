# Environmental Impact, Space Debris Risks, and Regulatory Challenges of Space Data Centres

**Research Date:** July 2026
**Scope:** Comprehensive analysis of environmental, orbital safety, astronomical, and regulatory dimensions of proposals to relocate data centre infrastructure to orbit.

---

## Table of Contents

1. [Space Debris and Kessler Syndrome](#1-space-debris-and-kessler-syndrome)
2. [Light Pollution and Astronomy Impact](#2-light-pollution-and-astronomy-impact)
3. [Environmental Footprint](#3-environmental-footprint)
4. [Energy Comparison: Space vs Earth](#4-energy-comparison-space-vs-earth)
5. [Regulatory and Legal Framework](#5-regulatory-and-legal-framework)
6. [Public and Community Opposition to Terrestrial Data Centres](#6-public-and-community-opposition-to-terrestrial-data-centres)
7. [Conclusions](#7-conclusions)
8. [Sources](#8-sources)

---

## 1. Space Debris and Kessler Syndrome

### 1.1 What Is Kessler Syndrome?

Kessler Syndrome, first described by NASA scientist Donald J. Kessler in 1978, refers to a theoretical cascading chain reaction in which collisions between objects in low Earth orbit (LEO) generate debris that causes further collisions, eventually rendering certain orbital altitudes unusable for decades or centuries. The concern is not a single catastrophic event but a self-sustaining feedback loop: each collision creates fragments, each fragment increases the probability of further collisions, and the resulting exponential growth in debris density makes safe satellite operations impossible.

A March 2025 assessment by researchers Lewis and Kessler himself found that **the current population of intact objects already exceeds the unstable threshold at all altitudes between 400 km and 1,000 km**, and exceeds the runaway threshold at nearly all altitudes between 520 km and 1,000 km (SpaceOrbitals, "Kessler Syndrome: The Cascading Debris Risk in Low Earth Orbit," 2026).

The "CRASH Clock" metric -- a measure of orbital safety margin -- stood at **5.5 days in 2025, compared to 164 days in 2018**, meaning a disruptive event such as a severe solar storm could trigger catastrophic debris generation in as little as 2.8 days (SpaceOrbitals, 2026).

### 1.2 Current Tracked Objects in Orbit

According to ESA's Space Environment Report 2025 and subsequent 2026 updates:

| Category | Count |
|----------|-------|
| Tracked objects (>10 cm) | ~43,000 |
| Active payloads | ~11,000 |
| Spent rocket stages | >2,000 |
| Estimated objects 1-10 cm | ~1.2 million |
| Estimated objects <1 cm | >140 million |
| Total debris mass in orbit | ~12,400 tonnes |

(ESA, "Space Environment Report 2025," 2025; New Space Economy, "Statistics on Space Debris by Orbit as of 2025," January 2026; Orbital Radar, "Space Debris Statistics 2026," 2026)

ESA's 2026 report documents a **20% jump in collision probability in LEO** year-over-year (FODNews, "ESA: LEO Debris Collision Risk Up 20% in 2026," 2026).

### 1.3 Collision Probability with 100,000+ New Satellites

The scale of proposed orbital data centre constellations is without precedent:

- **SpaceX** filed an FCC application on January 30, 2026, for **up to one million orbital data centre satellites** at altitudes between 500 and 2,000 km (SpaceNews, "SpaceX files plans for million-satellite orbital data center constellation," January 2026).
- **Orbital Compute Inc.** filed for **100,000 satellites** for distributed computing (Pixalytics, "Data Centres in Space," 2026).
- **SpaceX's existing Starlink** constellation already operates approximately **10,413 satellites** as of June 2026, with plans for 42,000 (Space.com, "Starlink satellites: Facts, tracking and impact on astronomy," 2026).

SpaceX reported that Starlink satellites performed approximately **300,000 collision-avoidance manoeuvres in 2025 alone** (SpaceOrbitals, 2026). The conjunction warning rate for operational satellites in the 600-900 km band is roughly **5-10x what it was a decade ago** (SpaceOrbitals, 2026).

Adding hundreds of thousands or millions more objects to an already congested environment would dramatically increase collision probability. The relationship between object count and collision risk is not linear but approximately quadratic -- doubling the number of objects roughly quadruples the collision probability.

### 1.4 Major Historical Debris Events

**Chinese ASAT Test (January 11, 2007)**
China launched a kinetic kill vehicle that destroyed its own defunct Fengyun-1C weather satellite at 863 km altitude, creating at least **2,087 trackable debris pieces and over 35,000 smaller fragments**. This remains the largest single debris-generating event in history. Less than 7% of the debris is predicted to decay within 10 years (ResearchGate, "Analysis of the 2007 Chinese ASAT Test," 2012; Space.com, "Worst Satellite Breakups in History," updated).

**Cosmos-Iridium Collision (February 10, 2009)**
An active Iridium 33 communications satellite and the derelict Russian military satellite Cosmos 2251 collided at 789 km above Siberia, producing **more than 2,300 pieces of trackable debris**. These two events alone accounted for more than a third of the total catalogued satellite population in LEO at the time (KeepTrack, "The Day Two Satellites Hit Each Other at 26,000 MPH").

**Russian ASAT Test (November 2021)**
Russia destroyed its own defunct Cosmos 1408 satellite with a direct-ascent anti-satellite missile, generating over **1,500 pieces of trackable debris** and forcing the International Space Station crew to shelter in their spacecraft.

### 1.5 Deorbiting Requirements

The regulatory landscape for satellite disposal has tightened significantly:

| Authority | Requirement | Status |
|-----------|-------------|--------|
| IADC/UN COPUOS | 25-year post-mission disposal guideline | Adopted 2002/2007 |
| FCC (US) | **5-year post-mission disposal** for LEO satellites | Adopted September 2022 |
| ESA Zero Debris Charter | Under-5-year disposal, 90% success probability | Adopted November 2023 |
| ESA Zero Debris Charter Target | No new debris generation | By 2030 |

(FCC, "FCC Adopts New '5-Year Rule' for Deorbiting Satellites," 2022; NASA, "Deorbit Systems," 2026; HawkLogic, "FCC 5-Year Rule vs ESA Zero Debris vs 25-Year," 2026)

The shift from 25 years to 5 years reflects growing urgency, but compliance remains a challenge. The 5-year rule applies only to FCC-licensed satellites; other national jurisdictions may have weaker or no equivalent requirements.

### 1.6 What Happens When a Server Satellite Fails in Orbit

When a satellite loses power or control capability, it becomes an uncontrollable piece of debris tumbling through its orbital path. Unlike traditional communications satellites, space data centre satellites carry **dense computing hardware, additional thermal management systems, and potentially lithium batteries**, making them both heavier and more complex than conventional small satellites.

A failed server satellite:

1. **Cannot perform collision avoidance manoeuvres**, becoming a passive threat to every other object sharing its orbital altitude.
2. **May not be able to execute a controlled deorbit**, remaining in orbit for years or decades depending on altitude (satellites above ~600 km can persist for 25+ years without active deorbit).
3. **Creates a larger debris field if struck**, as the dense hardware components fragment into numerous high-velocity projectiles.
4. **May release hazardous materials**, including lithium battery components and semiconductor materials, into the orbital environment.

The 2009 Cosmos-Iridium collision demonstrated the consequences: a single failed satellite colliding with an active one created **more than 1,800 pieces of debris at least 10 cm or larger**, each carrying the kinetic energy to destroy another satellite (European Parliament, "What if orbital debris destroyed satellites?" February 2025; BBC Science Focus, "A satellite collision catastrophe is now inevitable, experts warn," 2026).

### 1.7 Active Debris Removal Efforts

- **Astroscale** demonstrated the first commercial capture-and-deorbit with the ELSA-d servicer in 2024-2025.
- **ClearSpace** has an ESA contract for a 2026-2027 debris removal mission (ClearSpace-1).
- These efforts are nascent and can remove at most a few objects per year -- orders of magnitude below the rate of new object introduction.

---

## 2. Light Pollution and Astronomy Impact

### 2.1 Current Impact of Starlink on Ground-Based Astronomy

With **10,413 Starlink satellites in orbit as of June 2026**, the impact on astronomical observations is already measurable and significant:

- Wide-field surveys and deep observations of faint objects are compromised, with some images containing **more than 90 satellite streaks** (BBC Sky at Night Magazine, "Are we destroying our window to the cosmos?" 2026).
- For the Vera C. Rubin Observatory (LSST), studies predict that **20% of midnight images will contain satellite trails**, and **30-80% of all exposures during twilight** will be affected (Rubin Observatory, "Impact of Satellite Constellations," updated; Tyson et al., "Mitigation of LEO Satellite Brightness and Trail Effects on the Rubin Observatory LSST," *Astronomical Journal*, 2020).
- The LSST's ability to detect asteroids approaching from interior to Earth's orbit would be **severely impacted** because those directions are visible only during twilight when LEO satellites are brightest (Tyson et al., 2020).

### 2.2 Impact of 100,000+ Additional Satellites

An ESO study warned that proposals to launch over **1.7 million satellites** would have **"devastating consequences for astronomy"** (BBC Sky at Night Magazine, "This is one hour of satellite trails over the world's darkest sky," 2026).

A 2025 study published in *Monthly Notices of the Royal Astronomical Society* found that the recommended maximum to preserve astronomical observation is **no more than 100,000 faint satellites** (satellites not visible to the naked eye) in orbit at any time (MNRAS, "Reducing the impact of satellite brightness for astronomy," 2025).

SpaceX's single filing for one million orbital data centre satellites would exceed this threshold by an order of magnitude.

### 2.3 Radio Frequency Interference

The impact extends beyond optical astronomy to radio wavelengths:

- Starlink satellites have been detected **transmitting unintended electromagnetic radiation outside their designated downlink frequencies**, interfering with radio telescope observations (CBC News, "Starlink satellites create light pollution and disrupt radio frequencies," 2024).
- A 2025 study in *Astronomy & Astrophysics* documented **growing unintended Starlink broadband emission in the SKA-Low frequency range**, the frequencies used by the forthcoming Square Kilometre Array (A&A, "The growing impact of unintended Starlink broadband emission on radio astronomy in the SKA-Low frequency range," 2025).
- Aggregate radio signals from satellite constellations can threaten observations even when individual satellites comply with emission standards (IAU, "Satellite Constellations" theme page).

### 2.4 IAU Position

The International Astronomical Union established the **Centre for the Protection of the Dark & Quiet Sky from Satellite Constellation Interference (IAU CPS)** and has taken a formal position:

> "The IAU embraces the principle of a dark and radio-quiet sky as not only essential to advancing our understanding of the Universe, but also as a resource that should be protected for all the Earth's inhabitants." (IAU, "Statement on Satellite Constellations," 2019; updated positions through 2026)

The IAU uses its status as Permanent Observer in the UN Committee for the Peaceful Uses of Outer Space (COPUOS) to advocate for regulation. A July 2025 preprint found that **satellite constellations already exceed the brightness limits established by the IAU** (arXiv:2507.00107, "Satellite Constellations Exceed the Limits of Acceptable Brightness Established by the IAU," 2025).

### 2.5 Vera Rubin Observatory / LSST Impact Studies

The Vera C. Rubin Observatory, currently under commissioning in Chile, is the facility most severely affected by satellite constellations due to its extremely wide field of view (9.6 square degrees):

- Simulations predict that **nearly every LSST image taken during twilight will be affected** by at least one satellite trail (Tyson et al., 2020).
- Precision cosmological studies are vulnerable to systematic artefacts from masking satellite trail regions (Tyson et al., 2020).
- The NSF awarded **$750,000 in July 2024** for a three-year project to develop satellite avoidance tools and improved brightness modelling (NSF/Rubin Observatory, 2024).

### 2.6 Mitigation Attempts

| Mitigation | Description | Effectiveness |
|-----------|-------------|---------------|
| DarkSat | Darkened satellite coating | Measurable but insufficient for wide-field surveys |
| VisorSat | Sun visor attachment | Reduced brightness ~50%, still above IAU threshold |
| Sunshades | Various designs | Modest improvements, engineering trade-offs |
| Software masking | Algorithmic trail removal | Can introduce systematic artefacts |
| Satellite avoidance | Scheduling around passes | Reduces usable observation time |

(Scientific American, "Starlink and Astronomers Are in a Light Pollution Standoff," 2025; MNRAS, 2025)

All hardware modifications have been **"insufficient to prevent contamination of sensitive wide-field surveys"** (MNRAS, 2025).

---

## 3. Environmental Footprint

### 3.1 Carbon Footprint of Rocket Launches

Rocket launches produce significant emissions, though their absolute contribution remains a small fraction of global emissions -- for now:

- Rockets generate **50-75 tonnes of CO2 per passenger** equivalent, compared to 1-3 tonnes for a long-haul flight (Space Launch Schedule, "Rocket Launches: Balancing Innovation and Sustainability," 2024).
- Between 2019 and 2024, **rocket fuel consumption more than tripled** (Space Launch Schedule, 2024).
- Current spaceflight contributes approximately **1,000 tonnes of black carbon to the stratosphere annually** (NOAA CSL, 2022).
- A Falcon 9 launch produces approximately **425 tonnes of CO2** per flight. SpaceX alone conducted over 100 launches in 2024 (various sources).

To deploy and maintain a million-satellite constellation, SpaceX would need to conduct **thousands of launches annually**, dramatically scaling up these emissions.

### 3.2 Launch Emissions vs Terrestrial Data Centre Emissions

| Category | Annual CO2 Equivalent |
|----------|----------------------|
| Global data centres (operational) | ~200-300 million tonnes CO2e |
| SpaceX 2024 launches (~100 flights) | ~42,500 tonnes CO2 |
| Hypothetical 1,000 launches/year for orbital DCs | ~425,000 tonnes CO2 (launch only) |
| Single GPT-4 training run | ~5,000-12,500 tonnes CO2e |

(IEA, "Key Questions on Energy and AI," 2025; Space Launch Schedule, 2024; Polytechnique Insights, "Carbon footprint and space activities," 2024)

While current launch emissions are dwarfed by data centre operational emissions, the comparison changes dramatically if the launch cadence increases by 10-100x to support orbital data centre constellations. Furthermore, this comparison omits satellite manufacturing emissions, which are significant.

### 3.3 Lifecycle Analysis: Satellites vs Terrestrial Data Centres

**Terrestrial data centres** have lifespans of 15-25 years, with server hardware refreshed every 3-5 years. The embodied carbon of construction and hardware manufacturing is amortised over these long periods.

**Orbital data centre satellites** face:
- **Radiation degradation** of electronics, significantly shortening useful life compared to ground-based servers.
- **5-year maximum orbital lifetime** under FCC rules, requiring complete fleet replacement every few years.
- **No repair or upgrade capability** for most proposed designs (unlike terrestrial servers that can be upgraded incrementally).
- **Full replacement costs** in both manufacturing emissions and launch emissions every cycle.

### 3.4 Water Usage: Terrestrial Data Centres

Data centre cooling is a massive water consumer:

- A medium-sized data centre consumes **up to 300,000 gallons of water per day**, equivalent to approximately 1,000 households (EESI, "Data Centers and Water Consumption," 2024).
- Larger facilities consume **up to 5 million gallons per day** -- equivalent to a town of 10,000-50,000 people (DGTL Infra, "Data Center Water Usage," 2025).
- Google reported **6.1 billion gallons** of water consumption in 2024, an increase from 4.3 billion gallons in 2021 (DGTL Infra, 2025).
- AI data centres consume **10-50x more cooling water** than traditional server farms (Lincoln Institute, "Data Drain," 2025).
- Data centres in Texas alone are projected to use **49 billion gallons in 2025**, potentially rising to **399 billion gallons by 2030** (Congressional Research Service, R48646, 2025).
- By 2027, global AI demand could drive annual water withdrawals of **1.1-1.7 trillion gallons** (Introl, "Water Usage Efficiency," 2025).

Space data centres would not require water cooling (the vacuum of space provides natural thermal radiation), which is a genuine advantage. However, the water savings must be weighed against the atmospheric and orbital environmental costs of launch and satellite disposal.

### 3.5 E-Waste: Orbit vs Earth

**Terrestrial e-waste** is a major environmental problem, with approximately 62 million tonnes generated globally in 2022 (UN Global E-Waste Monitor). However, terrestrial e-waste can be recycled, with critical minerals recovered.

**Orbital e-waste** presents a different problem:
- Satellites that deorbit burn up in the atmosphere, releasing materials as **metallic vapour and nanoparticles** into the upper atmosphere.
- In 2022, reentring satellites caused a **29.5% increase in aluminium above natural atmospheric levels**, depositing approximately **17 metric tonnes of aluminium oxides** into the mesosphere (Ferreira et al., "Potential Ozone Depletion From Satellite Demise During Atmospheric Reentry," *Geophysical Research Letters*, 2024).
- In a megaconstellation era, this could rise to **360 tonnes of aluminium oxide per year** entering the atmosphere (Ferreira et al., 2024).
- A typical 250-kg satellite generates approximately **30 kg of aluminium oxide nanoparticles** upon reentry, which may persist for **decades** before drifting to stratospheric altitudes (Science, "Burned-up satellites are polluting the atmosphere," 2024).
- These aluminium oxides are **catalysts for chlorine activation that depletes stratospheric ozone** (University of Southampton, "First study to examine environmental impact of deorbited satellites," 2024).
- No minerals or materials are recoverable from burned-up satellites -- they are permanently lost to the supply chain.

### 3.6 Ozone Layer Effects from Rocket Exhaust

Research published in *Nature npj Climate and Atmospheric Science* (2025) demonstrates that rocket launches pose a direct threat to the ozone layer:

- Rocket exhaust products from the four most common propellant types (kerosene, cryogenic, hypergolic, and solid rocket motor) can **all cause ozone depletion** (Ryan et al., *Earth's Future*, 2022).
- Black carbon from rockets accumulates in the stratosphere, absorbs solar radiation, warms surrounding air, and **alters global circulation patterns**, causing ozone column reductions primarily in northern high latitudes (Maloney et al., *Journal of Geophysical Research: Atmospheres*, 2022).
- Projections show an ambitious launch growth scenario yields a **-0.29% depletion in annual-mean total column ozone by 2030**, with Antarctic springtime ozone decreasing by **3.9%** (Nature, 2025).
- Ongoing and frequent launches **could delay ozone recovery**, which is particularly concerning as the ozone layer is still healing from CFC-related damage (NOAA CSL, 2022; Undark, "As Rocket Launches Increase, They May Be Polluting the Skies," April 2026).

**Combined effect of launches and reentry**: By 2040, NOAA projects there would be **enough alumina in the stratosphere from satellite reentry to alter wind speeds and temperatures at the poles** and impact Earth's climate in ways scientists do not fully understand (NOAA CSL, April 2025).

---

## 4. Energy Comparison: Space vs Earth

### 4.1 Global Data Centre Energy Consumption

Data centre energy consumption is growing at an unprecedented rate, driven primarily by AI workloads:

| Year | Consumption | Growth |
|------|-------------|--------|
| 2024 | ~380-400 TWh | Baseline |
| 2025 | ~460-490 TWh | +17% YoY |
| 2026 (projected) | ~565 TWh | +26% YoY |
| 2030 (projected) | ~945 TWh | ~2x from 2025 |

(IEA, "Data centre electricity use surged in 2025," 2026; Gartner, "Data Center Electricity Consumption to Grow 26% in 2026," June 2026)

- AI-focused data centres consumed **155 TWh in 2025**, representing 0.49% of global electricity, with **50% year-over-year growth** (IEA, 2026).
- Worldwide data centre power demand is expected to reach **132 gigawatts in 2026**, up from 104 GW in 2025 (Gartner, 2026).
- The five largest hyperscalers committed **$660-690 billion in capital expenditure in 2026**, with approximately 75% tied to AI infrastructure (Axis Intelligence, "AI Data Center Energy Consumption Statistics," 2026).

### 4.2 AI Training Energy Demands

Individual AI model training runs consume enormous amounts of energy:

| Model | Estimated Training Energy | Equivalent |
|-------|--------------------------|------------|
| GPT-3 (175B params) | ~1,287 MWh | ~120 US homes for 1 year |
| GPT-4 (~280B+ params) | ~50,000 MWh (50 GWh) | San Francisco for ~3 days |
| Llama 3.1 (8B/70B/405B) | ~30,000 MWh (30 GWh) | 39.3M GPU-hours on H100s |
| Current frontier models | 20-25 MW continuous for ~3 months | ~15,000-18,000 MWh per run |

(PatentPC, "AI Energy Consumption," 2025; MIT Technology Review, "We did the math on AI's energy footprint," May 2025; Epoch AI, "How much energy does ChatGPT use?" 2025)

The leading AI supercomputer (xAI's Colossus) grew from **13 MW in 2019 to 280 MW in 2025** -- more than a 20x increase in six years (IEA, 2026).

### 4.3 Could Space Solar Offset Terrestrial Grid Pressure?

Space-based solar power (SBSP) is an attractive concept: solar panels in orbit receive continuous sunlight unaffected by weather, atmosphere, or nighttime. Key considerations:

**Potential advantages:**
- Continuous power generation (no day/night cycle in certain orbits)
- Each satellite can view a quarter of the globe, acting as a "giant interconnector in space" transferring power between regions almost instantaneously (Harvard Technology Review, "The Future of Energy," September 2025).
- SBSP requires **orders of magnitude fewer critical minerals** than terrestrial renewables with equivalent storage (arXiv:2504.05052, "Assess Space-Based Solar Power in European-Scale Power System Decarbonization," 2025).
- Can reduce storage and transmission investment by offsetting temporal and spatial variability of terrestrial wind and solar (WEF, "Why we need space-based solar power," October 2025).

**Critical barriers:**
- **Conversion losses** in beaming power to Earth via microwave or laser substantially reduce the net energy delivered.
- **Launch costs** remain the biggest financial barrier and must drop by orders of magnitude for commercial feasibility (Do the Math, "Space-Based Solar Power," updated).
- **Scale**: delivering meaningful grid-scale power (gigawatts) requires enormous orbital structures far beyond anything yet demonstrated.
- No operational SBSP system exists; the concept remains pre-commercial despite decades of study.

**Verdict:** SBSP could theoretically contribute to grid pressure relief in the 2040s-2050s timeframe if launch costs continue to decline, but it is not a near-term solution. Orbital data centres powered by solar panels for their own use is more feasible than beaming power to Earth, but the scale of infrastructure required is enormous.

### 4.4 Renewable Energy for Terrestrial Data Centres

- Renewables currently supply approximately **27% of data centre electricity globally** (IEA, "Energy supply for AI," 2026).
- The Climate Neutral Data Centre Pact requires signatories (including AWS, Google, Microsoft) to match **75% of electricity with renewables by 2025** and **100% by 2030** on an hourly basis (various sources).
- Renewables for data centres are growing at **22% annually between 2024-2030**, projected to meet nearly **50% of growth in data centre electricity demand** (IEA, 2026).
- Google claims 100% renewable energy match on a global annual basis since 2017, though hourly matching is a more rigorous standard (Google Data Centers, "Operating sustainably").

Terrestrial renewable energy deployment for data centres, while challenging, is advancing more rapidly and more cost-effectively than orbital alternatives.

---

## 5. Regulatory and Legal Framework

### 5.1 FCC Licensing for Mega-Constellations

The FCC is the primary licensing authority for satellite constellations operating in US jurisdiction:

- SpaceX's January 2026 filing for **one million orbital data centre satellites** was accepted for review by the FCC's Space Bureau within five days (SpaceNews, January 2026).
- The FCC imposes **milestone requirements**: typically 50% deployment within six years and 100% within nine years. SpaceX has requested a waiver of these timelines (SpaceNews, 2026).
- The FCC's 2022 orbital debris rules require **5-year post-mission disposal** and **indemnification of the United States** for costs associated with international treaty claims (FCC 22-74, 2022).
- Critics argue the FCC guidelines **fail to require Environmental Assessments** for LEO operations and **do not mandate space situational awareness data sharing** (Runnels, "Protecting Earth and Space Industries from Orbital Debris," *American Business Law Journal*, 2023).

### 5.2 ITU Frequency Coordination Challenges

The International Telecommunication Union (ITU) manages spectrum allocation, facing unprecedented challenges:

- LEO mega-constellations enabling direct smartphone connectivity create **unprecedented spectrum management challenges** (ScienceDirect, "Space safety in the age of LEO constellations," 2025).
- The ITU established **deployment milestones** for non-geosynchronous operators: 10% of satellites within 2 years, 50% within 5 years, 100% within 7 years to retain spectrum rights (SpaceNews, "ITU sets milestones for megaconstellations").
- **WRC-23** reaffirmed EPFD (Equivalent Power Flux Density) as the primary protection mechanism for geostationary networks, with studies on aggregate effects from multiple NGSO systems to conclude by WRC-27 (Frontiers, 2026).
- Proposed solutions include **dynamic spectrum sharing, spectrum sensing, and frequency hopping**, but international coordination remains inadequate for the scale of proposed deployments (ScienceDirect, 2025).

### 5.3 Outer Space Treaty Implications

The 1967 Outer Space Treaty (OST) provides the foundational legal framework:

- Article I declares space the **"province of all mankind"**.
- Article II prohibits **"national appropriation by means of use or occupation"**.
- The de facto occupation of orbital shells by a single nation's commercial constellations is **"arguably in violation"** of these principles (Runnels, *American Business Law Journal*, 2023).
- Article VI makes States **internationally responsible** for national activities in outer space, including by private entities.
- Article VII establishes **launching State liability** for damage caused by space objects.

### 5.4 Liability for Space Debris Damage

The 1972 **Liability Convention** clarifies the OST's Article VII:

- **Absolute liability** for damage caused on Earth or to aircraft in flight by a space object.
- **Fault-based liability** for damage caused in outer space.
- No mechanism for claims between private companies; claims must be made **State-to-State**.
- The FCC now requires licensees to **indemnify the United States** against treaty claims (FCC 22-74, 2022).
- **Satellite insurance premiums for LEO operators have risen substantially since 2023**, with the $6 billion space insurance market facing its "biggest stress test yet" (Insurance Business, 2025).

### 5.5 National Regulations

**United States:**
- FCC 5-year deorbit rule (2022)
- ORBITS Act of 2025: proposed programme for active debris remediation and uniform standards
- No comprehensive national space debris law; regulation is fragmented across FCC, FAA, NOAA, and DoD (ABA, "On Clearing Earth's Orbital Debris," January 2022)

**European Union:**
- EU Space Act draft published June 25, 2025 -- potentially the first comprehensive EU-wide space regulation
- Currently a patchwork of national laws (France, Germany, Luxembourg have sophisticated frameworks; others lag)
- ESA's Zero Debris Charter (voluntary, non-binding)
(Bird & Bird, "Space and Satellite wrap up," 2026)

**China:**
- No comprehensive national space law
- Interim administrative measures on space debris mitigation (2009)
- Dual approach since 2025: encouraging private sector while tightening risk controls
- Three-Body Computing Constellation has launched 12 operational orbital computing satellites
(Lexology, "A general introduction to Space Law in China," 2025)

### 5.6 Astronomy Community Opposition

The scientific community has mounted sustained opposition:

- The IAU CPS provides formal technical recommendations and advocacy at the UN level (IAU, various statements 2019-2026).
- A December 2024 preprint called for formal protection of dark and quiet skies from satellite interference (arXiv:2412.08244).
- A July 2025 paper demonstrated that satellite constellations **already exceed IAU-established brightness limits** (arXiv:2507.00107).
- The **Quiet Skies Report** (December 2025) provided a primer on protecting radio astronomy from mega-constellations (arXiv:2512.00941).

---

## 6. Public and Community Opposition to Terrestrial Data Centres

### 6.1 The Devon, UK Proposal

The most prominent current example is the **850-acre data centre proposal near Great Torrington, Devon**:

- Developer **Xlinks** proposes the largest AI data centre and energy storage facility in the UK on farmland between Torrington, Huntshaw, and Weare Gifford.
- The project: **1.5 GW of AI-optimised compute capacity** with **1.8 GW on-site battery storage**, costing **GBP 13.8 billion** (Farming UK, "GBP 13bn Devon data centre plan delayed amid farmland concerns," 2026).
- The campaign group **"Leave Devon Alone!"** gathered over **23,500 petition signatures** (North Devon Gazette, 2026).
- Hundreds attended a public meeting chaired by MP Sir Geoffrey Cox (North Devon Gazette, 2026).
- Key concerns: **noise, landscape impact, water demand, electricity use, and loss of farmland** within the **North Devon UNESCO Biosphere Reserve** (Tamar Valley Times, "Opposition grows to huge AI data centre in Devon countryside," 2026; BBC News, "Data centre plans spark fury among residents," 2026).
- A local resident stated: **"It's not a Nimby issue. Nobody would want this anywhere because of its size and its implications"** (North Devon Gazette, 2026).
- North Devon Council leader subsequently declared support, creating political tension (BBC News, 2026).

### 6.2 Global Data Centre Opposition

Opposition has become a **structural risk** for the industry:

- **833 active opposition groups** by end of March 2026, up from 396 at end of 2025, spanning **49 US states** (Fortune, "Data center hate is snowballing," June 2026).
- At least **75 data centre projects worth more than $130 billion** delayed or cancelled in Q1 2026 alone (Fortune, 2026).
- An estimated **$98 billion** in projects delayed or blocked in a single quarter of 2025 (Introl, "Data Center Community Opposition," 2026).
- **30-50% of data centre capacity expected in 2026** may not be delivered on schedule (Data Center Frontier, 2026).
- A **500-group coalition** backed by Greenpeace, Friends of the Earth, and the NAACP opposes unfettered construction (Fortune, 2026).
- **About a dozen US states** have introduced data centre construction moratoriums, including New York's one-year pause on large permits (Wikipedia, "Opposition to AI data centers," updated 2026).

**Notable examples worldwide:**

| Location | Details |
|----------|---------|
| **Monterey Park, California** | 45-day moratorium; ~5,000 petition signatures; multilingual outreach campaign |
| **New York State** | One-year legislative pause on large data centre permits |
| **Devon, UK** | 850-acre proposal with 23,500+ petition signatures |
| **Various US locations** | Water use concerns in 40%+ of contested projects |

(Data Center Frontier, "Community Opposition Emerges as New Gatekeeper," 2026; Commons Library, "How to Stop a Data Centre," 2026)

### 6.3 Primary Community Concerns

The most frequently cited concerns in order of prevalence:

1. **Water use** -- mentioned in >40% of contested projects
2. **Energy consumption and electricity rate increases** -- strain on local grids
3. **Noise pollution** -- industrial cooling fans operating 24/7
4. **Land use** -- loss of agricultural land, green spaces
5. **Property values** -- perceived negative impact
6. **Visual impact** -- large industrial facilities in rural areas
7. **Tax incentives** -- data centres receiving large tax breaks while imposing infrastructure costs

### 6.4 Is "Moving to Space" a Legitimate Solution?

The Pixalytics blog post articulates the proposition clearly: **Euwyn Poon (Orbital Compute CEO) argues space solves "three key issues for data centres": solar power, natural cooling, and no local community opposition** (Pixalytics, "Data Centres in Space," 2026).

This framing is problematic for several reasons:

1. **It does not eliminate environmental impact; it redistributes it.** Orbital e-waste, atmospheric aluminium oxide pollution, ozone depletion from launches and reentries, and light pollution affect the entire planet rather than a specific community.

2. **"No local opposition" means "no democratic input."** Outer space currently lacks meaningful community governance. The absence of local residents to object is not the same as the absence of affected parties.

3. **The physical challenges are formidable.** Radiation degrades electronics far faster than on Earth; latency for ground-based users is significant; maintenance and repair are essentially impossible; and the launch emissions to build and replenish orbital data centres are substantial (The Conversation, "Building data centers in space is an intriguing idea on paper, but major engineering challenges must be solved," 2025).

4. **The scale required is unrealistic in the near term.** SpaceX's filing for one million satellites at 100 GW of compute would require launching **one million tonnes of satellites annually** -- far beyond current global launch capacity (SpaceNews, 2026).

5. **It exacerbates the commons problem.** LEO is a shared global resource. Using it to avoid local terrestrial planning processes transfers costs from specific communities to all of humanity through debris risk, light pollution, and atmospheric contamination.

As Asia Times summarised: **"Off-worlding data centers won't solve AI's environmental problems"** -- it transforms them into different, potentially less tractable problems (Asia Times, July 2026).

---

## 7. Conclusions

### The Case Against Orbital Data Centres as Environmental Solution

The evidence across all six research areas points to a consistent conclusion: **space data centres do not solve the environmental problems of terrestrial data centres; they trade known, localised impacts for novel, global, and potentially irreversible ones.**

| Problem | Terrestrial Impact | Orbital Alternative Impact |
|---------|--------------------|---------------------------|
| Water cooling | Significant local water consumption | Eliminated -- but replaced by atmospheric metal oxide pollution |
| Energy use | Grid strain, fossil fuel dependence | Launch emissions, ozone depletion, black carbon |
| Community impact | Noise, land use, visual | Light pollution, debris risk, loss of dark skies |
| E-waste | Recyclable (partially) | Permanently destroyed in atmosphere with chemical byproducts |
| Scalability | Land and power constrained | Orbital space physically constrained (Kessler risk) |
| Regulatory framework | Established planning law | Fragmented international law with weak enforcement |

### Key Risk Assessment

1. **Kessler Syndrome risk is already elevated.** Adding 100,000-1,000,000 satellites to an environment where the debris population already exceeds stability thresholds at most LEO altitudes is a gamble with civilisation-scale consequences.

2. **Atmospheric chemistry effects are poorly understood.** The combination of dramatically increased rocket exhaust (launches) and aluminium oxide deposition (satellite reentries) could delay ozone recovery and alter polar atmospheric circulation in ways current models cannot fully predict.

3. **Regulatory frameworks are inadequate.** The Outer Space Treaty was written for a world of dozens of satellites, not millions. The FCC accepted SpaceX's million-satellite filing within five days, without requiring an environmental assessment.

4. **Terrestrial alternatives exist and are advancing.** Renewable energy for data centres is growing at 22% annually; liquid cooling and air cooling technologies reduce water usage; and distributed edge computing reduces the need for hyperscale facilities.

---

## 8. Sources

### Space Debris and Kessler Syndrome
- [SpaceOrbitals, "Kessler Syndrome: The Cascading Debris Risk in Low Earth Orbit (2026 Reference)"](https://spaceorbitals.com/articles/kessler-syndrome-orbital-debris-2026/)
- [ESA, "Space Environment Report 2025"](https://www.esa.int/Space_Safety/Space_Debris/ESA_Space_Environment_Report_2025)
- [New Space Economy, "Statistics on Space Debris by Orbit as of 2025"](https://newspaceeconomy.ca/2026/01/05/statistics-on-space-debris-by-orbit-as-of-2025/)
- [Orbital Radar, "Space Debris Statistics 2026"](https://orbitalradar.com/space-debris-statistics)
- [FODNews, "ESA: LEO Debris Collision Risk Up 20% in 2026"](https://fodnews.com/esa-space-environment-report-2026-leo-debris-collision-risk/)
- [SpaceNews, "SpaceX files plans for million-satellite orbital data center constellation"](https://spacenews.com/spacex-files-plans-for-million-satellite-orbital-data-center-constellation/)
- [KeepTrack, "The Day Two Satellites Hit Each Other at 26,000 MPH"](https://www.keeptrack.space/deep-dive/iridium-cosmos-collision)
- [Space.com, "Worst Satellite Breakups in History"](https://www.space.com/19450-space-junk-worst-events-anniversaries.html)
- [ResearchGate, "Analysis of the 2007 Chinese ASAT Test"](https://www.researchgate.net/publication/242460823_Analysis_of_the_2007_Chinese_ASAT_Test_and_the_Impact_of_its_Debris_on_the_Space_Environment)
- [European Parliament, "What if orbital debris destroyed satellites?"](https://epthinktank.eu/2025/02/28/what-if-orbital-debris-destroyed-satellites/)
- [BBC Science Focus, "A satellite collision catastrophe is now inevitable, experts warn"](https://www.sciencefocus.com/news/satellite-collisions-disaster)
- [FCC, "FCC Adopts New '5-Year Rule' for Deorbiting Satellites"](https://www.fcc.gov/document/fcc-adopts-new-5-year-rule-deorbiting-satellites-0)
- [NASA, "Deorbit Systems"](https://www.nasa.gov/smallsat-institute/sst-soa/deorbit-systems/)
- [HawkLogic, "FCC 5-Year Rule vs ESA Zero Debris vs 25-Year"](https://hawklogicsystems.com/tools/deorbit-regulations)
- [Insurance Business, "The $6 billion space insurance market faces its biggest stress test yet"](https://www.insurancebusinessmag.com/us/news/breaking-news/the-6-billion-space-insurance-market-faces-its-biggest-stress-test-yet-578992.aspx)

### Light Pollution and Astronomy
- [Space.com, "Starlink satellites: Facts, tracking and impact on astronomy"](https://www.space.com/spacex-starlink-satellites.html)
- [BBC Sky at Night Magazine, "Are we destroying our window to the cosmos?"](https://www.skyatnightmagazine.com/news/satellite-trails-destroying-view-of-night-sky)
- [BBC Sky at Night Magazine, "This is one hour of satellite trails over the world's darkest sky"](https://www.skyatnightmagazine.com/news/eso-study-satellite-trails)
- [Scientific American, "Starlink and Astronomers Are in a Light Pollution Standoff"](https://www.scientificamerican.com/article/starlink-and-astronomers-are-in-a-light-pollution-standoff/)
- [CBC News, "Starlink satellites create light pollution and disrupt radio frequencies"](https://www.cbc.ca/news/science/spacex-starlinks-astronomy-1.7334803)
- [A&A, "The growing impact of unintended Starlink broadband emission on radio astronomy in the SKA-Low frequency range"](https://www.aanda.org/articles/aa/full_html/2025/07/aa54787-25/aa54787-25.html)
- [MNRAS, "Reducing the impact of satellite brightness for astronomy"](https://academic.oup.com/mnras/article/550/1/stag1136/8722194)
- [IAU, "Statement on Satellite Constellations"](https://iauarchive.eso.org/news/announcements/detail/ann19035/)
- [IAU, "Satellite Constellations" theme page](https://iauarchive.eso.org/public/themes/satellite-constellations/)
- [arXiv:2507.00107, "Satellite Constellations Exceed the Limits of Acceptable Brightness Established by the IAU"](https://arxiv.org/pdf/2507.00107)
- [arXiv:2412.08244, "Call to Protect the Dark and Quiet Sky"](https://arxiv.org/pdf/2412.08244)
- [arXiv:2512.00941, "Quiet Skies Report"](https://arxiv.org/pdf/2512.00941)
- [Rubin Observatory, "Impact of Satellite Constellations"](https://project.lsst.org/vera-c-rubin-observatory-%E2%80%93-impact-satellite-constellations)
- [Tyson et al., "Mitigation of LEO Satellite Brightness and Trail Effects on the Rubin Observatory LSST," AJ (2020)](https://iopscience.iop.org/article/10.3847/1538-3881/abba3e)

### Environmental Footprint
- [Space Launch Schedule, "Rocket Launches: Balancing Innovation and Sustainability"](https://www.spacelaunchschedule.com/news/rocket-launch-pollution/)
- [Polytechnique Insights, "Carbon footprint and space activities"](https://www.polytechnique-insights.com/en/columns/space/carbon-footprint-and-space-activities-an-ambiguous-common-ground/)
- [NOAA CSL, "Projected increase in space travel may damage ozone layer" (2022)](https://www.csl.noaa.gov/news/2022/352_0621.html)
- [NOAA CSL, "Within 15 years, plummeting satellites could release enough aluminum to alter winds, temps in the stratosphere" (2025)](https://csl.noaa.gov/news/2025/427_0428.html)
- [Nature, "Near-future rocket launches could slow ozone recovery" (2025)](https://www.nature.com/articles/s41612-025-01098-6)
- [Ryan et al., "Impact of Rocket Launch and Space Debris Air Pollutant Emissions," Earth's Future (2022)](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2021EF002612)
- [Maloney et al., "The Climate and Ozone Impacts of Black Carbon Emissions From Global Rocket Launches," JGR Atmospheres (2022)](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2021JD036373)
- [Undark, "As Rocket Launches Increase, They May Be Polluting the Skies" (April 2026)](https://undark.org/2026/04/06/as-rocket-launches-increase-they-may-be-polluting-the-skies/)
- [Ferreira et al., "Potential Ozone Depletion From Satellite Demise During Atmospheric Reentry," GRL (2024)](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2024GL109280)
- [Science, "Burned-up satellites are polluting the atmosphere" (2024)](https://www.science.org/content/article/burned-satellites-are-polluting-atmosphere)
- [University of Southampton, "First study to examine environmental impact of deorbited satellites" (2024)](https://www.southampton.ac.uk/news/2024/05/environmental-impact-of-deorbited-satellites.page)
- [Scientific American, "Satellite Mega Constellations Could Jeopardize Ozone-Hole Recovery"](https://www.scientificamerican.com/article/satellite-mega-constellations-could-jeopardize-ozone-hole-recovery/)
- [DGTL Infra, "Data Center Water Usage"](https://dgtlinfra.com/data-center-water-usage/)
- [EESI, "Data Centers and Water Consumption"](https://www.eesi.org/articles/view/data-centers-and-water-consumption)
- [Lincoln Institute, "Data Drain: The Land and Water Impacts of the AI Boom"](https://www.lincolninst.edu/publications/land-lines-magazine/articles/land-water-impacts-data-centers/)
- [Congressional Research Service, R48646](https://www.congress.gov/crs-product/R48646)
- [Introl, "Water Usage Efficiency: AI Data Center Cooling"](https://introl.com/blog/water-usage-efficiency-wue-ai-data-center-cooling-guide-2025)

### Energy Comparison
- [IEA, "Data centre electricity use surged in 2025"](https://www.iea.org/news/data-centre-electricity-use-surged-in-2025-even-with-tightening-bottlenecks-driving-a-scramble-for-solutions)
- [IEA, "Key Questions on Energy and AI"](https://www.iea.org/reports/key-questions-on-energy-and-ai/executive-summary)
- [IEA, "Energy supply for AI"](https://www.iea.org/reports/energy-and-ai/energy-supply-for-ai)
- [Gartner, "Data Center Electricity Consumption to Grow 26% in 2026"](https://www.gartner.com/en/newsroom/press-releases/2026-06-10-gartner-says-data-center-electricity-demand-to-grow-26-percent-in-2026)
- [Axis Intelligence, "AI Data Center Energy Consumption Statistics"](https://axis-intelligence.com/ai-data-center-energy-consumption-statistics/)
- [Our World in Data, "How much energy do data centers and artificial intelligence use?"](https://ourworldindata.org/how-much-energy-do-data-centers-and-artificial-intelligence-use)
- [PatentPC, "AI Energy Consumption: How Much Power AI Models Like GPT-4 Are Using"](https://patentpc.com/blog/ai-energy-consumption-how-much-power-ai-models-like-gpt-4-are-using-new-stats)
- [MIT Technology Review, "We did the math on AI's energy footprint" (May 2025)](https://www.technologyreview.com/2025/05/20/1116327/ai-energy-usage-climate-footprint-big-tech/)
- [Epoch AI, "How much energy does ChatGPT use?"](https://epoch.ai/gradient-updates/how-much-energy-does-chatgpt-use)
- [Harvard Technology Review, "The Future of Energy: Unlocking the Potential of Space-Based Solar Power" (September 2025)](https://harvardtechnologyreview.com/2025/09/05/the-future-of-energy-unlocking-the-potential-of-space-based-solar-power/)
- [WEF, "Why we need space-based solar power" (October 2025)](https://www.weforum.org/stories/2025/10/space-based-solar-power-energy-transition/)
- [arXiv:2504.05052, "Assess Space-Based Solar Power in European-Scale Power System Decarbonization"](https://arxiv.org/pdf/2504.05052)

### Regulatory and Legal Framework
- [Runnels, "Protecting Earth and Space Industries from Orbital Debris," American Business Law Journal (2023)](https://onlinelibrary.wiley.com/doi/10.1111/ablj.12221)
- [ABA, "On Clearing Earth's Orbital Debris & Enforcing the Outer Space Treaty" (January 2022)](https://www.americanbar.org/groups/business_law/resources/business-law-today/2022-january/on-clearing-earth-s-orbital-debris/)
- [FCC, "Mitigation of Orbital Debris in the New Space Age" (FCC 22-74)](https://docs.fcc.gov/public/attachments/FCC-22-74A1.pdf)
- [Federal Register, "Space Innovation; Mitigation of Orbital Debris" (August 2024)](https://www.federalregister.gov/documents/2024/08/09/2024-17093/space-innovation-mitigation-of-orbital-debris-in-the-new-space-age)
- [SpaceNews, "ITU sets milestones for megaconstellations"](https://spacenews.com/itu-sets-milestones-for-megaconstellations/)
- [ScienceDirect, "Space safety in the age of LEO constellations" (2025)](https://www.sciencedirect.com/science/article/abs/pii/S2468896725000734)
- [Bird & Bird, "Space and Satellite wrap up -- Legal and regulatory developments in 2025"](https://www.twobirds.com/en/insights/2026/space-and-satellite-wrap-up---legal-and-regulatory-developments-in-2025)
- [Lexology, "A general introduction to Space Law in China"](https://www.lexology.com/library/detail.aspx?g=57881328-e01f-4eab-8026-8f5e5aa36cbf)
- [SpaceNexus, "Space Debris Regulations by Country: A Global Comparison"](https://spacenexus.us/blog/space-debris-regulations-by-country-comparison)
- [Relm Insurance, "Space Insurance Liability, Debris, and Regulatory Compliance"](https://relminsurance.com/space-insurance-liability-debris-and-regulatory-compliance/)

### Terrestrial Data Centre Opposition
- [Pixalytics, "Data Centres in Space"](https://www.pixalytics.com/data-centres-in-space/)
- [Fortune, "Data center hate is snowballing" (June 2026)](https://fortune.com/2026/06/16/data-center-opposition-construction-delays-blocks-report/)
- [Data Center Frontier, "Community Opposition Emerges as New Gatekeeper for AI Data Center Expansion"](https://www.datacenterfrontier.com/site-selection/article/55359925/community-opposition-emerges-as-new-gatekeeper-for-ai-data-center-expansion)
- [Introl, "Data Center Community Opposition: The $64B Financial Risk"](https://introl.com/blog/data-center-community-opposition-64-billion-backlash)
- [Commons Library, "How to Stop a Data Centre"](https://commonslibrary.org/how-to-stop-a-data-centre-tools-for-community-resistance/)
- [Wikipedia, "Opposition to AI data centers"](https://en.wikipedia.org/wiki/Opposition_to_AI_data_centers)
- [North Devon Gazette, "Devon data centre open days pushed back as petition gains 23,000 signatures"](https://www.northdevongazette.co.uk/news/devon-data-centre-open-days-pushed-back-as-petition-gains-23000-signatures-8786644)
- [Tamar Valley Times, "Opposition grows to huge AI data centre in Devon countryside"](https://www.tamarvalleytimes.co.uk/news/opposition-grows-to-huge-ai-data-centre-in-devon-countryside-922035)
- [Farming UK, "GBP 13bn Devon data centre plan delayed amid farmland concerns"](https://www.farminguk.com/news/-13bn-devon-data-centre-plan-delayed-amid-farmland-concerns_68796.html)
- [BBC News, "Data centre plans spark fury among residents"](https://feeds.bbci.co.uk/news/articles/c4nn52nvvljo)

### Orbital Data Centre Proposals
- [Introl, "Orbital Data Center Race 2026"](https://introl.com/blog/orbital-data-centers-space-computing-race-2026)
- [Introl, "First Orbital Data Center Nodes Reach Space"](https://introl.com/blog/orbital-data-center-nodes-launch-space-computing-infrastructure-january-2026)
- [Axiom Space, "Orbital Data Centers"](https://www.axiomspace.com/orbital-data-center)
- [The Conversation, "Building data centers in space is an intriguing idea on paper"](https://theconversation.com/building-data-centers-in-space-is-an-intriguing-idea-on-paper-but-major-engineering-challenges-must-be-solved-284053)
- [Asia Times, "Off-worlding data centers won't solve AI's environmental problems" (July 2026)](https://asiatimes.com/2026/07/off-worlding-data-centers-wont-solve-ais-environmental-problems/)
- [Carbon Trust, "Data centres in space: Leave the planet to save the planet?"](https://www.carbontrust.com/news-and-insights/insights/data-centres-in-space-leave-the-planet-to-save-the-planet)
- [Fortune, "Google CEO Sundar Pichai: Data centers in space will be the new normal"](https://fortune.com/article/what-is-google-ceo-sundar-pichai-timeline-ai-data-centers-in-space/)
