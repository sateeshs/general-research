# Companies and Initiatives Building Data Centres in Space (2024-2026)

**Research Date:** July 2026
**Scope:** Comprehensive survey of commercial ventures, government programs, and technical architectures for orbital computing infrastructure.

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Orbital Inc](#1-orbital-inc)
3. [SpaceX / Starmind](#2-spacex--starmind)
4. [Blue Origin / Project Sunrise](#3-blue-origin--project-sunrise)
5. [Starcloud (formerly Lumen Orbit)](#4-starcloud-formerly-lumen-orbit)
6. [Google / Project Suncatcher](#5-google--project-suncatcher)
7. [Axiom Space](#6-axiom-space)
8. [Microsoft, AWS, and Major Cloud Providers](#7-microsoft-aws-and-major-cloud-providers)
9. [China's Orbital Computing Programs](#8-chinas-orbital-computing-programs)
10. [European Initiatives (ESA ASCEND)](#9-european-initiatives-esa-ascend)
11. [Other Companies and Government Programs](#10-other-companies-and-government-programs)
12. [Satellite Count Context](#11-satellite-count-context)
13. [Comparative Analysis](#12-comparative-analysis)
14. [Sources](#sources)

---

## Executive Summary

The orbital data centre industry has emerged as one of the most capital-intensive and ambitious sectors in the space economy between 2024 and 2026. Driven by insatiable AI compute demand, terrestrial power grid constraints, and falling launch costs, at least eight major entities have filed plans or launched prototypes for space-based computing infrastructure. The combined FCC filings alone propose over 1.2 million satellites dedicated to orbital computing. Key milestones include:

- **SpaceX** filed for up to 1 million compute satellites (January 2026), confirmed under the name "Starmind"
- **Starcloud** (formerly Lumen Orbit) launched the first GPU satellite (November 2025) and reached unicorn status ($1.1B valuation) within 17 months of Y Combinator graduation
- **Blue Origin** filed for 51,600 satellites under "Project Sunrise" (March 2026)
- **Orbital Inc** filed for 100,000 satellites targeting 10 GW of compute (June 2026)
- **Axiom Space** deployed the first orbital data centre nodes to LEO (January 2026)
- **Google** announced Project Suncatcher for 81-satellite orbital TPU clusters (late 2025)
- **China** launched 12 AI satellites as part of its Three-Body Computing Constellation (May 2025) with plans for 1,000 POPS orbital supercomputer
- **ESA** continues the ASCEND program with a 2026 demonstration mission and 300 million euro budget

---

## 1. Orbital Inc

| Attribute | Detail |
|-----------|--------|
| **Official Name** | Orbital (formerly referred to as Orbital Compute Inc) |
| **Website** | [orbital.inc](https://orbital.inc/) |
| **Founded** | Early 2026 (emerged from a16z Speedrun in May 2026) |
| **Headquarters** | Los Angeles, California |
| **Founder/CEO** | Euwyn Poon |
| **Funding** | $5 million pre-seed (oversubscribed) |
| **Lead Investor** | a16z Speedrun |
| **Valuation** | Not publicly disclosed |

### Leadership

**Euwyn Poon** is a Cornell-educated engineer and lawyer who previously founded Spin, a micromobility company that deployed hundreds of thousands of electric vehicles across 100+ cities and scaled to over $100 million in revenue before being acquired by Ford in 2018 for a reported $100 million. The team of approximately a dozen people in Los Angeles includes engineers with experience at Amazon LEO (Kuiper), SpaceX, and Northrop Grumman.

> *Sources: [TechCrunch, June 2026](https://techcrunch.com/2026/06/09/how-an-e-scooter-founder-raised-5-million-to-build-space-data-centers/); [Citybiz](https://www.citybiz.co/article/858361/euwyn-poons-orbital-raises-5m-to-build-data-centers-in-space/); [Forbes, April 2026](https://www.forbes.com/sites/davidprosser/2026/04/14/why-orbital-believes-space-is-the-next-frontier-in-the-ai-revolution/)*

### Technical Architecture: The Orbital Datacenter System

**Per-Satellite Specifications:**

| Parameter | Value |
|-----------|-------|
| Dry mass | 1.5-2.5 metric tons (approximately 2 tons nominal) |
| Total span | ~100 meters tip-to-tip |
| Solar array power | 100 kilowatts |
| Solar array size | Roughly the size of a tennis court |
| Compute payload | Small cluster of NVIDIA Space-1 Vera Rubin GPUs (full satellite); single NVIDIA Blackwell GPU (pathfinder) |
| Cooling | Passive radiative cooling into space vacuum (~3 K) |
| Radiator panels | Comparable size to solar panels |

Each satellite functions as "a flying, high-density server rack." The solar arrays exploit the 1,361 W/m^2 solar irradiance in LEO, which Orbital claims is more than 5x the energy density of ground-based solar. Heat rejection occurs at zero operating cost through radiation into space's near-absolute-zero thermal environment.

**Regarding the "~8 servers per satellite" claim:** This specific figure does not appear in any Orbital press release, FCC filing summary, or technical disclosure found during research. What is confirmed is that each satellite carries "a small cluster" of NVIDIA GPUs in a "high-density server rack" configuration. The pathfinder mission carries only a single GPU. The full Orbital-1 satellite GPU/server count has not been publicly disclosed.

> *Sources: [Interesting Engineering](https://interestingengineering.com/space/us-firm-files-fcc-application-for-100000-satellite-data-center-constellation); [IEEE Spectrum, May 2026](https://spectrum.ieee.org/orbital-inference-data-center); [orbital.inc](https://orbital.inc/)*

### FCC Filing Details

- **Filing date:** June 24, 2026
- **Satellite count:** Up to 100,000
- **Orbit type:** Sun-synchronous
- **Altitude range:** 500-850 km
- **Total compute power:** 10 GW (at full constellation)

The 10 GW figure is described as equivalent to "the total new electricity capacity added to the entire United States power grid last year." Orbital is the second entity to file for an orbital data centre constellation in 2026, following SpaceX's January application.

**Is 10 GW realistic?** At 100 kW per satellite x 100,000 satellites = 10 GW mathematically. Whether 100,000 satellites can actually be manufactured, launched, and maintained is another question entirely. The constellation would require thousands of launches over many years and represents an order of magnitude beyond anything deployed to date. For comparison, the entire Starlink constellation (10,700+ satellites) took roughly 5 years to build.

> *Sources: [SpaceNews](https://spacenews.com/orbital-files-plans-for-100000-orbital-data-centers/); [MLQ News](https://mlq.ai/news/orbital-compute-files-fcc-application-for-100000-satellite-10gw-space-data-center-constellation/)*

### Timeline and Current Progress

| Date | Milestone | Status |
|------|-----------|--------|
| May 2026 | Emerged from a16z Speedrun | Completed |
| June 2026 | $5M pre-seed closed | Completed |
| June 2026 | FCC application filed | Filed, under review |
| 2026 | Satellite design finalization | In progress |
| 2026 | Factory-1 R&D facility (LA South Bay) | Opening soon |
| April 2027 | Pathfinder mission: single GPU on SpaceX Falcon 9 | Planned |
| 2028 | Orbital-1: first purpose-built satellite | Planned |
| Future | 100,000-satellite constellation | Aspirational |

### Investors and Partners

**Investors:** a16z Speedrun (lead), Basis Set, Human Element, Wayfinder Ventures, Antler, Anti Fund, Ascent Venture Partners, Rubik Ventures, Zero Knowledge Ventures, LYVC, Feld Ventures, New Legacy, FNDR, UpHonest Capital, Asterisk.

**Partners:** NVIDIA (Inception Program, providing Space-1 Vera Rubin GPUs and Blackwell chips), SpaceX (launch provider).

> *Sources: [SiliconANGLE, April 2026](https://siliconangle.com/2026/04/14/ai-satellite-constellation-startup-orbital-gets-funded-andreessen-horowitz-verify-space-based-data-center-concept/); [orbital.inc press release](https://orbital.inc/press/orbital-raises-5m-preseed.html)*

---

## 2. SpaceX / Starmind

| Attribute | Detail |
|-----------|--------|
| **Project Name** | Starmind (officially confirmed June 24, 2026) |
| **Parent Company** | SpaceX / Space Exploration Holdings (merged with xAI in February 2026) |
| **Headquarters** | Hawthorne, California |
| **Founded** | SpaceX: 2002; xAI: 2023; Starmind project: 2025-2026 |
| **Funding** | Internal (SpaceX valued at $350B+) |

### What is Starmind?

Starmind is a planned constellation of up to **1 million** satellite data centres designed to run AI inference directly in low Earth orbit. Unlike Starlink (a telecommunications network), Starmind satellites process data in space and relay computed outputs back to Earth. The architecture uses high-bandwidth optical inter-satellite links and integrates with existing Starlink infrastructure for ground communication.

The name "Starmind" was first identified in mid-June 2026 when public intellectual property registries showed a trademark filing by SpaceX subsidiary xAI. On June 24, 2026, Elon Musk confirmed via X (formerly Twitter) that Starmind is the official name.

> *Sources: [Gear Musk, June 2026](https://gearmusk.com/2026/06/24/named-starmind-ai-satellite/); [Motley Fool, July 2026](https://www.fool.com/investing/2026/07/16/elon-musk-spacex-merge-xai-orbital-data-center/)*

### SpaceX-xAI Merger Context

SpaceX acquired xAI in **February 2026**, bringing xAI's AI models (Grok) and engineering talent under the same corporate umbrella as SpaceX's satellite manufacturing and launch capabilities. Starmind represents the convergence of these two entities' core competencies: xAI provides the AI models and chips, SpaceX provides satellite manufacturing and launch infrastructure.

> *Source: [Motley Fool, July 2026](https://www.fool.com/investing/2026/07/16/elon-musk-spacex-merge-xai-orbital-data-center/)*

### FCC Application

- **Filing date:** January 30, 2026
- **FCC acceptance:** February 2026 (accepted for public review)
- **Satellite count:** Up to 1,000,000
- **Orbit type:** Non-geostationary (NGSO), optimized for high-capacity computing
- **Purpose:** "Orbital data center operations"

This was the first FCC filing for an orbital data centre constellation, predating all others in the 2026 wave.

> *Sources: [CryptoBriefing](https://cryptobriefing.com/spacex-starmind-ai-satellite-network/); [DataCenterDynamics](https://www.datacenterdynamics.com/en/news/spacex-files-for-million-satellite-orbital-ai-data-center-megaconstellation/)*

### AI1 Satellite Specifications

| Parameter | Value |
|-----------|-------|
| Designation | AI1 |
| Wingspan | 70 meters (230 feet) tip-to-tip |
| Height (deployed) | 20 meters (66 feet) |
| Peak computing power | 150 kilowatts |
| Average compute output | 120 kilowatts |
| Solar panel rating | 150 kilowatts total |
| Output density | 250 watts per square meter |
| AI chips | Custom chips running xAI's Grok models |
| Cooling | Radiative cooling in vacuum |
| Power source | Solar |

The AI1 is described as wider than a Boeing 747 and functions as an "orbiting server rack."

> *Sources: [ExplainX](https://explainx.ai/blog/spacex-ai1-solar-orbital-datacenter-space-compute-2026); [Quartz](https://qz.com/spacex-ai1-satellite-orbital-data-center-ipo-061026); [The Robotics Media](https://theroboticsmedia.com/article/spacex-starmind-ai1-orbital-data-center-constellation)*

### Timeline

| Date | Milestone | Status |
|------|-----------|--------|
| January 2026 | FCC application filed | Completed |
| February 2026 | FCC accepted for public review | Completed |
| February 2026 | xAI acquisition completed | Completed |
| June 2026 | "Starmind" name confirmed | Completed |
| Early 2027 | Two prototype AI1 satellites launch | Planned |
| Late 2027 | Production ramp to ~1 GW orbital compute/year | Planned |
| 2028 | Commercial operation begins | Planned |

### Starlink as Infrastructure

Starlink's existing constellation of 10,700+ active satellites provides the communications backbone for Starmind. The optical inter-satellite links developed for Starlink Gen2 satellites serve as the data relay network for Starmind's compute outputs. This gives SpaceX a significant infrastructure advantage over competitors who must build both compute and communications networks from scratch.

---

## 3. Blue Origin / Project Sunrise

| Attribute | Detail |
|-----------|--------|
| **Project Name** | Project Sunrise |
| **Parent Company** | Blue Origin (owned by Jeff Bezos) |
| **Headquarters** | Kent, Washington |
| **Founded** | Blue Origin: 2000; Project Sunrise: 2026 |
| **Funding** | Internal (Bezos personal funding, historically $1B+/year) |

### Constellation Plans

On **March 19, 2026**, Blue Origin filed with the FCC seeking authorization to launch and operate Project Sunrise, a constellation of up to **51,600** satellites providing in-space computing services.

| Parameter | Value |
|-----------|-------|
| Satellite count | Up to 51,600 |
| Orbit type | Sun-synchronous |
| Altitude range | 500-1,800 km |
| Inter-satellite links | Optical |
| Power source | Solar (continuous sun exposure) |
| Purpose | In-space AI computing services |

> *Sources: [SpaceNews](https://spacenews.com/blue-origin-joins-the-orbital-data-center-race/); [GeekWire](https://www.geekwire.com/2026/blue-origin-data-center-space-race-project-sunrise/); [Data Centre Magazine](https://datacentremagazine.com/news/project-sunrise-blue-origin-data-centre-space-race)*

### Integration with TeraWave

Project Sunrise complements Blue Origin's previously announced **TeraWave** communications constellation of 5,408 satellites. TeraWave provides ultra-high-speed connectivity for:
- Project Sunrise compute satellites
- Terrestrial data centres
- Large-scale enterprises
- Government customers

The combined system (51,600 + 5,408 = ~57,000 satellites) represents Blue Origin's full orbital infrastructure vision.

> *Source: [Blue Origin FCC filing summary, Substack](https://isoclive.substack.com/p/blue-origin-fcc)*

### Current Status

Blue Origin's orbital data centre plans are at the **regulatory filing stage**. No satellite prototypes have been publicly announced or launched. Blue Origin does have operational launch vehicles (New Glenn completed its first orbital flight in early 2025), giving it an in-house launch capability advantage shared only with SpaceX among orbital data centre competitors. However, no specific timeline for prototype deployment has been disclosed.

---

## 4. Starcloud (formerly Lumen Orbit)

| Attribute | Detail |
|-----------|--------|
| **Current Name** | Starcloud |
| **Previous Name** | Lumen Orbit |
| **Founded** | 2024 |
| **Headquarters** | Redmond, Washington (Seattle area) |
| **CEO/Co-Founder** | Philip Johnston (former McKinsey associate) |
| **CTO/Co-Founder** | Ezra Feilden (ex-Oxford Space Systems, Airbus Defence and Space) |
| **Chief Engineer/Co-Founder** | Adi Oltean (ex-SpaceX Starlink, principal software engineer) |
| **Total Funding** | $200+ million |
| **Valuation** | $1.1 billion (March 2026) |
| **Y Combinator** | Summer 2024 cohort |

### Funding History

| Round | Amount | Lead | Date |
|-------|--------|------|------|
| Pre-seed | $2.4M | Various | March 2024 |
| Seed | $11M | NFX | October-December 2024 |
| Additional | $10M | NFX | Early 2025 (rebrand period) |
| Series A | $170M | Benchmark, EQT Ventures | March 2026 |
| **Total** | **$200M+** | | |

Other investors: Y Combinator, FUSE Ventures, Soma Capital, 776 Ventures, Manhattan West, Monolith Power Systems, Nebular, Adjacent. Angel investors include former Boeing CEO Dennis Muilenburg. Scout funds from Andreessen Horowitz and Sequoia also participated in earlier rounds.

Starcloud became the **fastest Y Combinator graduate to reach unicorn status** ($1.1B valuation), achieving this milestone just 17 months after completing the program.

> *Sources: [GeekWire, December 2024](https://www.geekwire.com/2024/lumen-orbit-a-seattle-area-startup-that-wants-to-put-data-centers-in-space-raises-11m/); [TechCrunch, October 2024](https://techcrunch.com/2024/10/24/lumen-orbit-closed-one-of-the-biggest-rounds-from-y-combinators-last-cohort/); [SpaceNews, March 2026](https://spacenews.com/starcloud-achieves-unicorn-status-with-170-million-raise-for-orbital-data-centers/); [TechCrunch, March 2026](https://techcrunch.com/2026/03/30/starcloud-raises-170-million-series-ato-build-data-centers-in-space)*

### Technical Approach

Starcloud builds orbital data centres composed of modular **pods** that hold compute hardware and attach to large solar panels in clusters. The business model focuses on **in-space edge processing**: other satellites send raw data to the Starcloud constellation, which runs AI models on on-board GPUs to extract insights, then downlinks the processed results.

**Starcloud-1 Satellite (launched November 2025):**
- Mass: 60 kg
- Compute: Single NVIDIA H100 GPU
- Significance: "100x more powerful than has ever been operated in space before"
- Demonstrated capability: Ran a version of Google's Gemini AI model in orbit
- Launch: SpaceX rideshare mission
- Time from founding to launch: 21 months

> *Sources: [SpaceNews](https://spacenews.com/starcloud-files-plans-for-88000-satellite-constellation/); [DataCenterDynamics](https://www.datacenterdynamics.com/en/news/lumen-orbit-rebrands-to-starcloud-raises-another-10m-for-in-orbit-data-centers/)*

### FCC Filing

- **Filing accepted:** March 13, 2026
- **Satellite count:** Up to 88,000
- **Orbit:** Sun-synchronous, 600-850 km altitude
- **Purpose:** Orbital data centres for AI and other applications

### Timeline

| Date | Milestone | Status |
|------|-----------|--------|
| 2024 | Founded as Lumen Orbit | Completed |
| Summer 2024 | Y Combinator graduation | Completed |
| November 2025 | Starcloud-1 launched (H100 GPU) | Completed |
| Early 2025 | Rebrand to Starcloud | Completed |
| March 2026 | FCC filing for 88,000 satellites | Filed |
| March 2026 | $1.1B unicorn valuation | Achieved |
| October 2026 | Starcloud-2 launch (100x power generation of first) | Planned |
| End of decade | Multi-gigawatt compute clusters | Goal |

---

## 5. Google / Project Suncatcher

| Attribute | Detail |
|-----------|--------|
| **Project Name** | Project Suncatcher |
| **Parent Company** | Alphabet / Google |
| **Announced** | Late 2025 |
| **Satellite Manufacturer** | Planet Labs |
| **Launch Provider** | In discussions with SpaceX |

### Technical Concept

Google's approach differs from the constellation-scale filings of SpaceX, Blue Origin, and others. Project Suncatcher envisions **81 satellites** within a 1 km radius formation operating as a single distributed data centre.

| Parameter | Value |
|-----------|-------|
| Satellite count | 81 (cluster formation) |
| Formation radius | ~1 km |
| Inter-satellite spacing | 100-200 meters |
| Orbit | Sun-synchronous LEO |
| Inter-satellite links | Ultra-high-bandwidth optical |
| Compute hardware | Google custom Tensor Processing Units (TPUs) |

The cluster operates as a single, distributed data centre connected by optical links, rather than as independent compute nodes.

### Current Status

- **Late 2025:** Concept publicly outlined with small prototype satellite designs
- **Testing focus:** Power generation, thermal management, radiation exposure, communications latency
- **2027 target:** Planet Labs to build and deploy two demonstration spacecraft
- **SpaceX discussions:** Google is in talks with SpaceX for launch services

> *Sources: [Forbes, November 2025](https://www.forbes.com/sites/anishasircar/2025/11/11/google-unveils-project-suncatcher-to-run-ai-on-solar-satellites-in-orbit/); [DataCenterDynamics](https://www.datacenterdynamics.com/en/news/google-in-talks-with-spacex-regarding-suncatcher-orbital-data-center-project/); [Space Explored, January 2026](https://spaceexplored.com/2026/01/05/planet-and-google-explore-computing-in-orbit/)*

---

## 6. Axiom Space

| Attribute | Detail |
|-----------|--------|
| **Company** | Axiom Space |
| **Headquarters** | Houston, Texas |
| **Founded** | 2016 |
| **Focus** | Commercial space station + orbital data centres |
| **Key Achievement** | First entity to deploy operational orbital data centre nodes |

### Milestones

Axiom Space holds the distinction of being the **first company to actually deploy orbital data centre hardware in space**.

| Date | Milestone |
|------|-----------|
| 2022 | AWS Snowcone device operated on ISS (Ax-1 Mission) |
| Fall 2025 | AxDCU-1 prototype deployed to ISS |
| January 11, 2026 | First two dedicated ODC nodes launched to LEO |
| 2027 | ODC T1 data centre deployment (planned) |
| 2030+ | Network expansion to megawatt-scale capacity |

### Technical Specifications

| Parameter | Value |
|-----------|-------|
| Optical link capacity | 2.5 GB/s |
| Standards | SDA Tranche 1 optical communication |
| Hardware | Commercial off-the-shelf (COTS) |
| OS | Industry-standard containerized systems |
| Power | Solar energy, modular and scalable |
| Software | Red Hat Device Edge (AxDCU-1) |

### Capabilities

- Real-time in-orbit data processing and analytics
- AI/ML model deployment
- Autonomous decision-making during ground connectivity loss
- Over-the-air software updates
- Multi-source data fusion
- Cloud computing, AI/ML, data fusion, space cybersecurity

### Partners

- **AWS** (Snowcone deployment, 2022)
- **Quantinuum** (quantum-secure communications)
- **Kepler Communications** (optical relay network)
- **Skyloom Global** (optical inter-satellite links)
- **Red Hat** (Device Edge software)
- **Redwire** (ROSA solar arrays for Axiom Station)

### Customers

National security and government entities, space agencies, private astronauts, commercial satellite constellations.

> *Sources: [Axiom Space](https://www.axiomspace.com/orbital-data-center); [Axiom Press Release](https://www.axiomspace.com/release/axiom-space-to-launch-orbital-data-center-nodes-to-support-national-security-commercial-international-customers); [ISS National Lab](https://issnationallab.org/press-releases/orbital-data-center-launching-to-iss-to-advance-space-computing/)*

---

## 7. Microsoft, AWS, and Major Cloud Providers

### Microsoft Azure Space

Microsoft has not filed for its own orbital compute constellation but is actively building the ground segment and partnerships:

- **Azure Orbital Ground Station:** Connects ground-based Azure data centres to satellites via a global network of ground stations
- **SpaceX Partnership:** Uses Starlink to bring broadband connectivity to Azure Modular Data Centres in remote areas
- **Additional Partners:** KSAT, ViaSat, US Electrodynamics (ground stations); SES (satellite broadband)
- **Azure Modular Data Centre:** Portable, ruggedized containers that can operate in extreme environments, connected via satellite

Microsoft's strategy is to **connect terrestrial cloud to space assets** rather than placing compute in orbit.

> *Sources: [DataCenterKnowledge](https://www.datacenterknowledge.com/cloud/microsoft-pushes-azure-cloud-services-into-new-frontier-space); [DataCenterFrontier](https://www.datacenterfrontier.com/cloud/article/11428715/azure-orbital-will-connect-microsoft8217s-cloud-data-centers-to-space-satellites)*

### Amazon / AWS

- **AWS Ground Station:** Service connecting Earth-based workloads to satellite data
- **AWS Space Accelerator:** Program supporting space-related startups
- **Amazon Leo (formerly Project Kuiper):** A communications constellation (not compute), with 394+ satellites launched as of mid-2026
- **No orbital compute filing:** Amazon has not filed for orbital data centre satellites; its space focus remains connectivity via Amazon Leo

> *Source: [DataCenterFrontier](https://www.datacenterfrontier.com/cloud/article/11428161/the-space-cloud-satellite-strategies-for-aws-google-and-microsoft)*

### Summary

Among hyperscale cloud providers, **only Google (via Project Suncatcher) has announced plans to put actual compute hardware in orbit**. Microsoft and AWS are focused on connecting terrestrial cloud to satellite networks.

---

## 8. China's Orbital Computing Programs

China has taken a coordinated, state-directed approach to orbital computing, contrasting with the venture-backed startup model dominant in the United States.

### Three-Body Computing Constellation

| Attribute | Detail |
|-----------|--------|
| **Led by** | Zhejiang Lab |
| **First launch** | May 14, 2025 (12 satellites) |
| **Current computing power** | 5 POPS (peta operations per second) |
| **2027 target** | 100 satellites |
| **Ultimate goal** | 1,000 POPS orbital supercomputer |
| **Features** | Inter-satellite laser links, in-orbit data processing |

### ADAspace "Star Compute" Initiative

| Attribute | Detail |
|-----------|--------|
| **Company** | ADAspace |
| **Total planned satellites** | 2,800 |
| **Breakdown** | 2,400 inference satellites + 400 training satellites |
| **Status** | Second and third satellite groups in production, orbital deployment scheduled for 2026 |

### GuoXing Aerospace

In January 2026, GuoXing Aerospace deployed a general-purpose AI model aboard orbiting satellites and ran experiments where prompts were sent from Earth, processed onboard, and returned to ground stations in approximately 2 minutes.

### National Coordination

In 2026, China placed more than 100 space-computing organizations under a new **Beijing committee**, tying the orbital computing program to the 15th Five-Year Plan (2026-2030). The plan emphasizes a space-air-ground network combining communications, internet connectivity, positioning, and remote sensing. China's total investment in orbital data centre infrastructure is estimated at **$8.4 billion**.

> *Sources: [SpaceDaily](https://spacedaily.com/sd-in-2026-china-put-more-than-100-space-computing-organizations-under-a-new-beijing-committee-tying-12-ai-satellites-and-a-1000-pops-orbital-supercomputer-plan-to-the-five-year-plan-and-the-still/); [Xinhua, April 2026](https://english.news.cn/20260425/b4368923827e4988af1bd030dd01d9cc/c.html); [CarbonCredits](https://carboncredits.com/chinas-8-4b-orbital-data-center-push-sets-up-space-based-ai-showdown-with-spacex/); [Tom's Hardware](https://www.tomshardware.com/tech-industry/data-centers/china-unifies-tech-sector-to-build-grid-free-orbiting-satellite-ai-data-centers-challenging-elon-musks-spacex-beijings-forced-chip-and-satellite-alliance-announced-a-week-before-musks-ai1-reveal); [China Daily, December 2025](https://www.chinadaily.com.cn/a/202512/05/WS69323706a310d6866eb2d03e.html)*

---

## 9. European Initiatives (ESA ASCEND)

### ASCEND Program

| Attribute | Detail |
|-----------|--------|
| **Full Name** | Advanced Space Cloud for European Net Zero Emissions and Data Sovereignty |
| **Funding** | 300 million euros (through 2027) |
| **Funder** | European Commission (Horizon Europe program) |
| **Lead Contractor** | Thales Alenia Space |
| **Target** | 1 GW by 2050 |
| **ROI estimate** | Several hundred billion euros by 2050 |

### Key Features

- **Demonstration mission:** 2026 (deploying small-scale orbital data centre module)
- **Assembly method:** Modular infrastructures assembled in orbit using robotic technologies (EROSS IOD demonstrator)
- **Environmental angle:** No water cooling required; supports European Green Deal carbon neutrality goals
- **Sovereignty:** Strengthens European digital sovereignty and data independence
- **Feasibility:** Thales Alenia Space has published results confirming economic viability

### Other European Activities

- **ReOrbit** (Finland): Working with ESA's InCubed program on satellite launch for secure space-to-space and space-to-ground data transfer (2025)

> *Sources: [Thales Alenia Space](https://www.thalesaleniaspace.com/en/press-releases/thales-alenia-space-reveals-results-ascend-feasibility-study-space-data-centers-0); [Forbes Council](https://www.forbes.com/councils/forbestechcouncil/2026/04/14/the-orbital-pivot-why-your-next-data-center-wont-be-on-earth/); [Intelligent Data Centres](https://www.intelligentdatacentres.com/2024/07/26/beyond-earth-the-next-frontier-for-data-centre-innovation/)*

---

## 10. Other Companies and Government Programs

### Redwire

Redwire is not developing its own orbital data centre constellation but is a key **supplier** to the ecosystem. It was awarded a contract in September 2025 to provide roll-out solar arrays (ROSA) for Axiom Station's first commercial space station module, which will host orbital data centre infrastructure.

> *Source: [AINvest](https://www.ainvest.com/news/redwire-role-emerging-space-data-center-ecosystem-assessing-growth-potential-cash-burn-valuation-concerns-2512/)*

### Government Programs

| Agency | Program/Activity | Budget/Status |
|--------|-----------------|---------------|
| **NASA** | Commercial partnerships, technology development contracts | $200M in contracts |
| **DARPA** | Multiple programs exploring space-based AI for defense | Active, details classified |
| **ESA** | ASCEND program (see above) | 300M euros |
| **JAXA** | Space-based AI processing in strategic roadmap | Planning stage |
| **U.S. DoD** | Incorporated space-based AI into strategic roadmaps | Active |

NASA, NVIDIA, IBM, and Hewlett Packard Enterprise are collaborating on deploying scalable, radiation-hardened data centres in space capable of handling AI model training, real-time analytics, and cloud computing.

> *Sources: [Introl Blog](https://introl.com/blog/orbital-data-centers-space-computing-race-2026); [Cutter Consortium](https://www.cutter.com/article/orbit-data-centers-mapping-leaders-space-ai-computing)*

---

## 11. Satellite Count Context

### Total Satellites in Orbit (mid-2026)

| Metric | Value |
|--------|-------|
| Total active satellites | 14,500+ |
| Total Starlink payloads in orbit | 10,775 |
| Active Starlinks | 10,759 |
| Total Starlinks ever launched | 11,529 |
| Starlink share of all active satellites | ~59% |

> *Sources: [EarthSky](https://earthsky.org/spaceflight/10000-starlink-satellites-orbiting-earth-counting/); [Orbital Radar](https://orbitalradar.com/how-many-satellites-in-orbit); [HighSpeedInternet.com](https://www.highspeedinternet.com/resources/how-many-starlink-satellites-are-in-orbit-june-5-2026)*

### Amazon Leo (formerly Kuiper)

| Metric | Value |
|--------|-------|
| Production satellites launched | 394+ (across 19 missions) |
| FCC deadline | 1,618 satellites by July 30, 2026 |
| Authorized constellation | 3,236 satellites (original) |
| Approved expansion | 4,500 additional (total: 7,727) |
| Status | Extension requested; behind schedule |
| Rebrand | Renamed from Project Kuiper to Amazon Leo (November 2025) |
| Rank | Third-largest constellation in orbit |

> *Sources: [KeepTrack](https://keeptrack.space/deep-dive/amazon-leo-progress-2026); [Orbital Radar](https://orbitalradar.com/how-many-kuiper-satellites); [HighSpeedInternet.com](https://www.highspeedinternet.com/resources/when-will-project-kuiper-be-available)*

### Launch Growth Rate

| Year | Launches | Satellites Deployed |
|------|----------|-------------------|
| 2024 | 259 (record) | 2,695 |
| 2025 | 296 (record) | 4,434 |

The satellite launch vehicle market grew from $20.21B (2025) to $22.74B (2026), a CAGR of 12.6%.

> *Sources: [SIA Annual Report](https://sia.org/historic-number-of-launches-powers-commercial-satellite-industry-growth-satellite-industry-association-releases-the-28th-annual-state-of-the-satellite-industry-report/); [Sentinel Mission](https://sentinelmission.org/statistics/space-industry-statistics/)*

### Scale of Proposed Orbital Data Centres vs. Current Satellite Population

The combined FCC filings for orbital data centre constellations total approximately **1,239,600 satellites**:

| Company | Filed Satellite Count |
|---------|--------------------|
| SpaceX (Starmind) | 1,000,000 |
| Starcloud | 88,000 |
| Orbital | 100,000 |
| Blue Origin (Project Sunrise) | 51,600 |
| **Total** | **~1,239,600** |

This is **85x** the current total active satellite population of ~14,500. Even if only a fraction are deployed, it would fundamentally transform the orbital environment.

---

## 12. Comparative Analysis

### Company Comparison Table

| Company | Filed Satellites | Funding | First Hardware in Orbit | Orbit (km) | Power/Satellite | GPU/Chip |
|---------|-----------------|---------|------------------------|------------|----------------|----------|
| SpaceX (Starmind) | 1,000,000 | Internal | 2027 (planned) | LEO (NGSO) | 150 kW | xAI custom (Grok) |
| Starcloud | 88,000 | $200M+ | Nov 2025 (Starcloud-1) | 600-850 | TBD (60kg sat) | NVIDIA H100 |
| Orbital | 100,000 | $5M | 2027 (planned) | 500-850 | 100 kW | NVIDIA Vera Rubin / Blackwell |
| Blue Origin | 51,600 | Internal | None yet | 500-1,800 | TBD | TBD |
| Google (Suncatcher) | 81 | Internal | 2027 (planned) | LEO (SSO) | TBD | Google TPUs |
| Axiom Space | Modular | Private | Jan 2026 (ODC nodes) | ISS orbit (~400) | Solar/modular | COTS |
| China (Three-Body) | 100+ (2027) | $8.4B state | May 2025 (12 sats) | LEO | TBD | Chinese chips |
| ESA (ASCEND) | Demo only | 300M euros | 2026 (demo planned) | TBD | TBD | TBD |

### Key Advantages by Company

| Company | Primary Advantage |
|---------|------------------|
| **SpaceX** | In-house launch (Falcon 9, Starship), existing Starlink infrastructure, xAI models |
| **Starcloud** | First mover with hardware in orbit, fastest unicorn, proven GPU operation |
| **Orbital** | NVIDIA partnership (Space-1 GPUs), lean startup approach |
| **Blue Origin** | In-house launch (New Glenn), TeraWave communications backbone |
| **Google** | TPU hardware expertise, cluster computing experience, Planet Labs partnership |
| **Axiom** | ISS-proven hardware, government/defense customer base, first ODC nodes deployed |
| **China** | State coordination, $8.4B budget, 100+ organizations unified |
| **ESA** | Environmental angle, data sovereignty, 300M euro EU funding |

### Key Risks and Open Questions

1. **Orbital debris:** Adding 1.2 million satellites would dramatically increase collision risk; the Kessler syndrome remains a real concern.
2. **Latency:** Ground-to-orbit-to-ground round trips add ~10-30ms minimum; real-time applications may be impractical.
3. **Bandwidth:** Downlinking processed results from millions of satellites requires massive spectrum allocation.
4. **Radiation:** GPUs must withstand cosmic radiation; radiation hardening reduces performance vs. terrestrial equivalents.
5. **Maintenance:** Satellites cannot be physically serviced; failed units must be deorbited and replaced.
6. **Economics:** At current launch costs ($2,000-3,000/kg to LEO), deploying 100,000 two-ton satellites would cost $200-300 billion in launch costs alone.
7. **Spectrum allocation:** The ITU and FCC must allocate sufficient spectrum for inter-satellite links and downlinks, creating potential regulatory bottlenecks.
8. **Manufacturing scale:** Producing millions of satellites requires automotive-scale manufacturing that does not yet exist for spacecraft.

---

## Sources

### Orbital Inc
- [Orbital Inc Official Website](https://orbital.inc/)
- [SpaceNews: Orbital files plans for 100,000 orbital data centers](https://spacenews.com/orbital-files-plans-for-100000-orbital-data-centers/)
- [IEEE Spectrum: Orbital Inference Data Center Bets On Space GPUs](https://spectrum.ieee.org/orbital-inference-data-center)
- [Interesting Engineering: US startup proposes 100,000-satellite data center constellation](https://interestingengineering.com/space/us-firm-files-fcc-application-for-100000-satellite-data-center-constellation)
- [MLQ News: Orbital Compute Files FCC Application](https://mlq.ai/news/orbital-compute-files-fcc-application-for-100000-satellite-10gw-space-data-center-constellation/)
- [Forbes: Why Orbital Believes Space Is The Next Frontier](https://www.forbes.com/sites/davidprosser/2026/04/14/why-orbital-believes-space-is-the-next-frontier-in-the-ai-revolution/)
- [TechCrunch: Spin founder raises $5 million to build space data centers](https://techcrunch.com/2026/06/09/how-an-e-scooter-founder-raised-5-million-to-build-space-data-centers/)
- [SiliconANGLE: AI satellite constellation startup Orbital gets funded by a16z](https://siliconangle.com/2026/04/14/ai-satellite-constellation-startup-orbital-gets-funded-andreessen-horowitz-verify-space-based-data-center-concept/)
- [Citybiz: Euwyn Poon's Orbital Raises $5M](https://www.citybiz.co/article/858361/euwyn-poons-orbital-raises-5m-to-build-data-centers-in-space/)
- [LA Business Journal: Orbital Plans to Send Data Centers to Space](https://labusinessjournal.com/technology/orbital-plans-to-send-data-centers-to-space/)
- [Orbital Press Release: $5M Pre-Seed](https://orbital.inc/press/orbital-raises-5m-preseed.html)
- [Orbital Press Release: 100,000 Constellation](https://orbital.inc/press/orbital-100000-constellation.html)

### SpaceX / Starmind
- [CryptoBriefing: SpaceX plans Starmind](https://cryptobriefing.com/spacex-starmind-ai-satellite-network/)
- [Motley Fool: SpaceX Merged With xAI](https://www.fool.com/investing/2026/07/16/elon-musk-spacex-merge-xai-orbital-data-center/)
- [Gear Musk: SpaceX Confirms Starmind Name](https://gearmusk.com/2026/06/24/named-starmind-ai-satellite/)
- [ExplainX: SpaceX AI1 Solar Orbital Datacenter](https://explainx.ai/blog/spacex-ai1-solar-orbital-datacenter-space-compute-2026)
- [Quartz: SpaceX reveals AI1 satellite design](https://qz.com/spacex-ai1-satellite-orbital-data-center-ipo-061026)
- [The Robotics Media: SpaceX Starmind AI1](https://theroboticsmedia.com/article/spacex-starmind-ai1-orbital-data-center-constellation)
- [DataCenterDynamics: SpaceX files for million satellite constellation](https://www.datacenterdynamics.com/en/news/spacex-files-for-million-satellite-orbital-ai-data-center-megaconstellation/)
- [Optimusk Blog: What Is Starmind?](https://optimusk.blog/blog/what-is-starmind-elon-musk-ai-satellite-plan/)

### Blue Origin
- [SpaceNews: Blue Origin joins the orbital data center race](https://spacenews.com/blue-origin-joins-the-orbital-data-center-race/)
- [GeekWire: Blue Origin data center space race Project Sunrise](https://www.geekwire.com/2026/blue-origin-data-center-space-race-project-sunrise/)
- [Data Centre Magazine: Project Sunrise](https://datacentremagazine.com/news/project-sunrise-blue-origin-data-centre-space-race)
- [AI Business: Bezos' Blue Origin joins race](https://aibusiness.com/data-centers/bezos-blue-origin-joins-race-ai-data-centers-in-space)
- [ISOClive Substack: Blue Origin FCC Application Summary](https://isoclive.substack.com/p/blue-origin-fcc)

### Starcloud / Lumen Orbit
- [GeekWire: Lumen Orbit raises $11M](https://www.geekwire.com/2024/lumen-orbit-a-seattle-area-startup-that-wants-to-put-data-centers-in-space-raises-11m/)
- [TechCrunch: Lumen Orbit biggest round from YC](https://techcrunch.com/2024/10/24/lumen-orbit-closed-one-of-the-biggest-rounds-from-y-combinators-last-cohort/)
- [TechCrunch: 200 VCs wanted into Lumen Orbit's round](https://techcrunch.com/2024/12/11/200-vcs-wanted-to-get-into-lumen-orbits-11m-seed-round)
- [SpaceNews: Starcloud achieves unicorn status](https://spacenews.com/starcloud-achieves-unicorn-status-with-170-million-raise-for-orbital-data-centers/)
- [SpaceNews: Starcloud files for 88,000-satellite constellation](https://spacenews.com/starcloud-files-plans-for-88000-satellite-constellation/)
- [TechCrunch: Starcloud raises $170M Series A](https://techcrunch.com/2026/03/30/starcloud-raises-170-million-series-ato-build-data-centers-in-space)
- [Via Satellite: Starcloud Raises $170M](https://www.satellitetoday.com/finance/2026/03/30/starcloud-raises-170m-to-fund-orbital-data-center-plans/)
- [DataCenterDynamics: Lumen Orbit rebrands to Starcloud](https://www.datacenterdynamics.com/en/news/lumen-orbit-rebrands-to-starcloud-raises-another-10m-for-in-orbit-data-centers/)
- [Y Combinator: Starcloud Company Profile](https://www.ycombinator.com/companies/lumen-orbit)
- [GeekWire: Starcloud hits $1.1B valuation](https://www.geekwire.com/2026/orbital-ai-seattle-area-startup-starcloud-hits-1-1b-valuation-to-build-space-based-data-centers/)

### Google / Project Suncatcher
- [Forbes: Google Unveils Project Suncatcher](https://www.forbes.com/sites/anishasircar/2025/11/11/google-unveils-project-suncatcher-to-run-ai-on-solar-satellites-in-orbit/)
- [DataCenterDynamics: Google in talks with SpaceX regarding Suncatcher](https://www.datacenterdynamics.com/en/news/google-in-talks-with-spacex-regarding-suncatcher-orbital-data-center-project/)
- [Space Explored: Planet and Google explore computing in orbit](https://spaceexplored.com/2026/01/05/planet-and-google-explore-computing-in-orbit/)

### Axiom Space
- [Axiom Space: Orbital Data Center](https://www.axiomspace.com/orbital-data-center)
- [Axiom Space: ODC Nodes Launch Press Release](https://www.axiomspace.com/release/axiom-space-to-launch-orbital-data-center-nodes-to-support-national-security-commercial-international-customers)
- [ISS National Lab: Orbital Data Center Launching to ISS](https://issnationallab.org/press-releases/orbital-data-center-launching-to-iss-to-advance-space-computing/)
- [Introl Blog: First Orbital Data Center Nodes Reach Space](https://introl.com/blog/orbital-data-center-nodes-launch-space-computing-infrastructure-january-2026)
- [DataCenterDynamics: Axiom Space orbital data center](https://www.datacenterdynamics.com/en/news/axiom-space-to-develop-orbital-data-center-on-its-commercial-space-station/)

### Cloud Providers
- [DataCenterKnowledge: Microsoft Pushes Azure Into Space](https://www.datacenterknowledge.com/cloud/microsoft-pushes-azure-cloud-services-into-new-frontier-space)
- [DataCenterFrontier: The Space Cloud - Satellite Strategies](https://www.datacenterfrontier.com/cloud/article/11428161/the-space-cloud-satellite-strategies-for-aws-google-and-microsoft)

### China
- [SpaceDaily: China 100+ organizations, 1000 POPS plan](https://spacedaily.com/sd-in-2026-china-put-more-than-100-space-computing-organizations-under-a-new-beijing-committee-tying-12-ai-satellites-and-a-1000-pops-orbital-supercomputer-plan-to-the-five-year-plan-and-the-still/)
- [Xinhua: China eyes computing in space](https://english.news.cn/20260425/b4368923827e4988af1bd030dd01d9cc/c.html)
- [CarbonCredits: China's $8.4B Orbital Data Center Push](https://carboncredits.com/chinas-8-4b-orbital-data-center-push-sets-up-space-based-ai-showdown-with-spacex/)
- [Tom's Hardware: China unifies tech sector](https://www.tomshardware.com/tech-industry/data-centers/china-unifies-tech-sector-to-build-grid-free-orbiting-satellite-ai-data-centers-challenging-elon-musks-spacex-beijings-forced-chip-and-satellite-alliance-announced-a-week-before-musks-ai1-reveal)
- [China Daily: Chinese tech firms race to build AI computing](https://www.chinadaily.com.cn/a/202512/05/WS69323706a310d6866eb2d03e.html)

### ESA ASCEND
- [Thales Alenia Space: ASCEND Feasibility Study Results](https://www.thalesaleniaspace.com/en/press-releases/thales-alenia-space-reveals-results-ascend-feasibility-study-space-data-centers-0)
- [Forbes Council: The Orbital Pivot](https://www.forbes.com/councils/forbestechcouncil/2026/04/14/the-orbital-pivot-why-your-next-data-center-wont-be-on-earth/)

### Satellite Counts and Industry Statistics
- [EarthSky: 10,000 Starlink satellites](https://earthsky.org/spaceflight/10000-starlink-satellites-orbiting-earth-counting/)
- [Orbital Radar: How Many Satellites in Orbit](https://orbitalradar.com/how-many-satellites-in-orbit)
- [HighSpeedInternet: Starlink satellite count](https://www.highspeedinternet.com/resources/how-many-starlink-satellites-are-in-orbit-june-5-2026)
- [Orbital Radar: Kuiper satellite count](https://orbitalradar.com/how-many-kuiper-satellites)
- [KeepTrack: Amazon Leo Progress 2026](https://keeptrack.space/deep-dive/amazon-leo-progress-2026)
- [SIA: 28th Annual State of the Satellite Industry Report](https://sia.org/historic-number-of-launches-powers-commercial-satellite-industry-growth-satellite-industry-association-releases-the-28th-annual-state-of-the-satellite-industry-report/)
- [Sentinel Mission: Space Industry Statistics 2026](https://sentinelmission.org/statistics/space-industry-statistics/)

### Industry Overview
- [Introl Blog: Orbital Data Center Race 2026](https://introl.com/blog/orbital-data-centers-space-computing-race-2026)
- [Enkiai: Orbital Data Centers 2026](https://enkiai.com/ai-market-intelligence/orbital-data-centers-2026-capital-shifts-to-infrastructure)
- [RackSolutions: Are Data Centers Headed to Space?](https://www.racksolutions.com/news/data-centers-news/are-data-centers-headed-to-space/)
- [AINvest: Redwire Role in Space Data Center Ecosystem](https://www.ainvest.com/news/redwire-role-emerging-space-data-center-ecosystem-assessing-growth-potential-cash-burn-valuation-concerns-2512/)
