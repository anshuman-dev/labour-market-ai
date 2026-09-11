# Build Brief: "A Billion Prices Project for India's AI Labor Impact"
For handoff to Claude Code. This is a spec, not final copy. Every section lists the insight, the exact data, the recommended visual, and the source.

---

## 0. Framing (for the whole page)
**Hypothesis (method-level):** A high-frequency, bottom-up approach (the same logic Cavallo used for prices) can track AI's labor effect in India faster and more honestly than static, survey-based exposure maps.
**Structure:** scrollytelling, single page, sticky scroll-progress nav, hover tooltips on every chart, expandable "sources" footnote per section.

---

## Section 1: Hero
**Visual:** animated counter on load.
**Candidate stats (pick one or rotate):**
- "15x, how much faster Indian Claude users complete complex tasks with AI, vs. 12x globally" (Anthropic India Brief, Feb 2026)
- "23,460: net jobs cut at TCS in FY26, its largest single-year reduction ever"
- "50.7%: share of Infosys's workforce under 30, the lowest in 15 years"

---

## Section 2: What was the Billion Prices Project
**Visual:** simple annotated diagram (scraped price dots → index line), callout on Argentina CPI manipulation catch. No hard data needed here; explainer only.

---

## Section 3: Our reframed hypothesis
**Visual:** side-by-side mapping card.
| Original (Cavallo) | Ours |
|---|---|
| Millions of scraped online prices | Job ad text, hiring/headcount disclosures, AI usage data, wage bands |
| → real-time inflation index | → real-time AI labor-impact index |
| Validated against official (sometimes manipulated) CPI | Validated against PLFS/CMIE (slow, contested employment data) |

---

## Section 3.5: How we'd actually build this (methodology)
**Placement:** immediately after Section 3 (reframing), before the Pizzinelli critique. Visible on the main page in full; this is not a teaser, it needs to stand on its own as a real methodology. A separate, deeper "how we'd build this" panel holds the technical appendix (spec below).

### Visible on main page: four concrete steps

**1. Fixing the occupation crosswalk.**
Exposure scores like AIOE are built on US O*NET task data. Pizzinelli et al. mapped these onto India via ISCO-08 codes, but this assumes a "software developer" in the US and in India involve the same tasks, which is shaky given India's IT sector is disproportionately delivery/execution-heavy (offshore services model) rather than the design/architecture-heavy mix implied by US task data.
**Our fix:** use the same crosswalk as a starting point, but spot-audit a sample of matched occupations against real Indian job descriptions to check whether task content genuinely matches; flag and adjust the likely mismatches, starting with IT services roles.

**2. Building the job-ad signal.**
Pull postings monthly from Naukri, LinkedIn India, and Indeed India. Tag each posting by occupation (title + description matched to NCO codes). Classify AI-skill demand using a keyword-seeded, embedding-expanded classifier; seed terms like "GenAI," "LLM," "prompt engineering," "Copilot," expanded via semantic similarity so postings describing AI work without our exact keywords aren't missed. Track: share of AI-tagged postings and listed salary bands, per occupation, per month.

**3. Proving causation, not coincidence.**
Difference-in-differences design: occupation × month as the unit, AI exposure score as treatment intensity, event time anchored to GenAI's India adoption inflection (~late 2022/2023). Outcomes: posting growth, wage growth, hiring volume. Critical check: exposed and non-exposed occupations must show parallel trends *before* 2023, otherwise the result is confounded. Add a geography split (IT-hub states vs. non-IT states) as a triple-difference check, specifically to rule out the 2023-24 global IT-spending slowdown as the real driver instead of AI.

**4. Checking if it's actually working.**
Compare the monthly index against PLFS (quarterly) and CMIE (monthly) official employment data. The direct test of the whole hypothesis: does the faster index *lead* the slow official numbers, the way BPP led CPI, especially around known inflection points like the 2025-26 IT hiring slowdown.

### Expandable panel / linked deep-dive page: spec
Content that would drown the main narrative if inlined, but should exist one click away:
- Full NCO ↔ ISCO ↔ O*NET crosswalk table for the top 30-40 occupations by employment share, with flagged mismatches from the audit step.
- Full regression specification: functional form, fixed effects (occupation, month, state), clustering approach, and the exact parallel-trends test/plot.
- Classifier technical design: embedding model choice, seed-term list, validation approach (precision/recall on a hand-labeled sample), and how the classifier handles Hindi/regional-language postings.
- Sensitivity checks: re-running the whole pipeline with Eloundou et al.'s GPT-exposure scores instead of AIOE, to see if conclusions hold under a different exposure measure.
- Scraping architecture notes and ToS/legal considerations for each platform (Naukri, LinkedIn, Indeed).
- Sample-size and statistical power discussion: how many postings/months are needed before the DiD estimates are reliable.

---

## Section 4: The static picture (critique of Pizzinelli et al., IMF WP 23/216)
**Source:** Pizzinelli, Panton, Tavares, Cazzaniga & Li (2023), IMF Working Paper 23/216.

**Chart A, 2x2 quadrant scatter:** AI Exposure (AIOE) vs. Complementarity (θ), India occupations plotted, median reference lines.

**Chart B, small-multiples bar, % of workforce in "high exposure" occupations, by country:**
| Country | Total high-exposure | High-exposure + high-complement (benefit) | High-exposure + low-complement (risk) |
|---|---|---|---|
| India | 26% | 14% | 12% |
| Brazil | ~40% | ~20% | ~20% |
| Colombia | ~40% | ~20% | ~20% |
| South Africa | ~40% | ~20% | ~20% |
| US | N/A | 49.8% | 29.7% |
| UK (highest overall) | N/A | 51.9% | 32% |

**Callout stat:** 70% of Indian workers fall below just the 40th percentile of AIOE (vs. 25% in the UK), driven by agriculture (>30% of employment).

**Callout card, the gender flip:** India is the *only* country in the study where women show *lower* AI exposure than men (24% vs. 28%), because women are concentrated in agriculture. Every other country in the sample shows the opposite (e.g., US: women 68% vs. men 51%; Brazil: women 52% vs. men 32%).

**Data-staleness callout:** India's numbers come from PLFS 2018-19, pre-ChatGPT, and were coded at a coarser 3-digit occupation level vs. 4-digit for other countries in the study.

---

## Section 5: The dynamic evidence
**Source A:** Copestake, Marczinek, Pople & Stapleton, "AI and Services-Led Growth: Evidence from Indian Job Adverts" (2023, updated 2024-25). Near-exponential AI-skill demand growth in Indian job postings since 2016, concentrated in IT/finance/professional services; negative effect on non-AI postings and top-percentile wages, concentrated in high-skilled managerial/professional, non-routine roles.
*(Chart: line, "AI-skill demand share in job postings, 2016-2021," reconstructed at illustrative shape from paper's reported trend; flag as approximate/illustrative pending access to raw series.)*

**Source B, company-level real numbers (toggle between companies, same chart shape):**
| Company | Metric | Value |
|---|---|---|
| TCS | FY26 headcount | 584,000 (down 23,460 from FY25), incl. ~12,000-role layoff explicitly tied to AI/restructuring |
| Infosys | Under-30 workforce share | 50.7% FY26 (down from 53% FY25; lowest in 15 years; was ~two-thirds until FY18) |
| Infosys | Fresher hires FY26 | 20,000 (target met) |
| Infosys | AI-skill engineer pay | Up to ₹21 lakh/yr, several times standard fresher package |
| Reliance | New hires FY26 vs FY25 | ~1 lakh+ (down from 1.9 lakh in FY25, a cut of ~90,000) |
| Xpheno | Entry-level tech openings (0-2 yrs) | 10,000 (May 2026) vs 13,000 (May 2025), 44% YoY decline |
| Sector-wide | Net industry headcount | +~1.4 lakh (to ~59 lakh professionals) despite Big-4 cuts; compositional shift, not aggregate collapse |

---

## Section 6: Anthropic India Brief (live pulse)
**Source:** Anthropic, "India Country Brief: The Anthropic Economic Index" (Feb 16, 2026), based on Nov 2025 data.

**Map, India choropleth, share of national Claude.ai usage by state:**
| State | Share |
|---|---|
| Maharashtra | 15.5% |
| Tamil Nadu | 13.2% |
| Karnataka | 12.7% |
| Delhi | 10.5% |
(combined >50% of India's total usage)

**Global standing:**
- India: 5.8% of global Claude usage (2nd after US's 21.6%)
- Per-capita rank (Anthropic AI Usage Index): 101st of 116 countries

**Radar/spider chart, India vs. global average ("economic primitives"):**
| Metric | India | Global |
|---|---|---|
| Task speedup | 15x (14.8 min for a 3.8 hr task) | 12x (15.4 min for a 3.1 hr task) |
| Work-related use | 51.3% | 46% |
| Coursework use | 20.9% | 19.3% |
| Personal use | 27.8% | 34.7% |
| AI autonomy delegation (1-5) | 3.60 | 3.38 |
| Tasks human could do alone | 84.6% | 87.9% |
| Human prompt education level | 12.2 yrs | N/A |
| AI response education level | 12.5 yrs (top 10% globally) | N/A |

**Bar, occupational task mix:** India 45.2% software-related tasks (highest of any country) vs. Vietnam 42.1%, Egypt 39.2%.

---

## Section 7: The "canary" cohort
**India data:** Infosys under-30 workforce share: two-thirds (until FY18) → 53% (FY25) → 50.7% (FY26, lowest in 15 years). Plot as single annotated trend line.

**US reference inset (clearly labeled as US, not India):** Brynjolfsson, Chandar & Chen, "Canaries in the Coal Mine?" (Stanford, rev. Aug 2026), using ADP payroll data (millions of workers, 730 occupations, monthly). Employment for 22-25-year-olds in AI-exposed occupations ~19% below counterfactual as of mid-2026; effect driven by reduced hiring, not layoffs; concentrated in occupations where AI *automates* rather than *augments*. Software developers age 22-25 specifically down ~20% from Oct-2022 peak to July 2025.

---

## Section 8: What we can't see (honest limitations)
**Visual, iceberg diagram:** visible tip = formal, urban, English-speaking workforce covered by our proxies (job portals, EPFO, listed-company disclosures); submerged mass = India's large informal workforce, largely invisible to all of these sources.

**Checklist, data infrastructure gap:**
| Has population-wide administrative payroll/wage register? | |
|---|---|
| US (ADP) | Yes, monthly, individual-level, 730 occupations |
| Denmark (Statistics Denmark) | Yes, linked to worker surveys |
| India (EPFO) | No, monthly aggregate by industry only, not individual-level |

**Caution callout:** Humlum & Vestergaard, "Still Waters, Rapid Currents" (Denmark, NBER/Rockwool 2025-26), using 25,000 workers linked to full administrative wage/hours records, found *precise null effects on earnings and hours* two years post-ChatGPT (ruling out effects >2%), despite widespread adoption. What moved instead: task composition and occupational mobility. **Lesson for our page: don't overclaim a clean wage effect. Even in a far more data-rich country, it hasn't been proven yet.**

---

## Section 9: Our proposed live index (interactive payoff)
**Visual:** mock dashboard, one composite line ("Illustrative AI Labor Impact Index for India") built from three sub-signals.
**Interaction:** three sliders (Wage signal / Hiring signal / Usage signal weight) that reshape the composite line live when adjusted. Purely illustrative/synthetic data; label clearly as a demo of the *method*, not a real published index.

---

## Section 10: Verdict
**Closing card, plain text, 2-3 bullets:**
- The method works in principle: Copestake et al. already proved job-ad-based tracking detects real AI labor effects in India.
- Anthropic's own India data + TCS/Infosys/Xpheno numbers show the signal is live and visible right now, concentrated in IT/urban India.
- But India lacks the payroll-level data infrastructure the US and Denmark have, so the index has to stay indirect and proxy-based, and any wage-effect claims should stay cautious (see Denmark null result).

---

## Full source list
1. Pizzinelli, C. et al. (2023). "Labor Market Exposure to AI: Cross-Country Differences and Distributional Implications." IMF WP 23/216.
2. Copestake, A., Marczinek, M., Pople, A., Stapleton, K. (2023, upd. 2024-25). "AI and Services-Led Growth: Evidence from Indian Job Adverts." R&R, Journal of Human Resources.
3. Anthropic (2026). "India Country Brief: The Anthropic Economic Index." Feb 16, 2026.
4. Brynjolfsson, E., Chandar, B., Chen, R. (rev. Aug 2026). "Canaries in the Coal Mine? Six Facts about the Recent Employment Effects of Artificial Intelligence." Stanford Digital Economy Lab.
5. Humlum, A., Vestergaard, E. (2025-26). "Still Waters, Rapid Currents: Early Labor Market Transformation under Generative AI." NBER / Rockwool Foundation Berlin.
6. News/company disclosures: TCS, Infosys, Reliance FY26 filings; Xpheno staffing data (via Outlook Business, June 2026).
