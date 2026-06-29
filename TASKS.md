# TASKS — repair-cafe-kits (open community-repair event guides + fixable-item checklists)

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (maintainer) · Lane: donated

## How these tasks map to Elyos

Each task below becomes an Elyos **Task JSON** validated against
`packages/schema/src/schemas.ts`. Field mapping:

- `id` — stable slug ID, e.g. `repair-cafe-kits-arch-001`.
- `title` — the task title from the table.
- `project` — `"repair-cafe-kits"`.
- `type` — one of `code | research | writing | data | design-spec | maintenance` ("Type" column).
- `lane` — `"donated"` for all tasks here (no escrow/API spend). A `funded` task would additionally
  require `fundedBudgetUsd`.
- `priority` — `high | medium | low`.
- `domain` — array, e.g. `["environment","right-to-repair","software","accessibility","safety"]`.
- `riskTier` — `low | medium | high` ("Risk" column). **All electrical/safety-critical tasks are
  `high`** and require credentialed-expert sign-off.
- `urgent` — boolean (default `false`; this is community infrastructure, not live response).
- `deliverable` — `pr | dataset | document | translation` ("Deliverable" column).
- `tokenEstimate` — `small | medium | large` ("Size" column).
- `status` — `open | in-progress | review | delivered | done` (all start `open`).
- `context`, `objective`, `acceptanceCriteria[]`, `output` — task narrative + checkable criteria.
- `resources[]` — source/reference URLs or repo paths.
- `requestor` — partner/requestor (**TO BE SECURED**; `"TBD"` until a partner is named).
- `verifiedNeed` — **`false` until a named partner org confirms need in writing** (honest default).
- `outputLicense` — `"MIT"` for code, `"CC-BY-4.0"` for content/translations.

**Reviewer column legend:** `maintainer` (code review), `content` (domain reviewer), `electrical-SME`
(credentialed/licensed electrician or chartered electrical engineer — for `high`-risk content),
`a11y` (accessibility + print legibility reviewer), `translation+safety` (competent speaker paired
with safety-accuracy re-check), `steward` (last-mile/partner owner).

**Content review rules (all content tasks):** the unit's **author may not approve their own work**
(`reviewedBy` ≠ `approvedBy`); each unit cites sources with a `reusePermitted` flag and the build
**fails on disallowed reuse** (no NC/copyrighted text copied; no third-party logos/trademarks; no
"Repair Café" naming). Every approval writes a **PR-tied, append-only review-log entry**.

**High-risk (electrical) rule:** a `high` unit ships **only** with (a) `electrical-SME` sign-off
distinct from the author and credential recorded, (b) scope confirmed **triage-and-referral-only (no
mains-repair steps)**, and (c) the mandatory **"informational, not a substitute for professional
electrical training/inspection/repair"** disclaimer. The content-governance gate blocks publish
otherwise.

**Sequencing rule (M0):** the content-format ADR (**arch-001**) is decided **before** the content
schema (**data-002**) and any authored content; until then the schema is provisional.

---

## Milestone M0 — Foundation & cold-start

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| repair-cafe-kits-arch-001 | ADRs: content format (**decide first**), delivery framework (i18n/RTL scope as input), print/PDF, offline strategy, hosting | design-spec | small | low | document | — | maintainer |
| repair-cafe-kits-data-002 | Content-unit schema + provenance/review-log + **risk-tier router & high-risk expert-gate** rules | data | medium | medium | dataset | arch-001 | maintainer, content |
| repair-cafe-kits-site-003 | Static, printable, offline-capable delivery skeleton (renders a unit; prints legibly) | code | medium | low | pr | arch-001 | maintainer, a11y |
| repair-cafe-kits-ci-004 | CI gates: lint, typecheck, unit, **content-governance gate** (citation/license/`reusePermitted`, no-self-approval, high-risk-needs-expert), axe a11y, print-smoke, no-telemetry/PII audit | code | medium | low | pr | site-003 | maintainer |
| repair-cafe-kits-content-005 | Sample non-electrical triage checklist (textiles), source-cited + license-clean | writing | small | low | document | data-002 | content |

**Acceptance criteria — key tasks**

- **repair-cafe-kits-data-002 (schema + governance rules):**
  - Schema captures: `id`, `kind`, localized `title`, `riskClass`, `category`, localized `body`,
    `sources[]` (org/title/url/retrievedDate/sourceLicense/`reusePermitted`), `reviewStatus`,
    `reviewedBy`, `approvedBy` (distinct), optional `expertSignOff` (name/credential/`scopeConfirmed`/
    date/logRef), `disclaimers[]`, `lang`, `contentLicense`, `contentVersion`, `lastReviewed`.
  - Risk-tier router classifies each unit and the build **rejects**: a unit missing required
    citations; a unit citing a source whose license does not permit the reuse made; a unit where
    `approvedBy == reviewedBy`; a `high` unit lacking a valid `expertSignOff` **or** the mandatory
    "not a substitute" disclaimer.
  - Format follows the content-format ADR (arch-001), which lands first; schema is provisional until.
- **repair-cafe-kits-ci-004 (CI gates):**
  - CI fails on lint/type/unit errors, on any critical axe violation, on print-smoke failure, and on
    the content-governance gate rejecting an invalid unit.
  - No-telemetry/no-PII uses defense in depth: static audit (trackers/analytics **and PII fields in
    templates**) **plus** a runtime network-interception E2E that fails on any unexpected outbound
    request; CSP `connect-src 'none'` asserted. A grep alone does not pass.
- **repair-cafe-kits-content-005 (textiles sample):**
  - Every claim traceable to a cited, **reuse-permitted** source; retrieval date + license recorded;
    no verbatim copying of copyrighted/NC text; no third-party logos; no "Repair Café" naming.
  - Reviewed by an approver **distinct from the author**; PR-tied review-log entry written.
  - Renders from the schema and **prints legibly** (contrast, font size, no color-only meaning).

**Definition of Done (M0):** ADRs recorded (content format first); content schema + provenance/
review-log + risk-tier router + expert-gate rules defined; CI enforces governance/a11y/print/
no-telemetry-PII gates; the delivery skeleton renders and prints one source-cited, license-clean,
distinctly-reviewed textiles checklist; trademark guardrail verified; zero PII in templates.

---

## Milestone M1 — Core low-risk toolkit

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| repair-cafe-kits-content-006 | Organizer playbook (planning, roles, layout, **PII-free** intake/triage flow, safety-rules one-pager, wrap-up, local-resource pointers) | writing | large | medium | document | content-005 | content |
| repair-cafe-kits-content-007 | Non-electrical triage checklist set (furniture/wood, bikes, ceramics/gluing, jewelry, toys) — ≥ 5 categories | writing | large | medium | document | content-005 | content |
| repair-cafe-kits-content-008 | Right-to-repair primer (find manuals/parts; rights overview) — **informational, not legal advice** | writing | medium | medium | document | content-005 | content |
| repair-cafe-kits-feat-009 | Client-side print bundle / PDF export of the full kit (no server) | code | medium | low | pr | site-003, content-006 | maintainer, a11y |
| repair-cafe-kits-a11y-010 | WCAG 2.2 AA hardening + manual assistive-tech audit + print-legibility audit | code | medium | low | pr | site-003, feat-009 | a11y |

**Acceptance criteria — key tasks**

- **repair-cafe-kits-content-006 (organizer playbook):**
  - End-to-end coverage so a first-time organizer can run a safe event; roles + station layout +
    safety-rules one-pager included.
  - The intake/triage "ticket" template collects **no attendee PII** (item type + fault + outcome
    only) and carries a visible "do not record personal data" notice; liability/insurance handled as
    **pointers to local guidance**, never an on-platform form.
  - Sourced where claims are factual; license-clean; no trademark usage; distinctly reviewed.
- **repair-cafe-kits-content-008 (right-to-repair primer):**
  - Product/brand-neutral; cites authoritative sources; carries the **"informational, not legal
    advice"** disclaimer; reviewed for neutrality + accuracy.
  - Does **not** reproduce copyrighted manuals; links to legitimate manual/parts sources only.
- **repair-cafe-kits-a11y-010 (AA + print):**
  - Automated axe/pa11y pass with 0 critical issues across core flows.
  - Documented manual AT audit (NVDA+Firefox, JAWS+Chrome, VoiceOver+Safari, TalkBack+Chrome,
    keyboard-only per desktop browser) signed off by the qualified reviewer; cadence before milestone
    exit + each release.
  - Print-legibility audit passes (contrast ≥ AA, minimum font size, no color-only meaning).

**Definition of Done (M1):** organizer playbook + ≥ 5 non-electrical triage checklists + the
right-to-repair primer shipped (sourced, license-clean, distinctly reviewed); full kit exportable as
a print bundle and usable offline; web layer meets WCAG 2.2 AA (automated + manual) and print
legibility; zero PII confirmed.

---

## Milestone M2 — Electrical safety notes (high-risk, expert-gated)

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| repair-cafe-kits-research-011 | Recruit + confirm a credentialed electrical SME (licensed/registered electrician or CEng/PE) + target jurisdiction/standards | research | small | medium | document | — | maintainer, steward |
| repair-cafe-kits-content-012 | Electrical safety **triage** notes (visual red flags, refuse criteria, PAT framing, "refer to a qualified person") — **no mains-repair steps** | writing | medium | high | document | data-002, research-011 | electrical-SME |
| repair-cafe-kits-ci-013 | Governance-gate **negative test**: build blocks a high-risk unit lacking expert sign-off or the mandatory disclaimer (deliberate fixture) | code | small | medium | pr | ci-004 | maintainer |

**Acceptance criteria — key tasks**

- **repair-cafe-kits-research-011 (recruit SME):**
  - A **credentialed electrician or chartered/professional electrical engineer** is engaged, with
    credential + jurisdiction recorded; willing to sign off and periodically re-validate.
  - If unfilled, M2 **does not proceed** to publish electrical content (M0–M1 value is unaffected).
- **repair-cafe-kits-content-012 (electrical triage notes):**
  - Strictly **triage-and-referral only** — no instruction to open/rewire/repair mains items;
    `expertSignOff.scopeConfirmed = "triage-and-referral-only"`.
  - Signed off by the `electrical-SME` **distinct from the author**, credential recorded in the
    review log; sources paraphrased + cited (no verbatim from copyrighted codes/agencies; no logos).
  - Carries the mandatory **"informational, not a substitute for professional electrical training,
    inspection, or repair — if in doubt, stop and consult a qualified electrician"** disclaimer.
- **repair-cafe-kits-ci-013 (negative test):**
  - A test fixture of a `high` unit **without** sign-off and one **without** the disclaimer each cause
    the content-governance gate to **fail the build**; a fully-compliant fixture passes.

**Definition of Done (M2):** credentialed electrical SME engaged; electrical triage notes shipped
under the expert gate with confirmed triage-only scope + mandatory framing; the governance gate is
**proven by a negative test** to block non-compliant high-risk units.

---

## Milestone M3 — i18n, accessibility depth, partner adoption & delivery

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
| --- | --- | --- | --- | --- | --- | --- | --- |
| repair-cafe-kits-i18n-014 | i18n framework (RTL, bundled offline fonts, ICU plural/select, locale formatting) + completeness check in CI | code | medium | low | pr | site-003 | maintainer, a11y |
| repair-cafe-kits-l10n-015 | Localize core kit (organizer playbook + ≥ 2 checklists) into ≥ 2 non-English languages, safety-accuracy reviewed | writing | large | medium | translation | i18n-014, content-006, content-007 | translation+safety |
| repair-cafe-kits-content-016 | Expand to ≥ 7 reviewed non-electrical categories (add general-mechanical + 1 more) | writing | medium | medium | document | content-007 | content |
| repair-cafe-kits-research-017 | Secure named partner org (need, priority categories, languages, endorsement) | research | medium | medium | document | — | maintainer, steward |
| repair-cafe-kits-deploy-018 | Production deploy (web + versioned print bundle w/ visible version+date) + disclaimer/branding terms | code | medium | low | pr | a11y-010, i18n-014 | maintainer, steward |
| repair-cafe-kits-ops-019 | Outcomes-tracking process (organizer self-report, **no PII**, published waste-estimation method) + re-review cadence | maintenance | small | low | document | research-017 | maintainer, steward |

**Acceptance criteria — key tasks**

- **repair-cafe-kits-research-017 (secure partner):**
  - A named org (library system / repair network / council/waste authority / men's-sheds federation)
    confirms the need in writing (letter of support or MOU) and names priority categories + languages.
  - On success, `verifiedNeed` flips to `true` and `requestor` is set to the named org across tasks.
- **repair-cafe-kits-l10n-015 (localization):**
  - Translations of medium/high content are **safety-accuracy reviewed**, not only fluency-checked;
    high-risk (electrical) translations also re-confirmed against the SME-approved source meaning.
  - Source-license/attribution rules respected; `contentLicense` = CC-BY-4.0; fonts bundled offline.
- **repair-cafe-kits-ops-019 (outcomes + freshness):**
  - Privacy-preserving self-report template (events run; items assessed/repaired by category;
    **no PII**) with a **published, cited per-category weight method** for the waste-diverted estimate;
    confirmed counts kept separate from estimates.
  - Re-review cadence defined (≥ annual; sooner on guidance change); electrical units re-validated by
    the SME; stale-content flagging via `lastReviewed`; print bundle carries visible version + date.

**Definition of Done (M3):** ≥ 7 reviewed non-electrical categories; ≥ 3 localized languages
(safety-accuracy reviewed); **named partner endorsement/adoption on file** (`verifiedNeed = true`);
production web + versioned print bundle deployed with disclaimer/branding; outcomes tracking +
re-review cadence operational. Satisfies *Definition of Shipped (partner-adopted)*.

**Decision point (so a finished kit isn't stranded):** if no partner is secured by **6 months after
the M3 production build is ready**, the steward + Elyos governance declare **"Publicly Shipped
(generic public good)"** — Plan criteria (1)–(5) met, distributed directly and via community/repair-
network channels, outcomes by best-effort self-report. A later endorsement upgrades the status.

---

## Backlog / future

| ID | Title | Type | Size | Risk | Deliverable | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| repair-cafe-kits-content-020 | Easy-read / low-literacy checklist variants | writing | medium | medium | document | a11y + content review |
| repair-cafe-kits-content-021 | Open pictogram/icon set for stations + triage (license-clean) | design-spec | medium | low | document | No third-party logos/trademarks |
| repair-cafe-kits-content-022 | Small-appliance **mechanical** (non-mains) triage (e.g. battery, manual) | writing | medium | medium | document | Strictly non-mains; SME advisory |
| repair-cafe-kits-data-023 | Optional integration with Open Repair Data Standard for fault patterns | data | medium | medium | dataset | License-verified ORDS only |
| repair-cafe-kits-feat-024 | Optional service-worker offline cache + content-version manifest/hard-invalidation | code | medium | low | pr | For corrected safety notes |
| repair-cafe-kits-ops-025 | Annual re-validation pass (electrical units re-checked by SME) | maintenance | small | medium | document | Recurring |
| repair-cafe-kits-sec-026 | Dependency/supply-chain audit + SRI hardening | maintenance | small | low | pr | Recurring |
| repair-cafe-kits-content-027 | Event-organizer liability/insurance pointer pack per jurisdiction (pointers, not advice) | writing | small | medium | document | Links only; no advice |

---

## Example task JSON

Complete, schema-valid Task JSON for the first M0 task. `verifiedNeed` is `false` and `requestor` is
`"TBD"` because **no partner org is secured yet** (honest default per the plan).

```json
{
  "id": "repair-cafe-kits-arch-001",
  "title": "ADRs: content format (decide first), delivery framework, print/PDF, offline, hosting",
  "project": "repair-cafe-kits",
  "type": "design-spec",
  "lane": "donated",
  "priority": "high",
  "domain": ["right-to-repair", "environment", "software", "accessibility"],
  "riskTier": "low",
  "urgent": false,
  "deliverable": "document",
  "tokenEstimate": "small",
  "status": "open",
  "context": "repair-cafe-kits is an openly-licensed, printable, offline-usable set of guides and fixable-item checklists that let anyone run a community repair event and safely triage common items, advancing right-to-repair. This task records the foundational architecture decisions. The content-format ADR must be decided first because the content schema and all authored guides/checklists depend on it; electrical content is a gated high-risk class requiring credentialed-expert sign-off, so the format must be able to express risk class, citations with a reuse-permitted flag, and an expert sign-off record.",
  "objective": "Record ADRs for: (1) content format (JSON vs MDX, decided first) and how citations/license/risk are enforced in CI; (2) the static delivery framework with i18n/RTL scope as input; (3) print/PDF approach; (4) offline strategy; (5) hosting + versioning.",
  "acceptanceCriteria": [
    "ADR #1 selects a content format and specifies how per-unit citations, source license + reusePermitted, risk class, and the high-risk expert sign-off record are validated in CI; this ADR is recorded before the content schema is finalized",
    "ADR #2 selects an accessibility-first, low-bundle delivery framework with i18n/RTL, bundled offline fonts, and ICU pluralization scope captured as explicit inputs",
    "ADR #3 selects a print/PDF approach that meets print-legibility requirements (contrast, font size, no color-only meaning)",
    "ADR #4 records the offline strategy (downloadable print bundle as primary; optional service worker), and ADR #5 records the static hosting + versioning target",
    "Each ADR states the trademark guardrail (no 'Repair Café' name/logo; generic 'community repair event') and the zero-telemetry/zero-PII posture as binding constraints"
  ],
  "resources": [
    "C:\\Users\\jason\\AppData\\Local\\Temp\\claude\\C--code-elyos\\5eca0d44-6b8b-4c30-9696-37a524cb249a\\scratchpad\\plans\\repair-cafe-kits\\PLAN.md",
    "C:\\code\\elyos\\packages\\schema\\src\\schemas.ts",
    "C:\\code\\elyos\\planning\\projects\\proper-prepper\\PLAN.md"
  ],
  "output": "A committed ADR set (5 decisions) covering content format, delivery framework, print/PDF, offline strategy, and hosting, with the content-format ADR decided first and the trademark/privacy guardrails recorded as binding constraints.",
  "requestor": "TBD",
  "verifiedNeed": false,
  "outputLicense": "MIT"
}
```
