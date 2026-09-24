# LAUNCH OS — Localization

Updated: 2026-09-24

## Supported languages

- English — primary
- Italian
- German
- French
- Russian

## Implementation

Localization is implemented in the browser prototype without external i18n dependencies.

The locale layer provides:
- translated workflow navigation
- translated project/language/navigation labels
- translated save/export/import/reset controls
- translated Product Profile labels and placeholders
- translated stage headings and guidance
- translated core form placeholders for Validation, Product, Offer, Pricing, Research, Sales Page, Content, Launch and Growth
- translated validation/search/import/reset feedback
- persisted language preference through localStorage key launchos_lang
- language included in portable project state and validated on import

The locale dictionary is kept separate from Product Profile data. Product data is never duplicated per language.

## Runtime contract

setLanguage() changes the active locale, updates the document language, reapplies translated UI text, rerenders workflow navigation and preserves the selected workflow stage.

Supported locale codes: en, it, de, fr, ru.

## Product boundary

Localization does not introduce Notion, backend infrastructure, paid APIs or external translation services. The MVP remains local-first.

## QA boundary

Static source verification confirms all five locale dictionaries exist, locale switching is wired to the language selector, language is persisted, import validation accepts only the five supported locales, and workflow labels plus core form placeholders have locale variants.

Real browser/device execution is not claimed here. That remains part of B10.

## B06 acceptance

B06 is complete at implementation level when all supported languages have a real dictionary-backed UI path rather than a shell-only selector.

B06 is now closed at 100%.