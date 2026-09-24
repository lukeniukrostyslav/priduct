# LAUNCH OS — Architecture V1

Updated: 2026-09-24

## 1. Architectural decision
LAUNCH OS is a standalone local-first web application.
The current MVP is intentionally implemented as a single browser-delivered document:
- prototype/index.html — application shell, UI, styles and runtime logic
- docs/ — product, architecture, decision, localization and progress documentation

Core application requirements do not include VPS, backend API, database, Redis, Docker, paid AI API, paid search API, Notion, or a mandatory third-party account. The browser is the runtime and localStorage is the persistence layer.

## 2. Product architecture
The product is organized as a linear ten-stage workflow:
| Step | Stage | Primary responsibility |
|---:|---|---|
| 0 | Idea | Product Profile and idea readiness |
| 1 | Validation | Evidence, source, strength and decision |
| 2 | Product | Scope, outcome, delivery |
| 3 | Offer | Promise, format, inclusions, differentiation, CTA |
| 4 | Pricing | Scenario calculation and price hypothesis |
| 5 | Research | Browser research and evidence log |
| 6 | Sales Page | Structured sales-page draft |
| 7 | Content | Seven-post launch sequence |
| 8 | Launch | Before / launch day / after checklist |
| 9 | Growth | Measure → Learn → Improve → Experiment |

The workflow is sequential for the user, but application state is shared. Later stages read earlier-stage fields rather than maintaining duplicate product facts.

## 3. Single source of truth
The Product Profile is the central product identity:
- name
- problem
- audience
- outcome
- productFormat
- productScope
- productOutcome
- productDelivery

Offer, pricing, research, sales-page, content, launch and growth generators consume this shared state.

## 4. Runtime structure
Logical runtime layers inside prototype/index.html:
- Presentation: sidebar, top bar, responsive navigation, workflow navigation, cards and forms
- Workflow state: activeStep, ten-stage navigation, bounded stage selection 0–9, contextual next-step guidance
- Domain state: Product Profile, Validation, Product, Offer, Pricing, Research, Sales Page, Content, Launch, Growth
- Persistence: buildState(), save(), load(), validateState(), exportData(), importData(), clearData()
- Generation: generateSalesPage(), generateContentPlan(), generateLaunchChecklist(), generateGrowthLoop()
- Research: query derivation, Google/Bing/DuckDuckGo search, evidence log, Research → Validation handoff

## 5. State contract
Current portable project state uses version 2.
Conceptual structure:
{ version: 2, savedAt: ISO timestamp, language: ru|en|it|de|fr, activeStep: 0..9, researchQuery: string, workflow fields: string }
All current form fields are persisted as strings.
Import accepts an object with integer version >= 2, string values for known form fields when present, activeStep in 0..9, and a supported language value.
Invalid JSON and invalid state are rejected without replacing the existing project.

## 6. Persistence and recovery
Normal persistence: form input → buildState() → JSON → localStorage[launchos].
Language preference is also stored separately in localStorage[launchos_lang].
Portable recovery: Export JSON → external user backup → Import JSON → validateState() → localStorage.
Reset requires browser confirmation, clears project state, language preference and research query, then returns to stage 0.
The product does not claim cloud backup or synchronization.

## 7. Online Research architecture
Research is intentionally browser-first.
Flow: Product Profile / Research Query → browser search engine → user reviews sources → structured evidence entry → research log → Validation.
Supported search actions: Google, Bing and DuckDuckGo.
The application does not scrape search results and does not claim to provide live research data internally.

## 8. Cross-stage data flow
Validation consumes Product Profile and Research evidence and produces hypothesis, evidence, source, finding, strength and decision.
Product context feeds Offer through outcome, format and scope.
Product Profile + Validation + Offer + Pricing feed the Sales Page generator.
Product + Offer + Validation + Pricing feed the seven-post Content generator.
Sales Page + Content + Offer + Pricing feed the Launch checklist.
Validation + Product + Offer + Pricing feed the Growth loop.

## 9. Commercial boundary
Architecture is aligned with the locked commercial model: one paid product, one-time purchase, initial price target $29, no subscription, no Free/Core/Pro tiers.
The $29 value is a launch pricing hypothesis, not a guaranteed commercial outcome.

## 10. Localization boundary
Supported languages are English, Italian, German, French and Russian.
The architecture treats localization as a separate concern from product data. The current MVP contains a limited translation shell; the full dictionary/i18n implementation belongs to B06 and is not considered complete in B04.

## 11. Responsive architecture
The application is one responsive web experience, not separate desktop/mobile applications.
Desktop uses sidebar + workspace + supporting column. Tablet reflows the workspace. Mobile uses a collapsible sidebar and single-column workspace.
Responsive CSS is not proof of real-device QA; device/browser execution remains B10.

## 12. Security and privacy model
Project data is stored in the user's browser. No application backend receives project state. No cloud project database is implied. Research searches open in the user's browser.
Users are responsible for exporting backups before clearing browser storage.

## 13. Extension points
Future refactoring can split the monolith into state, i18n, research, generators, workflow and UI modules without changing the product contract.

## 14. B04 acceptance criteria
B04 is complete when the repository explicitly documents runtime boundary, workflow stages, Product Profile source of truth, state contract, persistence/recovery, research flow, cross-stage data flow, localization boundary, responsive boundary, commercial boundary, security/privacy boundary, extension points, and separation from B06 and B10.
All of these criteria are now documented and mapped to the current MVP.

## 15. Out of scope for B04
- Full i18n dictionary implementation — B06
- Real browser/device visual execution — B10
- Commercial packaging — B12
- Gumroad release — B13
These blocks must be completed in sequence after their predecessors.