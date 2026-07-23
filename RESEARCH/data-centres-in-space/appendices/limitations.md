# Research Limitations

**Project:** Data Centres in Space
**Date:** July 2026

---

## Known Gaps

### 1. Classified/Proprietary Information
- DARPA programs for space-based AI are classified; scope and budget unknown
- SpaceX Starmind detailed technical specifications (beyond AI1) are proprietary
- Blue Origin Project Sunrise satellite design details not publicly disclosed
- Exact GPU counts per satellite for most companies are undisclosed

### 2. Cost Analysis Limitations
- True cost-per-GPU-hour in orbit is not publicly reported by any company
- Launch cost projections (especially Starship at $100-200/kg) are manufacturer claims, not independently verified
- Manufacturing cost per satellite is not disclosed
- Operating cost models are proprietary

### 3. Technical Feasibility Uncertainty
- Long-term radiation degradation rates for NVIDIA Space-1 GPUs are not yet empirically validated in orbit
- Thermal management at scale (>1 MW) is modeled but not demonstrated
- Inter-satellite optical link performance at constellation scale is theoretical
- Mean time between failure for space compute hardware lacks statistically significant orbital data

### 4. Environmental Impact Modeling
- Atmospheric effects of aluminium oxide from mass satellite reentry are based on projections, not observed megaconstellation reentries
- Ozone depletion models for 1,000+ annual launches are extrapolations from current launch rates
- Cumulative Kessler Syndrome probability for 1M+ satellite scenarios has not been rigorously simulated
- Light pollution models for data centre constellations specifically (vs. communications) are scarce

### 5. Market/Economic Projections
- $39.09B market projection (2035) at 67.4% CAGR comes from a single market research firm
- No independent cost-benefit analysis comparing full lifecycle orbital vs. terrestrial DC costs exists
- Revenue model viability (GPU-as-a-service from orbit) is untested at any scale

### 6. Regulatory Evolution
- FCC treatment of million-satellite filings is evolving in real-time; no precedent exists
- EU Space Act is still in draft form
- ITU spectrum allocation for orbital computing (vs. communications) has not been specifically addressed
- No international framework for orbital computing governance exists

## Potential Biases

### Source Bias
- Company press releases and investor materials naturally emphasize viability and minimize risks
- Environmental advocacy sources may overstate near-term risks
- Academic papers from JPL/Caltech may reflect NASA institutional perspectives
- Chinese state media sources may overstate program progress

### Temporal Bias
- Research conducted during peak hype cycle for orbital computing (mid-2026)
- Several companies are pre-revenue startups with aspirational timelines
- FCC filings represent intent, not commitment; most filings historically are not fully deployed

### Selection Bias
- English-language sources dominate; Chinese-language technical literature underrepresented
- US and European companies are better documented than Chinese/Indian programs
- Academic papers accessible via open access (arXiv) are overrepresented vs. paywalled journals

## What Would Change This Assessment

1. **Starship achieving $100/kg**: Would fundamentally alter the cost analysis
2. **First satellite failure cascade**: Would dramatically shift risk assessment
3. **NVIDIA Space-1 real-world performance data**: Would clarify the radiation/performance trade-off
4. **FCC environmental assessment requirement**: Would change regulatory landscape
5. **Successful 100+ satellite distributed computing demo**: Would validate technical architecture at scale
6. **Independent lifecycle cost analysis**: Would either validate or refute economic claims
