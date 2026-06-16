# Search Team Cypress — Test Gap Coverage Report

**Date:** 2026-06-16
**Scope:** Patient Web App Cypress E2E tests (638 test cases across 77 files) owned by `@Zocdoc/search`
**Source:** `webapps/patient-web-app/cypress/e2e/{search, guided-search, searchai}` in [Zocdoc/frontend-monorepo](https://github.com/Zocdoc/frontend-monorepo) — derived from `search-team-cypress-test-mapping.md`

---

## Executive Summary

| Metric | Cypress E2E |
|--------|-------------|
| Total test files analyzed | 77 |
| Total test cases analyzed | 638 |
| Relevant | **~585 (91.7%)** |
| Irrelevant / Stale / Redundant | ~41 (+12 intentional cross-viewport duplicates, see MH OON note) |
| High-priority missing gaps | 82 |
| Medium-priority missing gaps | 135 |
| Low-priority missing gaps | 65 |

**Top cross-cutting themes** (detailed in [High-Priority Gaps Summary](#high-priority-gaps-summary)):

1. **Guided-search triage verticals are missing two near-universal cases** — "quit → reload → triage stays hidden" (session persistence) and "does not call search when triggered from search page" are present for some verticals (MH, ObGyn) but absent for CT, dental, derm, eye, mammogram, MRI, ultrasound, and xray.
2. **Control / experiment-OFF coverage is inconsistent** — many feature files test only the ON state (guided-search entry, brands triage, MH triage, provider NER, provider qualities, next-availability, legal banners).
3. **Single-viewport coverage** — a large share of files run only desktop *or* only mobile, leaving the other viewport unverified for the same behavior.
4. **searchai (AI search) has the thinnest coverage relative to risk** — crisis/safety detection has a single test, error states assert only "container visible," and several tests use conditional assertions that can pass without exercising the feature.

---

## search/ — Test Analysis

### enhanced-availability-filter-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | should persist applied date+time filter after reload | Filter values survive page reload / are reflected on revisit (out-of-scope "Individual date persistence") | **High** |
| 2 | should apply multiple dates combined with a time range | Multiple date + time combination (explicit out-of-scope in test 3) | Medium |
| 3 | should support partial clearing of date or time only | Clearing one filter dimension while retaining the other (out-of-scope "Partial clearing") | Medium |
| 4 | should handle transition when experiment toggles ON after a session began on OFF | State transition between control and enhanced filter (out-of-scope "Transition between states") | Low |

### guided-search-tests.ts (1 test)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | shows Guided Search container | **Weak assertion** — only asserts container visible and no 500 error; no verification of guided-search content, interactions, or the experiment-OFF control. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | does not show Guided Search container when experiment is OFF | Control/OFF state of the guided search experiment | **High** |
| 2 | guided search drives a real search/navigation | Interacting with guided search inputs produces correct results/URL | **High** |
| 3 | guided search records AB assignment | Experiment assignment tracking on page view | Medium |

### networkbar-insurance-change-tests.ts (3 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | changes insurance via NetworkBar on desktop | Desktop insurance picker flow (explicit out-of-scope across all 3 tests — desktop NetworkBar entirely uncovered) | **High** |
| 2 | self-pay selection combined with active filters | Self-pay with other filters applied (out-of-scope in test 2) | Medium |
| 3 | carrier switch combined with plan reselection | Carrier switching path (out-of-scope in test 3) | Medium |
| 4 | NetworkBar reflects no-insurance / out-of-network state correctly | Negative state when no in-network insurance set | Low |

### patient-choice-badge-tests.ts (6 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 6 | should not record patient choice badge experiment for iphone-6 | **Redundant** — duplicates test 5's non-assignment logic with only a viewport change; assignment tracking is viewport-agnostic. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | badge does not appear for non-qualifying providers when experiment ON | Badge only renders for providers that earned it (negative case within ON state) | **High** |
| 2 | badge text/tooltip content and accessibility | Badge label copy, aria attributes, tooltip/explainer behavior | Medium |
| 3 | badge click attribution/metrics on navigation | Correct metric/attribution emitted when badge is clicked | Medium |

### search-availability-modal-tests.js (2 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | booking attribution on mobile (iphone-6) | Both tests are desktop-only (macbook-15); mobile timesgrid/quick-link attribution uncovered | **High** |
| 2 | repeat-patient attribution (repeatPatient=true) | Attribution when patient is returning (only false is tested) | Medium |
| 3 | quick-link availability when no timeslots available | Empty/edge availability state in modal | Low |

### search-availability-selection-tests.ts (8 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | time of day selection actually filters results | Test 5 only checks facet text "Time of day"; actual time-of-day selection behavior is out-of-scope and untested | **High** |
| 2 | availability selection persistence across sessions | Selected Date/Timeframe persists across navigation/reload (out-of-scope in test 4) | Medium |
| 3 | custom date navigation / multi-month date selection | Selecting future custom dates and multi-month ranges (out-of-scope in tests 3 and 6) | Medium |
| 4 | default availability behavior on desktop (macbook) | Default-state tests 1–6 are mobile-only; desktop default rendering uncovered | Low |

### search-branding-color-tests.ts (2 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | branding colors for additional whitelabels | Test 2 only covers iuhealth; other whitelabels' brand colors uncovered (explicit out-of-scope) | Medium |
| 2 | branding color on mobile viewport | Both tests appear desktop/default; mobile timeslot branding uncovered | Low |
| 3 | brand color applied to other UI elements (buttons/headers) | Branding beyond timeslot background only | Low |

### search-common-triage-tests.ts (3 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | v2 metrics on triage load for iphone-6 | Test 3 covers v2 load metrics only on macbook-13; mobile v2 load uncovered | Medium |
| 2 | continue/forward button metrics | Only back-button metrics covered; forward navigation metric emission untested | Medium |
| 3 | v2 metrics for non-derm triages | v2 metrics only validated for dermatologist triage (explicit out-of-scope) | Low |

### search-constraint-modals-tests.ts (2 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | constraint modal IS shown when behavior is not hide_all | Positive case — modal appears under non-default constraint behavior (only hide_all is tested) | **High** |
| 2 | constraint modal behavior on desktop (macbook) | Both tests are iphone-6 only; desktop constraint behavior uncovered | Medium |
| 3 | constraint modal on timeslot/availability click | Constraint handling when clicking a timeslot rather than profile/insurance | Medium |

### search-covid-testing-tests.js (2 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | should display proper special covid testing logic on covid search on macbook-15 | **Possibly stale** — COVID-testing search is a pandemic-era special case; confirm procedure 5028 and its special layout are still live product surfaces before maintaining. |
| 2 | should display proper special covid testing logic on covid search on iphone-6 | **Possibly stale** — same COVID-era legacy concern; mobile variant of a possibly retired feature. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | standard (non-COVID) search still shows split in/out-of-network sections | Positive control confirming the COVID layout difference is COVID-specific (regression guard) | Medium |
| 2 | COVID search booking/availability flow | Whether booking works in the COVID layout, not just section rendering | Low |

### search-crosslisting-pa-modal-tests.ts (12 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | does not show modal for searchtype=specialty for iphone-6 | **Overlapping** — heavily overlaps test 3 (no modal on specialty search, hide_all, iphone-6); the constraint-vs-crosslisting distinction is thin. |
| 2 | does not show modal for searchtype procedure for iphone-6 | **Overlapping** — heavily overlaps test 4 (no modal on procedure search, hide_all, iphone-6). |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | crosslisting modal IS shown when not hide_all | Positive case — modal renders under non-hide_all config (all tests assert absence) | **High** |
| 2 | diarrhea triage variant A/B with experiment OFF | Modal behavior when SEARCH_DIARRHEA_TRIAGE is off (only ON variants tested) | Medium |
| 3 | crosslisting modal navigation target correctness on mobile | Verify destination/params on mobile timeslot path (desktop checks SPO; mobile does not) | Medium |

### search-ct-triage-tests.ts (11 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | CT triage on specialty search | Tests cover procedure search only; specialty-search trigger behavior uncovered (explicit out-of-scope) | **High** |
| 2 | CT triage back-navigation / abandon flow | Quitting or navigating back mid-triage and resulting state | Medium |
| 3 | CT contrast paths on desktop (macbook) | Contrast yes/no/both paths (tests 3–5) are iphone-6 only; desktop uncovered | Medium |
| 4 | CT triage with zero provider results | Triage behavior when no CT providers available | Low |

### search-default-placemark-tests.ts (4 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | default placemark when geolocation is denied/unavailable | Negative case — fallback location when geolocation permission denied | **High** |
| 2 | manual location entry overrides placemark | Manual entry path (explicit out-of-scope across tests) | Medium |
| 3 | placemark behavior from other entry points | Entry points beyond Home and SEM | Low |

### search-dental-triage-tests.ts (12 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | dental triage paths on mobile (iphone-6) | Tests use macbook-15; mobile rendering/selection of dental triage uncovered | **High** |
| 2 | back-navigation within dental triage screens | Navigating backward through care-type/problem screens and preserving state | Medium |
| 3 | dental triage AB assignment recorded on trigger | Experiment assignment tracking on triage display | Medium |

### search-derm-triage-tests.ts (16 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 16+ | Additional specialty matching, skin problem, and cosmetic procedures flows | **Underspecified** — catch-all bundle ("[Multiple variations]") with no concrete names/assertions; should be enumerated into discrete tests rather than maintained as an opaque row. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | derm triage paths on mobile (iphone-6) | Nearly all derm tests are macbook-15; mobile derm triage flows uncovered | **High** |
| 2 | derm triage on procedure search | Trigger covers specialty search; procedure-search trigger out-of-scope and untested | Medium |
| 3 | specialty matching boundary: count just above threshold | Edge case at the provider-count threshold that toggles specialty matching | Low |

### search-diarrhea-triage-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | diarrhea triage variant B specialty selections enumerated | Test 5 bundles all variant B specialty selections into one opaque row; should be discrete per-specialty assertions like variant A | Medium |
| 2 | diarrhea triage paths on desktop (macbook) | All tests are iphone-6; desktop diarrhea triage uncovered | Medium |
| 3 | provider count exactly at threshold boundary | Behavior at count = 1 vs 0 boundary | Low |

### search-displayonpagerank-tests.js (1 test)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | rank ordering verified beyond first provider | Test only asserts the first provider's position; verify full-list ordering matches displayOnPageRank | Medium |
| 2 | display rank ordering on mobile (iphone-6) | Test is macbook-15 only; mobile card ordering uncovered | Medium |
| 3 | rank ordering after applying filters | Ordering stability when filters change the result set | Low |

### search-entrypoints.ts (not a test file)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| — | [EntryPoints type definitions and enum] | **Not a test** — file contains only type definitions, no test cases; should not be counted as test coverage. |

**Missing Tests:** None — type-definition file; no behavioral coverage applicable.

### search-eye-triage-tests.ts (16 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | eye triage paths on desktop (macbook) | All 16 tests are iphone-6 only; desktop eye triage rendering/selection uncovered | **High** |
| 2 | eye triage experiment OFF control | No explicit experiment-OFF / non-trigger control test; confirm OFF-state behavior | Medium |
| 3 | eye triage skip persistence cleared on new search | Whether skipped triage reappears on a genuinely new eligible search vs reload | Low |

### search-facet-filter-tests.ts (11 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | facet filters on desktop (macbook) viewport | Tests are mobile/iphone-6 focused; desktop facet dropdown behavior uncovered | **High** |
| 2 | insurance picker v4 / desktop insurance flow | Tests 10–11 cover v5 mobile only; v4 and desktop insurance flows explicit out-of-scope | Medium |
| 3 | combining distance + specialty + availability filters and clearing all | Multi-filter-type combination and bulk clear (each test isolates one filter type) | Medium |
| 4 | procedure filter change preserves other applied filters | Filter interaction/persistence when changing procedure | Low |

### search-insurance-correction-tests.ts (15 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | should record assignment for off variant when user is eligible to see the banner | **Weak/low-value** — only asserts assignment recording for OFF; near-identical to #1, no behavioral assertion (banner display out of scope). |
| 13 | …member id got corrected (member id difference is not discernible) | **Overlapping** — assertions identical to #12 ("both IDs visible → Click correction"); discernible vs non-discernible distinction is not actually verified differently. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | banner not shown for ineligible insurance with ON variant | Ineligible users (repeatedly out-of-scope across #1–#3) never see the banner — core gating/zero-coverage gap | **High** |
| 2 | banner not shown when experiment is OFF | OFF variant suppresses banner rendering (only assignment tested for OFF in #2) | **High** |
| 3 | localStorage completion flag persists across reload / suppresses banner on return | Verify the completion flag actually dismisses the banner after reload | Medium |
| 4 | eligibility check from banner with self-pay / no insurance selected | Edge case where user has no eligible plan after opening banner | Low |

### search-insurance-picker-v5-tests.ts (23 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 4 | records assignment when … timestone availability modal - off | **Weak** — OFF-variant assignment-only check; mirrors #3 with no behavioral difference asserted. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | v5 picker rendered/operable on desktop (macbook-13) for scan, skip, self-pay | Tests #17, #18, #21, #22 are mobile-only; scan/skip flows have no desktop coverage | **High** |
| 2 | custom carrier/plan search via autocomplete (typed query) | #5 covers only popular-list selection; typed/custom autocomplete search is out of scope | **High** |
| 3 | OON modal in-network (non-OON) provider path | #15 covers OON detection only; in-network counterpart out of scope | Medium |
| 4 | medical (non-dental) insurance preservation across PPS switches | #8 covers dental only; medical persistence out of scope | Medium |
| 5 | forward navigation persistence in availability modal | #6/#16 cover back navigation; forward-only flows out of scope | Low |

### search-insurance-plan-merges-tests.ts (2 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | partially deprecated plan handling | #1 covers fully deprecated only; partially deprecated explicitly out of scope | **High** |
| 2 | user-initiated plan change is not auto-overridden by merge logic | #2 covers auto-correction; user-initiated changes out of scope | Medium |
| 3 | merged plan persists in cookies across reload/search | Verify corrected plan sticks beyond the single visit | Low |

### search-legal-banners-tests.ts (2 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | banners do NOT display when flag OFF / in non-applicable states | No control/OFF-variant or wrong-state suppression coverage for either banner | **High** |
| 2 | banner click/analytics tracking fires | Click + analytics explicitly out of scope for both banners | Medium |
| 3 | banner not shown for unrelated procedure/state combos | Negative case: banners gated to correct procedure_id + state | Medium |

### search-location-tests.js (2 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | geolocation denied / permission-blocked handling | #1 only mocks granted geolocation; denied/error path is a user-facing gap | **High** |
| 2 | address cookie fallback when no query param | #2 explicitly leaves cookie fallback out of scope | Medium |
| 3 | mobile viewport for current-location and location-picker | This file has no viewport parameterization; mobile location flows untested | Medium |
| 4 | invalid/unrecognized address query param | Negative case for malformed address param | Low |

### search-mammogram-triage-tests.ts (27 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 21 | without a referral, get a referral (under 40) | **Misleading name** — duplicate name with #9; only the age branch differs, name gives no disambiguation. |
| 22 | without a referral, browse imaging facilities (under 40) | **Misleading name** — duplicate of #10's name; under-40 vs 40+ branch indistinguishable from title. |
| 23 | getting their first mammogram (under 40) | **Misleading name** — duplicate of #15's name; relies solely on row context to disambiguate age branch. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | desktop viewport coverage for triage decision tree | No viewport parameterization; the entire 27-case tree appears mobile-implicit, desktop unverified | **High** |
| 2 | radio-button metrics firing | #5 covers checkbox metrics; radio metrics explicitly out of scope | Medium |
| 3 | back/exit mid-triage does not re-show on reload | No session-persistence/exit coverage as exists for MH triage | Medium |
| 4 | invalid/unsupported mammogram procedure or specialty id | Negative gating case beyond the two valid trigger ids | Low |

### search-map-controls-tests.ts (5 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | actual zoom/pan layout behavior (not just metrics) | All 5 tests assert metrics only; functional map behavior explicitly out of scope | **High** |
| 2 | marker click with empty/no search results | Negative case for provider card on marker with zero results | Medium |
| 3 | expand/collapse layout state change verification | #2 verifies metrics only; actual layout change out of scope | Low |

### search-map-custom-popover-tests.js (5 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | desktop popover Book / View-profile metrics | #1–#3 viewport unspecified; #4–#5 mobile-only — desktop popover interactions unverified | **High** |
| 2 | swipe through single-provider marker (no carousel) | #5 covers multi-provider; single-provider edge out of scope | Medium |
| 3 | popover dismissal / close behavior | No coverage for closing the popover after open | Low |

### search-mental-health-oon-desktop-tests.js (6 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| all 6 | testSearchPageMoon cases | **Intentional cross-viewport duplication** — these are the same `testSearchPageMoon` cases run in the mobile file and defined in `search-mental-health-oon.js`. Not removable, but the desktop/mobile split triples the same 6 assertions; noting for awareness rather than deletion. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | insurance success modal re-show on plan change (not just carrier) | #3 covers carrier change to "choose later"; plan changes explicitly out of scope | Medium |
| 2 | triage re-trigger after forward navigation | #4/#6 cover back-button only; forward navigation out of scope | Medium |
| 3 | triage re-trigger after other updates (filter/insurance change) | #5 covers location update only; other update types out of scope | Low |

### search-mental-health-oon-mobile-tests.js (6 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| all 6 | testSearchPageMoon cases | **Intentional cross-viewport duplication** — identical cases to the desktop file via `testSearchPageMoon`; only the viewport differs. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | mobile-specific modal layout / full-screen rendering | Mobile file only re-runs desktop logic; no mobile-unique layout assertion (e.g., full-screen modal) | Medium |
| 2 | plan-change re-show on mobile | Same plan-vs-carrier gap as desktop, on mobile viewport | Low |

### search-mental-health-oon.js (6 tests — shared factory)

**Irrelevant / Stale Tests:** None — shared test factory consumed by the desktop/mobile files.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | viewport-agnostic guard assertions | Factory is consumed by desktop+mobile; no standalone gap beyond what callers cover | Low |

### search-mezz-header-tests.ts (4 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | mobile menu v1 (gro_mobile_web_improve_navigation OFF / control) | #3 covers v2 ON; v1/control menu explicitly out of scope | **High** |
| 2 | successful login completion (post-modal) | All tests stop at "modal visible"; no successful auth flow verified | Medium |
| 3 | desktop map toggle equivalent | #4 covers mobile map toggle only; desktop has no map-toggle coverage | Low |

### search-mh-triage-tests.ts (20 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 15 | should complete triage flow … with selecting same option again | **Overlapping** — largely re-runs #6's completion flow with an idempotent re-select; the completion + metric assertion duplicates #6. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | guided search experiment OFF / control behavior | Multiple tests assume "guided search experiment is on"; no OFF/control coverage | **High** |
| 2 | SSR-triggered insurance search (server-side triage) | #12 explicitly leaves SSR scenarios out of scope | Medium |
| 3 | individual therapy full path completion | #2 covers group; #3 covers individual only partially (back-nav) | Medium |
| 4 | v4 picker in triage (insurance picker v5 OFF) | #20 covers v5 only; v4 in triage out of scope | Low |

### search-miscellaneous-specialties-triage-tests.ts (4 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | each misc specialty actually triggers triage when ON | #2/#3 cover suppression; no positive per-category ON-trigger assertion despite parameterization | **High** |
| 2 | self-pay / skip-insurance path through misc triage | No insurance-skip coverage as exists in MH triage | Medium |
| 3 | back navigation / mid-triage exit for misc specialties | Only reload persistence (#1) tested; mid-triage back not covered | Low |

### search-mobile-header-tests.js (12 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 11 | insurance picker full screen … when insurancepickerv4=ON | **Stale/redundant** — v4 variant of #1; with v5 the current picker, the v4-on-map case is likely legacy duplication of #1's full-screen assertion. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | insurance picker v5 full-screen on mobile map | #1/#11 cover v2/v4; current v5 picker on mobile map untested here | **High** |
| 2 | PPS picker from header (specialty) | #4 explicitly leaves PPS picker out of scope | Medium |
| 3 | more-filters apply (non-clear) reflects in URL | #8 covers clear; applying a filter selection not verified | Medium |
| 4 | desktop equivalents of header interactions | Entire file is iphone-6+; no desktop header coverage | Low |

### search-mobile-map-refresh-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | desktop map/list refresh behavior | Entire file is mobile; no desktop coverage of refresh experiment | Medium |
| 2 | swipe on single-provider marker (no carousel) | #7 covers multi-provider swipe; single-provider edge out of scope | Low |
| 3 | toggle persistence across search refresh | Verify map/list view choice survives a results refresh | Low |

### search-mri-triage-tests.ts (9 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | MRI specialty-based trigger (not just procedure) | #1 covers procedure trigger; specialty-based explicitly out of scope | **High** |
| 2 | back navigation / mid-triage exit and reload persistence | No session/exit persistence coverage as exists for MH | Medium |
| 3 | referral=No with no issue category selected then search directly | Edge path through the No-referral branch without category | Low |

### search-next-availability-tests.ts (7 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | should record assignment for variant off | **Thin assignment-only check** — verifies off-variant assignment is recorded but does not confirm the modal/button is suppressed in control; overlaps heavily with #1. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | off-variant suppresses next-availability button/modal | That the control variant actually hides the entry point or falls back to legacy — only assignment is checked today | **High** |
| 2 | booking from availability modal timeslot | Clicking a timeslot navigates to /booking/start with correct params (out of scope in #4) | **High** |
| 3 | OON modal handling within insurance selection in modal | The out-of-network modal interaction is out of scope in #6 but is a real branch | Medium |
| 4 | modal on mobile viewport | All 7 tests appear desktop-implicit; verify modal date range, timeslots, close on iphone-6 | Medium |
| 5 | provider with no upcoming availability | Negative case where the 2-week window has zero timeslots — empty-state rendering | Low |

### search-obgyn-triage-tests.ts (45 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 32 | clicking a procedure goes to specialty matching guided search | **Duplicate name + flow** — identical name to #29 and overlaps the "something else" → specialty-matching assertion already covered by #29/#38. |
| 35 | clicking a procedure goes to specialty matching guided search | **Misleading/duplicated name** — third reuse of the same name; SomethingElse→Menopause→SpecialtyProviders largely duplicates #29/#38. |
| 30 | should not record experiment … specialty matching for low supply | **Redundant low-supply variant** — same 16==16 skip assertion as #33/#39 with a different entry procedure. |
| 39 | should not record experiment … full visit reason list … low supply | **Overlapping low-supply assertion** — near-identical to #30 and #33; the trio collapses to one parameterized case. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | experiment OFF for pregnancy/sexual-health/something-else flows | OFF-variant assignment only tested for AnnualExam (#43/#45); major OB-GYN flows lack control-state coverage | **High** |
| 2 | skip persistence across sessions | #14 explicitly scopes out cross-session persistence | Medium |
| 3 | OB-GYN triage on mobile viewport | All cases appear desktop; verify treatment-type, pregnancy, specialty-matching screens on iphone-6 | Medium |
| 4 | back navigation from specialty-matching view | Back tested for sexual-health/something-else lists but not from the specialty-matching screen | Medium |
| 5 | abortion/excluded treatment with experiment ON + highlighted IDs combined | Untested combination of exclusion rules layered together | Low |

### search-originator-tests.ts (11 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | search-bar re-search on results page sets correct originator | A new PPS search from /search (not homepage) attributes the right originator — a common uncovered path | **High** |
| 2 | "Find a provider" originator with quicklinks flag OFF | Control state for #5 — originator falls back correctly when search_ai_search_quicklinks is off | Medium |
| 3 | originator on mobile viewport | All originator checks appear desktop; quick links/search bar layout differs on mobile | Medium |
| 4 | originator preserved/reset through pagination after a filter | Combination of Filter then Pagination originator transitions | Low |

### search-ortho-triage-tests.js (5 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | specialty-matching flow (SpecialtyProviders / AllProviders) for ortho | ObGyn/PCP triage files have extensive specialty-matching + low-supply + assignment coverage; ortho has none despite the same experiment | **High** |
| 2 | experiment ON/OFF assignment recording for ortho | No control-state or assignment-recording test exists for ortho, unlike pcp/obgyn | **High** |
| 3 | skip persistence across page reload | obgyn/pcp explicitly test skip-then-reload; ortho only tests same-procedure re-trigger | Medium |
| 4 | ortho triage on mobile viewport | All ortho cases appear desktop-implicit | Medium |
| 5 | other treatment-type selections beyond Neck | #3/#4 only exercise the Neck branch (5838); other body-region options untested | Low |

### search-parent-request-id-tests.ts (3 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | distance/other non-procedure filters inherit parent ID | #3 notes distance filter inherits but is scoped out; verify each filter type's inherit-vs-reset behavior | Medium |
| 2 | browser back/forward preserves parentSearchRequestId | Navigation history interaction with parent ID propagation | Medium |
| 3 | new top-level search bar query resets parent ID | A fresh search should also reset — confirm parity with PPS reset (#2) | Low |

### search-pcp-triage-tests.ts (24 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 9 | does not show specialty matching screen if specialty count equals general care count | **Overlapping threshold case** — equal-count (30==30) skip is subsumed by parameterized edge cases in #15 (0,1)/(1,0)/(0,0). |
| 14 | does not show specialty matching screen if provider count is low | **Duplicate of #8** — same low-count (15,112) skip assertion, differing only in visit reason vs AnnualPhysical. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | PCP triage on mobile viewport | All 24 cases appear desktop; verify treatment-type, specialty-matching, Sam DAG long-list screens on iphone-6 | **High** |
| 2 | back navigation with Sam DAG backend triage | Back/reset tested for frontend triage (#17); the Search_Use_Sam_Dag backend path (#22–24) has no back-navigation coverage | Medium |
| 3 | skip persistence across sessions | #1 scopes out session storage | Medium |
| 4 | Sam DAG experiment OFF / fallback to frontend triage | #22–24 only test Sam DAG ON; no control comparing backend vs frontend | Medium |
| 5 | highlightedProfileIds bypass with experiment ON + specialty matching | Untested combination of bypass layered with specialty-matching | Low |

### search-picker-tests.js (13 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 7 | can clear insurance selection and search without insurance - iphone | **Overlaps #11** — clearing on mobile is also covered by #11 (default=false when clear); near-identical clear-on-mobile flow. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | scan OCR failure / unreadable card | #6 scopes out OCR accuracy; verify error/retry UX when the scanned card cannot be parsed | **High** |
| 2 | search with no insurance carriers / empty carrier list | Negative/empty-state rendering of the picker when carrier data is missing | Medium |
| 3 | desktop default-insurance-plan flag behavior | Default-plan flag (#9–#12) only tested on iphone-6; verify on macbook-15 | Medium |
| 4 | invalid preset insurance param in URL | Graceful handling when the URL carries a malformed/unknown carrier or plan ID | Medium |
| 5 | scan on desktop / camera unavailable | Scan flow is mobile-only; verify behavior or hiding of scan icon on desktop | Low |

### search-polaris-tests.ts (1 test)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | renders doctor card on desktop | Only mobile rendering covered; verify polaris doctor card + photo on macbook viewport | **High** |
| 2 | doctor card missing photo fallback | Negative case — placeholder/initials rendering when polaris-doctor-photo is absent | Medium |
| 3 | doctor card key fields render | Verify name, specialty, rating, CTA elements render, not just photo presence | Medium |

### search-previously-booked-tests.ts (8 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | desktop previously-booked banner rendering | Only #4 covers mobile; verify banner with date on macbook viewport | Medium |
| 2 | multiple previously-booked providers | Verify banner behavior when several providers in the param match results | Medium |
| 3 | previously-booked profile not in current results | Negative case — param references a provider absent from results (no banner, no crash) | Medium |
| 4 | future-dated or malformed date value | Date-formatting edge case beyond the valid path | Low |

### search-provider-ner-tests.ts (1 test)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | provider NER experiment OFF / control | No control-state test — verify highlighting and highlightedProfileIds absent when sam_provider_ner is off | **High** |
| 2 | NER query with no matching providers | Negative case — typed name matches nothing; verify no highlighted section and graceful results | Medium |
| 3 | provider NER on mobile viewport | Single test appears desktop; verify highlighted section renders on iphone-6 | Medium |

### search-provider-qualities-tests.js (1 test)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | provider quality flag OFF (review shown) | Inverse control — when quality badge is off, the review rating should display; only ON state is checked | **High** |
| 2 | provider with no quality data | Negative case — card renders without badge and without breaking layout | Medium |
| 3 | quality badge on mobile viewport | Single test appears desktop | Low |

### search-scoped-filters-tests.ts (5 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | scoped filters on desktop viewport | #1–#4 are iphone-6 only; verify in-person/video facet apply/clear on macbook-15 | Medium |
| 2 | combined facets (visit type + another scoped filter) | Interaction/persistence when more than one scoped filter is applied together | Medium |
| 3 | facet persistence through pagination | Verify visitType filter survives page navigation | Medium |
| 4 | "all" visit type explicitly clears filter from MH triage | MH triage covers in-person/video but not the no-filter/all path | Low |

### search-spo-click-attribution-tests.ts (14 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | records assignment when the flag is on and SPO results are present | **Subsumed by #5** — single-viewport ON case duplicated by parameterized #5 covering both viewports for the same availability-button attribution. |
| 3 | records assignment when flag is OFF and SPO results present but no api call | **Subsumed by #6** — single-viewport OFF case duplicated by parameterized #6 ([iphone-6, macbook-13]). |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | out-of-network insurance SPO attribution | In-network reinforcement is covered (#11–#13); the OON branch attribution is untested | **High** |
| 2 | attribution API failure (non-200) handling | All API checks assert 200; verify assignment/UX when the call errors or times out | Medium |
| 3 | doctor-card click (not just availability/timeslot/insurance) attribution | Card-level click attribution path coverage | Medium |
| 4 | next-availability OFF variant attribution | #14 only covers ON for next availability; no OFF control | Low |

### search-tests.js (13 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | automatically executes a search when selecting a location autocomplete prediction via mouse | **Overlaps #2** — same autocomplete-triggers-search behavior as #2 (mouse vs keyboard); #6 also re-exercises autocomplete click. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | empty/zero-results search state | Negative case — search returning no providers renders an empty state, not covered anywhere | **High** |
| 2 | invalid/unrecognized location input | Typing a non-resolvable location and verifying graceful handling | Medium |
| 3 | SSR rendering on mobile viewport | #1 SSR check appears desktop; verify SSR content on iphone-6 | Medium |
| 4 | doctor-card click on mobile opens profile | #11 (new-tab open) appears desktop; verify mobile navigation behavior | Medium |
| 5 | forward button after back restores pagination | #7 covers back; verify forward navigation symmetry | Low |

### search-timesgrid-tests.js (8 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | rolled-up availability ON behavior | #1 explicitly sets rolled-up availability OFF; the ON variant timesgrid rendering is untested | **High** |
| 2 | left arrow / backward navigation in timesgrid | Only the right arrow (#1) is tested; left-arrow navigation and its boundary at the current date are uncovered | Medium |
| 3 | provider with no availability in timesgrid | Empty/no-slots state rendering | Medium |
| 4 | timesgrid navigation on mobile | #1/#2 navigation tests are macbook-13; verify arrow/scroll behavior on iphone-6 | Medium |
| 5 | constraint modal cancel/dismiss path | #3 opens constraint modal but the dismiss-without-booking branch is untested | Low |

### search-top-practice-tag-tests.ts (4 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | top-practices tag on desktop viewport | All 4 tests are iphone-6 only; verify tag display + V2 metrics on macbook | **High** |
| 2 | banner click navigation destination | #4 acknowledges a race condition and scopes out post-click navigation; verify where the click routes | Medium |
| 3 | tag absent when zero organic results | Negative case — no SPO and no qualifying organic practices | Low |

### search-type-tests.ts (11 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 7 | when searching for procedure in search bar, search type is procedure [search page] | **Cross-surface duplication** — #1/#4/#7 assert identical procedure-identification logic across home/marketing/search surfaces. |
| 8 | when searching for specialty in search bar, search type is specialty [search page] | **Cross-surface duplication** — mirrors #2/#5 for specialty identification across surfaces; same logic repeated three times. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | search type on mobile viewport | All 11 cases appear desktop; verify procedure/specialty type detection on iphone-6 | Medium |
| 2 | searchType set via insurance/other filter (not just procedure filter) | #9 covers procedure filter; verify type behavior for other filter-driven changes | Medium |
| 3 | pagination preserves type for filter-initiated procedure searches | Combination of filter-driven type (#9) then pagination | Low |

### search-ultrasound-triage-tests.ts (5 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | referral order "Yes" path for ultrasound | The xray file tests the "Yes to referral" branch; ultrasound only tests "No" — missing parallel coverage | **High** |
| 2 | ultrasound triage on desktop for trigger/something-else cases | #2/#3/#4 appear single-viewport; only #5 parameterizes — verify trigger and something-else on macbook-15 | Medium |
| 3 | specialty-matching / assignment-ON-vs-OFF beyond #1 | #1 covers experiment-OFF skip; no specialty-matching or richer ON-variant assignment coverage | Medium |
| 4 | referral education back navigation | #3 enters referral education; verify back/reset from that screen | Low |

### search-xray-triage-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | xray triage on desktop for OFF / trigger cases | #1–#5 are iphone-6 only; only #6/#7 parameterize — verify OFF-skip and trigger on macbook-15 | Medium |
| 2 | back navigation between issue categories | #6 navigates across categories via back; verify state resets correctly mid-flow | Medium |
| 3 | specialty-matching / assignment-recording for xray | Like ultrasound, no specialty-matching coverage that obgyn/pcp triages have | Medium |
| 4 | referral education "No" then back to referral order | Negative/back path within the referral flow | Low |

---

## guided-search/ — Test Analysis

### guided-search-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | should not trigger triage when guided search experiment is off | Control/OFF variant of guided-search trigger (every vertical has an "off" test except this entry file) | **High** |
| 2 | tablet viewport (ipad) behavior | Viewport coverage gap — only iphone-6 and macbook-13 covered; tablet breakpoints untested | Medium |
| 3 | preserve triage skip state across browser back/forward | Session/skip persistence under native back-button, not just re-visit | Medium |
| 4 | triage state API returns malformed/empty payload | Negative case beyond the 500 error already covered | Low |

### search_brands_triage.tests.ts (4 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | should show old triage on brand search when variant is off | Control/OFF variant — every other vertical (CT, dental, derm, eye, mammogram, MRI, ultrasound, xray) has an explicit "variant off" test; brand triage lacks one | **High** |
| 2 | should not show brand triage for procedure search without brandId | Negative/trigger-exclusion case — only specialty trigger is covered | Medium |
| 3 | brand triage with abort/quit out of questionnaire | Quit/exit flow (out of scope on test #2) | Medium |
| 4 | brand triage experiment assignment logged once | Experiment assignment dedup, as covered in obgyn | Low |

### search-ct-triage-tests.ts (9 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session persistence after skip/quit — covered in MH and ObGyn but absent for CT | **High** |
| 2 | should not call search when triggered from search page | Triage prevents premature search call — covered for MH, missing for CT | **High** |
| 3 | issue category SomethingElse fallback to full procedure longlist | Negative/fallback for issue-driven flow when no category matches | Medium |
| 4 | referral flow with no contrast option available | Boundary case where contrast options are absent | Low |

### search-dental-triage-tests.ts (8 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — present for MH/ObGyn, missing for dental | **High** |
| 2 | should not call search when triggered from search page | Triage suppresses premature search — missing for dental | **High** |
| 3 | dental triage suppressed when highlightedProfileIds present | Triage suppression with highlighted profile (covered in MH/ObGyn) | Medium |
| 4 | cosmetic care SomethingElse / longlist fallback | Fallback path for cosmetic care type (only shortlist covered) | Medium |

### search-derm-triage-tests.ts (15 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — missing for derm despite many flow tests | **High** |
| 2 | should not call search when triggered from search page | Triage suppresses premature search call — missing for derm | **High** |
| 3 | derm triage suppressed when highlightedProfileIds present | Triage suppression with highlighted profile (covered MH/ObGyn) | Medium |
| 4 | back navigation between treatment-type and sub-screens preserves selection | Back-button state retention across derm sub-flows | Medium |

### search-eye-triage-tests.ts (10 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — missing for eye | **High** |
| 2 | should not call search when triggered from search page | Triage suppresses premature search call — missing for eye | **High** |
| 3 | eye exam with zero checkboxes selected then Continue | Negative/validation — no option chosen on checkbox screen | Medium |
| 4 | eye triage suppressed when highlightedProfileIds present | Triage suppression with highlighted profile | Medium |

### search-mammogram-triage-tests.ts (6 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | mammogram triage trigger on specialty search | Specialty-search trigger — only procedure-search trigger (#2) covered, unlike sibling verticals | **High** |
| 2 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — missing for mammogram | **High** |
| 3 | NotSure flow with a symptom checkbox selected | Branch of "not sure" where symptoms ARE present (only NoSymptom path covered) | Medium |
| 4 | routine screening 40+ needing ultrasound (Yes path) | Boundary — the "Yes need ultrasound" branch (only No covered) | Low |

### search-mh-triage-tests.ts (19 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 6 | should complete triage flow when guided search experiment is on | **Overlapping** — fully subsumed by #15 ("complete flow … with selecting same option again"), which exercises the same path plus the back/re-select variation; #6 adds no unique assertion. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | should show old fit questionnaire when guided search experiment is off | Control/OFF variant — MH has no "variant off" test while every other vertical does | **High** |
| 2 | insurance picker v5 self-pay then switch back to a carrier | Negative/validation on the v5 picker (only forward self-pay path in #19) | Medium |
| 3 | group therapy flow on mobile viewport | Viewport coverage — MH flows only exercised at default viewport | Low |

### search-mri-triage-tests.ts (9 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — missing for MRI | **High** |
| 2 | should not call search when triggered from search page | Triage suppresses premature search call — missing for MRI | **High** |
| 3 | issue category SomethingElse fallback to full longlist with no match | Fallback/negative within issue-driven flow | Medium |
| 4 | referral flow with no contrast option | Boundary where contrast options absent | Low |

### search-obgyn-triage-tests.ts (27 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 25 | clicking a procedure goes to the end of the flow | **Duplicate name** — shares the exact name with #23; both assert "direct procedure ends flow" (sexual_health vs something_else). Functionally distinct but the identical name is confusing and risks one masking the other in reporting. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | should not call search when triggered from search page | Triage suppresses premature search call — covered for MH, missing for ObGyn | **High** |
| 2 | ObGyn triage shown for specialty search (not just procedure) | Specialty-search trigger — only procedure-search trigger (#1) is positively asserted | Medium |
| 3 | pregnancy flow back navigation re-selecting trimester | Back/re-select state retention across the how-far-along sub-flow | Medium |
| 4 | annual exam SomethingElse longlist boundary | Fallback list completeness for the annual exam path | Low |

### search-ultrasound-triage-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — missing for ultrasound | **High** |
| 2 | should not call search when triggered from search page | Triage suppresses premature search call — missing for ultrasound | **High** |
| 3 | referral flow contrast/options variation | Ultrasound referral only asserts a single "Yes referred" URL; CT/MRI test multiple contrast options | Medium |
| 4 | issue category SomethingElse with no matching procedure | Fallback/negative within issue-driven flow | Low |

### search-xray-triage-tests.ts (7 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | can quit out of questionnaire, reload and triage stays hidden | Session/quit persistence — missing for xray | **High** |
| 2 | should not call search when triggered from search page | Triage suppresses premature search call — missing for xray | **High** |
| 3 | xray triage session ID persists across the full flow | Session-ID continuity — captured per step but never asserted stable end-to-end | Medium |
| 4 | issue category SomethingElse with no matching procedure | Fallback/negative within issue-driven flow | Low |

---

## searchai/ — Test Analysis

### searchai-crisis-detection-tests.ts (1 test)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | shows crisis/safety resource banner (e.g. 988 hotline) on crisis message | That a crisis message surfaces appropriate safety resources, not just "doesn't crash" | **High** |
| 2 | crisis detection across multiple phrasings (self-harm, overdose, abuse) | That varied crisis phrasings are all detected, not only "I feel hopeless" | **High** |
| 3 | crisis message handling on mobile (iphone-6+) | Crisis-flow safety on the mobile viewport (untested) | **High** |
| 4 | non-crisis message with crisis-adjacent words is not falsely flagged | False-positive guardrails | Medium |
| 5 | crisis message mid-conversation (multi-turn) still triggers safety handling | Crisis detection after triage context already exists | Medium |

### searchai-direct-search-tests.ts (5 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 4 | displays doctor cards with provider information (macbook-15) | **Overlapping** — duplicates searchai-results-tests #2/#4/#6 (provider card render + link on desktop). |
| 5 | displays doctor cards with provider information (iphone-6+) | **Overlapping** — duplicates searchai-results-tests #5/#7 (provider card render + link on mobile). |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DirectSearch routing returns zero results shows empty/no-results state | Empty-state UX when DirectSearch finds no providers | **High** |
| 2 | mobile chat becomes visible after triage phase ends | The explicitly out-of-scope "mobile visibility during triage" transition | Medium |
| 3 | DirectSearch vs triage routing decision honored via routing_decision param | That the routing param actually drives the DirectSearch path | Medium |
| 4 | chat sidebar visible with results on mobile | Mobile counterpart to #3 (desktop-only today) | Low |

### searchai-error-states-tests.ts (3 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | shows user-facing error message content / retry affordance on chat 500 | That the error state communicates something actionable, not just "container visible" | **High** |
| 2 | triage SSE stream error / timeout handled gracefully | Failure of the SSE triage stream (distinct from POST /chat 500) | **High** |
| 3 | error states render correctly on mobile (iphone-6+) | Error UI on mobile viewport (all 3 tests are desktop/viewport-agnostic) | Medium |
| 4 | recovery after transient error (retry succeeds, results load) | That the app recovers once the backend returns healthy | Medium |

### searchai-filters-tests.ts (5 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | applying a filter re-queries and updates results | Filter logic end-to-end (open modal is tested; apply is not) | **High** |
| 2 | desktop location/insurance/filter interactions (macbook-15) | Desktop pickers — only "header visible" is tested on desktop | **High** |
| 3 | selecting an insurance plan updates the insurance pill label | That picker selection persists back into the pill bar | Medium |
| 4 | clearing/resetting an applied filter restores prior results | Filter clear path | Medium |
| 5 | pill bar keyboard/accessibility (focus, ARIA on pills) | A11y of facet pills and modals | Low |

### searchai-homepage-entry-tests.ts (12 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 6 | navigates to search when submitting a free-text query (iphone-6+) | **Weak/overlapping** — identical assertion (URL matches /search) to #5 with same steps; mobile adds little since the flow is viewport-agnostic. |
| 8 | navigates to search when selecting an autocomplete item (iphone-6+) | **Weak/overlapping** — duplicates #7 assertion; both only assert URL matches /search. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | hero query routes to /searchai (AI path) vs /search (classic) per experiment | That routing logic is actually exercised, not just a "/search" regex match; control vs treatment | **High** |
| 2 | submitting empty / whitespace-only hero query is blocked or no-ops | Negative input validation on hero submit | Medium |
| 3 | autocomplete shows no/empty state for gibberish query | Empty autocomplete handling | Medium |
| 4 | location and insurance selections persist into the search/searchai URL params | That hero-selected facets carry into results | Medium |
| 5 | hero autocomplete keyboard navigation (arrow keys, enter) | A11y / keyboard selection of autocomplete | Low |

### searchai-insurance-confirmation-tests.ts (3 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | shows out-of-network modal for OON providers | **Weak/conditional** — asserts modal "if triggered"/"if data matches"; a conditional assertion can pass without ever exercising OON, giving false confidence. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | deterministic OON modal with mocked out-of-network provider data | Reliable OON modal trigger (replaces conditional #3) | **High** |
| 2 | changing insurance plan re-filters in-network badges | That insurance context updates provider in-network display | **High** |
| 3 | no insurance selected shows neutral state (no in-network badge) | Control/OFF state when insurance context absent | Medium |
| 4 | in-network badge / OON modal on mobile (iphone-6+) | Insurance confirmation UX on mobile viewport | Medium |
| 5 | OON modal copy and CTA (continue / pick different provider) | Modal content and actionability | Low |

### searchai-new-search-tests.ts (4 tests)

**Irrelevant / Stale Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | new search confirm fully clears prior facets/context (insurance, location, query) | That reset actually wipes state, not just returns to chat container | **High** |
| 2 | new search flow on mobile (iphone-6+) | Confirmation modal + reset on mobile (all 4 are viewport-agnostic) | Medium |
| 3 | follow-up message in search mode updates results, not just fires request | That refinement chat changes the result set (only request interception tested) | Medium |
| 4 | dismissing confirmation modal via overlay/escape preserves results | Alternate cancel paths beyond the Cancel button | Low |

### searchai-results-tests.ts (7 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | displays doctor cards with provider information | **Redundant** — subsumed by #4/#5 (cards render) and #6/#7 (cards have links); viewport-agnostic duplicate. |
| 4 | displays doctor cards in search results (macbook-15) | **Overlapping** — "first result exists" is weaker than and subsumed by #6 (desktop card has buttons/links). |
| 5 | displays doctor cards in search results (iphone-6+) | **Overlapping** — "first result exists" subsumed by #7 (mobile card has buttons/links). |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | zero-results / no-providers empty state renders | Empty results UX (no coverage today) | **High** |
| 2 | provider card click navigates to profile / booking destination | That card links actually route somewhere (out-of-scope "booking destinations") | **High** |
| 3 | section header grouping reflects backend grouping data | That grouping logic maps to correct labels (only presence is checked) | Medium |
| 4 | results pagination / load-more or scroll behavior | Loading additional providers | Medium |
| 5 | results render with no insurance/location context (defaults) | Control state with minimal params | Low |

### searchai-triage-chat-tests.ts (8 tests)

**Irrelevant / Stale Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 7 | shows chat response after triage on mobile | **Overlapping** — same mock-triage SSE + same "Let me find providers for you." assertion as #4 (mobile DOM existence); duplicate. |
| 8 | chat appears as sidebar on desktop | **Overlapping** — mock-triage SSE + chat header visible largely duplicates #3 (desktop response) plus searchai-direct-search #3. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | clicking a triage question option advances the DAG / next question appears | Multi-turn triage progression (only clickability tested, not the effect) | **High** |
| 2 | free-text triage answer (not preset option) is accepted and advances | Open-ended triage input path | **High** |
| 3 | ambiguous / unrelated query during triage handled gracefully | AI handling of off-topic or vague answers | Medium |
| 4 | triage question options clickable on mobile (iphone-6+) | Mobile counterpart to #5 (desktop-only) | Medium |
| 5 | triage chat accessibility (focus order, ARIA live region for responses) | A11y of the conversational flow | Low |

---

## High-Priority Gaps Summary

### Critical Theme 1: Missing triage parity across guided-search verticals

Two near-universal triage behaviors are present for the mature verticals (MH, ObGyn) but **absent across most imaging/specialty triages**. These are functional, user-facing gaps where one wrong flag could silently fire a premature search or re-show a skipped questionnaire.

| Vertical (guided-search/) | "quit → reload → stays hidden" | "does not call search when triggered from search page" |
|---------------------------|:------------------------------:|:------------------------------------------------------:|
| CT triage | ❌ missing | ❌ missing |
| Dental triage | ❌ missing | ❌ missing |
| Derm triage | ❌ missing | ❌ missing |
| Eye triage | ❌ missing | ❌ missing |
| Mammogram triage | ❌ missing | ✅ (procedure only) |
| MRI triage | ❌ missing | ❌ missing |
| Ultrasound triage | ❌ missing | ❌ missing |
| Xray triage | ❌ missing | ❌ missing |
| ObGyn triage | ✅ | ❌ missing |
| MH triage | ✅ | ✅ |

> **Eight of ten guided-search triage verticals lack session-persistence coverage, and nine of ten lack the "no premature search" guard.** Adding these as a shared parameterized helper across verticals would close ~16 high-priority gaps in one effort.

### Critical Theme 2: Control / experiment-OFF coverage missing

Many feature files verify only the experiment-ON state, leaving no guarantee that the control experience is correct (or that the feature is actually gated).

| File | Missing control/OFF coverage |
|------|------------------------------|
| guided-search-tests.ts (both dirs) | No "experiment OFF → no guided search / no triage" test |
| search_brands_triage.tests.ts | No "variant off → old triage" test (every other vertical has one) |
| search-mh-triage-tests.ts (guided) | No "experiment off → old fit questionnaire" test |
| search-provider-ner-tests.ts | No "sam_provider_ner OFF → no highlighting" test |
| search-provider-qualities-tests.js | No "flag OFF → review rating shown" test |
| search-next-availability-tests.ts | OFF variant only checks assignment, not button/modal suppression |
| search-legal-banners-tests.ts | No "flag OFF / non-applicable state → banner hidden" test |
| search-insurance-correction-tests.ts | No "ineligible / OFF → banner not shown" behavioral test |

### Critical Theme 3: searchai (AI search) is under-covered relative to risk

| # | File | Gap |
|---|------|-----|
| 1 | searchai-crisis-detection-tests.ts | **Single test for a safety-critical surface.** No assertion that crisis resources are actually shown, no coverage of varied crisis phrasings, no mobile coverage, no false-positive guardrail. |
| 2 | searchai-error-states-tests.ts | Error tests assert only "container visible" — no user-facing error content, no SSE stream-error path, no recovery-after-error. |
| 3 | searchai-insurance-confirmation-tests.ts | OON modal test (#3) uses a conditional assertion that can pass without exercising the modal. |
| 4 | searchai-filters-tests.ts | Filters are only *opened*, never *applied*; no verification that applying a filter re-queries. |
| 5 | searchai-results-tests.ts / direct-search | No zero-results empty state; card click never verified to navigate. Heavy card-render duplication across three files. |
| 6 | searchai-triage-chat-tests.ts | Triage options tested for clickability but not for advancing the DAG; no free-text answer path. |

### Critical Theme 4: Single-viewport coverage

A large share of files exercise only one viewport for behavior that renders on both. Highest-impact desktop-vs-mobile gaps:

| File | Covered | Missing viewport |
|------|---------|------------------|
| networkbar-insurance-change-tests.ts | mobile | desktop NetworkBar (entirely uncovered) |
| search-availability-modal-tests.js | desktop | mobile booking attribution |
| search-insurance-picker-v5-tests.ts | mobile (scan/skip) | desktop scan/skip/self-pay |
| search-mammogram-triage-tests.ts | mobile-implicit | desktop decision tree |
| search-eye-triage-tests.ts | mobile | desktop |
| search-pcp-triage-tests.ts / obgyn-triage | desktop | mobile |
| search-polaris-tests.ts | mobile | desktop card |
| search-top-practice-tag-tests.ts | mobile | desktop |
| search-facet-filter-tests.ts | mobile | desktop facet dropdowns |

### Weak / Shallow Tests Needing Strengthening

| File | Test | Issue |
|------|------|-------|
| guided-search-tests.ts (search/) | #1 | Asserts only container visible + no 500; no content or control state |
| searchai-insurance-confirmation-tests.ts | #3 | Conditional "if triggered" OON assertion — can pass without exercising the feature |
| searchai-error-states-tests.ts | all | Assert only "container visible," not actionable error content |
| search-map-controls-tests.ts | all 5 | Assert metrics only; no functional zoom/pan/layout verification |
| search-next-availability / insurance-picker-v5 / insurance-correction | OFF-variant tests | Assignment-only checks with no behavioral assertion |

### Notes

- **search-entrypoints.ts** is a type-definition/enum file, not a test file — it should not count toward test coverage (excluded from the relevant-test total above).
- **Mental Health OON files** (`search-mental-health-oon-desktop-tests.js`, `-mobile-tests.js`, and the shared `search-mental-health-oon.js`) run the same 6 `testSearchPageMoon` cases across viewports via a shared factory. This is intentional cross-viewport duplication, not stale code — counted separately from the stale/redundant total.
- **Duplicated test names** appear in `search-mammogram-triage-tests.ts` (#21/#22/#23 reuse #9/#10/#15 names) and `search-obgyn-triage-tests.ts` (#25 reuses #23's name; #29/#32/#35 share a name) — these are functionally distinct branches but the identical titles make failures hard to attribute and risk one masking another in reporting. Renaming to encode the branch (e.g., age band, treatment type) is recommended.
- Triage verticals that mirror each other (CT/MRI/ultrasound/xray referral + contrast flows; obgyn/pcp specialty-matching) are strong candidates for **shared parameterized helpers**, which would also make the missing-parity gaps in Theme 1 cheap to close.
