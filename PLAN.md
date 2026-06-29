# PLAN — repair-cafe-kits (open community-repair event guides + fixable-item checklists)

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

## Executive summary

**repair-cafe-kits** is an openly-licensed body of practical, remixable content — plus a light,
printable delivery layer — that lets **anyone, anywhere run a community repair event** and safely
**triage and fix common household items**. It advances the **right-to-repair**: keeping usable
things out of landfill, saving households money, building local repair skills, and pushing back
against disposability. The deliverables are an **organizer playbook** (how to plan, staff, and run
an event), **fixable-item triage checklists** (what is worth fixing and how to assess it), and a
neutral **right-to-repair primer** (how to find manuals, spare parts, and exercise repair rights).
Everything is free, attribution-only, and designed to be **printed and used offline** in a church
hall, library, or makerspace with poor connectivity.

The project has two coupled lanes of work: (1) **content** — sourced, review-gated guides and
checklists, each traceable to authoritative or openly-licensed references; and (2) a small
**delivery layer** — a static, printable, accessible site/bundle (TypeScript/ESM) so organizers can
read, search, and print the kit, with **zero telemetry and no attendee data collection**.

**This is a `medium` risk-tier project with a hard-gated `high`-risk content class.** Most content
(event logistics, textiles, furniture, bikes, ceramics, general triage) is low-to-medium risk. But
**anything touching electrical safety can get someone killed**, so all electrical content is treated
as **`high` risk**: it is **scope-limited to triage and "refer to a qualified person" only — never
mains-repair instruction** — and it **must not ship without sign-off from a credentialed
electrician or chartered electrical engineer**, carrying the mandatory framing *"informational only,
not a substitute for professional electrical training, inspection, or repair."* The right-to-repair
primer is **informational, not legal advice**.

**Honesty notes (load-bearing).**
- **No partner / verified need yet.** There is no signed partner, requestor, or MOU. Partner and
  `verifiedNeed` are **TO BE SECURED**; until then the project ships as a generic public good and
  every Task carries `verifiedNeed: false`, `requestor: "TBD"`.
- **"Repair Café" is a registered trademark** of Stichting Repair Café International. This project is
  **not affiliated** with it and **must not use that name or logo** in its outputs; we use the
  generic term **"community repair event."** The repo slug `repair-cafe-kits` is an internal
  identifier only and is **not** used as a public product name or brand.

## Problem & beneficiaries

**The problem.** Repairable goods are thrown away at scale — small electricals, textiles, furniture,
bikes, toys — because repair feels inaccessible: people lack the skill, the confidence, the manual,
the part, or a safe space to try. Community repair events fix this, but **starting one is hard**:
organizers reinvent the playbook (roles, layout, intake flow, safety rules, insurance pointers),
volunteer fixers lack a shared "is this worth fixing / is this safe to touch" triage reference, and
high-quality repair guidance is often **paywalled, copyrighted, vendor-locked, or English-only**.
Existing strong resources (e.g. iFixit) are frequently **non-commercial / share-alike licensed**, so
they can be linked and cited but **not** freely re-mixed into a commons. The result: avoidable
e-waste, lost household savings, and lost community skill-building.

**Who is helped (beneficiaries).**
- **Community organizers and host venues** — libraries, makerspaces, men's/community sheds,
  mutual-aid groups, schools, faith and community centres — who want a ready-to-run, brandable,
  translatable kit instead of building their own from scratch.
- **Volunteer fixers** — who need a consistent triage reference and clear, conservative safety rules
  (especially "when to stop and refuse a job").
- **The public who bring broken items** — saving money, learning skills, and keeping usable goods in
  use. The **environment** is an indirect beneficiary (waste diverted from landfill/incineration).
- **The right-to-repair movement** — gains a free, sourced, neutral on-ramp for new communities.

**Verified need / partner org: TO BE SECURED.** Community-repair need is well-documented by public
bodies and NGOs (e-waste volumes, the EU/UK/US right-to-repair policy wave, the Open Repair
Alliance's published repair data), so foundational work (M0–M1) proceeds on a **plausible but
unverified** basis. However, **no named partner has confirmed this specific need in writing.** A
named partner (e.g. a public-library system, a repair network, a local council/waste authority, or a
men's-sheds federation) confirming need, priority item categories, and target languages is required
before the project meets its *Definition of Shipped*. Until then all Tasks set `verifiedNeed: false`.

## Goals and non-goals

**Goals.**
- Ship an **organizer playbook** that lets a first-time organizer plan, staff, and run a safe
  community repair event end-to-end, using only free, openly-licensed material.
- Ship **fixable-item triage checklists** for common non-electrical categories (textiles, furniture/
  wood, bikes, ceramics/gluing, jewelry, toys, general mechanical), each sourced and reviewed.
- Ship, **behind a credentialed-expert gate**, conservative **electrical safety triage notes** —
  limited to assessment and referral, never mains repair.
- Ship a neutral, sourced **right-to-repair primer** (find manuals/parts; understand repair rights),
  clearly framed as **informational, not legal advice**.
- Be genuinely **free, private, and printable**: CC-BY-4.0 content / MIT code, no ads, no telemetry,
  no accounts, **no attendee PII**, and **fully usable on paper / offline**.
- Be **localizable** (i18n) and **accessible** (WCAG 2.2 AA for the web layer; plain-language,
  low-literacy-friendly, high-contrast print).
- Be **adoptable** by a named partner in their community's languages.

**Non-goals.**
- **Not mains-electrical repair instruction.** We do not teach people to open, rewire, or repair
  mains-powered appliances; we teach safe triage and referral to a qualified person. (Hard guardrail.)
- **Not legal, insurance, or medical advice.** The primer and event-liability material point to
  authoritative/local sources; they do not advise.
- **Not a product/brand recommender.** Vendor-, tool-, and brand-neutral; no affiliate links, no
  lead-gen, no upsell.
- **Not affiliated with, and not using the name or logo of, "Repair Café"** or any other trademark.
- **Not a database of people or events.** No attendee records, no sign-in tracking, no analytics.
- **Not a re-host of copyrighted repair manuals** or of non-commercial/share-alike guides; we link
  and cite those, we do not relicense them.

## Success metrics (outcomes)

Outcome-centric and beneficiary-first. Baselines are zero at project start unless noted. Because we
collect **no telemetry and no attendee PII**, reach/impact is measured by **organizer self-report**
via a standard template — an honest privacy/measurement trade-off, not in-app tracking.

| Outcome | Baseline | Target (first 12 months post-launch) | How measured (privacy-preserving) |
| --- | --- | --- | --- |
| Partner orgs endorsing/adopting the kit | 0 | ≥ 1 named org adopts; goal 3 | Signed letter of support / lightweight MOU (manual record) |
| Item categories with reviewed triage checklists | 0 | ≥ 7 non-electrical categories, each sourced + signed off | Review log in repo |
| Electrical safety notes shipped (expert-gated) | 0 | ≥ 1 set, **credentialed-electrician signed off** + "not a substitute" framing | Expert sign-off log in repo |
| Community repair events run using the kit | 0 | ≥ 25 events reported across ≥ 5 communities | Organizer self-report (standard template) |
| Items assessed / repaired at reported events | 0 | ≥ 1,000 items assessed; ≥ 50% repaired or repair-attempted | Organizer self-report (counts only, **no item-owner PII**) |
| Estimated waste diverted from disposal | 0 | ≥ 1,000 kg estimated (flagged as an **estimate**, methodology published) | Organizer self-report × published per-category weight factors |
| Languages fully localized (UI + core kit) | 1 (en) | ≥ 3 languages | Translation-completeness check in CI |
| Accessibility conformance (web layer) | none | WCAG 2.2 AA verified; 0 critical axe issues; manual AT pass | Automated (axe/pa11y) + manual screen-reader audit |
| Printable/offline usability | none | 100% of core kit usable from print/offline bundle (no network) | Print-render check + offline E2E in CI |
| Privacy posture | n/a | 0 telemetry endpoints, 0 trackers, 0 PII fields | Static audit + runtime network-interception E2E (CSP `connect-src 'none'`) |

We deliberately avoid vanity metrics (downloads, stars). **Waste-diverted is explicitly an
estimate**: organizers report item counts by category, and we multiply by **published, conservative,
cited per-category average weights**; the figure is always presented as an estimate with its method,
never as a measured tonnage. **No item-owner or volunteer personal data is collected** in any metric.

## Scope

**In scope.**
- **Organizer playbook:** planning timeline, venue checklist, roles (host/greeter/triage/fixer/
  safety lead), station layout, intake & triage flow (**PII-free** item ticket), volunteer
  onboarding, a **safety-rules one-pager**, post-event wrap-up, and **pointers** (not advice) to
  local insurance/liability and waste-stream resources.
- **Fixable-item triage checklists** (non-electrical, low–medium risk): textiles/sewing, furniture/
  wood, bikes, ceramics & gluing, jewelry & watches, toys, and a general mechanical checklist —
  each: "is it worth fixing?", common faults, tools needed, safe-handling notes, when to stop.
- **Electrical safety notes (high risk, expert-gated, triage-only):** visual inspection red flags,
  damaged-cable/plug refusal criteria, double-insulation vs. earthed basics (conceptual), PAT-test
  *framing* (what it is / that it needs a competent person), and a hard **"refer to a qualified
  electrician"** decision rule. **No mains repair steps.**
- **Right-to-repair primer (medium risk, not legal advice):** how to find manuals, spare parts, and
  serial/model info legitimately; what repair-rights frameworks exist at a high level; product-neutral.
- **Delivery layer:** static, printable, accessible web bundle + print-optimized PDFs; offline-capable;
  i18n; zero telemetry/PII.
- **Provenance & review infrastructure:** content schema, citation/license fields, a risk-tier router,
  an append-only review/sign-off log.

**Out of scope (explicit).**
- Mains-electrical, gas, pressure-vessel, or any **statutorily regulated** repair instruction.
- Legal/insurance/medical/financial **advice** (we link to authoritative/local sources only).
- Any **PII collection**, attendee database, event registry, or analytics.
- Re-hosting copyrighted manuals or relicensing non-commercial/share-alike content (link + cite only).
- Use of the "Repair Café" name/logo or any third-party trademark/branding.
- Vendor/brand recommendations, affiliate links, or commercial lead-gen.
- Content for categories/languages we cannot source-verify and review.

## Solution approach & architecture

**Overview.** Content-first. The primary artifacts are **structured, versioned content units**
(guides + checklists) with rigorous citation/license/review metadata. A thin **static delivery
layer** renders them for screen and **print**, works offline, and ships no telemetry. There is **no
backend and no user data**; the only network need is the initial load/update of the static bundle.

**Components.**
- **Content store:** versioned structured units (see data model) as static JSON/MDX, bundled for
  offline/print. Each unit declares its risk class, sources, license, and review/sign-off state.
- **Risk-tier router (content governance):** a build-time check that classifies each unit
  (`low | medium | high`) and **refuses to publish** a `high` (electrical) unit unless it carries a
  valid credentialed-expert sign-off record **and** the mandatory "not a substitute" disclaimer, and
  refuses **any** unit lacking required citations or with a forbidden license source.
- **Delivery layer (web/print):** TypeScript/ESM static site (lightweight, a11y-first framework —
  decided by ADR in M0), client-side search, **print-optimized CSS / client-side PDF** for every
  checklist and the full kit, optional service-worker offline cache (no remote runtime fetch).
- **i18n layer:** message catalogs + content keyed by `(unitId, lang)`; build-time completeness
  check; safe fallback to English; **bundled offline fonts** (no runtime web-font fetch); RTL-ready.
- **Provenance & review log:** append-only, PR-tied records (sources checked, reviewer/approver,
  expert credential for high-risk units, license verification) — the auditable basis for "shipped."
- **Build/CI:** pnpm workspace; lint, typecheck, unit, **content-governance gate** (risk router +
  citation/license validation + no-self-approval + high-risk-needs-expert), a11y, print/offline E2E,
  no-telemetry/PII audit.

**Tech stack.** TypeScript, ESM, pnpm workspaces; static site + print CSS / client PDF; optional
PWA service worker; static hosting (GitHub Pages / Netlify / Cloudflare Pages — no app server).
Testing: Vitest (unit + content-governance rules), axe-core/pa11y (a11y), Playwright (print render,
offline, network-interception). License: **MIT (code) / CC-BY-4.0 (content)**.

**Data model (content unit).**
```
RepairUnit {
  id: string                  // e.g. "checklist.textiles" | "guide.organizer" | "electrical.triage"
  kind: "guide" | "checklist" | "primer" | "safety-note"
  title: localized string
  riskClass: "low" | "medium" | "high"   // "high" => electrical/safety-critical => expert gate
  category: string            // e.g. "textiles" | "bikes" | "electrical" | "event-ops"
  body: localized structured content   // worth-fixing?, faults, tools, safe-handling, when-to-stop
  sources: Citation[]         // { org, title, url, retrievedDate, sourceLicense, reusePermitted }
  reviewStatus: "draft" | "in-review" | "approved"
  reviewedBy: string          // author/domain reviewer
  approvedBy: string          // MUST differ from reviewedBy (no self-approval)
  expertSignOff?: {           // REQUIRED iff riskClass == "high"
     name: string; credential: string;   // e.g. licensed/registered electrician or CEng (electrical)
     scopeConfirmed: "triage-and-referral-only";  // asserts no mains-repair instruction
     date: date; logRef: string
  }
  disclaimers: string[]       // high-risk units MUST include the "informational, not a substitute…" notice
  lang: string
  contentLicense: "CC-BY-4.0"
  contentVersion: string
  lastReviewed: date
}
```

**Key decisions (ADRs, recorded in M0).**
1. Content format (JSON vs. MDX) and how citations/license/risk are enforced in CI — **decided
   first**, because the schema and all content authoring depend on it.
2. Delivery framework (a11y + bundle size + print quality weighted), with i18n/RTL scope as input.
3. Print/PDF approach (print CSS vs. client PDF lib) — print quality is a first-class requirement.
4. Offline/SW strategy (and whether SW is needed at all vs. a downloadable print bundle).
5. Hosting target + update/versioning.

**Decision ordering (important).** The **content-format ADR (#1) lands before** the content schema
is finalized and before any content is authored; until then the schema above is **provisional**.
TASKS.md sequences this explicitly (schema + content tasks depend on the ADR task).

## Data, licensing & compliance

**This section is load-bearing. Be conservative.**

**Content sources (verify license per use).**
- **Open / openly-licensed:** the **Open Repair Alliance** Open Repair Data Standard and published
  repair data (open licenses — verify exact terms per dataset); government works that are **public
  domain** (e.g. US **CPSC** product-safety material); Wikipedia/Wikimedia (CC-BY-SA — share-alike,
  attribute) and openly-licensed imagery (verify each asset).
- **Authoritative but copyrighted — paraphrase + cite, never copy:** national safety bodies and
  standards bodies (e.g. UK **Electrical Safety First**, **OPSS**; **NFPA** electrical codes;
  manufacturer safety notices). Their **text and logos are not freely reusable**; we paraphrase,
  cite, and link.
- **Non-commercial / share-alike — link + cite only, DO NOT re-mix:** **iFixit** guides are
  **CC-BY-NC-SA** (non-commercial + share-alike) and **cannot** be relicensed into our CC-BY commons;
  we link to them as references, we do **not** copy their text/steps into our content.

**Licensing rigor (critical).**
- **Our outputs:** code **MIT**; content **CC-BY-4.0**.
- **Source reuse rule:** each source records `sourceLicense` and an explicit **`reusePermitted`**
  flag. The content-governance gate **fails the build** if a unit cites a source whose license does
  **not** permit the reuse being made (e.g. pulling text from an NC or copyrighted source). Default
  stance: **paraphrase and cite; never copy verbatim; never reuse third-party logos/trademarks;**
  when in doubt, **link, don't embed.**
- **Trademark guardrail:** **"Repair Café"** and similar marks are **not** used in outputs; the
  generic "community repair event" term is used; no third-party logos.
- **Translations** are derivatives — the same source-license rules apply, and (for medium/high units)
  translations are reviewed for **safety accuracy**, not just fluency.

**Provenance model.** Every unit carries `sources[]` with retrieval dates + license, plus a PR-tied
review-log entry. For `high`-risk units the **expert sign-off record (name, credential, date,
scope-confirmation)** is part of provenance. This log is the auditable record the *Definition of
Shipped* checks against.

**Privacy / PII stance.** **Zero PII.** No accounts, analytics, telemetry, cookies (beyond what an
optional SW needs), or third-party scripts. Crucially, the **organizer-facing templates are designed
to collect no attendee personal data**: the item-intake "ticket" records **item type + fault +
outcome only**, with a visible note *not* to record owner names/contact details on the platform's
templates. Any liability waiver or insurance step is a **pointer to seek local legal/insurance
guidance**, handled off-platform by the organizer — we provide **no** form that ingests personal
data. Enforced/audited in CI (no network egress in core flows; no PII fields in templates).

**Attribution.** Cited sources are credited per unit and in a credits page. We do **not** imply
endorsement by any agency, standards body, or trademark holder unless they have explicitly endorsed
the kit.

## Quality, review & risk gates

**Risk tier: `medium` overall, with a `high`-risk gated content class (electrical/safety-critical).**

**Required reviews before a deed is "done":**
- **Code/delivery tasks:** maintainer code review + CI green (lint, typecheck, unit,
  content-governance gate, **a11y**, **print/offline E2E**, **no-telemetry/PII** audit).
- **Low/medium content tasks:** a reviewer with relevant domain knowledge verifies each claim against
  cited sources; the **license/`reusePermitted` check** and **trademark guardrail** are enforced; the
  **author may not approve their own unit** (`reviewedBy` ≠ `approvedBy`).
- **High-risk content tasks (electrical / safety-critical) — mandatory expert gate:**
  - **Scope guardrail:** the unit must be **triage-and-referral only** (no mains-repair steps);
    `expertSignOff.scopeConfirmed = "triage-and-referral-only"`.
  - **Credentialed-expert sign-off (distinct from author):** a **licensed/registered electrician**
    (e.g. Part P / NICEIC-registered in the UK, or a state-licensed electrician in the US) **or a
    chartered/professional electrical engineer (CEng/PE, electrical)** signs off, with credential
    recorded in the review log. No self-approval.
  - **Mandatory framing:** the unit carries the disclaimer *"This is general safety information,
    not a substitute for professional electrical training, inspection, or repair. If in doubt, stop
    and consult a qualified electrician."* The content-governance gate **blocks publish** of any
    `high` unit missing the sign-off record or this disclaimer.
- **Right-to-repair primer (medium):** reviewed for neutrality and accuracy against cited sources;
  carries an **"informational, not legal advice"** notice; product/brand-neutral.
- **Accessibility (web layer):** automated axe/pa11y **and** a **manual assistive-technology audit**
  (NVDA+Firefox, JAWS+Chrome, VoiceOver+Safari, TalkBack+Chrome; keyboard-only per desktop browser)
  before each milestone exit and each release; plus a **print legibility** check (contrast, font
  size, no color-only meaning) since most field use is on paper.
- **Tamper-evident review log:** every approval/sign-off writes a PR-tied, append-only entry
  (PR #, commit SHA, unit `contentVersion`, reviewer + approver [+ expert credential for high-risk],
  sources + licenses checked, decisions).

**Definition of Shipped (project-level).** A deployed, printable, offline-capable kit that:
(1) ships only **sourced, license-clean, review-gated** content within scope; (2) has **all
electrical/high-risk content expert-signed-off** with the mandatory framing, or ships **without** any
electrical content; (3) meets WCAG 2.2 AA (web) + print legibility; (4) collects **no telemetry/PII**;
(5) is usable fully offline/on paper; and (6) is **adopted/endorsed by a named partner** in that
community's language(s). Until a partner exists, criterion (6) is **outstanding** — the kit is
"publicly usable" but not yet "shipped" by Elyos's *delivered, not merged* bar.

**"Publicly Shipped (generic public good)" fallback.** If, by a **decision point 6 months after the
M3 build is production-ready**, no partner is secured, the steward + Elyos governance may declare the
kit **Publicly Shipped (generic public good)** — criteria (1)–(5) met, deployed and distributed
directly and via community/mutual-aid and repair-network channels, outcomes tracked by best-effort
organizer self-report. A later partner endorsement **upgrades** the status rather than gating launch.

## Roadmap & milestones

Phased; each phase has measurable exit criteria. M0 is a thin cold-start foundation.

- **M0 — Foundation & cold-start (thin slice).**
  Goal: repo + delivery skeleton + content-governance scaffolding + one sourced sample checklist.
  Exit criteria: ADR #1 (content format) recorded **before** the content schema is finalized; ADRs
  for delivery framework, print/PDF, offline, hosting recorded; content schema + provenance/review-log
  format defined incl. the **risk-tier router** and **high-risk expert-gate** rules; CI runs lint/
  typecheck/unit/**content-governance gate**/axe/print-smoke + no-telemetry audit (CSP `connect-src
  'none'` + runtime network-interception E2E); **one non-electrical checklist** (textiles) renders
  from the schema, source-cited, license-clean, reviewed by an approver distinct from the author, and
  **prints legibly**; trademark guardrail verified (no "Repair Café" usage); zero PII in templates.

- **M1 — Core low-risk toolkit.**
  Goal: the real organizer value — full playbook + the non-electrical checklist set, all printable.
  Exit criteria: organizer playbook complete (planning, roles, layout, **PII-free** intake/triage
  flow, safety-rules one-pager, wrap-up, local-resource pointers); ≥ 5 non-electrical triage
  checklists reviewed + license-clean; right-to-repair primer shipped with "not legal advice" framing;
  every unit prints legibly and works offline; a11y AA on the web layer with manual AT audit; full
  kit downloadable as a print bundle.

- **M2 — Electrical safety notes (high-risk, expert-gated).**
  Goal: conservative, triage-only electrical safety notes that pass the credentialed-expert gate.
  Exit criteria: a credentialed electrician/electrical engineer (distinct from author) **signs off**;
  scope confirmed **triage-and-referral-only** (no mains-repair steps); mandatory "not a substitute"
  framing present and enforced by the governance gate; content-governance gate proven to **block**
  publish of a high-risk unit lacking sign-off or disclaimer (tested with a deliberate fixture).

- **M3 — i18n, accessibility depth, partner adoption & delivery.**
  Goal: localize, harden, secure a partner, deploy, and meet the full Definition of Shipped.
  Exit criteria: ≥ 7 reviewed non-electrical categories; ≥ 3 localized languages (UI + core kit,
  safety-accuracy reviewed); **named partner endorsement/adoption on file** (`verifiedNeed` → true);
  production deploy (web + print bundle) with versioned update strategy; outcomes-tracking process
  (organizer self-report, **no PII**, with the published waste-estimation method) operational.

Dependencies: M1 depends on M0 (schema + governance + skeleton). M2 depends on M0 governance (the
expert gate) and can run in parallel with M1 once an expert reviewer is engaged. M3 depends on M1/M2
(content base) and on the partner being secured (pursued in parallel from M0).

## Work breakdown

The itemized, schema-mapped backlog lives in **TASKS.md**, organized by the M0–M3 milestones above.
Each task maps to an Elyos Task JSON (see schema), is sized (small/medium/large), risk-tagged, and
names a reviewer. TASKS.md includes acceptance criteria for the most important tasks per milestone,
milestone Definitions of Done, a backlog, and a complete, schema-valid example Task JSON.

## Governance, roles & stakeholders

- **Maintainer (Owner): TBD.** Owns repo, roadmap, releases, review standards, license/trademark
  stance.
- **Code reviewers:** rotation of TS/web-competent contributors; ≥ 1 approval + CI green to merge.
- **Content/domain reviewers:** contributors with relevant repair-domain knowledge (textiles, bikes,
  woodwork, etc.); enforce sourcing, license/`reusePermitted`, neutrality, and no-self-approval.
- **Credentialed electrical expert(s): TO BE SECURED** — a **licensed/registered electrician or
  chartered electrical engineer** who signs off all `high`-risk electrical content. **No electrical
  content ships without this role filled.**
- **Accessibility reviewer:** contributor competent with assistive tech + print legibility.
- **Translation reviewers:** competent speakers per locale, paired with safety-accuracy re-check for
  medium/high units.
- **Steward (last-mile owner): TBD** — owns deployment, partner relationship, and getting the kit
  into organizers' hands.
- **Partner / requestor: TO BE SECURED** — a named org (library system, repair network, council/
  waste authority, men's-sheds federation) confirming need, priority categories, and languages.
- **Elyos governance/board:** arbitrates edge cases and risk-tier decisions per the good-deed
  definition; signs off the high-risk gate policy.

## Dependencies & integrations

- **External content sources (read-only, license-checked):** Open Repair Alliance / ORDS, CPSC (PD),
  Electrical Safety First / OPSS / NFPA (paraphrase+cite), iFixit (link-only, NC-SA), Wikimedia
  (CC-BY-SA), openly-licensed imagery.
- **Tooling/libraries:** static-site framework (TBD ADR), print/PDF lib, optional SW tooling, i18n
  library, test stack (Vitest, Playwright, axe-core/pa11y).
- **Hosting:** static host (GitHub Pages / Netlify / Cloudflare Pages) — no app server.
- **Elyos pieces:** Task schema (`packages/schema`), CLI workspace prep / PR flow (donated lane),
  good-deed definition & risk-tier governance, review/sign-off process.
- **Human/expert dependencies (gating, non-software):** the **credentialed electrical expert**, the
  domain reviewers, and the **partner org** — these gate shipping, not code.

## Risks & mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
| --- | --- | --- | --- | --- |
| Electrical safety content causes injury/death | Low | Critical | Hard scope guardrail (triage + referral only, **no mains repair**); mandatory credentialed-expert sign-off (distinct from author); governance gate blocks publish without sign-off + "not a substitute" framing; conservative "when in doubt, stop" rule | Electrical expert |
| Copyright/trademark misuse (iFixit NC-SA, "Repair Café" mark, agency logos/text) | Medium | High | `reusePermitted` license gate fails build on disallowed reuse; paraphrase+cite, never verbatim; no third-party logos; generic "community repair event" naming; provenance log | Maintainer |
| No partner / verified need secured | Medium | High | Pursue named partner early in parallel; 6-month-post-M3 decision point to declare "Publicly Shipped (generic public good)"; later endorsement upgrades status | Steward |
| No credentialed electrical expert recruited | Medium | High | M2 (electrical content) **does not ship** until the role is filled; M0–M1 deliver full value without electrical content; recruit via repair networks/IEE bodies early | Maintainer |
| Accidental collection of attendee PII via templates | Medium | High | Templates default to **no PII** (item+fault+outcome only); explicit "do not record personal data" notice; CI check for PII fields; off-platform handling of any waiver/insurance | Maintainer |
| Right-to-repair primer drifts into legal advice/partisanship | Medium | Medium | "Informational, not legal advice" framing; neutral, sourced; links to authoritative bodies; review for neutrality | Content reviewer |
| Content goes stale vs. updated safety/standards guidance | High | Medium | `lastReviewed` dates + periodic re-review cadence; provenance flags age; maintenance tasks; electrical units re-checked by expert | Content reviewer |
| Waste-diverted metric over-claims impact | Medium | Medium | Always presented as an **estimate** with published, cited per-category weight method; counts vs. estimates kept separate | Steward |
| Hostile/forked kit implies false endorsement (agency or trademark) | Low | Medium | Clear license/branding terms; "not an official/affiliated tool unless endorsed" disclaimer; no trademarks | Maintainer |
| Accessibility/print legibility regressions | Medium | Medium | a11y gate (axe/pa11y) blocking; manual AT audit; print-legibility check (contrast, size, no color-only meaning) | A11y reviewer |
| Maintainer bandwidth / bus factor | Medium | Medium | Reviewer rotation, documented process, MIT/CC-BY low lock-in | Maintainer |

## Security & privacy

**Threat surface.** A static, no-backend, no-PII site/bundle — small surface. Principal concerns:
(1) supply-chain risk in dependencies, (2) third-party script/tracker creep, (3) optional
service-worker cache staleness on **safety-critical** electrical content, (4) hostile forks implying
false endorsement, (5) accidental PII capture via organizer templates.

**Controls.**
- **No secrets** in the app; static hosting only; no API keys/tokens in code, logs, or receipts
  (per Elyos rule).
- **No telemetry / no PII (defense in depth):** strict CSP with **`connect-src 'none'`** (+ locked
  `script-src`/`img-src`/`font-src 'self'`) blocks runtime exfiltration; a **runtime
  network-interception E2E** fails the build on any unexpected outbound request; a static audit checks
  for trackers/analytics **and PII fields in templates**. A grep alone is not sufficient.
- **Supply chain:** pinned/locked deps (pnpm lockfile), dependency review, minimal deps, SRI where
  applicable, CI dependency audit.
- **Safety-content integrity:** if an optional SW caches content, a content-version manifest +
  per-unit integrity hash lets a **corrected electrical safety note be hard-invalidated** (purged +
  re-fetched, non-dismissible) so a corrected safety instruction is never served stale. The
  recommended primary distribution remains the **versioned print bundle**, which carries a visible
  version + date so a stale paper copy is identifiable.
- **Content integrity:** all guidance source-cited, license-checked, and review-/expert-gated.
- **Abuse/misuse:** prominent disclaimer that the kit is not an official or affiliated product unless
  a named partner endorses it; trademark/branding terms documented; license requires attribution.

## Sustainability & maintenance

- **Ownership after delivery:** the **maintainer** owns code/content releases; the **steward** owns
  deployment + the partner relationship; the **electrical expert** owns periodic re-validation of
  high-risk units. All currently **TBD/TO BE SECURED** and must be named before the relevant milestone
  (electrical expert before M2; partner + steward before M3 "shipped").
- **Content freshness:** units carry `lastReviewed`; a **periodic re-review cadence** (≥ annually, and
  after any material change to official safety/standards guidance) is enforced via maintenance tasks;
  electrical units are re-checked by a credentialed expert; stale units flagged.
- **Outcomes tracking:** privacy-preserving **organizer self-report** (events run, items assessed/
  repaired by category, estimated waste diverted via published method) — **no PII, no telemetry**.
- **Low lock-in:** MIT/CC-BY, static hosting, standard web + print tech keep the kit forkable and
  cheap to run.

## Open questions

1. **Partner org:** Who is the named partner (library system / repair network / council / men's
   sheds)? Needed before *Definition of Shipped*. **Human decision required.**
2. **Credentialed electrical expert:** Who signs off high-risk content, and to which jurisdiction's
   standards (UK Part P/NICEIC vs. US NEC/state licensing vs. EU)? Affects framing + sourcing.
   **Human decision required before M2.**
3. **Jurisdiction(s) of first focus:** safety/standards and right-to-repair frameworks differ by
   country; which region(s) and language(s) first (should be partner-driven)?
4. **Insurance/liability material:** how far do we go beyond "seek local legal/insurance advice"?
   (Default: pointers only, no advice.)
5. **Waste-estimation weight factors:** which cited source(s) for per-category average item weights?
6. **Delivery framework / print / offline ADRs** (M0).
7. **Item-category priority list:** confirm the first 7 non-electrical categories (partner-driven).

## References

- Elyos work rules — `C:\code\elyos\CLAUDE.md`
- Good-deed definition & risk tiers — `C:\code\elyos\docs\good-deed-definition.md`
- Task schema — `C:\code\elyos\packages\schema\src\schemas.ts`
- Portfolio roadmap (project listed Track 6) — `C:\code\elyos\planning\ROADMAP.md`
- Sibling exemplar plan — `C:\code\elyos\planning\projects\proper-prepper\PLAN.md`
- Content sources (license-checked per use): Open Repair Alliance / Open Repair Data Standard; US CPSC
  (public domain); UK Electrical Safety First / OPSS, NFPA (paraphrase + cite, copyrighted); iFixit
  (CC-BY-NC-SA — link/cite only); Wikimedia (CC-BY-SA).
- WCAG 2.2 AA (W3C Web Content Accessibility Guidelines).
- Trademark note: "Repair Café" is a registered trademark of Stichting Repair Café International —
  not used in outputs; this project is unaffiliated.

---

## Appendix A — Improvements applied

The following 25 specific improvements were made to the draft and are **already reflected** in the
plan above (and in TASKS.md). Each names the change and where it landed.

1. **Trademark guardrail made explicit and load-bearing.** Added a clear "Repair Café is a
   registered trademark; we are unaffiliated; use generic 'community repair event'; repo slug is
   internal-only" rule to the Executive summary, Non-goals, Licensing, and References.
2. **Electrical content re-tiered to `high` with a hard expert gate.** The roadmap's "low" label is
   overridden for electrical content: a credentialed-electrician/CEng sign-off (distinct from author)
   is mandatory, enforced by a build-time governance gate.
3. **"Triage-and-referral only, no mains repair" scope guardrail.** Codified as a non-goal, a schema
   field (`scopeConfirmed`), and a tested governance rule, so the riskiest failure mode (teaching
   mains repair) is structurally impossible to ship.
4. **Mandatory "informational, not a substitute" framing** for all high-risk units, enforced by the
   governance gate (publish blocked if the disclaimer is missing).
5. **License `reusePermitted` flag + build-time license gate.** Prevents pulling text from
   non-commercial (iFixit CC-BY-NC-SA) or copyrighted (NFPA, agency) sources into our CC-BY commons.
6. **iFixit handled correctly as link-only.** Explicitly called out that its NC-SA license forbids
   re-mixing into CC-BY; we cite/link, never copy.
7. **No-self-approval rule** (`reviewedBy` ≠ `approvedBy`) applied to all content, mirroring the
   sibling exemplar and enforced in CI.
8. **Zero-attendee-PII template design.** Item-intake "ticket" records item+fault+outcome only, with
   an explicit "do not record personal data" notice and a CI check for PII fields — a privacy risk
   unique to event tooling that a generic plan would miss.
9. **Waste-diverted metric honestly framed as an estimate** with a published, cited per-category
   weight method; confirmed counts kept separate from estimates.
10. **Outcome metrics made beneficiary-centric** (events run, items assessed/repaired, waste
    diverted, partner adoption) rather than vanity metrics, with privacy-preserving measurement.
11. **Right-to-repair primer constrained to "informational, not legal advice"** and product/brand-
    neutral, with neutrality review — avoiding the "unqualified high-stakes advice" guardrail.
12. **Content-format ADR sequenced first**, with the schema marked provisional until it lands, and
    TASKS dependencies wired accordingly (avoids rework).
13. **Print legibility elevated to a first-class quality gate** (contrast, font size, no color-only
    meaning) because real field use is on paper in low-connectivity venues.
14. **Offline/print bundle as primary distribution**, with the optional SW's stale-content risk
    mitigated via content-version manifest + hard-invalidation for corrected safety notes.
15. **Governance gate proven by a negative test** (M2): a deliberate fixture confirms the build
    **blocks** a high-risk unit lacking sign-off or disclaimer — not just asserting the happy path.
16. **"Publicly Shipped (generic public good)" fallback** with a concrete 6-month-post-M3 decision
    point, so a finished kit isn't stranded by the missing partner.
17. **Electrical-expert role gating M2** added to Risks and Governance: M0–M1 deliver full value
    without electrical content if the expert isn't yet recruited.
18. **Jurisdiction ambiguity surfaced** (UK Part P/NICEIC vs. US NEC/state vs. EU) as an open
    question that shapes both safety framing and right-to-repair content.
19. **Source-neutrality + no-endorsement clause**: we never imply agency/standards-body endorsement
    unless explicitly given; no third-party logos.
20. **Defense-in-depth no-telemetry enforcement** (CSP `connect-src 'none'` + runtime
    network-interception E2E + static audit), not a grep alone.
21. **Accessibility support matrix named** (NVDA/JAWS/VoiceOver/TalkBack + keyboard-only) with a
    defined cadence, rather than an ad-hoc spot check.
22. **i18n scope settled as input to the framework ADR** (RTL, bundled offline fonts, ICU plural/
    select, locale formatting) so localization isn't retrofitted.
23. **Periodic re-validation cadence** for content, with electrical units re-checked by a credentialed
    expert and stale units flagged via `lastReviewed`.
24. **Versioned print bundle carries a visible version + date** so a stale paper copy is identifiable
    in the field — closing the gap that digital-only invalidation leaves for printed material.
25. **Tamper-evident, PR-tied review/sign-off log** (incl. expert credential for high-risk units) as
    the single auditable basis for the *Definition of Shipped*.

## Review sign-off

**Reviewer:** drafting agent (senior staff engineer + TPM), self-review pass.
**Date:** 2026-06-28 · **Plan version reviewed:** 0.1.0.

**Completeness.** All 17 required H2 sections from `PLAN_SPEC.md` are present and in order; Appendix A
(25 applied improvements) and this sign-off are appended. TASKS.md exists with the required map,
per-milestone tables, acceptance criteria, DoDs, a backlog, and a schema-valid example Task JSON.

**Correctness checks performed and resolved.**
- **Schema conformance:** the example Task JSON includes every `required` field from
  `taskSchema` (id, title, project, type, lane, priority, domain, riskTier, urgent, deliverable,
  tokenEstimate, status, context, objective, acceptanceCriteria, output, verifiedNeed) with enum-valid
  values; `acceptanceCriteria` has ≥ 1 item; `outputLicense` set; donated lane so no `fundedBudgetUsd`
  required. Verified the conditional `if lane==funded then fundedBudgetUsd` does not apply.
- **Honesty defaults:** every Task sets `verifiedNeed: false` and `requestor: "TBD"` because no
  partner is secured — consistent with the plan's TO-BE-SECURED stance.
- **Risk-tier consistency:** all electrical Tasks are `riskTier: high` and carry the expert-sign-off
  acceptance criteria + "not a substitute" framing; the roadmap's "low" label is explicitly
  overridden and the rationale stated.
- **Guardrail coverage:** license/provenance (reusePermitted gate, iFixit link-only, no logos),
  trademark ("Repair Café" not used), privacy (zero attendee PII), and the high-risk expert gate are
  each present in Plan + enforced via a TASKS item and acceptance criteria.
- **Dependency sanity:** content/schema tasks depend on the content-format ADR; M2 depends on M0
  governance + the recruited expert; M3 depends on M1/M2 + partner. No dangling dependencies.

**Residual items requiring a human decision (not blockers to M0):** named partner; named credentialed
electrical expert + target jurisdiction; first language(s); waste-estimation weight source. These are
tracked in *Open questions* and reflected as `verifiedNeed: false` / TO BE SECURED throughout.

**Verdict:** Plan is internally consistent, schema-aligned, and guardrail-complete for a `medium`
project with a gated `high`-risk class. Approved as **Draft v0.1.0** for Elyos governance review.
