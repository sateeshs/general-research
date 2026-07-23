# Market and Economics of Space-Based Data Centres

**Research Date:** July 2026
**Status:** Deep Research Report - Market Economics Analysis

---

## Table of Contents

1. [AI Compute Demand Growth](#1-ai-compute-demand-growth)
2. [Terrestrial Data Centre Constraints](#2-terrestrial-data-centre-constraints)
3. [Space Economy Size and Growth](#3-space-economy-size-and-growth)
4. [Cost Analysis: Space vs Terrestrial](#4-cost-analysis-space-vs-terrestrial)
5. [Competing Alternative Solutions](#5-competing-alternative-solutions)
6. [Investment and Funding Landscape](#6-investment-and-funding-landscape)
7. [Revenue Models](#7-revenue-models)
8. [Market Projections](#8-market-projections)

---

## 1. AI Compute Demand Growth

### Current Market Scale

The global AI compute market is undergoing explosive expansion. The data center GPU market was valued at approximately $63.22 billion in 2024 and is projected to reach $592.18 billion by 2033, growing at a 28.22% CAGR ([PatentPC, 2025](https://patentpc.com/blog/the-ai-chip-boom-market-growth-and-demand-for-gpus-npus-latest-data)). The "Big Five" hyperscalers alone are expected to drive $600 billion in GPU and data centre spending by 2026 ([Carbon Credits, 2025](https://carboncredits.com/ai-demand-to-drive-600b-from-the-big-five-for-gpu-and-data-center-boom-by-2026/)).

### Training Compute Doubling Rate

Training compute for the largest AI models has been doubling approximately every 6-8 months since the deep learning era began around 2010 ([Epoch AI, 2024](https://epoch.ai/data-insights/cost-trend-large-scale)). However, there are signs of diminishing returns:

- In 2021, doubling compute reliably doubled measurable capability on most benchmarks. By 2025-2026, the same doubling yields progressively smaller improvements ([Medium, 2026](https://medium.com/@siddantvardey/the-frontier-reasoning-models-scaling-laws-whats-actually-coming-next-93bba260644b)).
- Research studying over 400 models found that as datasets grow very large, performance improvements decelerate faster than standard scaling laws predict, due to diminishing data density and redundancy ([Epoch AI, 2025](https://epoch.ai/topics/scaling)).
- OpenAI's Ilya Sutskever stated at NeurIPS 2024 that "pre-training as we know it will unquestionably end" due to peak data constraints ([Medium, 2026](https://medium.com/@siddantvardey/the-frontier-reasoning-models-scaling-laws-whats-actually-coming-next-93bba260644b)).

Despite shifting scaling dynamics, demand continues to grow through inference compute, test-time compute, and new modalities (video, multimodal, agentic AI).

### Inference Compute Growth

While training has received the most attention, inference compute is becoming the dominant workload. As AI models are deployed to billions of users through products like ChatGPT, Copilot, and Gemini, inference demand is scaling faster than training. McKinsey projects that by 2030, about 70% of data centre capacity demand will come from AI workloads, with capacity needs rising from 82 GW in 2025 to 219 GW by 2030 ([McKinsey, 2025](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/the-cost-of-compute-a-7-trillion-dollar-race-to-scale-data-centers)).

### GPU Shortage Timeline

The GPU shortage remains acute as of mid-2026:

- NVIDIA H100 and H200 lead times are running 36-52 weeks due to constrained CoWoS packaging capacity at TSMC and surging HBM demand that exceeds SK Hynix and Micron production capacity ([Spheron, 2026](https://www.spheron.network/blog/gpu-shortage-2026/)).
- Supply constraints from HBM shortages and CoWoS packaging bottlenecks are expected to persist through at least H1 2027 ([Apollo, 2026](https://www.apollo.com/wealth/insights-news/insights/2026/06/growing-compute-shortage)).
- GPUs are scarce, memory prices are surging, TSMC capacity is effectively sold out, and power infrastructure has become a critical bottleneck ([Apollo, 2026](https://www.apollo.com/wealth/insights-news/insights/2026/06/growing-compute-shortage)).

### Total Addressable Market

- Bain estimates the total addressable market for AI-related hardware and software will grow between 40% and 55% annually, reaching between $780 billion and $990 billion by 2027 ([Bain & Company, 2024](https://www.bain.com/insights/ais-trillion-dollar-opportunity-tech-report-2024/)).
- McKinsey projects $6.7 trillion in cumulative global data centre investment will be required by 2030, with $5.2 trillion attributed to AI processing loads ([McKinsey, 2025](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/the-cost-of-compute-a-7-trillion-dollar-race-to-scale-data-centers)).
- Goldman Sachs forecasts data center power demand increasing 165% by 2030 versus 2023 ([Goldman Sachs, 2025](https://thedatascore.substack.com/p/framing-the-solution-219-gigawatts)).
- Global data center electricity consumption rose from approximately 240 TWh in 2023 to 415 TWh in 2024 (a 73% increase), and is forecast to reach over 945 TWh by 2030 ([Tech Insider, 2026](https://tech-insider.org/ai-data-center-power-crisis-2026/)).

---

## 2. Terrestrial Data Centre Constraints

### Power Grid Limitations

Power availability has become the single largest bottleneck for terrestrial data centre expansion:

- **Gartner predicts power shortages will restrict 40% of AI data centers by 2027**, a direct consequence of demand outstripping local grid capacity ([CoreSite, 2026](https://www.coresite.com/blog/data-center-outlook-2026-power-and-cooling-challenges-and-solutions-are-top-of-mind)).
- Global data center electricity demand is estimated to exceed 1,000 TWh by 2026, roughly double the 2023 baseline ([Tech Insider, 2026](https://tech-insider.org/ai-data-center-power-crisis-2026/)).
- In the U.S., PJM's Independent Market Monitor attributes approximately 7.9 GW of additional data center demand in 2025/26 and roughly 12 GW in 2026/27 ([EnkiAI, 2026](https://enkiai.com/data-center/ai-data-center-grid-strain-power-halts-growth-in-2026/)).
- Removing all data centers from PJM's demand forecasts would result in a $9.33 billion (64%) reduction in capacity payments, illustrating the scale of grid strain ([EnkiAI, 2026](https://enkiai.com/data-center/ai-data-center-grid-strain-power-halts-growth-in-2026/)).

### Interconnection Queue Crisis

The U.S. grid interconnection queue has ballooned to a **2,600 GW backlog** as of 2026 ([EnkiAI, 2026](https://enkiai.com/data-center/ai-data-center-energy-2026-2600-gw-queue-pjm-plan/)):

- AI infrastructure projects entering service in 2025 took an average of more than **seven years** to reach operational status ([Data Center Knowledge, 2026](https://www.datacenterknowledge.com/energy-power-supply/why-ai-data-center-projects-face-years-of-delays-after-approval)).
- Projects spent an average of 3+ years reaching an interconnection service agreement, and another 4 years waiting to come online after approval ([Data Center Knowledge, 2026](https://www.datacenterknowledge.com/energy-power-supply/why-ai-data-center-projects-face-years-of-delays-after-approval)).
- In Northern Virginia, grid connections are taking up to 7 years, and transformer lead times run 2-4 years ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space)).
- In some markets, potential delays extend up to 12 years ([Data Center Knowledge, 2026](https://www.datacenterknowledge.com/energy-power-supply/gridlocked-how-power-constraints-are-shaping-the-future-of-data-centers)).

### Water Usage for Cooling

Data centres are significant water consumers, creating tension in water-scarce regions:

- Evaporative cooling systems use approximately **1,800-2,900 litres of water per MW per hour** ([Cloud Computing News, 2025](https://www.cloudcomputing-news.net/news/data-centre-water-consumption-crisis/)).
- A 1 MW data centre can consume up to **25.5 million litres of water annually** for cooling, equivalent to the daily water consumption of approximately 300,000 people ([DGTL Infra, 2025](https://dgtlinfra.com/data-center-water-usage/)).
- Larger data centers can each use up to **5 million gallons per day** (1.8 billion gallons annually), equivalent to a town of 10,000-50,000 people ([Cloud Computing News, 2025](https://www.cloudcomputing-news.net/news/data-centre-water-consumption-crisis/)).
- AI data centres consume **10-50x more cooling water** than traditional server farms ([The Ecologist, 2026](https://theecologist.org/2026/jun/29/data-centres-cooling-drives-heatwave-demand)).
- Southern Nevada has banned evaporative cooling in new developments, forcing dry cooling regardless of the 25-35% energy penalty ([ArXiv, 2026](https://arxiv.org/pdf/2606.21760)).

### NIMBY Opposition

Community resistance to data centre construction has intensified dramatically:

- **Gallup (May 2026) reported that 71% of U.S. adults oppose construction of AI data centres in their local area** ([NBC News, 2026](https://www.nbcnews.com/tech/tech-news/data-center-opposition-sharply-rising-2026-study-finds-rcna349728)).
- Data center opponents blocked or delayed at least **75 projects** nationwide from January through March 2026 alone ([NBC News, 2026](https://www.nbcnews.com/tech/tech-news/data-center-opposition-sharply-rising-2026-study-finds-rcna349728)).
- Projects worth nearly **$130 billion** have been blocked or delayed in 2026 ([NBC News, 2026](https://www.nbcnews.com/tech/tech-news/data-center-opposition-sharply-rising-2026-study-finds-rcna349728)).
- The number of active grassroots opposition groups more than doubled from 396 at the end of 2025 to **833 by March 2026** ([NBC News, 2026](https://www.nbcnews.com/tech/tech-news/data-center-opposition-sharply-rising-2026-study-finds-rcna349728)).
- Over **300 bills** were introduced in statehouses across the country in the first six weeks of 2026 alone ([NBC News, 2026](https://www.nbcnews.com/tech/tech-news/data-center-opposition-sharply-rising-2026-study-finds-rcna349728)).
- **Maine became the first U.S. state to ban new data center construction outright** in April 2026 ([Data Center Knowledge, 2026](https://www.datacenterknowledge.com/energy-power-supply/why-ai-data-center-projects-face-years-of-delays-after-approval)).

### Case Study: Devon, UK

The Xlinks 1.5 GW data centre campus proposal at Alverdiscott, Devon, represents a landmark case of community opposition in Europe:

- Expected to be the **largest data centre in Europe**, spanning 850 acres between Great Torrington, Weare Gifford and Huntshaw ([Farmers Guardian, 2026](https://www.farmersguardian.com/news/4532159/farmers-oppose-huge-centre-north-devon-countryside)).
- The "Leave Devon Alone!" campaign petition gathered over **23,500 signatures** ([North Devon Gazette, 2026](https://www.northdevongazette.co.uk/news/devon-data-centre-open-days-pushed-back-as-petition-gains-23000-signatures-8786644)).
- Concerns include noise, landscape impact, water demand, electricity use, and loss of farmland within the **North Devon UNESCO Biosphere Reserve** ([FarmingUK, 2026](https://www.farminguk.com/news/-13bn-devon-data-centre-plan-delayed-amid-farmland-concerns_68796.html)).
- The UK government subsequently scrapped mandatory public consultation for major infrastructure projects including data centres, provoking further backlash ([The Register, 2026](https://www.theregister.com/2026/01/23/uk_gov_dc/)).

### Permitting Timelines Summary

| Market | Typical Timeline |
|--------|-----------------|
| Northern Virginia | 5-7 years (grid connection) |
| PJM territory (U.S. East) | 7+ years average to operational |
| High-demand U.S. markets | Up to 12 years in worst cases |
| Transformer procurement | 2-4 year lead times |
| UK (Nationally Significant Infrastructure) | 3-5+ years with judicial review risk |

---

## 3. Space Economy Size and Growth

### Current Valuation

The global space economy has reached substantial scale:

- **$626.4 billion in 2025**, growing approximately 8% year-over-year ([Space Foundation, July 2025](https://www.spacefoundation.org/2025/07/22/the-space-report-2025-q2/); [Novaspace, 2025](https://nova.space/press-release/global-space-economy-reaches-626-billion-marking-a-new-phase-of-growth/)).
- Commercial revenue accounts for roughly **80% of the total** ($500B+), with government space budgets contributing approximately **$115 billion** ([Orbital Intel, 2026](https://orbital-intel.com/state-of-space-2026/)).
- The United States dominates with **55% market share** in 2026, representing approximately $259 billion in revenue ([Orbital Intel, 2026](https://orbital-intel.com/state-of-space-2026/)).

### Growth Projections

- Projected to reach **$1.01 trillion by 2034** ([Novaspace, 2025](https://nova.space/press-release/global-space-economy-reaches-626-billion-marking-a-new-phase-of-growth/)).
- SNS Insider projects the market at **$779.66 billion by 2033** at 7.20% CAGR ([SNS Insider via Yahoo Finance, 2026](https://finance.yahoo.com/news/space-economy-market-size-reach-130000220.html)).
- GMI projects growth from $512.7 billion in 2025 to over $1 trillion by 2035 ([GM Insights, 2026](https://www.gminsights.com/industry-analysis/space-economy-market)).

### Venture Capital and Investment

- Private space investment reached **$9-10.1 billion in 2025**, the largest annual increase since the 2021 investment peak ([StartUs Insights, 2026](https://www.startus-insights.com/innovators-guide/spacetech-outlook/)).
- **51% of global space venture capital** flows to American space startups ([Orbital Intel, 2026](https://orbital-intel.com/state-of-space-2026/)).
- SpaceX's Starlink network alone generated an estimated **$10.4 billion in revenue in 2025**, surpassing 9 million subscribers ([Orbital Intel, 2026](https://orbital-intel.com/state-of-space-2026/)).

### Government Space Budgets

- Global government space budgets totalled approximately **$74.7-115 billion** in 2025, depending on the measurement methodology ([StartUs Insights, 2026](https://www.startus-insights.com/innovators-guide/spacetech-outlook/)).
- The U.S. leads with approximately **$80 billion** in annual government space spending ([Orbital Intel, 2026](https://orbital-intel.com/state-of-space-2026/)).
- Defence and sovereignty have emerged as the dominant market drivers, a dynamic expected to persist well into the late 2020s ([StartUs Insights, 2026](https://www.startus-insights.com/innovators-guide/spacetech-outlook/)).

---

## 4. Cost Analysis: Space vs Terrestrial

### Current Cost Comparison (Mid-2026)

As of mid-2026, orbital compute remains significantly more expensive than terrestrial alternatives:

- **Orbital compute costs roughly 4x** what an equivalent terrestrial data center costs ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space)).
- A **1 GW orbital data center constellation** would cost approximately **$51 billion** over five years of operation, compared to roughly **$16 billion** for an equivalent terrestrial facility ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space)).
- Servers (primarily GPUs) account for roughly **60% of total cost of ownership** for AI data centers ([Business Model Analyst, 2026](https://businessmodelanalyst.com/space-data-centers-economics/)).

### Launch Cost Economics

Launch costs are the critical variable determining economic viability:

| Vehicle | Cost per kg to LEO | Status |
|---------|-------------------|--------|
| Falcon 9 (reused) | ~$2,700/kg | Operational |
| Starship (current) | Declining rapidly | Testing/early operations |
| Starship (target, fully reusable) | $100-200/kg | Projected by Musk (May 2026) |

- SpaceX's Starship V3 carries approximately **200 metric tons to LEO** in reusable configuration ([SpaceOrbitals, 2026](https://spaceorbitals.com/articles/starship-v3-cost-per-kg-2026/)).
- Starcloud projects space infrastructure dropping to **$5 billion per GW**, contingent on Starship achieving ~$500/kg commercial launch costs by 2028-2029 ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space)).

### Cost Parity Timeline

- Space compute starts at **>4x terrestrial cost in 2026**, narrows to a **~30% premium by the early 2030s**, and reaches **full levelized-cost parity around 2040** in the base case ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space); [SemiAnalysis, 2026](https://newsletter.semianalysis.com/p/to-boldly-go-the-case-for-space-datacenters)).
- AI compute costs are expected to fall from around **$38.4/watt in 2025 to $3.7/watt by 2040**, primarily because space-based data centres eliminate recurring power and cooling costs ([Upstox, 2026](https://upstox.com/news/upstox-originals/investing/economics-of-space-data-centres-ai-s-next-frontier/article-196817/)).

### Operational Cost Advantages of Space

**Advantages:**
- Unlimited solar power (no grid connection, no electricity bills)
- Passive radiative cooling (no water required)
- No land acquisition costs
- No NIMBY opposition or permitting delays
- No property taxes on orbital assets

**Disadvantages:**
- High upfront launch costs
- Hardware maintenance is extremely difficult/impossible
- Latency for ground-to-orbit communication
- Radiation hardening requirements for electronics
- Limited hardware upgrade path (no GPU swaps)

### The Masayoshi Son Critique

SoftBank founder Masayoshi Son publicly challenged the economics in June 2026, arguing that "electricity savings would be real in orbit, but power makes up only a small share of total data center costs compared with chips and other hardware. Cutting the smaller expense while adding launch costs, maintenance, and communication delays does not clear the bar." He further argued that "the battle for AI, the next few years will be far more important than what might happen a decade or so from now" ([TechTimes, June 2026](https://www.techtimes.com/articles/319218/20260628/orbital-ai-data-centers-son-cites-latency-launch-cost-spacex-race-heats.htm); [TechCrunch, June 2026](https://techcrunch.com/2026/06/27/softbanks-ceo-isnt-the-only-one-with-questions-about-elon-musks-orbital-data-center-hype/)).

### The Foregone Revenue Argument

The strongest economic case for orbital deployment rests not on cost parity but on **opportunity cost**:

- A **1 MW AI cluster generates roughly $70 million per year** in cloud GPU revenue ([Business Model Analyst, 2026](https://businessmodelanalyst.com/space-data-centers-economics/)).
- A **5-year grid queue delay represents about $350 million in foregone revenue per MW** ([SemiAnalysis, 2026](https://newsletter.semianalysis.com/p/to-boldly-go-the-case-for-space-datacenters)).
- This creates economic incentive for orbital deployment despite higher costs for customers who literally cannot access terrestrial power.

---

## 5. Competing Alternative Solutions

### Underwater Data Centres (Microsoft Project Natick)

**Status: Cancelled**

- Microsoft officially confirmed in June 2024 that **Project Natick is no longer active** ([Redmond Magazine, 2024](https://redmondmag.com/articles/2024/06/24/project-natick-dries-up.aspx)).
- The project ran from 2015-2024 and deployed a sealed container of servers on the seafloor off Scotland's Orkney Islands.
- **Key finding:** Underwater data centers saw **one-eighth the failure rate** compared to on-land counterparts, proving the concept's reliability ([Microsoft Research, 2020](https://news.microsoft.com/source/features/sustainability/project-natick-underwater-datacenter/)).
- **Why cancelled:** Noelle Walsh, Corporate VP of Microsoft Cloud Operations, stated: "I'm not building subsea data centers anywhere in the world... We learned a lot about operations below sea level and vibration and impacts on the server" ([IT Pro, 2024](https://www.itpro.com/infrastructure/data-centres/microsoft-scrapped-its-project-natick-underwater-data-center-trial-heres-why-it-was-never-going-to-work)).
- Maintenance and serviceability proved impractical at commercial scale.

### Arctic/Nordic Data Centres

**Status: Growing rapidly**

Nordic data centres represent one of the most mature alternative solutions:

- The Nordic data center market reached approximately **1.32 GW in 2025** and is projected to increase to **1.98 GW by 2031** ([Arizton via PR Newswire, 2026](https://www.prnewswire.com/news-releases/nordic-data-center-construction-market-to-reach-usd-13-81-billion-by-2031--fueled-by-surging-investments-across-norway-sweden-and-finland--arizton-302782985.html)).
- The construction market is expected to grow at a **23.2% CAGR between 2026 and 2035** ([Arizton, 2026](https://www.arizton.com/blog/nordic-data-center-construction-market-growth-trends)).
- Cooling advantages: Average annual temperatures below 10C provide up to **8,000 hours of free-air cooling per year**, enabling facility-level PUE as low as **1.09** ([w.media, 2025](https://w.media/special-feature-just-chill-cooling-innovations-in-nordic-data-centers-setting-new-sustainability-standards/)).
- Iceland is expected to attract around **$4 billion in investments between 2026-2031** ([Arizton, 2026](https://www.arizton.com/blog/nordic-data-center-construction-market-growth-trends)).
- Microsoft committed more than **$1.5 billion** to Nordic data center infrastructure in 2024-2025 combined ([w.media, 2025](https://w.media/special-feature-just-chill-cooling-innovations-in-nordic-data-centers-setting-new-sustainability-standards/)).
- **Key advantage:** Abundant renewable energy (hydropower in Norway, geothermal in Iceland) and competitive electricity pricing.
- **Key limitation:** Latency to major population centres; limited local talent pools; submarine cable capacity.

### Nuclear-Powered Data Centres

**Status: Under development, 2028-2030+ timelines**

Tech giants have committed heavily to nuclear power for data centres:

| Company | Commitment | Details | Timeline |
|---------|-----------|---------|----------|
| Microsoft | $16 billion | Restart Three Mile Island (835 MW) | Target 2028 |
| Google | 500 MW | Fleet deal with Kairos Power (SMRs) | 2030+ |
| Amazon | $20B+ | Susquehanna AI campus + 5 GW X-energy SMRs | 2028+ |
| Meta | 1-4 GW | RFP for new nuclear capacity | TBD |
| Oracle | 1 GW | Three SMRs for single data center | TBD |

- Tech giants have committed over **$10 billion toward SMR development** ([IDTechEx, 2025](https://www.idtechex.com/en/research-article/data-centers-go-nuclear-why-ai-giants-are-investing-in-smrs/34846)).
- The SMR market for data centres was valued at **$6.9 billion in 2025** and is projected to grow to **$13.8 billion by 2032** ([Introl, 2025](https://introl.com/blog/smr-nuclear-power-ai-data-centers-2025)).
- NuScale Power signed agreements for 2 SMRs with Standard Power for data centre applications ([EnkiAI, 2026](https://enkiai.com/nuclear/nuscale-smr-standard-power-data/)).
- **Key advantage:** Reliable baseload power without grid dependency.
- **Key limitation:** No commercial SMR has been deployed yet; regulatory and construction timelines remain uncertain.

### Modular/Edge Data Centres

**Status: Rapidly scaling**

- The modular data center market is growing from **$39.26 billion in 2025 to $47.75 billion in 2026** at a 21.6% CAGR ([Globe Newswire, 2026](https://www.globenewswire.com/news-release/2026/01/30/3229323/0/en/Global-Modular-Data-Center-Market-Set-to-Surge-from-USD-28-44-Billion-in-2025-to-USD-76-11-Billion-by-2031.html)).
- The modular edge data centers market was valued at **$7.29 billion in 2025** and is projected to reach **$25.5 billion by 2034** at 19.8% CAGR ([Intel Market Research, 2026](https://www.intelmarketresearch.com/modular-edge-data-centers-market-28018)).
- The broader edge data center market was valued at **$34.8 billion in 2025**, projected to reach **$105.8 billion by 2033** at 14.9% CAGR ([Grand View Research, 2026](https://www.grandviewresearch.com/industry-analysis/edge-data-center-market-report)).
- Micro-modular data centres are being deployed on urban rooftops, manufacturing floors, and telecom towers ([Grand View Research, 2026](https://www.grandviewresearch.com/industry-analysis/edge-data-center-market-report)).
- **Key advantage:** Faster deployment (weeks vs years), lower capital requirements, proximity to end users.
- **Key limitation:** Limited scale per unit; cannot support large-scale training workloads.

### Efficiency Improvements in Existing Infrastructure

- Microsoft is deploying **closed-loop, zero-water evaporation cooling**, eliminating evaporative water and reducing usage by **125M+ litres per facility annually** ([Cloud Computing News, 2025](https://www.cloudcomputing-news.net/news/data-centre-water-consumption-crisis/)).
- Liquid cooling and immersion cooling technologies are becoming mainstream for high-density GPU deployments.
- New chip architectures (NVIDIA Blackwell, custom ASICs) deliver more compute per watt.
- However, efficiency gains are being outpaced by demand growth.

---

## 6. Investment and Funding Landscape

### Space Data Centre Company Funding

#### Starcloud (formerly Lumen Orbit)

| Round | Amount | Date | Investors | Valuation |
|-------|--------|------|-----------|-----------|
| Seed | $11M | Dec 2024 | NFX, Y Combinator, FUSE, Soma Capital, scout funds from a16z and Sequoia | - |
| Seed extension | $10M | Feb 2025 | - | - |
| Series A | $170M | April 2026 | Benchmark, EQT Ventures (co-leads) | **$1.1 billion** |

- Total raised to date: approximately **$200 million** ([TechCrunch, March 2026](https://techcrunch.com/2026/03/30/starcloud-raises-170-million-series-ato-build-data-centers-in-space); [GeekWire, 2026](https://www.geekwire.com/2026/orbital-ai-seattle-area-startup-starcloud-hits-1-1b-valuation-to-build-space-based-data-centers/)).
- One of the highest-ever seed rounds for a Y Combinator company ([GeekWire, 2025](https://www.geekwire.com/2025/lumen-orbit-starcloud-10m-space-data-centers/)).
- NVIDIA is a backer; Starcloud launched the first AI model trained on an NVIDIA H100 GPU in orbit in November 2025 ([CNBC, December 2025](https://www.cnbc.com/2025/12/10/nvidia-backed-starcloud-trains-first-ai-model-in-space-orbital-data-centers.html)).

#### Orbital

- Received funding from **A16z Speedrun**, Andreessen Horowitz's accelerator program ([AI Business, 2026](https://aibusiness.com/generative-ai/funding-lays-groundwork-orbital-s-ai-data-centers-space)).
- Launched its first test mission in April 2026 ([AI Business, 2026](https://aibusiness.com/generative-ai/funding-lays-groundwork-orbital-s-ai-data-centers-space)).

#### Aetherflux

- Founded by former Robinhood co-founder and CEO Baiju Bhatt.
- Targeting deployment of an orbital data center satellite in **Q1 2027** ([Fierce Network, 2026](https://www.fierce-network.com/cloud/space-data-centers-starcloud-spacex-and-project-suncatcher-explained)).

#### K2 Space

- Raised a **$250 million round** for integrated space systems, one of the largest rounds in the sector ([EnkiAI, 2026](https://enkiai.com/ai-market-intelligence/orbital-data-centers-2026-capital-shifts-to-infrastructure/)).

#### Lonestar Data Holdings

- Working to put the **first commercial lunar data center** on the Moon's surface ([Introl, 2026](https://introl.com/blog/orbital-data-centers-space-computing-race-2026)).

### Corporate Initiatives

#### Google Project Suncatcher

- Unveiled November 2025 as a "moonshot" initiative to put **solar-powered satellites with Google's TPUs** into orbit ([Fierce Network, 2026](https://www.fierce-network.com/cloud/space-data-centers-starcloud-spacex-and-project-suncatcher-explained)).

#### SpaceX

- SpaceX's S-1 filing (ahead of its IPO) included a risk disclosure that **orbital AI data centres "may not be viable"**, even months after Musk called space-based AI a "no-brainer" ([The Next Web, 2026](https://thenextweb.com/news/spacex-orbital-data-centres-ipo-risk-disclosure)).
- SpaceX believes it is the only company with a commercially viable path to building orbital AI compute at scale, due to its unique ability to launch substantial mass at low cost ([TechCrunch, 2026](https://techcrunch.com/2026/06/27/softbanks-ceo-isnt-the-only-one-with-questions-about-elon-musks-orbital-data-center-hype/)).

### Broader Capital Shifts

- From 2025 onward, the scale of capital flowing into space data centres shifted from seed/Series A to **infrastructure-scale investments** ([EnkiAI, 2026](https://enkiai.com/ai-market-intelligence/orbital-data-centers-2026-capital-shifts-to-infrastructure/)).
- CB Insights tracks space-based data centres as a distinct investment category within defence tech and aerospace ([CB Insights, 2026](https://www.cbinsights.com/esp/industrials/defense-tech/space-based-data-centers)).

---

## 7. Revenue Models

### Primary Revenue Streams

#### 1. Cloud GPU-as-a-Service

The dominant revenue model for space data centres:

- A **1 MW AI cluster generates roughly $70 million per year** in cloud GPU revenue ([Business Model Analyst, 2026](https://businessmodelanalyst.com/space-data-centers-economics/)).
- The strategic play is to price space compute at a **30-50% premium** to terrestrial cloud rates, targeting customers who cannot get power elsewhere due to grid queues ([SemiAnalysis, 2026](https://newsletter.semianalysis.com/p/to-boldly-go-the-case-for-space-datacenters)).
- The **5-year grid queue delay = $350 million in foregone revenue per MW**, making even premium-priced orbital compute attractive to power-constrained buyers ([SemiAnalysis, 2026](https://newsletter.semianalysis.com/p/to-boldly-go-the-case-for-space-datacenters)).

#### 2. AI Training Compute

- Starcloud demonstrated LLM training on an NVIDIA H100 GPU in orbit (Starcloud-1 satellite, November 2025) ([CNBC, December 2025](https://www.cnbc.com/2025/12/10/nvidia-backed-starcloud-trains-first-ai-model-in-space-orbital-data-centers.html)).
- Starcloud-2 (planned October 2026) will carry multiple NVIDIA H100 and Blackwell-platform GPUs, enabling larger-scale training workloads ([GeekWire, 2026](https://www.geekwire.com/2026/orbital-ai-seattle-area-startup-starcloud-hits-1-1b-valuation-to-build-space-based-data-centers/)).
- Training workloads that are latency-tolerant (batch processing, fine-tuning) are the best initial fit for orbital compute.

#### 3. Government and Military Contracts

- Defence and sovereignty are the dominant drivers in the space economy, with government budgets of $74.7-115 billion annually ([StartUs Insights, 2026](https://www.startus-insights.com/innovators-guide/spacetech-outlook/)).
- Military and intelligence applications include:
  - Sovereign compute (processing classified data in national orbital assets)
  - Real-time satellite imagery analysis
  - Communications relay processing
  - Resilient compute infrastructure not dependent on terrestrial targets

#### 4. Earth Observation and In-Orbit Processing

- Processing satellite imagery and remote sensing data in orbit, rather than downlinking raw data, reduces bandwidth requirements and enables real-time analytics.
- Companies like Planet already generate substantial revenue from Earth observation data.
- In-orbit edge processing is a natural adjacent market for orbital data centres.

#### 5. Data Sovereignty and Compliance

- Orbital data centres could serve customers requiring data processing outside any national jurisdiction.
- Alternatively, orbital assets registered to specific nations could provide sovereign cloud capabilities.

---

## 8. Market Projections

### Space-Based Data Centre Market Size Forecasts

Multiple analyst projections exist, with significant variance reflecting the sector's uncertainty:

| Source | 2025-2026 Value | Projected Value | CAGR | Notes |
|--------|----------------|----------------|------|-------|
| Fortune Business Insights | $1.44B (2026) | $3.81B by 2034 | 12.96% | Conservative estimate |
| MarketsandMarkets | $500M (2025) | $39B by 2035 | ~50%+ | Aggressive growth scenario |
| Research Intelo | $1.77B (2025) | $105.4B by 2034 | 67.4% | Most bullish projection |
| Futurum Group | - | $1T TAM by 2030 | - | Addressable market, not revenue |

Sources: [Fortune Business Insights, 2026](https://www.fortunebusinessinsights.com/space-based-data-center-market-115870); [MarketsandMarkets, 2026](https://www.marketsandmarkets.com/Market-Reports/space-based-data-center-market-123768087.html); [Research Intelo, 2026](https://researchintelo.com/report/orbital-space-based-data-center-and-ai-compute-market); [Futurum Group, 2026](https://futurumgroup.com/press-release/orbital-computing-can-reach-1-trillion-addressable-market-by-2030/).

### Commercial Viability Timeline

| Milestone | Expected Date | Key Dependency |
|-----------|--------------|----------------|
| First GPU trained in orbit | November 2025 (achieved) | Starcloud-1 with NVIDIA H100 |
| Multi-GPU orbital cluster | October 2026 | Starcloud-2 launch |
| Sustained commercial compute | 2027-2028 | Aetherflux and multiple players |
| Cost-competitive for power-constrained markets | Early 2030s | Starship at $500/kg |
| Levelized cost parity with terrestrial | ~2040 | Starship at $100-200/kg |

Source: [Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space).

### Break-Even Analysis

- The economic case is strongest for **off-grid deployments** where terrestrial alternatives face multi-year power delays ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space)).
- At current costs (~4x terrestrial), space compute is only economically justified when the **opportunity cost of waiting** for grid connections exceeds the premium. At $70M/year revenue per MW and 5-7 year grid delays, the foregone revenue ($350-490M per MW) can exceed the orbital premium.
- Starcloud projects space infrastructure dropping to **$5 billion per GW** (from ~$51B today), contingent on Starship achieving ~$500/kg commercial launch costs by 2028-2029 ([Luminix, 2026](https://www.useluminix.com/reports/industry-analysis/data-centers-in-space)).
- Full break-even at scale requires:
  1. Starship launch costs reaching $200-500/kg (currently in progress)
  2. Radiation-hardened or radiation-tolerant GPU architectures maturing
  3. Inter-satellite optical links enabling distributed compute clusters
  4. Demonstrated hardware reliability over multi-year orbital lifetimes

### Key Risk Factors

1. **SpaceX's own S-1 filing** warns that orbital AI data centres "may not be viable" ([The Next Web, 2026](https://thenextweb.com/news/spacex-orbital-data-centres-ipo-risk-disclosure)).
2. **Latency:** Ground-to-LEO round-trip latency (~20-40ms) limits real-time inference applications.
3. **Hardware obsolescence:** GPU generations turn over every 1-2 years; orbital hardware cannot be upgraded.
4. **Radiation effects:** Cosmic radiation degrades electronics; hardening adds cost and reduces performance.
5. **Competitive alternatives:** Nuclear-powered terrestrial data centres, Nordic locations, and modular solutions may resolve many terrestrial constraints without going to orbit.
6. **Timing mismatch:** Masayoshi Son's critique that the AI race will be decided in the next few years, before orbital compute matures, has merit.

---

## Summary: The Investment Thesis

### Bull Case

- AI compute demand is growing faster than terrestrial infrastructure can be built (7+ year grid queues vs months for orbital deployment).
- $130 billion in blocked/delayed terrestrial projects in 2026 alone creates enormous unmet demand.
- Starship's cost trajectory could make orbital compute cost-competitive by the early 2030s.
- $200M+ already invested in Starcloud alone, with $1.1B valuation signal from Benchmark and EQT Ventures.
- Unlimited solar power and passive cooling eliminate the two most contentious terrestrial constraints (energy and water).

### Bear Case

- Current costs are 4x terrestrial, and cost parity is not expected until ~2040.
- No commercial-scale orbital compute has been demonstrated; only single-GPU proof of concepts.
- Hardware cannot be serviced, upgraded, or repaired in orbit.
- Latency constraints limit the workload types suitable for orbital processing.
- Nuclear SMRs and Nordic locations may resolve power and cooling constraints without the complexity of space.
- SpaceX's own S-1 filing flags viability risk.
- The AI compute race may be decided before orbital infrastructure matures.

### Key Numbers at a Glance

| Metric | Value | Source |
|--------|-------|--------|
| AI compute TAM by 2027 | $780B-$990B | Bain |
| Data centre investment needed by 2030 | $6.7 trillion | McKinsey |
| Terrestrial projects blocked/delayed (2026) | $130 billion | NBC/Data Center Watch |
| U.S. grid interconnection queue | 2,600 GW backlog | EnkiAI |
| Space-based DC market (2026) | $1.44 billion | Fortune Business Insights |
| Space-based DC market (2034 projected) | $3.81B-$105.4B | Various analysts |
| Starcloud valuation (2026) | $1.1 billion | TechCrunch/GeekWire |
| Orbital vs terrestrial cost ratio (2026) | ~4x | Luminix/SemiAnalysis |
| Cost parity target | ~2040 | Luminix/SemiAnalysis |
| Revenue per MW AI cluster | $70M/year | SemiAnalysis |

---

*Report compiled July 2026. All figures sourced from publicly available research, analyst reports, and news coverage as cited. Market projections vary significantly between analysts, reflecting the nascent and speculative nature of the orbital computing sector.*
