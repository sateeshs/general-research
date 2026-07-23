# Historical Precedents, Current State-of-the-Art, and Technical Milestones for Computing in Space

*Research Date: July 2026*

---

## Table of Contents

1. [History of Computing in Space](#1-history-of-computing-in-space)
2. [Recent Milestones (2024-2026)](#2-recent-milestones-2024-2026)
3. [Space-Based Solar Power (SBSP) Connection](#3-space-based-solar-power-sbsp-connection)
4. [Edge Computing in Orbit](#4-edge-computing-in-orbit)
5. [International Programs](#5-international-programs)
6. [Key Academic Research](#6-key-academic-research)
7. [Sources and Bibliography](#7-sources-and-bibliography)

---

## 1. History of Computing in Space

### 1.1 ISS Computing Systems

The International Space Station relies on a layered computing architecture spanning both the US and Russian segments.

**Command and Data Handling (CDH) System:**
The US segment uses Multiplexer/Demultiplexer (MDM) units manufactured by Honeywell as the backbone of its Command and Data Handling system. These MDMs route all incoming and outgoing data to its correct destination, controlling major functions including power generation and distribution, attitude control, environmental control, communications, and monitoring of scientific payloads (Honeywell Aerospace, n.d., "Multiplexer/Demultiplexer (MDM)," https://aerospace.honeywell.com/us/en/products-and-services/product/hardware-and-systems/space/multiplexer-demultiplexer). The MDM Loading Tool (MDMLT) enables web-based parallel configuration of the entire ISS MDM system via the MIL-STD-1553 bus (NASA Tech Briefs, "Multiplexer/Demultiplexer Loading Tool," https://www.techbriefs.com/component/content/article/13055-msc-24480-1).

**Crew Laptops:**
Commanding to the US vehicle segment is done using Portable Computer System (PCS) laptops running Linux, connected to the vehicle's 1553 system as remote terminals. Historically, NASA has used Lenovo ThinkPad T61P laptops, with some older A31p models still in use (Forbes, 2016, "NASA Chooses This Brand For Its Laptops Aboard The ISS," https://www.forbes.com/sites/quora/2016/05/14/what-kind-of-laptops-are-on-the-iss/).

**HPE Spaceborne Computers:**
Beginning in 2017, HPE deployed commercial off-the-shelf (COTS) supercomputing hardware to the ISS, dramatically expanding onboard computing capability (see Section 1.2).

### 1.2 HPE Spaceborne Computer (1 and 2)

**Spaceborne Computer-1 (SBC-1) — 2017-2019:**
HPE sent an unmodified COTS high-performance computer to the ISS, where it operated for 657 days (over 1.5 years) — the first long-term demonstration of supercomputing capabilities from a COTS system on the station. During its first year, SBC-1 completed hundreds of tests to determine how harsh space conditions affect supercomputing technology. Key lessons included understanding radiation-induced memory defects and thermal management in microgravity (ISS National Lab, "On the Edge of the Edge: Taking Supercomputing to Space," https://issnationallab.org/upward/hpe-supercomputing-return-space/).

**Spaceborne Computer-2 (SBC-2) — 2021-present:**
SBC-2 incorporated lessons learned from SBC-1, featuring twice the processing power and including GPUs along with AI and edge processing capabilities. The system is based on HPE EdgeLine and ProLiant servers. HPE tested new software technologies for recovering and mitigating transient memory defects during operations in space (HPE, 2024, "HPE Spaceborne Computer-2 Returns to the International Space Station," https://www.hpe.com/us/en/newsroom/press-release/2024/01/hpe-spaceborne-computer-2-returns-to-the-international-space-station.html).

**Key Achievement:** HPE successfully deployed and operated generative AI large language models (LLMs) on the ISS — believed to be the first LLM deployed in space — enabling astronauts to use generative AI without Earth-bound internet dependence (HPE, "Accelerating Space Exploration with the Spaceborne Computer," https://www.hpe.com/us/en/compute/hpc/supercomputing/spaceborne.html).

**Third Launch (January 2024):** HPE partnered with KIOXIA to add flash memory storage to test storage and recovery on long-term space missions, expanding the scope to data-center-level processing, HPC, AI, and ML workloads (ISS National Lab, 2024, https://issnationallab.org/press-releases/release-ng20-hpe-spaceborne-computer2/).

**Key Lessons Learned:**
- COTS hardware can survive in space with software-based error mitigation
- Processing raw data onboard and sending only results saves significant bandwidth
- GPU acceleration is viable in the space environment
- Software recovery techniques can handle radiation-induced memory errors

### 1.3 Computing on Mars Rovers

**Processor: BAE Systems RAD750**
Both NASA's Curiosity (landed 2012) and Perseverance (landed 2021) rovers use the RAD750, a radiation-hardened variant of the PowerPC 750 chip. The RAD750 contains just 10.4 million transistors and operates at up to 200 MHz — architecturally equivalent to the chip in Apple's 1998 iMac G3 (TechSpot, 2021, "NASA's Mars Perseverance Rover Uses the Same CPU as Apple's iMac from 1998," https://www.techspot.com/news/88796-nasa-mars-perseverance-rover-powered-processor-1998.html).

**Specifications:**
- Radiation tolerance: up to 1 million rads
- Operating temperature: -55°C to 125°C
- Two redundant single-core CPUs per rover
- 256 MB DRAM, 256 KB EEPROM, and 2 GB flash memory per CPU
- Processing speed: at least 400 million instructions per second

**Additional Hardware:**
Perseverance carries AMD FPGAs supporting computer vision (from 23 cameras), navigation, and the SHERLOC instrument package. The RAD750 has been used in over 150 spacecraft, including the Kepler space telescope (Big Think, 2021, "NASA's Perseverance Rover Has a 1997 Computer Chip Brain. Here's Why," https://bigthink.com/hard-science/perseverance-rover-brain/).

**Why Old Processors?**
Radiation hardening requires extensive testing and qualification, typically taking 5-10 years. The priority is proven reliability over performance in deep space, where a hardware failure cannot be repaired.

### 1.4 Satellite Onboard Processing Evolution

**1960s-2000s — The Bent-Pipe Era:**
For more than five decades, commercial satellites used a "bent-pipe" architecture, functioning primarily as data relays that forwarded signals to ground stations without any onboard processing (eoPortal, "Onboard Data Processing," https://www.eoportal.org/other-space-activities/onboard-data-processing).

**2010s — Early Onboard Processing:**
Satellites began incorporating more capable processors for basic data handling, compression, and telemetry processing. FPGAs became common for reconfigurable processing tasks.

**2019-2020 — The AI Inflection Point:**
Two missions marked the transition to genuine onboard AI:
- **ESA OPS-SAT** (December 2019): The first satellite mission dedicated to testing and validating new mission control and onboard software techniques, carrying an experimental computer 10x more powerful than any current ESA spacecraft (ESA, "OPS-SAT," https://www.esa.int/Enabling_Support/Operations/OPS-SAT).
- **ESA PhiSat-1** (September 2020): The first AI chip in orbit (see Section 1.5).

**2022-2026 — Edge AI Proliferation:**
Modern satellite architectures leverage hybrid CPU-GPU-FPGA systems capable of delivering up to 1,000 TOPS for AI workloads. Companies like Planet Labs, Satellogic, and Spire Global have deployed satellites with onboard AI processing as standard capability (Lockheed Martin, 2022, "AI/ML for Mission Processing Onboard Satellites," https://www.lockheedmartin.com/content/dam/lockheed-martin/space/documents/ai-ml/).

### 1.5 ESA PhiSat-1 — First AI Chip in Orbit

**Launch:** September 2020 as part of the FSSCat (Federated Satellite System) mission — a 6U CubeSat.

**AI Hardware:** Intel Movidius Myriad 2 Vision Processing Unit (VPU) — the same chip used in consumer smart cameras and selfie drones. The chip was not designed for space; Ubotica Technologies performed extensive "radiation characterization" testing to determine how to handle radiation-induced errors (Intel, 2020, "Intel Powers First Satellite with AI on Board," https://download.intel.com/newsroom/archive/2025/en-us-2020-10-20-intel-powers-first-satellite-with-ai-on-board.pdf).

**Function:** The onboard AI identifies and discards cloud-covered images before downlink, saving approximately 30% of bandwidth (AI Magazine, 2020, "Intel and ESA Launch Experimental AI Satellite PhiSat-1," https://aimagazine.com/ai-applications/intel-and-esa-launch-experimental-ai-satellite-phisat-1).

**Orbital Parameters:** Sun-synchronous orbit at approximately 530 km altitude, traveling at 27,500 km/h.

**Significance:** PhiSat-1 proved that commercial-grade AI chips could operate in orbit with software-based radiation mitigation, opening the door for subsequent missions using NVIDIA Jetson, Google TPUs, and other COTS AI accelerators.

**Successor — PhiSat-2:** ESA's Phi-Lab has continued the program with PhiSat-2 and expanded it into a broader Phi-Sats programme, testing increasingly capable onboard AI systems (ESA Phi-Lab, "Phi-Sats Programme," https://philab.esa.int/flagship-programmes/phi-sats-programme/).

### 1.6 Other AI-in-Orbit Experiments

**ESA OPS-SAT (2019-2024):**
Operated for over 4 years as a flying laboratory. Notable achievements included the first Canadian AI experiment in orbit (Mission Control's Spacefarer AI), which hybridized a neural network and reprogrammed an FPGA while orbiting Earth. The satellite re-entered Earth's atmosphere on May 22-23, 2024 (ESA, "OPS-SAT," https://www.esa.int/Enabling_Support/Operations/OPS-SAT; Mission Control Space, "OPS-SAT: AI Demo in Low Earth Orbit," https://missioncontrolspace.com/stories/ops-sat-ai-demo-in-low-earth-orbit/).

**Planetek AI-eXpress Constellation:**
By November 2025, a third AI-eXpress satellite was placed in orbit, establishing a constellation dedicated to edge intelligence in space (Planetek Italia, 2025, "Third AI-eXpress Satellite in Orbit," https://www.planetek.it/en/news_events/news_archive/2025/11/third_ai_express_satellite_in_orbit_for_a_new_era_of_edge_intelligence_in_space).

**Zhongke Tiansuan (Comospace) — China:**
Founded in 2024, the company has logged over 1,000 days of on-orbit operation with its Aurora 1000 space computer aboard a Jilin-1 satellite (China Daily, 2025, "Chinese Tech Firms Race to Build AI Computing Capabilities in Space," https://www.chinadaily.com.cn/a/202512/05/WS69323706a310d6866eb2d03e.html).

---

## 2. Recent Milestones (2024-2026)

### 2.1 Orbital Data Center Hardware Launches

The period from late 2025 through mid-2026 saw a historic acceleration in space computing hardware deployment:

| Date | Company | Milestone |
|------|---------|-----------|
| Nov 2, 2025 | Starcloud (fmr. Lumen Orbit) | First NVIDIA H100 GPU in space (Starcloud-1, 60 kg satellite) |
| Dec 2025 | Starcloud | First LLM trained in orbit (NanoGPT on Shakespeare) |
| Jan 11, 2026 | Kepler Communications | 10 optical relay satellites with 40 NVIDIA Jetson Orin modules |
| Jan 11, 2026 | Axiom Space | Two orbital data center nodes to LEO |
| Mar 16, 2026 | Kepler | Commissioned distributed on-orbit cloud computing |
| Mar 16, 2026 | NVIDIA | Announced Space-1 Vera Rubin Module, IGX Thor, and Jetson Orin space platforms |

(Introl Blog, 2026, "First Orbital Data Center Nodes Reach Space," https://introl.com/blog/orbital-data-center-nodes-launch-space-computing-infrastructure-january-2026; NVIDIA Newsroom, 2026, "NVIDIA Launches Space Computing," https://nvidianews.nvidia.com/news/space-computing; Kepler Space, 2026, "Kepler Deploys First Space-Based, Scalable Cloud Infrastructure," https://kepler.space/kepler-deploys-first-space-based-scalable-cloud-infrastructure-powered-by-nvidia/)

### 2.2 Lumen Orbit / Starcloud

**Background:** Founded as Lumen Orbit (Y Combinator-backed, headquartered in Redmond, Washington), the company rebranded to Starcloud in 2025.

**Funding:** Raised $2.4M in initial seed funding (Data Center Dynamics, 2024, https://www.datacenterdynamics.com/en/news/lumen-orbit-raises-24m-for-space-data-centers/), followed by $10M (GeekWire, 2025, https://www.geekwire.com/2025/lumen-orbit-starcloud-10m-space-data-centers/), and $170M Series A in March 2026 (Introl Blog, 2026).

**Technical Milestones:**
- Launched Starcloud-1 (60 kg, NVIDIA H100 GPU) on November 2, 2025, via SpaceX Falcon 9
- Claimed the most powerful processor ever flown in space
- Trained NanoGPT on the complete works of Shakespeare in orbit (December 2025)
- Running inference on Capella Space SAR imagery
- Filed with FCC for an 88,000-satellite constellation

**Upcoming:** Starcloud-2 (October 2026) with multiple H100 chips and Blackwell architecture. Long-term vision: 5 GW orbital data centre with solar arrays spanning 4 km x 4 km (Introl Blog, 2026, "Orbital Data Center Race 2026," https://introl.com/blog/orbital-data-centers-space-computing-race-2026).

### 2.3 Orbital Compute (Orbital Inc.)

Orbital came out of stealth in May 2026 with plans for thousands of small number-crunching satellites. The company expects to finalize satellite designs by 2026, launch in 2027, and build a manufacturing facility in Los Angeles by 2028 (IEEE Spectrum, May 2026, "Orbital Inference Data Center Bets On Space GPUs," https://spectrum.ieee.org/orbital-inference-data-center; Orbital Inc., https://orbital.inc/).

### 2.4 Other Companies Testing Hardware in Orbit

**Axiom Space:**
- Built on ISS prototype (AxDCU-1) tested in fall 2025
- Deployed two orbital data center nodes January 11, 2026
- Partners include Kepler, Skyloom Global, Spacebilt, Phison Electronics
- Next milestone: Fully optically-interconnected ISS node in 2027

**OrbitsEdge:**
- Partnership with Hewlett Packard Enterprise
- First orbital AI demonstration planned for 2026

**Lonestar Data Holdings:**
- Dual LEO and lunar strategy (lunar lava tubes for radiation shielding)
- $5M seed funding
- First LEO service targeted Q4 2026

**Aetherflux:**
- Founded by Robinhood co-founder Baiju Bhatt
- $60M total funding with US military support
- Demo satellite launch planned 2026 (SpaceX Falcon 9)
- Plans for orbital compute + power-beaming via infrared laser
- "Galactic Brain" data center node planned Q1 2027

(Sources: SpaceNews, 2025/2026; TechCrunch, 2025, https://techcrunch.com/2025/04/02/space-solar-startup-aetherflux-raises-50m-to-launch-first-space-demo-in-2026; New Atlas, 2026, https://newatlas.com/energy/laser-beamed-space-solar-power-aetherflux-2026-test/)

### 2.5 Major Tech Companies Entering the Space

**Google — Project Suncatcher:**
- Custom radiation-hardened Trillium TPU v6e chips
- Lab-demonstrated 1.6 terabits-per-second optical links
- Formation-flying clusters of up to 81 satellites at ~650 km altitude
- "Learning mission" with Planet Labs: two prototype satellites by early 2027
- Published research framing it as a path to orbital AI cloud

(Forbes, 2025, "Google Plans To Run AI Data Centers In Space With Project Suncatcher," https://www.forbes.com/sites/anishasircar/2025/11/11/google-unveils-project-suncatcher-to-run-ai-on-solar-satellites-in-orbit/; Tom's Guide, 2026, https://www.tomsguide.com/ai/elon-musk-might-be-right-heres-why-putting-ai-data-centers-in-space-isnt-as-crazy-as-it-sounds)

**SpaceX / xAI:**
- Merged February 2, 2026 ($1.25 trillion valuation)
- FCC filing January 30, 2026: authorization for up to 1 million orbital data center satellites
- Target altitudes: 500-2,000 km
- Projection: "one million tonnes of satellites annually would generate 100 gigawatts" of compute

**NVIDIA Space Computing (March 2026):**
- Space-1 Vera Rubin Module: delivers up to 25x more AI compute than H100 for space-based inferencing
- IGX Thor and Jetson Orin platforms for edge AI on orbit
- Customers include Aetherflux, Axiom Space, Kepler, Planet Labs, Sophia Space, Starcloud

(NVIDIA Newsroom, 2026, https://nvidianews.nvidia.com/news/space-computing; Via Satellite, 2026, https://www.satellitetoday.com/technology/2026/03/17/nvidia-launches-new-chips-for-space-missions/)

### 2.6 SpaceX Starship Progress and Cost Reduction

**Flight History:** As of October 13, 2025, Starship completed 11 launches (6 successes, 5 failures).

**Cost Trajectory:**
- Average LEO launch cost fell 96% to $3,868/kg by 2025
- Falcon 9 current rate: ~$2,700/kg
- Starship V3 reusable configuration: ~200 metric tons to LEO
- Elon Musk's target (May 2026, post-Flight 12): "$100-200/kg" fully reusable
- Industry consensus: meaningful commercial cost drops after 2027-2029 when reliability and flight rates improve

(Singularity Hub, 2026, "Spaceflight Nears Its Steamship Era," https://singularityhub.com/2026/07/20/space-launch-costs-have-fallen-96-since-1960-they-arent-done-yet/; Orbital Intel, "Launch Cost Per Kg: From $54,500 to $1,500," https://orbital-intel.com/launch-cost-history/; SpaceOrbitals, 2026, "How Cheap Is Starship V3 Really?," https://spaceorbitals.com/articles/starship-v3-cost-per-kg-2026/)

**Relevance to Space Computing:** Orbital data center economics hinge critically on launch cost. Current analysis requires dropping from ~$2,700/kg (Falcon 9) to <$100/kg for orbital compute cost parity with terrestrial data centers by 2028-2030.

---

## 3. Space-Based Solar Power (SBSP) Connection

### 3.1 SBSP and Orbital Data Centers

The connection between SBSP and orbital data centers is fundamental: both require large solar arrays in space, and the power-beaming technology being developed for SBSP could directly supply orbital computing facilities. In the right orbit, solar panels can be "up to 8 times more productive than on Earth," providing near-continuous power (Google Project Suncatcher research, 2025). Starcloud has claimed potential energy costs of $0.005/kWh versus $0.04-0.08/kWh for terrestrial facilities, though skeptics note that orbital compute currently costs "roughly three times more per watt" than ground alternatives when factoring in total system costs (Introl Blog, 2026).

### 3.2 Caltech SSPD-1 Experiment Results

**Launch:** January 3, 2023, aboard a Momentus Vigoride spacecraft.

**Three Experiments:**
1. **DOLCE** (Deployable on-Orbit ultraLight Composite Experiment): Successfully demonstrated a 1.8m x 1.8m deployable structure for novel solar array architecture
2. **ALBA**: Tested 32 different types of photovoltaic cells for space environment survivability
3. **MAPLE** (Microwave Array for Power-transfer Low-orbit Experiment): Successfully demonstrated wireless power transmission in space and beamed detectable power to Earth in 2023

**Results:** The mission successfully demonstrated wireless power transmission from space — a world first. Though all experiments were ultimately successful, "not everything went according to plan," with some technical challenges encountered during deployment (Caltech, 2024, "Space Solar Power Project Ends First In-Space Mission with Successes and Lessons," https://www.caltech.edu/about/news/space-solar-power-project-ends-first-in-space-mission-with-successes-and-lessons; phys.org, 2024, https://phys.org/news/2024-01-space-solar-power-mission-successes.html).

**Award:** The team won the 2024 Gizmodo Science Fair for proving it is possible to collect solar energy in space and send it to Earth as usable power.

### 3.3 ESA Solaris Program

**Launch:** 2023, with an initial goal of assessing the technical, political, and economic feasibility of photovoltaic power plants in geostationary orbit by end of 2025.

**Feasibility Studies:** ESA chose Thales Alenia Space for the SOLARIS feasibility study. The program brings together policymakers, energy suppliers, and space companies (ESA, "ESA Accelerates the Race Towards Clean Energy from Space," https://www.esa.int/Space_in_Member_States/United_Kingdom/ESA_accelerates_the_race_towards_clean_energy_from_space; Thales Alenia Space, "ESA Chooses Thales Alenia Space for SOLARIS Feasibility Study," https://www.thalesaleniaspace.com/en/press-releases/esa-chooses-thales-alenia-space-solaris-feasibility-study).

**Concept:** Energy harvested by solar panels in GEO would be transmitted via microwaves to large receiving antennas on Earth, then converted back to electricity. Results should allow Europe to make an informed decision on proceeding with full development, beginning with a subscale in-orbit demonstrator.

**Strategic Goal:** Position Europe as a key player — and potentially leader — in the international race toward scalable clean energy solutions.

### 3.4 Could SBSP Beam Power to Orbital Data Centers?

This is technically feasible and already being pursued:

- **Aetherflux** is building a combined power-beaming + orbital compute constellation, using infrared lasers to beam power between satellites and to ground stations. The company entered the orbital data center race specifically because the same satellite infrastructure serves both power delivery and compute (SpaceNews, 2026, "Space-Based Solar Power Startup Aetherflux Enters Orbital Data Center Race," https://spacenews.com/space-based-solar-power-startup-aetherflux-enters-orbital-data-center-race/).

- **Starcloud's** long-term vision includes 5 GW orbital data centres with massive solar arrays, essentially integrating SBSP directly into the computing infrastructure.

- **Google's Project Suncatcher** explicitly frames its satellites as "solar-powered" computing platforms, using continuous orbital sunlight to power TPU-equipped satellites.

The convergence of SBSP and orbital computing is one of the most significant technological trends in the space sector as of 2026.

### 3.5 Japanese SBSP Program

**JAXA OHISAMA Mission:**
- Implemented by JAXA and Japan Space Systems
- 180 kg satellite in LEO at 400 km altitude
- 2-square-meter photovoltaic panel converts solar energy to electricity
- Stores energy in onboard batteries, then beams as microwave energy to a ground station
- Power level: 1 kW (sufficient for a small appliance)
- Has demonstrated 1 kW orbital-to-ground microwave transmission to a receiving site in Yokohama

(Space.com, 2025, "Japanese Satellite Will Beam Solar Power to Earth in 2025," https://www.space.com/japan-space-based-solar-power-demonstration-2025; I-Connect007, 2025, https://iconnect007.com/article/146121/japans-ohisama-project-aims-to-beam-solar-power-from-space-this-year/)

Japan has the longest continuous SBSP research program, dating back to the 1980s, and OHISAMA represents the culmination of decades of incremental work.

### 3.6 Chinese SBSP Program

**Bishan Ground Test Facility:**
- Construction began in 2019 in Chongqing's Bishan District
- $15 million funding for a 2 km ground-based test array
- Fine-tuning radio wave transmission technology needed for orbital-to-ground power transfer
- August 2021: 300-meter line-of-sight microwave transmission test
- June 2022: Xidian University completed full system prototype test in Xi'an

**Future Plans:**
- 2027/2028: LEO demonstration mission (~10 kW generation and power beaming)
- 2030: GEO demonstration at megawatt level
- Long-term: Gigawatt-scale orbital solar power station

(Wikipedia, "Space-Based Solar Power," https://en.wikipedia.org/wiki/Space_based_solar_power; OPS Journal, "China Is Planning a Space-Based Solar Power Plant," https://www.opsjournal.org/DocumentLibrary/Uploads/China%20is%20planning%20a%20solar%20power%20plant%20with%20a%20capacity%20of%20one%20gigawatt%20in%20space.pdf)

---

## 4. Edge Computing in Orbit

### 4.1 Current Satellite Onboard Processing Capabilities

As of 2026, onboard satellite processing has evolved from simple telemetry to sophisticated AI inference:

| Generation | Era | Capability | Example |
|------------|-----|------------|---------|
| 1st | 1960s-2000s | Bent-pipe relay, no processing | Communications satellites |
| 2nd | 2000s-2010s | Basic data compression, telemetry | Early EO satellites |
| 3rd | 2010s-2020 | FPGA-based reconfigurable processing | Military reconnaissance |
| 4th | 2020-2024 | Single AI chip inference (VPU) | PhiSat-1 (Intel Movidius) |
| 5th | 2024-present | GPU-accelerated AI, multi-model inference | Starcloud (H100), Kepler (Jetson Orin) |

Modern architectures leverage hybrid CPU-GPU-FPGA systems capable of up to 1,000 TOPS for AI workloads (JPL, "Towards Space Edge Computing and Onboard AI for Real-Time [Processing]," https://ai.jpl.nasa.gov/public/documents/papers/ieee-leo-sats-report.pdf).

### 4.2 Earth Observation Satellites Processing Before Downlink

**Planet Labs:**
- Pelican constellation equipped with NVIDIA Jetson edge AI platform
- Next-generation Owl constellation integrates NVIDIA GPUs onboard for AI inference
- Designed for tip-and-cue operation with the Pelican fleet
- Working with Google on Project Suncatcher prototype satellites

(TerraWatch Space, 2026, "Edge Computing for Earth Observation — 2026 Edition," https://newsletter.terrawatchspace.com/edge-computing-for-earth-observation-2026-edition/; Player One Space Blog, "Brains in Orbit: A Complete Guide to Edge AI and Compute on Satellites," https://blog.playeronespace.com/p/brains-in-orbit-a-complete-guide)

**Satellogic:**
- "AI-First" architecture with continuous capture and onboard GPU processing
- Multiple AI models running simultaneously, updateable post-launch
- Partners with Palantir for Edge AI integration
- Next-gen Merlin constellation (projected October 2026) features native edge processing for real-time imagery analysis

(Satellogic, 2025, "Pushing Intelligence to the Edge," https://satellogic.com/2025/03/20/pushing-intelligence-to-the-edge-satellogics-vision-for-ai-powered-earth-observation/; Palantir Blog, "Edge AI in Space," https://blog.palantir.com/edge-ai-in-space-93d793433a1e)

**Spire Global:**
- Early adopter of on-orbit edge computing since 2022
- Partnered with SATE on an 18-month ESA-supported satellite AI research program
- Satellites with onboard processing for advanced data processing and decision-making

(Stock Titan, 2025, "Spire Global Partners on 18-Month Satellite AI Program," https://www.stocktitan.net/news/SPIR/spire-global-partners-with-sate-on-esa-supported-research-program-to-2kgxh4aondgy.html)

### 4.3 Process in Orbit vs. Downlink Raw Data

**The Bandwidth Bottleneck:**
EO satellites generate enormous volumes of raw data (Planet alone captures ~350 TB/day), but available downlink bandwidth is limited to brief ground station passes. This creates a fundamental tension:

| Factor | Process in Orbit | Downlink Raw Data |
|--------|-----------------|-------------------|
| Bandwidth usage | Reduced 30-90% (only insights transmitted) | Full raw data volume |
| Latency | Near real-time results | Hours to days for processing |
| Power consumption | Higher onboard power needed | Lower onboard, higher ground |
| Data fidelity | Some information lost in compression/filtering | Full raw data preserved |
| Flexibility | Model limited to onboard hardware | Full ground compute available |
| Cost | Higher satellite cost, lower ground infrastructure | Lower satellite cost, higher ground |

**The Trend:** The industry is clearly moving toward hybrid architectures where time-critical analysis happens onboard, while archival and research-grade processing occurs on the ground. PhiSat-1 demonstrated that cloud filtering alone saves ~30% bandwidth (Intel, 2020).

### 4.4 Bandwidth Limitations Driving In-Orbit Processing

Key bandwidth constraints driving the shift to onboard processing:

- **Ground station contact windows:** LEO satellites have 5-15 minute passes over ground stations, limiting total data downlink per orbit
- **Link rates:** Even advanced optical links are limited to ~10 Gbps from LEO, insufficient for the TB-scale imagery modern constellations produce
- **Constellation scale:** As fleet sizes grow (Planet: 200+ satellites; Starlink: 6,000+), aggregate bandwidth demands outstrip available spectrum
- **Latency requirements:** Military, disaster response, and maritime monitoring need results in seconds, not hours

These constraints make onboard AI processing not just desirable but increasingly necessary (UN-SPIDER, 2025, "AI-Enabled Onboard Edge Computing for Satellite Intelligence in Disaster Management," https://www.un-spider.org/news-and-events/news/ai-enabled-onboard-edge-computing-satellite-intelligence-disaster-management).

### 4.5 Companies Doing Satellite Edge Computing

| Company | Approach | Hardware | Status |
|---------|----------|----------|--------|
| Planet Labs | Pelican/Owl constellations with NVIDIA GPUs | Jetson, NVIDIA GPUs | Operational (Pelican), Development (Owl) |
| Spire Global | Multi-sensor processing, weather/maritime | Custom SoCs | Operational since 2022 |
| Satellogic | AI-First with real-time GPU inference | Onboard GPUs | Operational, Merlin constellation 2026 |
| Kepler Communications | Distributed cloud computing via optical network | 40x NVIDIA Jetson Orin across 10 satellites | Commissioned March 2026 |
| Starcloud | Full data-center-class GPU compute | NVIDIA H100, Blackwell planned | Operational since Nov 2025 |
| Planetek | AI-eXpress constellation for edge intelligence | Dedicated AI processors | 3 satellites operational by Nov 2025 |

---

## 5. International Programs

### 5.1 Chinese Space Computing Initiatives

China has the most aggressive and well-funded space computing program globally:

**Three-Body Computing Constellation (ADA Space / Zhejiang Lab):**
- First 12 satellites launched May 14, 2025
- Demonstrated distributed computing, inter-satellite networking, and deployment of 8-billion-parameter AI models in orbit — among the largest currently operating in space
- Target: 100 satellites by 2027, 1,000 satellites for commercial operations by 2030, full 2,800-satellite network by 2035
- Over 95% will be inference computing satellites

(Global Times, 2025, "China Pioneers in AI Satellite Deployment in Space," https://www.globaltimes.cn/page/202511/1349105.shtml; Xinhua, 2026, "From Ground to Orbit: China Eyes Computing in Space," https://english.news.cn/20260425/b4368923827e4988af1bd030dd01d9cc/c.html)

**Orbital Chenguang Project (CASC):**
- China Aerospace Science and Technology Corporation's five-year roadmap (announced February 2026)
- Goal: nationalized "Space Cloud" for AI workloads independent of terrestrial infrastructure
- Dawn-dusk sun-synchronous orbit at 700-800 km altitude
- Long-term target: gigawatt-scale space data center by 2035
- Backed by $8.4 billion in state credit lines

(SpaceNews, 2026, "China Backs Orbital Data Center Startup with $8.4 Billion in Credit Lines," https://spacenews.com/china-backs-orbital-data-center-startup-with-8-4-billion-in-credit-lines/)

**Zhongke Tiansuan (Comospace):**
- Founded 2024, already 1,000+ days of on-orbit operation
- Aurora 1000 space computer aboard Jilin-1 satellite

**Timeline:**
- 2025-2027: Core technology validation and first constellation launches
- 2028-2030: Earth-space integrated computing operations
- 2030-2035: Full commercial-scale orbital computing network

### 5.2 European Space Agency Programs

**PhiSat Programme:** Ongoing series of AI-in-orbit demonstrations (PhiSat-1, PhiSat-2, and beyond), testing increasingly sophisticated onboard AI capabilities (ESA Phi-Lab, https://philab.esa.int/flagship-programmes/phi-sats-programme/).

**OPS-SAT (2019-2024):** Successfully completed its mission after 4+ years, validating numerous onboard computing techniques. Successor mission planned.

**Solaris SBSP Program:** Feasibility assessment for orbital solar power (see Section 3.3).

**ESA-Supported Research:** Supporting Spire Global's 18-month satellite AI research program and other industry partnerships for in-orbit processing development.

### 5.3 Japanese Space Computing

**JAXA OHISAMA:** Primarily focused on SBSP demonstration but with computing implications for power delivery to orbital infrastructure (see Section 3.5).

**Japan's broader program:** Japan Space Systems and JAXA have maintained the world's longest continuous SBSP research effort since the 1980s, providing foundational technology applicable to powering orbital data centers.

### 5.4 Indian Space Computing

**ISRO AI Data Center Concept:**
ISRO is conceptualizing a proof-of-concept system for computation and storage in orbit, reflecting a strategic push toward edge computing in space. Onboard AI would enable real-time analysis, transmitting only insights (disaster alerts, crop health metrics) rather than raw data (ISRO/India Strategic, 2026, "ISRO Explores Establishing Orbiting AI Data Centres," https://www.indiastrategic.in/isro-explores-establishing-orbiting-ai-data-centres/).

**MOI-1 Mission (2026):**
India's first 2026 ISRO mission put an AI-powered imaging startup into orbit. MOI-1 is positioned as an open AI laboratory in LEO, allowing developers to deploy and test AI models without owning a satellite (American Bazaar, 2026, https://americanbazaaronline.com/2026/01/09/indias-first-2026-isro-mission-puts-ai-powered-startup-into-orbit-472903/).

**I-STAR Satellite Constellation:**
ISRO's AI-powered I-STAR constellation aims for SAR and thermal imaging with onboard AI for defense and civilian applications. The SBS-3 phase targets 52 dedicated defence satellites within four years (Defence XP, "Unveiling ISRO's AI-Powered I-STAR Satellite Constellation," https://www.defencexp.com/unveiling-isros-ai-powered-i-star-satellite-constellation/).

### 5.5 International Competition and Cooperation

The space computing race is shaping into a three-way competition:

| Bloc | Scale | Approach | Funding Model |
|------|-------|----------|---------------|
| US | SpaceX/xAI (1M sats), Google (81 sats), Starcloud (88K sats) | Private-led with defense contracts | VC + corporate + military |
| China | Three-Body (2,800 sats), Chenguang (GW-scale) | State-led with commercial execution | $8.4B+ state credit lines |
| Europe/Japan/India | ESA PhiSat, JAXA OHISAMA, ISRO I-STAR | Government R&D with industry partnerships | Agency budgets |

Notable: There is limited international cooperation in orbital computing compared to other space domains, with national security and data sovereignty concerns driving independent programs.

---

## 6. Key Academic Research

### 6.1 Core Academic Papers

**"Orbital Data Centers: Spacecraft Constraints and Economic Viability"**
- Author: Slava G. Turyshev (Jet Propulsion Laboratory, Caltech)
- Published: April 29, 2026, arXiv:2604.27197
- Key Finding: A representative 1 MW orbital system requires 5,640 m² of photovoltaic arrays, 2,500 m² of radiators, and 29.4-59 kg/kW mass efficiency. Current launch pricing alone is 3.4-13.5x below the necessary cost threshold. Orbital data centers are economically viable only for edge computing and preprocessing applications in the near term; general computing requires dramatic cost reductions.
- URL: https://arxiv.org/abs/2604.27197

**"Deep Tech to Space: Space Data Centers and AI Revolution at the Edge"**
- Published: May 2026, arXiv:2605.19892
- Examines the intersection of deep tech innovation and orbital AI infrastructure
- URL: https://arxiv.org/abs/2605.19892

**"Reliability and Risk in Space-Based Data Centers: A Lifecycle Assessment of Orbital Cloud Infrastructure"**
- Published: 2026, Applied Sciences, DOI: 10.3390/app16115247
- Covers lifecycle-oriented reliability across launch, orbital operation, maintenance, and end-of-life phases
- URL: https://doi.org/10.3390/app16115247

**"Tether-Based Architecture for Solar-Powered Orbital AI Data Centers"**
- Published: December 2025, arXiv:2512.09044
- Proposes novel tethered satellite architectures for thermal management and power distribution
- URL: https://arxiv.org/pdf/2512.09044

**"Space-CIM: Enabling Compute-In-Memory Accelerators for Thermally-Constrained Space Platforms"**
- Published: June 2026, arXiv:2606.05741
- Addresses the thermal constraints of space computing through novel compute-in-memory architectures
- URL: https://arxiv.org/pdf/2606.05741

**"Revolutionizing Wireless Communications with Space Data Centers: Applications and Open Challenges"**
- Published: June 2026, arXiv:2606.13086
- Explores communications architectures for orbital computing constellations
- URL: https://arxiv.org/pdf/2606.13086

### 6.2 Policy and Governance Research

**"Orbital Data Centers' Feasibility Gap Is a Governance Risk"**
- Author: Lauren Tokos
- Published: June 25, 2026, Brookings Institution
- Key Finding: The regulatory environment "lacks the interagency coordination necessary for ensuring space communications claims are rigorously assessed." Companies can exploit regulatory gaps unless space communication policy catches up with the market.
- URL: https://www.brookings.edu/articles/orbital-data-centers-feasibility-gap-is-a-governance-risk/

**University of Virginia — National Security Data and Policy Institute:**
- "Evaluating Space-Based Data Center Architectures: Capabilities, Constraints, and Trade-Offs"
- Examines national security implications of orbital computing
- URL: https://nationalsecurity.virginia.edu/research/evaluating-space-based-data-center-architectures-capabilities-constraints-and-trade-offs

### 6.3 What Researchers Say About Feasibility Timelines

Academic consensus on orbital data center feasibility timelines:

| Timeline | Milestone | Confidence |
|----------|-----------|------------|
| 2025-2026 | Prototype hardware in orbit (ACHIEVED) | Confirmed |
| 2027-2028 | Multi-satellite distributed computing demonstrations | High |
| 2029-2031 | Niche commercial viability (edge computing, EO preprocessing) | Moderate |
| 2033-2035 | Broader commercial operations if launch costs reach <$100/kg | Low-Moderate |
| ~2040 | Full levelized-cost parity with terrestrial data centers | Speculative |

**Current cost gap:** Space compute is over 4x terrestrial cost, projected to narrow to ~30% premium by the early 2030s (Luminix, 2026, "Data Centers in Space: Feasibility & Economics," https://www.useluminix.com/reports/industry-analysis/data-centers-in-space).

**The "Physics Wall" — Thermal Management:**
The most significant unsolved engineering challenge is heat rejection. In vacuum, heat can only be removed through radiation, requiring massive radiators. A single NVIDIA H100 GPU (350W) requires ~1.1 m² of radiator surface. A 10 MW orbital data center could require 200,000-1,000,000 kg in radiators alone, translating to $20-100M just for thermal management infrastructure (SatNews, 2026, "The 'Physics Wall': Orbiting Data Centers Face a Massive Cooling Challenge," https://satnews.com/2026/03/17/the-physics-wall-orbiting-data-centers-face-a-massive-cooling-challenge/; ACT, "Cooling Orbital Data Centers," https://www.1-act.com/resources/blog/orbital-data-centers-the-challenge-of-cooling-compute-in-space/).

**Market Projection:** The in-orbit data center market is valued at $1.77 billion by 2029 and projected to reach $39.09 billion by 2035 at a 67.4% CAGR (BusinessWire/ResearchAndMarkets, 2025, https://www.businesswire.com/news/home/20250421770595/en/In-Orbit-Data-Centers-Market-Analysis-2025).

---

## 7. Sources and Bibliography

### Primary Sources — Space Agencies and Companies

1. HPE. "HPE Spaceborne Computer-2 Returns to the International Space Station." January 29, 2024. https://www.hpe.com/us/en/newsroom/press-release/2024/01/hpe-spaceborne-computer-2-returns-to-the-international-space-station.html
2. HPE. "Accelerating Space Exploration with the Spaceborne Computer." https://www.hpe.com/us/en/compute/hpc/supercomputing/spaceborne.html
3. ISS National Lab. "Hewlett Packard Enterprise Expanding Space Computing." https://issnationallab.org/press-releases/release-ng20-hpe-spaceborne-computer2/
4. ISS National Lab. "On the Edge of the Edge: Taking Supercomputing to Space." https://issnationallab.org/upward/hpe-supercomputing-return-space/
5. ISS National Lab. "Orbital Data Center Launching to ISS." August 2025. https://issnationallab.org/press-releases/orbital-data-center-launching-to-iss-to-advance-space-computing/
6. Intel. "Intel Powers First Satellite with AI on Board." October 2020. https://download.intel.com/newsroom/archive/2025/en-us-2020-10-20-intel-powers-first-satellite-with-ai-on-board.pdf
7. ESA. "OPS-SAT." https://www.esa.int/Enabling_Support/Operations/OPS-SAT
8. ESA Phi-Lab. "Phi-Sats Programme." https://philab.esa.int/flagship-programmes/phi-sats-programme/
9. ESA. "ESA Accelerates the Race Towards Clean Energy from Space." https://www.esa.int/Space_in_Member_States/United_Kingdom/ESA_accelerates_the_race_towards_clean_energy_from_space
10. NVIDIA Newsroom. "NVIDIA Launches Space Computing, Rocketing AI Into Orbit." March 16, 2026. https://nvidianews.nvidia.com/news/space-computing
11. NVIDIA. "Space Computing: On-Orbit AI & Accelerated Computing." https://www.nvidia.com/en-us/edge-computing/space-computing/
12. Kepler Space. "Kepler Deploys First Space-Based, Scalable Cloud Infrastructure Powered by NVIDIA." March 16, 2026. https://kepler.space/kepler-deploys-first-space-based-scalable-cloud-infrastructure-powered-by-nvidia/
13. Caltech. "Space Solar Power Project Ends First In-Space Mission with Successes and Lessons." January 2024. https://www.caltech.edu/about/news/space-solar-power-project-ends-first-in-space-mission-with-successes-and-lessons
14. Orbital Inc. https://orbital.inc/
15. Satellogic. "Pushing Intelligence to the Edge." March 2025. https://satellogic.com/2025/03/20/pushing-intelligence-to-the-edge-satellogics-vision-for-ai-powered-earth-observation/
16. Honeywell Aerospace. "Multiplexer/Demultiplexer (MDM)." https://aerospace.honeywell.com/us/en/products-and-services/product/hardware-and-systems/space/multiplexer-demultiplexer

### News and Industry Analysis

17. GeekWire. "Lumen Orbit Changes Its Name to Starcloud and Raises $10M for Space Data Centers." 2025. https://www.geekwire.com/2025/lumen-orbit-starcloud-10m-space-data-centers/
18. Data Center Dynamics. "Lumen Orbit Raises $2.4M for Space Data Centers." 2024. https://www.datacenterdynamics.com/en/news/lumen-orbit-raises-24m-for-space-data-centers/
19. SpaceNews. "China Backs Orbital Data Center Startup with $8.4 Billion in Credit Lines." 2026. https://spacenews.com/china-backs-orbital-data-center-startup-with-8-4-billion-in-credit-lines/
20. Forbes. "Google Plans To Run AI Data Centers In Space With Project Suncatcher." November 11, 2025. https://www.forbes.com/sites/anishasircar/2025/11/11/google-unveils-project-suncatcher-to-run-ai-on-solar-satellites-in-orbit/
21. SpaceNews. "Space-Based Solar Power Startup Aetherflux Enters Orbital Data Center Race." 2026. https://spacenews.com/space-based-solar-power-startup-aetherflux-enters-orbital-data-center-race/
22. TechCrunch. "Space Solar Startup Aetherflux Raises $50M to Launch First Space Demo in 2026." April 2, 2025. https://techcrunch.com/2025/04/02/space-solar-startup-aetherflux-raises-50m-to-launch-first-space-demo-in-2026
23. IEEE Spectrum. "Orbital Inference Data Center Bets On Space GPUs." May 10, 2026. https://spectrum.ieee.org/orbital-inference-data-center
24. Introl Blog. "Orbital Data Center Race 2026." 2026. https://introl.com/blog/orbital-data-centers-space-computing-race-2026
25. Introl Blog. "First Orbital Data Center Nodes Reach Space." January 2026. https://introl.com/blog/orbital-data-center-nodes-launch-space-computing-infrastructure-january-2026
26. Singularity Hub. "Spaceflight Nears Its Steamship Era." July 20, 2026. https://singularityhub.com/2026/07/20/space-launch-costs-have-fallen-96-since-1960-they-arent-done-yet/
27. Tom's Guide. "Google and SpaceX in Talks to Launch 'Project Suncatcher' Orbital AI Data Centers." 2026. https://www.tomsguide.com/ai/elon-musk-might-be-right-heres-why-putting-ai-data-centers-in-space-isnt-as-crazy-as-it-sounds
28. Via Satellite. "Are Orbital Data Centers the Next Frontier of AI Infrastructure?" June 2, 2026. https://www.satellitetoday.com/technology/2026/06/02/are-orbital-data-centers-the-next-frontier-of-ai-infrastructure/
29. Xinhua. "From Ground to Orbit: China Eyes Computing in Space." April 25, 2026. https://english.news.cn/20260425/b4368923827e4988af1bd030dd01d9cc/c.html
30. Global Times. "China Pioneers in AI Satellite Deployment in Space." November 2025. https://www.globaltimes.cn/page/202511/1349105.shtml
31. China Daily. "Chinese Tech Firms Race to Build AI Computing Capabilities in Space." December 5, 2025. https://www.chinadaily.com.cn/a/202512/05/WS69323706a310d6866eb2d03e.html
32. Space.com. "Japanese Satellite Will Beam Solar Power to Earth in 2025." 2025. https://www.space.com/japan-space-based-solar-power-demonstration-2025
33. TechSpot. "NASA's Mars Perseverance Rover Uses the Same CPU as Apple's iMac from 1998." 2021. https://www.techspot.com/news/88796-nasa-mars-perseverance-rover-powered-processor-1998.html
34. Big Think. "NASA's Perseverance Rover Has a 1997 Computer Chip Brain. Here's Why." 2021. https://bigthink.com/hard-science/perseverance-rover-brain/
35. AI Magazine. "Intel and ESA Launch Experimental AI Satellite PhiSat-1." 2020. https://aimagazine.com/ai-applications/intel-and-esa-launch-experimental-ai-satellite-phisat-1
36. SatNews. "The 'Physics Wall': Orbiting Data Centers Face a Massive Cooling Challenge." March 17, 2026. https://satnews.com/2026/03/17/the-physics-wall-orbiting-data-centers-face-a-massive-cooling-challenge/
37. Orbital Intel. "Launch Cost Per Kg: From $54,500 to $1,500." 2026. https://orbital-intel.com/launch-cost-history/

### Academic and Research Papers

38. Turyshev, S.G. "Orbital Data Centers: Spacecraft Constraints and Economic Viability." arXiv:2604.27197. April 29, 2026. https://arxiv.org/abs/2604.27197
39. "Deep Tech to Space: Space Data Centers and AI Revolution at the Edge." arXiv:2605.19892. May 2026. https://arxiv.org/abs/2605.19892
40. "Reliability and Risk in Space-Based Data Centers." Applied Sciences, 2026. https://doi.org/10.3390/app16115247
41. "Tether-Based Architecture for Solar-Powered Orbital AI Data Centers." arXiv:2512.09044. December 2025. https://arxiv.org/pdf/2512.09044
42. "Space-CIM: Enabling Compute-In-Memory Accelerators for Thermally-Constrained Space Platforms." arXiv:2606.05741. June 2026. https://arxiv.org/pdf/2606.05741
43. "Revolutionizing Wireless Communications with Space Data Centers." arXiv:2606.13086. June 2026. https://arxiv.org/pdf/2606.13086
44. Tokos, Lauren. "Orbital Data Centers' Feasibility Gap Is a Governance Risk." Brookings Institution. June 25, 2026. https://www.brookings.edu/articles/orbital-data-centers-feasibility-gap-is-a-governance-risk/
45. University of Virginia NSDPI. "Evaluating Space-Based Data Center Architectures." 2026. https://nationalsecurity.virginia.edu/research/evaluating-space-based-data-center-architectures-capabilities-constraints-and-trade-offs
46. "The OPS-SAT Case: A Data-Centric Competition for Onboard Satellite Image Classification." Astrodynamics, Springer Nature, 2023. https://link.springer.com/article/10.1007/s42064-023-0196-y

### Market Research

47. BusinessWire/ResearchAndMarkets. "In Orbit Data Centers Market Analysis 2025." April 21, 2025. https://www.businesswire.com/news/home/20250421770595/en/In-Orbit-Data-Centers-Market-Analysis-2025
48. Luminix. "Data Centers in Space: Feasibility & Economics (Mid-2026)." 2026. https://www.useluminix.com/reports/industry-analysis/data-centers-in-space

### Additional References

49. ACT. "Cooling Orbital Data Centers." https://www.1-act.com/resources/blog/orbital-data-centers-the-challenge-of-cooling-compute-in-space/
50. eoPortal. "Onboard Data Processing." https://www.eoportal.org/other-space-activities/onboard-data-processing
51. eoPortal. "PhiSat-1 & -2 Nanosatellite Mission." https://www.eoportal.org/satellite-missions/phisat-1
52. Ubotica Technologies. "Satellite Successfully Applies AI to Process Earth Observation Imagery In-flight." https://ubotica.com/satellite-successfully-applies-ai-to-process-earth-observation-imagery-in-flight-in-historic-first-for-space/
53. Palantir Blog. "Edge AI in Space." https://blog.palantir.com/edge-ai-in-space-93d793433a1e
54. Planetek Italia. "Third AI-eXpress Satellite in Orbit." November 2025. https://www.planetek.it/en/news_events/news_archive/2025/11/third_ai_express_satellite_in_orbit_for_a_new_era_of_edge_intelligence_in_space
55. Lockheed Martin. "AI/ML for Mission Processing Onboard Satellites." 2022. https://www.lockheedmartin.com/content/dam/lockheed-martin/space/documents/ai-ml/
56. ISRO/India Strategic. "ISRO Explores Establishing Orbiting AI Data Centres." 2026. https://www.indiastrategic.in/isro-explores-establishing-orbiting-ai-data-centres/
57. Forbes. "NASA Chooses This Brand For Its Laptops Aboard The ISS." 2016. https://www.forbes.com/sites/quora/2016/05/14/what-kind-of-laptops-are-on-the-iss/
58. Thales Alenia Space. "ESA Chooses Thales Alenia Space for SOLARIS Feasibility Study." https://www.thalesaleniaspace.com/en/press-releases/esa-chooses-thales-alenia-space-solaris-feasibility-study
59. New Atlas. "Aetherflux: Space Solar Startup Aims for 2026 Laser Power Demo." 2026. https://newatlas.com/energy/laser-beamed-space-solar-power-aetherflux-2026-test/
60. SpaceOrbitals. "How Cheap Is Starship V3 Really?" 2026. https://spaceorbitals.com/articles/starship-v3-cost-per-kg-2026/
