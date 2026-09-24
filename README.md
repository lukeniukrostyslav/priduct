# LAUNCH OS

Standalone local-first web application for creators and freelancers who want to take a digital product from **IDEA → VALIDATION → PRODUCT → OFFER → PRICING → RESEARCH → SALES PAGE → CONTENT → LAUNCH → GROWTH**.

## What it is

LAUNCH OS is a practical workflow application, not a PDF guide, prompt pack, course, Notion workspace, or generic income promise.

The product keeps one **Product Profile** as a source of truth and carries it through validation, product definition, offer, pricing, research, sales-page drafting, content planning, launch preparation, and growth.

## Core capabilities

- Product Profile as shared source of truth
- Idea readiness scoring
- Validation evidence and decision tracking
- Product and Offer definition
- Pricing scenarios and calculator
- Online research through the user's normal browser
- Research evidence log with handoff into Validation
- Sales Page draft generator
- 7-post launch Content Plan generator
- Launch checklist generator
- Growth loop generator
- Local persistence in the browser
- JSON export/import for portability and recovery
- English, Italian, German, French and Russian UI
- Responsive desktop/mobile browser layout

## Commercial model

- **One paid product**
- **One-time purchase**
- Initial launch price target: **$29**
- No subscription
- No Free/Core/Pro tiers
- No guaranteed-income claims

The price is a test hypothesis and may be revised after real customer feedback.

## Infrastructure

The core product is local-first:

- no VPS required
- no mandatory backend
- no database required
- no Redis/Docker requirement
- no paid AI API required
- no paid search API required

Online research uses ordinary browser search. The application does not pretend to provide live data or AI results where none are available.

## How to run

Open:

`prototype/index.html`

in a modern desktop or mobile browser.

The MVP stores project state locally in the browser. Use **Export** to create a JSON backup before clearing or moving a project.

## Product workflow

1. Idea
2. Validation
3. Product
4. Offer
5. Pricing
6. Research
7. Sales Page
8. Content
9. Launch
10. Growth

## Current development status

The functional QA block is complete at source level. Responsive/device execution testing is still pending, and commercial packaging is the current development phase.

See:

- `docs/PROGRESS.md`
- `docs/DECISIONS.md`
- `docs/MARKET_VALIDATION_V1.md`
- `docs/DESIGN_SYSTEM_V1.md`
- `docs/LOCALIZATION.md`

## Important product boundaries

LAUNCH OS deliberately does **not** include:

- Notion integration or Notion workspace
- mandatory cloud infrastructure
- paid AI/search dependencies
- guaranteed earnings or sales claims
