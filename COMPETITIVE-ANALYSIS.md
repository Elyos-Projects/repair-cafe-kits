# Competitive + Improvement Analysis — repair-cafe-kits

> Analyst: research agent · Date: 2026-06-29 · Plan reviewed: PLAN.md v0.1.0 + TASKS.md v0.1.0
> Scope: open kits/guides to help communities run repair events + safely triage/fix common items
> (right-to-repair, waste reduction). Guardrails: SAFETY (electrical/appliance shock + fire risk),
> accuracy, open license, attribution, environmental benefit.

---

## 1. Correctness & completeness review of PLAN.md

The plan is unusually disciplined for a v0.1.0 draft. It is internally consistent, schema-aligned,
and the riskiest failure mode (teaching mains repair) is structurally walled off. The findings below
are refinements and a few genuine gaps, ordered by importance.

**1a. Electrical/appliance safety — strong, but the boundary is drawn slightly too narrowly.**
The plan correctly re-tiers all electrical content to `high`, scope-limits it to
"triage-and-referral-only (no mains-repair steps)", mandates credentialed-electrician/CEng sign-off
distinct from the author, enforces a "not a substitute" disclaimer, and proves the gate with a
negative test (M2 / ci-013). This is the right architecture. Gaps:
  - **The hazard list is electrical-centric and misses other lethal energy classes.** Real community
    repair brings in items with hazards beyond mains AC: **stored-energy capacitors** in microwaves,
    CRT TVs, and camera flashes (microwave-oven and CRT capacitors can hold a **lethal charge even
    when unplugged** — the single most common "killed while unplugged" scenario); **lithium-ion
    batteries** (puncture → thermal runaway / fire — extremely common in the small-electricals that
    dominate repair-event intake and ORA data); **gas appliances** (the prompt flags this — gas is
    statutorily regulated in most jurisdictions, e.g. UK Gas Safe); **pressure vessels**; **asbestos**
    in pre-1990s appliances/textiles; **refrigerant** in fridges/AC. The plan names "mains-electrical,
    gas, pressure-vessel" once in Out-of-scope, but the *triage checklists and refusal criteria* are
    framed almost entirely around mains AC. Recommendation: generalize the high-risk gate to a
    **"hazardous-energy / regulated-trade" class** (mains AC, stored capacitive charge, Li-ion,
    gas, pressure, refrigerant, asbestos) each with an explicit "do not open / refuse / refer"
    rule. Capacitor and Li-ion hazards in particular must appear in the *first* electrical unit,
    not a backlog item.
  - **"Visual inspection" and "PAT framing" still imply hands-on contact.** Even triage (plugging in
    to observe, opening a casing to inspect) is a contact activity. The real-world standard (UK CRN /
    Restart / Repair Café Wales) is that mains items are powered through an **RCD or isolating
    transformer** and inspected/tested by a **PAT-competent person**. The plan should state the
    "safe-to-energize" preconditions (RCD/isolation, competent tester) as part of triage, or the
    "triage-only" boundary is ambiguous about whether energizing is permitted.
  - **"Know your limits" is implied but not a named, repeated artifact.** The guardrail wants an
    explicit, prominent "know your limits / when to stop" rule. The plan has a "when to stop" column
    and a safety one-pager; elevate "know your limits" to a **standalone, translated, top-of-every-
    checklist banner**, not a column.

**1b. Liability / waiver model is under-specified — currently "pointers only", which may be too thin.**
The plan deliberately keeps insurance/waiver **off-platform** ("seek local guidance") to avoid giving
legal advice and to avoid ingesting PII. That is defensible and privacy-correct, but real organizers
*need* a usable waiver/disclaimer and a risk-assessment template to run an event at all — every
mature competitor (CRN, Repair Café Wales, CAG) ships exactly these. Recommendation: ship a
**non-personalized, clearly-labelled *template* disclaimer + risk-assessment checklist + "what
insurance to ask about" explainer** ("informational, not legal advice; have it reviewed locally"),
rather than only a pointer. A template is materially more useful and is not legal advice if framed
as a starting point. Note the privacy tension: the **participant intake ticket** is correctly PII-free,
but a **liability waiver inherently needs the item-owner's name/signature** — so the plan must
distinguish "platform templates collect no PII" (true, kept off-platform) from "the organizer's
own paper waiver, which we template but never ingest." Make that distinction explicit so M1 reviewers
don't read the no-PII rule as forbidding a waiver template.

**1c. Accuracy of repair guides — the review model is good; add a "no fabricated steps" rule and a
freshness trigger tied to standards.** The no-self-approval + cited-source + expert-gate model is
sound. Two additions: (i) an explicit **"every repair step / refusal criterion must trace to a cited
source; no model-generated steps without a human-verified source"** rule (see §5); (ii) the
`lastReviewed` cadence should be **event-triggered**, not just annual — e.g. a change to UK PAT
guidance, a CPSC recall, or an EU Ecodesign update should force re-review of affected units.

**1d. Tool/skill prerequisites — present but shallow.** Checklists include a "tools needed" field,
which is good. Missing: a **per-category skill-prerequisite / competency statement** ("this is safe
for a confident beginner" vs. "needs a competent fixer") and a **PPE note** (eye protection for
grinding/soldering, gloves for sharps/glass, ventilation for solder/adhesives). Restart's wiki and
CRN both treat toolkit + competency as first-class; the plan should too. Consider cross-linking to a
sibling **tool-atlas** project (see §7).

**1e. Scope vs iFixit is correct and honest, but the plan slightly *under*-claims the crowding of the
*organizer-kit* niche.** The plan frames iFixit as the dominant *repair-guide* incumbent (true) and
positions itself in the *organizer-kit* gap. But the organizer-kit niche is **already occupied** by
several free resources: **iFixit's own "Community Repair Getting Started" wiki**, **The Restart
Project / Restarters wiki** (toolkit, electrical safety, multimeter, water-damage guides), **UK
Community Repair Network** (getting-started, risk & insurance, impact, fundraising), **Culture of
Repair**, and **Fixit Clinic**. The differentiator therefore can't just be "an organizer kit
exists" — it must be **license-clean remixability + safety-forward structure + offline/print +
i18n + provenance** (see §4). The plan's analysis should name these incumbents explicitly so it
isn't surprised by them.

**1f. Environmental-impact framing is honest (good) but the weight-factor source is unresolved.**
Presenting waste-diverted as an *estimate* with a published per-category weight method, separate from
counts, is exactly right and avoids over-claiming. The open question "which cited source for
per-category weights" is real — the **Open Repair Alliance / ORDS dataset and the UN Global E-waste
Monitor 2024** (62 Mt e-waste in 2022, only 22.3% formally recycled) are the natural citations, plus
a reuse-vs-recycle carbon factor. Resolve this before any tonnage is published.

**1g. Accessibility is a genuine strength.** WCAG 2.2 AA, named AT support matrix
(NVDA/JAWS/VoiceOver/TalkBack + keyboard), print-legibility as a first-class gate, low-literacy /
plain-language, RTL, bundled offline fonts — this is more rigorous than any competitor's organizer
material, most of which are PDFs/Google Docs with no a11y commitment. Keep it; it is a differentiator.
One addition: **numeracy/iconography for low-literacy and multilingual users** (safety pictograms,
ISO-style hazard symbols) — but verify symbol licenses.

**1h. Minor correctness nits.**
  - PLAN says iFixit is **CC-BY-NC-SA**; iFixit's own licensing page states **CC BY-NC-SA 3.0**
    (the plan's prose elsewhere implies 4.0). Either is "link/cite only, do not remix" so the
    conclusion holds, but cite the correct version. **Also: iFixit's Terms prohibit using their data
    to train/operate ML/AI models** — directly relevant to §5 (we must not scrape iFixit into any
    Claude prompt/pipeline).
  - PLAN lists **Open Repair Alliance / ORDS in the "open / openly-licensed" bucket** for reuse. ORDS
    data is **CC-BY-SA 4.0 (share-alike)**, not plain CC-BY. *Facts and statistics* extracted for
    analysis are fine (facts aren't copyrightable), but a **redistributed/remixed ORDS-derived
    dataset would inherit SA**, conflicting with the project's CC-BY-4.0 commons. Treat ORDS like
    Wikipedia (CC-BY-SA): analyze and cite freely; if you republish a derived dataset, license that
    artifact SA, separate from the CC-BY content.

---

## 2. Competitive landscape (researched, cited)

**iFixit** — the dominant global repair-guide platform; tens of thousands of step-by-step guides,
teardowns, repairability scores, parts/tools sales, and a "Self-Repair Manifesto." Also runs a
**"Community Repair Getting Started" wiki** and acquired/hosts the **Restarters** software suite.
*Strengths:* unmatched guide depth, brand, repairability scoring, active right-to-repair advocacy.
*Weaknesses for our purpose:* content is **CC BY-NC-SA (3.0)** — **non-commercial + share-alike**, so
it **cannot be remixed into a CC-BY commons**; **Terms forbid AI/ML training on their data**;
guide-centric, not a turnkey *event-organizer + offline/print + i18n* kit. (https://www.ifixit.com/Info/Licensing,
https://www.ifixit.com/Wiki/Community_Repair_Getting_Started, https://www.ifixit.com/Manifesto)

**Repair Café International Foundation** (Amsterdam) — the movement's brand; **~3,650–3,800+
registered Repair Cafés in 50+ countries** (RCIF site, 2025). Provides a paid/members starter package
and network support. *Strengths:* brand recognition, scale, network effects, real-world event model.
*Weaknesses:* **"Repair Café" is a registered trademark** (plan correctly avoids it); starter
materials are **not an open commons**; localization and offline/print accessibility are not the
emphasis. (https://www.repaircafe.org/en/about/, https://www.repaircafe.org/en/already-750-repair-cafes-around-the-world/)

**The Restart Project / Restarters wiki + Fixometer** (UK, global community) — open community of
repair activists; the **Restarters wiki** covers **repair safety, electrical safety, multimeter use,
water-damage rescue, toolkit building**; the **Fixometer** logs fixes and feeds the Open Repair
Alliance. Code is **open-source on GitHub**. *Strengths:* genuinely open ethos, strong safety
content, real data pipeline, the closest philosophical sibling. *Weaknesses:* wiki UX/structure is
uneven, not packaged as a printable/offline/i18n kit, no formal a11y/provenance gating, content
licensing per-page varies. (https://wiki.restarters.net/Main_Page, https://therestartproject.org/fixometer-2/,
https://github.com/TheRestartProject/restarters.net)

**Fixit Clinic** (US) — "explore-and-discover STEM" community repair events; getting-started guidance
(people/space/tools/partners). *Strengths:* strong pedagogy, US footprint, public-library/county
partnerships (e.g. Hennepin County). *Weaknesses:* lighter on packaged, license-clean, translatable
organizer artifacts; blog-style distribution. (https://fixitclinic.blogspot.com/p/scheduled-events.html,
https://sustainableconsumption.usdn.org/initiatives-list/community-repair-events)

**UK Community Repair Network (CRN)** — **the most direct overlap with our organizer-kit niche.**
Provides getting-started, **risk & insurance**, measuring-impact, fundraising, and education guidance,
plus PAT/insurance/CE-marking specifics. *Strengths:* practical, UK-legally-grounded, exactly the
event-ops content we plan. *Weaknesses:* **no explicit open license**, UK-specific, not
offline/print/i18n/a11y-engineered, links out to partner Google Docs. (https://communityrepairnetwork.org.uk/how-to-run-a-repairgroup/risk-and-insurance/)
Related: **Repair Café Wales volunteer H&S guidelines**, **CAG how-to guide**, **Culture of Repair**
(US "how to start one").

**Right-to-Repair advocacy orgs** — **The Repair Association (repair.org)** and **US PIRG** in the
US; **Right to Repair Europe** in the EU. *Context (research):* **right-to-repair bills have now been
introduced in all 50 US states**; five states (NY, CA, MN, OR, CO) plus WA have **passed** electronics
laws; the **EU Right to Repair Directive + Ecodesign** and **repairability/energy labels for
smartphones/tablets (from June 2025)** are live. *Strengths:* authoritative policy framing to cite in
the primer. *Weaknesses:* advocacy, not how-to-fix content. (https://www.repair.org/legislation,
https://pirg.org/edfund/resources/the-state-of-right-to-repair/, https://www.ifixit.com/News/108371/right-to-repair-laws-have-now-been-introduced-in-all-50-us-states)

**Open Repair Alliance / ORDS** — shared data standard; **combined datasets published every ~6 months**,
**licensed CC-BY-SA 4.0**; members include Restart, Repair Café Foundation, Fixit Clinic, iFixit,
Anstiftung. *Strengths:* the authoritative open dataset of what breaks and what's fixable — a
goldmine for evidence-based triage prioritization and waste estimation. *Weaknesses:* **share-alike**
(see §1h); raw data, not guidance. (https://openrepair.org/open-data/open-standard/,
https://standard.openrepair.org/, https://openrepair.org/open-data/downloads/)

**Manufacturer manuals / safety bodies** — OEM service manuals (copyrighted), **UK Electrical Safety
First / OPSS**, **NFPA** (copyrighted; paraphrase+cite), **US CPSC** (public domain — directly
reusable). The plan handles these licensing tiers correctly.

---

## 3. Gaps we can fill

1. **A license-clean (CC-BY) organizer + triage commons.** Every strong incumbent is either
   NC-SA (iFixit, much wiki content), trademark-gated (Repair Café), CC-BY-SA (ORDS, Wikimedia,
   Restart pages), or un-licensed (CRN, CAG). **There is no truly CC-BY, freely-remixable, attribution-
   only organizer + safety commons.** That permissive license *is* the white space — it lets councils,
   libraries, and other projects (incl. Elyos siblings) fold the material into their own works without
   NC/SA friction.
2. **Safety-forward structure with a hard expert gate + provenance log.** No competitor enforces
   credentialed sign-off, a "triage-only" scope guarantee, and a tamper-evident review log in CI.
3. **Offline / print-first, low-connectivity-ready.** Field use is in church halls, libraries, sheds
   with poor wifi. Competitors are websites/Google Docs/PDFs; none ships a versioned, dated,
   print-legibility-audited offline bundle.
4. **Genuine i18n + safety-accuracy-reviewed translations.** Most material is English-only;
   safety-accurate localization is essentially absent.
5. **WCAG 2.2 AA + low-literacy + plain-language.** Accessibility is an afterthought across the field.
6. **Zero-PII-by-design event tooling.** A privacy-clean intake template (item+fault+outcome only) is
   a real, defensible differentiator versus tools that quietly collect attendee data.
7. **A unified, cross-jurisdiction right-to-repair primer** that's product-neutral and current with
   the 2025–26 EU + 50-state landscape — most how-to-fix sites don't cover rights, and rights orgs
   don't cover how-to-run-an-event.
8. **Evidence-based triage prioritization from ORDS** — use the open repair dataset to choose *which*
   categories/faults to write checklists for first (highest-volume, highest-fixability).

---

## 4. Differentiators to win (vs iFixit's guide dominance)

We **do not** out-compete iFixit on guide depth — and we **must not** copy or train on their NC-SA
content. We win on the axes iFixit and the others structurally cannot/do not occupy:

1. **License: CC-BY-4.0 attribution-only commons.** The single strongest differentiator. iFixit
   (NC-SA), Restart/Wikimedia/ORDS (SA), and Repair Café (™) cannot offer frictionless remix into
   other works; we can. This is the moat.
2. **Safety as an engineered guarantee, not prose.** Credentialed-expert gate + "triage-only" scope
   field + governance gate that *blocks publish* + negative test + tamper-evident log. "Provably can't
   ship mains-repair instructions" is a claim no competitor makes.
3. **Offline/print-first + versioned/dated bundles** for low-connectivity venues.
4. **Localized + safety-accuracy-reviewed** in ≥3 languages with RTL/offline fonts.
5. **WCAG 2.2 AA + low-literacy/plain-language + hazard pictograms.**
6. **Zero-telemetry, zero-attendee-PII by construction** (CSP `connect-src 'none'`, runtime
   network-interception E2E) — a privacy posture organizers can trust and councils can endorse.
7. **Evidence-driven content roadmap** powered by ORDS/e-waste data (cite, don't relicense).
8. **Composability** as the "glue" layer: we *link* to iFixit's deep guides (allowed) while owning the
   *organizer kit + triage + safety + rights + offline/i18n/a11y* wrapper around them — complement,
   not clone.

---

## 5. Claude API leverage — and the hard "Claude must NOT decide" lines

**Where Claude adds real leverage (all human-/expert-gated before publish):**
1. **Drafting organizer artifacts from sourced inputs** — playbook sections, station-layout
   checklists, volunteer-onboarding scripts, risk-assessment and *template* waiver/disclaimer drafts,
   post-event wrap-up templates — synthesized from CRN/Restart/CPSC-style *public* sources, then
   human-reviewed. Big time-saver on boilerplate.
2. **Structuring/normalizing repair-triage content into the RepairUnit schema** — taking a
   human-written or public-domain source and emitting well-formed JSON/MDX with citation fields,
   `riskClass` suggestions, "worth-fixing / common-faults / tools / safe-handling / when-to-stop"
   sections, and consistent plain-language reading level. Claude is excellent at this shaping.
3. **ORDS / e-waste data analysis** — rank categories/faults by volume × fixability to prioritize the
   first 7 checklists; compute and *document* per-category weight factors for the waste estimate;
   summarize trends for the primer. (Use ORDS facts/stats; respect SA on any republished derivative.)
4. **Right-to-repair primer drafting + currency** — summarize the 2025–26 EU Directive/Ecodesign and
   50-state landscape into neutral, product-agnostic prose with citations; flag staleness.
5. **i18n/localization first drafts + a "safety-term consistency" check** — draft translations and
   flag where a safety instruction may have drifted, for the human safety-accuracy reviewer.
6. **Governance tooling** — a build-time linter that uses Claude to flag *candidate* license/provenance
   problems, unsourced claims, or mains-repair-instruction language in a PR (advisory, not gating).
7. **Accessibility/plain-language passes** — rewrite to low-literacy reading level, draft alt text and
   pictogram captions (human-verified).

**Where Claude must NOT be the decider (hard lines):**
- **Electrical/gas/hazardous-energy safety boundaries are expert-reviewed, not model-decided.** Claude
  may *draft* triage language, but a **credentialed electrician/CEng/gas-safe person** sets and signs
  off every refusal threshold, "safe-to-energize" precondition, and "get a professional" boundary.
  The `expertSignOff` record gates publish; no model output substitutes for it.
- **No fabricated repair steps or refusal criteria.** Every step/threshold must trace to a
  human-verified cited source. A "no model-invented procedure" rule + provenance check must block any
  unsourced safety instruction. Hallucinated repair steps in this domain can kill.
- **"Get a professional" thresholds must be explicit and conservative**, authored to fail safe; Claude
  must never relax or infer them.
- **Liability/waiver/insurance text is "informational, not legal advice" and human/legally reviewed** —
  Claude drafts templates only; it does not give jurisdiction-specific legal/insurance advice.
- **License & trademark calls are human-verified.** Claude may *flag* a suspected NC/SA/copyright/™
  problem, but a human confirms `reusePermitted` per source. **Never feed iFixit content into Claude**
  (their Terms forbid AI training/use on their data) and never relicense SA/NC material.
- **Don't publish model-estimated tonnage as fact** — waste figures stay labelled estimates with a
  cited method.

---

## 6. Ten concrete optimizations

1. **Generalize the `high`-risk class from "electrical" to "hazardous-energy / regulated-trade"** —
   add stored-capacitor charge, Li-ion thermal runaway, gas, pressure, refrigerant, asbestos; each
   with an explicit do-not-open/refuse/refer rule. Put **capacitor + Li-ion hazards in the first
   safety unit**, not the backlog. *(Closes the biggest safety gap; §1a.)*
2. **Define "safe-to-energize" preconditions** (RCD/isolating transformer + PAT-competent person)
   inside the triage flow so "triage-only" is unambiguous about powering devices on. *(§1a.)*
3. **Ship a labelled *template* waiver + risk-assessment checklist + "insurance to ask about"
   explainer** ("informational, not legal advice; review locally"), and explicitly reconcile it with
   the no-PII rule (platform ingests none; organizer's paper waiver is theirs). *(§1b.)*
4. **Add a "no fabricated steps / every step traces to a cited source" rule** to the content schema +
   governance gate, with an advisory Claude linter that flags unsourced procedures. *(§1c, §5.)*
5. **Add per-category skill-prerequisite + PPE fields** to the checklist schema. *(§1d.)*
6. **Name the organizer-kit incumbents (iFixit Community Repair, Restart wiki, CRN, Fixit Clinic,
   Culture of Repair) in the plan** and reposition the differentiator as license+safety+offline+i18n+
   provenance, not "a kit exists." *(§1e, §4.)*
7. **Use ORDS + UN e-waste data to drive the first-7 category selection and the waste-weight method**;
   record the chosen weight source now (resolves open question 5). Respect CC-BY-SA on any republished
   derivative dataset. *(§1f, §1h, §3.8.)*
8. **Fix the licensing citations:** iFixit = CC BY-NC-SA **3.0** + AI-training-prohibited; ORDS =
   CC-BY-**SA** 4.0 (move out of the plain-"open" reuse bucket, treat like Wikimedia). *(§1h.)*
9. **Make `lastReviewed` re-review event-triggered** (CPSC recall, PAT/standards change, Ecodesign
   update) in addition to the annual cadence. *(§1c.)*
10. **Add hazard pictograms + a standalone "Know Your Limits / When to Stop" banner** at the top of
    every checklist (translated, high-contrast, license-verified symbols) for low-literacy/multilingual
    field use. *(§1a, §1g.)*

---

## 7. Parallel & perpendicular spin-offs

- **tool-atlas (parallel):** an open, CC-BY catalog of repair tools (what each does, safe use, PPE,
  budget vs. pro tiers) that the per-category "tools needed" + skill-prerequisite fields link into.
  Removes a recurring gap (organizers reinventing toolkit lists) and is reusable across both projects.
- **oer-science-labs (perpendicular):** repair is applied physics/electronics pedagogy (Fixit Clinic's
  "STEM through fixing" model). Co-produce open educational modules — multimeter basics, simple
  circuits, materials/adhesives — that double as fixer up-skilling and school OER.
- **home-energy-savings (parallel):** strong thematic adjacency — keeping appliances working longer,
  spotting energy-wasteful/failing units, "repair vs. replace for efficiency" guidance, shared
  waste/energy/carbon factors and the same offline/print/a11y delivery layer.
- **microbusiness-toolkit (perpendicular):** a "pathway to a paid local repair service / repair
  micro-enterprise" track for fixers who want to go pro — sits *outside* the CC-BY non-commercial
  commons but references it, and ties to the right-to-repair economic argument.
- **Open Repair Alliance data tie-in (parallel):** contribute an **ORDS-conformant, CC-BY-SA export**
  of any anonymized, aggregate outcome counts organizers self-report (events, item categories,
  fixed/not-fixed) — feeding the alliance's twice-yearly dataset while keeping our CC-BY *content*
  separate from the SA *data* artifact. Strengthens both the evidence base and the partnership story.
- **MCP server (perpendicular):** a **"community-repair-kit" MCP server** exposing the CC-BY content
  as read-only tools — `search_triage_checklists`, `get_safety_refusal_criteria`,
  `get_organizer_template`, `query_ords_stats` — so any agent/assistant can surface license-clean,
  provenance-tagged, *expert-gated* repair-triage and event-ops content (with the "refer to a
  professional" boundaries baked in) without scraping NC/™ sources. A natural Elyos showcase.

---

## 8. Open questions

1. **Hazard scope:** will governance adopt the broadened "hazardous-energy / regulated-trade" class
   (capacitors, Li-ion, gas, pressure, refrigerant, asbestos), or stay electrical-only? *(Drives §6.1.)*
2. **Energizing in triage:** is powering a device on (via RCD/isolation) in-scope for "triage," or is
   triage strictly de-energized visual inspection? Affects required competencies and liability.
3. **Waiver/risk-assessment templates:** ship labelled templates, or hold to pointers-only? If
   templates, who provides the one-time legal review, and for which jurisdiction(s)?
4. **First jurisdiction(s) + standards** (UK Part P/NICEIC/Gas Safe vs. US NEC/state vs. EU) — gates
   the electrical SME recruit and the primer framing. *(Partner-driven; PLAN open Q2–3.)*
5. **Waste-estimation weight source** — confirm ORDS + UN e-waste + a reuse-vs-recycle carbon factor.
6. **ORDS reciprocity:** do we contribute an ORDS-conformant outcomes export, and how do we keep the
   SA data artifact cleanly separated from the CC-BY content commons?
7. **iFixit relationship:** pursue an explicit "link-only, no-remix, no-training" understanding so the
   complement-not-clone positioning is unambiguous and respectful of their Terms?
8. **Pictogram/symbol licensing:** which hazard-symbol set is license-clean for CC-BY redistribution?
9. **Named partner + electrical SME** — still TO BE SECURED; both gate the Definition of Shipped /
   M2 respectively. *(PLAN open Q1–2.)*
