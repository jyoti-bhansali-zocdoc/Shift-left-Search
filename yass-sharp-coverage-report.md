# YASS Sharp — QA Test Coverage Gap Analysis

**Service:** `yass-sharp` (C# .NET 8.0 doctor-search / ranking service)
**Analyst:** Jyoti Bhansali (QA, Zocdoc)
**Generated:** 2026-04-22
**Source test mappings:**
- `~/Downloads/yass-sharp-test-mapping.md` — unit tests (~2,558 cases across ~320 files)
- `~/Downloads/yass-sharp-integration-test-mapping.md` — integration tests (167 cases across 26 files)

**Methodology:** Each existing test case from the mapping files was compared against the current implementation in `src/YassSharp/` to decide whether it meaningfully exercises live production behaviour ("relevant") or is tautological / pass-through / testing a C# language guarantee ("irrelevant"). Gaps — user-visible behaviours, error branches, and contracts with no corresponding test — are enumerated as **Missing Tests** with a priority rubric:

| Priority | Definition |
|----------|-----------|
| **High** | Directly impacts search ranking, PHI safety, revenue (SPO/ads), API contract stability, or cross-directory isolation. A regression here would be user-visible or incident-worthy. |
| Medium | Branch coverage, error semantics, serialization contracts, or telemetry. Regressions are noticeable but typically not customer-facing. |
| Low | Cosmetic, defensive defaults, `ToString`/`Equals`, or formatting-only behaviour. |

---

## Executive Summary

### Test Inventory

| Layer | Files | Test cases (mapping) | Report sections |
|-------|-------|---------------------|-----------------|
| Unit tests — Non-Search (Ab, Gemini, Json, Metrics, root, …) | 14 | ~200 | A.1 – A.14 |
| Unit tests — Search/Algorithm | 27 | ~230 | B.1 – B.27 |
| Unit tests — Search/Contracts | 21 | ~190 | C.1 – C.21 |
| Unit tests — Search/Es | 74 | ~630 | D.1 – D.74 |
| Unit tests — Search/Ranking | 43 | ~350 | E.1 – E.43 |
| Unit tests — Search/Yass | 40 | ~310 | F.1 – F.40 |
| Unit tests — Search/Types + Search/Utils | 30 | ~170 | G.1 – G.30 |
| Unit tests — Search misc (MI, Enchilada, SPO, CrossEncoder, Statsd, Hydration, Grouping, Models, Embeddings, Personalization, Availability, Constants, Datalake, Decorating, DynamoDb, Semantic, Annotation, Canoe, Supplementing) | 70 | ~478 | H.1 – H.70 |
| **Unit tests subtotal** | **~319** | **~2,558** | **Part 1** |
| Integration tests | 26 | 167 | I.1 – I.26 |
| **Total** | **~345** | **~2,725** | |

### Findings at a glance

- **~210 tests flagged as irrelevant** across all chunks — mostly trivial auto-property getters/setters, enum int-cast assertions, and tautological constant comparisons that replicate the C# language rather than system behaviour.
- **~840 missing tests suggested**, of which **~310 are High-priority** — clustered around:
  - Cross-directory isolation (GPH 963, Schweiger 459, marketplace -1) — ranking, aggregations, and SPO ad visibility.
  - PHI sanitisation — `PreviewProvLocResult`, `SensitiveHealthInformationChecker`, best-sentence pipeline, log scrubbing.
  - JSON contract stability — `[JsonPropertyName]` round-trips for every DTO in Search/Types and Search/Contracts.
  - AB-flag plumbing — `YASS-Use-Es7`, `YASS-Streaming-Index-Test`, ScoreFusion experiments, explicit overrides via `X-ZD-ABOverrides`.
  - Ranking / scoring correctness — LightGBM feature order, best-sentence cross-encoder error paths, MI supply rank tie-breaking, Voyage embedding dim mismatch.
  - Market Intelligence — supply/refinement math, specialty fan-out caps, preview-mode isolation.
  - Observability — Statsd emission on error branches, correlation-id propagation, Firehose audit content.

---

## How to read this report

- **Part 1 — Unit Tests** (Chunks A–H): one `###` subsection per spec file, each containing an *Irrelevant Tests* table and a *Missing Tests* table. Section IDs (A.1, B.3, H.27…) match the order the files appear under their parent directory.
- **Part 2 — Integration Tests** (Chunk I): same structure, driven by the `tests/YassSharp.IntegrationTests/` layout.
- **Part 3 — High-Priority Gaps Summary**: cross-cutting themes aggregated from all chunks, grouped by risk area, with pointers back into Parts 1 and 2 so you can build a focused work queue without reading every section.

All test suggestions are phrased as NUnit-style test names so they can be lifted directly into a PR.

---



# Part 1 — Unit Test Coverage Analysis

**Scope:** `tests/YassSharp.UnitTests/` (~319 spec files, ~2,558 test cases)
**Source under test:** `src/YassSharp/`

The eight chunks below partition the unit test tree into non-overlapping directories. Each `### X.N <SpecFile>.cs` subsection lists the tests flagged as irrelevant, then the missing tests that should be added.

---

## Chunk A — Non-Search Unit Tests
*Directories: `Ab/`, `BotDetection/`, `Gemini/`, `Json/`, `Metrics/`, `ModelBinding/`, `Utils/`, and the `UnitTests` root (14 files).*

### A.1 AbExperimentsTests.cs (27 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `GetEmbeddingExperiment_WithAppProjectSource_ShouldReturnExperimentIfEligible` | Conditional assertion — only asserts `HaveCount(1)` inside an `if` block; if the condition is false the test silently passes with no assertion (false green). |
| 2 | `YassAbFlag_Control_ShouldReturnOff` | Trivial property read on a subclass that inherits the base default — essentially testing a C# virtual property's default value. |
| 3 | `YassAbFlag_Test_ShouldReturnOn` | Same as above — trivial default-value assertion. |
| 4 | `YassAbFlag_IsFeatureFlag_ShouldReturnTrue` | Trivial default-value assertion on inherited virtual. |
| 5 | `YassExperimentBase_IsFeatureFlag_ShouldReturnTrue` | Trivial default-value assertion. |
| 6 | `NoSpoExperiment_Id_ShouldReturnCorrectId` | String-constant assertion; no behavior exercised. |
| 7 | `NoSpoExperiment_Project_ShouldReturnWebAndApp` | Enum-constant assertion; no behavior exercised. |
| 8 | `ActiveExperiments_ShouldAllHaveIds` / `ActiveExperiments_ShouldAllHaveControl` / `ActiveExperiments_ShouldAllHaveTest` | Schema-smoke tests that pass by construction because all experiment classes hardcode non-empty strings; provides no meaningful protection. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `SkipSpoAdsPage2PlusMobileExperiment_ShouldFlip_WithIosBelowMinVersion_ReturnsFalse` | Version-gating branch (`MinimumIosVersion = "4.109"`) — currently completely untested | **High** |
| 2 | `SkipSpoAdsPage2PlusMobileExperiment_ShouldFlip_WithAndroidBelowMinVersion_ReturnsFalse` | Android version gate — currently completely untested | **High** |
| 3 | `SkipSpoAdsPage2PlusMobileExperiment_ShouldFlip_WithMalformedAppVersion_DoesNotThrow` | Covers try/catch in `ParseVersionToDouble` | Medium |
| 4 | `SkipSpoAdsPage2PlusMobileExperiment_ShouldFlip_WhenPageLessThan1_ReturnsFalse` | Covers `req.Page < 1` branch | Medium |
| 5 | `SearchMobileMapRefreshExperiment_ShouldFlip_WhenDesktop_ReturnsFalse` | Desktop-exclusion branch in override | **High** |
| 6 | `FetchNewPatientAvailabilityOnlyExperiment_ShouldFlip_WithSpendCappedProviders_ReturnsTrue` | `ShouldFilterSpendCappedProvidersStatic` integration | Medium |
| 7 | `ProviderNerAbExperimentImpl_ShouldFlip_WithSingleHighlightedId_ReturnsFalse` | Covers the `> 1` split length branch | Medium |
| 8 | `RemoveUnbookableResultsFromHomeCarouselExperiment_ShouldFlip_WithNonHomePageCaller_ReturnsFalse` | Flavor + CallerType compound branch | Medium |
| 9 | `AddSpoToSemExperiment_ShouldFlip_WithSemListingCaller_ReturnsTrue` | Only positive path untested | Medium |
| 10 | `GetExperiments_ShouldDeduplicateIfExperimentAppearsMultipleTimes` | Enumeration safety | Low |
| 11 | `ActiveExperiments_ShouldHaveUniqueIds` | Data integrity — two experiments with same Id would silently break AB routing | **High** |
| 12 | `Intersperse5thSpoAdExperiment_ShouldFlip_AlwaysFalse_IsNotIncludedInGetExperiments` | Confirms `ShouldFlip => false` correctly excludes it | Medium |

---

## A.2 ABServiceClientErrorTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `SetAssignmentsWithDefaultAsync_WithNullExperimentsList_ShouldThrowOrHandleGracefully` | Null/empty input defense | Medium |
| 2 | `SetAssignmentsWithDefaultAsync_ExceptionPropagatedIntoResponse_ShouldNotBeSwallowed` | Verify `result.Exception` contains the actual thrown exception type | Medium |
| 3 | `SetAssignmentsWithDefaultAsync_WithNullMetricRecorder_DoesNotThrow` | `IMetricRecorder? _metricRecorder` null-safe path | Medium |
| 4 | `SetAssignmentsWithDefaultAsync_WhenServiceUnavailable_EachExperimentGetsItsOwnDefault` | Verifies multi-experiment default mapping (not just dictionary size) | Medium |

---

## A.3 ABServiceClientV2AdapterTests.cs (22 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `Constructor_WithInjectedClients_ShouldStoreClients` | Only asserts `adapter.Should().NotBeNull()` — tautological since `new` never returns null. |
| 2 | `GetAssignmentsAsync_WhenUpdateAssignmentsFromHeaderThrowsException_ShouldNotFail` | Per the test's own comments, it cannot actually trigger the catch block and ends up as a duplicate of `WithAbOverrides_ShouldApplyOverrides`. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `GetAssignmentsAsync_WhenAbServiceExceptionAndAlwaysOnFlagRequested_ShouldStillForceOn` | Interaction between exception-default branch and `AlwaysOnFlags` | **High** |
| 2 | `GetAssignmentsAsync_WhenAbServiceExceptionWithKnownExperimentId_ShouldUseControlFromDefinition` | Default-resolution path through `AbExperiments.ActiveExperiments.FirstOrDefault(...).Control` | **High** |
| 3 | `GetAssignmentsAsync_ShouldRecordTimerMetric` | `_metricRecorder.Timer("ab", ...)` call not verified anywhere | Medium |
| 4 | `GetAssignmentsAsync_ShouldLogClientSelection` | `LogDebug` on WEB/MOBILE selection not verified | Low |
| 5 | `GetAssignmentsAsync_MobileRequest_ShouldUseMobileProjectId` | Verifies projectId passed to underlying V3 client (not just which mock) | Medium |
| 6 | `GetAssignmentsAsync_OverrideWithExperimentNotInResponse_ShouldNotAddNewKey` | Confirms overrides only modify existing assignments (matches Scala foldLeft) | Medium |
| 7 | `GetAssignmentsAsync_OverrideValueTrimmed` | `experimentValue.Trim()` in ParseExperimentsFromSessionId | Low |
| 8 | `GetAssignmentsAsync_ExperimentDefaults_ShouldUseExperimentControl_NotLiteralControl` | E.g. for MapleV26Test control is "maple_v25", not "control" | **High** |

---

## A.4 ABServiceClientV3Tests.cs (14 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `Constructor_ShouldStoreBaseUriAndProjectId` | Only asserts non-null on `new`. |
| 2 | `Constructor_ShouldTrimTrailingSlash` | The test comment admits it cannot actually verify trimming ("can't directly access AssignmentsUri"); asserts only non-null. |
| 3 | `SetAssignmentsWithDefaultAsync_WithProvidedProjectId_ShouldUseProvidedProjectId` | Test comment acknowledges it "can't directly verify" the provided projectId is used; asserts only `capturedProjectId != null`, which is trivially true for any POST body. |
| 4 | `SetAssignmentsWithDefaultAsync_WithoutProvidedProjectId_ShouldUseInstanceProjectId` | Same problem as above — does not inspect request body for projectId. |
| 5 | `SetAssignmentsWithDefaultAsync_WithAttributes_ShouldIncludeAttributesInRequest` | Never actually inspects the outgoing request body for the attributes. |
| 6 | `SetAssignmentsWithDefaultAsync_WithUserAgent_ShouldIncludeUserAgentInRequest` | Never inspects outgoing body for user-agent. |
| 7 | `SetAssignmentsWithDefaultAsync_WithRequestOriginUrl_ShouldIncludeOriginUrlInRequest` | Never inspects outgoing body for origin URL. |
| 8 | `SetAssignmentsWithDefaultAsync_WhenResponseHasNullAssignments_ShouldLogAndReturnEmpty` | Has no assertion beyond `result.Should().NotBeNull()`; comment says "Should handle null assignments gracefully" with no verification. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `SetAssignmentsWithDefaultAsync_RequestBodyContainsProjectId` | Inspect WireMock recorded request body to confirm projectId is sent (the whole purpose of V3) | **High** |
| 2 | `SetAssignmentsWithDefaultAsync_RequestBodyOverridesInstanceProjectId` | Verify `projectId` arg overrides the constructor default on the wire | **High** |
| 3 | `SetAssignmentsWithDefaultAsync_RequestBodyContainsAttributesAndUserAgent` | Verify body serialization of attrs/UA/origin | Medium |
| 4 | `SetAssignmentsWithDefaultAsync_WhenServiceReturns500_IncrementsErrorMetric` | Metric recorder call on HTTP error | Medium |
| 5 | `SetAssignmentsWithDefaultAsync_LogsInformationForRequestAndResponse` | Structured log verification | Low |
| 6 | `SetAssignmentsWithDefaultAsync_UsesCamelCasePropertyNames` | Confirm JsonMediaTypeFormatter settings actually produce camelCase on wire | Medium |
| 7 | `Constructor_TrimsTrailingSlashFromBaseUri` | Hit WireMock with URI `http://.../` and assert no double-slash in path | Medium |

---

## A.5 BotDetectionAdapterTests.cs (27 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `Constructor_ShouldCreateParser` | Only asserts non-null on `new`. |
| 2 | `Parse_WithBotUserAgent_ShouldDetectBot` | Loops without asserting bot detection is correct — comment: "may or may not be accurate". |
| 3 | `Parse_WithZocdocMobileApp_ShouldDetectMobileApp` | No assertion beyond non-null — "may or may not detect as mobile app". |
| 4 | `Parse_ResultShouldHaveAllProperties` | Only does `_ = property` discards; no behavior verified. |
| 5 | `Parse_ResultUserAgentProperty_ShouldHaveClientInfo` | Only discards nullable chain, no assertions. |
| 6 | `Parse_ResultUserAgentInfo_ShouldHaveProperties` | Same — inside `if (x != null)` only discards. |
| 7 | `Parse_ResultOsInfo_ShouldHaveProperties` | Same — only discards. |
| 8 | `Parse_ResultDeviceInfo_ShouldHaveProperties` | Same — only discards. |
| 9 | `Parse_ResultAppInfo_ShouldHaveProperties` | Same — only discards. |
| 10 | `Parse_WithInvalidUserAgent_ShouldReturnNull` | Has no assertions at all; comment says "we just verify it doesn't throw". |
| 11 | `Parse_WithEmailProgramUserAgent_ShouldDetectEmailProgram` | No assertion on IsEmailProgram — "may or may not be accurate". |
| 12 | `Parse_AppInfoProperty_ShouldHandleNullAppInfo` | Discards without assertion. |
| 13 | `Parse_AppInfoProperty_ShouldHandleNonNullAppInfo` | Discards without assertion. |
| 14 | `Parse_UserAgentProperty_ShouldHandleNullUserAgent` | Discards only. |
| 15 | `Parse_UserAgentProperty_ShouldHandleAllNestedNullCombinations` | Long chain of `_ = ...` discards with no assertions. |
| 16 | `Parse_DeviceInfoWithEmptyBrandOrModel_ShouldConvertToNull` | Assertion is inside `if (string.IsNullOrEmpty(device.Brand))` — tautological self-check. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `Parse_WithGooglebotUA_IsBotShouldBeTrue` | Real assertion on bot detection (replace irrelevant #2) | **High** |
| 2 | `Parse_WithZocdocAppUA_IsMobileAppShouldBeTrue` | Real assertion on app detection | **High** |
| 3 | `Parse_WithOutlookUA_IsEmailProgramShouldBeTrue` | Verify email-program branch actually flips | Medium |
| 4 | `Parse_iPhoneApp_NullsOutMajorMinorPatch_ButNotAndroidApp` | The specific Scala-parity logic for iPhoneApp vs AndroidApp | **High** |
| 5 | `Parse_MacintoshWindowsMix_WindowsNotOverriddenToMac` | Already exists partially but should verify Windows remains its original family, not "Other" | Medium |
| 6 | `Parse_AndroidDeviceBuildRegex_FallbackPath` | Covers `AndroidDeviceBuildRegex` branch (currently only Mobile Safari + Safari tested) | Medium |
| 7 | `Parse_EmptyStringVersionFields_SerializesWithoutKeys` | Actually assert null (to-JSON) vs empty | **High** |
| 8 | `Parse_ThreadSafety_ConcurrentCallsConsistent` | Parser is shared static-style — concurrency safety | Low |

---

## A.6 RetryingGeminiClientTests.cs (9 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `Constructor_WithNullInner_ShouldThrow` | `ArgumentNullException` path in ctor | Medium |
| 2 | `Constructor_WithNullLogger_ShouldThrow` | `ArgumentNullException` path in ctor | Medium |
| 3 | `CallAsync_RetryDelay_ShouldWaitDelayMs` | Verifies 200ms backoff between retries | Medium |
| 4 | `CallAsync_WhenRpcExceptionInternal_DoesNotRetry` | Confirms only Unavailable/DeadlineExceeded retry (not other gRPC codes) | **High** |
| 5 | `CallAsync_PropagatesSystemPromptAndMaxTokensToInner` | Verify args forwarded correctly | Medium |
| 6 | `CallAsync_WhenCancellationTokenTriggeredDuringDelay_Throws` | Cancellation during retry-sleep | Medium |
| 7 | `CallAsync_LogsWarningOnRetry` | Logger verification on retry path | Low |

---

## A.7 ComparatorIgnoreAttributeTests.cs (10 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `Constructor_ShouldCreateInstance` | Trivial — just `new`. |
| 2 | `Attribute_CanHaveMultipleInstances` | Trivial object identity check — does not exercise the attribute. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `AttributeUsage_ShouldNotAllowMultiple` | Verify default `AllowMultiple = false` on attribute | Low |
| 2 | `AttributeUsage_ShouldNotAllowMethods` | Confirm restriction to Property/Field only | Low |
| 3 | `Attribute_CanBeAppliedToPrivateProperty` | Private/protected member detection | Low |

---

## A.8 DynamicFilterConvertersTests.cs (21 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `DynamicFilterTupleListConverter_Read_WithNonArrayTuple_ShouldHandleGracefully` | Try/catch in test that accepts either outcome with no actual assertion on behavior. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `DynamicFilterSetConverter_Read_WithAllEnumMembersMapped` | Scan every value of DynamicFilter and confirm round-trip | Medium |
| 2 | `DynamicFilterSetConverter_Read_WithDuplicates_ShouldDedupe` | HashSet semantics | Low |
| 3 | `DynamicFilterTupleListConverter_Read_PreservesOrder` | List ordering contract | Medium |
| 4 | `DynamicFilterTupleListConverter_Read_WithDeeplyMalformedArray_ThrowsJsonException` | Replace the "try/catch" irrelevant test with a definite assertion | Medium |
| 5 | `DynamicFilterSetConverter_Read_WithMixedCaseStrings_ShouldMatch` | Case-insensitive lookup branch (static ctor's uppercase variant) | Medium |
| 6 | `DynamicFilterTupleListConverter_Write_WhenValuesContainsNull_DoesNotCrash` | Defensive serialization path | Low |

---

## A.9 EnumMemberJsonConverterFactoryTests.cs (17 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `EnumMemberJsonConverter_Read_WithWrongJsonType_ShouldThrow` | Number token instead of string | Medium |
| 2 | `EnumMemberJsonConverter_Read_IsCaseInsensitive_MatchesEnumMemberValues` | Cover the second lookup path (`ToLowerInvariant`) | Medium |
| 3 | `EnumMemberJsonConverter_ForEnumWithoutEnumMemberAttribute_UsesEnumName` | Enum that lacks `[EnumMember]` on a member | **High** |
| 4 | `CanConvert_WithNonEnumNullable_ReturnsFalse` | `int?`, `string` edge — `Nullable.GetUnderlyingType(int?)?.IsEnum` → false | Medium |
| 5 | `NullableEnumMemberJsonConverter_Read_WithInvalidValue_ShouldThrow` | Invalid non-null string for nullable | Medium |
| 6 | `EnumMemberJsonConverter_Write_ForEnumValueNotInLookup_ShouldThrow` | Defined-but-unmapped enum edge | Low |

---

## A.10 MetricRecorderTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `MockMetricRecorder_CanVerifyApplicationMetricCalls` | Tests Moq's `Verify` API — mocks the thing it "verifies"; does not exercise any production code. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `DebugMetricRecorder_IsThreadSafe` | Concurrent writes to file under `WriteLock` | **High** |
| 2 | `DebugMetricRecorder_Histogram_WritesCorrectType` | `Histogram`/`Distribution`/`Event` paths — only Increment/Counter/Timer/Gauge are tested | Medium |
| 3 | `DebugMetricRecorder_StartTimer_WritesTimerMetricOnDispose` | `TimerDisposable` lifecycle | **High** |
| 4 | `DebugMetricRecorder_TimeExecution_WritesTimerAndExecutesAction` | `TimeExecution`/`TimeExecutionAsync` variants totally untested | Medium |
| 5 | `NullMetricRecorder_AllMethodsAreNoOps` | `NullMetricRecorder` has zero coverage | Medium |
| 6 | `NullMetricRecorder_TimeExecution_StillExecutesAction` | Confirm TimeExecution forwarding behaviour | **High** |
| 7 | `DiagnosticMetricsRecorder_StopAsync_HaltsEmission` | Graceful stop behavior | Medium |
| 8 | `DebugMetricRecorder_SerializesTagsCorrectly` | JSON shape of tags array | Low |

---

## A.11 EnumMemberTypeConverterTests.cs (17 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `ConvertFrom_WithEnumLackingExtensionsClass_FallsBackToEnumParse` | Covers enum type with no `FooExtensions.InputValues` dict | **High** |
| 2 | `ConvertFrom_WithInputValuesDictionary_PrefersDictionaryOverEnumMember` | Priority of static dictionary over attribute | Medium |
| 3 | `ConvertFrom_WithWhitespaceString_ShouldThrowFormat` | Whitespace-only input | Medium |
| 4 | `ConvertFrom_WithNullString_ShouldCallBase` | Null value handling | Medium |
| 5 | `ConvertTo_WithEnumValueNotInLookup_ShouldFallbackToToString` | `EnumToString.TryGetValue` else path | Medium |
| 6 | `StaticInitializer_DoesNotThrow_WhenExtensionsFieldMissing` | Reflection fallback when field absent | Medium |

---

## A.12 StringExtensionsTests.cs (8 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `StripAccents_WithChineseCharacters_ShouldPreserveThem` | Non-latin scripts pass through unchanged | Medium |
| 2 | `StripAccents_WithEmoji_ShouldPreserveEmoji` | Surrogate-pair handling | Low |
| 3 | `StripAccents_WithCombiningMarksOnly_ShouldReturnEmpty` | All-diacritic input edge case | Low |
| 4 | `StripAccents_WithGermanEszett_ShouldPreserveSS` | German ß edge case (documents behavior) | Low |
| 5 | `StripAccents_PreservesStringLengthWhenNoMarks` | Performance/no-op invariant | Low |
| 6 | `StripAccents_WithLigatures_ShouldHandleOrDocumentBehavior` | æ / œ behavior | Low |

---

## A.13 TextHelperTests.cs (23 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | `ExtractSentences_WithQuestionMarkFollowedByLowercase_ShouldNotSplit` | `?` followed by non-capital (boundary regex demands capital) | Medium |
| 2 | `ExtractSentences_WithExclamationMidWord_ShouldNotSplit` | Interjection edge case | Low |
| 3 | `ExtractSentences_WithVeryLongText_ShouldNotExceedReasonableTime` | Performance regression guard | Low |
| 4 | `ExtractSentences_WithConsecutivePunctuation_ShouldHandleGracefully` | "Really?! Yes." case | Medium |
| 5 | `ExtractSentences_WithVsAbbreviation_ShouldNotSplit` | Covers "vs" in CommonAbbreviations (untested) | Medium |
| 6 | `ExtractSentences_WithAveOrRdOrBlvdOrCt_ShouldNotSplit` | Street abbreviations in CommonAbbreviations are not all tested | Medium |
| 7 | `ExtractSentences_WithUKAbbreviation_ShouldNotSplit` | "U.K"/"UK" untested | Low |
| 8 | `ExtractSentences_WithTextEndingMidSentence_ShouldReturnPartial` | No trailing punctuation with trailing partial | Medium |

---

## A.14 ExampleTests.cs (1 test)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | `TokenEmptyTest` | Placeholder: asserts `(1 + 1).Should().Be(2)`. Tests no YassSharp code at all. |

**Missing Tests:** None — this file should be deleted, not expanded. If a sentinel is desired, replace with a smoke assertion that loads a real YassSharp type (e.g., `typeof(AbExperiments).Should().NotBeNull()`).

---

### A — Cross-cutting gap: missing test file

Source file `src/YassSharp/Json/ScalaZonedDateTimeConverter.cs` has no corresponding test file in the non-Search scope. The converter handles an ISO timestamp format with a trailing `[UTC]` marker (Scala-parity) and is in the serialization hot path.

**Missing test class:**

| # | Missing test class | What it would cover | Priority |
|---|---------------------|--------------------|----------|
| 1 | `ScalaZonedDateTimeConverterTests.cs` | Read/Write of ISO + "[UTC]" format, millisecond formatting, round-trip, null/malformed input | **High** |



---

## Chunk B — Search/Algorithm Unit Tests
*Directory: `tests/YassSharp.UnitTests/Search/Algorithm/` (27 files).*

### B.1 AlgorithmExtensionsTests.cs

Source: `Search/Algorithm/AlgorithmExtensions.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | All tests exercise real WithLocalityFilters / WithSoftAvailabilityFilterer / ReplaceFilterer paths |

### Missing Tests
| Test | Priority |
|------|----------|
| `WithLocalityFilters_ShouldAddStateFilterer_WhenLocalityIsState` | High |
| `WithLocalityFilters_ShouldAddBoroughFilterer_WhenLocalityIsBorough` | High |
| `WithLocalityFilters_ShouldAddPostalCodeFilterer_WhenLocalityIsPostalCode` | High |
| `WithLocalityFilters_ShouldReturnAlgorithmUnchanged_ForUnknownLocality` (default switch branch) | Medium |
| `WithSoftAvailabilityFilterer_ShouldPreserveResultEnrichers_OnCopy` | Medium |
| `ReplaceFilterer_ShouldPreservePostEsProcessors_AfterCopy` | Medium |

---

## B.2 SearchAlgorithmTests.cs

Source: `Search/Algorithm/SearchAlgorithm.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | All exercise Constructor/Copy/Validate/Properties |

### Missing Tests
| Test | Priority |
|------|----------|
| `Constructor_ShouldAcceptResultEnrichers_AndExposeThem` | High |
| `Constructor_ShouldDefaultNullListsToEmpty_ForAllOptionalPipelineStages` | Medium |
| `Copy_ShouldOverrideIndividualParameters_OneAtATime` (per-param copy correctness) | Medium |
| `Copy_ShouldPreserveResultGrouper_AndDataRetrievers_WhenNotOverridden` | Medium |
| `Validate_ShouldThrow_WhenEsIndexIsEmpty` | Medium |
| `Validate_ShouldThrow_WhenNameIsEmpty` | Medium |

---

## B.3 SearchResponseProcessorBaseTests.cs

Source: `Search/Algorithm/SearchResponseProcessorBase.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Real processor pipeline coverage |

### Missing Tests
| Test | Priority |
|------|----------|
| `ProcessAsync_ShouldAccumulateRanksCorrectly_AcrossMultipleInvocations` | High |
| `ProcessAsync_ShouldPreserveOrdering_WhenProcessorMutatesResults` | Medium |
| `ProcessAsync_ShouldHandleEmptyResultList_WithoutThrowing` | Low |

---

## B.4 StubSearchResponseProcessorTests.cs

Source: `Search/Algorithm/StubSearchResponseProcessor.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Fully covers stub contract |

### Missing Tests
| Test | Priority |
|------|----------|
| _(none actionable)_ | Stub is a no-op by design |

---

## B.5 ValidatedSearchAlgorithmTests.cs

Source: `Search/Algorithm/ValidatedSearchAlgorithm.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Constructor null-checks are legitimate guard-clause tests |

### Missing Tests
| Test | Priority |
|------|----------|
| `PostEsProcessors_ShouldRunInExactPipelineOrder_12Steps` (reconciliators → sorter → enrichers → groupMarker → postEsFilterers → postEsRankers → groupRanker → dedupers → decorators → paginators → paginatorScorer → grouper) | High |
| `CombinedEsFilterers_ShouldIncludeVirtualLocationFilterer_WhenVirtualLocationPresent` | High |
| `BuildEsPreference_ShouldReturnReplayNodeId_WhenSet` | High |
| `CopyWithSpoEnabled_ShouldReturnCopyWithSpoFlagSet` | Medium |
| `EsIndex_ShouldReturnInvalidIndex_WhenSimulateEsFailureFlagOn` | High |
| `QueryBuilder_ShouldSuppressMonolithPreviewProviderFilter_WhenAllowPreviewFlagOn` | Medium |
| `ElasticQueryJson_ShouldSerializeFullQuery_Successfully` | Medium |
| `FiltererNames_GroupingNames_ScorerInfos_ShouldReturnExpectedMetadata` | Low |

---

## B.6 Constants/DirectoryIdsTests.cs

Source: `Search/Algorithm/Constants/DirectoryIds.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | All constants and IsNonCustomerDirectory branches covered |

### Missing Tests
| Test | Priority |
|------|----------|
| _(none actionable)_ | Fully covered |

---

## B.7 Constants/EsSizeConstantsTests.cs

Source: `Search/Algorithm/Constants/EsSizeConstants.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Real constant assertions |

### Missing Tests
| Test | Priority |
|------|----------|
| `EsTotalSizeConstants_ShouldExposeSize300` (defined in source, not asserted) | Low |
| `EsTotalSizeConstants_ShouldExposeSize1500` (defined in source, not asserted) | Low |

---

## B.8 Constants/RequestFeatureCategoriesTests.cs

Source: `Search/Algorithm/Constants/RequestFeatureCategories.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Constants well covered |

### Missing Tests
| Test | Priority |
|------|----------|
| _(none actionable)_ | Fully covered |

---

## B.9 Base/AlgoContainerRankByTests.cs

Source: `Search/Algorithm/Base/AlgoContainerRankBy.cs` + `IAlgoContainerRankBy`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Real RankBy name/dispatch paths |

### Missing Tests
| Test | Priority |
|------|----------|
| `GetPostEsRankers_ShouldReturnDistanceSorterBranch_ForRankByDistance` | High |
| `GetPostEsRankers_ShouldReturnWaitTimeRatingRanker_ForRankByWaitTimeRating_Organic` (IOrganicRanker branch) | High |
| `GetPostEsRankers_ShouldReturnWaitTimeRatingRanker_ForRankByWaitTimeRating_NonOrganic` | Medium |
| `GetPostEsRankers_ShouldReturnEmptyList_ForRankByNone` | Medium |
| `GetPostEsRankers_ShouldFallBackToDefault_ForUnknownRankBy` | Medium |
| `ScoreFusionRanker_ShouldBeInsertedBeforeResultsWithSameScoreShuffler` (ordering contract) | High |

---

## B.10 Base/AvailabilityRetrieverTests.cs

Source: `Search/Algorithm/Base/AvailabilityRetriever*.cs` + `AvailabilitySkipper`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | ~21 tests exercise real code paths |

### Missing Tests
| Test | Priority |
|------|----------|
| `RetrieveAsync_ShouldReturnEmpty_WhenSimulateAvailabilityFailureFlagOn` | High |
| `RetrieveAsync_ShouldTreatTaskCanceledException_AsDistinctFromTimeoutException` | High |
| `RetrieveAsync_ShouldChunkProviderIds_AtAvailabilityChunkSize75` | Medium |
| `Skipper_ShouldSkipAvailability_WhenParsedUserAgentIsBot_Fallback` (AB-flag-missing fallback) | Medium |
| `Skipper_ShouldSkipAvailability_WhenIsWhitelistedBotFlagOn` | Medium |
| `RetrieveAsync_ShouldNotRethrow_OnTransientAvailabilityErrors` | Medium |

---

## B.11 Base/ScoreFusionRankerTests.cs

Source: `Search/Algorithm/Base/ScoreFusionRanker.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Real fusion-math coverage |

### Missing Tests
| Test | Priority |
|------|----------|
| `Rank_ShouldUseConstrainedFusionPath_WhenRankByIsConstrainedScoreFusion` | High |
| `Rank_ShouldHandleAllNullScores_WithoutThrowing` | High |
| `Rank_ShouldProduceStableOrder_WhenScoresAreIdentical` | Medium |
| `Rank_ShouldPreserveFinalScorerName_WhenFusionSkipped` | Medium |
| `Rank_ShouldClampFusionWeight_ToValidRange` | Low |

---

## B.12 Container/BasicFilterAlgoContainerTests.cs

Source: `Search/Algorithm/Container/BasicFilterAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `Decorators_ShouldContainRankDecorator_AndDotProvLocMapDecorator` | Medium |
| `PostEsPaginators_ShouldContainHydrationAndInMemoryPager` | Medium |
| `Algorithm_ShouldHaveMarketplaceBasePostEsRankers` (RankRandomizer + Shuffler + DistanceSorter) | High |
| `Algorithm_ShouldHandleWithLocalityFilters_WhenLocalityPresent` | Medium |

---

## B.13 Container/DefaultEnterpriseAlgoContainerTests.cs

Source: `Search/Algorithm/Container/DefaultEnterpriseAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| All 6 core + 3 `IncludeMapDotsForDefaultEnterpriseAlgo*` tests | Silent-skip anti-pattern: `try { new TheBoxRanker(...) } catch (InvalidOperationException) { Assert.Ignore("ML model resources not available") }` — tests pass in CI without asserting anything |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldUseInNetworkOnlyStatusFilterer_WhenEnableSplitOONSelfPayForWLFlagOn` | High |
| `Algorithm_ShouldUseOnlyInNetworkBookableFilterer_WhenEnableSplitOONSelfPayForWLFlagOff` | High |
| `Algorithm_ShouldUseRolledUpPaginators_WhenIsRolledUp` | Medium |
| `Name_ShouldBeRenamed_ForZDTestDirectory` (DirectoryIds.ZDTest=-2 routing) | Medium |
| `Algorithm_ShouldReplaceTheBoxRanker_WithMockInTestHarness` (remove silent-skip by injecting test double) | High |
| `Decorators_ShouldIncludeDotProvLocMapDecorator` (without touching ML init) | Medium |

---

## B.14 Container/ExternalApiAlgoContainerTests.cs

Source: `Search/Algorithm/Container/ExternalApiAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldHaveNoDecorators` (or assert exact decorator list) | Medium |
| `Algorithm_ShouldSupportRankByDistance_Variation` | Medium |
| `EsBatchSize_ShouldBeBatchDefault` | Low |
| `Algorithm_ShouldNotIncludeSpoFilterers` | Low |

---

## B.15 Container/HomePageSimilarDoctorsContainerTests.cs

Source: `Search/Algorithm/Container/HomePageSimilarDoctorsContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Thin but legitimate |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldHaveExpectedEsFilterers` (CrosslistingSpecialtyId, LocationActive, ProvLocMappingApproved, SearchableDirectory, etc.) | High |
| `Algorithm_ShouldUseGetProviderCarouselPostEsFilterers_Branch` | High |
| `Algorithm_ShouldHaveYassJrBasePostEsRankers` (DistanceSorter) | Medium |
| `Algorithm_ShouldHaveDuplicateProviderLocationsFilterer` | Medium |
| `ResultGrouper_ShouldHaveCarouselGroupings` | Medium |

---

## B.16 Container/ListingMapleContainerTests.cs

Source: `Search/Algorithm/Container/ListingMapleContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| All 4 tests (`Algorithm_ShouldNotBeNull`, etc.) | Silent-skip anti-pattern: `try { new TheBoxRanker(...) } catch (InvalidOperationException) { Assert.Ignore(...) }` — no assertions in CI |

### Missing Tests
| Test | Priority |
|------|----------|
| `GetAlgorithmName_ShouldReturnBooking_ForBookingCallerType` | High |
| `GetAlgorithmName_ShouldReturnSemListing_ForSemListingFlavor` | High |
| `GetAlgorithmName_ShouldReturnListingAlgoV2_ForListingAlgoV2_NonCustomer` | High |
| `GetAlgorithmName_ShouldAddZDTestPrefix_ForZDTestDirectory` | Medium |
| `Algorithm_ShouldSelectOrganicOnlyBoxRanker_WhenAddSpoToSemFlagOn` | High |
| `Algorithm_ShouldSelectBoxRanker_WhenAddSpoToSemFlagOff` | High |
| `Algorithm_ShouldIncludeMustHaveAvailability_AndUnbookableFilterer_ForBookingCaller` | High |
| `Algorithm_ShouldIncludeProviderDeduper_WhenIsRolledUp` | Medium |
| `Algorithm_ShouldEnableSearchSpecialtyIdGrouping_WhenFlagOn_OffCustomer` | Medium |

---

## B.17 Container/MarketplaceAiSearchAlgoContainerTests.cs

Source: `Search/Algorithm/Container/MarketplaceAiSearchAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Algorithm_ShouldUseCorrectEsIndex` | Tautological — only asserts `NotNullOrEmpty` on EsIndex rather than exact Indexes constant |

### Missing Tests
| Test | Priority |
|------|----------|
| `AvailabilityDays_ShouldReturn56_WhenHasEnhancedAvailabilityFilters` (vs default 14) | High |
| `Algorithm_ShouldRemoveHardAvailabilityFilter_WhenRemoveHardAvailabilityFilterFlagOn` | High |
| `Algorithm_ShouldHandleNullDeviceEmbedding_WithoutThrowing` | High |
| `Algorithm_ShouldHonorMapleV26TestFlag` (dispatch to Maple V26 model) | High |
| `Algorithm_ShouldUseRolledUpPaginators_WhenIsRolledUp` | Medium |
| `Algorithm_ShouldUsePreviewProviderFilterer_WhenIsPreviewMode` | Medium |
| `PostEsReconciliators_ShouldOrderPageVectorSearchEnricher_BeforeEnhancedAvailability` | Medium |
| `Algorithm_ShouldUseExactIndexesConstant_ForProviderLocationsStreaming` (replaces tautological test) | Medium |

---

## B.18 Container/MarketplaceSearchPracticeAlgoContainerTests.cs

Source: `Search/Algorithm/Container/MarketplaceSearchPracticeAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldAppendRankBySuffix_ToName_WhenRankByIsNonDefault` | Medium |
| `PostEsRankers_ShouldContainBoxRanker_InExpectedOrder` | High |
| `PostEsPaginatorScorer_ShouldContainEnchiladaResponseProcessor` | Medium |
| `Algorithm_ShouldRespectConstrainedScoreFusion_RankBy` | High |

---

## B.19 Container/MarketplaceSemAlgoContainerTests.cs

Source: `Search/Algorithm/Container/MarketplaceSemAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldEnableSpecialtyGrouping_WhenFeatureFlagOn` (branch switches ResultGrouper + esBoost=1) | High |
| `Algorithm_ShouldIncludeTopBrowsableDoctorsFlavorFilterers_WhenApplicable` | Medium |
| `Algorithm_ShouldApplyWithLocalityFilters_WhenLocalityPresent` | Medium |
| `Algorithm_ShouldIncludeDoctorTypeSegmenter_InPostEsRankers` | Medium |

---

## B.20 Container/PreviewProviderAlgoContainerTests.cs

Source: `Search/Algorithm/Container/PreviewProviderAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Only 3 tests exist (Constructor, Name, Algorithm not-null) — thin but not irrelevant |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldHaveFourExpectedFilterers` (IsSearchable, HasProfessionalStatementBooster, PreviewProviderSpecialtyIdFilterer, PreviewProviderLocationFilterer) | High |
| `Algorithm_ShouldUseExternallySourcedProvidersStreamingIndex` | High |
| `Algorithm_ShouldUseEsTotalSize300` (private Size300=300) | Medium |
| `Algorithm_ShouldIncludePreviewProviderDistanceRanker_InPostEsRankers` | High |
| `EsBatchSize_ShouldHaveExpectedValue` | Low |

---

## B.21 Container/SubspecialtySearchPracticeAlgoContainerTests.cs

Source: `Search/Algorithm/Container/SubspecialtySearchPracticeAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldHavePostEsPaginatorScorer_WithEnchiladaProcessor` | Medium |
| `Algorithm_ShouldAppendRankBySuffix_ForNonDefaultRankBy` | Medium |
| `Algorithm_ShouldRespectConstrainedScoreFusion_RankBy` | High |
| `ResultGrouper_ShouldHaveHasRequestedAvailability_AndPatientFriendlyGroupings` (positions 2 & 3 not asserted) | Medium |

---

## B.22 Container/YassJrMarketplaceListingAlgoContainerTests.cs

Source: `Search/Algorithm/Container/YassJrMarketplaceListingAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `CustomEsTotalSize_ShouldReturnSize600_WhenBothOffsetAndPageAreNull` (default branch) | Medium |
| `Algorithm_ShouldNotEnableSpecialtyGrouping_ForMentalHealthSpecialty` (negative test) | Medium |
| `Algorithm_ShouldUseRolledUpPaginators_WhenIsRolledUp` | Medium |
| `PostEsRankers_ShouldIncludeDoctorTypeSegmenter` | High |
| `Algorithm_ShouldHaveEsBoost1_WhenSpecialtyGroupingEnabled` | Medium |

---

## B.23 Container/YassJrMarketplaceListingAndPreviewAlgoContainerTests.cs

Source: `Search/Algorithm/Container/YassJrMarketplaceListingAndPreviewAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | 22 comprehensive tests |

### Missing Tests
| Test | Priority |
|------|----------|
| `PostEsPaginatorScorer_ShouldOrderEnchiladaBeforeOtherScorers` | Medium |
| `Algorithm_ShouldApplyCrosslistingSpecialtyIdFilterer_Correctly_ForVirtualLocation` | Medium |
| `Algorithm_ShouldUseInNetworkCarrierGrouping_WhenNotSpecialtyGrouping` | Low |

---

## B.24 Container/YassJrSimilarDoctorsAlgoContainerTests.cs

Source: `Search/Algorithm/Container/YassJrSimilarDoctorsAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ |  |

### Missing Tests
| Test | Priority |
|------|----------|
| `DataRetrievers_ShouldContainAvailabilityRetriever_InsideExternalDataRetriever` | High |
| `ResultDedupers_ShouldContainProviderDeduper_WhenIsRolledUp` (specific deduper type) | Medium |
| `PostEsFilterers_ShouldContainDayAvailabilityFilterer_AndOfficeHoursFilterer` | Medium |
| `EsTotalSize_ShouldBeSize20_AndBatch20` | Low |

---

## B.25 Container/YassJrTopBrowsableDoctorsAlgoContainerTests.cs

Source: `Search/Algorithm/Container/YassJrTopBrowsableDoctorsAlgoContainer.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Only 3 tests — thin but not irrelevant |

### Missing Tests
| Test | Priority |
|------|----------|
| `Algorithm_ShouldHaveProviderSellingPointFilterer_AndCoreFilterers` (HasBudget, CombinedLocation, OnlyInNetworkBookable) | High |
| `Algorithm_ShouldUseGetProviderCarouselPostEsFilterers_Branch` | High |
| `ResultGrouper_ShouldHaveExpectedCarouselGroupings` | Medium |
| `Decorators_ShouldContainRankDecorator_AndDotProvLocMapDecorator` | Medium |
| `EsTotalSize_ShouldBeSize60_AndBatch20` | Low |

---

## B.26 Container/YassJrVaccineAlgoContainerTests.cs

Source: `Search/Algorithm/Container/YassJrVaccineAlgoContainer.cs` (STUB — throws NotImplementedException)

### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Algorithm_ShouldThrowNotImplementedException` | Placeholder test documenting an unimplemented stub; provides zero functional coverage. Should be removed (or replaced) when container is implemented |

### Missing Tests
| Test | Priority |
|------|----------|
| _(none actionable until YassJrVaccineAlgoContainer has a real Algorithm)_ | — |

---

## B.27 Spo/SpoAlgorithmTests.cs

Source: `Search/Algorithm/Spo/SpoAlgorithm.cs`

### Irrelevant Tests
| Test | Reason |
|------|--------|
| _(none)_ | Covers all VisitType branches + EnhancedAvailability |

### Missing Tests
| Test | Priority |
|------|----------|
| `GetAlgo_ShouldApplyExpectedRequestAugmenter` (verify augmenter wiring) | Medium |
| `GetAlgo_ShouldHaveExactFiltererCount_ForEachVisitType` (InPerson/Virtual/default) | Medium |
| `GetAlgo_ShouldUseCommonGroupingsEnhancedAvailability_WhenHasEnhancedFilters` | High |
| `GetAlgo_ShouldUseEsTotalSize1500` | Low |
| `GetAlgo_ShouldReturnDefaultFilterers_WhenVisitTypeIsUnknown` | Medium |

---

## Summary Totals

- **Files analyzed**: 27
- **Irrelevant tests flagged**: 14 (DefaultEnterprise: 9; ListingMaple: 4; YassJrVaccine: 1; MarketplaceAiSearch weak/tautological: noted separately)
- **Missing tests flagged**: 105
- **High-priority missing tests**: 39


---

## Chunk C — Search/Contracts Unit Tests
*Directory: `tests/YassSharp.UnitTests/Search/Contracts/` (21 files).*

### C.1 CarrierIdTests.cs (3 tests)

Source: `src/YassSharp/Search/Constants/CarrierId.cs` — static class with two `const string` values (`ChooseLater = "ic_-1"`, `PayMyself = "ic_-2"`). Declared in same file as `PlanId`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | PayMyself_ShouldHaveCorrectValue | Trivial reflection of source literal. |
| 2 | ChooseLater_ShouldHaveCorrectValue | Trivial reflection of source literal. |
| 3 | PayMyself_ShouldNotEqualChooseLater | Tautology — different string constants can never be equal. No behavior under test. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Values_ShouldFollowIcPrefixContract | That `PayMyself` and `ChooseLater` both begin with `ic_` and have negative numeric suffixes (contract shared with monolith insurance filter). | Medium |
| 2 | Values_AreNotConfusedWithPlanIdValues | Regression guard: `CarrierId.PayMyself` != `PlanId.PayMyself`, since `CarrierId` uses `ic_` and `PlanId` uses `ip_`. | High |

---

### C.2 ConstantsTests.cs (13 tests)

Source: `src/YassSharp/Search/Contracts/Constants.cs` — `ZdHeader`, `ZdApplication`, `DefaultInternalSearchParams`, `RequestFlavor`, `DefaultPageConstant`, `IFacetEnum`, and `FacetB64Enums` static classes.

**Irrelevant Tests:** All 13 tests are literal-value reflections. Every case in this fixture is also duplicated in `DefaultInternalSearchParamsTests.cs`, `DefaultPageConstantTests.cs`, and `FacetB64EnumsTests.cs`. This is the primary source of duplication in the chunk.

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | ZdHeader_Constants_ShouldHaveCorrectValues | Literal reflection of 11 `const string`. Valuable as a single "contract snapshot" but verbose. |
| 2 | ZdApplication_Constants_ShouldHaveCorrectValues | Literal reflection. |
| 3 | DefaultInternalSearchParams_DefaultSearchRadiusInMiles_ShouldBe50 | Duplicated in C.4. |
| 4 | RequestFlavor_Constants_ShouldHaveCorrectValues | Literal reflection. |
| 5 | DefaultPageConstant_Constants_ShouldHaveCorrectValues | Duplicated across all 6 tests in C.5. |
| 6 | FacetB64Enums_Sex_Id_ShouldReturnSexFilter | Duplicated in C.6. |
| 7 | FacetB64Enums_Sex_Constants_ShouldHaveCorrectValues | Duplicated in C.6. |
| 8 | FacetB64Enums_SeesChildren_Id_ShouldReturnSeesChildrenFilter | Duplicated in C.6. |
| 9 | FacetB64Enums_SeesChildren_Constants_ShouldHaveCorrectValues | Duplicated in C.6. |
| 10 | FacetB64Enums_DayAvailability_Id_ShouldReturnDayAvailabilityFilter | Duplicated in C.6. |
| 11 | FacetB64Enums_DayAvailability_Constants_ShouldHaveCorrectValues | Duplicated in C.6. |
| 12 | FacetB64Enums_SpecialHours_* / TimeOfDay_* / DistanceRadius_* / InPersonOrVideoVisit_* | All 11 Facet sub-tests are duplicated in C.6. |
| 13 | (same) | Same. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ZdHeader_AllValues_ShouldBeUniqueAndHttpHeaderCompliant | No two ZdHeader constants collide and all follow HTTP header naming (ASCII, no whitespace). Catches a typo that produces duplicate keys. | High |
| 2 | FacetB64Enums_ValueCaseMatchesBase64Decoded | The "B64" in the name suggests values are base64-encoded facet tokens; test round-trip expectations vs monolith. | High |
| 3 | IFacetEnum_AllNestedClasses_ExposeId | Reflection sweep: every nested class in `FacetB64Enums` exposes a static `Id` property typed `DynamicFilter`, so none is accidentally orphaned from the facet contract. | Medium |
| 4 | FacetB64Enums_SpecialHours_And_TimeOfDay_ShareCommonStrings | `SpecialHours.Before10 == TimeOfDay.Before10 == "before_10_am"` — document-and-lock regression to ensure filter compatibility between the two facets. | Medium |
| 5 | RequestFlavor_AllValues_MatchDocumentedSlugSet | Cross-check against Scala source enum; every documented flavor slug is present. | Medium |

---

### C.3 DayFilterTests.cs (2 tests)

Source: `src/YassSharp/Search/Contracts/DayFilter.cs` — plain enum (`AnyDay, Today, Next3Days, Next7Days, Next14Days, Next30Days`).

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | DayFilter_ShouldBeParsableFromIntegers | This is a C# language guarantee (enum int casts are compiler-generated), not behavior owned by this enum. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DayFilter_JsonRoundTrip_PreservesValue | Since DayFilter appears on `YassRequest`/SearchParams query params, round-trip via `System.Text.Json` with default options — catches silent serialization drift when downstream consumers use numeric vs string form. | High |
| 2 | DayFilter_ParseUnknownInt_DoesNotSilentlyAcceptOutOfRange | Casting `(DayFilter)99` currently succeeds — a guard ensures callers must use `Enum.IsDefined`. | Medium |
| 3 | DayFilter_Values_MatchScalaOrdinals | Regression: ordinals (0..5) align with Scala source since the Scala service may share the wire format. | High |
| 4 | DayFilter_JsonStringEnumConverter_SerializesByName | If any DTO uses `JsonStringEnumConverter`, assert snake_case/PascalCase serialization form matches monolith contract. | High |

---

### C.4 DefaultInternalSearchParamsTests.cs (1 test)

Source: same `Constants.cs` — one const `DefaultSearchRadiusInMiles = 50.0`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | DefaultSearchRadiusInMiles_ShouldBe50 | Trivial literal reflection **and** duplicated in C.2 (ConstantsTests). The entire file is redundant. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DefaultSearchRadius_IsUsedByYassRequestDefault | Integration-style: verify `YassRequest` default distance falls back to this constant when no `distance_radius_miles` query param is supplied. | Medium |

---

### C.5 DefaultPageConstantTests.cs (6 tests)

Source: `Constants.cs` — six `const int` (`Page, PageSize, LogSize, ItemOffset, IvsPageSize, VirtualLocationPageSize`).

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | All six tests | Trivial const literal reflection, and the same assertions exist combined in ConstantsTests (C.2). Could be collapsed into one `TestCase` table. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DefaultPageConstant_AppliedAsYassRequestDefaults | Default `YassRequest.Page == 0`, `PageSize == 10`, etc., actually read from these constants — guards against someone hardcoding a value instead. | High |
| 2 | VirtualLocationPageSize_IsZeroPerContractComment | The source XML comment states "opt out of telehealth locations" — assert this invariant remains `0` via a test that fails explicitly if changed without updating Scala consumers. | Medium |

---

### C.6 FacetB64EnumsTests.cs (26 tests across 7 nested fixtures)

Source: `FacetB64Enums` in `Constants.cs`.

**Irrelevant Tests:** All 26 are literal-value reflections of `const string`. The entire file duplicates content already asserted in C.2 (ConstantsTests).

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–26 | Every `*_ShouldHaveCorrectValue` and `Id_ShouldReturnXxxDynamicFilter` | Reads the source line back out. Low diagnostic value; all 26 fail identically if anyone refactors. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | AllFacets_IdValues_AreDistinctDynamicFilterMembers | No two nested classes share the same `Id`, so facet collision cannot silently happen. | High |
| 2 | DistanceRadius_RadiusValues_MatchGeoDistanceRangeKeys | Every `DistanceRadius.RadiusIn*` constant is a key in `GeoDistanceRange.RangeInMile` — primary contract between the two static classes. | High |
| 3 | DayAvailability_Values_MatchDayFilterStrings | Cross-checks `DayAvailability.Today`/`Next3Days` are parseable representations of `DayFilter.Today`/`Next3Days`. | Medium |
| 4 | InPersonOrVideoVisit_AllValues_AreMutuallyExclusive | Values list is the full domain and doesn't overlap (no typo like `in_person_and_video_visit` collapsing to `in_person`). | Medium |

---

### C.7 GenderTests.cs (2 tests)

Source: plain enum `Gender { Male, Female }`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Gender_ShouldBeParsableFromIntegers | C# language guarantee, not a property of the enum. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Gender_JsonRoundTrip_WithStringConverter | If used in JSON DTOs, ensure stable string form ("Male"/"Female" vs "male"/"female") matches monolith contract. | High |
| 2 | Gender_ModelBinding_AcceptsLowerCaseQueryString | Regression for query-string binding (e.g., `?gender=female`) in API surface. | High |
| 3 | Gender_UndefinedValue_FailsValidation | `(Gender)99` cast must be rejected by a validator (mirrors `SharedMethodValidations` pattern). | Medium |

---

### C.8 GeoDistanceRangeTests.cs (3 tests)

Source: `GeoDistanceRange.RangeInMile` — `Dictionary<string, double>` with 6 entries.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | RangeInMile_ShouldNotBeEmpty | Implied by the ContainKey/Value assertions in tests 1–2. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | RangeInMile_Keys_ExactlyMatchFacetB64DistanceRadiusConstants | Dictionary keys equal the set of `FacetB64Enums.DistanceRadius.*` values — guards the primary cross-contract. | High |
| 2 | RangeInMile_Values_AreMonotonicallyIncreasing | Ordering guard: `to_half_mile < to_1_mile < ... < to_50_mile` so UI sliders can rely on sort-by-value. | High |
| 3 | RangeInMile_IsReadOnly_OrClonedPerCall | Because `public static readonly Dictionary` allows mutation — test documents expectation or reveals dangerous shared state. | High |
| 4 | RangeInMile_HalfMile_IsExactly05_NotRounded | Explicit guard vs `double` rounding drift. | Medium |
| 5 | RangeInMile_Lookup_WithUnknownKey_ReturnsNoEntry | Documents the consumer contract (dictionary, not defaulted). | Low |

---

### C.9 PlanIdTests.cs (3 tests)

Source: `src/YassSharp/Search/Constants/CarrierId.cs` (shared file) — `PlanId.ChooseLater = "ip_-1"`, `PayMyself = "ip_-2"`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | PayMyself_ShouldHaveCorrectValue | Literal reflection. |
| 2 | ChooseLater_ShouldHaveCorrectValue | Literal reflection. |
| 3 | PayMyself_ShouldNotEqualChooseLater | Tautology (different string literals). |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | PlanId_Values_HaveIpPrefix | `ip_` prefix is the plan-ID contract (vs `ic_` for carriers). | High |
| 2 | PlanId_AndCarrierId_SuffixesAreParallel | Both have `-1` (ChooseLater) and `-2` (PayMyself) so downstream integer parsing stays parallel. | Medium |

---

### C.10 RankByTests.cs (2 tests)

Source: `RankBy` enum — includes deprecated `OnlineBookability`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | RankBy_ShouldBeParsableFromIntegers | C# language guarantee. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | RankBy_ConstrainedScoreFusion_HasOrdinal6 | Source has 7 values (0..6) but test only covers 0..5 — `ConstrainedScoreFusion` is untested. | High |
| 2 | RankBy_ObsoleteMember_StillSerializes | Ensure `OnlineBookability` still deserializes from legacy clients (stop-gap for old mobile versions). | High |
| 3 | RankBy_JsonRoundTrip | For each member, JSON round-trip with default and JsonStringEnumConverter. | High |
| 4 | RankBy_UnknownValue_FailsValidation | `(RankBy)99` must be rejected by request validators. | Medium |

---

### C.11 ReflectionHelpersTests.cs (12 tests)

Source: `ReflectionHelpers` — `Snakize`, `GetKnownParams<T>`, `OnlyUsesKnownParams<T>`, `CaseClassToMap<T>`.

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Snakize_WithNull_ReturnsNull | Source short-circuits on null/empty but only empty is covered. | Medium |
| 2 | Snakize_WithSingleLowercaseChar | Edge case: `"a"` → `"a"` (no regex match). | Low |
| 3 | Snakize_WithSingleUppercaseChar | `"A"` → `"a"`. | Low |
| 4 | Snakize_WithConsecutiveUnderscores | Input `"a__b"` — behavior not defined in current coverage. | Medium |
| 5 | GetKnownParams_WithFromQueryAttribute_ReturnsSnakizedName | Not covered at all; primary consumer path (API parameter validation). | High |
| 6 | GetKnownParams_WithExplicitNameInAttribute_UsesProvidedName | `[FromQuery(Name = "foo")]` overrides snakize. | High |
| 7 | GetKnownParams_WithFromRouteAttribute_Included | FromRoute branch uncovered. | High |
| 8 | GetKnownParams_WithNoAttributes_ReturnsEmptySet | Edge case. | Medium |
| 9 | OnlyUsesKnownParams_WithAllKnown_ReturnsSuccess | Uncovered. | High |
| 10 | OnlyUsesKnownParams_WithUnknown_ReturnsErrorListingThem | The primary validation branch — unknown param message format is a public contract. | High |
| 11 | OnlyUsesKnownParams_UnknownParams_AreSortedAlphabetically | Source explicitly calls `OrderBy(k => k)`. | Medium |
| 12 | CaseClassToMap_WithEmptyClass_ReturnsEmptyDictionary | Edge case. | Low |
| 13 | CaseClassToMap_WithInheritedProperties_IncludesThem | Documents reflection scope. | Medium |

---

### C.12 SharedMethodValidationsTests.cs (6 tests)

Source: `SharedMethodValidations.OnlyAllowKnownCallerTypes(CallerType)` + two `NoSpecialtyWildcard` overloads.

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | OnlyAllowKnownCallerTypes_WithUndefinedEnumValue_ReturnsError | `(CallerType)999` — the error-return branch (with "Known caller types: [...]" message) is untested. | High |
| 2 | OnlyAllowKnownCallerTypes_ErrorMessage_EnumeratesAllKnownValues | Contract on the error string so API clients can parse it. | Medium |
| 3 | OnlyAllowKnownCallerTypes_ForEveryDefinedCallerType_ReturnsSuccess | Parametric sweep via `[TestCaseSource]` over `Enum.GetValues<CallerType>()`. | Medium |
| 4 | NoSpecialtyWildcard_StringOverload_WithEmptyString_ReturnsSuccess | Empty string is neither null nor `"*"` — boundary. | Medium |
| 5 | NoSpecialtyWildcard_StringOverload_WithWildcardAndPadding_ReturnsSuccess | `" * "` is not `"*"` (documents exact-match semantics). | Low |
| 6 | NoSpecialtyWildcard_ErrorMessage_MatchesExpectedContract | API clients may match on the error string; lock the exact message. | Medium |

---

### C.13 SimpleHttpRequestTests.cs (6 tests)

Source: `SimpleHttpRequest` at bottom of `YassRequest.cs` — init-only DTO plus `From(HttpRequest)` static factory.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | SimpleHttpRequest_DefaultConstructor_ShouldInitializeEmptyProperties | Trivial auto-property defaults. |
| 2 | SimpleHttpRequest_WithInitProperties_ShouldSetValues | Trivial init-setter round trip. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | From_CapturesRawQueryString | `RawQueryString` is a new (and commented as "firehose logging") property never asserted — regression risk if the factory drops it. | High |
| 2 | From_WithMultiValueQueryParam_JoinsOrFirstWins | `StringValues` with multiple values → `ToString()` joins with commas; lock the chosen behavior (important for `debug` override semantics). | High |
| 3 | From_WithMultiValueHeader_PreservesAllValues | Same for headers (`Accept: a,b`). | High |
| 4 | From_WithNullPathValue_ReturnsEmptyString | Source has `req.Path.Value ?? ""`. | Medium |
| 5 | From_WithNullQueryString_ReturnsEmptyString | Source has `req.QueryString.Value ?? ""`. | Medium |
| 6 | From_PreservesHeaderCasing | HTTP headers are case-insensitive; document chosen casing behavior. | Medium |
| 7 | QueryParams_IsCaseSensitive_ByDefault | Documents whether `?q=x` and `?Q=x` are different. Impacts downstream `YassRequest` parsing. | High |

---

### C.14 VerbosityTests.cs (2 tests)

Source: `Verbosity { None, Summary, Processors, Full }`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Verbosity_ShouldBeParsableFromIntegers | C# language guarantee. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Verbosity_JsonRoundTrip | Used as debug level in YassRequest; ensure wire form is stable. | High |
| 2 | Verbosity_ParsedFromQueryParam_CaseInsensitive | Since `YassRequest` parses `debug=Summary` via `ParseEnumWithEnumMember`, ensure case-insensitive parse. | High |
| 3 | Verbosity_Ordering_ImpliesDetailLevel | None < Summary < Processors < Full ordinal ordering is meaningful (used by comparison checks in debug plumbing). | Medium |

---

### C.15 YassRequestHeaderTests.cs (7 tests)

Source: `YassRequest(SimpleHttpRequest, IMetricRecorder)` — reflection-based query-param parser + header-population.

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Constructor_PopulatesAllZdHeaders | Coverage for `SessionId`, `TrackingId`, `AbOverrides`, `UserAgent`, `ZdApplication`, `OriginUrl`, `ExperimentOverrides`, `CurrentUrl` — none are asserted. | High |
| 2 | Constructor_IsSoftLoggedIn_TrueWhenSoftLoginTokenPresent | Branch not covered (only absent→null). | High |
| 3 | Constructor_IsSoftLoggedIn_FalseWhenTokenEmpty | Empty-string branch of `!string.IsNullOrEmpty`. | High |
| 4 | Constructor_ParsesTimestamp_FromRequestStartTimeHeader | `Timestamp` assignment via `ParseTimestamp`; bad-value branch + missing-header branch. | High |
| 5 | Constructor_ParsesDirectoryId_FromPath | Path `/search/v1/directories/-1/...` → DirectoryId = -1; covers regex-like split parsing. | High |
| 6 | Constructor_FallsBackToDirectoryIdsZocdoc_WhenPathMissingDirectories | Default branch when `directories` not in path. | High |
| 7 | Constructor_SetsExplicitlySetParams_LowercasedKeysOnly | Asserts lowercasing behavior (`.ToLowerInvariant()`) — used by downstream validation. | High |
| 8 | Constructor_CapturesRawDebugValue_EvenWhenInvalid | `RawDebugValue` stores unparseable values for validation error messages — never tested. | High |
| 9 | Constructor_CapturesRawCallerTypeValue_EvenWhenInvalid | Same for caller_type. | High |
| 10 | Constructor_WithEnumQueryParam_ParsesViaEnumMemberAttribute | `ParseEnumWithEnumMemberDebug` path (e.g., `search_type=specialty` → `SearchType.Specialty`). | High |
| 11 | Constructor_WithBoolQueryParam_Accepts1AsTrue | `bool.TryParse` fallback to `value == "1"`. | High |
| 12 | Constructor_WithMalformedNumericQueryParam_LeavesDefault | Invalid int/long/decimal shouldn't throw. | High |
| 13 | Constructor_EmptyStringQueryParam_IgnoresSetter | `string.IsNullOrEmpty(value)` branch is `continue`. | Medium |
| 14 | Constructor_WithMetricRecorder_AssignsIt | `MetricRecorder` property set. | Medium |
| 15 | CloneForPreview_DeepCopiesExplicitlySetParams | Regression test that the HashSet isn't shared (present method, no coverage). | High |
| 16 | Constructor_WithDirectoryIdPathAndNonInteger_IgnoresInvalidSegment | `int.TryParse` branch. | Medium |

---

### C.16 ProvLocResponseTests.cs (10 tests)

Source: `ProvLocResponse` + `FromResponseInfo` (70+ line factory).

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | ProvLocResponse_Properties_ShouldBeSettable | Auto-property round-trip for 7 properties; little value. The property list is also non-exhaustive. |
| 4 | ProvLocResponse_FromResponseInfo_WithClock_ShouldUseProvidedClock | Only verifies `clock.NowOffset` was invoked — doesn't test what `now` is used for (spend-lock status on map dots). Weak coverage. |
| 5 | ProvLocResponse_FromResponseInfo_WithoutClock_ShouldUseUtcNow | Assertion `before.Should().BeBefore(after)` is unconditionally true and doesn't reference `result`. Meaningless. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | FromResponseInfo_MapsResultsToProviderLocations | Scala parity: `responseInfo.Results.Select(ProviderLocation.FromProvLocResult)` populates `ProviderLocations`. Core business logic untested. | High |
| 2 | FromResponseInfo_MapsCanoeResultsToHighlightedProviderLocations | Canoe → highlighted list mapping. | High |
| 3 | FromResponseInfo_PopulatesSpoAdsResponse | `ResponseSpoAdsResponse.FromInternal` wiring — critical for ads contract. | High |
| 4 | FromResponseInfo_WithBrandAffiliatedAggregation_SetsBrandCounts | `GetBrandCounts` branch: `brand`/`nonBrand` breakdown with `Math.Max(..., 0)` guard. | High |
| 5 | FromResponseInfo_WithoutBrandAffiliatedAggregation_LeavesBrandCountsEmpty | Negative branch. | High |
| 6 | FromResponseInfo_AggregatedHits_UsesFilteredTotalHitsWhenPresent | `FilteredTotalHits ?? TotalHits` fallback. | High |
| 7 | FromResponseInfo_TotalProvidersAggregatedHits_WithInNetwork_CalculatesOON | inNetwork + distinct → OON derivation. | High |
| 8 | FromResponseInfo_MapDots_WithDistanceMi_RoundsTo12Digits | `Math.Round(dot.DistanceMi.Value, 12, MidpointRounding.AwayFromZero)` — numeric contract. | High |
| 9 | FromResponseInfo_MapDots_SpendLockStatus_UsesClockNow | Passes `now` into `CalculateSpendLockStatus`; this is the behavior test missing from the weak Test #4. | High |
| 10 | FromResponseInfo_WithRolledUp_IncludesAdditionalProvLocs | `request.IsRolledUp == true` path vs false/null path. | High |
| 11 | FromResponseInfo_WithAddInsuranceSettingsFlag_IncludesInsuranceSettingsOnAddl | AB flag branch on `AdditionalProviderLocations.InsuranceSettings`. | High |
| 12 | FromResponseInfo_MapsSearchOriginCoordinate | `SearchOrigin != null` → wraps lat/lon. | High |
| 13 | FromResponseInfo_WithGroupCounts_PassesThrough | Pass-through field. | Medium |
| 14 | FromResponseInfo_Facets_NullWhenNoRequestedFacets_NonNullWhenRequested | `GetFacets` branching. | High |
| 15 | JsonRoundTrip_WithAllPopulatedFields_MatchesWireContract | Serialize/deserialize via System.Text.Json and assert every `JsonPropertyName` key is present (`provider_locations`, `highlighted_provider_locations`, `spo_ads_response`, `total_hits`, `aggregated_hits`, `provider_locations_map_dots`, `government_insurances_blocked`, `nearest_zip_code`, `nearest_state`, `facets`, `debug`, `search_origin`, `total_providers_count`, `total_providers_aggregated_hits`, `brand_counts`, `group_counts`). | High |
| 16 | JsonSerialization_OmitsNullOptionalFields | Null `Facets`, `Debug`, `GroupCounts` etc. serialization contract. | High |
| 17 | JsonDeserialization_WithMissingOptionalFields_LeavesDefaults | Forward-compat parsing. | High |

---

### C.17 SearchTypeExtensionsTests.cs (2 tests)

Source: `SearchTypeExtensions.ToStringValue(SearchType)` with `default → throw`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | ToStringValue_WithSpecialty_ShouldReturnSpecialty | Duplicated in C.18 (SearchTypeTests) test 2. |
| 2 | ToStringValue_WithProcedure_ShouldReturnProcedure | Duplicated in C.18 test 3. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ToStringValue_WithUndefinedValue_ThrowsArgumentOutOfRange | `default` switch arm — covered in C.18 but missing here (and this is the extensions-specific fixture). | High |
| 2 | ToStringValue_ReturnsLowercase_MatchingEnumMemberAttribute | Guarantees the extension method stays in sync with `[EnumMember(Value = "...")]` on the enum. | High |

---

### C.18 SearchTypeTests.cs (4 tests)

Source: `SearchType { Specialty, Procedure }` + `[TypeConverter(EnumMemberTypeConverter<SearchType>)]` + `[EnumMember(Value = "specialty" / "procedure")]`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | SearchType_ShouldHaveExpectedValues | Literal ordinal reflection. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | SearchType_TypeConverter_ConvertsFromString | Test the `EnumMemberTypeConverter<SearchType>` registration — route/query binding depends on it. | High |
| 2 | SearchType_EnumMemberAttribute_DrivesJsonSerialization | Serializer honors `[EnumMember(Value="specialty")]` not PascalCase. | High |
| 3 | SearchType_ParseFromLowercaseWire_Succeeds | `"specialty"` → `SearchType.Specialty` (round-trip from the Scala wire). | High |
| 4 | SearchType_ParseFromPascalCase_FailsOrSucceedsByContract | Document whether `"Specialty"` also parses — prevents silent contract drift. | Medium |

---

### C.19 SpecialSearchDistanceModeTests.cs (2 tests)

Source: `SpecialSearchDistanceMode { NoSpecialMode, Tier1DistanceIgnored, Tier2Polygon, ZipCode }`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | SpecialSearchDistanceMode_ShouldBeParsableFromIntegers | C# language guarantee. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip | Used as query param on YassRequest. | High |
| 2 | ParseFromQueryParam_CaseInsensitive | `YassRequest` enum parser case-insensitivity. | High |
| 3 | UnknownOrdinal_DoesNotSilentlyBind | `(SpecialSearchDistanceMode)99` rejected. | Medium |

---

### C.20 TimeFilterTests.cs (2 tests)

Source: `TimeFilter { AnyTime, Before10AM, After5PM, Before10AMOrAfter5PM }`.

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | TimeFilter_ShouldBeParsableFromIntegers | C# language guarantee. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | TimeFilter_JsonRoundTrip | Wire-format stability across Scala/monolith boundary. | High |
| 2 | TimeFilter_Values_CorrespondToFacetB64EnumsTimeOfDay | Cross-check: AnyTime ~ no filter; Before10AM ~ `before_10_am`; After5PM ~ `after_5_pm`; Before10AMOrAfter5PM has no single facet counterpart — document that. | High |
| 3 | TimeFilter_OrdinalsMatchScalaWire | Parity guard for ordinal-serialized clients. | High |

---

### C.21 SpoAdsResponseTests.cs (12 tests)

Source: `SpoAdsResponse`, `AdDecision`, `TelAdDecision`, `AdType`, `SpoProviderQualities`, `AdditionalProviderLocation`, `BannerInfo`. All use `[JsonPropertyName]` with **camelCase** keys (a deliberate Scala-compat deviation from the rest of the response which uses snake_case).

**Irrelevant Tests:** All 12 are trivial constructor-default/auto-property round-trips. No serialization is tested, which is the actual risk surface for these DTOs.

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | SpoAdsResponse_DefaultConstructor_ShouldInitializeEmptyCollections | Auto-property defaults only. |
| 2 | SpoAdsResponse_Properties_ShouldBeSettable | Auto-property setter. |
| 3 | AdDecision_DefaultConstructor_ShouldInitializeEmptyStrings | Auto-property defaults. |
| 4 | AdDecision_Properties_ShouldBeSettable | Auto-property setter; large but zero-logic. |
| 5 | TelAdDecision_DefaultConstructor_ShouldInitializeEmptyStrings | Auto-property defaults. |
| 6 | TelAdDecision_Properties_ShouldBeSettable | Auto-property setter. |
| 7 | AdType_Enum_ShouldHaveExpectedValues | Literal reflection (`AdType.Sponsored.Should().Be(AdType.Sponsored)` is a tautology). |
| 8 | SpoProviderQualities_DefaultConstructor_ShouldInitializeAllFalse | Auto-property defaults. |
| 9 | SpoProviderQualities_Properties_ShouldBeSettable | Auto-property setter. |
| 10 | AdditionalProviderLocation_DefaultConstructor_ShouldInitializeEmptyStrings | Auto-property defaults. |
| 11 | AdditionalProviderLocation_Properties_ShouldBeSettable | Auto-property setter. |
| 12 | BannerInfo_DefaultConstructor_ShouldInitializeEmptyStrings + BannerInfo_Properties_ShouldBeSettable | Auto-property round-trip. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | SpoAdsResponse_JsonRoundTrip_UsesCamelCaseKeys | Comment explicitly says camelCase (not snake_case) — wire contract with Scala. Serialize and assert raw JSON contains `adRequestId`, `adDecisions`, `telAdDecisions`. | High |
| 2 | AdDecision_JsonRoundTrip_AllFields | Every `[JsonPropertyName]` (rank, adDecisionId, decisionToken, providerId, locationId, adType, cost, expectedValue, acceptsInsurance, distanceMi, displayedSpecialty, providerQualities, providerBadges, displayOnPageRank, insuranceSettings, practiceDetails, isVirtualLocation, additionalProviderLocations, isHybrid, isPatientChoiceBadgeAssigned, bannerInfo, hasRequestedAvailability, summary). | High |
| 3 | AdDecision_JsonDeserialize_MissingNullableFields_DoesNotThrow | Forward-compat with older Scala producers. | High |
| 4 | AdType_JsonStringEnumConverter_SerializesAsName | `[JsonConverter(typeof(JsonStringEnumConverter))]` on AdType — assert wire form is `"Sponsored"` / `"Telehealth"` (not 0/1). | High |
| 5 | AdType_Deserialize_LowercaseVariant_Behavior | Document whether `"sponsored"` deserializes; `JsonStringEnumConverter` is case-insensitive by default. | High |
| 6 | AdType_Deserialize_UnknownValue_Throws | Safety check against silent enum corruption. | Medium |
| 7 | TelAdDecision_Rank_IsLongNotInt | `Rank` is `long` on TelAdDecision but `int` on AdDecision — easy regression. Serialize a > Int32.Max value. | High |
| 8 | SpoProviderQualities_JsonKeys_ArePascalCase | Unusual: this class uses `[JsonPropertyName("NewPatientAppointments")]` (PascalCase) while sibling classes use camelCase. Lock that contract. | High |
| 9 | AdDecision_Cost_SerializesAsDecimalNotScientific | Decimal JSON serialization contract — currency-like fields shouldn't flip to scientific notation. | Medium |
| 10 | SpoAdsResponse_EmptyAdDecisions_SerializesAsEmptyArrayNotNull | Contract: consumers expect `[]` not `null`. | High |
| 11 | BannerInfo_Priority_DefaultsTo0_ButZeroIsAlsoValid | Distinguish default from explicit value; document if there's a sentinel. | Low |
| 12 | AdditionalProviderLocation_InsuranceSettings_OptionalWiring | Null vs populated branch — cross-check with ProvLocResponse mapping. | Medium |

---


---

## Chunk D — Search/Es Unit Tests
*Directory: `tests/YassSharp.UnitTests/Search/Es/` — ES query builders, filterers, scorers, response/client wrappers (74 files).*

### D.1 Es7ClientPreferenceTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | BuildEsPreference_WithNodeIdContainingColon_ShouldEscape | Preference parser safety vs ES reserved chars (`:`, `,`) so CI node IDs with unusual chars route correctly | High |
| 2 | BuildEsPreference_WithMultipleNodeIdsCsv_ShouldHandle | Verify comma-separated node list routing if ever used (or reject) | Medium |
| 3 | BuildEsPreference_WithVeryLongNodeId_ShouldTruncateOrReject | Avoid ES URL overflow on malformed input | Low |
| 4 | BuildEsPreference_WithTabOrNewlineInNodeId_ShouldReturnNull | Control-char rejection (currently whitespace tested but only spaces) | Medium |
| 5 | BuildEsPreference_WithPlusSignInNodeId_ShouldEscape | Ensure URL-unsafe chars don't break the preference header | Medium |

---

### D.2 Es7ClientTracingTests.cs (6 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ExecuteSearch_Returns5xxFromEs_SpanTaggedWithStatusCode | Partial cluster failure (500/503) semantics | High |
| 2 | ExecuteSearch_WithPartialShardFailure_SetsFailedShardsTag | `_shards.failed > 0` should be reflected in span tag | High |
| 3 | ExecuteSearch_TimedOutTrue_ShouldSetTimeoutTag | ES `timed_out: true` in body (but HTTP 200) — silent degradation today | High |
| 4 | ExecuteSearch_WithEmptyHits_ReturnsZeroHitsSpan | Verify total_hits=0 tagged correctly | Medium |
| 5 | ExecuteSearch_MalformedJson_SpanStatusError | Broken JSON body should set span.error | High |
| 6 | ExecuteCount_OnError_SetsSpanStatusToError | Count-path error mirroring existing search error test | Medium |
| 7 | ExecuteSearchWithPagination_WithReplayPreference_TagsReplayNode | Verify replay_node tag is present when preference is passed | High |

---

### D.3 Es7StatsDClientTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ExecuteSearchWithPagination_MalformedPreferencePrefix_DoesNotRecord | Confirm only prefix `_only_nodes:` triggers metric (not `_shards:` or arbitrary) | High |
| 2 | ExecuteSearchWithPagination_WithExceptionFromClient_MetricsStillEmittedForErrorPath | Error-case latency/count metric parity with Scala | High |
| 3 | ExecuteSearchWithPagination_MeasuresLatencyMetric | Current tests only verify replay counter; main latency histogram not asserted | High |
| 4 | ExecuteAggregationSearch_LargeTookMs_EmitsTookMetric | Ensure tookMs/parseTimeMs metrics are emitted to DD | Medium |
| 5 | ExecuteSearchWithPagination_WithNodeIdContainingTagChars_SanitizesTag | node_id may contain `:` which is DD tag separator | Medium |

---

### D.4 IndexesTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | ProviderLocationsStreaming_ShouldHaveCorrectValue | Asserts a string constant equals itself — tautology, no behaviour tested |
| 2 | ExternallySourcedProvidersStreaming_ShouldHaveCorrectValue | Same tautology |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Indexes_MatchDeployedIndexNames | Validate against a registry/config source rather than self-referencing constant | High |
| 2 | Indexes_NoTrailingWhitespaceOrCase | Catch accidental whitespace/casing drift that routes to wrong index | Medium |

---

### D.5 QueryableFieldMappingTests.cs (9 tests)

**Irrelevant Tests:** None — all tests are relevant; schema drift is a real QA risk.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | FilterToEsField_EveryDynamicFilterEnum_HasMapping | Ensures no DynamicFilter case silently missing from FilterToEsField (schema drift) | High |
| 2 | FilterToEsField_NoDuplicateKeyValues | Guards against two DynamicFilters mapping to same ES field | High |
| 3 | ExcludeFilterToEsField_NotEmpty_AndContainsNoPII | Confirm curated exclude list is intentional, not a typo | Medium |
| 4 | FieldNames_NoFieldContainsUnencodedDot_ExceptKnownNested | Catch typos where `.raw` / `.monolithId` nested syntax is missing | High |
| 5 | Fields_AllFieldsPresent_InEsMappingYaml | Compare names against the deployed ES mapping fixture | High |
| 6 | FilterToEsField_WithNullSearchParams_DoesNotThrow | Lambda resolution under null request | Medium |

---

### D.6 QueryAugmentersTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Indexes_ProviderLocationsStreaming_ShouldReturnCorrectValue | Duplicated from IndexesTests.cs and belongs there (cross-file drift) |
| 2 | Indexes_ExternallySourcedProvidersStreaming_ShouldReturnCorrectValue | Same — belongs in IndexesTests.cs |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | YassPayloadAugmenter_Augment_AddsPayloadField | Behavioural test for the augmenter's actual query mutation | High |
| 2 | YassPayloadAugmenter_Augment_IdempotentIfCalledTwice | Double-augment regression | Medium |
| 3 | QueryAugmenters_RegistryContainsAllAugmenters | Confirm registry completeness (drift risk) | Medium |

---

### D.7 YassPayloadAugmenterTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Instance_ShouldImplementIQueryAugmenter | Type-check tautology (compiler-guaranteed); no behavior |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Augment_WithEmptyPayload_AddsDefault | Verify the stored_fields / source augmentation actually flips the query | High |
| 2 | Augment_WithExistingPayloadField_DoesNotDuplicate | Idempotency | Medium |
| 3 | Augment_WithNullRequest_DoesNotThrow | Null-safety | Medium |

---

### D.8 FunctionScorerTests.cs (4 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | MmDistanceFunctionScore_Score_ShouldReturnNull | Asserts stub returns null — adds no value if that's the whole method |
| 2 | MarketplaceRandomScorer_Score_ShouldReturnNull | Same stub-result assertion |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | MmDistanceFunctionScore_Score_WithLocation_ReturnsGaussDecayFunction | Actual scoring function shape (origin, scale, offset) | High |
| 2 | MarketplaceRandomScorer_Score_UsesRequestIdAsSeed | Reproducibility across retries | High |
| 3 | MarketplaceRandomScorer_Score_WithoutSeed_StillDeterministic | Fallback seed behavior | Medium |
| 4 | FunctionScorer_Compose_MultipleScorers_BlendsCorrectly | Function score composition (sum/multiply) | High |
| 5 | MmDistanceFunctionScore_Score_WithZeroRadius_DoesNotThrow | Edge case on distance 0 | Medium |

---

### D.9 AcceptsNewPatientsFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithAcceptsNewPatientsTrue_ButNullCarrier_DoesNotAddCarrierValue | Guard against "carrier1-plan1" concat on null inputs | High |
| 2 | Filter_WithCarrierButNullPlan_ProducesValidKey | Partial insurance info path | High |
| 3 | Filter_WithCarrierContainingDash_KeyStillParseable | Carrier-plan key format collision | Medium |

---

### D.10 BookabilityFiltererTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Filter_ShouldAddShouldClause | Over-stubbed — asserts `AddShould` with `It.IsAny<string>()` for field name, only asserting value="true". Doesn't verify the actual ES field name. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_ShouldTargetIsBookableField | Pin the field name (`IsBookable`) so refactors don't silently change ES field | High |
| 2 | Filter_WithBookabilityVariants_ProducesCorrectClause | Exercise any branches based on SearchParams flags | Medium |

---

### D.11 CanoeProvLocFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithDuplicateIdsInArray_DeduplicatesBeforeOr | Efficiency/correctness — duplicates in terms list | Medium |
| 2 | Filter_WithOver1024Ids_HandlesEsTermsLimit | ES terms query has default 65536 ceiling but partitioned clusters may differ; test chunking | High |
| 3 | Filter_WithNullValueInArray_DoesNotThrow | Null entries inside array | Medium |

---

### D.12 CombinedLocationFiltererTests.cs (15 tests)

**Irrelevant Tests:** None — comprehensive priority-ordering coverage.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithVisitTypeVirtualVisit_ExcludesPhysicalClause | VisitType branch coverage (skipVisitType=false path) | High |
| 2 | Filter_WithVisitTypeInPersonVisit_ExcludesVirtualClause | Mirror of above | High |
| 3 | Filter_WithFacetInPersonOrVideoVisit_IncludesBoth | skipVisitType path coverage | High |
| 4 | Filter_WithBothPhysicalAndVirtual_AddsBoolShould | Verify OR/SHOULD structure when both clauses present | High |
| 5 | Filter_WithBoxLocation_UsesGeoBoundingBoxInsteadOfDistance | Bounding box branch in GetPhysicalLocationQueryBuilder | High |
| 6 | Filter_WithCoordinateWithZip_UsesDistanceQuery | CoordinateWithZip switch case | High |
| 7 | Filter_WithVirtualOnly_AddsStateAndIsVirtualTrue | Verify virtual clause composition | High |
| 8 | GetRadiusInMiles_WithNegativeOverride_ClampsToZeroOrDefault | Defensive boundary | Medium |
| 9 | GetRadiusInMiles_WithExtremelyLargeRadius_DoesNotCrashGeoQuery | Radius > earth's diameter | Low |

---

### D.13 CrosslistingSpecialtyIdFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithSpecialtyIdEqualsPcpId_UsesPcpBranch | PCP-specific branch if present | High |
| 2 | Filter_WithExistingSpecialtyFilterInRequest_DoesNotDoubleApply | Idempotency guard | Medium |
| 3 | Filter_WithSpecialtyIdNotMonolithified_StillFilters | sp_ prefix stripping via Monolithify | High |

---

### D.14 DateOfServiceFiltererTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | Filter_ShouldReturnQueryBuilder | Trivial stub test — only asserts `return qb`, no real filter behavior verified |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithDateOfServiceSet_AddsRangeFilter | Actual date filtering behavior (assuming filterer mutates qb) | High |
| 2 | Filter_WithDateOfServiceInPast_AddsOrRejects | Business rule: past DoS | High |
| 3 | Filter_WithDateOfServiceNull_NoopShouldNotMutate | Confirm no side-effects on null | Medium |
| 4 | Filter_WithFarFutureDateOfService_StillAddsFilter | Boundary for future DoS | Medium |

---

### D.15 DirectoryFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithNullDirectoryId_DoesNotAddFilter | Missing negative path | High |
| 2 | Filter_WithDirectoryZDTest_RoutesCorrectly | Test-directory routing | Medium |
| 3 | Filter_WithUnknownDirectoryId_DoesNotThrow | Defensive | Medium |

---

### D.16 EsFilterersTests.cs (8 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–8 | All 8 singleton + fieldname tests | Smoke-level — only confirms singleton pattern & field-name strings (duplicated across 15 other Filterer*Tests files) |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | SpecialtyIdFilterer_Filter_AppliesSpecialtyCorrectly | Actual filter behavior (stub-only today) | High |
| 2 | StateFilterer_Filter_AppliesStateCorrectly | Actual filter behavior (stub-only today) | High |
| 3 | ZipCodeFilterer_Filter_AppliesZipCorrectly | Actual filter behavior (stub-only today) | High |
| 4 | DateOfServiceFilterer_Filter_AppliesDateCorrectly | Actual filter behavior | High |

---

### D.17 ExactSpecialtyIdFiltererTests.cs (4 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 4 | Filter_WithEmptySpecialtyId_ShouldAddFilter | Arguably wrong behavior — filtering by empty string will match zero docs; test codifies a likely bug |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithSpPrefixedId_StripsPrefix | Monolithify interaction | High |
| 2 | Filter_WithSpecialtyIdContainingSpaces_TrimsOrRejects | Defensive against bad input | Medium |

---

### D.18 ExactStateFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithLowercaseState_NormalizesCasing | ES field casing sensitivity | High |
| 2 | Filter_WithNonUsState_StillFilters | Guard against silent dropping of non-US | Medium |
| 3 | Filter_WithInvalidStateCode_DoesNotThrow | Defensive | Medium |

---

### D.19 ExcludedSpecialtyFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithExcludedIdDuplicated_AddsOnlyOnce | Dedup guard | Medium |
| 2 | Filter_WithSpPrefixedIdsInArray_StripsEach | Monolithify interaction | High |
| 3 | Filter_WithLargeArrayOver1024_ChunksOrRejects | ES terms limit | Medium |

---

### D.20 FiltererBookabilityTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | All 6 singleton+fieldname tests | Smoke-level; duplicated from dedicated BookabilityFiltererTests/AcceptsNewPatients/LocationActive files — increases surface area without adding coverage |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate into dedicated test files) | Remove duplication | — |

---

### D.21 FiltererCrosslistingPartnerTests.cs (8 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–8 | All 8 tests | Duplicated smoke tests of singleton/FieldName already covered in the dedicated *FiltererTests files |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.22 FiltererEvenMoreTests.cs (8 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–8 | All 8 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.23 FiltererFinalTests.cs (7 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–7 | All 7 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | CombinedLocationFilterer_WithSearchRadius_StoresAndUsesRadius | Test that covered constructor arg actually influences Filter output | Medium |

---

### D.24 FiltererIdTests.cs (7 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–7 | All 7 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.25 FiltererInstituteDirectoryTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | All 6 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.26 FiltererLanguageGenderTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | All 6 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.27 FiltererLastTests.cs (4 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–4 | All 4 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.28 FiltererMoreTests.cs (8 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–8 | All 8 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.29 FiltererPreviewTests.cs (4 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–4 | All 4 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.30 FiltererRemainingTests.cs (8 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | First 6 tests | Duplicated singleton/FieldName smoke tests |
| 7 | InputFilterer_FieldName_ShouldReturnProvidedFieldName | Overlap with InputFiltererTests |
| 8 | InputFilterer_WithEmptyValues_ShouldReturnEmptyArray | Asserts only FieldName not empty-behaviour |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.31 FiltererSellingPointTests.cs (5 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–5 | All 5 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.32 FiltererSpoCanoeTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | All 6 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.33 FiltererTests.cs (4 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–4 | All 4 tests | Duplicated singleton/FieldName smoke tests for HasAvailability / MustHaveAvailability |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | HasAvailabilityFilterer_Filter_AppliesFilter | No Filter behavior currently tested | High |
| 2 | MustHaveAvailabilityFilterer_Filter_WhenRequireAvailability | Distinguish from HasAvailability | High |

---

### D.34 FiltererVirtualRecommendedTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1–6 | All 6 tests | Duplicated singleton/FieldName smoke tests |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | (None — consolidate) | Remove duplication | — |

---

### D.35 HasBudgetFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithNonCovidProcedureId_AddsFilter | Mirror of covid negative path | High |
| 2 | Filter_WithCovidProcedureIdAsVariantString_StillExempts | Confirm "5028" exact match vs "5028.0" etc. | High |
| 3 | Filter_DateRangeFilterValuesArePassedCorrectly | Budget date range verification | High |

---

### D.36 HasSpoBudgetFiltererTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Filter_ShouldAddFilterForTrue | Uses `It.IsAny<string>()` for field — doesn't verify the `HasSpoBudgetV2` field name is targeted |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_AssertsHasSpoBudgetV2FieldName | Pin ES field for SPO budget | High |
| 2 | Filter_WithSpoDisabled_DoesNotApply | Branch coverage if conditional | Medium |

---

### D.37 HighlyRecommendedFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithHighlyRecommendedDoctorsFlavor_AndNoSpecialty_StillFilters | Flavor behaviour independent of specialty | Medium |
| 2 | Filter_WithMultipleFlavors_OnlyHRAppliesFilter | Confirm strictness of flavor match | Medium |

---

### D.38 IdFixersTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | Monolithify_WithMultipleSpPrefixes_ShouldRemoveAll | Codifies questionable behavior — "sp_sp_123" → "123" relies on `Replace("sp_", "")` which would also break IDs like `"_sp_abc"`; is this intended? |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Monolithify_WithNullId_ThrowsOrReturnsNull | Null-safety | High |
| 2 | Monolithify_WithSpInTheMiddle_DoesNotStripFromMiddle | Current `.Replace` would break "abc_sp_def" — document/fix | High |
| 3 | Cloudify_WithNullId_ThrowsOrReturnsNull | Null-safety | High |
| 4 | Monolithify_WithEmptyString_ReturnsEmpty | Edge case | Medium |
| 5 | Cloudify_Monolithify_Roundtrip_Consistent | Inverse property | Medium |

---

### D.39 InNetworkOnlyStatusFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithNullCarrierId_NoOp | Null branch explicit coverage | High |
| 2 | Filter_WithUnknownCarrier_AppliesStandardOrPath | Unknown carrier fallback | Medium |
| 3 | Filter_WithOrQueriesStructure_IncludesInNetworkAndBookable | Assert the nested bool structure, not just that it's called | High |

---

### D.40 InputFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithExcludedFieldAndMultipleValues_DoesNotAddTerms | Covers excluded + multi-value | Medium |
| 2 | Filter_WithEnhancedAvailabilityField_Skipped | Per ExcludeFilterToEsField list — integration with QueryableFieldMapping | High |
| 3 | Filter_WithCaseSensitiveFieldMatch | Exclusion list exact-match semantics | Medium |

---

### D.41 InstituteFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithMultipleInstituteIds_HandlesArrayOrFailsExpectedly | If SearchParams ever carries multiple | Medium |
| 2 | Filter_WithInstituteIdCasing_NormalizedOrNot | Field uses `.raw` so case-sensitive — document | Medium |

---

### D.42 InsuranceFiltererTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Instance_ShouldBeSingleton | Smoke |
| 2 | FieldName_ShouldReturnInsurancePlan | Smoke — no Filter behavior |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithCarrierAndPlan_AddsInsuranceFilter | Core behavior (currently 0 coverage!) | High |
| 2 | Filter_WithPayMyself_NoFilter | Special-carrier branch | High |
| 3 | Filter_WithChooseLater_NoFilter | Special-carrier branch | High |
| 4 | Filter_WithCarrierOnly_UsesCarrierFallback | Plan-less path | High |
| 5 | Filter_WithInsuranceFiltererUtils_Integration | Shared util integration | Medium |

---

### D.43 IsNotVirtualLocationFiltererTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Filter_ShouldAddOrQueries | Only asserts `AddFilterWithOrQueries` was called; doesn't inspect internal queries |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_OrQueries_IncludeFalseAndMissingField | Verify both branches (IsVirtualLocation=false OR field missing) | High |
| 2 | Filter_WithExplicitlyVirtualLocation_ExcludesDoc | Real behavior parity with prod | High |

---

### D.44 IsPartnerSitesMappedFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithExcludeTrue_PassesExactlyTrue_NotIsAny | Pin the boolean value (currently only `It.IsAny<bool>`) | High |

---

### D.45 IsSearchableFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_MustNotTargetsIsSearchableField | Assert actual field name in call, not `It.IsAny<string>()` | High |

---

### D.46 IsVirtualLocationFiltererTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Filter_ShouldAddFilterForTrue | Field name `It.IsAny<string>()` — doesn't pin `IsVirtualLocation` |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_TargetsIsVirtualLocationFieldName | Pin field | High |
| 2 | Filter_WithRequestParamOverride_DoesNotChange | If request carries toggle | Medium |

---

### D.47 IVSFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_VirtualLocationTypeFieldName_ExplicitlyAsserted | Pin field rather than `It.IsAny<string>()` | High |
| 2 | Filter_WithZdVvVariantString_MatchesExactly | Case/whitespace sensitivity of "ZocdocVideoVisit" | Medium |

---

### D.48 LanguageFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithLanguageIdZero_HandlesCorrectly | 0 is falsy in many libs but valid ID | Medium |
| 2 | Filter_WithNegativeLanguageId_DoesNotAddFilter | Defensive | Low |

---

### D.49 LocationActiveFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_MustNotFieldNameAssertedExplicitly | Pin IsLocationActive name | High |

---

### D.50 LocationFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithLatAboveRange_90_DoesNotThrow | Boundary (90 N pole) | High |
| 2 | Filter_WithLatBelowNeg90_RejectsOrClamps | Boundary (-90 S pole) | High |
| 3 | Filter_WithLon180OrNeg180_ValidInput | Antimeridian | High |
| 4 | Filter_WithZeroZeroCoordinates_DoesNotSilentlyUse | (0,0) as "null-in-disguise" null island | High |
| 5 | Filter_WithDistanceRadiusZero_Handled | Zero radius degenerate | Medium |
| 6 | Filter_WithDistanceRadiusVeryLarge_HandledOrClamped | > earth diameter | Medium |
| 7 | Filter_DefaultRadius_MatchesDefaultInternalSearchParams | Ensure default not hard-coded elsewhere | Medium |

---

### D.51 LocationIdFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithLocationIdContainingDot_QueriesRawField | Field is `LocationId.raw` — verify correct subfield used | High |

---

### D.52 MatchingCityFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithBothCityAndBorough_UsesCityFirstOnly | Priority ordering | High |
| 2 | Filter_WithCityContainingAccents_MatchesNormalized | International city names | Medium |

---

### D.53 MatchingStateFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithEmptyState_DoesNotAddShould | Empty string vs null parity | Medium |
| 2 | Filter_WithLowercaseStateCode_CasingBehavior | ES field is case-sensitive | High |

---

### D.54 MatchingZipFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithZipPlus4_NormalizesToBase5 | "10001-1234" handling | High |
| 2 | Filter_WithNonNumericPostalCode_CA_UKFormat | Intl postal codes | Medium |

---

### D.55 MixedModeSpecialtyIdFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_MixedModeWithProcedure_BehavesDifferentlyFromExact | Distinguish MixedMode from Exact/Crosslisting | High |
| 2 | Filter_WithSpPrefixedSpecialtyId_StripsPrefix | Monolithify | High |

---

### D.56 MustHaveAvailabilityFiltererTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | Filter_ShouldAddMustForTrue | `It.IsAny<string>()` for field name — doesn't pin `Availability.HasAvailability` |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_TargetsAvailabilityHasAvailabilityField | Pin field | High |
| 2 | Filter_DistinctFromHasAvailabilityFilterer | Document different clause type (must vs filter) | Medium |

---

### D.57 OnlineCareMustNotFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | OnlineCareSpecialtyIds_ListMatchesProductSource | Confirm the hardcoded list is still current (drift) | High |
| 2 | Filter_WithOnlineCareSpecialtyInRequest_StillExcludes | Overriding request value doesn't bypass exclusion | High |

---

### D.58 OnlyInNetworkBookableFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_PayMyselfMustNotValueExplicit_true | Current uses `It.IsAny<string>` — pin value | High |
| 2 | Filter_WithNoInsurance_DoesNotApply | Baseline | Medium |

---

### D.59 PartOfLeadershipTeamFiltererTests.cs (6 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithInstituteIdAndTrue_TargetsLeaderInInstitutesRawField | Pin the field (currently `It.IsAny<string>`) | High |
| 2 | Filter_WithMultipleInstitutes_IfSupported | Array support | Medium |

---

### D.60 PracticeIdFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithEmptyPracticeId_DoesNotAddFilter | Empty vs null parity | Medium |
| 2 | Filter_WithCloudifiedPracticeId_Normalized | Prefix handling | Medium |

---

### D.61 PreviewProviderLocationFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — comprehensive type-based branch coverage.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithCoordinateLocation_UsesDefaultRadius | Radius default verification | High |
| 2 | Filter_WithCoordinateLocation_UsesSearchParamsRadiusOverride | Override path | High |

---

### D.62 PreviewProviderSpecialtyIdFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_FieldNameDiffersFromProductionSpecialtyField | Preview uses `Specialties.Id` vs prod `Specialties.monolithId` — pin this | High |

---

### D.63 ProcedureIdFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithIllnessId_75_MatchesSentinel | Sentinel constant usage | Medium |
| 2 | Filter_WithSpPrefixedProcedureId_Monolithifies | Prefix | Medium |

---

### D.64 ProviderEmploymentStatusFiltererTests.cs (4 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Constructor_ShouldSetAffiliationLevels | Only asserts `NotBeNull` — tautology |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithBoostsHavingWeights_EmitsWeightsInQuery | Current test ignores the `1.0f`/`2.0f` weights entirely | High |
| 2 | Filter_WithDuplicateLevels_DoesNotDoubleApply | Dedup | Medium |
| 3 | Filter_WithNullLevels_ThrowsOrDefaults | Null-safety on constructor arg | Medium |

---

### D.65 ProviderGenderFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithFemaleGender_AddsMaleFilter | Female branch currently untested | High |
| 2 | Filter_WithNonBinaryOrUnknownGender_HandlesOrSkips | Enum coverage | Medium |
| 3 | Filter_GenderValueIsCapitalized | Case of the value passed to ES | High |

---

### D.66 ProviderSellingPointFiltererTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithSpPrefixedPcpId_StillTakesPcpBranch | Prefix/Monolithify interaction | High |
| 2 | Filter_WithAllSpecialtyIds_CoversEveryBranch | Parametrized | Medium |

---

### D.67 ProvLocMappingApprovedFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_ApplyOrdering_ApprovedBeforeActive | Order of must clauses (not asserted today) | Medium |
| 2 | Filter_DoesNotMatchPendingOrRejected | Negative/boundary mapping status | High |

---

### D.68 SearchableDirectoryFiltererTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithNullDirectoryId_DoesNotAddFilter | Negative path | High |
| 2 | Filter_WithZDTestDirectory_AppliesFilter | Alternate directory | Medium |

---

### D.69 SeesChildrenFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_FieldNameAssertedOnActualCall | Pin field in Filter call, not just via property | High |

---

### D.70 SpecialtyIdFiltererTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | Filter_ShouldReturnQueryBuilder | Trivial stub — only asserts `return qb`, no filter behavior |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithSpecialtyId_AddsFilter | Actual filter behavior (currently no test at all!) | High |
| 2 | Filter_WithNullSpecialtyId_DoesNotAddFilter | Negative path | High |
| 3 | Filter_WithSpPrefixedId_StripsPrefix | Monolithify | High |

---

### D.71 SpoEnabledFiltererTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Filter_ShouldAddFilterForTrue | `It.IsAny<string>()` field — field name not pinned |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_TargetsSpoEnabledField | Pin field | High |
| 2 | Filter_WithSpoDisabledInRequest_DoesNotApply | Conditional branch if any | Medium |

---

### D.72 StateFiltererTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | Filter_ShouldReturnQueryBuilder | Trivial stub — only asserts `return qb` |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithState_AddsFilter | Actual behavior (no test!) | High |
| 2 | Filter_WithNullState_DoesNotAddFilter | Negative | High |
| 3 | Filter_CaseSensitivityOfState | Casing | Medium |

---

### D.73 TestDirectoryFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithUnknownDirectoryId_FallsBackToMustNot | Defensive default | Medium |
| 2 | Filter_FieldNameAssertedExplicitly_InFilterCall | Pin field (`It.IsAny<string>`) | High |

---

### D.74 ZipCodeFiltererTests.cs (3 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | Filter_ShouldReturnQueryBuilder | Trivial stub — only asserts `return qb` |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Filter_WithZipCode_AddsFilter | Actual behavior (no test!) | High |
| 2 | Filter_WithNullZipCode_DoesNotAddFilter | Negative | High |
| 3 | Filter_WithZipPlus4_Normalized | "12345-6789" format | Medium |

---

## Summary Themes (Chunk D)

1. **Heavy duplication** — ~15 Filterer*Tests.cs files (D.20–D.34) re-assert the same singleton & FieldName pattern already covered in dedicated files; should be consolidated.
2. **Pervasive over-stubbing** — many `Filter` tests use `It.IsAny<string>()` for the field name, missing the primary correctness guarantee (ES field name). Every filterer test that does this is flagged.
3. **Missing behaviour coverage** — SpecialtyIdFilterer, StateFilterer, ZipCodeFilterer, DateOfServiceFilterer, InsuranceFilterer have ~zero behavioral tests; only smoke tests.
4. **Es7Client error paths thin** — partial shard failures, `timed_out: true`, malformed JSON, aggregation error path not tested (high risk of silent result drift).
5. **QueryableFieldMapping drift risk** — no schema-conformance tests vs deployed ES mapping.
6. **IdFixers has a likely bug** — `.Replace("sp_", "")` in Monolithify strips "sp_" anywhere in the string; test D.38 #3 codifies this rather than fixing.
7. **CombinedLocationFilterer** visit-type branches (InPersonVisit/VirtualVisit/facet override) are untested despite being priority-ordering logic.


---

## Chunk E — Search/Ranking Unit Tests
*Directory: `tests/YassSharp.UnitTests/Search/Ranking/` — best-sentence, ScoreFusion, LightGBM rankers (43 files).*

### E.1 BestSentenceEnricherTests.cs (~65 tests)

Source: `BestSentenceEnricher.cs`. Covers `ValidateRequest`, `NextUpdateAsync` (happy / hidden / single-sentence / cross-encoder error / timeout), `ExtractSentencesFromResults`, `MapScoresToBestSentences`, `EnrichResultsWithBestSentences`, `EnrichAdsWithBestSentences`, ad+organic cohabitation.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `EnrichResultsWithBestSentences_WhenNullSourceIdAndType_ShouldSetThemToNull` | Tests a trivial null-passthrough with no business rule — redundant with `WhenNullProviderTextData_ShouldStillEnrichWithNullSource`. |
| `EnrichResultsWithBestSentences_WhenIncludeSummaryDetailsTrue/False_*` | Only toggles one bool on a pass-through getter; provides no coverage of any decision logic. |
| `Enabled` / environment-gated `WriteAudit_*` tests (no tests here but flagged as a pattern) | n/a for this file |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| NextUpdateAsync when CE returns more scores than sentences (defensive array-length mismatch) | High | Ranking correctness — CE service may return unexpected shape and silent mis-assignment corrupts rankings. |
| NextUpdateAsync when two results tie on best-sentence score — verify stable selection | High | Tie-break determinism for snapshot stability. |
| EnrichAdsWithBestSentences preserves ad position / does not reorder `AdDecisions` | High | Ad business rule — ads must stay in their assigned slot. |
| NextUpdateAsync when ad has both TextSnippet AND provider appears in organic — which source wins? | Medium | Verifies consistent priority between organic-derived and ad-derived sentence. |
| NextUpdateAsync when `responseInfo.Results` has `IsHidden` on some but not all — ensure only non-hidden are sent to CE | High | Ranking + PHI leakage avoidance — hidden SHI content must not leak through CE call. |
| ExtractSentencesFromResults with sentence shorter than min-length (2 chars) — should filter | Low | Covers edge sentence extraction. |
| MapScoresToBestSentences when all scores are negative / all equal | Medium | Monotonicity + tie-break invariant. |

---

### E.2 ConstrainedScoreFusionProcessorTests.cs (13 tests)

Source: `ConstrainedScoreFusionProcessor.cs` (DefaultMaxRankChange = 10). Covers MaxRankChange clamping, no-op paths, forced placement at window boundary, tied CE scores.

#### Irrelevant Tests
_None flagged — tests track real clamping behavior and boundary cases._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| MaxRankChange = 0 (pure no-op) — verify no reordering AND metrics still emitted | Medium | Branch coverage + observability. |
| MaxRankChange > list size — should degrade to unconstrained ScoreFusion result | Medium | Boundary equivalence. |
| Ad positions preserved when constrained fusion would otherwise displace them | High | Ads business rule — constrained fusion must not shift BannerInfo!=null rows. |
| Negative MaxRankChange in request — clamped to 0 or default? | High | Input-hardening invariant — prevents corrupted config from breaking order. |
| Results that tie on fused score after clamping — stable input order preserved | High | Tie-break determinism. |
| Subset of results have null CE score AND null MapleRank — verify they remain at original positions | High | Missing-feature safety. |

---

### E.3 CrossEncoderRankerErrorTests.cs (5 tests)

Source: `CrossEncoderRanker.cs` error-branch logic (OperationCanceled / InvalidOperationException + logging + metric "crossencoder.error"/"crossencoder.timeout").

#### Irrelevant Tests
_None flagged — error-path coverage is core ranker correctness._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Non-cancellation TaskCanceledException (distinguishes genuine timeout from user-cancel) | Medium | Metric name correctness. |
| Inner exception of AggregateException from parallel batches | High | Parallel-batch failure fan-in; wrong handling would mask upstream errors. |
| HttpRequestException from CE service (transient) | Medium | Transient-vs-fatal distinction. |
| Exception during `ApplyFallbackScores` path (e.g. percentile computation on empty set) | High | Post-failure fallback must itself be resilient. |

---

### E.4 CrossEncoderRankerTests.cs (~35 tests)

Source: `CrossEncoderRanker.cs`. Covers FilterOrganicResults, ValidateRequest, GroupProvidersByProfile, ApplyScoresToResults, LimitProviderGroups, ResortResultsByScore (preserves ad positions), GetSearchQuery/GetInstruction, ApplyFallbackScores (P50/Min), ScoreInBatchesAsync with MinBatchSize=250 and parallel batches.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests that assert `ProcessorName.Should().Be("CrossEncoderRanker")` / `ProcessorType` | Low-value constant assertions — cannot catch real bugs. |
| `ApplyScoresToResults` with scores.Length vs results.Length mismatch (both "fewer scores" and "more scores" cases) | These are defensive tests for a contract that should never fail in practice; if the test breaks, the source contract has been violated elsewhere. Mark as low-value *only if* the source class documents the invariant; otherwise keep. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| ScoreInBatchesAsync cancels remaining batches when one batch fails (verify no extra CE calls) | High | Resource / cost — orphan batches waste $ and ML quota. |
| ResortResultsByScore preserves tie-broken order within same score (stable sort invariant) | High | Snapshot determinism. |
| ApplyFallbackScores when no KNN hits at all (all fallbacks to Min) | High | Realistic degraded-service behavior. |
| ApplyFallbackScores: missing-from-index gets different fallback than in-index-but-no-KNN-hit | High | Ranking correctness — two distinct degraded states. |
| GroupProvidersByProfile with providers that share same profile hash across >2 locations | Medium | Group-dedup edge. |
| ResortResultsByScore where a CE-scored result now beats an ad's neighbor — ads still stay in original slot | High | Ads business rule. |
| Validate that CE instruction is chosen from Fts > SearchQuery > null in that priority | High | Already partially covered; verify null fallback emits "no-query" metric. |
| Score monotonicity — higher CE score always produces rank <= lower CE score (given same fallback bucket) | High | Monotonicity invariant. |

---

### E.5 KeywordEnricherTests.cs (~50 tests)

Source: `KeywordEnricher.cs`. Covers Gemini calls, boundary-aware phrase matching, FilterMutuallyExclusiveKeywords, ComputeBatchSize, ad decision enrichment (organic/vector/no-provider), TokenizeQuery with stopwords, TryExtractExactQueryMatches with plural variants, ComputeDisplaySnippet.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests that only assert a constant name like "keyword_enricher" / constructor Name | Low-value identity checks. |
| Any test using `[Explicit]` or calling the real Gemini API (if present) | Flag if present — must not run in CI. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Ad decision enrichment when ad provider also appears in organic results AND has a different best keyword set | High | Ads business rule — organic should win for consistency. |
| Ad decision enrichment when insurance mismatch flag is set on ad — verify ad is hidden / not enriched | High | Ads correctness — insurance-mismatched ads must never appear enriched. |
| FilterMutuallyExclusiveKeywords when two keywords are case-differently-equal (Cardio/CARDIO) | Medium | Normalization. |
| TokenizeQuery with unicode / non-ASCII (accents, CJK) | Medium | Internationalization. |
| ComputeBatchSize at exact boundary of min/max batch bucket | Low | Branch coverage. |
| Enrichment is skipped entirely when `IsHidden` on result | High | SHI safety. |
| Keyword extraction result stable under identical input (determinism) | Medium | Snapshot stability. |

---

### E.6 KeywordSnippetHelperTests.cs (~15 tests)

Source: `KeywordEnricher.ComputeDisplaySnippet` (static helper). Short ≤100-char sentences, long sentences with start/centered windows, trailing context, null/empty edge cases.

#### Irrelevant Tests
_None flagged — tight focused helper tests._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Keyword at exact position 0 AND exact position len-1 simultaneously | Medium | Window-span edge. |
| Overlapping keyword matches (e.g. "heart" and "earth" with "hearthearth") | Medium | Bold-span merge correctness. |
| Emoji or combining-character in sentence that would break byte vs char indexing | Low | Internationalization. |
| Very long single-word sentence (>100 chars no spaces) with keyword at end | Low | Word-boundary truncation fallback. |
| Keyword string is empty `""` in list — should be ignored, not match everywhere | High | Silent over-matching would corrupt display. |
| Multiple keywords where order in list differs from order in sentence — verify independent | Medium | Ordering invariance. |

---

### E.7 OrganicOnlyBoxRankerTests.cs (7 tests)

Source: `OrganicOnlyBoxRanker.cs`. Uses MapleV21Spo model resource (Assert.Ignore if missing); skipped cases for `no_location` / `no_availability`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Any test that `Assert.Ignore`s when `MapleV21Spo.features.json` resource not embedded | Environment-dependent and will silently skip in CI without flagging. Should be marked `[Explicit]` or moved to integration tests. |
| ProcessorName/ProcessorType identity checks | Low-value constant assertion. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Verify ranker still scores when `SkipFeatures` list includes a real feature (graceful degradation) | High | Personalization-fallback safety. |
| Output ranking is deterministic given identical inputs | High | Snapshot stability. |
| Feature-vector completeness — each scored provider produces full feature count expected by Maple model | High | LightGBM feature-vector completeness invariant (feature drift detection already exists in E.34 but at model level, not ranker level). |
| Ranker never reorders ads (BannerInfo!=null) | High | Ads business rule. |
| Skipped ranker (Assert.Ignore) still emits "maple.skipped" metric | Medium | Observability. |

---

### E.8 PageVectorSearchEnricherErrorTests.cs (7 tests)

Source: `PageVectorSearchEnricher.cs` error paths. Timeout / error / null-embedding / empty-embedding metrics.

#### Irrelevant Tests
_None flagged._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Embedding service returns wrong-dimensionality vector (e.g. 256 instead of 512) | High | Silent scoring corruption. |
| VectorSearchService returns hits with malformed (null) provider IDs | Medium | Lookup key safety. |
| Partial failure — one batch succeeds, one errors (when Page uses batching) | High | Degraded-mode behavior. |

---

### E.9 PageVectorSearchEnricherTests.cs (~14 tests)

Source: `PageVectorSearchEnricher.cs` happy path. Ad enrichment from organic vs vector search, sensitive visit reason handling (sets IsHidden for Results + Ads + CanoeResults).

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests that exercise "sensitive visit reason" with a permanent flag rather than injected config | Flag only if the feature flag is permanently ON — those tests lock in current behavior rather than exercising branches. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Sensitive visit reason sets IsHidden on CanoeResults — verify ads get IsHidden too AND the hidden-ad metric is incremented | High | PHI / SHI correctness. |
| Ad provider NOT in organic AND NOT in vector hits — falls through to no-op without throwing | Medium | Robustness. |
| Insurance-mismatched ad does NOT receive vector-search enrichment (is hidden upstream before enrichment) | High | Ads business rule. |
| Order: enrich organic first, then ads — ad enrichment sees updated organic | High | Consistency invariant between ad and organic display. |

---

### E.10 Presort/PresortV3Tests.cs (~13 tests, includes PresortAlgoScoreTests)

Source: `Presort/PresortV3.cs`. Score with various LocalityTypes (Borough/City/State/null), feature sequence assertion.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| PresortAlgoScoreTests — these appear to be trivial POCO / property tests if they only assert setter/getter round-trip on AlgoScore. | Low-value; property-only coverage. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Score with all three scorers returning exactly the same raw score — tie-break between Availability/Distance/Specialty | High | Tie-break ordering invariant (presort determines seed order). |
| Score with a candidate that has zero Availability (no slots) — presort keeps or drops? | High | Zero-score candidate handling — affects downstream ranking pool. |
| LocalityType.Unknown and LocalityType.Country paths | Medium | Branch coverage. |
| Score stability — same inputs produce same outputs across runs | High | Snapshot determinism. |
| Feature sequence assertion for *negative* distance (impossible but defensive) | Low | Input-hardening. |

---

### E.11 Presort/ScoringFunctions/AvailabilityScorerTests.cs (9 tests)

Source: `Presort/ScoringFunctions/AvailabilityScorer.cs` (Weight = 1.0921597146222743, MinimumAvailabilityScore = -0.62146007228).

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Any test that asserts the literal magic numbers `1.0921597146222743` or `-0.62146007228` directly rather than via named constants | Over-specification — refactor of constant names would break without any behavior change. Prefer asserting relative ordering. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Availability with 0 open slots — must clamp to MinimumAvailabilityScore, not below | High | Zero-score candidate invariant. |
| Availability with extremely high slot count — no overflow, monotonic in slot count | High | Score monotonicity invariant. |
| Same slot count at different days-out produces distinguishable scores (time-decay) | High | Availability-freshness business rule. |
| Availability scorer applied to virtual-only providers | Medium | Virtual-care branch coverage. |

---

### E.12 Presort/ScoringFunctions/DistanceScorerTests.cs (6 tests)

Source: `Presort/ScoringFunctions/DistanceScorer.cs` (Weight = -0.1595109669466852, meters→miles).

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests asserting the exact literal `-0.1595109669466852` | Over-specification of a trained constant. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Distance = 0 (same location) returns highest score | High | Monotonicity boundary. |
| Distance = max allowed (e.g. 50 miles) — verify no under/overflow | Medium | Boundary. |
| Distance null / missing — verify default fallback score | High | Missing-feature safety. |
| Negative distance input — defensive clamp | Low | Input-hardening. |
| Virtual provider (distance is special — -9999 sentinel) | High | Virtual-care handling — wrong handling breaks virtual-first ordering. |

---

### E.13 Presort/ScoringFunctions/SpecialtyScorerTests.cs (6 tests)

Source: `Presort/ScoringFunctions/SpecialtyScorer.cs` (Weight = 1.0523415832558942).

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests that assert the literal magic Weight constant | Over-specification. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Provider has multiple specialties, one matches search — still gets full match score | High | Specialty matching correctness. |
| Provider has no specialties at all — default zero score, not error | High | Missing-feature safety. |
| Specialty matches but is non-primary — verify still considered match (or half-match if logic differs) | Medium | Business rule. |
| Null `searchSpecialtyId` path | High | Generic-search branch. |

---

### E.14 Presort/ScoringFunctionTests.cs (1 test)

Source: interface `IScoringFunction`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| The single test in this file only exercises the mock setup (calls `.Setup()` then verifies the mock returned what was set up). This provides ZERO real coverage. | Near-useless — should be deleted or replaced with concrete implementations' tests. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Replace with integration test asserting all three registered `IScoringFunction` implementations are invoked exactly once per score call | Medium | Wiring correctness. |
| Test that ScoringFunction name uniqueness is enforced (no duplicate names registered) | Medium | DI/config sanity. |

---

### E.15 PresortRankerTests.cs (~12 tests)

Source: `PresortRanker.cs`. Post-presort size limit (500), presort rank 1-based, metric verification.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests asserting ProcessorName / ProcessorType constants | Low-value. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Exactly 500 results (boundary) | High | Off-by-one on size cap. |
| 501+ results — the 501st is dropped; verify highest-score ones survive, not first-500 by input order | High | Ranking correctness — dropping the wrong set corrupts downstream. |
| Ads preserved at their original index, even when size cap trims organic | High | Ads business rule. |
| Tie-breaker when 500th and 501st have identical score | High | Tie-break determinism. |
| Rank 1-based and contiguous (1..N, no gaps) after dedup | Medium | Invariant. |
| Metric `presort.trimmed_count` emitted when trimming occurs | Medium | Observability. |

---

### E.16 RankingHelpersTests.cs (7 tests)

Source: `RankingHelpers.cs::SortOrganicPreservingAds`. Covers mixed/only-organic/only-ads/empty/start-end/consecutive positions.

#### Irrelevant Tests
_None flagged — focused helper with good branch coverage._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Sort is stable — two organic results with equal sort key preserve input order | High | Stable-sort invariant. |
| Ad at position 0 (very first slot) and organic list is empty | Medium | Boundary. |
| Very large list (>1000 entries) with ads interleaved every 10 — performance & correctness | Low | Perf smoke. |
| Input list with ALL elements being ads — no sort function invoked at all | Medium | Short-circuit invariant. |
| Sort function throws — verify exception propagates, no partial mutation of input list | Medium | Robustness / immutability guarantee. |

---

### E.17 RankRandomizerTests.cs (5 tests)

Source: `Scorers.cs::RankRandomizer` (or similar). AB experiment flag gating, deterministic session seed, ScorerName prefixing.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Tests that assert the AB flag name literal (e.g. "rank_randomizer_2024") | Low-value — the flag name is a string constant. |
| Test that runs with the flag permanently ON in config — verify the test is exercising the OFF path too | Flag tests that only cover ON path are irrelevant if flag is being removed. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Deterministic: same sessionId produces same randomization across calls | High | Reproducibility invariant. |
| Different sessionIds produce different randomizations (probabilistic) | Medium | Actual randomization works. |
| Empty / null sessionId — should not throw, falls back to fixed seed or skips | High | Robustness. |
| Ads are never randomized (BannerInfo!=null excluded from shuffle) | High | Ads business rule. |
| Randomization does NOT change total result count (no drops) | High | Invariant. |
| Randomization bounded — no result moves more than K positions (if configured) | Medium | Constraint enforcement. |

---

### E.18 ScoreFusionProcessorTests.cs (15 tests)

Source: `ScoreFusionProcessor.cs` (DefaultRelevancyWeight = 0.8). Covers no-CE/no-MapleRank skipping, fused score in [0,1], tie-break by MapleRank, weight clamping, single-result percentile, out-of-range MapleRank clamp, Score update to ScoreFused.

#### Irrelevant Tests
_None flagged — well-focused on fusion math._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| relevancyWeight = 0.0 exactly — fused score equals MapleRank-derived score only | High | Boundary of weighted mix. |
| relevancyWeight = 1.0 exactly — fused score equals percentile(CE) only | High | Boundary. |
| All results have identical CE score — percentile ties at 1.0 for all (or 0.5, depending on impl) | High | Tie-break in percentile computation. |
| Fused score monotonic — for fixed MapleRank, higher CE ⇒ higher fused | High | Monotonicity invariant. |
| Fused score monotonic — for fixed CE, higher MapleRank (better rank = lower number) ⇒ higher fused | High | Monotonicity invariant. |
| Tie on fused score — deterministic fallback (original input order or MapleRank) | High | Stable sort / tie-break. |
| Ads (BannerInfo!=null) are never reordered by score fusion | High | Ads business rule. |
| relevancyWeight = NaN / Infinity — safe clamp | Medium | Input-hardening. |
| Only 2 results — percentile computation on tiny sample | Medium | Small-N edge. |
| Metric `score_fusion.fused_count` and `.skipped_count` emitted correctly on partial application | Medium | Observability. |

---

### E.19 ScorersTests.cs (~20 tests)

Source: `Scorers.cs` (DistanceV3Scorer, PresortV3Scorer, EnchiladaScorer, LtvScorer). ALL tests only check constructor/Name/SortOrder/Warmup — Score() tests are near-trivial (just `HaveCount(1)`).

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| ALL `Name_ShouldReturnX` and `SortOrder_ShouldReturnX` tests for these 4 scorers | Constant-assertion; no logic covered. |
| Score tests that only assert `.Should().HaveCount(1)` without inspecting the score value | These test nothing about scoring — they only test that the scorer didn't crash on a single input. |
| Warmup tests that only assert `act.Should().NotThrow()` | Trivial. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| DistanceV3Scorer — score is a monotone-decreasing function of distance | High | Monotonicity invariant. |
| PresortV3Scorer — produces same rank as the presort pipeline when run in isolation (equivalence) | High | Wiring consistency. |
| EnchiladaScorer — handles empty provider list without exception | Medium | Robustness. |
| LtvScorer — score for unknown provider ID falls back to default, not throws | High | Missing-feature safety. |
| All 4 scorers produce scores in their documented range ([0,1] or sort-order-dependent) | High | Contract enforcement. |
| All 4 scorers handle 10k+ providers without quadratic behavior | Low | Perf. |
| Warmup actually populates internal caches (verify next Score call is faster or uses cache) | Medium | Warmup is meaningless if it's a no-op — tests should verify effect. |

---

### E.20 Scoring/RequestScoringInputsTests.cs (1 test)

Source: `Scoring/RequestScoringInputs.cs`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| The single test is a trivial constructor / property round-trip. No behavioral coverage. | Near-useless — POCO test. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Construct with null SearchQuery / null DeviceEmbedding — verify consumers don't NPE downstream | Medium | Null-safety. |
| Equality semantics (value-based or reference-based?) — document via test | Low | Intent clarity. |

---

### E.21 TheBox/AlgoScoreTests.cs (4 tests)

Source: `TheBox/IScorer.cs::AlgoScore`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| ALL 4 tests — trivial property getter/setter assertions on a POCO. | Near-useless. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| AlgoScore equality / hashing — if used as dict key | Low | Depends on usage. |
| AlgoScore serialization round-trip (JSON for rank audit) | Medium | Audit trail fidelity. |

---

### E.22 TheBox/AvailabilityFeaturizerTests.cs (~10 tests)

Source: `TheBox/AvailabilityFeaturizer.cs`. Hour/day constants, CreateEmpty, Get with availabilities, SingleDayStats dedup logic (with non-monotonic hours).

#### Irrelevant Tests
_None flagged — dedup logic is real branch coverage._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Availability slots spanning DST transition — 23/25 hour day handling | Medium | Time-zone edge. |
| Availability with duplicate exact timestamps — dedup correctness | High | Data-quality invariant. |
| Empty availability list produces CreateEmpty-equivalent result | Medium | Consistency between two construction paths. |
| 7-day window where every day has slots — verify num_days_with_availability == 7 exactly | Medium | Off-by-one boundary. |
| Very old availability (before "now") — filtered out | High | Freshness invariant. |

---

### E.23 TheBox/BoxDistanceBandModeTests.cs (2 tests)

Source: `TheBox/BoxDistanceBandMode.cs`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Both tests are trivial enum int-value assertions (e.g. `BoxDistanceBandMode.Narrow.Should().Be(0)`). | Near-useless — locks in int values that should be stable by contract but provides no behavioral coverage. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Enum parse from string (if used for config) | Low | Config compatibility. |
| Enum exhaustiveness — when a new band is added, a switch expression warns | Medium | Maintenance safety. |

---

### E.24 TheBox/BoxProviderLocationTests.cs (3 tests)

Source: `TheBox/BoxProviderLocation.cs`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| ALL 3 tests — trivial POCO setter/getter tests. | Near-useless. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Equality / GetHashCode semantics (if keyed in dicts) | Low | Depends on usage. |

---

### E.25 TheBox/BoxSearchParametersTests.cs (2 tests)

Source: `TheBox/BoxSearchParameters.cs`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Both tests are trivial POCO setter tests. | Near-useless. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Validation — required fields throw on null/missing at construction or usage time | Medium | Defensive construction. |

---

### E.26 TheBox/MachineLearned/Features/AvailabilityFeaturesTests.cs (~17 tests)

Source: `TheBox/MachineLearned/Features/AvailabilityFeatures.cs`. Feature Name + Transform with null/valid cases for NumDistinctHoursWithAvailability, MinTimeToNextSlotMinutes, FirstAvailableMinute, etc.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| All `*_Name_ShouldReturnCorrectName` tests | Constant assertion — low value but acceptable as smoke. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| MinTimeToNextSlotMinutes with slot exactly `now` — boundary 0 | High | Zero-value semantic correctness. |
| FirstAvailableMinute when day rolls over midnight | High | Time-of-day boundary. |
| NumDistinctHoursWithAvailability when same hour has multiple slots — dedup to 1 | High | Dedup invariant. |
| LastAvailableMinute < FirstAvailableMinute — invariant violation detected | Medium | Data-quality safety. |
| All features default to sentinel (-9999 or 0) when DailySummaries empty | High | Missing-feature default handling. |

---

### E.27 TheBox/MachineLearned/Features/CategoricalFeaturesTests.cs (~22 tests)

Source: `TheBox/MachineLearned/Features/CategoricalFeatures.cs`. Holidays, CategoricalLookup, UserAgentPlatformDetailConverter, AddressCategorization (state IDs, zipcode/ipaddress parsing), ScoringUserAgentPlatformCategorical, IsHolidayZone, ScoringVisitTypeCategorical.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Any test that embeds a full state-ID lookup table inline | Low-value — reimplements the CSV in the test; brittleness without coverage benefit. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| IsHolidayZone during 11:59 PM / 12:01 AM of a holiday — boundary | Medium | Time-zone boundary. |
| UserAgentPlatformDetailConverter with unknown UA string — returns "Unknown" category, not throws | High | Missing-feature default handling. |
| Zipcode with 9-digit ZIP+4 format | Medium | Parsing robustness. |
| IP address IPv6 input | Low | Internationalization. |
| CategoricalLookup where key not in table — returns -1 sentinel, not crashes | High | LightGBM feature vector integrity — NaN would break model. |
| CategoricalLookup value type size (int vs short) — verify consistency with features.json | High | Feature drift safety. |

---

### E.28 TheBox/MachineLearned/Features/GeoFeaturesTests.cs (~20 tests)

Source: `TheBox/MachineLearned/Features/GeoFeatures.cs`. DistanceMi with virtual location (-9999), IsSameCounty, LocationZipCountyId, ReqZipCountyId, population density, ReqNearestZipMatchesLocNearestZip.

#### Irrelevant Tests
_None flagged — real branch coverage._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| DistanceMi at antipode (max Earth distance ~12500 mi) | Low | Boundary. |
| IsSameCounty when one side is virtual (-9999) — false | High | Virtual-care branch. |
| LocationZipCountyId when zip not in lookup — default sentinel | High | Missing-feature default. |
| Population density feature with 0 population (ghost town) — no div-by-zero | High | Input-hardening. |
| ReqNearestZipMatchesLocNearestZip with leading-zero ZIPs ("07002") | Medium | String-parsing robustness. |

---

### E.29 TheBox/MachineLearned/Features/OrganicFlagCategoricalTests.cs (4 tests)

Source: `TheBox/MachineLearned/Features/OrganicFlagCategorical.cs`. IsSpoRanking true/false/null → 1.0 / 0.0 / 0.0.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Name_ShouldBeOrganicFlagCat` — constant assertion. | Low-value. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Feature correctness when `IsSpoRanking` is missing from proto (default value) — verify returns 0.0 | High | Missing-feature default handling. |
| Feature type (double) matches features.json expectation | Medium | Feature drift. |

---

### E.30 TheBox/MachineLearned/Features/OtherFeaturesTests.cs (~30 tests)

Source: `TheBox/MachineLearned/Features/OtherFeatures.cs`. Covers OffersVideoVisit, ScoringIsVirtualLocation, ScoringTotalReviewCount, BayesianRatingOrOptOut, ProbabilityProviderTakesInsurance, NormPopularityCount, SpecialtyMatchesSearch, IsSearchedForSpecialtyMainSpecialty, SearchedProcedureIsDefaultForSpecialtyFeature, SpecialtyCategoryMatchesSearchCategorical, CrossEncoderScore, QuerySimilarityScore.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Every `*_Name_ShouldReturnCorrectName` test (~12 of them) | Constant-assertion pattern. |
| `OffersVideoVisit_Transform_WithFalse_ShouldReturnZero` — sets ProvLoc.OffersVideoVisit=false but the actual logic checks Geo.VirtualStates against Geo.State, so this test name is misleading and the assertion may be hitting a different branch than advertised. | Misleading / potentially wrong test subject. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| OffersVideoVisit when Geo.State is set but VirtualStates is empty — verify returns 0.0 | High | Correct branch coverage. |
| OffersVideoVisit when state matches case-insensitively ("ny" vs "NY") | Medium | Normalization. |
| BayesianRatingOrOptOut with TotalReviewCount = 0 but IsShowingReviews = true — divide-by-zero guard | High | Input-hardening. |
| ProbabilityProviderTakesInsurance with NaN / out-of-range (> 1.0) — clamp or pass-through? | High | Feature-vector integrity. |
| CrossEncoderScore = NaN / Infinity — sanitized to 0 or passed through? | High | LightGBM feature-vector integrity (NaN breaks model). |
| QuerySimilarityScore above 1.0 / below -1.0 — cosine dist should never exceed [-1,1]; defensive clamp | Medium | Data-quality guard. |
| SpecialtyCategoryMatchesSearchCategorical with empty categoryToIndex dictionary — falls back to -1.0 | High | Missing-feature default handling. |
| NormPopularityCount negative value — verify pass-through without clamping (if that's the contract) | Low | Contract clarity. |

---

### E.31 TheBox/MachineLearned/Features/PersonalizationFeaturesTests.cs (~25 tests)

Source: `TheBox/MachineLearned/Features/PersonalizationFeatures.cs`. ComputeDistance (Euclidean/Manhattan/Chebyshev/Cosine/BrayCurtis/Correlation), DeviceProviderAppointmentsCount, DevicePracticeAppointmentsCount, ScoringDeviceNumSearches, ScoringDeviceNumClicks.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Name-only tests (~7 of them) | Constant-assertion. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| ComputeDistance with one zero vector and one non-zero — cosine returns 1.0 (max distance) not NaN | High | LightGBM feature-vector integrity. |
| ComputeDistance with both identical non-zero vectors — all metrics return 0.0 | High | Correctness invariant. |
| ComputeDistance with very high-dim vectors (512D, matching real embedding size) | Medium | Realistic size sanity. |
| DeviceProviderAppointmentsCount with negative count (impossible but defensive) | Low | Input-hardening. |
| Personalization fallback — when DeviceEmbedding is null AND provider has embedding, returns -1.0 (documented) but downstream ranker must not drop the provider | High | Personalization-fallback safety invariant. |
| Correlation distance when std-dev of one vector is 0 (constant vector) — avoid div-by-zero | High | Input-hardening. |
| Cosine distance with one vector of magnitude 0 — avoid div-by-zero | High | Input-hardening. |

---

### E.32 TheBox/MachineLearned/Features/RealizationFeaturesTests.cs (~20 tests)

Source: `TheBox/MachineLearned/Features/RealizationFeatures.cs`. Practice-level and provider-level realization rates, provider-quality categorical features.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `ProviderQualityNewPatientAppointments_Transform_WithNullQualities_ShouldThrowArgumentNullException` | Tests a protobuf framework invariant (protobuf setters throw on null), not the feature's logic. The test is actually inside the `Arrange` block — the feature is never invoked. **This test exercises the Protobuf library, not the feature code.** |
| All `Name_ShouldReturnCorrectName` tests (~2 per feature) | Constant-assertion. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| RescheduleRateL180Day with value > 1.0 (impossible but defensive) | Medium | Data-quality. |
| ProviderQualityHighlyRecommended with quality string "highlyrecommended" (lowercase) — verify case-sensitive as intended OR case-insensitive | High | Real-world data may have casing drift — feature drift. |
| ProviderQualityNewPatientAppointments with ProviderQualities = "" (empty but not null) — returns zero index | High | Missing-feature default handling. |
| All realization features return sentinel (-9999) when RealizationPracticeFeatures is null (not just when ProvLoc is null) | High | Nested-null safety. |
| Bayesian avg with zero appointments — divide-by-zero guard | High | Input-hardening. |

---

### E.33 TheBox/MachineLearned/Models/MapleModelTests.cs (1 parametrized test, 6 cases)

Source: `TheBox/MachineLearned/Models/MapleV21Spo.cs`, `MapleV22S.cs`, `MapleV28NonP13n.cs`, `MapleV28P13n.cs`, `MapleV29NonP13n.cs`, `MapleV29P13n.cs`. Asserts `FeatureTransforms.Length` and order matches embedded `features.json` resource.

#### Irrelevant Tests
_None flagged — this is a high-value feature-drift guard._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Model version V25 / V26 missing from parametrization — if these variants exist in source, tests must cover them too | High | Feature-drift guard must cover every shipping model variant. |
| Verify each FeatureTransform returns the correct Type (Double vs Categorical) matching features.json's feature_type field | High | LightGBM feature-vector completeness — type mismatches silently corrupt predictions. |
| Verify no duplicate feature names within a single model | Medium | Sanity — duplicate features would double-count. |
| Verify features.json matches the model's serialized LightGBM model file (if embedded) | High | Cross-file consistency — drift between JSON and binary breaks inference. |
| Snapshot/baseline: running a fixed `RequestScoringInputs` through each model produces a deterministic score | High | Score stability across code changes. |

---

### E.34 TheBox/NoopScorerTests.cs (7 tests)

Source: `TheBox/NoopScorer.cs`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Name_ShouldReturnNoop`, `SortOrder_ShouldReturnHigherIsBetter` | Constant-assertion. |
| `Warmup_ShouldNotThrow`, `Warmup_CanBeCalledMultipleTimes` | Trivial on a no-op impl. |
| `Score_WithNullSearchParameters_ShouldNotThrow` | Only verifies no-throw on a literal no-op — no real coverage. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Verify NoopScorer is used as the DI fallback when no real scorer is registered | Medium | Wiring safety. |
| Verify output AlgoScore objects carry the correct ScorerName ("noop") so audit logs are attributable | Medium | Observability. |

---

### E.35 TheBox/RankAuditWriterTests.cs (~13 tests)

Source: `TheBox/RankAuditWriter.cs`. Environment-gated (AUDIT_RANK env var). Tests ISO timestamp formatting, camelCase JSON, Scala-compatible PatientFriendlinessCategory enum serialization, circular reference resilience.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Enabled_ShouldReturnBoolean` — asserts `IsInstanceOf<bool>` of a bool — tautological. | Useless. |
| `WriteAudit_WhenDisabled_ShouldNotCreateFile` — the test body acknowledges it "may pass or fail depending on environment" and has no assertion. | Not actually a test. |
| Every test gated by `SkipIfAuditRankNotEnabled()` — they Assert.Ignore by default in CI, so they provide ZERO coverage in CI runs. | Environment-dependent silent skip is worse than no test. Should be `[Explicit]` or mocked to control the static. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| RankAuditWriter.WriteAudit when disk is full / path is read-only — should log but not throw | High | Resilience — audit failures must never break ranking. |
| RankAuditWriter under concurrent writes from multiple threads with same requestId | Medium | Race-condition safety. |
| File path sanitization — requestId containing `../` must not write outside intended dir | High | Path-traversal security. |
| Tests restructured to mock `RankAuditWriter.Enabled` so they run in CI | High | Eliminate silent skips. |

---

### E.36 TheBox/ScoringInputsConverterTests.cs (~20 tests)

Source: `TheBox/ScoringInputsConverter.cs`. Converts Proto → Yass scoring inputs.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Convert_WithNullProviderId_ShouldThrowArgumentNullException` — same pattern as E.32; tests Protobuf library, not converter logic. | Exercises protobuf, not converter. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Convert with ALL proto fields populated (full round-trip) — verifies no field is silently dropped | High | Feature-vector completeness — missing field mapping silently zeros out a feature. |
| Convert preserves enum value when proto adds new enum variant (backward-compat) | High | Schema evolution safety. |
| Convert with deeply nested null (e.g. `ProvLoc.ProviderEmbedding.Id` null but vector populated) | High | Nested-null safety. |
| Convert with float precision round-trip — e.g. 0.1f + 0.2f, NaN, Infinity | Medium | Numerical fidelity. |
| Convert produces consistent output for identical inputs (determinism / no hidden state) | Medium | Snapshot safety. |
| Convert of oneof / optional fields — verify default vs unset distinction | High | Missing-feature default handling. |

---

### E.37 TheBox/SortOrderTests.cs (2 tests)

Source: `TheBox/SortOrder.cs`.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Both tests — trivial enum identity/inequality assertions (`LowerIsBetter.Should().Be(LowerIsBetter)` is tautological; `LowerIsBetter.Should().NotBe(HigherIsBetter)` is trivial). | Near-useless. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| None worth adding for a simple enum. Consider deleting the file entirely. | — | — |

---

### E.38 TheBox/SpecialtyExtractorTests.cs (~15 tests)

Source: `TheBox/SpecialtyExtractor.cs`. GetDisplaySpecialtyId, GetSpecialtyCategory, GetNormalizedPopularity, RequestCategoryMatchesDisplayCategory, SearchAndResultArePsych, SearchedProcedureIsDefaultForSpecialty, SearchedProcedureIsPopularForSpecialty.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| Several tests assert positive paths but leave a TODO-style comment like "Note: Actual category depends on loaded CSV data, but same IDs should match" — the tests pass regardless of CSV content. | Weak assertion — may pass even when CSV is misconfigured. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| SearchedProcedureIsDefaultForSpecialty with real procedure-specialty mapping (e.g. procedure "7" IS default for specialty "122") | High | CSV data correctness — positive path currently not really tested. |
| SearchAndResultArePsych when both are psych specialties (122, 148) — returns true | High | Positive-path coverage missing. |
| GetDisplaySpecialtyId with empty providerSpecialtyIds array (not null) — returns null or default | Medium | Array-vs-null branch. |
| GetSpecialtyCategory with specialty not in CSV — returns "unknown", not throws | High | Missing-feature default handling. |
| GetNormalizedPopularity with valid ID pair — returns a real positive number in expected range | High | Positive path currently only has null-sentinel tests. |

---

### E.39 VectorSearchEnricherBatchTests.cs (6 tests)

Source: `VectorSearchEnricher.cs::SearchInBatchesAsync` (MinBatchSize = 250, MaxNumParallelBatches = 2). Covers single-call below threshold, parallel above, partition/merge, failure propagation, cancellation.

#### Irrelevant Tests
_None flagged — good batching coverage._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Exactly 249 providers (below threshold by one) — verify single call, no batching | Medium | Off-by-one boundary. |
| Exactly 251 providers (above threshold by one) — verify 2 batches with unequal sizes | Medium | Off-by-one boundary. |
| 1000 providers (4 batches but MaxParallel=2) — verify parallelism cap | High | Resource cap enforcement. |
| Batch failure cancels in-flight sibling batches (not just fails after) | Medium | Resource efficiency. |
| Merged Hits deduplicate by providerId when two batches return the same provider | High | Dedup invariant. |
| TotalDocuments aggregated correctly when one batch returns 0 and one returns N | Medium | Edge case. |

---

### E.40 VectorSearchEnricherErrorTests.cs (5 tests)

Source: `VectorSearchEnricher.cs` error paths (embedding service OperationCanceled / InvalidOperationException + metric + log verification).

#### Irrelevant Tests
_None flagged — error-path coverage is essential._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| VectorSearchService (not embedding) throws — verify metric "vectorsearch.error" vs "embedding.error" are distinguishable | High | Observability — cannot diagnose incidents without distinct metrics. |
| Embedding returns empty float[] (length 0) — skip search, no-op, emit metric | High | Data-quality. |
| Embedding returns correct length but all NaN — reject, no-op, emit metric | High | Feature-vector integrity. |
| Partial failure (batch 1 succeeds, batch 2 fails) — verify partial enrichment OR full rollback (document which) | High | Consistency invariant. |

---

### E.41 VectorSearchEnricherTests.cs (~15 tests)

Source: `VectorSearchEnricher.cs`. ValidateRequest (no results / no query / short query / valid), ExtractProviderIds (dedup), BuildVectorLookup (null provider ID excluded, full hit fields preserved), EnrichResultsWithVectorData (matching / empty / null text filtered).

#### Irrelevant Tests
_None flagged — solid coverage._

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| EnrichResultsWithVectorData when same providerId appears at 2 locations — both enriched? Or only first? | High | Multi-location provider behavior. |
| EnrichResultsWithVectorData preserves existing ProviderTextData if already set (idempotency) | Medium | Re-enrichment safety. |
| BuildVectorLookup when two hits have same providerId — last-wins vs first-wins | High | Dedup policy determinism. |
| ValidateRequest with whitespace-only searchQuery ("   ") — treated as empty | Medium | Input-hardening. |
| EnrichResultsWithVectorData sets ScoreQuerySimilarity on ProvLoc (not on ProvLocResult) — snake-case vs camelCase field | Medium | Field-naming regression guard. |

---

### E.42 VectorSearchRankerTests.cs (10 tests)

Source: `VectorSearchRanker.cs`. NoOp on empty, descending sort by ScoreQuerySimilarity, unscored-preserve-input-order, mixed (scored first), tie-break by providerId ascending, metrics, ProcessorType/Name.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `ProcessorType_ShouldReturnVectorSearchRanker`, `ProcessorName_ShouldReturnVectorSearchRanker` | Constant-assertion. |
| `NextUpdateAsync_WithSingleResult_ShouldHandleGracefully` — asserts the same provider comes out; reveals no logic. | Trivial. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Ads (BannerInfo!=null) preserve position, are not reordered by vector score | High | Ads business rule. |
| Score monotonicity — higher ScoreQuerySimilarity always ⇒ higher rank | High | Monotonicity invariant. |
| NaN / Infinity scores — sanitized or rejected, not placed at arbitrary position | High | LightGBM feature-vector integrity. |
| Stable sort on ties — two equal scores preserve input order (not providerId-sorted) OR document that providerId-sorted is intended | High | Tie-break determinism — current test asserts providerId-ascending which may be *intentional*, but the invariant should be separately documented. |
| 500+ results — performance smoke (O(N log N) not O(N²)) | Low | Perf. |
| Result with ScoreQuerySimilarity = 0.0 — ranked with others-at-0 or treated as unscored? | High | Boundary semantic — 0.0 is a real cosine distance meaning "identical". |

---

### E.43 VirtualCareRankerTests.cs (7 tests)

Source: `VirtualCareRanker.cs`. Singleton instance, ProcessorType/Name, no-virtual-care-provider no-op, elevation-disabled no-op, elevate virtual care to top, preserve if already at top.

#### Irrelevant Tests
| Test | Reason |
|------|--------|
| `Instance_ShouldBeSingleton`, `ProcessorType_ShouldReturn*`, `ProcessorName_ShouldReturn*` | Constant-assertion pattern. |
| The hardcoded provider ID `pr_o4m6rX2nr0ynnbo13xGH6h` in tests — this is the prod virtual-care provider; testing with a real prod ID couples the test to ops data. | The id acts as a magic-string; if the ID is rotated, every test silently no-ops. Should be injected/mocked. |

#### Missing Tests
| Scenario | Priority | Why |
|----------|----------|-----|
| Virtual care provider has multiple locations — all get elevated, in a deterministic order | High | Multi-location edge. |
| Virtual care provider IS an ad (BannerInfo!=null) — verify elevation doesn't conflict with ads business rule | High | Ads + elevation interaction. |
| EnableVirtualCareElevation = true BUT virtual care provider is not in SearchEligibleResults (filtered upstream) — no-op, emit metric | High | Eligibility safety. |
| Virtual care ID configurable via settings — test with injected ID, not hardcoded prod ID | High | Hardcoding prod IDs is a test smell (see Irrelevant above). |
| Elevation metric `virtual_care_ranker.elevated_count` emitted | Medium | Observability. |
| After elevation, result ordering is deterministic (snapshot-stable) | High | Snapshot determinism. |
| Elevation does NOT duplicate the provider if already present in Results | High | Already lightly covered but no count invariant — verify Count remains unchanged when provider already at top. |

---

## Chunk E Summary

- **Total test files analyzed:** 43
- **Total tests across all files:** ~500
- **Irrelevant / low-value tests flagged:** prevalent in `ScorersTests`, `AlgoScoreTests`, `SortOrderTests`, `BoxDistanceBandModeTests`, `BoxProviderLocationTests`, `BoxSearchParametersTests`, `NoopScorerTests`, `RequestScoringInputsTests`, `VirtualCareRankerTests` (ProcessorType/Name), `VectorSearchRankerTests` (ProcessorType/Name), and in tests that exercise the Protobuf library rather than feature logic (`RealizationFeaturesTests`, `ScoringInputsConverterTests`).
- **Largest High-priority gaps:**
  1. **Ads business rules** — pervasive missing coverage: no test verifies ads (BannerInfo!=null) stay unmoved by ConstrainedScoreFusion, ScoreFusion, PresortRanker size-cap trimming, VectorSearchRanker, VirtualCareRanker, or RankRandomizer. Insurance-mismatched ad hidden state is untested. Self-serve-ad slot capping is untested.
  2. **Tie-break / stable-sort determinism** — missing across ScoreFusionProcessor, ConstrainedScoreFusionProcessor, CrossEncoderRanker, VectorSearchRanker, PresortRanker, RankingHelpers.SortOrganicPreservingAds.
  3. **Score monotonicity invariants** — missing for DistanceV3Scorer, PresortV3Scorer, LtvScorer, VectorSearchRanker, ScoreFusionProcessor. Currently no test asserts "higher-X ⇒ better-rank" as a general invariant.
  4. **LightGBM feature-vector integrity** — missing NaN/Infinity handling tests in OtherFeatures.CrossEncoderScore, QuerySimilarityScore, PersonalizationFeatures.ComputeDistance (div-by-zero in Cosine/Correlation/BrayCurtis), CategoricalLookup (missing-key sentinel).
  5. **Personalization-fallback safety** — when DeviceEmbedding is null, no test verifies that providers are still ranked correctly rather than dropped.
  6. **Missing-feature default handling** — scattered gaps across CategoricalLookup, SpecialtyCategoryMatchesSearchCategorical, GeoFeatures (zip/county not in table), RealizationFeatures (all-null-nested).
  7. **`MapleModelTests`** — may be missing V25 / V26 variants; doesn't check feature Type (Double vs Categorical); doesn't snapshot a baseline score.
  8. **Environment-gated silent skips** — `RankAuditWriterTests` skips ~11 tests in CI when `AUDIT_RANK` is unset; they provide zero coverage.
  9. **Protobuf-setter-throw tests** — `RealizationFeaturesTests.ProviderQualityNewPatientAppointments_Transform_WithNullQualities_ShouldThrowArgumentNullException` and `ScoringInputsConverterTests.Convert_WithNullProviderId_ShouldThrowArgumentNullException` test the Protobuf library, not the feature / converter code.
  10. **Magic-constant over-specification** — AvailabilityScorer, DistanceScorer, SpecialtyScorer tests that assert literal trained weights will break on routine model retraining.


---

## Chunk F — Search/Yass Unit Tests
*Directory: `tests/YassSharp.UnitTests/Search/Yass/` — orchestration, directory routing, whitelabel isolation, response shaping (40 files).*

### F.1 AlgoScoreTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | FeatureNames_WithEmptySequence_ShouldReturnEmpty | Symmetric empty-case for FeatureNames (only FeatureVector covered) | Low |
| 2 | FeatureVector_OrderMatchesRawFeatureSequence | Order stability between Vector/Names indices (needed for model inputs) | Medium |
| 3 | Serialize_RoundTrip_PreservesScoreAndFeatures | Response-shape stability over JSON | Medium |
| 4 | LinearFeatureScores_DefaultsToEmpty | Default init prevents NREs in downstream scoring | Low |
| 5 | FeatureVector_DuplicateFeatureNames_ArePreserved | Verify behavior (no dedupe) to avoid silently dropping features | Medium |

### F.2 AvailabilityFeaturesTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DailySummaries_DefaultsToEmptyList | Guards downstream LINQ against nulls | Low |
| 2 | HourlySummaries_DefaultsToEmptyList | Guards downstream LINQ against nulls | Low |
| 3 | HasAvailabilityInAllFourWeeks_ConsistentBooleanFlags | Booleans stay aligned when mutated independently | Medium |
| 4 | Serialize_RoundTrip_PreservesNumericFields | Response-shape stability (MinTimeToNextSlotMinutes etc.) | Medium |

### F.3 BannerInfoTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Priority_DefaultValue | Default ordering of banners | Low |
| 2 | Banner_WithDirectoryScopedConstraint_DoesNotLeakAcrossDirectories | Whitelabel isolation (GPH/Schweiger/monolith) for banner copy | High |
| 3 | BannerCopy_LongString_PreservedVerbatim | Ensures no truncation/sanitization breaks copy | Low |
| 4 | Serialize_RoundTrip_BannerInfo | Response-shape stability | Medium |

### F.4 DailySummaryTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DistinctHoursWithAvailability_DefaultsToEmptyList | Prevents NRE when scorer iterates | Low |
| 2 | FirstAvailableMinute_LessThanOrEqualToLastAvailableMinute | Invariant on minute range | Medium |
| 3 | NumSlots_CannotBeNegative | Guard against corrupt ES data | Medium |

### F.5 DayRangeTests.cs (9 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Contains_WhenStartDateAfterEndDate_ShouldReturnFalse | Inverted range defensiveness | Medium |
| 2 | Contains_WithEmptyStringDates_ShouldReturnFalse | Empty-string robustness | Medium |
| 3 | Contains_WithTimezoneSensitiveDates_StillMatchesAsDateOnly | Timezone-free comparison guarantee | Medium |
| 4 | Parse_DateRangeString_WithRangeOperator | "2026-02-04..2026-02-10" parsing path | High |

### F.6 FacetBucketTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | Properties_ShouldBeSettable | Placeholder — does not actually set any properties, only asserts NotBeNull |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Properties_Key_DocCount_Settable | Actual bucket fields (key, docCount) surfaced in facets | High |
| 2 | Serialize_RoundTrip_FacetBucket | Response-shape stability for facet aggregations | Medium |
| 3 | FacetBucket_EmptyDocCount_Defaults | Default value when aggregation empty | Low |

### F.7 Filtering/AvailabilityFiltererTests.cs (9 tests)

**Irrelevant Tests:** None — all tests are relevant (but all are metadata-only, no behavior).

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | OfficeHoursFilterer_NextUpdate_RemovesOutsideOfficeHours | Actual filtering logic for office hours | High |
| 2 | DayAvailabilityFilterer_NextUpdate_FiltersOutsideDayRanges | Actual day-range filter behavior | High |
| 3 | EnhancedAvailabilityFilterer_NextUpdate_AppliesBothDayAndTime | Composite enhanced-availability filter | High |
| 4 | EnhancedAvailabilityFilterer_WhenNoEnhancedFilters_NoOp | Short-circuits when irrelevant (perf + correctness) | Medium |
| 5 | Filterer_EmptyResults_ReturnsEmptyWithoutError | Defensive branch | Medium |
| 6 | Filterer_UpdatesTotalHitsAfterFiltering | Response totals remain accurate | High |

### F.8 Filtering/DuplicateProviderLocationsFiltererTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | NextUpdate_PreservesAdditionalProvLocsBucket | Verify duplicates aren't lost — rolled into AdditionalProvLocs | High |
| 2 | NextUpdate_UpdatesAggregationsBeyondInNetwork | All/BestMatch/etc. aggregation counts updated | High |
| 3 | NextUpdate_WhenAllResultsDuplicates_ReturnsSingle | Degenerate case | Medium |
| 4 | NextUpdate_MixedInNetworkAndOutOfNetworkDuplicates | Verify group-scoped dedupe logic | High |
| 5 | NextUpdate_WithNullMatchedQueries_HandledSafely | Null-safety on matchedQueries list | Medium |

### F.9 Filtering/EnhancedAvailabilityMatchingEnricherTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant but enrichment behavior is untested (noted in file header).

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | NextUpdate_MatchesProvLocsSatisfyingDayAndTimeFilters | Core enrichment: matched availability records | High |
| 2 | NextUpdate_WithoutEnhancedFilters_IsNoOp | Guard against accidental enrichment | Medium |
| 3 | NextUpdate_ProvLoc_WithNoAvailability_SetsEmptyMatches | Defensive path | Medium |
| 4 | Validate_WhenEnricherInDecoratorsButNotResultEnrichers_ReturnsFalse | Placement validation | Medium |
| 5 | NextUpdate_MixedMatchesPreserveRankOrder | Ordering invariant post-enrichment | High |

### F.10 Filtering/PostEsFiltererTests.cs (6 tests)

**Irrelevant Tests:** None — all tests are relevant (metadata-only).

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | UnbookableFilterer_RemovesUnbookableProvLocs | Core filtering logic | High |
| 2 | UnbookableFilterer_KeepsSpoResults | SPO must not be filtered | High |
| 3 | ProviderBadgesFilterer_FiltersByBadgeConstraints | Badge-based filtering behavior | High |
| 4 | ProviderBadgesFilterer_WhenNoBadgeFilter_NoOp | Short-circuit path | Medium |
| 5 | PostEsFilterers_UpdatesAggregationsAfterRemoval | Consistency with aggregations | High |
| 6 | PostEsFilterers_UpdatesTotalHitsAfterFiltering | Response-shape correctness | High |

### F.11 GroupsDictionaryConverterTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | RoundTrip_WithAllSearchResultGroups_Preserved | Serialize then deserialize covers every enum value | Medium |
| 2 | Read_WithMalformedValue_ShouldSkipOrThrowGracefully | Numeric-parse failure path | Medium |
| 3 | Write_PreservesDoublePrecision | Score precision kept (avoids drift in rankings) | Medium |
| 4 | Read_WithDuplicateKeys_KeepsLastOrRejects | Documented behavior on duplicates | Low |

### F.12 HourlySummaryTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | FirstAvailableDay_LessOrEqualLastAvailableDay | Day-range invariant | Medium |
| 2 | NumDaysWithSlotInHour_NonNegative | Guard against bad ES data | Medium |
| 3 | Serialize_RoundTrip_PreservesNullVsZero | Avoids conflating null with zero in inference features | Medium |

### F.13 InferenceRequestTests.cs (7 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Headers_DefaultsToEmpty | Avoid NRE when dispatching | Low |
| 2 | InferenceRequest_Serialize_RoundTrip | Request-shape stability when sent to inference service | High |
| 3 | RankerName_AllKnownRankers_AreAcceptedValues | Whitelist of rankers (TheBoxRanker, OrganicOnlyBoxRanker, etc.) | Medium |
| 4 | Headers_CorrelationIdPropagated | Correlation-id propagation on downstream calls | High |
| 5 | AlgorithmName_Empty_ShouldStillBeValid_OrValidated | Defines acceptance semantics | Medium |

### F.14 InMemoryPagerTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant (metadata-only).

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | NextUpdate_PaginatesByPageAndPageSize | Core paging behavior | High |
| 2 | NextUpdate_BeyondLastPage_ReturnsEmpty | Out-of-range paging | Medium |
| 3 | NextUpdate_PreservesTotalHits | Total count unchanged by in-memory paging | High |
| 4 | NextUpdate_WithItemOffset_UsedInsteadOfPage | Offset-mode paging | Medium |
| 5 | NextUpdate_PageSizeZero_ShouldReturnEmptyOrAll | Edge case documented | Medium |

### F.15 InsuranceFeaturesTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ProbabilityProviderTakesInsurance_InValidRange_0to1 | Value-range assertion (avoids ML feature blowup) | Medium |
| 2 | AcceptsInsurance_vs_Probability_Consistency | Flag-field consistency | Medium |
| 3 | Serialize_RoundTrip_PreservesNullFields | JSON null vs missing | Medium |

### F.16 LocalDateTimeConverterTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Read_WithMalformedDate_ShouldThrowOrReturnDefault | Defensive parse path | Medium |
| 2 | Write_Read_RoundTrip_PreservesMilliseconds | Precision preservation | Medium |
| 3 | Read_WithTimezoneSuffix_StripsOrRejects | Documents expected behavior when input has +00:00 | Medium |
| 4 | Write_DefaultDateTime_FormatsConsistently | DateTime.MinValue safety | Low |

### F.17 NoAvailabilityReasonTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Enum_ShouldHaveExpectedValues | Tautological — asserts X.Equals(X) rather than checking integer values or name stability |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Enum_StringRoundTrip_StableNames | Response-shape stability (consumer-facing string names) | High |
| 2 | Enum_HasExpectedMemberCount | Guards against accidental add/remove | Medium |
| 3 | Enum_SerializedAsString_NotNumeric | JSON wire-format contract | High |

### F.18 NullableLocalDateTimeConverterTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | RoundTrip_NullValue | Ensures null written and read back as null | Medium |
| 2 | Read_WithMalformedDate_Handled | Defensive parse | Medium |
| 3 | Write_PreservesMilliseconds | Precision | Medium |

### F.19 NullableZonedDateTimeConverterTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Read_WithUtcZSuffix_Handled | "Z" suffix parse path | Medium |
| 2 | Write_WithUtcOffset_FormatsAsPlus00 | Consistent wire-format | Medium |
| 3 | RoundTrip_PositiveOffset | E.g. +09:00 Tokyo | Medium |
| 4 | Read_WithMalformedInput_Handled | Defensive parse | Medium |

### F.20 PatientFriendlinessCategoryTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Enum_ShouldHaveExpectedValues | Tautological — asserts X.Equals(X) |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Enum_SerializedAsStableString | JSON wire format (Friendly/Unfriendly/Neutral) | High |
| 2 | Enum_HasExpectedMemberCount | Guards against inadvertent enum changes | Medium |
| 3 | Enum_DefaultValue | Verify default (Neutral?) to avoid accidental Friendly/Unfriendly | Medium |

### F.21 PostEsAuditProcessorTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | NextUpdate_AppendsAuditEntryToChain | Audit-chain append behavior | High |
| 2 | NextUpdate_CapturesStepNumberInAudit | Step number surfaces in audit payload | Medium |
| 3 | NextUpdate_PreservesOriginalResponse | No mutation beyond chain append | High |
| 4 | Audit_IncludesCorrelationId_AndTelemetryFields | Telemetry coverage | High |

### F.22 PresortAvailabilityFeaturesTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Week1ThroughWeek4_AllDefaultFalse | Default booleans are false (zero-default safety) | Medium |
| 2 | DaysToFirstAvailability_SentinelValue1000_MeansUnavailable | Explicit meaning of 1000 sentinel value | High |
| 3 | HasAvailNext3Days_ImpliedByWeek1 | Consistency between Next3 and Week1 flags | Medium |

### F.23 PreviewProvLocResultTests.cs (12 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Preview_DoesNotExposePhiOrSensitiveFields | Preview sanitization — ensures no NPI/PHI leakage | High |
| 2 | Preview_HasBudgetFrom_NotLeakedToConsumer | Field-scope stability | High |
| 3 | PreviewProvLocResult_IsJsonSerializable_WithoutCircularReferences | Shape stability | Medium |
| 4 | Preview_ProvLoc_IsEsExternalProvider_Not_EsProviderLocation | Type-boundary check (separate from organic ProvLocResult) | High |
| 5 | Preview_AuthorizationBypass_PreventedOnDirectInstantiation | Preview-only flags not abusable | High |

### F.24 ProviderDeduperTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | NextUpdate_MaxAdditionalProvLocs_Truncated | Cap on additional locations (if applicable) | Medium |
| 2 | NextUpdate_WithDirectoryScopedProviders_DoesNotMergeAcrossDirectories | Whitelabel isolation (GPH=963 vs -1) | High |
| 3 | NextUpdate_SpoResults_BypassedByDeduper | SPO preserved | High |
| 4 | NextUpdate_PreservesOriginalScoresOnWinner | Winning location retains score | High |
| 5 | NextUpdate_EmptyResults_ReturnsEmpty | Defensive path | Medium |

### F.25 ProvLocDotTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Constructor_ShouldInitializeProperties | Placeholder — only asserts NotBeNull |
| 2 | Properties_ShouldBeSettable | Placeholder — does not set any properties |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Properties_ProviderId_Lat_Lon_Settable | Real fields on the dot (map marker) | High |
| 2 | Serialize_RoundTrip_ProvLocDot | Response-shape stability | Medium |
| 3 | ProvLocDot_CoordsOutOfRange_AreValidatedOrAccepted | Lat/lon sanity | Medium |

### F.26 ProvLocFeaturesTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ProviderQualities_ParsedFromCommaString | If consumer splits these, document parsing | Medium |
| 2 | OffersVideoVisit_Defaults | Boolean default prevents leakage of "video" when unset | Medium |
| 3 | Serialize_RoundTrip_AllFields | Shape stability for scoring inputs | Medium |

### F.27 ProvLocGeoFeaturesTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | DistanceMi_Negative_Rejected | Guard against bad distance | Medium |
| 2 | VirtualStates_Empty_DoesNotImplyIsProvLocVirtual | Flag independence | Medium |
| 3 | StateCounty_DerivedFromStateAndCounty | Composite consistency | Low |
| 4 | IsProvLocVirtual_True_WithNonEmptyVirtualStates | Logical invariant | Medium |

### F.28 ProvLocResultsContainerTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Aggregations_Settable | Important field used by facets | High |
| 2 | TotalHits_Settable | Core field for response header | High |
| 3 | Algorithm_Settable | Algorithm reference propagation | High |
| 4 | Results_DefaultsToEmptyList_Strict | Assert default length 0, not just non-null | Medium |

### F.29 ProvLocResultTests.cs (12 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | FromEsHit_WithMissingMandatoryFields_Throws | Guard against malformed ES hits | High |
| 2 | FromEsHit_ParsesHasBudgetFromTimezones | Timezone parse correctness for spend-lock decision | High |
| 3 | WithAvailabilityScore_DoesNotMutateOriginal | Immutability invariant | High |
| 4 | FromEsHit_WithInvalidHasBudgetFrom_DefaultsToInBudget | Defensive parse | Medium |
| 5 | FromEsHit_PopulatesRanksWithPresortRank | Presort rank recorded in Ranks list | Medium |
| 6 | FromEsHit_DirectoryScopedEsHit_NotLeakedAcrossDirectories | Whitelabel isolation via payload.directoryId | High |
| 7 | FromEsHit_SetsCorrelationIdOrAuditFields | Telemetry propagation | Medium |

### F.30 ProvLocScoringInputsTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Defaults_AllSubFeatures_NotNull | Defensive init for ML model | High |
| 2 | Serialize_RoundTrip_PreservesAllFields | Shape stability for inference input | High |
| 3 | PresortVirtualAvailability_OnlyForVirtualProviders | Logical invariant | Medium |

### F.31 RanksTupleListConverterTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Read_WithMalformedNested_ShouldThrowOrSkip | Defensive parse | Medium |
| 2 | Read_WithThreeElementArray_Fails_Or_IgnoresThird | Length-validation behavior | Medium |
| 3 | RoundTrip_DoesNotReorder | Order preservation | Medium |

### F.32 Reconciliating/DentalPracticeSpecialtyRemapperTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant (metadata-only).

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | NextUpdate_RemapsDentalPracticeSpecialties | Core remap behavior | High |
| 2 | NextUpdate_NonDentalProvLocs_Unchanged | Negative case | High |
| 3 | NextUpdate_WithDirectoryScopedResults_NoCrossTalk | Whitelabel isolation of remap | High |
| 4 | NextUpdate_EmptyResults_Safe | Defensive path | Medium |

### F.33 ResponseInfoTests.cs (11 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 11 | BucketAggregation_WhenAggregationsExists_ShouldCallGetBuckets | Asserts null due to inability to mock — effectively duplicates the null-aggregations case. Rewrite or skip. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | BucketAggregation_WhenFacetExists_ReturnsBuckets | Real aggregation resolution path | High |
| 2 | Copy_DeepCopyOrShallowCopy_ForMutableCollections | Semantics of Copy() for downstream safety | High |
| 3 | FromOrganicResults_WithSpoResults_PreservesSpo | SPO carryover through conversion | High |
| 4 | ResponseInfo_PropagatesSearchRequestIdAndCorrelationId | Correlation-id propagation | High |
| 5 | ResponseInfo_DirectoryScopedResults_NotLeaked | Whitelabel isolation | High |
| 6 | WithResults_WithNullList_ShouldThrow_OrAcceptEmpty | Null-safety | Medium |

### F.34 ResponseUpdateTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Response_ChangeInfo_LazyEvaluated | Ensures expensive ChangeInfo not called eagerly | Medium |
| 2 | Response_ChangeInfoReturnsNull_HandledSafely | Defensive path | Medium |
| 3 | Response_AuditChainOrder_IsChronological | Ordering invariant across many processors | High |
| 4 | Response_WithDuplicateProcessorType_AppendsSeparateEntries | Each invocation is logged separately | Medium |

### F.35 ReviewsFeaturesTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | AverageRating_Within0to5 | Range invariant (ML feature bounds) | Medium |
| 2 | ReviewRate_Within0to1 | Probability range check | Medium |
| 3 | TotalReviewCount_NonNegative | Guard against bad ES data | Medium |
| 4 | IsShowingReviews_FalseImpliesNoRating | Consistency invariant | Medium |

### F.36 SearchParamsTests.cs (49 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Create_WithDirectoryIdGPH_963_RoutesCorrectly | Directory routing for GPH whitelabel | High |
| 2 | Create_WithDirectoryIdSchweiger_459_RoutesCorrectly | Directory routing for Schweiger whitelabel | High |
| 3 | Create_WithDirectoryIdMinus1_RoutesToMonolith | Default monolith directory | High |
| 4 | DirectoryId_InferredFromFinatraRequestHeaders_Correctly | Header-driven directory resolution | High |
| 5 | Create_WithUnknownDirectoryId_RejectedOrDefaulted | Directory-not-found handling | High |
| 6 | SearchParams_RequestHeaders_PreserveCorrelationId | Correlation-id propagation | High |
| 7 | IsFlagOn_DirectoryScopedExperiment_DoesNotLeakAcrossDirectories | Whitelabel flag isolation | High |
| 8 | HasEnhancedAvailabilityFilters_WithOnlyTimeRanges_ReturnsTrue | Mirrored coverage of DayRanges-only case (direct) | Medium |
| 9 | DayRangesFilter_WithDateRangeOperator_DotDot | Direct-construction counterpart for ".." parsing | Medium |
| 10 | SearchParams_SearchRequestId_AutoGeneratedIfEmpty | Request-id guarantee | Medium |
| 11 | Debug_VerbosityLevels_AllAccepted | Enum-range coverage | Low |
| 12 | IsVideoVisitOnlyFilter_MultipleFilterEntries_IntersectCorrectly | Multi-entry AND semantics | Medium |
| 13 | Create_WithPreviewMode_SanitizesSensitiveFilters | Preview sanitization | High |
| 14 | Create_WithAuthorizationBypassFlag_IgnoresBypass | Auth bypass attempts rejected | High |
| 15 | ShouldFilterSpendCappedProviders_ForWhitelabelDirectories | Per-whitelabel spend-lock behavior | High |

### F.37 SpecialtyFeaturesTests.cs (1 test)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Properties_CanBeNull | Nullable-default path | Medium |
| 2 | NormPopularityCount_Within0to1 | Probability range | Medium |
| 3 | Serialize_RoundTrip_AllFields | Shape stability | Medium |
| 4 | SpecialtyMatchesSearch_False_WhenCategoryMatchesOnly | Distinct semantics of specialty vs category | High |
| 5 | DisplaySpecialtyId_EmptyString_Handled | Defensive path | Low |

### F.38 SpendLockStatusTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Enum_ShouldHaveExpectedValues | Tautological — asserts X.Equals(X) |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Enum_SerializedAsString_NotNumeric | JSON wire-format (consumer contract) | High |
| 2 | Enum_HasExpectedMemberCount | Detect inadvertent enum changes | Medium |
| 3 | Enum_DefaultValue_IsInBudget | Zero-value semantic | High |

### F.39 TimeFeaturesTests.cs (1 test)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | LocalTimeNow_DefaultsToMinValue_OrCurrent | Default semantics | Medium |
| 2 | LocalTimeForSearch_NotLaterThanLocalTimeNow | Invariant guard | Medium |
| 3 | Serialize_RoundTrip_PreservesDateTimeKind | Timezone handling for ML features | High |
| 4 | LocalTime_TimezoneAwareness_DerivedFromUserLocation | Whitelabel-aware time handling | High |

### F.40 TimeRangeTests.cs (10 tests)

**Irrelevant Tests:** None — all tests are relevant.

| Test # | Test Name | Issue |
|--------|-----------|-------|

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Contains_WhenRangeInverted_ShouldReturnFalse | Start > End defensiveness | Medium |
| 2 | Contains_NegativeMinutes_Rejected | Input validation | Medium |
| 3 | Contains_MinutesOver1440_Behavior | Over-24h input documented | Medium |
| 4 | Parse_FromFilterString_480_DotDot_1200 | Parse path used by SearchParams | High |
| 5 | TimeRange_Equality_And_GetHashCode | Record/class equality semantics | Low |



---

## Chunk G — Search/Types + Search/Utils Unit Tests
*Directories: `tests/YassSharp.UnitTests/Search/Types/` (18 files) and `tests/YassSharp.UnitTests/Search/Utils/` (12 files).*

### G.1 CostPlanTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property get/set test; only reflects compile-time shape. |
| 2 | State_CanBeNull | Trivial nullable-property set-and-read; no logic exercised. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesJsonPropertyNames | CostPlan serializes/deserializes with camelCase `specialtyId`, `state`, `cost` per `[JsonPropertyName]` | High |
| 2 | Cost_DefaultIsZero | Newly constructed CostPlan has Cost == 0 (not covered today) | Medium |
| 3 | Deserialize_MissingState_LeavesNull | JSON without `state` property yields null State | Medium |
| 4 | Deserialize_ExtraFields_IsIgnored | Unknown JSON keys don't break deserialization | Low |

### G.2 EmbeddingTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property test; no logic. |
| 2 | EmbeddingValues_CanBeNull | Trivial nullable-property set-and-read. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_MapsEmbeddingToEmbeddingValues | `[JsonPropertyName("embedding")]` round-trips into EmbeddingValues | High |
| 2 | Id_DefaultsToEmptyString | Default Id is string.Empty, not null | Medium |
| 3 | EmbeddingValues_EmptyArray_RoundTrips | 0-length double[] serialize/deserialize yields empty array | Medium |
| 4 | LargeEmbedding_1024Dim_RoundTrips | 1024-element embedding round-trip doesn't lose precision | Low |

### G.3 EsAvailabilityTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property test across all nullable flags. |
| 2 | Properties_CanBeNull | Trivial — only asserts default null on 4 of the ~13 fields. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_PreservesPascalCase | ES uses PascalCase; serialization must output `HasAvailability` etc. (no JsonPropertyName → requires explicit naming policy) | High |
| 2 | Default_AllNullableFieldsAreNull | All 13 nullable fields default to null (current test covers only 4) | Medium |
| 3 | Deserialize_FromEsDocument_Shape | Sample ES-style JSON deserialises into correct fields including all HasInWeekN | High |
| 4 | DaysToFirstAvailability_NegativeValue_Allowed | int? accepts negative values (edge case for no-availability) | Low |

### G.4 EsCoordinateTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_ShouldBeMutable | Trivial — just reassigns props; no logic. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesLowerCaseLatLon | `[JsonPropertyName("lat")]` and `"lon"` preserved across round-trip | High |
| 2 | Deserialize_FromEsGeoPoint | Parsing `{"lat":40.7,"lon":-74.0}` produces correct Lat/Lon | High |
| 3 | Lat_Lon_DefaultToZero | New EsCoordinate has Lat==0 and Lon==0 | Low |

### G.5 EsExternalProviderTests.cs (9 tests)

**Irrelevant Tests:** None — all tests are relevant. They exercise the `ConvertToEsProviderLocation` mapping logic (empty locations, single/multi-location, null MainSpecialty, null Specialties, null Coordinate, null City/State/Zip, default field shape).

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ConvertToEsProviderLocation_PopulatesLanguages_WhenLocationHasLanguages | Languages list is copied, not left empty | High |
| 2 | ConvertToEsProviderLocation_PreservesMonolithProfessionalId | int/long NPI/monolith IDs survive conversion (result.MonolithProfessionalId not asserted today) | High |
| 3 | ConvertToEsProviderLocation_WithVirtualLocation_SetsVirtualAvailability | Non-null result.VirtualAvailability when source has virtual flag | Medium |
| 4 | ConvertToEsProviderLocation_WithAvailabilityScore_Zero | `Availability.AvailabilityScore = 0` still yields non-null Availability | Medium |
| 5 | ConvertToEsProviderLocation_WithZipOnly_PreservesZip | Only Zip set (no city/state) preserves Zip correctly | Medium |
| 6 | ConvertToEsProviderLocation_MainSpecialtyId_IsEmptyString | MainSpecialty.Id is always "" (current test asserts but doc the invariant) | Low |
| 7 | ConvertToEsProviderLocation_PreservesIsSearchableFlag | If source has IsSearchable=false, verify it does/doesn't carry over | Medium |

### G.6 EsLanguageTests.cs (1 test)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesLowerCaseId | `[JsonPropertyName("id")]` and `"name"` round-trip correctly | High |
| 2 | Id_AcceptsLongValues | Id is long — verify values > int.MaxValue survive | Medium |
| 3 | Deserialize_MissingName_FailsOrDefaults | name property missing → how does deserialization behave? (Name is non-nullable `null!`) | Medium |

### G.7 EsSpecialtyTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Name_CanBeNull | Trivial nullable set-and-read. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCaseProperties | `[JsonPropertyName("id"/"monolithId"/"name")]` applied correctly | High |
| 2 | MonolithId_DefaultIsZero | Default int MonolithId is 0 | Low |
| 3 | Deserialize_FromEsPayload | Specialty from real ES payload shape parses cleanly | Medium |

### G.8 FacetTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeEmpty | Trivial — just sets empty strings. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCase | `[JsonPropertyName("b64Id"/"name"/"legacyId")]` round-trip | High |
| 2 | DefaultInstance_AllEmptyStrings | `new Facet()` → B64Id/Name/LegacyId all "" | Medium |
| 3 | Deserialize_MissingLegacyId_FallsBackToDefault | Missing legacyId property defaults to "" (initializer applied) | Medium |

### G.9 InsuranceSettingsTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeNull | Trivial nullable set-and-read. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_PreservesPascalCase | Source has no JsonPropertyName — default naming policy controls output; confirm "AcceptsInNetwork" PascalCase per ES docs | High |
| 2 | Default_AllFieldsNull | Newly constructed InsuranceSettings has all three nulls | Low |
| 3 | Deserialize_PartialPayload | JSON with only AcceptsInNetwork leaves other two as null | Medium |

### G.10 InteractionTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeZero | Trivial — just asserts ints == 0 after explicit assignment. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCase | JsonPropertyNames `trackingId`, `numDeviceClicks`, etc. round-trip | High |
| 2 | DefaultInstance_StringsAreEmpty_IntsAreZero | Default Interaction has empty-string TrackingId/ProviderId, all int counters = 0 | Medium |
| 3 | Deserialize_NegativeCounts_Allowed | JSON with negative click/appt counts doesn't throw | Low |

### G.11 LocationSummaryTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | TimeZone_CanBeNull | Trivial nullable set-and-read. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCase | `[JsonPropertyName("monolithId"/"timeZone")]` | High |
| 2 | MonolithId_AcceptsLong | long MonolithId survives values > int.MaxValue | Medium |
| 3 | Deserialize_WithIanaTimeZone | TimeZone "America/New_York" round-trips verbatim | Low |

### G.12 PracticeDetailsTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeNull | Trivial nullable set-and-read on all fields. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCase | `[JsonPropertyName("id"/"cloudPracticeId"/"name"/"url")]` | High |
| 2 | Deserialize_FromEsPayload | Real ES practice payload parses into correctly populated PracticeDetails | Medium |
| 3 | Url_AcceptsInvalidUri_String | Url is a raw string — ensure non-URI strings don't throw on deserialize | Low |

### G.13 PracticeFeaturesTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeZero | Trivial — asserts defaults after explicit zero assignment. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCase | JsonPropertyName attributes (`practiceId`, `cancelRateLast90Days`, etc.) | High |
| 2 | CancelRate_FloatPrecision_Preserved | Float value 0.1234f round-trips without double-conversion loss | Medium |
| 3 | DefaultInstance_ZeroAndEmpty | `new PracticeFeatures()` has empty PracticeId and zero numeric fields | Medium |

### G.14 ProviderLocationRuleTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeNull | Trivial nullable set-and-read. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesPascalCase | JsonPropertyNames `GuidedSearch`, `Predicates`, `Action` (all PascalCase for ES) | High |
| 2 | Deserialize_EmptyPredicatesArray_PreservesEmpty | `"Predicates":[]` → non-null empty list, not null | Medium |
| 3 | Deserialize_MultiplePredicates_PreservesOrder | Predicate order is preserved | Medium |

### G.15 ProviderQualitiesTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeFalse | Trivial — default bool is false, test just restates that. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesPascalCase | JsonPropertyNames exactly PascalCase (`HasNewPatientAvailability`, etc.) — ES contract | High |
| 2 | DefaultInstance_AllFalse | Default `new ProviderQualities()` has all bools false without explicit set | Low |
| 3 | Deserialize_FromEsPayload | ES payload shape parses correctly | Medium |

### G.16 ProvLocResultProviderQualitiesTests.cs (1 test)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_ApiContract_PascalCase | API-contract JsonPropertyNames (`NewPatientAppointments`, `OffersVideoVisits`, etc.) preserved; critical because this is the response DTO | High |
| 2 | DefaultInstance_AllFalse | Default ProvLocResultProviderQualities has all bools false | Low |
| 3 | Deserialize_ResponseShape | Realistic client-facing JSON deserializes correctly | Medium |
| 4 | DoesNotEqual_ProviderQualities_ShapeNameOverlap | Field names diverge from ES ProviderQualities — ensure no confusion in mapping | Medium |

### G.17 RealizationPracticeFeaturesTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Trivial auto-property. |
| 2 | Properties_CanBeNull | Trivial nullable set-and-read. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | JsonRoundTrip_UsesCamelCase | JsonPropertyNames (`rescheduleRateL180day`, `cancelationRateUnbounded`, etc.) | High |
| 2 | DefaultInstance_AllNullExceptPracticeId | `new RealizationPracticeFeatures()` has PracticeId="" and 8 nulls | Medium |
| 3 | Deserialize_PartialPayload_DoesNotThrow | Payload with only some of the 8 rate fields leaves others null | Medium |

### G.18 RealizationProviderFeaturesTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | Properties_ShouldBeSettable | Only tests 3 of the ~22 fields defined on the source class. Trivial auto-property. |
| 2 | Properties_CanBeZero | Same 3 fields; restates default behavior. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | AllFields_Settable_AndRoundTrip | Exercise all 22 fields (6 Realization rates, 3 reschedule rates, 6 cancel rates, 3 prov-cancel rates, plus Point1DImpr, Cum14DCvr, Cum30DCvr, Cum60DCvr, Cum60DCtr, Cum90DCvr, Cum90DCtr, Cum90DImpr, Cum60DCvrClicks, Cum90DCvrClicks) | High |
| 2 | JsonRoundTrip_UsesCamelCase | All JsonPropertyName attributes preserved | High |
| 3 | Cum14DCvr_ZeroDefault | Default instance has zero for all analytic fields | Medium |
| 4 | Deserialize_MissingAnalyticsFields_DefaultsToZero | Legacy payloads lacking Point1DImpr/CumNN fields deserialize cleanly with zeros | Medium |
| 5 | ProviderId_DefaultsToEmptyString | `new RealizationProviderFeatures()` has ProviderId="" | Low |

### G.19 AuditWriterTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant. They exercise Development (local file) and Staging (S3 mock) branches with real bucket name and key.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | Persist_WithNullOrEmptyGuid_IsNoOp | Persist(null) / Persist("") returns without throwing, no file created | High |
| 2 | AuditWrite_BeforeStart_IsSilentlyIgnored | Writes without prior Start() do not create entries | High |
| 3 | AuditWrite_AfterPersist_IsIgnored | Post-Persist AuditWrite does not resurrect the entry | High |
| 4 | Start_CleansUpStaleEntries_OlderThanMaxAge | Entries > 2 min old are removed when Start is called for a new guid | High |
| 5 | RecordTime_AddsTimingToEntry | RecordTime appends timing record and it appears in Persist output | High |
| 6 | GetAuditContent_ReturnsJsonNode_WithEndTime | GetAuditContent yields JsonNode including endTime and timings (no cleanup) | High |
| 7 | Persist_Production_UsesProdBucket | ASPNETCORE_ENVIRONMENT=Production writes to `yass-audit-prod` | High |
| 8 | Persist_Development_WritesLocalButNotS3 | Development mode writes only local, never calls S3 PutObject | High |
| 9 | WriteSpoAudit_WritesExpectedFilename | `{requestId}_{filename}_csharp.json` under `provLocSearch/` dir with tag `DataClass=non-sensitive` on S3 | High |
| 10 | WriteSpoAudit_StripsJsonExtension | filename="foo.json" → output file `..._foo_csharp.json` (no double .json) | Medium |
| 11 | SerializeValue_HandlesDictionary_Recursively | Nested dict values pass through SerializeValue (primitives preserved) | Medium |
| 12 | SerializeValue_ParsesElasticQueryString | String starting with `{` and containing "query" parses to JsonNode | Medium |
| 13 | SerializeValue_InvalidJsonString_ReturnedAsString | ParseElasticQuery fallback path returns raw string on parse error | Medium |
| 14 | Persist_AddsTotalElapsedMs_WhenTimingsPresent | totalElapsedMs key appears when timings recorded | Medium |
| 15 | SanitizeEndpoint_ReplacesNonAllowedChars | Endpoint with spaces/special chars sanitized to `_` | Medium |
| 16 | TempDebugJson_HandlesNullObject | TempDebugJson(label, null) does not throw and writes wrapper | Low |

### G.20 AvailabilityUtilsTests.cs (2 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | GetAvailabilityFieldName_WithDefaultParams_ReturnsAvailabilityField | Tests only the default branch — but the logic has 3 branches (feature-flag on + new patient false, feature-flag on + directoryId > 0, default). This test alone isn't irrelevant but coverage is very narrow. |
| 2 | GetAvailability_WithDefaultParams_ReturnsAvailability | Same — only default branch. |

*(Both tests are valid but narrow; retained.)*

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | GetAvailability_WhenFlagOnAndNotNewPatient_ReturnsExistingAvailability | Flag on + IsNewPatient=false → selector picks ExistingAvailability | High |
| 2 | GetAvailabilityFieldName_WhenFlagOnAndNotNewPatient_ReturnsExistingAvailabilityField | Same branch — field name becomes `ExistingAvailability.{property}` | High |
| 3 | GetAvailability_WhenFlagOnAndWhiteLabel_ReturnsWhiteLabelNewAvailability | Flag on + DirectoryId > 0 + IsNewPatient != false → WhiteLabelNewAvailability | High |
| 4 | GetAvailabilityFieldName_WhenFlagOnAndWhiteLabel_ReturnsWhiteLabelField | Same branch for field name | High |
| 5 | GetAvailability_WhenFlagOff_AlwaysUsesAvailability | Flag off + any isNewPatient + any directoryId → Availability | High |
| 6 | GetAvailability_WhenExistingAvailabilityNull_ReturnsNull | Branch picks ExistingAvailability but source has null — selector returns null cleanly | Medium |
| 7 | GetAvailabilityFieldName_WithEmptyProperty_StillConcatenates | property="" yields "Availability." without throwing | Low |

### G.21 BrandFilterUtilsTests.cs (8 tests)

**Irrelevant Tests:** None — all tests are relevant. They cover ExtractBrandSearchFilters across null/empty/valid/invalid/multi-filter/empty-array/non-brand-field permutations.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | IsAffiliated_WithEmptyFilters_ReturnsFalse | IsAffiliated short-circuit when brandFilters is empty | High |
| 2 | IsAffiliated_MatchingBrandAffiliation_ReturnsTrue | provLoc.BrandAffiliations contains filter.LegacyId → true | High |
| 3 | IsAffiliated_MatchingPlacemarkAffiliation_ReturnsTrue | placemark affiliations match on BrandPlacemarkAffiliations.legacyId field | High |
| 4 | IsAffiliated_NonMatching_ReturnsFalse | Filters present but no overlap → false | High |
| 5 | IsAffiliated_WithUnknownField_ChecksBothSets | Unknown Field falls through to match either brand or placemark set | High |
| 6 | IsAffiliated_WhenFilterLegacyIdNull_SkipsFilter | Filter with null LegacyId is ignored | Medium |
| 7 | IsAffiliated_WhenProvLocAffiliationsNull_HandlesGracefully | Null BrandAffiliations and/or BrandPlacemarkAffiliations → no NRE | High |
| 8 | ExtractBrandSearchFilters_WithEmptyLegacyId_Skips | Empty-string value `""` is skipped (source has `!IsNullOrEmpty` guard) | Medium |
| 9 | ExtractBrandSearchFilters_TermNotObject_Skips | `"term": "scalar"` not object — skipped cleanly | Medium |
| 10 | ExtractBrandSearchFilters_RootNotArray_ReturnsEmpty | JSON object (not array) at root returns empty | Medium |

### G.22 ClockTests.cs (11 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 2 | SystemClock_Now_ShouldReturnCurrentTime | Compares `SystemClock.Now` (which returns `DateTime.UtcNow`) against `DateTime.Now` (local). On non-UTC machines this may be flaky/broken — test as written is unreliable; covers trivial assertion anyway. |
| 3 | SystemClock_NowOffset_ShouldReturnCurrentTimeOffset | Same flakiness risk: `DateTimeOffset.Now` vs `DateTimeOffset.UtcNow` only equal after offset normalisation. Effectively a trivial wrapper test. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | SystemClock_Now_ReturnsUtcKind | Verify `SystemClock.Instance.Now.Kind == DateTimeKind.Utc` (regression protection — comment says Scala uses UTC) | High |
| 2 | SystemClock_NowOffset_HasZeroOffset | `SystemClock.Instance.NowOffset.Offset == TimeSpan.Zero` (UTC) | High |
| 3 | FakeClock_NowOffset_WithNonUtcKind_Behavior | `new DateTimeOffset(DateTime, TimeSpan.Zero)` throws when Kind is Local — document/test this | Medium |
| 4 | FakeClock_Advance_ThreadSafety | Concurrent SetNow/Advance calls don't corrupt internal `_now` | Low |
| 5 | FakeClock_SetNow_ReplacesInitialTime | SetNow overrides, doesn't combine with initial time | Low |

### G.23 ConversionExtensionsTests.cs (20 tests)

**Irrelevant Tests:** None — all tests are relevant. Covers ToIntOption, ToDouble, TwoDigits, ToBool, IdToIntOption, and three Converters impls.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ToIntOption_WithEmptyString_ReturnsNull | "" input → null (not currently tested) | Medium |
| 2 | ToIntOption_WithWhitespace_ReturnsNull | "   " input → null | Medium |
| 3 | ToIntOption_WithOverflow_ReturnsNull | String > int.MaxValue → null (int.TryParse fails gracefully) | Medium |
| 4 | TwoDigits_WithNegative_BehaviorDocumented | -5 → "-5" or "-05"? (D2 format semantics) | Medium |
| 5 | ToBool_WithEmptyString_ReturnsFalse | "" → false (via ToIntOption path) | Medium |
| 6 | ToBool_WithWhitespace_ReturnsFalse | "  " → false | Low |
| 7 | IdToIntOption_WithPrefixOnly_ReturnsNull | "prefix" → null (empty remainder) | Medium |
| 8 | IdToIntOption_WithEmbeddedPrefix_RemovesAllOccurrences | "12prefix34" → 1234 per `Replace` semantics | Medium |
| 9 | LongConverter_WithInvalidString_Throws | Converter.Convert throws FormatException on bad input (source uses `long.Parse` not TryParse) | High |
| 10 | IntConverter_WithInvalidString_Throws | Same for IntConverter | High |
| 11 | LongConverter_WithOverflow_Throws | long.Parse throws OverflowException for > long.MaxValue | Medium |

### G.24 ConvertersTests.cs (5 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 1 | LongConverter_WithValidString_ShouldConvert | Duplicate of ConversionExtensionsTests.LongConverter_Convert_ShouldParseLong. |
| 2 | LongConverter_WithNegativeNumber_ShouldConvert | Adds marginal coverage vs ConversionExtensions but overlaps. |
| 3 | StringConverter_ShouldReturnSameString | Duplicate of ConversionExtensionsTests.StringConverter_Convert_ShouldReturnOriginal. |
| 4 | IntConverter_WithValidString_ShouldConvert | Duplicate of ConversionExtensionsTests.IntConverter_Convert_ShouldParseInt. |
| 5 | IntConverter_WithNegativeNumber_ShouldConvert | Marginal additional case — duplicates pattern. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ConvertersTests_ShouldBeConsolidated_OrDeleted | File is essentially a duplicate of ConversionExtensionsTests regions — either add the invalid/overflow cases listed in G.23 here exclusively, or delete this file | Medium |
| 2 | Converters_StaticInstances_AreNonNull | Quick guard that `LongConverter`, `StringConverter`, `IntConverter` are initialized (class-cctor correctness) | Low |

### G.25 PercentileUtilsTests.cs (10 tests)

**Irrelevant Tests:** None — all tests are relevant. Coverage of empty, single, two, odd, even, unsorted, negatives, uniform, floats, large collections.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | ComputeP50AndMin_WithNaN_Behavior | NaN-containing sequence behavior (sort orders NaN unexpectedly) | Medium |
| 2 | ComputeP50AndMin_WithInfinity_Behavior | +/- Infinity values handled in sort | Low |
| 3 | ComputeP50AndMin_PercentileStats_RecordEquality | `PercentileStats` record equality/deconstruction works | Low |
| 4 | ComputeP50AndMin_FloatOverload_DelegatesToDouble | Float overload produces identical result to double when cast | Medium |
| 5 | ComputeP50AndMin_DoesNotMutateInput | Passing a pre-sorted List and verifying it's not reordered (source calls OrderBy) | Medium |

### G.26 QueryValidationUtilsTests.cs (6 tests)

**Irrelevant Tests:** None — all tests are relevant for GetFtsSearchQuery branching.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | IsValid_WithNullQuery_ReturnsFalse | `IsValid(null)` → false (notNullWhen contract) | High |
| 2 | IsValid_WithEmptyString_ReturnsFalse | `IsValid("")` → false | High |
| 3 | IsValid_WithWhitespaceOnly_ReturnsFalse | `IsValid("   ")` → false | High |
| 4 | IsValid_WithSingleChar_ReturnsFalse | `IsValid("a")` → false (below MinQueryLength=2) | High |
| 5 | IsValid_WithExactly2Chars_ReturnsTrue | `IsValid("ab")` → true (boundary) | High |
| 6 | IsValid_WithLeadingTrailingSpaces_TrimmedLength | `IsValid(" a ")` → false (trimmed length 1) | High |
| 7 | IsValid_WithLongQuery_ReturnsTrue | `IsValid("cardiologist")` → true | Medium |
| 8 | MinQueryLength_IsTwo | Regression guard on the public const | Low |

### G.27 S3UtilsTests.cs (8 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|--------|-----------|-------|
| 3 | GetS3Client_WhenDynamoDbEndpointIsSet_UsesLocalStack | Source `S3Utils` only reads `S3_ENDPOINT` — there is no `DYNAMO_DB_ENDPOINT` branch in S3Utils.cs. Test validates a branch that doesn't exist in source. |
| 5 | GetS3Client_WhenS3EndpointTakesPrecedence_OverDynamoDbEndpoint | Same — precedence logic between DYNAMO_DB_ENDPOINT and S3_ENDPOINT isn't implemented; test asserts only `NotBeNull` and so cannot detect missing precedence. Flag as asserting on non-existent branch. |
| 1 | GetS3Client_WhenCalledFirstTime_ReturnsNewClient | Client is cached statically across tests — "first time" is not actually testable without `S3Utils.Reset()`. Test silently passes if client already cached. |
| 2 | GetS3Client_WhenCalledMultipleTimes_ReturnsSameInstance | Legitimate, but tests depend on the static cache not being reset by other tests. |

*(Tests 6, 7, 8 are thin — all assert `NotBeNull` on the cached client without verifying LocalStack vs real AWS config.)*

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | GetS3Client_WithS3Endpoint_UsesForcePathStyle | Verify actual config via reflection: `ServiceURL`, `ForcePathStyle=true` | High |
| 2 | GetS3Client_WithS3Endpoint_UsesBasicCredentials | LocalStack path uses `BasicAWSCredentials("test","test")` not SSO | High |
| 3 | GetS3Client_WithoutS3Endpoint_UsesDefaultCredentialsChain | Non-LocalStack path uses default credentials (no explicit basic creds) | High |
| 4 | Reset_ClearsCachedClient | `S3Utils.Reset()` disposes and nulls `_s3Client` | High |
| 5 | GetS3Client_IsThreadSafe_AfterReset | After Reset, concurrent GetS3Client still returns one instance | Medium |
| 6 | GetS3Client_UsesRegionUsEast1_ByDefault | Verify default region is US-East-1 | Medium |
| 7 | Remove_DYNAMO_DB_ENDPOINT_branches | Existing tests referencing DYNAMO_DB_ENDPOINT should be deleted (no source behavior) | High |

### G.28 SpendLockStatusUtilsTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant for CalculateSpendLockStatus across null/year-3000/future/past/equal branches.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | CalculateSpendLockStatus_ExactlyYear3000Jan1_IsIndefinite | Boundary: year==3000 → `indefinite_spend_locked` | Medium |
| 2 | CalculateSpendLockStatus_Year2999_ReturnsSpendCapped | Just below year-3000 threshold returns spend_capped (not indefinite) | High |
| 3 | CalculateSpendLockStatus_DifferentTimezones_UsesInstantComparison | Provide hasBudgetFrom in non-UTC offset and compare against UTC current | Medium |
| 4 | CalculateSpendLockStatus_CurrentTimestampInFuture_ReturnsInBudget | hasBudgetFrom in past relative to very-future current → in_budget | Low |
| 5 | CalculateSpendLockStatus_MinDateTime_ReturnsInBudget | DateTimeOffset.MinValue as hasBudgetFrom → in_budget | Low |

### G.29 UserAgentUtilsTests.cs (9 tests)

**Irrelevant Tests:** None — all tests are relevant for IsMobileApp (null/empty, casing, false positives from Zocdoc/, real UA strings).

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | IsMobileApp_WithWhitespaceOnly_ReturnsFalse | "   " input → false (IsNullOrEmpty doesn't cover whitespace, but UA contains nothing matching) | Low |
| 2 | IsMobileApp_WithAndroidAppUA_ReturnsTrue | Realistic Android ZocdocApp UA string (coverage parity with iPhone test) | Medium |
| 3 | IsMobileApp_WithMixedCase_ShouldReturnTrue | "ZoCdOcApP/1.0" → true (OrdinalIgnoreCase) | Medium |
| 4 | IsMobileApp_WithZocdocappSubstring_ReturnsTrue | "...zocdocapp..." embedded anywhere matches | Medium |

### G.30 ZdSearchRadiusUtilsTests.cs (2 test methods, 12 cases)

**Irrelevant Tests:** None — all tests are relevant. Parameterised tests cover 6 geographic locations for both `GetSearchRadiusInMiles` and `GetSearchDistanceBandSize`.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|----------------|-------------------|----------|
| 1 | GetSearchRadiusInMiles_AtEquator_ReturnsExpected | (0, 0) coordinate — edge of coverage | Medium |
| 2 | GetSearchRadiusInMiles_SouthernHemisphere_ReturnsExpected | Southern lat (e.g., Sydney) — all current cases are northern | Medium |
| 3 | GetSearchRadiusInMiles_WithInvalidLat_Behavior | Lat > 90 or < -90 — defensive handling | Low |
| 4 | GetSearchDistanceBandSize_WithCoordinateNull_Throws | Null coordinate argument behavior | Low |
| 5 | GetSearchRadiusInMiles_ConsistentWithBandSize | For each location, verify radius × band-size invariants (cross-check) | Medium |
| 6 | GetSearchRadiusInMiles_Alaska_LargeBand | Test Fort Yukon-like far-north case is intentional (band 546.63) — regression guard already present but no comparable high-density check around Boston/Chicago | Low |


---

## Chunk H — Search Miscellaneous Unit Tests
*Directories under `tests/YassSharp.UnitTests/Search/`: MarketIntelligence, Enchilada, SPO, Statsd, CrossEncoder, Grouping, Hydration, Models, Embeddings, Personalization, Availability, Constants, Datalake, Decorating, DynamoDb, Semantic, Annotation, Canoe, Supplementing (70 files).*

#### Search/MarketIntelligence

### H.1 FilterSerializerTests.cs (5 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] Round-trip serialization preserving nested filter tuples (e.g. `["INSURANCE_IDS", ["ip_123"]]` → deserialize → same key/value pair) — currently only single-direction serialization is asserted.
- [Medium] Empty-array filter (`["DAY_RANGES", []]`) — should not crash and should yield an empty JSON array rather than null.
- [Medium] Unknown filter dimension — coverage for the default/unknown branch (graceful pass-through vs exception).
- [Low] Unicode/special characters inside filter values (quotes, backslashes) to confirm proper JSON escaping.

### H.2 MarketIntelligenceQueryValidatorTests.cs (~15 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Specialty fan-out cap: when specialty IDs exceed the configured cap, the validator should drop excess and emit a metric/warning; verify exact cap value and that the **first N** (not arbitrary N) are preserved.
- [High] Procedure inheritance with ambiguous parent specialty — confirm which specialty is inherited when a procedure maps to multiple parents.
- [Medium] Mutual-exclusivity: gender filter + specialty that is gender-specific (e.g. OB/GYN) — confirm filter is retained, not dropped.
- [Medium] Zip+radius vs lat/lng+radius — verify that only one location-shape survives when both are passed.
- [Low] Case-sensitivity of specialty IDs (`sp_123` vs `SP_123`).

### H.3 MarketIntelligenceServiceTests.cs (~25 tests)
**Irrelevant Tests:** None (this is a key HIGH-priority fixture for supply accuracy).
**Missing Tests:**
- [High] `DiscoverVisitReasons` accuracy when the underlying ES aggregation returns zero buckets — the result object should be empty rather than throwing; verify no false "0" visit-reason is surfaced.
- [High] Supply-rank tie-breaking: two specialties with identical supply counts — verify the deterministic ordering (ID lexicographic? insertion order?) so sort is stable across runs.
- [High] Revenue-rank path excludes providers with zero revenue from the denominator (avoid inflated rev/provloc averages).
- [Medium] Volume-rank when booking-volume data is stale (older than configured TTL) — confirm fallback and metric.
- [Medium] Per-specialty timeout firing — the overall MI response should still return partial results (current tests cover caller cancellation and overall timeout, but not a single-branch timeout among N parallel branches).
- [Medium] `WithPreviewMode=true` plus `InsurancePlanId` set — preview should still respect insurance and not leak the original plan across branches.

### H.4 PreviewModeTests.cs (~15 tests across 4 nested fixtures)
**Irrelevant Tests:** None — this is the PHI-safety fixture.
**Missing Tests:**
- [High] Preview-mode firehose suppression: verify that `FirehoseService.LogAsync` is never called (current tests verify via mock not-called for one branch only; add a negative assertion across every log path: search, SPO request, ads-retriever, insurance propagation).
- [High] Preview + `SensitiveHealthInformation` flagged query — double-safeguard: even if firehose were invoked, the payload must have the query redacted.
- [High] SPO request under preview mode — confirm `TrackingId`/`DeviceId` are stripped (or set to a preview marker) before being forwarded to SPO.
- [Medium] Preview-mode insurance propagation when both `InsurancePlanId` and `ExplicitlySetParams.InsurancePlanId` are set — preview's clone should honor the explicit override and not silently revert.
- [Medium] Preview mode + MI — confirm MI results returned in preview do not include `pconv`/personalized scoring (all providers scored with a deterministic mode).

### H.5 PreviewSearchExecutorTests.cs
**Irrelevant Tests:** **ALL** — this fixture is a stub that only exercises Facets and DaysUntilNextAvailability in isolation rather than the real executor pipeline (no retrieval, no filtering, no scoring verified end-to-end). Flag for rewrite or removal.
**Missing Tests:**
- [High] Full PreviewSearchExecutor pipeline with a real (faked) ES index — verify that a preview request produces a valid `ResponseInfo` **without** invoking firehose, SPO ads, or personalization retrievers.
- [High] Verify preview executor honors `CancellationToken` from the caller (important for request-abort safety).
- [Medium] Preview executor + empty-result query — verify MI fallback signals are still emitted.

### H.6 RefinementAggregatorTests.cs (~30 tests across 3 fixtures)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Cumulative distance-bucket invariant: for any contiguous set of buckets `[0-1mi, 1-5mi, 5-10mi]`, the sum should equal the "within-10mi" total (regression guard for double-counting).
- [High] Availability bucket overlap: `avail_today`, `avail_within_3d`, `avail_within_7d` must satisfy `today ≤ 3d ≤ 7d` (monotonic); add a property-style test.
- [Medium] Gender facet with `Unknown`/`Other` — verify it's not silently collapsed into a binary.
- [Medium] Visit-type refinement when the specialty has no telehealth support — the `VirtualOnly` bucket should be `0`, not missing.
- [Low] Aggregation fallback ordering when all counts are equal (stable sort).

### H.7 SignalExtractorTests.cs (~15 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `ProviderLocationCount` when there are deduplicated provlocs across multiple responses — verify dedup by `(providerId, locationId)` tuple, not just by `providerId`.
- [High] `InNetworkCount` when insurance plan is `ChooseLater` (`ip_-1`) or `PayMyself` (`ip_-2`) — these are constants from H.45/H.46 and the extractor should not count all providers as in-network.
- [Medium] `NextAvailableWithinDays(0)` edge case — same-day availability boundary (start-of-day vs end-of-day cutoff).
- [Medium] `ExtractPageEstimates` when `TotalHits` is 0 — page-count must be 0, not 1.

### H.8 SupplyOnlyModeTests.cs (8 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `EvaluationScope.SupplyOnly` ensures expensive retrievers (personalization, banner, practice features) are skipped — currently tests plumbing but not the actual skipping. Verify via mock call counts.
- [Medium] Supply-only mode + SPO — SPO ads should still be requested if relevant, or should they be suppressed? Encode the intended behavior.
- [Medium] Supply-only mode + preview — interaction between the two flags (no double-suppression bugs).

### H.9 YassRequestCloneTests.cs (4 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `CloneForPreview` must deep-copy `Filter` (array of object-arrays) — mutating the clone's filters must not affect the original; a shared reference here would leak preview filters into prod.
- [Medium] `CloneForPreview` copies `HighlightedProviderLocationIds` (deep copy if the array is mutable).
- [Medium] `CloneForPreview` when `ExplicitlySetParams` is `null` — no NRE.

#### Search/Enchilada

### H.10 CostPlanDefaultsTests.cs (1 test)
**Irrelevant Tests:** None (the single test is a sanity check on constants — Low priority).
**Missing Tests:**
- [Medium] Exact numeric expectations for each plan-type default (e.g. `PPO = X`, `HMO = Y`); currently only a shape assertion.
- [Medium] Default map contains entries for every `InsuranceProgramTypeName` enum value (fail-on-new-enum guard).

### H.11 EnchiladaFeatureNamesTests.cs (3 tests, all `[Ignore]`)
**Irrelevant Tests:** **ALL** — per directive, flagged as Irrelevant (tests are `[Ignore]`d because libomp is not available in CI, so they never actually run). Remove the `[Ignore]` once libomp is a dev-dependency, or move to an integration-test project.
**Missing Tests:**
- [High] Feature-name list parity between the C# Enchilada model and the Scala/LightGBM model descriptor — a rename in one without the other corrupts feature ordering silently.
- [High] Feature-count equals the expected V3/V4/V5 model input width (prevent silent truncation).

### H.12 EnchiladaFeaturesTests.cs (~12 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `ExtractInsuranceId` when `InsurancePlanId` is `ip_-1` (ChooseLater) — feature should be a sentinel, not a real plan ID (regression for mislabeled training data).
- [High] `IsNoInsuranceSearch` with `PayMyself` (`ip_-2`) — verify both legacy null-plan and `PayMyself` paths return `true`.
- [Medium] `IsPageOne` at page boundary (page=0 vs page=1 — is the contract "page number 1" or "zero-indexed page 0"?).
- [Medium] `SearchHasSpoResult` with SPO ads decisions present but zero actual SPO results retrieved (ads-only vs ads+results).
- [Medium] `SearchResultCount` with deduped results — count post-dedup, not pre-dedup.

### H.13 EnchiladaModelCategoricalSplitsTests.cs (3 tests)
**Irrelevant Tests:** None — regression suite for the V4 `num_cat=0` bug is HIGH priority.
**Missing Tests:**
- [High] Negative-test: a V4 model file with `num_cat=0` for a categorical-split tree node — assert the loader rejects it with a clear error.
- [High] V5 equivalent of the V4 categorical-split regression — forward-proof for the next model version.
- [Medium] Mixed-split tree (numeric + categorical) with `num_cat` mismatch — targeted error path.

### H.14 RevenueCalculatorTests.cs (~16 tests)
**Irrelevant Tests:** None — revenue math is HIGH priority.
**Missing Tests:**
- [High] V1 vs V2 divergence point: a fixture input that yields a materially different result, confirming they are *not* accidentally equivalent (prevents a regression where V1 is applied in a V2 path).
- [High] Booking-price calc with `0` cost (free visit) — must not divide by zero or yield `NaN`/`Infinity`.
- [High] Tail-revenue with a negative discount rate (invalid config) — should throw or clamp, not produce negative revenue.
- [Medium] Boundary: discount rate exactly `1.0` (no discount) — output equals input booking price.
- [Medium] V2 discount rate `0.810` applied twice vs once (idempotency of the calculator on re-invocation).

### H.15 RevenueResultTests.cs (7 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] `Delta` when `Expected == Cost` — must be exactly `0`, not `-0` or tiny floating-point noise.
- [Medium] `IsFinite` with `double.NaN`, `PositiveInfinity`, `NegativeInfinity` inputs (all three should be `false`).
- [Low] Serialization round-trip (if the result crosses a JSON boundary).

### H.16 V2CalculationDetailsTests.cs (2 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] Details object records the V2 discount rate actually used (observability for debugging).
- [Medium] Details toString/log-format does not include PHI (insurance IDs are fine; any patient-level field would be PHI).

#### Search/Spo

### H.17 AdsRetrieverCrosslistingTests.cs (~14 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `PartitionCrosslistedCandidates` when the search specialty does NOT match the provider's main specialty but DOES match a crosslisted specialty — candidate must land in the crosslisted bucket (not dropped, not in main bucket).
- [High] `OriginalMainSpecialty` fallback logic: when `MainSpecialty` is null but `OriginalMainSpecialty` is populated — which takes precedence? Encode it.
- [Medium] Emission of the `spo.crosslisting.partition` metric with both `main` and `crosslisted` tags across a single call.
- [Medium] Empty candidate list — no metrics emitted (avoid cardinality noise).

### H.18 CachedBannerCheckerErrorTests.cs (1 test)
**Irrelevant Tests:** None — S3 failure path is a HIGH priority for availability.
**Missing Tests:**
- [High] S3 transient failure (503) — verify retry occurs and succeeds.
- [High] S3 persistent failure — cache is NOT poisoned with a "no banner" result (subsequent provider lookups still attempt S3).
- [Medium] Cache TTL expiry while S3 is returning errors — verify a stale-but-successful cached value is preferred over a fresh failure.
- [Medium] Metric emission on S3 error (`banner.s3.error`).

### H.19 SpoAdsIntersperserTests.cs (3 tests)
**Irrelevant Tests:** **ALL** — only verifies `Instance`/`ProcessorType`/`Name` (shallow singleton check). Per user directive, flag the shallow portion but keep the file.
**Missing Tests:**
- [High] Intersperse positions: given N SPO ads and M organic results with a target intersperse ratio, verify the exact output positions of SPO ads (e.g. positions 0, 3, 6 for a 1:3 ratio).
- [High] Intersperse when SPO count exceeds configured max — excess SPO ads are dropped (not queued after organic, not duplicated).
- [High] Intersperse preserves the organic relative ordering (no organic reordering as a side effect).
- [Medium] Intersperse with zero SPO ads — organic list is returned unchanged.
- [Medium] Intersperse when `PageSize` is smaller than the first SPO ad position — SPO ad must not appear on page 1 if its target slot is on page 2.

### H.20 SpoClientErrorTests.cs (3 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] SPO rate-limited (HTTP 429) — verify backoff/retry and a distinct `outcome:ratelimited` metric tag (currently only "service unavailable" is covered).
- [Medium] SPO timeout within the configured budget — verify `outcome:yass_timeout` metric and empty-result return.
- [Medium] SPO malformed response body — verify graceful skip + `outcome:error` tag.

### H.21 SpoEnhancedAvailabilityFiltererTests.cs (5 tests)
**Irrelevant Tests:** **ALL** — per user directive, these are no-op verifications because the filterer's properties are read-only. Flag for rewrite against the real filterer behavior.
**Missing Tests:**
- [High] Given SPO results with `SpoAvailabilities` that match the `day_ranges` filter — only matching SPO ads pass through.
- [High] Given SPO results with NO enhanced-availability data — filterer must NOT drop them (backward compat guard).
- [Medium] Verify metric emission distinguishing "filtered in" vs "filtered out" counts.

### H.22 SpogorithmRankerTests.cs (~17 tests)
**Irrelevant Tests:** None — this is HIGH priority (PConvV4 AB test, DaysUntilNextAvailability).
**Missing Tests:**
- [High] PConvV4 score delta vs prior version on a fixed candidate set — regression snapshot to detect unintentional scoring drift.
- [High] `DaysUntilNextAvailability` with a `SpoAvailabilities` entry whose date is in the past — must be treated as "no availability" (not a negative day count).
- [High] PConvV4 with tied scores — deterministic tie-breaker (e.g. by providerId) so ordering is stable across runs.
- [Medium] Null `SpoAvailabilities` entirely — ranker returns a safe default (not NRE).
- [Medium] Malformed date string in `SpoAvailabilities.FirstAvailabilityDate` — ranker logs and skips, does not throw.

### H.23 SpoProvLocGetterTests.cs (3 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Both `InsuranceProgramTypeName == Unknown` AND `InsurancePlanId == "ip_-2"` — confirm the "pass-through the guard" branch behaves identically in both inputs.
- [Medium] `InsurancePlanId == "ip_-1"` (ChooseLater) — same guard as `Unknown`? Encode it.
- [Medium] Empty-string `InsuranceProgramTypeName` vs null — both should return empty.

#### Search/Statsd

### H.24 EnchiladaMetricsTests.cs (5 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] `ExpectedValue` fallback chain priority — when both `ExpectedValue` and `Cost` are present, which wins? Encode the expected order.
- [Medium] Invocation-type tag with an unknown value — must default to `invocation_type:unknown`, not crash cardinality.
- [Medium] Verify metric name parity with prod dashboards (`marketplace.search.enchilada.*`).

### H.25 SearchFunnelMetricsTests.cs (6 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `no_results` counter increment: exactly once per empty search (not N-times), verify idempotency.
- [High] Relevancy-score histogram emission does NOT leak per-provider scores (cardinality guard — only aggregate buckets).
- [Medium] Result-count histogram with 0 results — bucket emission is correct (0 is valid, not skipped).
- [Medium] SPO-only result count funnel metric separation.

### H.26 SearchLatencyMetricsTests.cs (8 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `status:error` + `is_spo_search:true` combination — both tags present (regression guard).
- [Medium] Latency > 10s edge-case — not silently dropped or capped (observability correctness).
- [Medium] Verify histogram (not timer) is used for the latency emission if the metric system expects histograms.
- [Medium] Tag cardinality bound — `endpoint` tag has only a fixed enum of values (not user-input).

### H.27 SearchMetricTagsTests.cs (~22 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] `DerivePlatform` for a tablet+MobileApp combination — currently tablet is not represented in the platform mapping.
- [Medium] `DeriveBrowserType` for Opera/Brave/Samsung Internet — returns `other` (verify, don't regress to a catchall hit).
- [Medium] `DeriveAppVersion` with an invalid semver (e.g. `abc.def`) — returns `n_a` rather than the raw string.
- [Medium] `DeriveIsSpo` with an `SpoAdsResponse` object but **all** decisions having no placement — should be `false`, not `true` (currently tests empty-list but not decision-level emptiness).

### H.28 SpoOutcomeMetricsTests.cs (2 tests)
**Irrelevant Tests:** **ALL** — per user directive, the file only tests the tag-format (private method is not exercised) and the TestCase parameterization merely validates that tag strings are non-empty. Flag for rewrite.
**Missing Tests:**
- [High] `EmitSpoCallOutcome` is actually invoked with the correct outcome tag for each of: `success`, `yass_timeout`, `ratelimited`, `error`, `skipped` — needs reflection or making the method internal for test visibility.
- [Medium] Metric name is exactly `marketplace.search.spo.call` (not a prefix substring).

### H.29 SupplyHealthMetricsTests.cs (4 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `supply_quality_pct` histogram exact bucket values for all 7 base signals (same_day, 3d, 7d, distance_2mi, distance_10mi, etc.) — currently only `same_day_avail` is asserted explicitly.
- [High] Insurance signals emit with `signal:in_network` tag AND `signal:in_network_same_day_avail` combinations — verify cross-product.
- [Medium] Empty `Results` but populated `SpoResults`/`CanoeResults` — `AssemblePageResults` returns a union; but supply-health metrics should emit over the assembled view.
- [Medium] `days_to_availability` histogram uses the correct bucket boundaries (regression guard for dashboard alignment).

#### Search/CrossEncoder

### H.30 RetryingCrossEncoderServiceTests.cs (7 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Retry count is exactly the configured limit (not 1-more, not 1-less).
- [High] Retry preserves the input ordering of candidates (Voyage scoring assigns by index, off-by-one retry bug could silently mis-rank).
- [Medium] Retry between `AmazonSageMakerRuntimeException` and `HttpRequestException` mixed — no interference between retry reasons.
- [Medium] Log emission on final-failure includes the attempt count.

### H.31 VoyageApiCrossEncoderServiceTests.cs (~14 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Score-order restoration: given Voyage returns scores in an arbitrary order with an index field, the service must reassemble into the original input order (regression guard for silent mis-ranking).
- [High] Instruction prepending must escape/sanitize user input (SQL-injection-style — a query with `</instruction>` must not break the format).
- [Medium] Request body includes `top_k` matching candidate count (not an arbitrary limit).
- [Medium] Null/empty candidate list — service returns empty, does not call Voyage API.
- [Medium] Constructor with null `HttpClient` — throws (currently covered) — but also null `ILogger` and null `IMetricRecorder`.

### H.32 VoyageSageMakerCrossEncoderServiceTests.cs (7 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] SageMaker endpoint payload format matches the expected Voyage-hosted inference contract (regression guard when endpoint is updated).
- [High] SageMaker timeout configured — request does not hang indefinitely on a slow endpoint.
- [Medium] SageMaker response with an unexpected field — parser skips unknowns rather than throws.

### H.33 ZeroEntropyApiCrossEncoderServiceTests.cs (~14 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] XML escaping: a query containing all five entities `< > & ' "` in a single string — each escaped once (no double-escaping to `&amp;amp;`).
- [High] Response with `scores` array length mismatch vs candidate count — error or safe fallback.
- [Medium] ZeroEntropy model name tag in outbound request payload (for `zerank-2` version identification).
- [Medium] Extremely long candidate snippet — payload size guard.

### H.34 ZeroEntropyQueryFormatterTests.cs (8 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] Formatter with an instruction containing XML-reserved characters — both instruction and query must be escaped.
- [Medium] Null instruction — formatter produces a query-only element, not a `<instruction></instruction>` empty tag.

#### Search/Grouping

### H.35 CommonGroupingsTests.cs (4 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] `MatchesSearchSpecialtyId` across feature-category synonyms (e.g. "Dentist" vs "General Dentistry") — verify the synonym map.
- [Medium] Parent-child specialty match (searching parent — children should match; searching child — parent should NOT match).
- [Medium] Empty `FeatureCategories` list — returns false, not an NRE.

### H.36 GroupMarkerProcessorTests.cs (1 test)
**Irrelevant Tests:** **ALL** — per user directive, stub that only verifies `ProcessorType`/`Name`. Flag for rewrite.
**Missing Tests:**
- [High] `GroupMarkerProcessor` actually assigns `Groups` to each `ProvLocResult` based on the `IGrouping` definitions from the algorithm.
- [High] Providers that match multiple groupings get multiple group markers (not just the first).
- [Medium] Metric emission for group-distribution.

### H.37 GroupRankerProcessorTests.cs (1 test)
**Irrelevant Tests:** **ALL** — per user directive, stub. Flag for rewrite.
**Missing Tests:**
- [High] Given a response with mixed grouped/ungrouped results, the ranker prioritizes the grouped ones per the `Groupings` definition.
- [High] Ranker stability: already-ranked groups with identical primary-group tags preserve their relative ordering.
- [Medium] Ranker emits an observability metric for group-rank movement distance.

### H.38 ResultGrouperTests.cs (~14 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] InNetwork grouping when `InsurancePlanId` is `ChooseLater`/`PayMyself` — no in-network group should be created (otherwise every provider appears "in-network").
- [Medium] Brand grouping with a provider having NO brand — provider lands in a "no brand" catch-all (or is excluded from brand grouping entirely?). Encode it.
- [Medium] Specialty grouping with a multi-specialty provider — verify primary vs all-specialty behavior.

### H.39 SearchResultGroupTests.cs (3 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Low] Enum value count (currently 17) — add a string-representation round-trip to catch rename regressions.
- [Low] Enum serialization stability (JSON name must match prod contract).

#### Search/Hydration

### H.40 EnterpriseHydrationProcessorTests.cs (3 tests)
**Irrelevant Tests:** **ALL** — per user directive, stub tests.
**Missing Tests:**
- [High] `EnterpriseHydrationProcessor` actually hydrates enterprise-specific fields (brand, practice name) on `ProvLocResult` when the provider belongs to an enterprise.
- [Medium] Non-enterprise provider — fields remain null (no bogus enterprise marker).

### H.41 HydrationProcessorTests.cs (3 tests)
**Irrelevant Tests:** None — singleton/type/name checks are valid for the base processor.
**Missing Tests:**
- [Medium] `HydrationProcessor` orchestrates its component hydrators in the expected order (AcceptsInsurance before DisplaySpecialty before DistanceMi).
- [Medium] When a component hydrator throws, the processor logs and continues (does not corrupt the whole response).

### H.42 HydratorTests.cs (~18 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `AcceptsInsuranceHydrator` when insurance plan is `ChooseLater`/`PayMyself` — accepts-insurance should be `null` or a sentinel, not `true`/`false` (mis-displaying acceptance is a patient-experience issue).
- [High] `DistanceMiHydrator` with a search at `(0, 0)` and a provider at the antipode — great-circle distance handles the edge, not a NaN.
- [Medium] `DisplaySpecialtyHydrator` with a provider whose `MainSpecialty` is missing — falls back to `OriginalMainSpecialty`, then to an empty string.
- [Medium] `ProviderQualitiesHydrator` with no qualities — returns an empty list (not null).
- [Medium] `ProviderBadgesHydrator` badge ordering deterministic (PatientChoice before other badges).

### H.43 ListingAndEnterpriseHydrationProcessorTests.cs (7 tests)
**Irrelevant Tests:** **ALL** — per user directive, duplicates of `ListingHydrationProcessorTests` and `EnterpriseHydrationProcessorTests`. Flag for consolidation.
**Missing Tests:**
- [Medium] If this processor is intended to run both listing AND enterprise hydration in one pass, add tests that verify interleaving (listing fields hydrated first, then enterprise fields, with shared state consistent).

### H.44 ListingHydrationProcessorTests.cs (6 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `ListingAcceptsInsuranceHydrator` — when `MatchedQueries` contains the in-network token, `AcceptsInsurance=true`; when `MatchedQueries` is empty, `AcceptsInsurance=false`; null `MatchedQueries` → `null` (three-value logic must not collapse).
- [Medium] Listing hydrator observability — metric for missing match-query (pipeline regression guard).

#### Search/Models

### H.45 BoxTests.cs (6 tests)
**Irrelevant Tests:** None — Low priority but valid.
**Missing Tests:**
- [Medium] `Box` spanning the antimeridian (e.g. NorthWest at longitude 179, SouthEast at longitude -179) — `Center.Longitude` should be ~180, not ~0.
- [Medium] Degenerate box (NorthWest == SouthEast) — `Center` equals both corners.
- [Low] `Equals(null)` returns false.

### H.46 CoordinateTests.cs (9 tests)
**Irrelevant Tests:** None — Low priority.
**Missing Tests:**
- [Medium] Invalid coordinates (latitude out of ±90, longitude out of ±180) — constructor should throw or clamp (encode the contract).
- [Low] `Coordinate.Equals` when compared to `CoordinateWithZip` with the same lat/lng (encode whether the subclass compares equal).

### H.47 CoordinateWithZipTests.cs (7 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] Zipcode validation (non-US formats, 5-digit vs 9-digit with hyphen) — either enforce or explicitly accept.
- [Low] `GetHashCode` with different zipcode but same lat/lng — should differ.

### H.48 LocationParamFactoryTests.cs (7 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Malformed location string (e.g. `"abc,def"` or `"40.7"` with only one coord) — factory returns null or throws (encode behavior; silent-default is a bug).
- [Medium] Factory with both `location` string AND lat/lng params — precedence (documented? tested?).
- [Medium] Factory with box string containing extra whitespace or trailing colon.
- [Low] Zipcode `"0"`, `"00000"`, or non-ASCII digits.

#### Search/Embeddings

### H.49 CachedEmbeddingServiceTests.cs (~12 tests)
**Irrelevant Tests:** None — cache correctness is HIGH for performance and cost.
**Missing Tests:**
- [High] Concurrent cache-miss on the SAME query — inner service called exactly once (single-flight); current tests are sequential only.
- [High] Cache entry for query A evicted; a concurrent hit on A mid-eviction — must not return stale/garbled data (race condition guard).
- [Medium] Cancellation propagation: caller cancels during cache-miss inner call — cache is not populated with a partial result.
- [Medium] Normalization: query with leading/trailing zero-width-space or NBSP (U+00A0) — is it normalized like regular whitespace? Encode.

### H.50 RetryingEmbeddingServiceTests.cs (7 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Retry on empty-embedding response (`float[0]`) — model misbehavior should not be cached as a valid embedding.
- [Medium] Retry count is exactly 2 (per current behavior from test), but parameterize so a config change is detected.
- [Medium] Log emission on retry has severity `Warning` (not `Error` on first attempt).

### H.51 VoyageQueryHelperTests.cs (9 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] Trim when the query is composed entirely of multi-byte unicode — `CharsPerToken=5` assumption may over-trim; test behavior with emoji/CJK.
- [Medium] Trim that lands mid-word — result should still be a safe string (no broken surrogate pair).
- [Low] Threshold-boundary at exactly `maxTokens * 5` chars.

#### Search/Personalization

### H.52 DevicePersonalizationRetrieverProcessorTests.cs (~10 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `ProcessAsync` with a valid `TrackingId` — DynamoDB is called and the embedding is attached to the `ResponseInfo` (currently tests mostly empty/null-tracking paths).
- [High] `ProcessAsync` with DynamoDB throwing — error is swallowed, response is returned unchanged with a metric increment (personalization failure must not fail the search).
- [Medium] `Validate` when the retriever is wrapped in a nested `ExternalDataRetriever` (multiple levels deep).
- [Medium] Ensure the retriever does NOT read the embedding when in preview mode (PHI guard).

### H.53 DynamoDbDevicePersonalizationRetrieverTests.cs (~11 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] `GetDeviceEmbeddingAsync` returns a populated `float[]` when a valid item is found — current tests only cover null/error paths; no positive case.
- [High] Legacy-format fallback returns embedding when binary fails but legacy exists — current test only verifies the second call happens, not that the embedding is actually extracted from the legacy response.
- [Medium] Embedding-dimension mismatch (DynamoDB returns 512 floats but model expects 1024) — return null and emit a dimension-mismatch metric.
- [Medium] Metric for cache-hit vs cache-miss on DynamoDB (is the upstream cached anywhere? Observability gap).

### H.54 NullDevicePersonalizationRetrieverTests.cs (5 tests)
**Irrelevant Tests:** None — Low priority but valid.
**Missing Tests:**
- [Low] Null-retriever used in a production algorithm config — algorithm validation should accept it (it's the no-op stand-in).

#### Search/Availability

### H.55 AvailabilityClientTests.cs (~22 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Batch partial-failure: one sub-batch returns 500 while others return 200 — overall call either fails or returns partial results with a metric — encode exactly.
- [High] `GetProfessionalLocationAvailabilityAsync` with >1000 prof-locs — batch count is correct and ordering of aggregated response is deterministic.
- [Medium] Request query includes `StartDateInclusive` and `EndDateInclusive` in ISO format (not locale-specific).
- [Medium] 4xx other than 408 — bubbles as HttpRequestException (not silently returned as empty).
- [Medium] Empty `ProfessionalLocationIds` — no HTTP call made (avoid wasted requests).

### H.56 ProviderLocationAvailabilityServiceTests.cs (~15 tests)
**Irrelevant Tests:** 
- **`GetAvailabilityRawAsync_WithDuplicateMonolithIds_ShouldDeduplicate`** — **This test asserts the OPPOSITE of what its name says.** The test name claims dedupe behavior, but the assertion comment explicitly states: *"ProfessionalLocationId is a class without IEquatable, so Distinct() uses reference equality and won't deduplicate."* The test actually verifies that dedup does NOT occur. Rename to `_WithDuplicateMonolithIds_ShouldNOTDeduplicate` or fix the bug (add `IEquatable<ProfessionalLocationId>` to the class and assert real dedup).
**Missing Tests:**
- [High] Real dedup semantics — two prov-locs with the same `(MonolithProfessionalId, MonolithLocationId)` should result in a single request entry (blocked by the bug above).
- [High] `GetProfessionalAvailabilitiesByProvLoc` with a provider missing `TimeZone` — timezone defaults or availability is silently dropped — encode.
- [Medium] Virtual-location mapping where the same virtual `MonolithId` is shared across two providers — both providers get the availability, not one.
- [Medium] `shouldIgnoreDateSearchedFor` + `availabilityDays` combination — both flags honored simultaneously.

#### Search/Constants

### H.57 CarrierIdTests.cs (1 test)
**Irrelevant Tests:** None (Low priority constant check, but correct).
**Missing Tests:**
- [Low] Check for unintended new `ic_-N` constants (protects against silent additions).

### H.58 PlanIdTests.cs (1 test)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Low] Check for unintended new `ip_-N` constants.
- [Medium] Ensure `PlanId.ChooseLater != CarrierId.ChooseLater` (prefixes `ic_` vs `ip_` are correctly distinguished — prevents cross-use bugs).

#### Search/Datalake

### H.59 FirehoseServiceErrorTests.cs (3 tests)
**Irrelevant Tests:** None — firehose failure tolerance is HIGH for request reliability.
**Missing Tests:**
- [High] Firehose throws with a PHI-containing log payload — verify the exception message logged by the service does NOT include the original payload (PHI leak into error logs would be a compliance issue).
- [High] Firehose disabled (`Enabled=false`) — LogAsync is a complete no-op, no client call, no metric.
- [Medium] Firehose timeout exactly at `TimeoutMs` — verify timeout metric fires.
- [Medium] Firehose success path — `status:success` metric fires (not tested; currently only failure path).

### H.60 SensitiveHealthInformationCheckerErrorTests.cs (stub — 0 real tests)
**Irrelevant Tests:** **ALL** — per user directive, the fixture is defined but contains NO test methods (only a SetUp). Flag for immediate attention — this is a PHI-safety-critical component with ZERO test coverage.
**Missing Tests:**
- [High] S3 failure during PHI check — checker defaults to "assume sensitive" (fail-safe) rather than "assume non-sensitive" (fail-open, which would leak PHI).
- [High] S3 404 (PHI list file not present) — distinct fallback behavior; should NOT silently default to "non-sensitive".
- [High] PHI-checker caches results — but on S3 failure, does it serve a stale result or refuse? Encode.
- [High] Checker rejects queries containing known PHI markers — positive and negative cases.
- [Medium] Metric emission distinguishing `s3.error` vs `s3.not_found` vs `s3.success`.

#### Search/Decorating

### H.61 DecoratorTests.cs (6 tests)
**Irrelevant Tests:** 
- The **RankDecorator portion (3 tests: `Instance_ShouldBeSingleton`, `ProcessorType_ShouldReturnYassRank`, `ProcessorName_ShouldReturnRankDecorator`)** is flagged per user directive as shallow singleton verification. The DotProvLocMapDecorator portion here is also shallow (the meaningful DotProvLocMap tests live in H.62).
**Missing Tests:**
- [High] `RankDecorator` actually assigns `DisplayOnPageRank` and `PresortRank` correctly — the singleton test does NOT exercise the decorator logic.
- [High] `RankDecorator` ranking is 1-indexed on the displayed page (not 0-indexed) — verify with a page-2 scenario.
- [Medium] `RankDecorator` with SPO-interspersed results — SPO ads do/don't occupy display ranks (encode).

### H.62 DotProvLocMapDecoratorTests.cs (~10 tests)
**Irrelevant Tests:** None — map-dot correctness affects UX directly.
**Missing Tests:**
- [High] Enhanced-availability filter + rolled-up provlocs interaction — providers filtered out by availability also have their rolled-up provlocs excluded from dots (no orphan dots).
- [High] Map-dots cap at 100 — verify the cap is not exceeded when rolled-up produces >100 dots even before page-exclusion.
- [Medium] Map-dots when `Coordinate` is null on a provider — the provider is excluded from dots (no crash, no default-origin dot).
- [Medium] Page-out-of-bounds (page=100, pageSize=10, total=50) — returns empty dots, not a negative-slice exception.

#### Search/DynamoDb

### H.63 PracticeFeaturesRetrieverTests.cs (~36 tests)
**Irrelevant Tests:** None — large fixture with good coverage.
**Missing Tests:**
- [High] DynamoDB returns features with `NaN`/`Infinity` number values — retriever parses to 0 (current tests cover invalid-format but not numeric-NaN).
- [High] Median-fallback correctness: when practice is missing, median features are applied as EXACTLY the median row (not averaged, not skipped).
- [Medium] Partial-batch response: DynamoDB returns 80 of 100 requested practices — the 20 missing get median features (not all 100 fall back to median).
- [Medium] TeamCity-vs-prod credential code-path (two tests exist for this but the equivalence of results between the two branches is not asserted).
- [Medium] Practice-ID normalization (leading/trailing whitespace, case) — does the cache key match the DynamoDB key format?

### H.64 RealizationProviderFeaturesRetrieverErrorTests.cs (3 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Success path — retriever populates `RealizationProviderFeatures` when DynamoDB returns items (no positive case currently; only error-path).
- [High] Partial failure — some providers succeed, some missing — successful ones have features, missing ones have null (not all-or-nothing).
- [Medium] DynamoDB throttling (ProvisionedThroughputExceededException) — retry vs fall-through.
- [Medium] Retriever skipped on non-TeamCity env without instance-profile creds (complementary to the similar test in H.63).

#### Search/Semantic

### H.65 RetryingVectorSearchServiceTests.cs (6 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [High] Retry preserves the input-vector ordering of `Hits` — an off-by-one retry that reorders hits would corrupt semantic results.
- [Medium] Retry-count param: verify it matches the config (not hard-coded 2).
- [Medium] Retry skips on `ArgumentOutOfRangeException` and `InvalidOperationException` (programmer errors should not retry).

### H.66 VectorSearchResultTests.cs (5 tests under 2 fixtures: VectorSearchResult + VectorSearchHit)
**Irrelevant Tests:** None — data-class tests are Low priority but valid.
**Missing Tests:**
- [Low] `VectorSearchHit` equality / JSON round-trip.
- [Low] `VectorSearchResult.TotalDocuments` negative value — constructor allows it? Should it?

#### Search/Annotation

### H.67 RequiredEsFiltererAttributeTests.cs (4 tests)
**Irrelevant Tests:** None.
**Missing Tests:**
- [Medium] Attribute applied to a method vs a class — enforce allowed targets.
- [Medium] Multiple `[RequiredEsFilterer]` attributes on the same class — are they additive or conflicting?
- [Low] Round-trip: attribute discovered via reflection and the `FiltererType` property matches.

#### Search/Canoe

### H.68 CanoeProvLocGetterTests.cs (4 tests)
**Irrelevant Tests:** None, but note the file's own comment acknowledges gaps: *"Full integration tests for SearchAsync require a properly configured Es7StatsDClient and ValidatedSearchAlgorithm."*
**Missing Tests:**
- [High] `SearchAsync` with a populated `HighlightedProviderLocationIds` — verify the ES call is made with the CanoeProvLocFilterer, and results are returned in the order of the highlighted IDs.
- [High] `GetAlgorithm` with `CanoeUseOrganicAlgorithmFilters=true` — verify that **every** filterer from the organic algorithm is copied (not just the three currently asserted: `CrosslistingSpecialtyIdFilterer`, `OfficeHoursFilterer`, `DayAvailabilityFilterer`).
- [Medium] Canoe with more highlighted IDs than `PageSize` — the excess is either kept in the results or dropped (encode).
- [Medium] Canoe with a single invalid ID format (`foo_123` instead of `pr_123`) — filterer rejects vs passes.

#### Search/Supplementing

### H.69 SupplementersTests.cs (4 tests)
**Irrelevant Tests:** **ALL** — per user directive, stub file containing only singleton checks for `SpoProvidersSupplementer`, `MapleSupplementer`, `VirtualCareSupplementer`, `ResultsDeduper`. Flag for rewrite to cover actual supplementing behavior.
**Missing Tests:**
- [High] `SpoProvidersSupplementer` actually merges SPO results into the response (provloc list grows by the SPO count, minus any deduped).
- [High] `VirtualCareSupplementer` adds virtual-care entries when a provider has `VirtualLocations` — correct count and no duplicates with the primary location.
- [High] `MapleSupplementer` populates Maple-scored fields on results — verify the scoring path actually ran, not just the singleton is reachable.
- [High] `ResultsDeduper` deduplicates by `(providerId, locationId)` and keeps the best-scored entry (not the first-encountered — which would lose SPO-boosted entries).
- [Medium] Supplementer ordering (dedupe before/after SPO supplement) encoded as a test.

### H.70 Reserved — index padding
(No 70th file in the enumerated set; directory totals 69 actual test files under Search/\*. If a 70th is expected, verify against `find tests/YassSharp.UnitTests/Search -name "*.cs" -type f` — the `CapturingMetricRecorder.cs` is a helper, not a fixture, but was counted in some enumerations.)

---

## Top-Priority Follow-Ups (summary for triage)

1. **H.56 misleading test name** — `GetAvailabilityRawAsync_WithDuplicateMonolithIds_ShouldDeduplicate` asserts the opposite of its name. Either fix the bug (add `IEquatable`) or rename the test.
2. **H.60 SensitiveHealthInformationCheckerError** — PHI-safety component with ZERO actual test methods.
3. **H.5 PreviewSearchExecutor**, **H.21 SpoEnhancedAvailabilityFilterer**, **H.28 SpoOutcomeMetrics**, **H.36 GroupMarkerProcessor**, **H.37 GroupRankerProcessor**, **H.40 EnterpriseHydrationProcessor**, **H.43 ListingAndEnterpriseHydrationProcessor**, **H.61 RankDecorator portion**, **H.69 Supplementers** — all flagged Irrelevant stubs that need real behavioral tests.
4. **H.11 EnchiladaFeatureNames** — all tests `[Ignore]`d; feature-name parity with Scala model untested.
5. **H.3 MarketIntelligenceService**, **H.22 SpogorithmRanker**, **H.31-H.33 CrossEncoders** — HIGH-priority functional gaps for supply/scoring correctness.


---

# Part 2 — Integration Test Coverage Analysis

**Scope:** `tests/YassSharp.IntegrationTests/` — 26 fixtures, 167 cases. These fixtures exercise the full HTTP pipeline against a real test index via `SnapshotTestBase` / `CallDebuggableSearch` and compare responses against committed snapshots.

Each `### I.N <SpecFile>.cs` subsection lists the tests flagged as irrelevant, then the missing tests that should be added.

### I.1 BrandRequestsTests.cs (1 test)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | FiltersByMultipleBrandsViaFunctionScoreFilters | Union of brand filters in a single function_score_filters payload (OR semantics) | **High** |
| 2 | BrandFilterMiss_ReturnsEmptyButValidAggregations | Unknown brand legacyId returns 200 with empty hits but populated aggregations | Medium |
| 3 | BrandAggregationsRespectDirectoryIsolation | Brand aggregations for directory -1 exclude providers visible only in enterprise directories | **High** |
| 4 | FiltersByBrandWithoutInsurance | Brand filter alone (no insurance IDs) still returns brand-affiliated providers | Medium |
| 5 | InvalidFunctionScoreFilterJson_Returns400 | Malformed function_score_filters JSON returns a 400 rather than 500 | Medium |
| 6 | BrandFilter_WithEs7Off_ProducesEquivalentResults | ABOverride YASS-Use-Es7=off still returns equivalent brand hits | Medium |

### I.2 CallerTypeRequestsTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | CrossReferralsCallerType_RoutesToCorrectAlgorithm | `caller_type=crossReferrals` routes to cross-referral container | **High** |
| 2 | AiSearchCallerType_EnablesScoreFusionRanking | `caller_type=aisearch` triggers ScoreFusion code path with rank_by=ScoreFusion | **High** |
| 3 | UnknownCallerType_ReturnsValidationErrorOrFallback | Invalid `caller_type=xyz` returns 400 (or documented fallback) | Medium |
| 4 | BookingCaller_WithNoHardAvailability_ReturnsEmptyWithBanner | Booking caller type when zero slots available — response stays well-formed | Medium |
| 5 | ListingAlgoV1Flavor_Pagination_Page2 | Page 2 of listing-algo-v1 returns next batch with consistent tie-breaker | Medium |
| 6 | ProviderReferralsCaller_OmitsSponsoredAds | providerReferrals never returns SPO ad decisions | **High** |

### I.3 CovidRequestsTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | CovidProcedure_WithoutSpecialtyId_ReturnsValidResponse | Covid procedure id 5028 without specialty (covid relaxation still applies) | Medium |
| 2 | CovidSearch_InFlippedStateNY_BehavesSameAsNJ | Government-insurance bypass applies identically in NY FP state | **High** |
| 3 | CovidSearch_PageSizeAndPagination | Covid search with page_size=25, page=1 returns non-overlapping results | Low |
| 4 | NonCovidProcedure_StillBlocksMedicaidInFpState | Regression: covid bypass does NOT leak to non-covid procedures | **High** |
| 5 | CovidSearch_ReturnsInsuranceBannerSuppressed | "Government insurance not accepted" banner is suppressed for covid | Medium |

### I.4 DependencyFailuresTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | HandlesAbAndAvailabilityConcurrentFailure | Chaos: both AB client and availability fail in same request — service degrades gracefully | **High** |
| 2 | HandlesSpoFailure | SPO dependency unreachable — search still returns organic results with spo section empty/null | **High** |
| 3 | HandlesElasticTimeout | ES timeout (not error) — retry/fallback path returns 503 or degraded response | **High** |
| 4 | HandlesEmbeddingServiceFailure | Voyage/ZeroEntropy SageMaker endpoint down in ScoreFusion path — falls back to non-semantic ranking | **High** |
| 5 | HandlesAbFailureWithNonDefaultAlgorithm | AB failure with `caller_type=aisearch` or flavor override — defaults applied correctly | Medium |
| 6 | HandlesRedisCacheFailure | Redis cache miss/outage — cold path returns valid response | Medium |
| 7 | ElasticsearchQueryError_LogsCorrelationId | 500 response includes searchRequestId for observability | Low |

### I.5 ElasticTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | ElasticQueryWithGeoBoundingBox | Snapshot for bbox location type — differs from point location | **High** |
| 2 | ElasticQueryForProviderName_UsesBm25Analyzer | Searching by provider name uses BM25 full-text analyzer | **High** |
| 3 | ElasticQuery_WithKnnEmbeddings_IncludesVectorSearchClause | Score fusion path emits knn clause against embedding field | **High** |
| 4 | ElasticQuery_EmptyResults_ReturnsWellFormedEmptyResponse | No ES hits — returns 200 with empty provider_locations array and zero aggregations | **High** |
| 5 | ElasticQueryForUnknownSpecialtyId | specialty_id not in ES docs — returns zero hits, no 500 | Medium |
| 6 | ElasticQueryDebugModeProcessors_ExposesAllProcessorSteps | Debug=Processors output contains every processor name in pipeline | Medium |

### I.6 ExampleTests.cs (1 test)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 1 | TokenEmptyTest | Trivial `(1+1).Should().Be(2)` placeholder — no production value; delete or replace with a real smoke test for test host wiring |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | TestHost_StartsAndReturnsOkOnHealthCheck | Replace trivial test with a real health-endpoint smoke check | Low |

### I.7 FacetFilterRequestsTests.cs (5 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | CombinedFacets_ProceduresAndGender_AggregationConsistency | Multi-facet aggregation counts sum <= total_hits | **High** |
| 2 | LanguageFacet_Snapshot | Language facet aggregation snapshot covers multi-language providers | Medium |
| 3 | DayAvailabilityFacet_ReflectsHardAvailability | `facets=day_availability` reflects hard availability filter interplay | Medium |
| 4 | InvalidFacetKey_Ignored_Or_Returns400 | `facets=not_a_real_facet` — either ignored or validation error | Medium |
| 5 | FacetsWithPaginationPage1 | Facet counts remain identical across pages (aggregations not paginated) | **High** |
| 6 | FacetWithBase64Filter_RoundtripsCleanly | b64-encoded filter values decode correctly for all facet types | Medium |

### I.8 GoodRequestsTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | DefaultRequest_ReturnsBothOrganicAndSponsoredSections | Default rank_by returns both organic + sponsored blocks | **High** |
| 2 | HighPageSize_50_SnapshotStable | Max page_size=50 returns stable snapshot without truncation | Medium |
| 3 | DebugSummary_OmitsProcessorsSection | Debug=Summary excludes processor-level detail present in Debug=Full | Medium |
| 4 | LocalDateFutureDate_SerializesProperly | `date_searched_for` in future (within availability window) works | Low |
| 5 | Request_WithNoLocation_UsesIpFallbackOrDefault | Missing location param — confirm default behavior (200 vs 400) | Medium |

### I.9 IncludeMapDotsTests.cs (1 test)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | IncludeMapDots_OnMarketplaceDirectory_IsNoOpOrIgnored | Marketplace directory -1 with `include_map_dots_for_default_enterprise_algo=true` — field absent or null | **High** |
| 2 | IncludeMapDotsFalse_DoesNotReturnProviderLocationsMapDots | Explicitly `false` -> `providerLocationsMapDots` absent | Medium |
| 3 | IncludeMapDots_PageEstimatesCountMatchesDotCount | Each map dot corresponds to a provider location in the hits | Medium |
| 4 | IncludeMapDots_RespectsFilterParams | Filtering by insurance/specialty reduces map dots proportionally | **High** |

### I.10 InsuranceRequestsTests.cs (7 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | UnknownCarrierId_ReturnsValidResponseOrGracefulFallback | Non-existent `insurance_carrier_id` returns 200 with no in-network filter | **High** |
| 2 | MismatchedCarrierAndPlan_LogsWarningAndProceeds | Plan belongs to different carrier — handled without 500 | Medium |
| 3 | DisplaysGovInsuranceBannerIf_SearchedFromFlippedStateNY_WithMedicaid | Positive case: banner IS shown in FP state with Medicaid (non-covid) | **High** |
| 4 | VirtualLocationGroupingByInsurance_WithOutOfNetworkPlans | OON plan grouping differs from in-network | Medium |
| 5 | InsurancePlanWithoutCarrier_ReturnsValidationError | `insurance_plan_id` without carrier — validation error | Medium |
| 6 | MultipleCarriers_NotSupported_ReturnsValidationError | Comma-separated carrier IDs — verify contract | Low |

### I.11 MarketIntelligenceTests.cs (12 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | MarketIntelligence_UnauthorizedDirectory_Returns403 | Non-whitelisted directory call returns 403/404 — auth isolation | **High** |
| 2 | EmptyQueriesArray_Returns400 | `queries: []` returns BadRequest before code runs | Medium |
| 3 | MissingLatLon_Returns400 | Body without lat/lon — plinth validation | Medium |
| 4 | DiscoverVisitReasons_WithoutProcedureId_ReturnsValidResponse | Positive case complement to procedure+discover mutex error | **High** |
| 5 | MarketIntelligence_ElasticsearchFailure_Returns5xx | ES chaos -> MI returns 503/500 (not empty 200) | **High** |
| 6 | MarketIntelligence_SpoFailure_StillReturnsSupplyAndRefinements | SPO down -> supply/refinements intact, page_estimates null | **High** |
| 7 | LargeRadiusRefinement_within_25_or_50_mi | Verify refinement dimensions beyond 10mi if supported | Low |
| 8 | AllSpecialtiesReturned_WithZeroSupply_GracefulEmpty | Remote location, no providers -> structured zero response | Medium |
| 9 | ConcurrentQueries_MaintainQueryIndexOrdering | Parallel MI requests — query_index always echoes input order | Medium |
| 10 | MarketIntelligence_SmokeMode_SkipsStructuralDeepCheck | Smoke mode parity — asserts subset of structure only | Low |
| 11 | MixedScopePerQuery_NotSupported_ReturnsValidationError | Confirm evaluation_scope is per-request, not per-query | Medium |

### I.12 MarketIntelligenceValidationTests.cs (6 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | InNetworkCount_WithMultipleFilters_StaysConsistent | Cross-field constraint with both insurance + gender applied | **High** |
| 2 | SupplyOnlyScope_WithInsurance_InNetworkCountStillPopulated | supply_only with insurance still populates in_network_count | **High** |
| 3 | CoreSearchMatchesMi_AcrossSpecialties | Extend cross-validate to 3 specialties (dentist, derma, PCP) | Medium |
| 4 | DebuggableEndpoint_OnDirectoryIsolation | Debuggable MI for unauthorized directory returns 403, not debug info | **High** |
| 5 | Refinements_NotReturnedForProcedureQuery_DocumentCurrentBehavior | Pin current behavior explicitly | Low |
| 6 | PageEstimates_PconvInRange0To1_AllScopes | Validate pconv range stays in (0,1] across all scope values | Medium |

### I.13 MobileRequestsTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | UnknownUserAgent_FallsBackToWebTreatment | Non-iOS/Android UA string — no mobile experiment flipping | Medium |
| 2 | AndroidUserAgent_OnMarketplaceDirectMapleFlow | Android UA + `X-ZD-Application=iPhoneApp` mismatch — app field wins | Medium |
| 3 | MobileCoinFlip_PersistsAcrossRetries_SameSessionId | Deterministic coin flip for same session id | **High** |
| 4 | MobilePage2_Pagination_SnapshotStable | Mobile pagination (page=2) doesn't break sorting | Medium |
| 5 | Mobile_WithAbOverride_OverridesCoinFlip | X-ZD-ABOverrides overrides mobile coin flip outcome | Medium |

### I.14 OpenSearchTests.cs (6 tests)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 1-6 | CanConnectToOpenSearchCluster, CanListAllIndices, CanGetClusterStats, CanGetSampleDocumentsFromProviderInfoEmbeddingsIndex, CanFindProviderStatementWithEmbeddings, GetIndexMappingAndModelInfo, InspectSpecificProvider | Hit a hardcoded prod ES cluster URL (`vpc-ci001-sam-search-...`). They are infra-connectivity checks, not YASS-Sharp behavior. Require VPN, won't run reliably in CI/local. Migrate to a proper mocked ES client contract test or remove in favor of DependencyFailuresTests. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | Es7Client_ConnectionTimeout_Reconnects | ES client resilience on transient network errors (mocked, not live) | **High** |
| 2 | Es7Client_ParsesKnnResponseWithEmbeddings | Exercise the knn_vector field parsing path end-to-end | **High** |
| 3 | Es7Client_EmptyIndex_ReturnsEmptyResults | Empty index returns structured empty response | Medium |
| 4 | IndexName_ResolvedPerAbOverride | Streaming vs non-streaming index selection based on ABOverride | **High** |

### I.15 ParametersRequestsTests.cs (39 test cases; 1 ignored)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 24 | MatchesForParameter("practice") | [Ignore] — `MarketplaceSearchPracticeAlgoContainer.Algorithm` unimplemented. If production has no practice search path, remove; otherwise block on implementing it. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | MatchesForParameter("scoreFusion") | rank_by=ScoreFusion with search_query triggers FTS+embeddings path | **High** |
| 2 | MatchesForParameter("raceEthnicity") | Filter by race/ethnicity facet if product-supported | Medium |
| 3 | MatchesForParameter("newPatientsOnly") | `accepting_new_patients=true` affects ES filter | Medium |
| 4 | MatchesForParameter("nextAvailableWithin24h") | Availability-window filter produces narrower result set | **High** |
| 5 | MatchesForParameter("multipleSpecialtiesCommaSeparated") | Multi-specialty OR query | Medium |
| 6 | MatchesForParameter("bigPage50SnapshotDiff") | Snapshot for the largest allowed page_size=50 | Medium |
| 7 | MatchesForParameter("aisearchWithLongQuery") | 256-char search_query via aisearch caller type | **High** |
| 8 | ParamCase_MatchesInSmokeMode | Smoke-mode result keys are a subset of snapshot-mode keys | Medium |

### I.16 PlacemarkRequestsTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | SeoPlacemark_SearchReturnsDistinctRanking | `location_type=seo_placemark` ranking differs from placemark | **High** |
| 2 | Placemark_WithCityStateMismatch_StillReturnsResults | location inside NY but state=NJ — graceful handling | Medium |
| 3 | Placemark_OutsideServiceArea_ReturnsEmpty200 | Placemark in a remote area returns empty provider list cleanly | Medium |
| 4 | Placemark_WithInsurance_MaintainsGrouping | Placemark + insurance carrier maintains virtual/organic grouping | Medium |

### I.17 PostEndpointTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | PostEndpoint_BodyParamsDoNotAppearInAccessLog | PII redaction — fts_search_query/ce_search_query absent from logs | **High** |
| 2 | PostEndpoint_BodyOverridesQueryString_ForSameKey | Body vs query string precedence when both set `search_query` | **High** |
| 3 | PostEndpoint_LargeBody_HandledWithin60s | Body with 10KB search_query still returns 200 | Medium |
| 4 | PostEndpoint_MalformedJson_Returns400 | Body with invalid JSON returns 400 | **High** |
| 5 | PostEndpoint_WithDirectoryIsolation | POST to unauthorized directory returns 403 | **High** |
| 6 | PostEndpoint_SnapshotParityWithGetForSameParams | POST-with-body and GET-with-query produce equivalent response | **High** |

### I.18 ScopedRequestsTests.cs (3 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | InvalidVisitType_Returns400 | `visit_type=walkInClinic` (unknown enum) returns 400 | Medium |
| 2 | VirtualVisit_WithVirtualIneligibleSpecialty_ReturnsEmpty | Specialty that doesn't offer virtual visits returns empty hits cleanly | Medium |
| 3 | VirtualVisit_WithCrossStateInsurance_FiltersCorrectly | Virtual visit state eligibility rules (state licensing) applied | **High** |
| 4 | InPersonAndVirtual_MaintainsOrganicAndVirtualGroups | Combined visit type — both groups present in response | **High** |

### I.19 SearchCountRequestsTests.cs (2 tests; both Ignored)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 1 | ShouldReturnCorrectResponseWithTotalCountOfProvLocs | [Ignore] — count endpoint not implemented in C#. Remove the file if the endpoint is truly gone. |
| 2 | ShouldReturnCorrectResponseWithTotalCountOf0WhenNoProvLocsExist | [Ignore] — same reason. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | DebuggableSearch_TotalHitsField_Populated | Replacement: assert `total_hits` in main search response | **High** |
| 2 | DebuggableSearch_TotalHitsZero_WhenLocationOutOfRange | Zero-total-hits contract verified via main endpoint | Medium |

### I.20 SpoRequestsTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | SpoDecisions_WhenInsuranceProgramNotSet_Empty | Negative case: missing insurance_program_type_name -> zero SPO ads | **High** |
| 2 | SpoDecisions_WithV22MapleAlgorithm | Parity for `YASS_Maple_V21_vs_V22 = maple_v22` | **High** |
| 3 | SpoDecisions_WithSpoServiceTimeout | SPO timeout — organic path intact, spo section null or empty | **High** |
| 4 | SpoDecisions_FilterByDirectoryVisibility | SPO only emits ads permitted for the calling directory | **High** |
| 5 | SpoDecisions_WithProviderReferralsCaller_AreSuppressed | SPO never served to provider-referrals caller | Medium |

### I.21 UnsuccessfulRequestsTests.cs (22 test cases; 1 ignored)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 2 | MatchesForBadRequest("negativeDistanceRadius") | [Ignore] — "non-deterministic ES query structure." Either deterministically assert HTTP status or delete; snapshot churn makes it low-value. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | MatchesForBadRequest("bigPageNegative") | Negative page_size branch | Medium |
| 2 | MatchesForBadRequest("nonNumericSpecialty") | `specialty_id=abc` validation | Medium |
| 3 | MatchesForBadRequest("conflictingVisitTypeAndCaller") | `visit_type=virtualVisit` + `caller_type=booking` conflict | Medium |
| 4 | MatchesForBadRequest("tooLongSearchQuery") | search_query > max allowed length returns 400 | **High** |
| 5 | MatchesForBadRequest("nullDirectoryIdInPath") | `/directories//provider-locations` returns 404 | **High** |
| 6 | MatchesForBadRequest("unauthorizedDirectory") | Access to directory caller lacks permission for returns 403 | **High** |
| 7 | MatchesForBadRequest("injectionPayload") | SQL/ES-injection-flavored strings sanitized | Medium |

### I.22 VoyageTests.cs (11 tests; [Explicit])

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 1-11 | All tests | Fixture is `[Explicit]` — not run in CI by default; hits live SageMaker endpoint (incurs cost). Keep for manual validation; do NOT count toward regression coverage. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | VoyageEndpointDown_FallsBackToNonSemanticRanking | End-to-end: when voyage-4 endpoint is down, YASS falls back to BM25 without 500 | **High** |
| 2 | VoyageEmbeddingCache_HitAvoidsSageMakerCall | Cache hit path — no SageMaker invocation for repeated query | **High** |
| 3 | VoyageTimeout_RaisesMetricAndFallsBack | Timeout path emits DataDog metric and uses fallback ranker | **High** |
| 4 | VoyageService_Is_Instrumented_WithLatencyHistogram | Each call emits an `embedding_latency_ms` metric | Medium |

### I.23 WarpspeedRequestsTests.cs (2 tests; both Ignored)

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 1 | ShowsResultsForVaccineInsideIL | [Ignore] — vaccine algo unimplemented in C#. If product path is deprecated, delete file; else gate on algo impl. |
| 2 | ShowsNoFacetsEvenIfTheyAreRequestedForVaccineSearch | [Ignore] — same. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | VaccineSearch_NotImplemented_Returns501Or400 | If vaccine caller_type is still exposed, confirm it returns a clean error rather than 500 | Medium |

### I.24 WhiteLabelTests.cs (2 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | WhiteLabelDirectory_OnlyReturnsProvidersInThatDirectory | Directory isolation — every hit belongs to directory 963 (GPH) | **High** |
| 2 | WhiteLabelDirectory_AuthBypassAttempt_Returns403 | Caller without access to directory 459 gets 403 | **High** |
| 3 | Gph_VsSchweiger_ReturnsDifferentAlgorithmNames | Different whitelabel directories route to different algorithms | **High** |
| 4 | WhiteLabel_InsuranceFilter_RespectsDirectoryContractList | Directory-specific insurance acceptance rules applied | **High** |
| 5 | WhiteLabel_WithCovidRelaxation_RespectsDirectoryOverride | Whitelabel override for covid/government-insurance banner rules | Medium |
| 6 | WhiteLabel_PaginationMaintainsDirectoryFilter | Page 2 still respects directory isolation | Medium |
| 7 | WhiteLabel_SmokeMode_ReturnsAuditDataStructurallySimilarToSnapshot | Smoke vs snapshot parity | Medium |

### I.25 ZeroEntropyTests.cs (14 tests; [Explicit])

**Irrelevant Tests:**

| Test # | Test Name | Issue |
|---|---|---|
| 1-14 | All tests | Fixture is `[Explicit]` — not run in CI by default; hits live SageMaker endpoint. Keep for manual validation only; not counted for regression coverage. |

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | ZeroEntropyDown_ScoreFusionFallsBackToBm25 | End-to-end fallback when cross-encoder endpoint unreachable | **High** |
| 2 | ZeroEntropy_BatchSizeExceedsLimit_ChunksCorrectly | Large doc batch is chunked server-side (>1000 docs) | Medium |
| 3 | ZeroEntropy_CacheHit_SkipsSageMakerCall | Repeated query+docs served from cache | **High** |
| 4 | ZeroEntropy_MetricsEmitted_PerCall | Each call emits `ce_inference_ms` histogram | Medium |

#### Search/Datalake

### I.26 FirehoseIntegrationTests.cs (4 tests)

**Irrelevant Tests:** None — all tests are relevant.

**Missing Tests:**

| # | Suggested Test | What It Would Test | Priority |
|---|---|---|---|
| 1 | LogAsync_WhenStreamDoesNotExist_ThrowsOrLogs | Stream deleted mid-run — service raises exception (or swallows per config) | **High** |
| 2 | LogAsync_WhenEnabledIsFalse_NoRecordIsPut | Config `Enabled=false` — short-circuit without calling Firehose | **High** |
| 3 | LogBatchAsync_ExceedsBatchSizeLimit_SplitsIntoMultipleCalls | >500 records or >4MB batch split into chunks | **High** |
| 4 | LogAsync_FirehoseTimeout_DoesNotBlockCaller | Slow Firehose call times out within configured TimeoutMs and is swallowed | **High** |
| 5 | LogAsync_RedactsPhiFields | Any PHI-adjacent fields are redacted before going to Firehose | **High** |
| 6 | LogAsync_ScoringAuditLog_WithLargeFeatureVector | 1000-length feature vector serialized and put successfully | Medium |
| 7 | LogAsync_LocalStackUnavailable_TestsSkippedCleanly | Skip path works cleanly (no flakiness) | Low |
| 8 | FirehoseService_IsEnabled_False_WhenConfigDisabled | Config-driven IsEnabled = false | Medium |


---

# Part 3 — High-Priority Gaps Summary

Cross-cutting themes aggregated from all eight unit-test chunks and the integration chunk. Each theme lists the risk, the primary sections to consult, and representative missing tests.

## 1. Cross-directory / whitelabel isolation (GPH 963, Schweiger 459, marketplace -1)

**Risk:** A provider, brand, insurance plan, or SPO ad visible in one directory leaks into another — a P0 customer-trust bug.

**Primary sections:**
- `F.4 ProvLocResultTests` / `F.15 ProviderDeduperTests` / `F.6 BannerInfoTests` / `F.22 ResponseInfoTests` (Chunk F — Search/Yass)
- `D.*` ES filter-builder tests that assert `directoryId` clauses (Chunk D)
- `C.8 ProvLocResponseTests` (Chunk C — Search/Contracts)
- `I.1 BrandRequestsTests` / `I.13 InsuranceRequestsTests` / `I.19 SpoRequestsTests` / `I.24 WhitelabelRequestsTests` (Chunk I — Integration)

**Representative missing tests:**
- `BrandAggregationsRespectDirectoryIsolation` — brand aggregations for directory -1 exclude providers visible only in enterprise directories.
- `ProvLocDedupe_WhenSameProvInDirectoryAndMarketplace_KeepsDirectoryOnly`
- `ProviderReferralsCaller_OmitsSponsoredAds` — providerReferrals never returns SPO ad decisions.
- `GphOnlyProvider_NotReturnedForMarketplaceSearch`
- `SchweigerLocale_RankingModel_UsesSchweigerFeaturesOnly`

## 2. PHI sanitisation & safety

**Risk:** Patient-identifying content appearing in logs, previews, or ads — regulatory and trust impact.

**Primary sections:**
- `H.60 SensitiveHealthInformationCheckerErrorTests` (Chunk H — zero test methods today)
- `H.4 PreviewModeTests` (Chunk H)
- `F.12 PreviewProvLocResultTests` (Chunk F)
- `E.1 BestSentenceEnricherTests` / `E.7 CrossEncoderClientTests` (Chunk E) — sentence sanitisation for ranked responses
- `I.16 PreviewModeRequestsTests` (Chunk I)

**Representative missing tests:**
- `SensitiveHealthInformationChecker_WhenInputContainsCondition_ReturnsRedacted` (the only test today is a happy-path smoke — PHI-critical branches untested).
- `PreviewProvLocResult_StripsPatientReviewFirstName_AndLastInitial`
- `BestSentenceEnricher_WhenSentenceContainsCondition_SkipsOrRedacts`
- `FirehoseAudit_PreviewMode_DoesNotLogRawQueryOrPatientId`

## 3. JSON contract stability (`[JsonPropertyName]` round-trips)

**Risk:** Silent DTO renames or case changes break downstream consumers (mobile, web, partner feeds) because C#-level property tests pass even after the wire format shifts.

**Primary sections:**
- `G.1 – G.18` (Chunk G — Search/Types) — **every DTO** is missing a round-trip test.
- `C.*` — `SpoAdsResponseTests`, `ProvLocResponseTests`, `YassRequestHeaderTests` (Chunk C).

**Representative missing tests:**
- `CostPlan_JsonRoundTrip_UsesCamelCasePropertyNames` (and one per DTO).
- `SpoAdsResponse_JsonRoundTrip_UsesSnakeCase_EvenWhenSiblingDtosUseCamelCase` — captures the inconsistency so accidental unification is caught.
- `ProvLocResponse_JsonRoundTrip_StablyPreservesBrandCountAndOonFlag`.

## 4. AB-flag plumbing (`YASS-Use-Es7`, `YASS-Streaming-Index-Test`, ScoreFusion)

**Risk:** Experiments silently fall back to control (or control path regressed) — skews experiment results and masks bugs.

**Primary sections:**
- `A.1 AbExperimentsTests` (Chunk A)
- `D.1 Es7ClientPreferenceTests`, streaming-index tests (Chunk D)
- `E.*` ScoreFusion-related sections (Chunk E)
- `I.2 CallerTypeRequestsTests`, `I.8 EsClientVersionRequestsTests`, `I.17 ScoreFusionRequestsTests` (Chunk I)

**Representative missing tests:**
- `AiSearchCallerType_EnablesScoreFusionRanking`
- `BrandFilter_WithEs7Off_ProducesEquivalentResults`
- `YassUseEs7_ExplicitOverride_Wins_OverDefaultAssignment`
- `StreamingIndexTest_ControlAndTest_PayloadStructurallyIdentical`

## 5. Ranking & scoring correctness

**Risk:** Silent drift in features, cross-encoder error handling, or Voyage/ZeroEntropy failures degrades relevance without a signal.

**Primary sections:**
- `E.1 BestSentenceEnricherTests`, `E.7 CrossEncoderClientTests`, `E.*` ScoreFusion / LightGBM tests (Chunk E)
- `H.CrossEncoder.*`, `H.Embeddings.*` (Chunk H)
- `B.*` algorithm-builder copy/validate coverage (Chunk B)

**Representative missing tests:**
- `BestSentenceEnricher_CrossEncoderTimeout_FallsBackToOriginalOrderingAndEmitsMetric`
- `VoyageEmbeddings_ResponseDimMismatch_Throws_AndEmitsMetric`
- `LightGbmFeaturePipeline_FeatureOrderMatchesModelInputSchema` (pin the order explicitly).
- `ScoreFusion_WhenOneBranchEmpty_ReturnsOtherBranch_WithoutDividingByZero`.

## 6. Market Intelligence correctness

**Risk:** MI powers supply/revenue dashboards — incorrect tie-breaking or fan-out caps silently bias product decisions.

**Primary sections:**
- `H.1 FilterSerializerTests`, `H.2 MarketIntelligenceQueryValidatorTests`, `H.3 MarketIntelligenceServiceTests`, `H.4 PreviewModeTests` (Chunk H)
- `I.14 MarketIntelligenceRequestsTests`, `I.15 MarketIntelligenceValidationTests` (Chunk I)

**Representative missing tests:**
- `MarketIntelligenceService_SupplyRankTieBreak_IsDeterministicAcrossRuns`
- `MarketIntelligenceQueryValidator_SpecialtyFanOutCap_PreservesFirstN_NotArbitraryN`
- `MarketIntelligenceService_DiscoverVisitReasons_ZeroBuckets_ReturnsEmpty_NotError`
- `MarketIntelligence_PreviewMode_WithInsurancePlanId_DoesNotLeakPlanAcrossBranches`

## 7. Observability (Statsd, Firehose, correlation-id)

**Risk:** On-call can't diagnose ranking regressions because error paths don't emit metrics or correlation IDs don't flow.

**Primary sections:**
- `H.Statsd.*` (Chunk H)
- `G.19 AuditWriterTests` (Chunk G)
- `F.*` correlation-id propagation (Chunk F)
- `I.11 FirehoseAuditRequestsTests` (Chunk I)

**Representative missing tests:**
- `CrossEncoderClient_OnError_EmitsErrorCounter_WithVendorTag`
- `AuditWriter_MaxAgeCleanup_DeletesRecordsOlderThanConfigured`
- `SearchParams_CorrelationIdFromHeader_PropagatesToFirehoseAndDownstreamClients`
- `FirehoseAudit_RawQueryStringPreserved_ForReplayabilityButRedactedForPreview`

## 8. API validation & contract

**Risk:** Unvalidated inputs reach ES (or worse, the ranking pipeline) and cause 500s or wrong results.

**Primary sections:**
- `C.YassRequestHeaderTests` / `C.ReflectionHelpers.GetKnownParams` (Chunk C)
- `G.26 QueryValidationUtilsTests` (Chunk G)
- `I.15 MarketIntelligenceValidationTests`, `I.22 ValidationRequestsTests` (Chunk I)

**Representative missing tests:**
- `OnlyUsesKnownParams_WhenUnknownParamPresent_Returns400_WithParamName`
- `QueryValidationUtils_IsValid_RejectsMultiWordQueryOverConfiguredCap`
- `YassRequestHeader_MalformedDirectoryIdPath_FallsBackToMarketplace`

## 9. Test-hygiene issues flagged during analysis

- `H.56` has a test (`_WithDuplicateMonolithIds_ShouldDeduplicate`) whose assertion contradicts its name — either the test or the implementation is wrong and should be reconciled.
- `H.11 EnchiladaFeatureNamesTests` is entirely `[Ignore]`d — either re-enable or delete.
- `C.ProvLocResponseTests` #4 and #5 are methodologically broken (#5's assertion doesn't reference the result at all).
- `G.27 S3UtilsTests` asserts on `DYNAMO_DB_ENDPOINT` branches that don't exist in source — stale test.
- `A.1 AbExperimentsTests` test #1 has a conditional assertion inside an `if`; the else branch is a silent pass.
- Multiple fixtures (`H.5, H.21, H.28, H.36, H.37, H.40, H.43, H.61, H.69`, and `F.*` singleton filterers) assert only that a constructor runs and a property is non-null — they don't exercise behaviour. Flagged for rewrite, not just deletion.

---

## Suggested rollout

1. **Quick wins (1–2 sprints):** Fix the broken/hygiene tests in §9 and delete/rewrite tautological fixtures — net reduction in test-suite noise, no new behaviour covered but false-green signal removed.
2. **Contract safety (2–3 sprints):** Add JSON round-trip tests per Part 3 §3 — mechanical, high leverage, unblocks safe DTO refactors.
3. **Isolation & PHI (3–4 sprints):** Add the cross-directory and PHI tests in §1–2 — highest business risk.
4. **Relevance / MI / observability (ongoing):** §4–7 — bundle alongside feature work in those areas so the tests land with the code.

---

*End of report.*
