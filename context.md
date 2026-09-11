# Build Brief: "A Billion Prices Project for India's AI Labor Impact"
For handoff to Claude Code. This is a spec, not final copy. Every section lists the insight, the exact data, the recommended visual, and the source.

---

## 0. Framing (for the whole page)
**Hypothesis (method-level):** A high-frequency, bottom-up approach (the same logic Cavallo used for prices) can track AI's labor effect in India faster and more honestly than static, survey-based exposure maps.
**Structure:** scrollytelling, single page, sticky scroll-progress nav, hover tooltips on every chart, expandable "sources" footnote per section.

**Voice/tone guardrail, apply across every section, not just the ones flagged below.** V1 copy reads AI-generated in a few consistent ways worth hunting for everywhere:
- Parallel-structure triplets/quadruplets ("fixing X, building Y, proving Z, checking W"). Say it as a person would, once, plainly.
- "Not X, but Y" or "not just X, but Y" constructions ("proving causation, not coincidence"). A dead giveaway pattern, rewrite as a direct statement.
- The same comparison repeated near-identically across multiple sections (the "the way BPP led CPI" line currently shows up three times). Say it once, where it matters most, and vary or drop it elsewhere.
- Over-precise connector phrases ("specifically to rule out," "the direct test of the whole hypothesis"). Replace with how someone would actually explain it out loud.
- A hypothesis stated as a settled conclusion instead of a live question (the current hero headline). The page's honesty (sections 8 and 10) only works if the opening doesn't already assume the answer.

---

## Site-wide navigation: left sidebar with real sub-items

**Reference model:** Skimmaxxer's paper-viewer left nav; instead of listing chapter titles only, it lists the actual sub-claims inside each chapter, numbered and clickable, so a visitor knows exactly what's coming before they scroll. Build the same thing here. This is cheap to build because the sub-items already exist as content inside the brief below; this section just organizes them into nav form.

**Structure:** sidebar stays visible/sticky on desktop, collapses to a top drawer on mobile. Top-level items are the sections (renumbered so 3.5 is its own numbered section). Each top-level item expands to show its sub-items below it. Clicking a sub-item scrolls/jumps directly to that specific claim within the section, not just the top of the section.

**Full sub-item list, section by section:**

**01, The Hypothesis**
- The question we're asking
- The stat that opens it

**02, The Original Method**
- How Cavallo built the price index
- The Argentina catch
- Why this is our inspiration

**03, Our Reframing**
- The original mapping: prices to inflation
- Our mapping: labor signals to AI impact index

**04, The Methodology**
- Step 1: fixing the occupation crosswalk
- Step 2: building the job-ad signal
- Step 3: making sure it's actually AI, not something else
- Step 4: checking the index against official data

**05, The Static Picture**
- The exposure quadrant, explained
- India vs. five other countries
- 70% of Indian workers below the 40th percentile
- The gender flip
- Why the underlying data is stale (2018-19, pre-ChatGPT)

**06, The Dynamic Evidence**
- Copestake's job-ad findings
- TCS's headcount cut
- Infosys's under-30 share
- Xpheno's entry-level hiring drop
- Reliance's hiring pullback
- The sector-wide picture: compositional shift, not collapse

**07, The Live Pulse (Anthropic India Brief)**
- Usage by state, mapped
- Where India stands globally
- India vs. global average: the five primitives
- Software's share of India's task mix

**08, The Canary Cohort**
- Infosys's under-30 trend, year by year
- The US reference: Brynjolfsson's ADP findings

**09, What We Can't See**
- The iceberg: visible formal economy vs. invisible informal economy
- The data-infrastructure checklist (US, Denmark, India)
- Humlum & Vestergaard's null result, and why it matters here

**10, The Live Index**
- The three signals, explained
- Try it: reweight the sliders

**11, The Verdict**
- The three-bullet closing case

---

## Story / Evidence toggle: applies to the whole page

**Reference model:** Skimmaxxer's "Interactive Wiki" vs. "Annotated Paper" toggle. We don't have one underlying paper to annotate the way they do; we've stitched together six different sources, so a literal copy of their toggle doesn't map cleanly. The version that fits our situation: **"The Story"** (default, the scrollytelling narrative as already specced above) vs. **"The Evidence"** (same section order, but every section expands in place to show its full underlying detail: data tables, exact figures, exact quotes, methodology notes). This generalizes the pattern already built once for the methodology section (visible four steps + expandable deep-dive) to every section on the page, instead of leaving it as a one-off.

**Toggle placement:** top of page, next to or below the title, persistent as the user scrolls, same position Skimmaxxer uses.

**What "The Evidence" mode unlocks, section by section:**

**04, The Methodology:** the deep-dive content already specced: full NCO/ISCO/O*NET crosswalk table for the top 30-40 occupations, full regression specification (functional form, fixed effects, clustering, the parallel-trends plot), classifier technical design (embedding model, seed-term list, precision/recall validation, handling of Hindi/regional-language postings), the sensitivity check against Eloundou et al.'s exposure scores, scraping architecture and ToS notes, sample-size/power discussion.

**05, The Static Picture:** the full six-country data table with exact percentages (not just the illustrative quadrant placement shown in Story mode): India, Brazil, Colombia, South Africa, US, UK, all four exposure/complementarity buckets per country where available. The paper's own stated limitation, quoted directly: it describes itself as "static and in partial equilibrium, providing a snapshot view of exposure in one year." A note on the 3-digit vs. 4-digit ISCO coding difference and what precision is lost because of it.

**06, The Dynamic Evidence:** Copestake's actual econometric design in plain terms (event-study and shift-share approach, what they're comparing against what), the exact company filing numbers rather than just the toggle, and a note on what counts as an "entry-level" posting in Xpheno's count where that's known.

**07, The Live Pulse:** the complete metric table already specced (every "economic primitive," not just the ones charted in Story mode), plus a short note on how Anthropic's AI Usage Index is calculated (usage adjusted for working-age population) and the brief's underlying sample period (Nov 2025 data, published Feb 2026).

**08, The Canary Cohort:** the full Brynjolfsson stats table (the -19% and -20% figures), the "automate vs. augment" distinction explained in more depth, and the note that the effect is driven by reduced hiring rather than layoffs.

**09, What We Can't See:** the full Humlum & Vestergaard quote already in the brief, plus their study design in more depth (25,000 workers, linked to Denmark's administrative wage/hours records, two-year post-ChatGPT window, the plus-or-minus 2% bound on ruled-out effects), and a more detailed version of the EPFO limitation (monthly, industry-level aggregates only, no individual-level or occupation-level granularity).

**10, The Live Index:** an explanation of how the synthetic demo data was generated and exactly why it's synthetic (no real composite index like this currently exists to point to; this is a demonstration of what the method would produce, not a real published series).

**Sections 01, 02, 03, 11:** no meaningful "Evidence" expansion needed; these are framing/narrative sections, not data sections. Toggle leaves them unchanged in both modes, and the expand affordance is omitted entirely for these four.

---

## Section 1: Hero
**Fix note:** the current headline ("Prices moved first. Jobs move next.") states the hypothesis as a settled fact. That contradicts the hedged, honest tone the page earns later (sections 8 and 10). The hero needs to pose the question, not announce the answer.

**Revised headline (pick one):**
- "Prices moved first. **Is India's job market next?**"
- Or, drop the parallelism entirely: "Can we watch AI change India's job market before the government's job data does?"

**Revised body copy (replace current paragraph):**
"A decade ago, economists stopped waiting for official inflation numbers and started scraping millions of online prices themselves. This page asks the same kind of question about jobs: can fast, unofficial, ground-up data (job ads, hiring disclosures, AI usage numbers) show us what AI is doing to India's labour market before the slow, official surveys do?"

**Visual:** animated counter on load.
**Candidate stats (pick one or rotate):**
- "15x, how much faster Indian Claude users complete complex tasks with AI, vs. 12x globally" (Anthropic India Brief, Feb 2026)
- "23,460: net jobs cut at TCS in FY26, its largest single-year reduction ever"
- "50.7%: share of Infosys's workforce under 30, the lowest in 15 years"

---

## Section 2: What was the Billion Prices Project (+ why it's the inspiration)
**Fix note:** the current chart is a single smooth line trending up from 2008-2024, no axis, no units. It shows nothing; the actual story is a *divergence*, and that divergence is the whole reason this project is interesting.

**Chart fix:** two lines, not one: "Official Argentina CPI" vs. "BPP scraped price index," tracking together, then splitting apart around 2010-2012, scraped index running well above the official one. Label clearly as illustrative/approximate; we don't have BPP's exact published series, just the shape of the known divergence.

**Missing piece, add 2-3 sentences of "why this is our inspiration" after the history paragraph, before the chart:**
"Prices were just the visible tip of something bigger, and even something that basic turned out to be worth double-checking against what a government was willing to admit. Official job numbers move slower than prices ever did (once a quarter or once a year, not daily) and are just as open to dispute. If a government's own numbers can lag or misstate something as measurable as prices, they're even more likely to be behind on something as new as AI."

**Visual:** the two-line divergence chart above the "why this is our inspiration" text, callout on the Argentina catch already present.

---

## Section 3: Our reframed hypothesis
**Fix note:** this section currently jumps straight into the mapping table with no connecting sentence; after reading section 2's history, a reader lands here without being told why prices and jobs should behave the same way. Add one line before the table:

**Add this line before the table:** "The mechanism doesn't change, only what's being counted does."

**Visual:** side-by-side mapping card.
| Original (Cavallo) | Ours |
|---|---|
| Millions of scraped online prices | Job ad text, hiring/headcount disclosures, AI usage data, wage bands |
| → real-time inflation index | → real-time AI labor-impact index |
| Validated against official (sometimes manipulated) CPI | Validated against PLFS/CMIE (slow, contested employment data) |

---

## Section 4: How we'd actually build this (methodology)
**Placement:** immediately after Section 3 (reframing), before the Pizzinelli critique. Visible on the main page in full; this is not a teaser, it needs to stand on its own as a real methodology. A separate, deeper "how we'd build this" panel holds the technical appendix (spec below).

**Fix note on the earlier draft copy:** it read as AI-generated: parallel-structure triplets ("fixing the blind spots, building the live signal, proving it's causal, checking it against reality"), "not X, but Y" constructions ("proving causation, not coincidence"), and the same "the way the Billion Prices Project led CPI" comparison repeated near-identically across sections. Rewritten below in plainer, one-time language.

### Visible on main page: four concrete steps

**Section intro:** "This is normally the part that gets waved away with a slide that says 'we'll build an index.' Here's what we'd actually have to do."

**1. Fix the occupation crosswalk.**
Exposure scores like AIOE were built on US task data. Pizzinelli et al. mapped them onto India using occupation codes, but that assumes a software developer's job looks the same in Bangalore as it does in Seattle, a stretch, since Indian IT work leans much more toward delivery and execution than the design-heavy roles the US data was built on.
*Our fix: keep their crosswalk as a starting point, but spot-check a sample of matched occupations against real Indian job listings, and adjust wherever the task content clearly doesn't line up, IT services roles first.*

**2. Build the job-ad signal.**
Pull postings every month from Naukri, LinkedIn India, and Indeed India. Match each one to an occupation code by title and description. Then flag which ones mention AI skills, starting from obvious terms like "GenAI" or "prompt engineering," but expanded so we also catch postings that describe the same work without using those exact words. Track how that share moves, month by month, occupation by occupation, along with whatever salary ranges are listed.

**3. Make sure it's actually AI.**
We'd run this as a comparison between occupations more exposed to AI and less exposed, before and after GenAI adoption picked up in India, roughly late 2022 into 2023. But this only means anything if exposed and non-exposed occupations were tracking together *before* that point. If they weren't already moving in step, we can't credibly blame AI for what happens after. We'd also split the data by state, IT hubs vs. everywhere else, mainly to make sure we're not just picking up the 2023-24 global IT-spending slowdown and mislabeling it as an AI effect.

**4. Check if it's actually working.**
Compare our monthly numbers against the official ones, PLFS every quarter, CMIE every month, and see if ours moves first. That's really the whole bet here: a faster index built from job ads and hiring data should show cracks before the slow official surveys catch up, the way scraped prices once got ahead of a government's own inflation numbers. The 2025-26 IT hiring slowdown is a real, recent moment we could actually test that against.

### Expandable panel / linked deep-dive page: spec
Content that would drown the main narrative if inlined, but should exist one click away:
- Full NCO ↔ ISCO ↔ O*NET crosswalk table for the top 30-40 occupations by employment share, with flagged mismatches from the audit step.
- Full regression specification: functional form, fixed effects (occupation, month, state), clustering approach, and the exact parallel-trends test/plot.
- Classifier technical design: embedding model choice, seed-term list, validation approach (precision/recall on a hand-labeled sample), and how the classifier handles Hindi/regional-language postings.
- Sensitivity checks: re-running the whole pipeline with Eloundou et al.'s GPT-exposure scores instead of AIOE, to see if conclusions hold under a different exposure measure.
- Scraping architecture notes and ToS/legal considerations for each platform (Naukri, LinkedIn, Indeed).
- Sample-size and statistical power discussion: how many postings/months are needed before the DiD estimates are reliable.

---

## Section 5: The static picture (critique of Pizzinelli et al., IMF WP 23/216)
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

## Section 6: The dynamic evidence
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

## Section 7: Anthropic India Brief (live pulse)
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

## Section 8: The "canary" cohort
**India data:** Infosys under-30 workforce share: two-thirds (until FY18) → 53% (FY25) → 50.7% (FY26, lowest in 15 years). Plot as single annotated trend line.

**US reference inset (clearly labeled as US, not India):** Brynjolfsson, Chandar & Chen, "Canaries in the Coal Mine?" (Stanford, rev. Aug 2026), using ADP payroll data (millions of workers, 730 occupations, monthly). Employment for 22-25-year-olds in AI-exposed occupations ~19% below counterfactual as of mid-2026; effect driven by reduced hiring, not layoffs; concentrated in occupations where AI *automates* rather than *augments*. Software developers age 22-25 specifically down ~20% from Oct-2022 peak to July 2025.

---

## Section 9: What we can't see (honest limitations)
**Visual, iceberg diagram:** visible tip = formal, urban, English-speaking workforce covered by our proxies (job portals, EPFO, listed-company disclosures); submerged mass = India's large informal workforce, largely invisible to all of these sources.

**Checklist, data infrastructure gap:**
| Has population-wide administrative payroll/wage register? | |
|---|---|
| US (ADP) | Yes, monthly, individual-level, 730 occupations |
| Denmark (Statistics Denmark) | Yes, linked to worker surveys |
| India (EPFO) | No, monthly aggregate by industry only, not individual-level |

**Caution callout:** Humlum & Vestergaard, "Still Waters, Rapid Currents" (Denmark, NBER/Rockwool 2025-26), using 25,000 workers linked to full administrative wage/hours records, found *precise null effects on earnings and hours* two years post-ChatGPT (ruling out effects >2%), despite widespread adoption. What moved instead: task composition and occupational mobility. **Lesson for our page: don't overclaim a clean wage effect. Even in a far more data-rich country, it hasn't been proven yet.**

---

## Section 10: Our proposed live index (interactive payoff)
**Visual:** mock dashboard, one composite line ("Illustrative AI Labor Impact Index for India") built from three sub-signals.
**Interaction:** three sliders (Wage signal / Hiring signal / Usage signal weight) that reshape the composite line live when adjusted. Purely illustrative/synthetic data; label clearly as a demo of the *method*, not a real published index.

---

## Section 11: Verdict
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
