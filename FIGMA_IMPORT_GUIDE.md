# Figma import guide

## What this is
This is an honest, editable import package. It is not a `.fig` file. Each screen is an individual SVG canvas sized 393 × 852 px (intended as an initial 393dp Android frame). Text and vector shapes can be edited after import. Some compound illustrations arrive as grouped paths/shapes; they can be ungrouped as needed.

## Recommended page structure

1. `00 — Cover and Project Overview` → `boards/00-cover-project-overview.svg`
2. `01 — Foundations` → `boards/01-foundations.svg`
3. `02 — Components` → `boards/02-components.svg` and files in `components/`
4. `03 — Navigation and User Flows` → `boards/03-navigation-user-flows.svg`
5. `04 — Onboarding and Authentication` → screen files `splash.svg`, `onboarding.svg`, `sign-in.svg`, `create-account.svg`, `forgot-password.svg`, `reset-confirmation.svg`, `auth-loading.svg`, `auth-error.svg`
6. `05 — Home and Discovery` → `home-*.svg`
7. `06 — Search and Filters` → `explore-*.svg`, `location-selection.svg`, `search-*.svg`, `filter-*.svg`, `sort-sheet.svg`, `price-range.svg`, `property-type.svg`, `bed-bath.svg`, `date-picker.svg`, `guest-selector.svg`
8. `07 — Property Details and Gallery` → `property-detail-*.svg`, `property-gallery.svg`, `property-description-expanded.svg`, `detail-*.svg`
9. `08 — Saved Properties` → `saved-*.svg`
10. `09 — Requests` → `stay-request-*.svg`, `rent-*.svg`, `buy-*.svg`, `request-*.svg`, `requests-*.svg`, `cancel-request-confirm.svg`
11. `10 — Profile and Settings` → `profile-*.svg`
12. `11 — Loading, Error, Empty and Offline States` → relevant `*-loading.svg`, `*-error.svg`, `*-empty.svg`, `offline-state.svg`, `empty-state-library.svg`
13. `12 — Interactive Prototype` → use `prototype/index.html` as the interaction reference while manually wiring the imported Figma screens
14. `13 — Developer Handoff` → `boards/13-developer-handoff.svg` and documentation files

## Import steps

1. Unzip the package. Open Figma and create a blank Design file.
2. Create the 14 pages above.
3. Drag one SVG file onto its matching page, or use **File → Place image** where available. Each SVG is a standalone source frame.
4. Keep the original 393 × 852 sizing. For board SVGs, place them on a board page and scale only if necessary.
5. To organize layers, select the imported screen group and name the root frame with the corresponding filename. SVG `id` values provide meaningful names for many important groups and controls.
6. Convert recurring shapes into Figma components and variants; define variables/styles from `design-tokens.json`; apply Auto Layout to repeated component internals. SVG alone cannot encode Figma-native component properties/Auto Layout.
7. Add prototype connections according to `NAVIGATION_AND_STATES.md`. Use the HTML prototype for expected interaction behaviour, not as imported Figma content.
8. Replace the temporary text-only PLAVIO label with the official logo file when available. Replace architectural illustration groups with cleared, licensed photography.

## Important limitations

- No native `.fig` file or Figma URL was created.
- SVG-to-Figma import produces editable vector/text layers but does not guarantee a clean native component tree. Review grouping after import.
- Auto Layout, component variants, Variables and the clickable Figma prototype need a final Figma-native pass.
- The HTML browser prototype is functional for a selected walkthrough but does not integrate with a backend.
