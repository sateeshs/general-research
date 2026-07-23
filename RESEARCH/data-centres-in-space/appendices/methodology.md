# Research Methodology

**Project:** Data Centres in Space
**Date:** July 2026
**Framework:** 7-Phase Deep Research with Graph of Thoughts

---

## Research Design

### Phase 1: Question Scoping

**Primary Question:** What is the current state, technical feasibility, economic viability, environmental impact, and regulatory landscape of proposals to build data centres in space?

**Triggered by:** [Pixalytics article](https://www.pixalytics.com/data-centres-in-space/) reporting FCC filings for 100,000+ satellite data centre constellations.

**Scope boundaries:**
- Temporal: 2017 (HPE Spaceborne Computer) through July 2026
- Geographic: Global (US, China, EU, Japan, India)
- Technical: LEO orbital computing only (not lunar or deep space)
- Economic: Commercial viability and cost analysis
- Environmental: Debris, atmospheric, light pollution impacts

### Phase 2: Retrieval Planning

Decomposed into 5 research subtopics, each assigned to a parallel agent:

| Agent | Focus Area | Search Strategy |
|-------|-----------|-----------------|
| 1 | Companies & Initiatives | Company filings, press releases, investor reports |
| 2 | Technical Feasibility | Engineering papers, NVIDIA specs, thermal analysis |
| 3 | Environmental / Debris / Regulatory | ESA reports, IAU positions, legal frameworks |
| 4 | Market & Economics | Market reports, VC data, cost analysis |
| 5 | History & Precedents | NASA archives, HPE reports, academic papers |

### Phase 3: Iterative Querying

Each agent executed 10-20 web searches across diverse sources:
- News outlets (SpaceNews, GeekWire, TechCrunch, IEEE Spectrum)
- Government/agency sources (ESA, NASA, FCC, NOAA)
- Academic papers (arXiv, Nature, MNRAS, Applied Sciences)
- Industry analysis (Gartner, IEA, SIA, ResearchAndMarkets)
- Company sources (official websites, press releases)
- Policy/think tanks (Brookings, Congressional Research Service)

### Phase 4: Source Triangulation

Cross-validated claims across multiple sources:
- FCC filing details verified against SpaceNews + company press releases
- Debris statistics cross-referenced: ESA reports + academic papers + industry trackers
- Funding figures verified across TechCrunch + GeekWire + SpaceNews
- Technical specifications verified against IEEE Spectrum + NVIDIA announcements + arXiv papers

### Phase 5: Knowledge Synthesis

Combined findings from 5 agents into structured output:
- Executive summary (key findings, conclusions)
- Full reports (3 major documents, 1,850+ lines total)
- Statistics compilation (quantified data tables)
- Source quality assessment (A-E ratings)

### Phase 6: Quality Assurance

- Citation validation: verified URL accessibility and attribution accuracy
- Cross-reference check: confirmed key claims appear in multiple independent sources
- Bias assessment: included both pro-orbital and skeptical perspectives
- Temporal accuracy: ensured dates and timelines are internally consistent

### Phase 7: Output & Packaging

Generated structured research directory with:
- README with navigation
- Executive summary
- Agent reports (5)
- Statistics compilation
- Bibliography with quality ratings
- Methodology documentation
- Limitations acknowledgment

## Source Selection Criteria

**Included:**
- Peer-reviewed academic papers
- Government and space agency reports
- Established technology/space industry news outlets
- Company official communications
- Policy institute analyses

**Excluded:**
- Social media speculation
- Unattributed blog posts without verifiable claims
- Sources behind hard paywalls where content couldn't be verified
- Pre-2020 sources (except for historical context)

## Graph of Thoughts Pattern

Used **Balanced** pattern for this research:
- Generate(5): Spawned 5 parallel research agents
- Score: Rated initial findings for completeness and source quality
- Deepen: Agents performed iterative search refinement
- Aggregate: Synthesized across all 5 agent outputs
- Refine: Cross-validated and filled gaps

## Tools Used

- WebSearch: Primary research queries (50+ searches)
- WebFetch: Source article retrieval and verification
- Agent: Parallel research agent deployment
- TaskCreate/TaskUpdate: Progress tracking
