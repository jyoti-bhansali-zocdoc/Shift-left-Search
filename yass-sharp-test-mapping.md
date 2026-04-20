# YassSharp Unit Tests - Test Case Mapping

**Repository:** https://github.com/Zocdoc/yass-sharp/tree/main/tests/YassSharp.UnitTests  
**Framework:** NUnit  
**Total Test Files:** 426  
**Total Test Cases:** 2558  

---

# (root)

## ExampleTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Example_ShouldPass | Verifying that example should pass | Setup test data and mocks -> Call Example -> Assert expected behavior of Example | Example should pass | In scope: Example behavior, should pass scenario. Out of scope: other scenarios and methods not under test. |

# Ab

## ABServiceClientErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAssignments_WhenHttpClientThrows_ShouldReturnEmptyAssignments | Verifying that get assignments when http client throws returns empty assignments | Setup mock to throw exception -> Call GetAssignments -> Assert returns empty collection | GetAssignments when http client throws returns empty assignments | In scope: error handling in GetAssignments. Out of scope: successful execution paths. |
| 2 | | GetAssignments_WhenResponseIsInvalid_ShouldReturnEmptyAssignments | Verifying that get assignments when response is invalid returns empty assignments | Setup when response is invalid -> Call GetAssignments -> Assert returns empty collection | GetAssignments when response is invalid returns empty assignments | In scope: GetAssignments behavior, when response is invalid scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAssignments_WhenDeserializationFails_ShouldReturnEmptyAssignments | Verifying that get assignments when deserialization fails returns empty assignments | Setup mock to throw exception -> Call GetAssignments -> Assert returns empty collection | GetAssignments when deserialization fails returns empty assignments | In scope: error handling in GetAssignments. Out of scope: successful execution paths. |

## ABServiceClientV2AdapterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAssignments_ShouldCallClientV2WithCorrectParameters | Verifying that get assignments should call client v2 with correct parameters | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should call client v2 with correct parameters | In scope: GetAssignments behavior, should call client v2 with correct parameters scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAssignments_ShouldReturnDeserializedAssignments | Verifying that get assignments should return deserialized assignments | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should return deserialized assignments | In scope: GetAssignments behavior, should return deserialized assignments scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAssignments_ShouldIncludeExperimentIds | Verifying that get assignments should include experiment ids | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should include experiment ids | In scope: GetAssignments behavior, should include experiment ids scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAssignments_ShouldPassContextProperly | Verifying that get assignments should pass context properly | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should pass context properly | In scope: GetAssignments behavior, should pass context properly scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAssignments_WhenNoExperiments_ShouldReturnEmpty | Verifying that get assignments when no experiments returns empty | Setup when no experiments -> Call GetAssignments -> Assert returns empty collection | GetAssignments when no experiments returns empty | In scope: GetAssignments behavior, when no experiments scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAssignments_ShouldHandleNullResponse | Verifying that get assignments should handle null response | Setup with null input -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should handle null response | In scope: null input handling for GetAssignments. Out of scope: valid input scenarios. |
| 7 | | GetAssignments_ShouldReturnCorrectNumberOfAssignments | Verifying that get assignments should return correct number of assignments | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should return correct number of assignments | In scope: GetAssignments behavior, should return correct number of assignments scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAssignments_WhenSingleExperiment_ShouldReturnSingleAssignment | Verifying that get assignments when single experiment returns single assignment | Setup when single experiment -> Call GetAssignments -> Assert return single assignment | GetAssignments when single experiment returns single assignment | In scope: GetAssignments behavior, when single experiment scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAssignments_ShouldPassThroughHeaders | Verifying that get assignments should pass through headers | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should pass through headers | In scope: GetAssignments behavior, should pass through headers scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAssignments_ShouldIncludePlatformInContext | Verifying that get assignments should include platform in context | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should include platform in context | In scope: GetAssignments behavior, should include platform in context scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAssignments_ShouldIncludeZocdocAppVersion | Verifying that get assignments should include zocdoc app version | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should include zocdoc app version | In scope: GetAssignments behavior, should include zocdoc app version scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetAssignments_WithNullPlatform_ShouldStillWork | Verifying that get assignments with null platform still work | Setup with null input -> Call GetAssignments -> Assert still work | GetAssignments with null platform still work | In scope: null input handling for GetAssignments. Out of scope: valid input scenarios. |
| 13 | | GetAssignments_ShouldMapVariantCorrectly | Verifying that get assignments should map variant correctly | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should map variant correctly | In scope: GetAssignments behavior, should map variant correctly scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetAssignments_ShouldMapParameterCorrectly | Verifying that get assignments should map parameter correctly | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should map parameter correctly | In scope: GetAssignments behavior, should map parameter correctly scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetAssignments_WithControlGroup_ShouldMapCorrectly | Verifying that get assignments with control group map correctly | Setup with control group -> Call GetAssignments -> Assert map correctly | GetAssignments with control group map correctly | In scope: GetAssignments behavior, with control group scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | GetAssignments_ShouldNotIncludeExperimentWithNoAssignment | Verifying that get assignments should not include experiment with no assignment | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should not include experiment with no assignment | In scope: GetAssignments behavior, should not include experiment with no assignment scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | GetAssignments_WithMultipleExperiments_ShouldReturnAll | Verifying that get assignments with multiple experiments returns all | Setup with multiple experiments -> Call GetAssignments -> Assert return all | GetAssignments with multiple experiments returns all | In scope: GetAssignments behavior, with multiple experiments scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | GetAssignments_ShouldUseCorrectEndpoint | Verifying that get assignments should use correct endpoint | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should use correct endpoint | In scope: GetAssignments behavior, should use correct endpoint scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | GetAssignments_ShouldIncludeDeviceId | Verifying that get assignments should include device id | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should include device id | In scope: GetAssignments behavior, should include device id scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | GetAssignments_ShouldIncludeUserId | Verifying that get assignments should include user id | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should include user id | In scope: GetAssignments behavior, should include user id scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | GetAssignments_WithNullDeviceId_ShouldStillWork | Verifying that get assignments with null device id still work | Setup with null input -> Call GetAssignments -> Assert still work | GetAssignments with null device id still work | In scope: null input handling for GetAssignments. Out of scope: valid input scenarios. |
| 22 | | GetAssignments_WithNullUserId_ShouldStillWork | Verifying that get assignments with null user id still work | Setup with null input -> Call GetAssignments -> Assert still work | GetAssignments with null user id still work | In scope: null input handling for GetAssignments. Out of scope: valid input scenarios. |
| 23 | | GetAssignments_ShouldReturnFlagStatus | Verifying that get assignments should return flag status | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should return flag status | In scope: GetAssignments behavior, should return flag status scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | GetAssignments_ShouldHandlePartialResponse | Verifying that get assignments should handle partial response | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should handle partial response | In scope: GetAssignments behavior, should handle partial response scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | GetAssignments_WithTimeout_ShouldThrow | Verifying that get assignments with timeout throw | Setup with timeout -> Call GetAssignments -> Assert exception is thrown | GetAssignments with timeout throw | In scope: GetAssignments behavior, with timeout scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | GetAssignments_ShouldLogRequestDetails | Verifying that get assignments should log request details | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should log request details | In scope: GetAssignments behavior, should log request details scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | GetAssignments_ShouldTrackLatency | Verifying that get assignments should track latency | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should track latency | In scope: GetAssignments behavior, should track latency scenario. Out of scope: other scenarios and methods not under test. |

## ABServiceClientV3Tests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAssignments_ShouldCallV3Endpoint | Verifying that get assignments should call v3 endpoint | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should call v3 endpoint | In scope: GetAssignments behavior, should call v3 endpoint scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAssignments_ShouldPassExperimentIds | Verifying that get assignments should pass experiment ids | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should pass experiment ids | In scope: GetAssignments behavior, should pass experiment ids scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAssignments_ShouldReturnMappedAssignments | Verifying that get assignments should return mapped assignments | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should return mapped assignments | In scope: GetAssignments behavior, should return mapped assignments scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAssignments_WithEmptyResponse_ShouldReturnEmpty | Verifying that get assignments with empty response returns empty | Setup with empty input -> Call GetAssignments -> Assert returns empty collection | GetAssignments with empty response returns empty | In scope: empty input handling for GetAssignments. Out of scope: non-empty input scenarios. |
| 5 | | GetAssignments_ShouldIncludeContextHeaders | Verifying that get assignments should include context headers | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should include context headers | In scope: GetAssignments behavior, should include context headers scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAssignments_ShouldPassDeviceId | Verifying that get assignments should pass device id | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should pass device id | In scope: GetAssignments behavior, should pass device id scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAssignments_ShouldPassUserId | Verifying that get assignments should pass user id | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should pass user id | In scope: GetAssignments behavior, should pass user id scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAssignments_ShouldPassSessionId | Verifying that get assignments should pass session id | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should pass session id | In scope: GetAssignments behavior, should pass session id scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAssignments_ShouldMapVariantValues | Verifying that get assignments should map variant values | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should map variant values | In scope: GetAssignments behavior, should map variant values scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAssignments_ShouldMapParameters | Verifying that get assignments should map parameters | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should map parameters | In scope: GetAssignments behavior, should map parameters scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAssignments_WithMultipleAssignments_ShouldReturnAll | Verifying that get assignments with multiple assignments returns all | Setup with multiple assignments -> Call GetAssignments -> Assert return all | GetAssignments with multiple assignments returns all | In scope: GetAssignments behavior, with multiple assignments scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetAssignments_WithControlVariant_ShouldMapCorrectly | Verifying that get assignments with control variant map correctly | Setup with control variant -> Call GetAssignments -> Assert map correctly | GetAssignments with control variant map correctly | In scope: GetAssignments behavior, with control variant scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetAssignments_WithNullableFields_ShouldHandleGracefully | Verifying that get assignments with nullable fields handle gracefully | Setup with null input -> Call GetAssignments -> Assert handle gracefully | GetAssignments with nullable fields handle gracefully | In scope: null input handling for GetAssignments. Out of scope: valid input scenarios. |
| 14 | | GetAssignments_ShouldLogRequestAndResponse | Verifying that get assignments should log request and response | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should log request and response | In scope: GetAssignments behavior, should log request and response scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetAssignments_ShouldEmitMetrics | Verifying that get assignments should emit metrics | Setup test data and mocks -> Call GetAssignments -> Assert expected behavior of GetAssignments | GetAssignments should emit metrics | In scope: GetAssignments behavior, should emit metrics scenario. Out of scope: other scenarios and methods not under test. |

## AbExperimentsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | AllExperimentIds_ShouldReturnNonEmptyCollection | Verifying that all experiment ids should return non empty collection | Setup with empty input -> Call AllExperimentIds -> Assert expected behavior of AllExperimentIds | AllExperimentIds should return non empty collection | In scope: empty input handling for AllExperimentIds. Out of scope: non-empty input scenarios. |
| 2 | | AllExperimentIds_ShouldContainUniqueValues | Verifying that all experiment ids should contain unique values | Setup test data and mocks -> Call AllExperimentIds -> Assert expected behavior of AllExperimentIds | AllExperimentIds should contain unique values | In scope: AllExperimentIds behavior, should contain unique values scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | EachExperiment_ShouldHaveNonNullExperimentId | Verifying that each experiment should have non null experiment id | Setup with null input -> Call EachExperiment -> Assert expected behavior of EachExperiment | EachExperiment should have non null experiment id | In scope: null input handling for EachExperiment. Out of scope: valid input scenarios. |
| 4 | | EachExperiment_ShouldHaveNonNullFlagName | Verifying that each experiment should have non null flag name | Setup with null input -> Call EachExperiment -> Assert expected behavior of EachExperiment | EachExperiment should have non null flag name | In scope: null input handling for EachExperiment. Out of scope: valid input scenarios. |
| 5 | | EachExperiment_ShouldHaveNonNullExperimentOwner | Verifying that each experiment should have non null experiment owner | Setup with null input -> Call EachExperiment -> Assert expected behavior of EachExperiment | EachExperiment should have non null experiment owner | In scope: null input handling for EachExperiment. Out of scope: valid input scenarios. |
| 6 | | EachExperiment_ExperimentId_ShouldNotContainWhitespace | Verifying that each experiment experiment id does not contain whitespace | Setup test data and mocks -> Call EachExperiment -> Assert not contain whitespace | EachExperiment experiment id does not contain whitespace | In scope: EachExperiment behavior, experiment id scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | EachExperiment_FlagName_ShouldNotContainWhitespace | Verifying that each experiment flag name does not contain whitespace | Setup test data and mocks -> Call EachExperiment -> Assert not contain whitespace | EachExperiment flag name does not contain whitespace | In scope: EachExperiment behavior, flag name scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ExperimentProperties_ShouldBeConsistent | Verifying that experiment properties should be consistent | Setup test data and mocks -> Call ExperimentProperties -> Assert expected behavior of ExperimentProperties | ExperimentProperties should be consistent | In scope: ExperimentProperties behavior, should be consistent scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | TotalExperimentCount_ShouldMatchExpected | Verifying that total experiment count should match expected | Setup test data and mocks -> Call TotalExperimentCount -> Assert expected behavior of TotalExperimentCount | TotalExperimentCount should match expected | In scope: TotalExperimentCount behavior, should match expected scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | AllExperimentIds_ShouldNotContainDuplicates | Verifying that all experiment ids should not contain duplicates | Setup test data and mocks -> Call AllExperimentIds -> Assert expected behavior of AllExperimentIds | AllExperimentIds should not contain duplicates | In scope: AllExperimentIds behavior, should not contain duplicates scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | AllFlagNames_ShouldBeDistinct | Verifying that all flag names should be distinct | Setup test data and mocks -> Call AllFlagNames -> Assert expected behavior of AllFlagNames | AllFlagNames should be distinct | In scope: AllFlagNames behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | ExperimentOwners_ShouldAllBeValid | Verifying that experiment owners should all be valid | Setup test data and mocks -> Call ExperimentOwners -> Assert expected behavior of ExperimentOwners | ExperimentOwners should all be valid | In scope: ExperimentOwners behavior, should all be valid scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Experiments_ShouldImplementIYassExperiment | Verifying that experiments should implement i yass experiment | Setup test data and mocks -> Call Experiments -> Assert expected behavior of Experiments | Experiments should implement i yass experiment | In scope: Experiments behavior, should implement i yass experiment scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Experiments_ShouldHaveCorrectFormat | Verifying that experiments should have correct format | Setup test data and mocks -> Call Experiments -> Assert expected behavior of Experiments | Experiments should have correct format | In scope: Experiments behavior, should have correct format scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | MarketplaceSearchNoMSC_ShouldHaveCorrectId | Verifying that marketplace search no m s c should have correct id | Setup test data and mocks -> Call MarketplaceSearchNoMSC -> Assert expected behavior of MarketplaceSearchNoMSC | MarketplaceSearchNoMSC should have correct id | In scope: MarketplaceSearchNoMSC behavior, should have correct id scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | MarketplaceSearchRelevancyReranking_ShouldHaveCorrectProperties | Verifying that marketplace search relevancy reranking should have correct properties | Setup test data and mocks -> Call MarketplaceSearchRelevancyReranking -> Assert expected behavior of MarketplaceSearchRelevancyReranking | MarketplaceSearchRelevancyReranking should have correct properties | In scope: MarketplaceSearchRelevancyReranking behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | ConstrainedScoreFusion_ShouldHaveCorrectProperties | Verifying that constrained score fusion should have correct properties | Setup test data and mocks -> Call ConstrainedScoreFusion -> Assert expected behavior of ConstrainedScoreFusion | ConstrainedScoreFusion should have correct properties | In scope: ConstrainedScoreFusion behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | VectorSearchEnrichment_ShouldHaveCorrectProperties | Verifying that vector search enrichment should have correct properties | Setup test data and mocks -> Call VectorSearchEnrichment -> Assert expected behavior of VectorSearchEnrichment | VectorSearchEnrichment should have correct properties | In scope: VectorSearchEnrichment behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | CrossEncoderReranking_ShouldHaveCorrectProperties | Verifying that cross encoder reranking should have correct properties | Setup test data and mocks -> Call CrossEncoderReranking -> Assert expected behavior of CrossEncoderReranking | CrossEncoderReranking should have correct properties | In scope: CrossEncoderReranking behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | BestSentenceEnrichment_ShouldHaveCorrectProperties | Verifying that best sentence enrichment should have correct properties | Setup test data and mocks -> Call BestSentenceEnrichment -> Assert expected behavior of BestSentenceEnrichment | BestSentenceEnrichment should have correct properties | In scope: BestSentenceEnrichment behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | KeywordEnrichment_ShouldHaveCorrectProperties | Verifying that keyword enrichment should have correct properties | Setup test data and mocks -> Call KeywordEnrichment -> Assert expected behavior of KeywordEnrichment | KeywordEnrichment should have correct properties | In scope: KeywordEnrichment behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | OrganicOnlyBoxRanker_ShouldHaveCorrectProperties | Verifying that organic only box ranker should have correct properties | Setup test data and mocks -> Call OrganicOnlyBoxRanker -> Assert expected behavior of OrganicOnlyBoxRanker | OrganicOnlyBoxRanker should have correct properties | In scope: OrganicOnlyBoxRanker behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | PageVectorSearchEnrichment_ShouldHaveCorrectProperties | Verifying that page vector search enrichment should have correct properties | Setup test data and mocks -> Call PageVectorSearchEnrichment -> Assert expected behavior of PageVectorSearchEnrichment | PageVectorSearchEnrichment should have correct properties | In scope: PageVectorSearchEnrichment behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | AiSearchReranking_ShouldHaveCorrectProperties | Verifying that ai search reranking should have correct properties | Setup test data and mocks -> Call AiSearchReranking -> Assert expected behavior of AiSearchReranking | AiSearchReranking should have correct properties | In scope: AiSearchReranking behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | AiSearchFiltering_ShouldHaveCorrectProperties | Verifying that ai search filtering should have correct properties | Setup test data and mocks -> Call AiSearchFiltering -> Assert expected behavior of AiSearchFiltering | AiSearchFiltering should have correct properties | In scope: AiSearchFiltering behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | GeminiKeywordEnrichment_ShouldHaveCorrectProperties | Verifying that gemini keyword enrichment should have correct properties | Setup test data and mocks -> Call GeminiKeywordEnrichment -> Assert expected behavior of GeminiKeywordEnrichment | GeminiKeywordEnrichment should have correct properties | In scope: GeminiKeywordEnrichment behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | SelfServeAds_ShouldHaveCorrectProperties | Verifying that self serve ads should have correct properties | Setup test data and mocks -> Call SelfServeAds -> Assert expected behavior of SelfServeAds | SelfServeAds should have correct properties | In scope: SelfServeAds behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | PresortV3_ShouldHaveCorrectProperties | Verifying that presort v3 should have correct properties | Setup test data and mocks -> Call PresortV3 -> Assert expected behavior of PresortV3 | PresortV3 should have correct properties | In scope: PresortV3 behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | BatchVectorSearchEnrichment_ShouldHaveCorrectProperties | Verifying that batch vector search enrichment should have correct properties | Setup test data and mocks -> Call BatchVectorSearchEnrichment -> Assert expected behavior of BatchVectorSearchEnrichment | BatchVectorSearchEnrichment should have correct properties | In scope: BatchVectorSearchEnrichment behavior, should have correct properties scenario. Out of scope: other scenarios and methods not under test. |

# BotDetection

## BotDetectionAdapterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | IsBot_WithNullUserAgent_ShouldReturnFalse | Verifying that is bot with null user agent returns false | Setup with null input -> Call IsBot -> Assert returns false | IsBot with null user agent returns false | In scope: null input handling for IsBot. Out of scope: valid input scenarios. |
| 2 | | IsBot_WithEmptyUserAgent_ShouldReturnFalse | Verifying that is bot with empty user agent returns false | Setup with empty input -> Call IsBot -> Assert returns false | IsBot with empty user agent returns false | In scope: empty input handling for IsBot. Out of scope: non-empty input scenarios. |
| 3 | | IsBot_WithGooglebot_ShouldReturnTrue | Verifying that is bot with googlebot returns true | Setup with googlebot -> Call IsBot -> Assert returns true | IsBot with googlebot returns true | In scope: IsBot behavior, with googlebot scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | IsBot_WithBingbot_ShouldReturnTrue | Verifying that is bot with bingbot returns true | Setup with bingbot -> Call IsBot -> Assert returns true | IsBot with bingbot returns true | In scope: IsBot behavior, with bingbot scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | IsBot_WithSlurp_ShouldReturnTrue | Verifying that is bot with slurp returns true | Setup with slurp -> Call IsBot -> Assert returns true | IsBot with slurp returns true | In scope: IsBot behavior, with slurp scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | IsBot_WithDuckDuckBot_ShouldReturnTrue | Verifying that is bot with duck duck bot returns true | Setup with duck duck bot -> Call IsBot -> Assert returns true | IsBot with duck duck bot returns true | In scope: IsBot behavior, with duck duck bot scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | IsBot_WithBaidu_ShouldReturnTrue | Verifying that is bot with baidu returns true | Setup with baidu -> Call IsBot -> Assert returns true | IsBot with baidu returns true | In scope: IsBot behavior, with baidu scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | IsBot_WithYandex_ShouldReturnTrue | Verifying that is bot with yandex returns true | Setup with yandex -> Call IsBot -> Assert returns true | IsBot with yandex returns true | In scope: IsBot behavior, with yandex scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | IsBot_WithSogou_ShouldReturnTrue | Verifying that is bot with sogou returns true | Setup with sogou -> Call IsBot -> Assert returns true | IsBot with sogou returns true | In scope: IsBot behavior, with sogou scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | IsBot_WithFacebookbot_ShouldReturnTrue | Verifying that is bot with facebookbot returns true | Setup with facebookbot -> Call IsBot -> Assert returns true | IsBot with facebookbot returns true | In scope: IsBot behavior, with facebookbot scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | IsBot_WithTwitterbot_ShouldReturnTrue | Verifying that is bot with twitterbot returns true | Setup with twitterbot -> Call IsBot -> Assert returns true | IsBot with twitterbot returns true | In scope: IsBot behavior, with twitterbot scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | IsBot_WithLinkedInBot_ShouldReturnTrue | Verifying that is bot with linked in bot returns true | Setup with linked in bot -> Call IsBot -> Assert returns true | IsBot with linked in bot returns true | In scope: IsBot behavior, with linked in bot scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | IsBot_WithWhatsApp_ShouldReturnTrue | Verifying that is bot with whats app returns true | Setup with whats app -> Call IsBot -> Assert returns true | IsBot with whats app returns true | In scope: IsBot behavior, with whats app scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | IsBot_WithTelegramBot_ShouldReturnTrue | Verifying that is bot with telegram bot returns true | Setup with telegram bot -> Call IsBot -> Assert returns true | IsBot with telegram bot returns true | In scope: IsBot behavior, with telegram bot scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | IsBot_WithSlackbot_ShouldReturnTrue | Verifying that is bot with slackbot returns true | Setup with slackbot -> Call IsBot -> Assert returns true | IsBot with slackbot returns true | In scope: IsBot behavior, with slackbot scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | IsBot_WithDiscordBot_ShouldReturnTrue | Verifying that is bot with discord bot returns true | Setup with discord bot -> Call IsBot -> Assert returns true | IsBot with discord bot returns true | In scope: IsBot behavior, with discord bot scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | IsBot_WithApplebot_ShouldReturnTrue | Verifying that is bot with applebot returns true | Setup with applebot -> Call IsBot -> Assert returns true | IsBot with applebot returns true | In scope: IsBot behavior, with applebot scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | IsBot_WithAhrefsBot_ShouldReturnTrue | Verifying that is bot with ahrefs bot returns true | Setup with ahrefs bot -> Call IsBot -> Assert returns true | IsBot with ahrefs bot returns true | In scope: IsBot behavior, with ahrefs bot scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | IsBot_WithSemrushBot_ShouldReturnTrue | Verifying that is bot with semrush bot returns true | Setup with semrush bot -> Call IsBot -> Assert returns true | IsBot with semrush bot returns true | In scope: IsBot behavior, with semrush bot scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | IsBot_WithMJ12bot_ShouldReturnTrue | Verifying that is bot with m j12bot returns true | Setup with m j12bot -> Call IsBot -> Assert returns true | IsBot with m j12bot returns true | In scope: IsBot behavior, with m j12bot scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | IsBot_WithDotBot_ShouldReturnTrue | Verifying that is bot with dot bot returns true | Setup with dot bot -> Call IsBot -> Assert returns true | IsBot with dot bot returns true | In scope: IsBot behavior, with dot bot scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | IsBot_WithPetalBot_ShouldReturnTrue | Verifying that is bot with petal bot returns true | Setup with petal bot -> Call IsBot -> Assert returns true | IsBot with petal bot returns true | In scope: IsBot behavior, with petal bot scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | IsBot_WithBytespider_ShouldReturnTrue | Verifying that is bot with bytespider returns true | Setup with bytespider -> Call IsBot -> Assert returns true | IsBot with bytespider returns true | In scope: IsBot behavior, with bytespider scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | IsBot_WithGPTBot_ShouldReturnTrue | Verifying that is bot with g p t bot returns true | Setup with g p t bot -> Call IsBot -> Assert returns true | IsBot with g p t bot returns true | In scope: IsBot behavior, with g p t bot scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | IsBot_WithClaudeBot_ShouldReturnTrue | Verifying that is bot with claude bot returns true | Setup with claude bot -> Call IsBot -> Assert returns true | IsBot with claude bot returns true | In scope: IsBot behavior, with claude bot scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | IsBot_WithCCBot_ShouldReturnTrue | Verifying that is bot with c c bot returns true | Setup with c c bot -> Call IsBot -> Assert returns true | IsBot with c c bot returns true | In scope: IsBot behavior, with c c bot scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | IsBot_WithDataForSeoBot_ShouldReturnTrue | Verifying that is bot with data for seo bot returns true | Setup with data for seo bot -> Call IsBot -> Assert returns true | IsBot with data for seo bot returns true | In scope: IsBot behavior, with data for seo bot scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | IsBot_WithChromeUserAgent_ShouldReturnFalse | Verifying that is bot with chrome user agent returns false | Setup with chrome user agent -> Call IsBot -> Assert returns false | IsBot with chrome user agent returns false | In scope: IsBot behavior, with chrome user agent scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | IsBot_WithFirefoxUserAgent_ShouldReturnFalse | Verifying that is bot with firefox user agent returns false | Setup with firefox user agent -> Call IsBot -> Assert returns false | IsBot with firefox user agent returns false | In scope: IsBot behavior, with firefox user agent scenario. Out of scope: other scenarios and methods not under test. |
| 30 | | IsBot_WithSafariUserAgent_ShouldReturnFalse | Verifying that is bot with safari user agent returns false | Setup with safari user agent -> Call IsBot -> Assert returns false | IsBot with safari user agent returns false | In scope: IsBot behavior, with safari user agent scenario. Out of scope: other scenarios and methods not under test. |
| 31 | | IsBot_WithEdgeUserAgent_ShouldReturnFalse | Verifying that is bot with edge user agent returns false | Setup with edge user agent -> Call IsBot -> Assert returns false | IsBot with edge user agent returns false | In scope: IsBot behavior, with edge user agent scenario. Out of scope: other scenarios and methods not under test. |
| 32 | | IsBot_WithZocdocApp_ShouldReturnFalse | Verifying that is bot with zocdoc app returns false | Setup with zocdoc app -> Call IsBot -> Assert returns false | IsBot with zocdoc app returns false | In scope: IsBot behavior, with zocdoc app scenario. Out of scope: other scenarios and methods not under test. |
| 33 | | IsBot_WithMobileApp_ShouldReturnFalse | Verifying that is bot with mobile app returns false | Setup with mobile app -> Call IsBot -> Assert returns false | IsBot with mobile app returns false | In scope: IsBot behavior, with mobile app scenario. Out of scope: other scenarios and methods not under test. |
| 34 | | IsBot_WithCaseInsensitiveGooglebot_ShouldReturnTrue | Verifying that is bot with case insensitive googlebot returns true | Setup with case insensitive googlebot -> Call IsBot -> Assert returns true | IsBot with case insensitive googlebot returns true | In scope: IsBot behavior, with case insensitive googlebot scenario. Out of scope: other scenarios and methods not under test. |
| 35 | | IsBot_WithCaseInsensitiveBingbot_ShouldReturnTrue | Verifying that is bot with case insensitive bingbot returns true | Setup with case insensitive bingbot -> Call IsBot -> Assert returns true | IsBot with case insensitive bingbot returns true | In scope: IsBot behavior, with case insensitive bingbot scenario. Out of scope: other scenarios and methods not under test. |
| 36 | | IsBot_WithBotSubstring_ShouldDetectCorrectly | Verifying that is bot with bot substring detect correctly | Setup with bot substring -> Call IsBot -> Assert detect correctly | IsBot with bot substring detect correctly | In scope: IsBot behavior, with bot substring scenario. Out of scope: other scenarios and methods not under test. |
| 37 | | IsBot_WithCrawlerSubstring_ShouldReturnTrue | Verifying that is bot with crawler substring returns true | Setup with crawler substring -> Call IsBot -> Assert returns true | IsBot with crawler substring returns true | In scope: IsBot behavior, with crawler substring scenario. Out of scope: other scenarios and methods not under test. |
| 38 | | IsBot_WithSpiderSubstring_ShouldReturnTrue | Verifying that is bot with spider substring returns true | Setup with spider substring -> Call IsBot -> Assert returns true | IsBot with spider substring returns true | In scope: IsBot behavior, with spider substring scenario. Out of scope: other scenarios and methods not under test. |
| 39 | | IsBot_WithFetcherSubstring_ShouldReturnTrue | Verifying that is bot with fetcher substring returns true | Setup with fetcher substring -> Call IsBot -> Assert returns true | IsBot with fetcher substring returns true | In scope: IsBot behavior, with fetcher substring scenario. Out of scope: other scenarios and methods not under test. |
| 40 | | IsBot_WithScraperSubstring_ShouldReturnTrue | Verifying that is bot with scraper substring returns true | Setup with scraper substring -> Call IsBot -> Assert returns true | IsBot with scraper substring returns true | In scope: IsBot behavior, with scraper substring scenario. Out of scope: other scenarios and methods not under test. |
| 41 | | IsBot_WithCurlUserAgent_ShouldReturnTrue | Verifying that is bot with curl user agent returns true | Setup with curl user agent -> Call IsBot -> Assert returns true | IsBot with curl user agent returns true | In scope: IsBot behavior, with curl user agent scenario. Out of scope: other scenarios and methods not under test. |

# Gemini

## RetryingGeminiClientTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GenerateContent_WhenFirstCallSucceeds_ShouldReturnResponse | Verifying that generate content when first call succeeds returns response | Setup when first call succeeds -> Call GenerateContent -> Assert return response | GenerateContent when first call succeeds returns response | In scope: GenerateContent behavior, when first call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GenerateContent_WhenFirstCallFails_ShouldRetry | Verifying that generate content when first call fails retry | Setup mock to throw exception -> Call GenerateContent -> Assert retry | GenerateContent when first call fails retry | In scope: error handling in GenerateContent. Out of scope: successful execution paths. |
| 3 | | GenerateContent_WhenAllRetriesFail_ShouldThrow | Verifying that generate content when all retries fail throw | Setup mock to throw exception -> Call GenerateContent -> Assert exception is thrown | GenerateContent when all retries fail throw | In scope: error handling in GenerateContent. Out of scope: successful execution paths. |
| 4 | | GenerateContent_ShouldRetryUpToMaxAttempts | Verifying that generate content should retry up to max attempts | Setup test data and mocks -> Call GenerateContent -> Assert expected behavior of GenerateContent | GenerateContent should retry up to max attempts | In scope: GenerateContent behavior, should retry up to max attempts scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GenerateContent_WhenSecondCallSucceeds_ShouldReturnResponse | Verifying that generate content when second call succeeds returns response | Setup when second call succeeds -> Call GenerateContent -> Assert return response | GenerateContent when second call succeeds returns response | In scope: GenerateContent behavior, when second call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GenerateContent_ShouldPassRequestThrough | Verifying that generate content should pass request through | Setup test data and mocks -> Call GenerateContent -> Assert expected behavior of GenerateContent | GenerateContent should pass request through | In scope: GenerateContent behavior, should pass request through scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GenerateContent_WhenCancelled_ShouldThrowOperationCancelledException | Verifying that generate content when cancelled throw operation cancelled exception | Setup when cancelled -> Call GenerateContent -> Assert exception is thrown | GenerateContent when cancelled throw operation cancelled exception | In scope: GenerateContent behavior, when cancelled scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GenerateContent_ShouldUseExponentialBackoff | Verifying that generate content should use exponential backoff | Setup test data and mocks -> Call GenerateContent -> Assert expected behavior of GenerateContent | GenerateContent should use exponential backoff | In scope: GenerateContent behavior, should use exponential backoff scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GenerateContent_WhenNullResponse_ShouldRetry | Verifying that generate content when null response retry | Setup with null input -> Call GenerateContent -> Assert retry | GenerateContent when null response retry | In scope: null input handling for GenerateContent. Out of scope: valid input scenarios. |

# Json

## ComparatorIgnoreAttributeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | CompareJson_WithIdenticalObjects_ShouldBeEqual | Verifying that compare json with identical objects is equal | Setup with identical objects -> Call CompareJson -> Assert be equal | CompareJson with identical objects is equal | In scope: CompareJson behavior, with identical objects scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | CompareJson_WithDifferentValues_ShouldNotBeEqual | Verifying that compare json with different values does not be equal | Setup with different values -> Call CompareJson -> Assert not be equal | CompareJson with different values does not be equal | In scope: CompareJson behavior, with different values scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | CompareJson_WithIgnoredProperty_ShouldBeEqual | Verifying that compare json with ignored property is equal | Setup with ignored property -> Call CompareJson -> Assert be equal | CompareJson with ignored property is equal | In scope: CompareJson behavior, with ignored property scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | CompareJson_WithMultipleIgnoredProperties_ShouldBeEqual | Verifying that compare json with multiple ignored properties is equal | Setup with multiple ignored properties -> Call CompareJson -> Assert be equal | CompareJson with multiple ignored properties is equal | In scope: CompareJson behavior, with multiple ignored properties scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | CompareJson_WithNonIgnoredDifference_ShouldNotBeEqual | Verifying that compare json with non ignored difference does not be equal | Setup with non ignored difference -> Call CompareJson -> Assert not be equal | CompareJson with non ignored difference does not be equal | In scope: CompareJson behavior, with non ignored difference scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | CompareJson_WithNestedObjects_ShouldHandleIgnoredProperties | Verifying that compare json with nested objects handle ignored properties | Setup with nested objects -> Call CompareJson -> Assert handle ignored properties | CompareJson with nested objects handle ignored properties | In scope: CompareJson behavior, with nested objects scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | CompareJson_WithArrayProperties_ShouldBeEqual | Verifying that compare json with array properties is equal | Setup with array properties -> Call CompareJson -> Assert be equal | CompareJson with array properties is equal | In scope: CompareJson behavior, with array properties scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | CompareJson_WithNullIgnoredProperty_ShouldBeEqual | Verifying that compare json with null ignored property is equal | Setup with null input -> Call CompareJson -> Assert be equal | CompareJson with null ignored property is equal | In scope: null input handling for CompareJson. Out of scope: valid input scenarios. |
| 9 | | CompareJson_WithMixedIgnoredAndNonIgnored_ShouldCheckNonIgnored | Verifying that compare json with mixed ignored and non ignored check non ignored | Setup with mixed ignored and non ignored -> Call CompareJson -> Assert check non ignored | CompareJson with mixed ignored and non ignored check non ignored | In scope: CompareJson behavior, with mixed ignored and non ignored scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | CompareJson_WithBothHavingIgnoredDifferences_ShouldBeEqual | Verifying that compare json with both having ignored differences is equal | Setup with both having ignored differences -> Call CompareJson -> Assert be equal | CompareJson with both having ignored differences is equal | In scope: CompareJson behavior, with both having ignored differences scenario. Out of scope: other scenarios and methods not under test. |

## DynamicFilterConvertersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Serialize_SingleFieldSingleValue_ShouldWriteSimpleFilter | Verifying that serialize single field single value write simple filter | Setup test data and mocks -> Call Serialize -> Assert write simple filter | Serialize single field single value write simple filter | In scope: Serialize behavior, single field single value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Serialize_SingleFieldMultipleValues_ShouldWriteArrayFilter | Verifying that serialize single field multiple values write array filter | Setup test data and mocks -> Call Serialize -> Assert write array filter | Serialize single field multiple values write array filter | In scope: Serialize behavior, single field multiple values scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Serialize_MultipleFields_ShouldWriteMultipleFilters | Verifying that serialize multiple fields write multiple filters | Setup test data and mocks -> Call Serialize -> Assert write multiple filters | Serialize multiple fields write multiple filters | In scope: Serialize behavior, multiple fields scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Deserialize_SimpleFilter_ShouldParseCorrectly | Verifying that deserialize simple filter parse correctly | Setup test data and mocks -> Call Deserialize -> Assert parse correctly | Deserialize simple filter parse correctly | In scope: Deserialize behavior, simple filter scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Deserialize_ArrayFilter_ShouldParseMultipleValues | Verifying that deserialize array filter parse multiple values | Setup test data and mocks -> Call Deserialize -> Assert parse multiple values | Deserialize array filter parse multiple values | In scope: Deserialize behavior, array filter scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Deserialize_MultipleFilters_ShouldParseAll | Verifying that deserialize multiple filters parse all | Setup test data and mocks -> Call Deserialize -> Assert parse all | Deserialize multiple filters parse all | In scope: Deserialize behavior, multiple filters scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | RoundTrip_ShouldPreserveData | Verifying that round trip should preserve data | Setup test data and mocks -> Call RoundTrip -> Assert expected behavior of RoundTrip | RoundTrip should preserve data | In scope: RoundTrip behavior, should preserve data scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Deserialize_EmptyObject_ShouldReturnEmptyList | Verifying that deserialize empty object returns empty list | Setup with empty input -> Call Deserialize -> Assert returns empty collection | Deserialize empty object returns empty list | In scope: empty input handling for Deserialize. Out of scope: non-empty input scenarios. |
| 9 | | Serialize_EmptyList_ShouldWriteEmptyObject | Verifying that serialize empty list write empty object | Setup with empty input -> Call Serialize -> Assert write empty object | Serialize empty list write empty object | In scope: empty input handling for Serialize. Out of scope: non-empty input scenarios. |
| 10 | | Deserialize_NullValue_ShouldHandleGracefully | Verifying that deserialize null value handle gracefully | Setup with null input -> Call Deserialize -> Assert handle gracefully | Deserialize null value handle gracefully | In scope: null input handling for Deserialize. Out of scope: valid input scenarios. |
| 11 | | Deserialize_IntegerValue_ShouldConvertToString | Verifying that deserialize integer value convert to string | Setup test data and mocks -> Call Deserialize -> Assert convert to string | Deserialize integer value convert to string | In scope: Deserialize behavior, integer value scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Deserialize_BooleanValue_ShouldConvertToString | Verifying that deserialize boolean value convert to string | Setup test data and mocks -> Call Deserialize -> Assert convert to string | Deserialize boolean value convert to string | In scope: Deserialize behavior, boolean value scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Deserialize_MixedArray_ShouldConvertAllToStrings | Verifying that deserialize mixed array convert all to strings | Setup test data and mocks -> Call Deserialize -> Assert convert all to strings | Deserialize mixed array convert all to strings | In scope: Deserialize behavior, mixed array scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Serialize_WithSpecialCharacters_ShouldEscapeCorrectly | Verifying that serialize with special characters escape correctly | Setup with special characters -> Call Serialize -> Assert escape correctly | Serialize with special characters escape correctly | In scope: Serialize behavior, with special characters scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Deserialize_NestedObject_ShouldThrow | Verifying that deserialize nested object throw | Setup test data and mocks -> Call Deserialize -> Assert exception is thrown | Deserialize nested object throw | In scope: Deserialize behavior, nested object scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | RoundTrip_WithMultipleFieldsAndValues_ShouldPreserve | Verifying that round trip with multiple fields and values preserve | Setup with multiple fields and values -> Call RoundTrip -> Assert preserve | RoundTrip with multiple fields and values preserve | In scope: RoundTrip behavior, with multiple fields and values scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Deserialize_EmptyArray_ShouldReturnEmptyValues | Verifying that deserialize empty array returns empty values | Setup with empty input -> Call Deserialize -> Assert returns empty collection | Deserialize empty array returns empty values | In scope: empty input handling for Deserialize. Out of scope: non-empty input scenarios. |
| 18 | | Serialize_NullValues_ShouldSkip | Verifying that serialize null values skip | Setup with null input -> Call Serialize -> Assert skip | Serialize null values skip | In scope: null input handling for Serialize. Out of scope: valid input scenarios. |
| 19 | | Deserialize_WithWhitespace_ShouldTrimValues | Verifying that deserialize with whitespace trim values | Setup with whitespace -> Call Deserialize -> Assert trim values | Deserialize with whitespace trim values | In scope: Deserialize behavior, with whitespace scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Serialize_DuplicateFieldNames_ShouldMergeValues | Verifying that serialize duplicate field names merge values | Setup test data and mocks -> Call Serialize -> Assert merge values | Serialize duplicate field names merge values | In scope: Serialize behavior, duplicate field names scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | RoundTrip_WithEmptyStringValues_ShouldPreserve | Verifying that round trip with empty string values preserve | Setup with empty input -> Call RoundTrip -> Assert preserve | RoundTrip with empty string values preserve | In scope: empty input handling for RoundTrip. Out of scope: non-empty input scenarios. |
| 22 | | Deserialize_LargeArray_ShouldHandleEfficiently | Verifying that deserialize large array handle efficiently | Setup test data and mocks -> Call Deserialize -> Assert handle efficiently | Deserialize large array handle efficiently | In scope: Deserialize behavior, large array scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | Serialize_WithEncodedCharacters_ShouldPreserve | Verifying that serialize with encoded characters preserve | Setup with encoded characters -> Call Serialize -> Assert preserve | Serialize with encoded characters preserve | In scope: Serialize behavior, with encoded characters scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | Deserialize_WithNumericFieldNames_ShouldParse | Verifying that deserialize with numeric field names parse | Setup with numeric field names -> Call Deserialize -> Assert parse | Deserialize with numeric field names parse | In scope: Deserialize behavior, with numeric field names scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | RoundTrip_WithSingleValuePerField_ShouldPreserve | Verifying that round trip with single value per field preserve | Setup with single value per field -> Call RoundTrip -> Assert preserve | RoundTrip with single value per field preserve | In scope: RoundTrip behavior, with single value per field scenario. Out of scope: other scenarios and methods not under test. |

## EnumMemberJsonConverterFactoryTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Serialize_ShouldUseEnumMemberValue | Verifying that serialize should use enum member value | Setup test data and mocks -> Call Serialize -> Assert expected behavior of Serialize | Serialize should use enum member value | In scope: Serialize behavior, should use enum member value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Deserialize_ShouldMapEnumMemberValueBackToEnum | Verifying that deserialize should map enum member value back to enum | Setup test data and mocks -> Call Deserialize -> Assert expected behavior of Deserialize | Deserialize should map enum member value back to enum | In scope: Deserialize behavior, should map enum member value back to enum scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Serialize_WithoutEnumMember_ShouldUseName | Verifying that serialize with out enum member use name | Setup with out enum member -> Call Serialize -> Assert use name | Serialize with out enum member use name | In scope: Serialize behavior, with out enum member scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Deserialize_WithoutEnumMember_ShouldMapByName | Verifying that deserialize with out enum member map by name | Setup with out enum member -> Call Deserialize -> Assert map by name | Deserialize with out enum member map by name | In scope: Deserialize behavior, with out enum member scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Serialize_MultipleValues_ShouldMapCorrectly | Verifying that serialize multiple values map correctly | Setup test data and mocks -> Call Serialize -> Assert map correctly | Serialize multiple values map correctly | In scope: Serialize behavior, multiple values scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Deserialize_MultipleValues_ShouldMapCorrectly | Verifying that deserialize multiple values map correctly | Setup test data and mocks -> Call Deserialize -> Assert map correctly | Deserialize multiple values map correctly | In scope: Deserialize behavior, multiple values scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Deserialize_CaseInsensitive_ShouldMapCorrectly | Verifying that deserialize case insensitive map correctly | Setup test data and mocks -> Call Deserialize -> Assert map correctly | Deserialize case insensitive map correctly | In scope: Deserialize behavior, case insensitive scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | RoundTrip_ShouldPreserveValues | Verifying that round trip should preserve values | Setup test data and mocks -> Call RoundTrip -> Assert expected behavior of RoundTrip | RoundTrip should preserve values | In scope: RoundTrip behavior, should preserve values scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Serialize_NullableEnum_WithValue_ShouldSerialize | Verifying that serialize nullable enum with value_ should serialize | Setup with null input -> Call Serialize -> Assert with value_ serialize | Serialize nullable enum with value_ should serialize | In scope: null input handling for Serialize. Out of scope: valid input scenarios. |
| 10 | | Serialize_NullableEnum_WithNull_ShouldWriteNull | Verifying that serialize nullable enum with null_ should write null | Setup with null input -> Call Serialize -> Assert with null_ write null | Serialize nullable enum with null_ should write null | In scope: null input handling for Serialize. Out of scope: valid input scenarios. |
| 11 | | Deserialize_NullableEnum_WithValue_ShouldDeserialize | Verifying that deserialize nullable enum with value_ should deserialize | Setup with null input -> Call Deserialize -> Assert with value_ deserialize | Deserialize nullable enum with value_ should deserialize | In scope: null input handling for Deserialize. Out of scope: valid input scenarios. |
| 12 | | Deserialize_NullableEnum_WithNull_ShouldReturnNull | Verifying that deserialize nullable enum with null_ should return null | Setup with null input -> Call Deserialize -> Assert returns null | Deserialize nullable enum with null_ should return null | In scope: null input handling for Deserialize. Out of scope: valid input scenarios. |
| 13 | | Serialize_Array_ShouldSerializeAllValues | Verifying that serialize array serialize all values | Setup test data and mocks -> Call Serialize -> Assert serialize all values | Serialize array serialize all values | In scope: Serialize behavior, array scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Deserialize_Array_ShouldDeserializeAllValues | Verifying that deserialize array deserialize all values | Setup test data and mocks -> Call Deserialize -> Assert deserialize all values | Deserialize array deserialize all values | In scope: Deserialize behavior, array scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | CanConvert_WithEnumType_ShouldReturnTrue | Verifying that can convert with enum type returns true | Setup with enum type -> Call CanConvert -> Assert returns true | CanConvert with enum type returns true | In scope: CanConvert behavior, with enum type scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | CanConvert_WithNonEnumType_ShouldReturnFalse | Verifying that can convert with non enum type returns false | Setup with non enum type -> Call CanConvert -> Assert returns false | CanConvert with non enum type returns false | In scope: CanConvert behavior, with non enum type scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Deserialize_UnknownValue_ShouldThrow | Verifying that deserialize unknown value throw | Setup test data and mocks -> Call Deserialize -> Assert exception is thrown | Deserialize unknown value throw | In scope: Deserialize behavior, unknown value scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Serialize_FlagsEnum_ShouldHandleCorrectly | Verifying that serialize flags enum handle correctly | Setup test data and mocks -> Call Serialize -> Assert handle correctly | Serialize flags enum handle correctly | In scope: Serialize behavior, flags enum scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | RoundTrip_WithDictionary_ShouldPreserveKeys | Verifying that round trip with dictionary preserve keys | Setup with dictionary -> Call RoundTrip -> Assert preserve keys | RoundTrip with dictionary preserve keys | In scope: RoundTrip behavior, with dictionary scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Serialize_WithJsonPropertyName_ShouldUseEnumMemberValue | Verifying that serialize with json property name use enum member value | Setup with json property name -> Call Serialize -> Assert use enum member value | Serialize with json property name use enum member value | In scope: Serialize behavior, with json property name scenario. Out of scope: other scenarios and methods not under test. |

# Metrics

## MetricRecorderTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Increment_ShouldCallStatsdIncrement | Verifying that increment should call statsd increment | Setup test data and mocks -> Call Increment -> Assert expected behavior of Increment | Increment should call statsd increment | In scope: Increment behavior, should call statsd increment scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Timer_ShouldCallStatsdTimer | Verifying that timer should call statsd timer | Setup test data and mocks -> Call Timer -> Assert expected behavior of Timer | Timer should call statsd timer | In scope: Timer behavior, should call statsd timer scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Gauge_ShouldCallStatsdGauge | Verifying that gauge should call statsd gauge | Setup test data and mocks -> Call Gauge -> Assert expected behavior of Gauge | Gauge should call statsd gauge | In scope: Gauge behavior, should call statsd gauge scenario. Out of scope: other scenarios and methods not under test. |

# ModelBinding

## EnumMemberTypeConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ConvertFrom_WithEnumMemberValue_ShouldReturnEnum | Verifying that convert from with enum member value returns enum | Setup with enum member value -> Call ConvertFrom -> Assert return enum | ConvertFrom with enum member value returns enum | In scope: ConvertFrom behavior, with enum member value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ConvertFrom_WithEnumName_ShouldReturnEnum | Verifying that convert from with enum name returns enum | Setup with enum name -> Call ConvertFrom -> Assert return enum | ConvertFrom with enum name returns enum | In scope: ConvertFrom behavior, with enum name scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ConvertFrom_CaseInsensitive_ShouldReturnEnum | Verifying that convert from case insensitive returns enum | Setup test data and mocks -> Call ConvertFrom -> Assert return enum | ConvertFrom case insensitive returns enum | In scope: ConvertFrom behavior, case insensitive scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ConvertFrom_WithInvalidString_ShouldThrow | Verifying that convert from with invalid string throw | Setup with invalid string -> Call ConvertFrom -> Assert exception is thrown | ConvertFrom with invalid string throw | In scope: ConvertFrom behavior, with invalid string scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ConvertFrom_WithNull_ShouldThrow | Verifying that convert from with null throw | Setup with null input -> Call ConvertFrom -> Assert exception is thrown | ConvertFrom with null throw | In scope: null input handling for ConvertFrom. Out of scope: valid input scenarios. |
| 6 | | ConvertTo_WithEnum_ShouldReturnEnumMemberValue | Verifying that convert to with enum returns enum member value | Setup with enum -> Call ConvertTo -> Assert return enum member value | ConvertTo with enum returns enum member value | In scope: ConvertTo behavior, with enum scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ConvertTo_WithEnumWithoutAttribute_ShouldReturnName | Verifying that convert to with enum without attribute returns name | Setup with enum without attribute -> Call ConvertTo -> Assert return name | ConvertTo with enum without attribute returns name | In scope: ConvertTo behavior, with enum without attribute scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | CanConvertFrom_WithString_ShouldReturnTrue | Verifying that can convert from with string returns true | Setup with string -> Call CanConvertFrom -> Assert returns true | CanConvertFrom with string returns true | In scope: CanConvertFrom behavior, with string scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | CanConvertFrom_WithInt_ShouldReturnFalse | Verifying that can convert from with int returns false | Setup with int -> Call CanConvertFrom -> Assert returns false | CanConvertFrom with int returns false | In scope: CanConvertFrom behavior, with int scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | CanConvertTo_WithString_ShouldReturnTrue | Verifying that can convert to with string returns true | Setup with string -> Call CanConvertTo -> Assert returns true | CanConvertTo with string returns true | In scope: CanConvertTo behavior, with string scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | CanConvertTo_WithInt_ShouldReturnFalse | Verifying that can convert to with int returns false | Setup with int -> Call CanConvertTo -> Assert returns false | CanConvertTo with int returns false | In scope: CanConvertTo behavior, with int scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | ConvertFrom_WithMultipleEnumValues_ShouldMapCorrectly | Verifying that convert from with multiple enum values map correctly | Setup with multiple enum values -> Call ConvertFrom -> Assert map correctly | ConvertFrom with multiple enum values map correctly | In scope: ConvertFrom behavior, with multiple enum values scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | ConvertTo_WithMultipleEnumValues_ShouldMapCorrectly | Verifying that convert to with multiple enum values map correctly | Setup with multiple enum values -> Call ConvertTo -> Assert map correctly | ConvertTo with multiple enum values map correctly | In scope: ConvertTo behavior, with multiple enum values scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | RoundTrip_ShouldPreserveValue | Verifying that round trip should preserve value | Setup test data and mocks -> Call RoundTrip -> Assert expected behavior of RoundTrip | RoundTrip should preserve value | In scope: RoundTrip behavior, should preserve value scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | ConvertFrom_WithWhitespace_ShouldTrim | Verifying that convert from with whitespace trim | Setup with whitespace -> Call ConvertFrom -> Assert trim | ConvertFrom with whitespace trim | In scope: ConvertFrom behavior, with whitespace scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | ConvertFrom_WithEmptyString_ShouldThrow | Verifying that convert from with empty string throw | Setup with empty input -> Call ConvertFrom -> Assert exception is thrown | ConvertFrom with empty string throw | In scope: empty input handling for ConvertFrom. Out of scope: non-empty input scenarios. |
| 17 | | ConvertTo_WithNullDestinationType_ShouldThrow | Verifying that convert to with null destination type throw | Setup with null input -> Call ConvertTo -> Assert exception is thrown | ConvertTo with null destination type throw | In scope: null input handling for ConvertTo. Out of scope: valid input scenarios. |

# Search/Algorithm

## AlgoContainerRankByTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | DefaultRankBy_ShouldReturnBestMatch | Verifying that default rank by should return best match | Setup test data and mocks -> Call DefaultRankBy -> Assert expected behavior of DefaultRankBy | DefaultRankBy should return best match | In scope: DefaultRankBy behavior, should return best match scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | WithDistanceRankBy_ShouldReturnDistance | Verifying that with distance rank by should return distance | Setup test data and mocks -> Call WithDistanceRankBy -> Assert expected behavior of WithDistanceRankBy | WithDistanceRankBy should return distance | In scope: WithDistanceRankBy behavior, should return distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | WithAvailabilityRankBy_ShouldReturnAvailability | Verifying that with availability rank by should return availability | Setup test data and mocks -> Call WithAvailabilityRankBy -> Assert expected behavior of WithAvailabilityRankBy | WithAvailabilityRankBy should return availability | In scope: WithAvailabilityRankBy behavior, should return availability scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | WithCustomRankBy_ShouldReturnCustom | Verifying that with custom rank by should return custom | Setup test data and mocks -> Call WithCustomRankBy -> Assert expected behavior of WithCustomRankBy | WithCustomRankBy should return custom | In scope: WithCustomRankBy behavior, should return custom scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | WithNullRankBy_ShouldReturnDefault | Verifying that with null rank by should return default | Setup test data and mocks -> Call WithNullRankBy -> Assert expected behavior of WithNullRankBy | WithNullRankBy should return default | In scope: WithNullRankBy behavior, should return default scenario. Out of scope: other scenarios and methods not under test. |

## AlgorithmExtensionsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAlgorithmVersion_WithVersionedAlgorithm_ShouldReturnVersion | Verifying that get algorithm version with versioned algorithm returns version | Setup with versioned algorithm -> Call GetAlgorithmVersion -> Assert return version | GetAlgorithmVersion with versioned algorithm returns version | In scope: GetAlgorithmVersion behavior, with versioned algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAlgorithmVersion_WithNullAlgorithm_ShouldReturnNull | Verifying that get algorithm version with null algorithm returns null | Setup with null input -> Call GetAlgorithmVersion -> Assert returns null | GetAlgorithmVersion with null algorithm returns null | In scope: null input handling for GetAlgorithmVersion. Out of scope: valid input scenarios. |
| 3 | | GetAlgorithmVersion_WithUnversionedAlgorithm_ShouldReturnNull | Verifying that get algorithm version with unversioned algorithm returns null | Setup with unversioned algorithm -> Call GetAlgorithmVersion -> Assert returns null | GetAlgorithmVersion with unversioned algorithm returns null | In scope: GetAlgorithmVersion behavior, with unversioned algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAlgorithmDescription_WithDescribedAlgorithm_ShouldReturnDescription | Verifying that get algorithm description with described algorithm returns description | Setup with described algorithm -> Call GetAlgorithmDescription -> Assert return description | GetAlgorithmDescription with described algorithm returns description | In scope: GetAlgorithmDescription behavior, with described algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAlgorithmDescription_WithNullAlgorithm_ShouldReturnNull | Verifying that get algorithm description with null algorithm returns null | Setup with null input -> Call GetAlgorithmDescription -> Assert returns null | GetAlgorithmDescription with null algorithm returns null | In scope: null input handling for GetAlgorithmDescription. Out of scope: valid input scenarios. |
| 6 | | GetAlgorithmDescription_WithUndescribedAlgorithm_ShouldReturnNull | Verifying that get algorithm description with undescribed algorithm returns null | Setup with undescribed algorithm -> Call GetAlgorithmDescription -> Assert returns null | GetAlgorithmDescription with undescribed algorithm returns null | In scope: GetAlgorithmDescription behavior, with undescribed algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAlgorithmName_ShouldReturnTypeName | Verifying that get algorithm name should return type name | Setup test data and mocks -> Call GetAlgorithmName -> Assert expected behavior of GetAlgorithmName | GetAlgorithmName should return type name | In scope: GetAlgorithmName behavior, should return type name scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAlgorithmName_WithNullAlgorithm_ShouldReturnNull | Verifying that get algorithm name with null algorithm returns null | Setup with null input -> Call GetAlgorithmName -> Assert returns null | GetAlgorithmName with null algorithm returns null | In scope: null input handling for GetAlgorithmName. Out of scope: valid input scenarios. |
| 9 | | IsEnabled_WithEnabledAlgorithm_ShouldReturnTrue | Verifying that is enabled with enabled algorithm returns true | Setup with enabled algorithm -> Call IsEnabled -> Assert returns true | IsEnabled with enabled algorithm returns true | In scope: IsEnabled behavior, with enabled algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | IsEnabled_WithDisabledAlgorithm_ShouldReturnFalse | Verifying that is enabled with disabled algorithm returns false | Setup with disabled algorithm -> Call IsEnabled -> Assert returns false | IsEnabled with disabled algorithm returns false | In scope: IsEnabled behavior, with disabled algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | IsEnabled_WithNullAlgorithm_ShouldReturnFalse | Verifying that is enabled with null algorithm returns false | Setup with null input -> Call IsEnabled -> Assert returns false | IsEnabled with null algorithm returns false | In scope: null input handling for IsEnabled. Out of scope: valid input scenarios. |

## AvailabilityRetrieverTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailability_WithValidProvLocs_ShouldReturnAvailability | Verifying that get availability with valid prov locs returns availability | Setup with valid prov locs -> Call GetAvailability -> Assert return availability | GetAvailability with valid prov locs returns availability | In scope: GetAvailability behavior, with valid prov locs scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_WithEmptyProvLocs_ShouldReturnEmpty | Verifying that get availability with empty prov locs returns empty | Setup with empty input -> Call GetAvailability -> Assert returns empty collection | GetAvailability with empty prov locs returns empty | In scope: empty input handling for GetAvailability. Out of scope: non-empty input scenarios. |
| 3 | | GetAvailability_ShouldCallClientWithCorrectParameters | Verifying that get availability should call client with correct parameters | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should call client with correct parameters | In scope: GetAvailability behavior, should call client with correct parameters scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAvailability_ShouldMapProvLocIdsCorrectly | Verifying that get availability should map prov loc ids correctly | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map prov loc ids correctly | In scope: GetAvailability behavior, should map prov loc ids correctly scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAvailability_WhenClientReturnsNull_ShouldReturnEmpty | Verifying that get availability when client returns null returns empty | Setup with null input -> Call GetAvailability -> Assert returns empty collection | GetAvailability when client returns null returns empty | In scope: null input handling for GetAvailability. Out of scope: valid input scenarios. |
| 6 | | GetAvailability_ShouldHandleLargeNumberOfProvLocs | Verifying that get availability should handle large number of prov locs | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle large number of prov locs | In scope: GetAvailability behavior, should handle large number of prov locs scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAvailability_ShouldRespectDateRange | Verifying that get availability should respect date range | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should respect date range | In scope: GetAvailability behavior, should respect date range scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAvailability_ShouldIncludeTimeZone | Verifying that get availability should include time zone | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should include time zone | In scope: GetAvailability behavior, should include time zone scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAvailability_WithMixedResults_ShouldReturnPartial | Verifying that get availability with mixed results returns partial | Setup with mixed results -> Call GetAvailability -> Assert return partial | GetAvailability with mixed results returns partial | In scope: GetAvailability behavior, with mixed results scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAvailability_ShouldLogRequestDetails | Verifying that get availability should log request details | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should log request details | In scope: GetAvailability behavior, should log request details scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAvailability_ShouldEmitLatencyMetrics | Verifying that get availability should emit latency metrics | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should emit latency metrics | In scope: GetAvailability behavior, should emit latency metrics scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetAvailability_WhenClientThrows_ShouldPropagate | Verifying that get availability when client throws propagate | Setup mock to throw exception -> Call GetAvailability -> Assert propagate | GetAvailability when client throws propagate | In scope: error handling in GetAvailability. Out of scope: successful execution paths. |
| 13 | | GetAvailability_ShouldPassInsuranceInfo | Verifying that get availability should pass insurance info | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass insurance info | In scope: GetAvailability behavior, should pass insurance info scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetAvailability_ShouldBatchRequests | Verifying that get availability should batch requests | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should batch requests | In scope: GetAvailability behavior, should batch requests scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetAvailability_WithCancellation_ShouldCancel | Verifying that get availability with cancellation cancel | Setup with cancellation -> Call GetAvailability -> Assert cancel | GetAvailability with cancellation cancel | In scope: GetAvailability behavior, with cancellation scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | GetAvailability_ShouldMapDailySummaries | Verifying that get availability should map daily summaries | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map daily summaries | In scope: GetAvailability behavior, should map daily summaries scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | GetAvailability_ShouldMapHourlySummaries | Verifying that get availability should map hourly summaries | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map hourly summaries | In scope: GetAvailability behavior, should map hourly summaries scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | GetAvailability_ShouldReturnNoAvailabilityReason | Verifying that get availability should return no availability reason | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should return no availability reason | In scope: GetAvailability behavior, should return no availability reason scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | GetAvailability_WithVideoVisitFilter_ShouldPassThrough | Verifying that get availability with video visit filter pass through | Setup with video visit filter -> Call GetAvailability -> Assert pass through | GetAvailability with video visit filter pass through | In scope: GetAvailability behavior, with video visit filter scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | GetAvailability_ShouldHandleNullProvLocIds | Verifying that get availability should handle null prov loc ids | Setup with null input -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle null prov loc ids | In scope: null input handling for GetAvailability. Out of scope: valid input scenarios. |
| 21 | | GetAvailability_ShouldDeduplicateRequests | Verifying that get availability should deduplicate requests | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should deduplicate requests | In scope: GetAvailability behavior, should deduplicate requests scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | GetAvailability_ShouldMapOfficeHours | Verifying that get availability should map office hours | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map office hours | In scope: GetAvailability behavior, should map office hours scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | GetAvailability_ShouldHandlePartialFailures | Verifying that get availability should handle partial failures | Setup mock to throw exception -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle partial failures | In scope: error handling in GetAvailability. Out of scope: successful execution paths. |
| 24 | | GetAvailability_ShouldReturnNextAvailableSlot | Verifying that get availability should return next available slot | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should return next available slot | In scope: GetAvailability behavior, should return next available slot scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | GetAvailability_ShouldHandleTimezoneConversion | Verifying that get availability should handle timezone conversion | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle timezone conversion | In scope: GetAvailability behavior, should handle timezone conversion scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | GetAvailability_ShouldFilterByVisitType | Verifying that get availability should filter by visit type | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should filter by visit type | In scope: GetAvailability behavior, should filter by visit type scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | GetAvailability_ShouldIncludeBookingUrl | Verifying that get availability should include booking url | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should include booking url | In scope: GetAvailability behavior, should include booking url scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | GetAvailability_ShouldMapScheduleInfo | Verifying that get availability should map schedule info | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map schedule info | In scope: GetAvailability behavior, should map schedule info scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | GetAvailability_ShouldHandleExpiredSlots | Verifying that get availability should handle expired slots | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle expired slots | In scope: GetAvailability behavior, should handle expired slots scenario. Out of scope: other scenarios and methods not under test. |
| 30 | | GetAvailability_ShouldHandleDSTTransitions | Verifying that get availability should handle d s t transitions | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle d s t transitions | In scope: GetAvailability behavior, should handle d s t transitions scenario. Out of scope: other scenarios and methods not under test. |
| 31 | | GetAvailability_ShouldRespectMaxDaysAhead | Verifying that get availability should respect max days ahead | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should respect max days ahead | In scope: GetAvailability behavior, should respect max days ahead scenario. Out of scope: other scenarios and methods not under test. |
| 32 | | GetAvailability_ShouldMapProviderLocationPairs | Verifying that get availability should map provider location pairs | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map provider location pairs | In scope: GetAvailability behavior, should map provider location pairs scenario. Out of scope: other scenarios and methods not under test. |
| 33 | | GetAvailability_ShouldHandleSameDayAvailability | Verifying that get availability should handle same day availability | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle same day availability | In scope: GetAvailability behavior, should handle same day availability scenario. Out of scope: other scenarios and methods not under test. |
| 34 | | GetAvailability_ShouldOrderSlotsByTime | Verifying that get availability should order slots by time | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should order slots by time | In scope: GetAvailability behavior, should order slots by time scenario. Out of scope: other scenarios and methods not under test. |

## ContainerApiVersionTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | V1_ShouldBeCorrectString | Verifying that v1 should be correct string | Setup test data and mocks -> Call V1 -> Assert expected behavior of V1 | V1 should be correct string | In scope: V1 behavior, should be correct string scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | V2_ShouldBeCorrectString | Verifying that v2 should be correct string | Setup test data and mocks -> Call V2 -> Assert expected behavior of V2 | V2 should be correct string | In scope: V2 behavior, should be correct string scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | V3_ShouldBeCorrectString | Verifying that v3 should be correct string | Setup test data and mocks -> Call V3 -> Assert expected behavior of V3 | V3 should be correct string | In scope: V3 behavior, should be correct string scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AllVersions_ShouldBeDistinct | Verifying that all versions should be distinct | Setup test data and mocks -> Call AllVersions -> Assert expected behavior of AllVersions | AllVersions should be distinct | In scope: AllVersions behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## ContainerConstantsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | DefaultPageSize_ShouldBe15 | Verifying that default page size should be15 | Setup test data and mocks -> Call DefaultPageSize -> Assert expected behavior of DefaultPageSize | DefaultPageSize should be15 | In scope: DefaultPageSize behavior, should be15 scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | MaxPageSize_ShouldBe100 | Verifying that max page size should be100 | Setup test data and mocks -> Call MaxPageSize -> Assert expected behavior of MaxPageSize | MaxPageSize should be100 | In scope: MaxPageSize behavior, should be100 scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | DefaultElasticSize_ShouldBe150 | Verifying that default elastic size should be150 | Setup test data and mocks -> Call DefaultElasticSize -> Assert expected behavior of DefaultElasticSize | DefaultElasticSize should be150 | In scope: DefaultElasticSize behavior, should be150 scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | MaxElasticSize_ShouldBe1500 | Verifying that max elastic size should be1500 | Setup test data and mocks -> Call MaxElasticSize -> Assert expected behavior of MaxElasticSize | MaxElasticSize should be1500 | In scope: MaxElasticSize behavior, should be1500 scenario. Out of scope: other scenarios and methods not under test. |

## ScoreFusionRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_ShouldCombineScores | Verifying that rank should combine scores | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should combine scores | In scope: Rank behavior, should combine scores scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithSingleScore_ShouldReturnAsIs | Verifying that rank with single score returns as is | Setup with single score -> Call Rank -> Assert return as is | Rank with single score returns as is | In scope: Rank behavior, with single score scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithNoScores_ShouldReturnDefault | Verifying that rank with no scores returns default | Setup with no scores -> Call Rank -> Assert return default | Rank with no scores returns default | In scope: Rank behavior, with no scores scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_ShouldNormalizeBeforeFusion | Verifying that rank should normalize before fusion | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should normalize before fusion | In scope: Rank behavior, should normalize before fusion scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithEqualWeights_ShouldAverageScores | Verifying that rank with equal weights average scores | Setup with equal weights -> Call Rank -> Assert average scores | Rank with equal weights average scores | In scope: Rank behavior, with equal weights scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithUnequalWeights_ShouldWeightProperly | Verifying that rank with unequal weights weight properly | Setup with unequal weights -> Call Rank -> Assert weight properly | Rank with unequal weights weight properly | In scope: Rank behavior, with unequal weights scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_ShouldHandleNegativeScores | Verifying that rank should handle negative scores | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should handle negative scores | In scope: Rank behavior, should handle negative scores scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_ShouldHandleZeroScores | Verifying that rank should handle zero scores | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should handle zero scores | In scope: Rank behavior, should handle zero scores scenario. Out of scope: other scenarios and methods not under test. |

## SearchAlgorithmTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_ShouldCallContainerWithCorrectParameters | Verifying that execute should call container with correct parameters | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should call container with correct parameters | In scope: Execute behavior, should call container with correct parameters scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_ShouldReturnSearchResponse | Verifying that execute should return search response | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should return search response | In scope: Execute behavior, should return search response scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Execute_ShouldPassSearchParams | Verifying that execute should pass search params | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should pass search params | In scope: Execute behavior, should pass search params scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Execute_ShouldPassHeaders | Verifying that execute should pass headers | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should pass headers | In scope: Execute behavior, should pass headers scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Execute_ShouldCallContainerProcessors | Verifying that execute should call container processors | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should call container processors | In scope: Execute behavior, should call container processors scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Execute_WithCancellation_ShouldCancel | Verifying that execute with cancellation cancel | Setup with cancellation -> Call Execute -> Assert cancel | Execute with cancellation cancel | In scope: Execute behavior, with cancellation scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Name_ShouldReturnAlgorithmName | Verifying that name should return algorithm name | Setup test data and mocks -> Call Name -> Assert expected behavior of Name | Name should return algorithm name | In scope: Name behavior, should return algorithm name scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Version_ShouldReturnAlgorithmVersion | Verifying that version should return algorithm version | Setup test data and mocks -> Call Version -> Assert expected behavior of Version | Version should return algorithm version | In scope: Version behavior, should return algorithm version scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Description_ShouldReturnAlgorithmDescription | Verifying that description should return algorithm description | Setup test data and mocks -> Call Description -> Assert expected behavior of Description | Description should return algorithm description | In scope: Description behavior, should return algorithm description scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | IsEnabled_ShouldReturnTrue | Verifying that is enabled should return true | Setup test data and mocks -> Call IsEnabled -> Assert expected behavior of IsEnabled | IsEnabled should return true | In scope: IsEnabled behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |

## SearchResponseProcessorBaseTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ProcessorType_ShouldReturnCorrectType | Verifying that processor type should return correct type | Setup test data and mocks -> Call ProcessorType -> Assert expected behavior of ProcessorType | ProcessorType should return correct type | In scope: ProcessorType behavior, should return correct type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProcessorName_ShouldReturnCorrectName | Verifying that processor name should return correct name | Setup test data and mocks -> Call ProcessorName -> Assert expected behavior of ProcessorName | ProcessorName should return correct name | In scope: ProcessorName behavior, should return correct name scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_ShouldCallNextUpdate | Verifying that process should call next update | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should call next update | In scope: Process behavior, should call next update scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Process_ShouldReturnResponseUpdate | Verifying that process should return response update | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should return response update | In scope: Process behavior, should return response update scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Process_WithNullInput_ShouldHandleGracefully | Verifying that process with null input handle gracefully | Setup with null input -> Call Process -> Assert handle gracefully | Process with null input handle gracefully | In scope: null input handling for Process. Out of scope: valid input scenarios. |
| 6 | | Validate_ShouldReturnTrue | Verifying that validate should return true | Setup test data and mocks -> Call Validate -> Assert expected behavior of Validate | Validate should return true | In scope: Validate behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |

## SortByTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | BestMatch_ShouldBeCorrectValue | Verifying that best match should be correct value | Setup test data and mocks -> Call BestMatch -> Assert expected behavior of BestMatch | BestMatch should be correct value | In scope: BestMatch behavior, should be correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Distance_ShouldBeCorrectValue | Verifying that distance should be correct value | Setup test data and mocks -> Call Distance -> Assert expected behavior of Distance | Distance should be correct value | In scope: Distance behavior, should be correct value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Availability_ShouldBeCorrectValue | Verifying that availability should be correct value | Setup test data and mocks -> Call Availability -> Assert expected behavior of Availability | Availability should be correct value | In scope: Availability behavior, should be correct value scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AllValues_ShouldBeDistinct | Verifying that all values should be distinct | Setup test data and mocks -> Call AllValues -> Assert expected behavior of AllValues | AllValues should be distinct | In scope: AllValues behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## SpoAlgorithmTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_ShouldCallSpoClient | Verifying that execute should call spo client | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should call spo client | In scope: Execute behavior, should call spo client scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_ShouldReturnSpoResults | Verifying that execute should return spo results | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should return spo results | In scope: Execute behavior, should return spo results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Execute_WithNoResults_ShouldReturnEmpty | Verifying that execute with no results returns empty | Setup with no results -> Call Execute -> Assert returns empty collection | Execute with no results returns empty | In scope: Execute behavior, with no results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Execute_ShouldPassCorrectSearchParams | Verifying that execute should pass correct search params | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should pass correct search params | In scope: Execute behavior, should pass correct search params scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Execute_ShouldIncludeInsuranceInfo | Verifying that execute should include insurance info | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should include insurance info | In scope: Execute behavior, should include insurance info scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Execute_WithCancellation_ShouldCancel | Verifying that execute with cancellation cancel | Setup with cancellation -> Call Execute -> Assert cancel | Execute with cancellation cancel | In scope: Execute behavior, with cancellation scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Execute_WhenSpoClientThrows_ShouldPropagate | Verifying that execute when spo client throws propagate | Setup mock to throw exception -> Call Execute -> Assert propagate | Execute when spo client throws propagate | In scope: error handling in Execute. Out of scope: successful execution paths. |
| 8 | | Execute_ShouldEmitLatencyMetrics | Verifying that execute should emit latency metrics | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should emit latency metrics | In scope: Execute behavior, should emit latency metrics scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Execute_ShouldLogRequestDetails | Verifying that execute should log request details | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should log request details | In scope: Execute behavior, should log request details scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Execute_ShouldMapAdDecisions | Verifying that execute should map ad decisions | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should map ad decisions | In scope: Execute behavior, should map ad decisions scenario. Out of scope: other scenarios and methods not under test. |

## StubSearchResponseProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ProcessorType_ShouldReturnStub | Verifying that processor type should return stub | Setup test data and mocks -> Call ProcessorType -> Assert expected behavior of ProcessorType | ProcessorType should return stub | In scope: ProcessorType behavior, should return stub scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProcessorName_ShouldReturnStubName | Verifying that processor name should return stub name | Setup test data and mocks -> Call ProcessorName -> Assert expected behavior of ProcessorName | ProcessorName should return stub name | In scope: ProcessorName behavior, should return stub name scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_ShouldReturnNoOpUpdate | Verifying that process should return no op update | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should return no op update | In scope: Process behavior, should return no op update scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Validate_ShouldReturnTrue | Verifying that validate should return true | Setup test data and mocks -> Call Validate -> Assert expected behavior of Validate | Validate should return true | In scope: Validate behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Instance_ShouldBeSingleton | Verifying that instance should be singleton | Setup test data and mocks -> Call Instance -> Assert expected behavior of Instance | Instance should be singleton | In scope: Instance behavior, should be singleton scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Process_ShouldNotModifyInput | Verifying that process should not modify input | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should not modify input | In scope: Process behavior, should not modify input scenario. Out of scope: other scenarios and methods not under test. |

## ValidatedSearchAlgorithmTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_WithValidRequest_ShouldCallInnerAlgorithm | Verifying that execute with valid request call inner algorithm | Setup with valid request -> Call Execute -> Assert call inner algorithm | Execute with valid request call inner algorithm | In scope: Execute behavior, with valid request scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_WithInvalidRequest_ShouldReturnValidationError | Verifying that execute with invalid request returns validation error | Setup with invalid request -> Call Execute -> Assert return validation error | Execute with invalid request returns validation error | In scope: Execute behavior, with invalid request scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Validate_ShouldCallValidators | Verifying that validate should call validators | Setup test data and mocks -> Call Validate -> Assert expected behavior of Validate | Validate should call validators | In scope: Validate behavior, should call validators scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Name_ShouldReturnInnerAlgorithmName | Verifying that name should return inner algorithm name | Setup test data and mocks -> Call Name -> Assert expected behavior of Name | Name should return inner algorithm name | In scope: Name behavior, should return inner algorithm name scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Version_ShouldReturnInnerAlgorithmVersion | Verifying that version should return inner algorithm version | Setup test data and mocks -> Call Version -> Assert expected behavior of Version | Version should return inner algorithm version | In scope: Version behavior, should return inner algorithm version scenario. Out of scope: other scenarios and methods not under test. |

# Search/Algorithm/Container

## BasicFilterContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetBasicFilters | Verifying that configure should set basic filters | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set basic filters | In scope: Configure behavior, should set basic filters scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldSetDefaultPageSize | Verifying that configure should set default page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set default page size | In scope: Configure behavior, should set default page size scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldIncludeRequiredFilterers | Verifying that configure should include required filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include required filterers | In scope: Configure behavior, should include required filterers scenario. Out of scope: other scenarios and methods not under test. |

## DefaultEnterpriseContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetEnterpriseDefaults | Verifying that configure should set enterprise defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set enterprise defaults | In scope: Configure behavior, should set enterprise defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeEnterpriseFilterers | Verifying that configure should include enterprise filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include enterprise filterers | In scope: Configure behavior, should include enterprise filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetEnterprisePageSize | Verifying that configure should set enterprise page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set enterprise page size | In scope: Configure behavior, should set enterprise page size scenario. Out of scope: other scenarios and methods not under test. |

## ExternalApiContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetExternalApiDefaults | Verifying that configure should set external api defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set external api defaults | In scope: Configure behavior, should set external api defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeExternalProviderFilterer | Verifying that configure should include external provider filterer | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include external provider filterer | In scope: Configure behavior, should include external provider filterer scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetApiPageSize | Verifying that configure should set api page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set api page size | In scope: Configure behavior, should set api page size scenario. Out of scope: other scenarios and methods not under test. |

## HomePageSimilarDoctorsContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetSimilarDoctorsDefaults | Verifying that configure should set similar doctors defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set similar doctors defaults | In scope: Configure behavior, should set similar doctors defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeSpecialtyFilterer | Verifying that configure should include specialty filterer | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include specialty filterer | In scope: Configure behavior, should include specialty filterer scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetSimilarDoctorsPageSize | Verifying that configure should set similar doctors page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set similar doctors page size | In scope: Configure behavior, should set similar doctors page size scenario. Out of scope: other scenarios and methods not under test. |

## ListingMapleContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetMapleModelDefaults | Verifying that configure should set maple model defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set maple model defaults | In scope: Configure behavior, should set maple model defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeMapleScorer | Verifying that configure should include maple scorer | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include maple scorer | In scope: Configure behavior, should include maple scorer scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetMaplePageSize | Verifying that configure should set maple page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set maple page size | In scope: Configure behavior, should set maple page size scenario. Out of scope: other scenarios and methods not under test. |

## MarketplaceAiSearchContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetAiSearchDefaults | Verifying that configure should set ai search defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set ai search defaults | In scope: Configure behavior, should set ai search defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeVectorSearchEnricher | Verifying that configure should include vector search enricher | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include vector search enricher | In scope: Configure behavior, should include vector search enricher scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetAiSearchPageSize | Verifying that configure should set ai search page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set ai search page size | In scope: Configure behavior, should set ai search page size scenario. Out of scope: other scenarios and methods not under test. |

## MarketplaceSearchPracticeContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetPracticeSearchDefaults | Verifying that configure should set practice search defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set practice search defaults | In scope: Configure behavior, should set practice search defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludePracticeFilterers | Verifying that configure should include practice filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include practice filterers | In scope: Configure behavior, should include practice filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetPracticePageSize | Verifying that configure should set practice page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set practice page size | In scope: Configure behavior, should set practice page size scenario. Out of scope: other scenarios and methods not under test. |

## MarketplaceSemContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetSemDefaults | Verifying that configure should set sem defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set sem defaults | In scope: Configure behavior, should set sem defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeSemFilterers | Verifying that configure should include sem filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include sem filterers | In scope: Configure behavior, should include sem filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetSemPageSize | Verifying that configure should set sem page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set sem page size | In scope: Configure behavior, should set sem page size scenario. Out of scope: other scenarios and methods not under test. |

## PreviewProviderContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetPreviewDefaults | Verifying that configure should set preview defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set preview defaults | In scope: Configure behavior, should set preview defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludePreviewFilterers | Verifying that configure should include preview filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include preview filterers | In scope: Configure behavior, should include preview filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetPreviewPageSize | Verifying that configure should set preview page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set preview page size | In scope: Configure behavior, should set preview page size scenario. Out of scope: other scenarios and methods not under test. |

## SubspecialtySearchPracticeContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetSubspecialtyDefaults | Verifying that configure should set subspecialty defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set subspecialty defaults | In scope: Configure behavior, should set subspecialty defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeSubspecialtyFilterer | Verifying that configure should include subspecialty filterer | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include subspecialty filterer | In scope: Configure behavior, should include subspecialty filterer scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetSubspecialtyPageSize | Verifying that configure should set subspecialty page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set subspecialty page size | In scope: Configure behavior, should set subspecialty page size scenario. Out of scope: other scenarios and methods not under test. |

## YassJrMarketplaceListingAndPreviewContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetListingAndPreviewDefaults | Verifying that configure should set listing and preview defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set listing and preview defaults | In scope: Configure behavior, should set listing and preview defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeListingFilterers | Verifying that configure should include listing filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include listing filterers | In scope: Configure behavior, should include listing filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetListingAndPreviewPageSize | Verifying that configure should set listing and preview page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set listing and preview page size | In scope: Configure behavior, should set listing and preview page size scenario. Out of scope: other scenarios and methods not under test. |

## YassJrMarketplaceListingContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetListingDefaults | Verifying that configure should set listing defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set listing defaults | In scope: Configure behavior, should set listing defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeListingFilterers | Verifying that configure should include listing filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include listing filterers | In scope: Configure behavior, should include listing filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetListingPageSize | Verifying that configure should set listing page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set listing page size | In scope: Configure behavior, should set listing page size scenario. Out of scope: other scenarios and methods not under test. |

## YassJrSimilarDoctorsContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetSimilarDoctorsDefaults | Verifying that configure should set similar doctors defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set similar doctors defaults | In scope: Configure behavior, should set similar doctors defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeSimilarDoctorsFilterers | Verifying that configure should include similar doctors filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include similar doctors filterers | In scope: Configure behavior, should include similar doctors filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetSimilarDoctorsPageSize | Verifying that configure should set similar doctors page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set similar doctors page size | In scope: Configure behavior, should set similar doctors page size scenario. Out of scope: other scenarios and methods not under test. |

## YassJrTopBrowsableDoctorsContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetTopBrowsableDefaults | Verifying that configure should set top browsable defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set top browsable defaults | In scope: Configure behavior, should set top browsable defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeTopBrowsableFilterers | Verifying that configure should include top browsable filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include top browsable filterers | In scope: Configure behavior, should include top browsable filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetTopBrowsablePageSize | Verifying that configure should set top browsable page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set top browsable page size | In scope: Configure behavior, should set top browsable page size scenario. Out of scope: other scenarios and methods not under test. |

## YassJrVaccineContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_ShouldSetVaccineDefaults | Verifying that configure should set vaccine defaults | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set vaccine defaults | In scope: Configure behavior, should set vaccine defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_ShouldIncludeVaccineFilterers | Verifying that configure should include vaccine filterers | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should include vaccine filterers | In scope: Configure behavior, should include vaccine filterers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_ShouldSetVaccinePageSize | Verifying that configure should set vaccine page size | Setup test data and mocks -> Call Configure -> Assert expected behavior of Configure | Configure should set vaccine page size | In scope: Configure behavior, should set vaccine page size scenario. Out of scope: other scenarios and methods not under test. |

# Search/Annotation

## RequiredEsFiltererAttributeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Attribute_ShouldBeApplicableToClass | Verifying that attribute should be applicable to class | Setup test data and mocks -> Call Attribute -> Assert expected behavior of Attribute | Attribute should be applicable to class | In scope: Attribute behavior, should be applicable to class scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Attribute_ShouldStoreFiltererType | Verifying that attribute should store filterer type | Setup test data and mocks -> Call Attribute -> Assert expected behavior of Attribute | Attribute should store filterer type | In scope: Attribute behavior, should store filterer type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Attribute_ShouldAllowMultiple | Verifying that attribute should allow multiple | Setup test data and mocks -> Call Attribute -> Assert expected behavior of Attribute | Attribute should allow multiple | In scope: Attribute behavior, should allow multiple scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Attribute_ShouldBeInheritable | Verifying that attribute should be inheritable | Setup test data and mocks -> Call Attribute -> Assert expected behavior of Attribute | Attribute should be inheritable | In scope: Attribute behavior, should be inheritable scenario. Out of scope: other scenarios and methods not under test. |

# Search/Availability

## AvailabilityClientTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailability_ShouldCallHttpClient | Verifying that get availability should call http client | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should call http client | In scope: GetAvailability behavior, should call http client scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_ShouldDeserializeResponse | Verifying that get availability should deserialize response | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should deserialize response | In scope: GetAvailability behavior, should deserialize response scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAvailability_ShouldPassProvLocIds | Verifying that get availability should pass prov loc ids | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass prov loc ids | In scope: GetAvailability behavior, should pass prov loc ids scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAvailability_ShouldPassDateRange | Verifying that get availability should pass date range | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass date range | In scope: GetAvailability behavior, should pass date range scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAvailability_ShouldPassInsuranceInfo | Verifying that get availability should pass insurance info | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass insurance info | In scope: GetAvailability behavior, should pass insurance info scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAvailability_WhenClientThrows_ShouldThrow | Verifying that get availability when client throws throw | Setup mock to throw exception -> Call GetAvailability -> Assert exception is thrown | GetAvailability when client throws throw | In scope: error handling in GetAvailability. Out of scope: successful execution paths. |
| 7 | | GetAvailability_ShouldUseCorrectEndpoint | Verifying that get availability should use correct endpoint | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should use correct endpoint | In scope: GetAvailability behavior, should use correct endpoint scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAvailability_ShouldPassHeaders | Verifying that get availability should pass headers | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass headers | In scope: GetAvailability behavior, should pass headers scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAvailability_WithEmptyProvLocs_ShouldReturnEmpty | Verifying that get availability with empty prov locs returns empty | Setup with empty input -> Call GetAvailability -> Assert returns empty collection | GetAvailability with empty prov locs returns empty | In scope: empty input handling for GetAvailability. Out of scope: non-empty input scenarios. |
| 10 | | GetAvailability_ShouldMapDailySummaries | Verifying that get availability should map daily summaries | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map daily summaries | In scope: GetAvailability behavior, should map daily summaries scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAvailability_ShouldMapHourlySummaries | Verifying that get availability should map hourly summaries | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map hourly summaries | In scope: GetAvailability behavior, should map hourly summaries scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetAvailability_ShouldHandlePartialResponse | Verifying that get availability should handle partial response | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle partial response | In scope: GetAvailability behavior, should handle partial response scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetAvailability_ShouldLogRequestDetails | Verifying that get availability should log request details | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should log request details | In scope: GetAvailability behavior, should log request details scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetAvailability_ShouldEmitMetrics | Verifying that get availability should emit metrics | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should emit metrics | In scope: GetAvailability behavior, should emit metrics scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetAvailability_ShouldHandleTimeout | Verifying that get availability should handle timeout | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle timeout | In scope: GetAvailability behavior, should handle timeout scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | GetAvailability_ShouldBatchLargeRequests | Verifying that get availability should batch large requests | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should batch large requests | In scope: GetAvailability behavior, should batch large requests scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | GetAvailability_ShouldPassVisitType | Verifying that get availability should pass visit type | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass visit type | In scope: GetAvailability behavior, should pass visit type scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | GetAvailability_ShouldPassSpecialtyId | Verifying that get availability should pass specialty id | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass specialty id | In scope: GetAvailability behavior, should pass specialty id scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | GetAvailability_ShouldIncludeTimezone | Verifying that get availability should include timezone | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should include timezone | In scope: GetAvailability behavior, should include timezone scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | GetAvailability_ShouldRespectCancellationToken | Verifying that get availability should respect cancellation token | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should respect cancellation token | In scope: GetAvailability behavior, should respect cancellation token scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | GetAvailability_ShouldMapOfficeHoursInfo | Verifying that get availability should map office hours info | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map office hours info | In scope: GetAvailability behavior, should map office hours info scenario. Out of scope: other scenarios and methods not under test. |

## ProviderLocationAvailabilityServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailability_ShouldCallClient | Verifying that get availability should call client | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should call client | In scope: GetAvailability behavior, should call client scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_ShouldReturnMappedResults | Verifying that get availability should return mapped results | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should return mapped results | In scope: GetAvailability behavior, should return mapped results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAvailability_WithCacheMiss_ShouldCallClient | Verifying that get availability with cache miss call client | Setup with cache miss -> Call GetAvailability -> Assert call client | GetAvailability with cache miss call client | In scope: GetAvailability behavior, with cache miss scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAvailability_WithCacheHit_ShouldReturnCachedResult | Verifying that get availability with cache hit returns cached result | Setup with cache hit -> Call GetAvailability -> Assert return cached result | GetAvailability with cache hit returns cached result | In scope: GetAvailability behavior, with cache hit scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAvailability_ShouldBatchProvLocIds | Verifying that get availability should batch prov loc ids | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should batch prov loc ids | In scope: GetAvailability behavior, should batch prov loc ids scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAvailability_ShouldMergeResponses | Verifying that get availability should merge responses | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should merge responses | In scope: GetAvailability behavior, should merge responses scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAvailability_ShouldFilterExpiredSlots | Verifying that get availability should filter expired slots | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should filter expired slots | In scope: GetAvailability behavior, should filter expired slots scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAvailability_ShouldHandlePartialFailures | Verifying that get availability should handle partial failures | Setup mock to throw exception -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle partial failures | In scope: error handling in GetAvailability. Out of scope: successful execution paths. |
| 9 | | GetAvailability_ShouldMapNoAvailabilityReason | Verifying that get availability should map no availability reason | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map no availability reason | In scope: GetAvailability behavior, should map no availability reason scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAvailability_ShouldLogCacheHitRate | Verifying that get availability should log cache hit rate | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should log cache hit rate | In scope: GetAvailability behavior, should log cache hit rate scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAvailability_ShouldHandleEmptyResponse | Verifying that get availability should handle empty response | Setup with empty input -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle empty response | In scope: empty input handling for GetAvailability. Out of scope: non-empty input scenarios. |
| 12 | | GetAvailability_ShouldPassInsuranceContext | Verifying that get availability should pass insurance context | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should pass insurance context | In scope: GetAvailability behavior, should pass insurance context scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetAvailability_ShouldHandleNullProvLocs | Verifying that get availability should handle null prov locs | Setup with null input -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle null prov locs | In scope: null input handling for GetAvailability. Out of scope: valid input scenarios. |
| 14 | | GetAvailability_ShouldMapEnhancedAvailability | Verifying that get availability should map enhanced availability | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map enhanced availability | In scope: GetAvailability behavior, should map enhanced availability scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetAvailability_ShouldRespectCancellation | Verifying that get availability should respect cancellation | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should respect cancellation | In scope: GetAvailability behavior, should respect cancellation scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | GetAvailability_ShouldEmitAvailabilityMetrics | Verifying that get availability should emit availability metrics | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should emit availability metrics | In scope: GetAvailability behavior, should emit availability metrics scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | GetAvailability_ShouldHandleDuplicateProvLocs | Verifying that get availability should handle duplicate prov locs | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should handle duplicate prov locs | In scope: GetAvailability behavior, should handle duplicate prov locs scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | GetAvailability_ShouldMapSlotDetails | Verifying that get availability should map slot details | Setup test data and mocks -> Call GetAvailability -> Assert expected behavior of GetAvailability | GetAvailability should map slot details | In scope: GetAvailability behavior, should map slot details scenario. Out of scope: other scenarios and methods not under test. |

# Search/Canoe

## CanoeProvLocGetterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetProvLocs_ShouldCallCanoeClient | Verifying that get prov locs should call canoe client | Setup test data and mocks -> Call GetProvLocs -> Assert expected behavior of GetProvLocs | GetProvLocs should call canoe client | In scope: GetProvLocs behavior, should call canoe client scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetProvLocs_ShouldReturnMappedResults | Verifying that get prov locs should return mapped results | Setup test data and mocks -> Call GetProvLocs -> Assert expected behavior of GetProvLocs | GetProvLocs should return mapped results | In scope: GetProvLocs behavior, should return mapped results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetProvLocs_WithEmptyResponse_ShouldReturnEmpty | Verifying that get prov locs with empty response returns empty | Setup with empty input -> Call GetProvLocs -> Assert returns empty collection | GetProvLocs with empty response returns empty | In scope: empty input handling for GetProvLocs. Out of scope: non-empty input scenarios. |
| 4 | | GetProvLocs_WhenClientThrows_ShouldPropagate | Verifying that get prov locs when client throws propagate | Setup mock to throw exception -> Call GetProvLocs -> Assert propagate | GetProvLocs when client throws propagate | In scope: error handling in GetProvLocs. Out of scope: successful execution paths. |

# Search/Constants

## CarrierIdTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SelfPay_ShouldBeCorrectValue | Verifying that self pay should be correct value | Setup test data and mocks -> Call SelfPay -> Assert expected behavior of SelfPay | SelfPay should be correct value | In scope: SelfPay behavior, should be correct value scenario. Out of scope: other scenarios and methods not under test. |

## PlanIdTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SelfPay_ShouldBeCorrectValue | Verifying that self pay should be correct value | Setup test data and mocks -> Call SelfPay -> Assert expected behavior of SelfPay | SelfPay should be correct value | In scope: SelfPay behavior, should be correct value scenario. Out of scope: other scenarios and methods not under test. |

# Search/Contracts

## CarrierIdTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | CarrierId_ShouldHaveCorrectValue | Verifying that carrier id should have correct value | Setup test data and mocks -> Call CarrierId -> Assert expected behavior of CarrierId | CarrierId should have correct value | In scope: CarrierId behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | CarrierId_ShouldBePositiveInteger | Verifying that carrier id should be positive integer | Setup test data and mocks -> Call CarrierId -> Assert expected behavior of CarrierId | CarrierId should be positive integer | In scope: CarrierId behavior, should be positive integer scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | CarrierId_ShouldMatchConstant | Verifying that carrier id should match constant | Setup test data and mocks -> Call CarrierId -> Assert expected behavior of CarrierId | CarrierId should match constant | In scope: CarrierId behavior, should match constant scenario. Out of scope: other scenarios and methods not under test. |

## ConstantsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SearchConstants_ShouldHaveExpectedValues | Verifying that search constants should have expected values | Setup test data and mocks -> Call SearchConstants -> Assert expected behavior of SearchConstants | SearchConstants should have expected values | In scope: SearchConstants behavior, should have expected values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | SearchConstants_ShouldBeImmutable | Verifying that search constants should be immutable | Setup test data and mocks -> Call SearchConstants -> Assert expected behavior of SearchConstants | SearchConstants should be immutable | In scope: SearchConstants behavior, should be immutable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | AllConstants_ShouldBeDistinct | Verifying that all constants should be distinct | Setup test data and mocks -> Call AllConstants -> Assert expected behavior of AllConstants | AllConstants should be distinct | In scope: AllConstants behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | DefaultTimeout_ShouldBePositive | Verifying that default timeout should be positive | Setup test data and mocks -> Call DefaultTimeout -> Assert expected behavior of DefaultTimeout | DefaultTimeout should be positive | In scope: DefaultTimeout behavior, should be positive scenario. Out of scope: other scenarios and methods not under test. |

## DayFilterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Parse_WithMonday_ShouldReturnMonday | Verifying that parse with monday returns monday | Setup with monday -> Call Parse -> Assert return monday | Parse with monday returns monday | In scope: Parse behavior, with monday scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Parse_WithTuesday_ShouldReturnTuesday | Verifying that parse with tuesday returns tuesday | Setup with tuesday -> Call Parse -> Assert return tuesday | Parse with tuesday returns tuesday | In scope: Parse behavior, with tuesday scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Parse_WithWednesday_ShouldReturnWednesday | Verifying that parse with wednesday returns wednesday | Setup with wednesday -> Call Parse -> Assert return wednesday | Parse with wednesday returns wednesday | In scope: Parse behavior, with wednesday scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Parse_WithThursday_ShouldReturnThursday | Verifying that parse with thursday returns thursday | Setup with thursday -> Call Parse -> Assert return thursday | Parse with thursday returns thursday | In scope: Parse behavior, with thursday scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Parse_WithFriday_ShouldReturnFriday | Verifying that parse with friday returns friday | Setup with friday -> Call Parse -> Assert return friday | Parse with friday returns friday | In scope: Parse behavior, with friday scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Parse_WithSaturday_ShouldReturnSaturday | Verifying that parse with saturday returns saturday | Setup with saturday -> Call Parse -> Assert return saturday | Parse with saturday returns saturday | In scope: Parse behavior, with saturday scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Parse_WithSunday_ShouldReturnSunday | Verifying that parse with sunday returns sunday | Setup with sunday -> Call Parse -> Assert return sunday | Parse with sunday returns sunday | In scope: Parse behavior, with sunday scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Parse_WithInvalidDay_ShouldThrow | Verifying that parse with invalid day throw | Setup with invalid day -> Call Parse -> Assert exception is thrown | Parse with invalid day throw | In scope: Parse behavior, with invalid day scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Parse_WithNullString_ShouldThrow | Verifying that parse with null string throw | Setup with null input -> Call Parse -> Assert exception is thrown | Parse with null string throw | In scope: null input handling for Parse. Out of scope: valid input scenarios. |
| 10 | | AllDays_ShouldContainSevenDays | Verifying that all days should contain seven days | Setup test data and mocks -> Call AllDays -> Assert expected behavior of AllDays | AllDays should contain seven days | In scope: AllDays behavior, should contain seven days scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | ToString_ShouldReturnExpectedValue | Verifying that to string should return expected value | Setup test data and mocks -> Call ToString -> Assert expected behavior of ToString | ToString should return expected value | In scope: ToString behavior, should return expected value scenario. Out of scope: other scenarios and methods not under test. |

## DefaultInternalSearchParamsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetDefaultValues | Verifying that constructor should set default values | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set default values | In scope: Constructor behavior, should set default values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | DefaultPageSize_ShouldMatchConstant | Verifying that default page size should match constant | Setup test data and mocks -> Call DefaultPageSize -> Assert expected behavior of DefaultPageSize | DefaultPageSize should match constant | In scope: DefaultPageSize behavior, should match constant scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | DefaultElasticSize_ShouldMatchConstant | Verifying that default elastic size should match constant | Setup test data and mocks -> Call DefaultElasticSize -> Assert expected behavior of DefaultElasticSize | DefaultElasticSize should match constant | In scope: DefaultElasticSize behavior, should match constant scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | DefaultSortBy_ShouldBeBestMatch | Verifying that default sort by should be best match | Setup test data and mocks -> Call DefaultSortBy -> Assert expected behavior of DefaultSortBy | DefaultSortBy should be best match | In scope: DefaultSortBy behavior, should be best match scenario. Out of scope: other scenarios and methods not under test. |

## DefaultPageConstantTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Value_ShouldBeExpected | Verifying that value should be expected | Setup test data and mocks -> Call Value -> Assert expected behavior of Value | Value should be expected | In scope: Value behavior, should be expected scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Value_ShouldBePositive | Verifying that value should be positive | Setup test data and mocks -> Call Value -> Assert expected behavior of Value | Value should be positive | In scope: Value behavior, should be positive scenario. Out of scope: other scenarios and methods not under test. |

## FacetB64EnumsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Serialize_ShouldEncodeToBase64 | Verifying that serialize should encode to base64 | Setup test data and mocks -> Call Serialize -> Assert expected behavior of Serialize | Serialize should encode to base64 | In scope: Serialize behavior, should encode to base64 scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Deserialize_ShouldDecodeFromBase64 | Verifying that deserialize should decode from base64 | Setup test data and mocks -> Call Deserialize -> Assert expected behavior of Deserialize | Deserialize should decode from base64 | In scope: Deserialize behavior, should decode from base64 scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | RoundTrip_ShouldPreserveValues | Verifying that round trip should preserve values | Setup test data and mocks -> Call RoundTrip -> Assert expected behavior of RoundTrip | RoundTrip should preserve values | In scope: RoundTrip behavior, should preserve values scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Serialize_WithNullValue_ShouldReturnEmpty | Verifying that serialize with null value returns empty | Setup with null input -> Call Serialize -> Assert returns empty collection | Serialize with null value returns empty | In scope: null input handling for Serialize. Out of scope: valid input scenarios. |
| 5 | | Deserialize_WithInvalidBase64_ShouldThrow | Verifying that deserialize with invalid base64 throw | Setup with invalid base64 -> Call Deserialize -> Assert exception is thrown | Deserialize with invalid base64 throw | In scope: Deserialize behavior, with invalid base64 scenario. Out of scope: other scenarios and methods not under test. |

## GenderTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Male_ShouldHaveCorrectValue | Verifying that male should have correct value | Setup test data and mocks -> Call Male -> Assert expected behavior of Male | Male should have correct value | In scope: Male behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Female_ShouldHaveCorrectValue | Verifying that female should have correct value | Setup test data and mocks -> Call Female -> Assert expected behavior of Female | Female should have correct value | In scope: Female behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | NonBinary_ShouldHaveCorrectValue | Verifying that non binary should have correct value | Setup test data and mocks -> Call NonBinary -> Assert expected behavior of NonBinary | NonBinary should have correct value | In scope: NonBinary behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AllValues_ShouldBeDistinct | Verifying that all values should be distinct | Setup test data and mocks -> Call AllValues -> Assert expected behavior of AllValues | AllValues should be distinct | In scope: AllValues behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## GeoDistanceRangeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetMinAndMaxDistance | Verifying that constructor should set min and max distance | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set min and max distance | In scope: Constructor behavior, should set min and max distance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Contains_WithDistanceInRange_ShouldReturnTrue | Verifying that contains with distance in range returns true | Setup with distance in range -> Call Contains -> Assert returns true | Contains with distance in range returns true | In scope: Contains behavior, with distance in range scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Contains_WithDistanceOutOfRange_ShouldReturnFalse | Verifying that contains with distance out of range returns false | Setup with distance out of range -> Call Contains -> Assert returns false | Contains with distance out of range returns false | In scope: Contains behavior, with distance out of range scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Contains_WithZeroDistance_ShouldHandleCorrectly | Verifying that contains with zero distance handle correctly | Setup with zero distance -> Call Contains -> Assert handle correctly | Contains with zero distance handle correctly | In scope: Contains behavior, with zero distance scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Contains_WithNegativeDistance_ShouldReturnFalse | Verifying that contains with negative distance returns false | Setup with negative distance -> Call Contains -> Assert returns false | Contains with negative distance returns false | In scope: Contains behavior, with negative distance scenario. Out of scope: other scenarios and methods not under test. |

## PlanIdTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SelfPay_ShouldHaveCorrectValue | Verifying that self pay should have correct value | Setup test data and mocks -> Call SelfPay -> Assert expected behavior of SelfPay | SelfPay should have correct value | In scope: SelfPay behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | SelfPay_ShouldBePositive | Verifying that self pay should be positive | Setup test data and mocks -> Call SelfPay -> Assert expected behavior of SelfPay | SelfPay should be positive | In scope: SelfPay behavior, should be positive scenario. Out of scope: other scenarios and methods not under test. |

## RankByTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | BestMatch_ShouldHaveCorrectValue | Verifying that best match should have correct value | Setup test data and mocks -> Call BestMatch -> Assert expected behavior of BestMatch | BestMatch should have correct value | In scope: BestMatch behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Distance_ShouldHaveCorrectValue | Verifying that distance should have correct value | Setup test data and mocks -> Call Distance -> Assert expected behavior of Distance | Distance should have correct value | In scope: Distance behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Availability_ShouldHaveCorrectValue | Verifying that availability should have correct value | Setup test data and mocks -> Call Availability -> Assert expected behavior of Availability | Availability should have correct value | In scope: Availability behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AllValues_ShouldBeDistinct | Verifying that all values should be distinct | Setup test data and mocks -> Call AllValues -> Assert expected behavior of AllValues | AllValues should be distinct | In scope: AllValues behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## SearchTypeExtensionsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ToSearchType_WithMarketplace_ShouldReturnMarketplace | Verifying that to search type with marketplace returns marketplace | Setup with marketplace -> Call ToSearchType -> Assert return marketplace | ToSearchType with marketplace returns marketplace | In scope: ToSearchType behavior, with marketplace scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ToSearchType_WithEnterprise_ShouldReturnEnterprise | Verifying that to search type with enterprise returns enterprise | Setup with enterprise -> Call ToSearchType -> Assert return enterprise | ToSearchType with enterprise returns enterprise | In scope: ToSearchType behavior, with enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ToSearchType_WithInvalidString_ShouldThrow | Verifying that to search type with invalid string throw | Setup with invalid string -> Call ToSearchType -> Assert exception is thrown | ToSearchType with invalid string throw | In scope: ToSearchType behavior, with invalid string scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ToString_ShouldReturnCorrectValue | Verifying that to string should return correct value | Setup test data and mocks -> Call ToString -> Assert expected behavior of ToString | ToString should return correct value | In scope: ToString behavior, should return correct value scenario. Out of scope: other scenarios and methods not under test. |

## SearchTypeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Marketplace_ShouldHaveCorrectValue | Verifying that marketplace should have correct value | Setup test data and mocks -> Call Marketplace -> Assert expected behavior of Marketplace | Marketplace should have correct value | In scope: Marketplace behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enterprise_ShouldHaveCorrectValue | Verifying that enterprise should have correct value | Setup test data and mocks -> Call Enterprise -> Assert expected behavior of Enterprise | Enterprise should have correct value | In scope: Enterprise behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | AllValues_ShouldBeDistinct | Verifying that all values should be distinct | Setup test data and mocks -> Call AllValues -> Assert expected behavior of AllValues | AllValues should be distinct | In scope: AllValues behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## SpecialSearchDistanceModeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Default_ShouldHaveCorrectValue | Verifying that default should have correct value | Setup test data and mocks -> Call Default -> Assert expected behavior of Default | Default should have correct value | In scope: Default behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extended_ShouldHaveCorrectValue | Verifying that extended should have correct value | Setup test data and mocks -> Call Extended -> Assert expected behavior of Extended | Extended should have correct value | In scope: Extended behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | AllValues_ShouldBeDistinct | Verifying that all values should be distinct | Setup test data and mocks -> Call AllValues -> Assert expected behavior of AllValues | AllValues should be distinct | In scope: AllValues behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## TimeFilterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Parse_WithMorning_ShouldReturnMorning | Verifying that parse with morning returns morning | Setup with morning -> Call Parse -> Assert return morning | Parse with morning returns morning | In scope: Parse behavior, with morning scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Parse_WithAfternoon_ShouldReturnAfternoon | Verifying that parse with afternoon returns afternoon | Setup with afternoon -> Call Parse -> Assert return afternoon | Parse with afternoon returns afternoon | In scope: Parse behavior, with afternoon scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Parse_WithEvening_ShouldReturnEvening | Verifying that parse with evening returns evening | Setup with evening -> Call Parse -> Assert return evening | Parse with evening returns evening | In scope: Parse behavior, with evening scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Parse_WithInvalidTime_ShouldThrow | Verifying that parse with invalid time throw | Setup with invalid time -> Call Parse -> Assert exception is thrown | Parse with invalid time throw | In scope: Parse behavior, with invalid time scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Parse_WithNullString_ShouldThrow | Verifying that parse with null string throw | Setup with null input -> Call Parse -> Assert exception is thrown | Parse with null string throw | In scope: null input handling for Parse. Out of scope: valid input scenarios. |
| 6 | | AllTimes_ShouldBeDistinct | Verifying that all times should be distinct | Setup test data and mocks -> Call AllTimes -> Assert expected behavior of AllTimes | AllTimes should be distinct | In scope: AllTimes behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

# Search/Contracts/Request

## ReflectionHelpersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetPropertyValue_ShouldReturnCorrectValue | Verifying that get property value should return correct value | Setup test data and mocks -> Call GetPropertyValue -> Assert expected behavior of GetPropertyValue | GetPropertyValue should return correct value | In scope: GetPropertyValue behavior, should return correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetPropertyValue_WithInvalidProperty_ShouldReturnNull | Verifying that get property value with invalid property returns null | Setup with invalid property -> Call GetPropertyValue -> Assert returns null | GetPropertyValue with invalid property returns null | In scope: GetPropertyValue behavior, with invalid property scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetPropertyValue_WithNullObject_ShouldReturnNull | Verifying that get property value with null object returns null | Setup with null input -> Call GetPropertyValue -> Assert returns null | GetPropertyValue with null object returns null | In scope: null input handling for GetPropertyValue. Out of scope: valid input scenarios. |
| 4 | | SetPropertyValue_ShouldSetCorrectly | Verifying that set property value should set correctly | Setup test data and mocks -> Call SetPropertyValue -> Assert expected behavior of SetPropertyValue | SetPropertyValue should set correctly | In scope: SetPropertyValue behavior, should set correctly scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAllProperties_ShouldReturnAllProperties | Verifying that get all properties should return all properties | Setup test data and mocks -> Call GetAllProperties -> Assert expected behavior of GetAllProperties | GetAllProperties should return all properties | In scope: GetAllProperties behavior, should return all properties scenario. Out of scope: other scenarios and methods not under test. |

## SharedMethodValidationsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ValidateSearchParams_WithValidParams_ShouldReturnTrue | Verifying that validate search params with valid params returns true | Setup with valid params -> Call ValidateSearchParams -> Assert returns true | ValidateSearchParams with valid params returns true | In scope: ValidateSearchParams behavior, with valid params scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ValidateSearchParams_WithInvalidParams_ShouldReturnFalse | Verifying that validate search params with invalid params returns false | Setup with invalid params -> Call ValidateSearchParams -> Assert returns false | ValidateSearchParams with invalid params returns false | In scope: ValidateSearchParams behavior, with invalid params scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ValidateSearchParams_WithNullParams_ShouldReturnFalse | Verifying that validate search params with null params returns false | Setup with null input -> Call ValidateSearchParams -> Assert returns false | ValidateSearchParams with null params returns false | In scope: null input handling for ValidateSearchParams. Out of scope: valid input scenarios. |
| 4 | | ValidatePageSize_WithValidSize_ShouldReturnTrue | Verifying that validate page size with valid size returns true | Setup with valid size -> Call ValidatePageSize -> Assert returns true | ValidatePageSize with valid size returns true | In scope: ValidatePageSize behavior, with valid size scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ValidatePageSize_WithZeroSize_ShouldReturnFalse | Verifying that validate page size with zero size returns false | Setup with zero size -> Call ValidatePageSize -> Assert returns false | ValidatePageSize with zero size returns false | In scope: ValidatePageSize behavior, with zero size scenario. Out of scope: other scenarios and methods not under test. |

## SimpleHttpRequestTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetUrlAndMethod | Verifying that constructor should set url and method | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set url and method | In scope: Constructor behavior, should set url and method scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | AddHeader_ShouldAddHeaderToRequest | Verifying that add header should add header to request | Setup test data and mocks -> Call AddHeader -> Assert expected behavior of AddHeader | AddHeader should add header to request | In scope: AddHeader behavior, should add header to request scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Build_ShouldReturnValidRequest | Verifying that build should return valid request | Setup test data and mocks -> Call Build -> Assert expected behavior of Build | Build should return valid request | In scope: Build behavior, should return valid request scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AddQueryParam_ShouldAddParameter | Verifying that add query param should add parameter | Setup test data and mocks -> Call AddQueryParam -> Assert expected behavior of AddQueryParam | AddQueryParam should add parameter | In scope: AddQueryParam behavior, should add parameter scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | SetBody_ShouldSetRequestBody | Verifying that set body should set request body | Setup test data and mocks -> Call SetBody -> Assert expected behavior of SetBody | SetBody should set request body | In scope: SetBody behavior, should set request body scenario. Out of scope: other scenarios and methods not under test. |

## VerbosityTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | None_ShouldHaveCorrectValue | Verifying that none should have correct value | Setup test data and mocks -> Call None -> Assert expected behavior of None | None should have correct value | In scope: None behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Minimal_ShouldHaveCorrectValue | Verifying that minimal should have correct value | Setup test data and mocks -> Call Minimal -> Assert expected behavior of Minimal | Minimal should have correct value | In scope: Minimal behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Full_ShouldHaveCorrectValue | Verifying that full should have correct value | Setup test data and mocks -> Call Full -> Assert expected behavior of Full | Full should have correct value | In scope: Full behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Debug_ShouldHaveCorrectValue | Verifying that debug should have correct value | Setup test data and mocks -> Call Debug -> Assert expected behavior of Debug | Debug should have correct value | In scope: Debug behavior, should have correct value scenario. Out of scope: other scenarios and methods not under test. |

## YassRequestHeaderTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Parse_WithValidHeader_ShouldReturnValue | Verifying that parse with valid header returns value | Setup with valid header -> Call Parse -> Assert return value | Parse with valid header returns value | In scope: Parse behavior, with valid header scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Parse_WithNullHeader_ShouldReturnNull | Verifying that parse with null header returns null | Setup with null input -> Call Parse -> Assert returns null | Parse with null header returns null | In scope: null input handling for Parse. Out of scope: valid input scenarios. |
| 3 | | Parse_WithEmptyHeader_ShouldReturnNull | Verifying that parse with empty header returns null | Setup with empty input -> Call Parse -> Assert returns null | Parse with empty header returns null | In scope: empty input handling for Parse. Out of scope: non-empty input scenarios. |
| 4 | | Parse_WithMultipleHeaders_ShouldReturnFirst | Verifying that parse with multiple headers returns first | Setup with multiple headers -> Call Parse -> Assert return first | Parse with multiple headers returns first | In scope: Parse behavior, with multiple headers scenario. Out of scope: other scenarios and methods not under test. |

# Search/Contracts/Response

## ProvLocResponseTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Mapping_ShouldMapCorrectly | Verifying that mapping should map correctly | Setup test data and mocks -> Call Mapping -> Assert expected behavior of Mapping | Mapping should map correctly | In scope: Mapping behavior, should map correctly scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Results_ShouldDefaultToEmptyList | Verifying that results should default to empty list | Setup with empty input -> Call Results -> Assert expected behavior of Results | Results should default to empty list | In scope: empty input handling for Results. Out of scope: non-empty input scenarios. |

# Search/Contracts/Response/Spo

## SpoAdsResponseTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | AdDecisions_ShouldBeSettable | Verifying that ad decisions should be settable | Setup test data and mocks -> Call AdDecisions -> Assert expected behavior of AdDecisions | AdDecisions should be settable | In scope: AdDecisions behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AdDecisions_ShouldDefaultToEmptyList | Verifying that ad decisions should default to empty list | Setup with empty input -> Call AdDecisions -> Assert expected behavior of AdDecisions | AdDecisions should default to empty list | In scope: empty input handling for AdDecisions. Out of scope: non-empty input scenarios. |

# Search/CrossEncoder

## RetryingCrossEncoderServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rerank_WhenFirstCallSucceeds_ShouldReturnResponse | Verifying that rerank when first call succeeds returns response | Setup when first call succeeds -> Call Rerank -> Assert return response | Rerank when first call succeeds returns response | In scope: Rerank behavior, when first call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rerank_WhenFirstCallFails_ShouldRetry | Verifying that rerank when first call fails retry | Setup mock to throw exception -> Call Rerank -> Assert retry | Rerank when first call fails retry | In scope: error handling in Rerank. Out of scope: successful execution paths. |
| 3 | | Rerank_WhenAllRetriesFail_ShouldThrow | Verifying that rerank when all retries fail throw | Setup mock to throw exception -> Call Rerank -> Assert exception is thrown | Rerank when all retries fail throw | In scope: error handling in Rerank. Out of scope: successful execution paths. |
| 4 | | Rerank_ShouldRetryUpToMaxAttempts | Verifying that rerank should retry up to max attempts | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should retry up to max attempts | In scope: Rerank behavior, should retry up to max attempts scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rerank_WhenSecondCallSucceeds_ShouldReturnResponse | Verifying that rerank when second call succeeds returns response | Setup when second call succeeds -> Call Rerank -> Assert return response | Rerank when second call succeeds returns response | In scope: Rerank behavior, when second call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rerank_ShouldPassRequestThrough | Verifying that rerank should pass request through | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should pass request through | In scope: Rerank behavior, should pass request through scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rerank_WhenCancelled_ShouldThrowOperationCancelledException | Verifying that rerank when cancelled throw operation cancelled exception | Setup when cancelled -> Call Rerank -> Assert exception is thrown | Rerank when cancelled throw operation cancelled exception | In scope: Rerank behavior, when cancelled scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rerank_ShouldUseExponentialBackoff | Verifying that rerank should use exponential backoff | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should use exponential backoff | In scope: Rerank behavior, should use exponential backoff scenario. Out of scope: other scenarios and methods not under test. |

## VoyageApiCrossEncoderServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rerank_ShouldCallVoyageApi | Verifying that rerank should call voyage api | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should call voyage api | In scope: Rerank behavior, should call voyage api scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rerank_ShouldPassQueryAndDocuments | Verifying that rerank should pass query and documents | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should pass query and documents | In scope: Rerank behavior, should pass query and documents scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rerank_ShouldReturnRankedResults | Verifying that rerank should return ranked results | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should return ranked results | In scope: Rerank behavior, should return ranked results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rerank_ShouldHandleEmptyDocuments | Verifying that rerank should handle empty documents | Setup with empty input -> Call Rerank -> Assert expected behavior of Rerank | Rerank should handle empty documents | In scope: empty input handling for Rerank. Out of scope: non-empty input scenarios. |
| 5 | | Rerank_WhenApiThrows_ShouldPropagate | Verifying that rerank when api throws propagate | Setup mock to throw exception -> Call Rerank -> Assert propagate | Rerank when api throws propagate | In scope: error handling in Rerank. Out of scope: successful execution paths. |
| 6 | | Rerank_ShouldMapScoresCorrectly | Verifying that rerank should map scores correctly | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should map scores correctly | In scope: Rerank behavior, should map scores correctly scenario. Out of scope: other scenarios and methods not under test. |

## VoyageSageMakerCrossEncoderServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rerank_ShouldCallSageMakerEndpoint | Verifying that rerank should call sage maker endpoint | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should call sage maker endpoint | In scope: Rerank behavior, should call sage maker endpoint scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rerank_ShouldPassQueryAndDocuments | Verifying that rerank should pass query and documents | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should pass query and documents | In scope: Rerank behavior, should pass query and documents scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rerank_ShouldReturnRankedResults | Verifying that rerank should return ranked results | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should return ranked results | In scope: Rerank behavior, should return ranked results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rerank_WhenEndpointThrows_ShouldPropagate | Verifying that rerank when endpoint throws propagate | Setup mock to throw exception -> Call Rerank -> Assert propagate | Rerank when endpoint throws propagate | In scope: error handling in Rerank. Out of scope: successful execution paths. |
| 5 | | Rerank_ShouldMapResponseCorrectly | Verifying that rerank should map response correctly | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should map response correctly | In scope: Rerank behavior, should map response correctly scenario. Out of scope: other scenarios and methods not under test. |

## ZeroEntropyApiCrossEncoderServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rerank_ShouldCallZeroEntropyApi | Verifying that rerank should call zero entropy api | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should call zero entropy api | In scope: Rerank behavior, should call zero entropy api scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rerank_ShouldPassFormattedQuery | Verifying that rerank should pass formatted query | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should pass formatted query | In scope: Rerank behavior, should pass formatted query scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rerank_ShouldReturnRankedResults | Verifying that rerank should return ranked results | Setup test data and mocks -> Call Rerank -> Assert expected behavior of Rerank | Rerank should return ranked results | In scope: Rerank behavior, should return ranked results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rerank_WhenApiThrows_ShouldPropagate | Verifying that rerank when api throws propagate | Setup mock to throw exception -> Call Rerank -> Assert propagate | Rerank when api throws propagate | In scope: error handling in Rerank. Out of scope: successful execution paths. |
| 5 | | Rerank_ShouldHandleEmptyResults | Verifying that rerank should handle empty results | Setup with empty input -> Call Rerank -> Assert expected behavior of Rerank | Rerank should handle empty results | In scope: empty input handling for Rerank. Out of scope: non-empty input scenarios. |

## ZeroEntropyQueryFormatterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Format_WithSimpleQuery_ShouldReturnFormattedQuery | Verifying that format with simple query returns formatted query | Setup with simple query -> Call Format -> Assert return formatted query | Format with simple query returns formatted query | In scope: Format behavior, with simple query scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Format_WithSpecialCharacters_ShouldEscapeCorrectly | Verifying that format with special characters escape correctly | Setup with special characters -> Call Format -> Assert escape correctly | Format with special characters escape correctly | In scope: Format behavior, with special characters scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Format_WithNullQuery_ShouldReturnEmpty | Verifying that format with null query returns empty | Setup with null input -> Call Format -> Assert returns empty collection | Format with null query returns empty | In scope: null input handling for Format. Out of scope: valid input scenarios. |
| 4 | | Format_WithEmptyQuery_ShouldReturnEmpty | Verifying that format with empty query returns empty | Setup with empty input -> Call Format -> Assert returns empty collection | Format with empty query returns empty | In scope: empty input handling for Format. Out of scope: non-empty input scenarios. |

# Search/Datalake

## FirehoseServiceErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | PutRecord_WhenFirehoseThrows_ShouldLogAndNotThrow | Verifying that put record when firehose throws log and not throw | Setup mock to throw exception -> Call PutRecord -> Assert no exception is thrown | PutRecord when firehose throws log and not throw | In scope: error handling in PutRecord. Out of scope: successful execution paths. |
| 2 | | PutRecord_WhenFirehoseThrows_ShouldEmitErrorMetric | Verifying that put record when firehose throws emit error metric | Setup mock to throw exception -> Call PutRecord -> Assert emit error metric | PutRecord when firehose throws emit error metric | In scope: error handling in PutRecord. Out of scope: successful execution paths. |
| 3 | | PutRecord_WhenFirehoseThrows_ShouldStillCallCallback | Verifying that put record when firehose throws still call callback | Setup mock to throw exception -> Call PutRecord -> Assert still call callback | PutRecord when firehose throws still call callback | In scope: error handling in PutRecord. Out of scope: successful execution paths. |

# Search/Decorating

## DecoratorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Decorate_ShouldCallAllDecorators | Verifying that decorate should call all decorators | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should call all decorators | In scope: Decorate behavior, should call all decorators scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Decorate_ShouldPassResultToEachDecorator | Verifying that decorate should pass result to each decorator | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should pass result to each decorator | In scope: Decorate behavior, should pass result to each decorator scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Decorate_WithNoDecorators_ShouldReturnOriginal | Verifying that decorate with no decorators returns original | Setup with no decorators -> Call Decorate -> Assert return original | Decorate with no decorators returns original | In scope: Decorate behavior, with no decorators scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Decorate_ShouldChainDecorators | Verifying that decorate should chain decorators | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should chain decorators | In scope: Decorate behavior, should chain decorators scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Decorate_ShouldHandleNullResult | Verifying that decorate should handle null result | Setup with null input -> Call Decorate -> Assert expected behavior of Decorate | Decorate should handle null result | In scope: null input handling for Decorate. Out of scope: valid input scenarios. |
| 6 | | Decorate_ShouldPreserveOrder | Verifying that decorate should preserve order | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should preserve order | In scope: Decorate behavior, should preserve order scenario. Out of scope: other scenarios and methods not under test. |

## DotProvLocMapDecoratorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Decorate_ShouldAddMapDotsForResults | Verifying that decorate should add map dots for results | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should add map dots for results | In scope: Decorate behavior, should add map dots for results scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Decorate_WithEmptyResults_ShouldReturnEmpty | Verifying that decorate with empty results returns empty | Setup with empty input -> Call Decorate -> Assert returns empty collection | Decorate with empty results returns empty | In scope: empty input handling for Decorate. Out of scope: non-empty input scenarios. |
| 3 | | Decorate_ShouldMapCoordinates | Verifying that decorate should map coordinates | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should map coordinates | In scope: Decorate behavior, should map coordinates scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Decorate_ShouldMapProviderInfo | Verifying that decorate should map provider info | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should map provider info | In scope: Decorate behavior, should map provider info scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Decorate_ShouldMapAvailabilityInfo | Verifying that decorate should map availability info | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should map availability info | In scope: Decorate behavior, should map availability info scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Decorate_ShouldMapRankInfo | Verifying that decorate should map rank info | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should map rank info | In scope: Decorate behavior, should map rank info scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Decorate_ShouldHandleNullCoordinates | Verifying that decorate should handle null coordinates | Setup with null input -> Call Decorate -> Assert expected behavior of Decorate | Decorate should handle null coordinates | In scope: null input handling for Decorate. Out of scope: valid input scenarios. |
| 8 | | Decorate_ShouldLimitDotCount | Verifying that decorate should limit dot count | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should limit dot count | In scope: Decorate behavior, should limit dot count scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Decorate_ShouldIncludeVirtualLocationDots | Verifying that decorate should include virtual location dots | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should include virtual location dots | In scope: Decorate behavior, should include virtual location dots scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Decorate_ShouldSetCorrectDotType | Verifying that decorate should set correct dot type | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should set correct dot type | In scope: Decorate behavior, should set correct dot type scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Decorate_ShouldHandleSpoDots | Verifying that decorate should handle spo dots | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should handle spo dots | In scope: Decorate behavior, should handle spo dots scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Decorate_ShouldSetGroupInformation | Verifying that decorate should set group information | Setup test data and mocks -> Call Decorate -> Assert expected behavior of Decorate | Decorate should set group information | In scope: Decorate behavior, should set group information scenario. Out of scope: other scenarios and methods not under test. |

# Search/DynamoDb

## PracticeFeaturesRetrieverTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case1 | Verifying that get features with batch retrieval returns features_ case1 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case1 | GetFeatures with batch retrieval returns features_ case1 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case2 | Verifying that get features with batch retrieval returns features_ case2 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case2 | GetFeatures with batch retrieval returns features_ case2 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case3 | Verifying that get features with batch retrieval returns features_ case3 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case3 | GetFeatures with batch retrieval returns features_ case3 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case4 | Verifying that get features with batch retrieval returns features_ case4 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case4 | GetFeatures with batch retrieval returns features_ case4 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case5 | Verifying that get features with batch retrieval returns features_ case5 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case5 | GetFeatures with batch retrieval returns features_ case5 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case6 | Verifying that get features with batch retrieval returns features_ case6 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case6 | GetFeatures with batch retrieval returns features_ case6 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetFeatures_WithBatchRetrieval_ShouldReturnFeatures_Case7 | Verifying that get features with batch retrieval returns features_ case7 | Setup with batch retrieval -> Call GetFeatures -> Assert return features_ case7 | GetFeatures with batch retrieval returns features_ case7 | In scope: GetFeatures behavior, with batch retrieval scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case1 | Verifying that get features with cache handling is have correctly_ case1 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case1 | GetFeatures with cache handling is have correctly_ case1 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case2 | Verifying that get features with cache handling is have correctly_ case2 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case2 | GetFeatures with cache handling is have correctly_ case2 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case3 | Verifying that get features with cache handling is have correctly_ case3 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case3 | GetFeatures with cache handling is have correctly_ case3 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case4 | Verifying that get features with cache handling is have correctly_ case4 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case4 | GetFeatures with cache handling is have correctly_ case4 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case5 | Verifying that get features with cache handling is have correctly_ case5 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case5 | GetFeatures with cache handling is have correctly_ case5 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case6 | Verifying that get features with cache handling is have correctly_ case6 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case6 | GetFeatures with cache handling is have correctly_ case6 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetFeatures_WithCacheHandling_ShouldBehaveCorrectly_Case7 | Verifying that get features with cache handling is have correctly_ case7 | Setup with cache handling -> Call GetFeatures -> Assert behave correctly_ case7 | GetFeatures with cache handling is have correctly_ case7 | In scope: GetFeatures behavior, with cache handling scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetFeatures_WithErrorRecovery_ShouldHandleGracefully_Case1 | Verifying that get features with error recovery handle gracefully_ case1 | Setup mock to throw exception -> Call GetFeatures -> Assert handle gracefully_ case1 | GetFeatures with error recovery handle gracefully_ case1 | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 16 | | GetFeatures_WithErrorRecovery_ShouldHandleGracefully_Case2 | Verifying that get features with error recovery handle gracefully_ case2 | Setup mock to throw exception -> Call GetFeatures -> Assert handle gracefully_ case2 | GetFeatures with error recovery handle gracefully_ case2 | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 17 | | GetFeatures_WithErrorRecovery_ShouldHandleGracefully_Case3 | Verifying that get features with error recovery handle gracefully_ case3 | Setup mock to throw exception -> Call GetFeatures -> Assert handle gracefully_ case3 | GetFeatures with error recovery handle gracefully_ case3 | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 18 | | GetFeatures_WithErrorRecovery_ShouldHandleGracefully_Case4 | Verifying that get features with error recovery handle gracefully_ case4 | Setup mock to throw exception -> Call GetFeatures -> Assert handle gracefully_ case4 | GetFeatures with error recovery handle gracefully_ case4 | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 19 | | GetFeatures_WithErrorRecovery_ShouldHandleGracefully_Case5 | Verifying that get features with error recovery handle gracefully_ case5 | Setup mock to throw exception -> Call GetFeatures -> Assert handle gracefully_ case5 | GetFeatures with error recovery handle gracefully_ case5 | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 20 | | GetFeatures_WithErrorRecovery_ShouldHandleGracefully_Case6 | Verifying that get features with error recovery handle gracefully_ case6 | Setup mock to throw exception -> Call GetFeatures -> Assert handle gracefully_ case6 | GetFeatures with error recovery handle gracefully_ case6 | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 21 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case1 | Verifying that get features with attribute mapping map correctly_ case1 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case1 | GetFeatures with attribute mapping map correctly_ case1 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case2 | Verifying that get features with attribute mapping map correctly_ case2 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case2 | GetFeatures with attribute mapping map correctly_ case2 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case3 | Verifying that get features with attribute mapping map correctly_ case3 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case3 | GetFeatures with attribute mapping map correctly_ case3 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case4 | Verifying that get features with attribute mapping map correctly_ case4 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case4 | GetFeatures with attribute mapping map correctly_ case4 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case5 | Verifying that get features with attribute mapping map correctly_ case5 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case5 | GetFeatures with attribute mapping map correctly_ case5 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case6 | Verifying that get features with attribute mapping map correctly_ case6 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case6 | GetFeatures with attribute mapping map correctly_ case6 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | GetFeatures_WithAttributeMapping_ShouldMapCorrectly_Case7 | Verifying that get features with attribute mapping map correctly_ case7 | Setup with attribute mapping -> Call GetFeatures -> Assert map correctly_ case7 | GetFeatures with attribute mapping map correctly_ case7 | In scope: GetFeatures behavior, with attribute mapping scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | GetFeatures_WithNullOrMissingData_ShouldHandleGracefully_Case1 | Verifying that get features with null or missing data handle gracefully_ case1 | Setup with null input -> Call GetFeatures -> Assert handle gracefully_ case1 | GetFeatures with null or missing data handle gracefully_ case1 | In scope: null input handling for GetFeatures. Out of scope: valid input scenarios. |
| 29 | | GetFeatures_WithNullOrMissingData_ShouldHandleGracefully_Case2 | Verifying that get features with null or missing data handle gracefully_ case2 | Setup with null input -> Call GetFeatures -> Assert handle gracefully_ case2 | GetFeatures with null or missing data handle gracefully_ case2 | In scope: null input handling for GetFeatures. Out of scope: valid input scenarios. |
| 30 | | GetFeatures_WithNullOrMissingData_ShouldHandleGracefully_Case3 | Verifying that get features with null or missing data handle gracefully_ case3 | Setup with null input -> Call GetFeatures -> Assert handle gracefully_ case3 | GetFeatures with null or missing data handle gracefully_ case3 | In scope: null input handling for GetFeatures. Out of scope: valid input scenarios. |
| 31 | | GetFeatures_WithNullOrMissingData_ShouldHandleGracefully_Case4 | Verifying that get features with null or missing data handle gracefully_ case4 | Setup with null input -> Call GetFeatures -> Assert handle gracefully_ case4 | GetFeatures with null or missing data handle gracefully_ case4 | In scope: null input handling for GetFeatures. Out of scope: valid input scenarios. |
| 32 | | GetFeatures_WithNullOrMissingData_ShouldHandleGracefully_Case5 | Verifying that get features with null or missing data handle gracefully_ case5 | Setup with null input -> Call GetFeatures -> Assert handle gracefully_ case5 | GetFeatures with null or missing data handle gracefully_ case5 | In scope: null input handling for GetFeatures. Out of scope: valid input scenarios. |
| 33 | | GetFeatures_WithNullOrMissingData_ShouldHandleGracefully_Case6 | Verifying that get features with null or missing data handle gracefully_ case6 | Setup with null input -> Call GetFeatures -> Assert handle gracefully_ case6 | GetFeatures with null or missing data handle gracefully_ case6 | In scope: null input handling for GetFeatures. Out of scope: valid input scenarios. |

## RealizationProviderFeaturesRetrieverErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetFeatures_WhenDynamoDbThrows_ShouldLogAndReturnEmpty | Verifying that get features when dynamo db throws log and return empty | Setup mock to throw exception -> Call GetFeatures -> Assert returns empty collection | GetFeatures when dynamo db throws log and return empty | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 2 | | GetFeatures_WhenDynamoDbThrows_ShouldEmitErrorMetric | Verifying that get features when dynamo db throws emit error metric | Setup mock to throw exception -> Call GetFeatures -> Assert emit error metric | GetFeatures when dynamo db throws emit error metric | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |
| 3 | | GetFeatures_WhenDynamoDbThrows_ShouldNotPropagateException | Verifying that get features when dynamo db throws does not propagate exception | Setup mock to throw exception -> Call GetFeatures -> Assert no exception is thrown | GetFeatures when dynamo db throws does not propagate exception | In scope: error handling in GetFeatures. Out of scope: successful execution paths. |

# Search/Embeddings

## CachedEmbeddingServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetEmbedding_WithCacheHit_ShouldReturnCachedResult | Verifying that get embedding with cache hit returns cached result | Setup with cache hit -> Call GetEmbedding -> Assert return cached result | GetEmbedding with cache hit returns cached result | In scope: GetEmbedding behavior, with cache hit scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetEmbedding_WithCacheMiss_ShouldCallService | Verifying that get embedding with cache miss call service | Setup with cache miss -> Call GetEmbedding -> Assert call service | GetEmbedding with cache miss call service | In scope: GetEmbedding behavior, with cache miss scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetEmbedding_WithCacheMiss_ShouldStoreInCache | Verifying that get embedding with cache miss store in cache | Setup with cache miss -> Call GetEmbedding -> Assert store in cache | GetEmbedding with cache miss store in cache | In scope: GetEmbedding behavior, with cache miss scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetEmbedding_ShouldUseCacheKey | Verifying that get embedding should use cache key | Setup test data and mocks -> Call GetEmbedding -> Assert expected behavior of GetEmbedding | GetEmbedding should use cache key | In scope: GetEmbedding behavior, should use cache key scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetEmbedding_WithExpiredCache_ShouldCallService | Verifying that get embedding with expired cache call service | Setup with expired cache -> Call GetEmbedding -> Assert call service | GetEmbedding with expired cache call service | In scope: GetEmbedding behavior, with expired cache scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetEmbedding_ShouldRespectTTL | Verifying that get embedding should respect t t l | Setup test data and mocks -> Call GetEmbedding -> Assert expected behavior of GetEmbedding | GetEmbedding should respect t t l | In scope: GetEmbedding behavior, should respect t t l scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetEmbedding_ShouldEmitCacheHitMetric | Verifying that get embedding should emit cache hit metric | Setup test data and mocks -> Call GetEmbedding -> Assert expected behavior of GetEmbedding | GetEmbedding should emit cache hit metric | In scope: GetEmbedding behavior, should emit cache hit metric scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetEmbedding_ShouldEmitCacheMissMetric | Verifying that get embedding should emit cache miss metric | Setup test data and mocks -> Call GetEmbedding -> Assert expected behavior of GetEmbedding | GetEmbedding should emit cache miss metric | In scope: GetEmbedding behavior, should emit cache miss metric scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetEmbedding_WhenCacheThrows_ShouldFallbackToService | Verifying that get embedding when cache throws fallback to service | Setup mock to throw exception -> Call GetEmbedding -> Assert fallback to service | GetEmbedding when cache throws fallback to service | In scope: error handling in GetEmbedding. Out of scope: successful execution paths. |

## RetryingEmbeddingServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetEmbedding_WhenFirstCallSucceeds_ShouldReturnResponse | Verifying that get embedding when first call succeeds returns response | Setup when first call succeeds -> Call GetEmbedding -> Assert return response | GetEmbedding when first call succeeds returns response | In scope: GetEmbedding behavior, when first call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetEmbedding_WhenFirstCallFails_ShouldRetry | Verifying that get embedding when first call fails retry | Setup mock to throw exception -> Call GetEmbedding -> Assert retry | GetEmbedding when first call fails retry | In scope: error handling in GetEmbedding. Out of scope: successful execution paths. |
| 3 | | GetEmbedding_WhenAllRetriesFail_ShouldThrow | Verifying that get embedding when all retries fail throw | Setup mock to throw exception -> Call GetEmbedding -> Assert exception is thrown | GetEmbedding when all retries fail throw | In scope: error handling in GetEmbedding. Out of scope: successful execution paths. |
| 4 | | GetEmbedding_ShouldRetryUpToMaxAttempts | Verifying that get embedding should retry up to max attempts | Setup test data and mocks -> Call GetEmbedding -> Assert expected behavior of GetEmbedding | GetEmbedding should retry up to max attempts | In scope: GetEmbedding behavior, should retry up to max attempts scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetEmbedding_WhenSecondCallSucceeds_ShouldReturnResponse | Verifying that get embedding when second call succeeds returns response | Setup when second call succeeds -> Call GetEmbedding -> Assert return response | GetEmbedding when second call succeeds returns response | In scope: GetEmbedding behavior, when second call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetEmbedding_ShouldUseExponentialBackoff | Verifying that get embedding should use exponential backoff | Setup test data and mocks -> Call GetEmbedding -> Assert expected behavior of GetEmbedding | GetEmbedding should use exponential backoff | In scope: GetEmbedding behavior, should use exponential backoff scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetEmbedding_WhenCancelled_ShouldThrowOperationCancelledException | Verifying that get embedding when cancelled throw operation cancelled exception | Setup when cancelled -> Call GetEmbedding -> Assert exception is thrown | GetEmbedding when cancelled throw operation cancelled exception | In scope: GetEmbedding behavior, when cancelled scenario. Out of scope: other scenarios and methods not under test. |

## VoyageQueryHelperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | PrepareQuery_WithSimpleText_ShouldReturnPreparedQuery | Verifying that prepare query with simple text returns prepared query | Setup with simple text -> Call PrepareQuery -> Assert return prepared query | PrepareQuery with simple text returns prepared query | In scope: PrepareQuery behavior, with simple text scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | PrepareQuery_WithLongText_ShouldTruncate | Verifying that prepare query with long text truncate | Setup with long text -> Call PrepareQuery -> Assert truncate | PrepareQuery with long text truncate | In scope: PrepareQuery behavior, with long text scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | PrepareQuery_WithSpecialCharacters_ShouldHandle | Verifying that prepare query with special characters handle | Setup with special characters -> Call PrepareQuery -> Assert handle | PrepareQuery with special characters handle | In scope: PrepareQuery behavior, with special characters scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | PrepareQuery_WithNullText_ShouldReturnEmpty | Verifying that prepare query with null text returns empty | Setup with null input -> Call PrepareQuery -> Assert returns empty collection | PrepareQuery with null text returns empty | In scope: null input handling for PrepareQuery. Out of scope: valid input scenarios. |
| 5 | | PrepareQuery_WithEmptyText_ShouldReturnEmpty | Verifying that prepare query with empty text returns empty | Setup with empty input -> Call PrepareQuery -> Assert returns empty collection | PrepareQuery with empty text returns empty | In scope: empty input handling for PrepareQuery. Out of scope: non-empty input scenarios. |
| 6 | | PrepareQuery_WithWhitespace_ShouldTrim | Verifying that prepare query with whitespace trim | Setup with whitespace -> Call PrepareQuery -> Assert trim | PrepareQuery with whitespace trim | In scope: PrepareQuery behavior, with whitespace scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | PrepareQuery_WithMedicalTerms_ShouldPreserve | Verifying that prepare query with medical terms preserve | Setup with medical terms -> Call PrepareQuery -> Assert preserve | PrepareQuery with medical terms preserve | In scope: PrepareQuery behavior, with medical terms scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | PrepareQuery_WithUnicodeCharacters_ShouldHandle | Verifying that prepare query with unicode characters handle | Setup with unicode characters -> Call PrepareQuery -> Assert handle | PrepareQuery with unicode characters handle | In scope: PrepareQuery behavior, with unicode characters scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | PrepareQuery_ShouldNormalizeWhitespace | Verifying that prepare query should normalize whitespace | Setup test data and mocks -> Call PrepareQuery -> Assert expected behavior of PrepareQuery | PrepareQuery should normalize whitespace | In scope: PrepareQuery behavior, should normalize whitespace scenario. Out of scope: other scenarios and methods not under test. |

# Search/Enchilada

## CostPlanDefaultsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | DefaultCostPlan_ShouldHaveExpectedValues | Verifying that default cost plan should have expected values | Setup test data and mocks -> Call DefaultCostPlan -> Assert expected behavior of DefaultCostPlan | DefaultCostPlan should have expected values | In scope: DefaultCostPlan behavior, should have expected values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | DefaultCostPlan_ShouldBeImmutable | Verifying that default cost plan should be immutable | Setup test data and mocks -> Call DefaultCostPlan -> Assert expected behavior of DefaultCostPlan | DefaultCostPlan should be immutable | In scope: DefaultCostPlan behavior, should be immutable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetDefault_ShouldReturnCorrectPlan | Verifying that get default should return correct plan | Setup test data and mocks -> Call GetDefault -> Assert expected behavior of GetDefault | GetDefault should return correct plan | In scope: GetDefault behavior, should return correct plan scenario. Out of scope: other scenarios and methods not under test. |

## EnchiladaFeatureNamesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | AllFeatureNames_ShouldBeDistinct | Verifying that all feature names should be distinct | Setup test data and mocks -> Call AllFeatureNames -> Assert expected behavior of AllFeatureNames | AllFeatureNames should be distinct | In scope: AllFeatureNames behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | AllFeatureNames_ShouldNotBeEmpty | Verifying that all feature names should not be empty | Setup with empty input -> Call AllFeatureNames -> Assert expected behavior of AllFeatureNames | AllFeatureNames should not be empty | In scope: empty input handling for AllFeatureNames. Out of scope: non-empty input scenarios. |
| 3 | | FeatureCount_ShouldMatchExpected | Verifying that feature count should match expected | Setup test data and mocks -> Call FeatureCount -> Assert expected behavior of FeatureCount | FeatureCount should match expected | In scope: FeatureCount behavior, should match expected scenario. Out of scope: other scenarios and methods not under test. |

## EnchiladaFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnCorrectFeatureCount | Verifying that extract should return correct feature count | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return correct feature count | In scope: Extract behavior, should return correct feature count scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_ShouldIncludeAvailabilityFeatures | Verifying that extract should include availability features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should include availability features | In scope: Extract behavior, should include availability features scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldIncludeDistanceFeatures | Verifying that extract should include distance features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should include distance features | In scope: Extract behavior, should include distance features scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Extract_ShouldIncludeSpecialtyFeatures | Verifying that extract should include specialty features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should include specialty features | In scope: Extract behavior, should include specialty features scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Extract_WithNullInput_ShouldReturnDefaults | Verifying that extract with null input returns defaults | Setup with null input -> Call Extract -> Assert return defaults | Extract with null input returns defaults | In scope: null input handling for Extract. Out of scope: valid input scenarios. |

## EnchiladaModelCategoricalSplitsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetSplit_WithValidCategory_ShouldReturnSplit | Verifying that get split with valid category returns split | Setup with valid category -> Call GetSplit -> Assert return split | GetSplit with valid category returns split | In scope: GetSplit behavior, with valid category scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetSplit_WithInvalidCategory_ShouldReturnDefault | Verifying that get split with invalid category returns default | Setup with invalid category -> Call GetSplit -> Assert return default | GetSplit with invalid category returns default | In scope: GetSplit behavior, with invalid category scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | AllSplits_ShouldBeValid | Verifying that all splits should be valid | Setup test data and mocks -> Call AllSplits -> Assert expected behavior of AllSplits | AllSplits should be valid | In scope: AllSplits behavior, should be valid scenario. Out of scope: other scenarios and methods not under test. |

## RevenueCalculatorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Calculate_WithStandardInput_ShouldReturnRevenue | Verifying that calculate with standard input returns revenue | Setup with standard input -> Call Calculate -> Assert return revenue | Calculate with standard input returns revenue | In scope: Calculate behavior, with standard input scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Calculate_WithZeroBookings_ShouldReturnZero | Verifying that calculate with zero bookings returns zero | Setup with zero bookings -> Call Calculate -> Assert return zero | Calculate with zero bookings returns zero | In scope: Calculate behavior, with zero bookings scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Calculate_WithNegativeValues_ShouldHandleGracefully | Verifying that calculate with negative values handle gracefully | Setup with negative values -> Call Calculate -> Assert handle gracefully | Calculate with negative values handle gracefully | In scope: Calculate behavior, with negative values scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Calculate_ShouldIncludeSpoRevenue | Verifying that calculate should include spo revenue | Setup test data and mocks -> Call Calculate -> Assert expected behavior of Calculate | Calculate should include spo revenue | In scope: Calculate behavior, should include spo revenue scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Calculate_ShouldIncludeOrganicRevenue | Verifying that calculate should include organic revenue | Setup test data and mocks -> Call Calculate -> Assert expected behavior of Calculate | Calculate should include organic revenue | In scope: Calculate behavior, should include organic revenue scenario. Out of scope: other scenarios and methods not under test. |

## RevenueResultTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | TotalRevenue_ShouldSumComponents | Verifying that total revenue should sum components | Setup test data and mocks -> Call TotalRevenue -> Assert expected behavior of TotalRevenue | TotalRevenue should sum components | In scope: TotalRevenue behavior, should sum components scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Properties_CanBeZero | Verifying that properties can be zero | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties can be zero | In scope: Properties behavior, can be zero scenario. Out of scope: other scenarios and methods not under test. |

## V2CalculationDetailsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Breakdown_ShouldContainAllComponents | Verifying that breakdown should contain all components | Setup test data and mocks -> Call Breakdown -> Assert expected behavior of Breakdown | Breakdown should contain all components | In scope: Breakdown behavior, should contain all components scenario. Out of scope: other scenarios and methods not under test. |

# Search/Es

## Es7ClientPreferenceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetPreference_WithDefaultConfig_ShouldReturnPrimary | Verifying that get preference with default config returns primary | Setup with default config -> Call GetPreference -> Assert return primary | GetPreference with default config returns primary | In scope: GetPreference behavior, with default config scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetPreference_WithFailoverConfig_ShouldReturnSecondary | Verifying that get preference with failover config returns secondary | Setup mock to throw exception -> Call GetPreference -> Assert return secondary | GetPreference with failover config returns secondary | In scope: error handling in GetPreference. Out of scope: successful execution paths. |
| 3 | | GetPreference_ShouldRespectConfigChanges | Verifying that get preference should respect config changes | Setup test data and mocks -> Call GetPreference -> Assert expected behavior of GetPreference | GetPreference should respect config changes | In scope: GetPreference behavior, should respect config changes scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetPreference_WithNullConfig_ShouldReturnDefault | Verifying that get preference with null config returns default | Setup with null input -> Call GetPreference -> Assert return default | GetPreference with null config returns default | In scope: null input handling for GetPreference. Out of scope: valid input scenarios. |
| 5 | | GetPreference_ShouldCacheResult | Verifying that get preference should cache result | Setup test data and mocks -> Call GetPreference -> Assert expected behavior of GetPreference | GetPreference should cache result | In scope: GetPreference behavior, should cache result scenario. Out of scope: other scenarios and methods not under test. |

## Es7ClientTracingTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Trace_ShouldRecordRequestDuration | Verifying that trace should record request duration | Setup test data and mocks -> Call Trace -> Assert expected behavior of Trace | Trace should record request duration | In scope: Trace behavior, should record request duration scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Trace_ShouldRecordRequestPath | Verifying that trace should record request path | Setup test data and mocks -> Call Trace -> Assert expected behavior of Trace | Trace should record request path | In scope: Trace behavior, should record request path scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Trace_ShouldRecordResponseStatus | Verifying that trace should record response status | Setup test data and mocks -> Call Trace -> Assert expected behavior of Trace | Trace should record response status | In scope: Trace behavior, should record response status scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Trace_ShouldRecordErrorDetails | Verifying that trace should record error details | Setup mock to throw exception -> Call Trace -> Assert expected behavior of Trace | Trace should record error details | In scope: error handling in Trace. Out of scope: successful execution paths. |
| 5 | | Trace_WithNullResponse_ShouldRecordError | Verifying that trace with null response record error | Setup with null input -> Call Trace -> Assert record error | Trace with null response record error | In scope: null input handling for Trace. Out of scope: valid input scenarios. |
| 6 | | Trace_ShouldIncludeCorrelationId | Verifying that trace should include correlation id | Setup test data and mocks -> Call Trace -> Assert expected behavior of Trace | Trace should include correlation id | In scope: Trace behavior, should include correlation id scenario. Out of scope: other scenarios and methods not under test. |

## Es7StatsDClientTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | RecordQuery_ShouldEmitLatencyMetric | Verifying that record query should emit latency metric | Setup test data and mocks -> Call RecordQuery -> Assert expected behavior of RecordQuery | RecordQuery should emit latency metric | In scope: RecordQuery behavior, should emit latency metric scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | RecordQuery_ShouldEmitCountMetric | Verifying that record query should emit count metric | Setup test data and mocks -> Call RecordQuery -> Assert expected behavior of RecordQuery | RecordQuery should emit count metric | In scope: RecordQuery behavior, should emit count metric scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | RecordQuery_ShouldIncludeTags | Verifying that record query should include tags | Setup test data and mocks -> Call RecordQuery -> Assert expected behavior of RecordQuery | RecordQuery should include tags | In scope: RecordQuery behavior, should include tags scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | RecordQuery_WithError_ShouldEmitErrorMetric | Verifying that record query with error emit error metric | Setup mock to throw exception -> Call RecordQuery -> Assert emit error metric | RecordQuery with error emit error metric | In scope: error handling in RecordQuery. Out of scope: successful execution paths. |

## IndexesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetIndex_ShouldReturnCorrectName | Verifying that get index should return correct name | Setup test data and mocks -> Call GetIndex -> Assert expected behavior of GetIndex | GetIndex should return correct name | In scope: GetIndex behavior, should return correct name scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetIndex_WithAlias_ShouldResolveAlias | Verifying that get index with alias resolve alias | Setup with alias -> Call GetIndex -> Assert resolve alias | GetIndex with alias resolve alias | In scope: GetIndex behavior, with alias scenario. Out of scope: other scenarios and methods not under test. |

## QueryAugmentersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Augment_ShouldAddBoostToQuery | Verifying that augment should add boost to query | Setup test data and mocks -> Call Augment -> Assert expected behavior of Augment | Augment should add boost to query | In scope: Augment behavior, should add boost to query scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Augment_ShouldAddFilterToQuery | Verifying that augment should add filter to query | Setup test data and mocks -> Call Augment -> Assert expected behavior of Augment | Augment should add filter to query | In scope: Augment behavior, should add filter to query scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Augment_WithNullQuery_ShouldReturnOriginal | Verifying that augment with null query returns original | Setup with null input -> Call Augment -> Assert return original | Augment with null query returns original | In scope: null input handling for Augment. Out of scope: valid input scenarios. |

## QueryableFieldMappingTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetMapping_WithKnownField_ShouldReturnMapping | Verifying that get mapping with known field returns mapping | Setup with known field -> Call GetMapping -> Assert return mapping | GetMapping with known field returns mapping | In scope: GetMapping behavior, with known field scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetMapping_WithUnknownField_ShouldReturnNull | Verifying that get mapping with unknown field returns null | Setup with unknown field -> Call GetMapping -> Assert returns null | GetMapping with unknown field returns null | In scope: GetMapping behavior, with unknown field scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetMapping_ShouldBeCaseInsensitive | Verifying that get mapping should be case insensitive | Setup test data and mocks -> Call GetMapping -> Assert expected behavior of GetMapping | GetMapping should be case insensitive | In scope: GetMapping behavior, should be case insensitive scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AllMappings_ShouldBeDistinct | Verifying that all mappings should be distinct | Setup test data and mocks -> Call AllMappings -> Assert expected behavior of AllMappings | AllMappings should be distinct | In scope: AllMappings behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetMapping_WithNullField_ShouldReturnNull | Verifying that get mapping with null field returns null | Setup with null input -> Call GetMapping -> Assert returns null | GetMapping with null field returns null | In scope: null input handling for GetMapping. Out of scope: valid input scenarios. |
| 6 | | FieldCount_ShouldMatchExpected | Verifying that field count should match expected | Setup test data and mocks -> Call FieldCount -> Assert expected behavior of FieldCount | FieldCount should match expected | In scope: FieldCount behavior, should match expected scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetMapping_ShouldReturnCorrectType | Verifying that get mapping should return correct type | Setup test data and mocks -> Call GetMapping -> Assert expected behavior of GetMapping | GetMapping should return correct type | In scope: GetMapping behavior, should return correct type scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetMapping_ShouldReturnCorrectAnalyzer | Verifying that get mapping should return correct analyzer | Setup test data and mocks -> Call GetMapping -> Assert expected behavior of GetMapping | GetMapping should return correct analyzer | In scope: GetMapping behavior, should return correct analyzer scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetMapping_ShouldHandleNestedFields | Verifying that get mapping should handle nested fields | Setup test data and mocks -> Call GetMapping -> Assert expected behavior of GetMapping | GetMapping should handle nested fields | In scope: GetMapping behavior, should handle nested fields scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | AllMappings_ShouldHaveNonNullValues | Verifying that all mappings should have non null values | Setup with null input -> Call AllMappings -> Assert expected behavior of AllMappings | AllMappings should have non null values | In scope: null input handling for AllMappings. Out of scope: valid input scenarios. |

## YassPayloadAugmenterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Augment_ShouldAddPayloadFields | Verifying that augment should add payload fields | Setup test data and mocks -> Call Augment -> Assert expected behavior of Augment | Augment should add payload fields | In scope: Augment behavior, should add payload fields scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Augment_WithNullPayload_ShouldReturnOriginal | Verifying that augment with null payload returns original | Setup with null input -> Call Augment -> Assert return original | Augment with null payload returns original | In scope: null input handling for Augment. Out of scope: valid input scenarios. |

# Search/Es/Filtering

## AcceptedInsuranceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingAcceptedInsurance_ShouldIncludeResult | Verifying that filter with matching accepted insurance include result | Setup with matching accepted insurance -> Call Filter -> Assert include result | Filter with matching accepted insurance include result | In scope: Filter behavior, with matching accepted insurance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingAcceptedInsurance_ShouldExcludeResult | Verifying that filter with non matching accepted insurance exclude result | Setup with non matching accepted insurance -> Call Filter -> Assert exclude result | Filter with non matching accepted insurance exclude result | In scope: Filter behavior, with non matching accepted insurance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullAcceptedInsurance_ShouldHandleGracefully | Verifying that filter with null accepted insurance handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null accepted insurance handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ActiveListingFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingActiveListing_ShouldIncludeResult | Verifying that filter with matching active listing include result | Setup with matching active listing -> Call Filter -> Assert include result | Filter with matching active listing include result | In scope: Filter behavior, with matching active listing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingActiveListing_ShouldExcludeResult | Verifying that filter with non matching active listing exclude result | Setup with non matching active listing -> Call Filter -> Assert exclude result | Filter with non matching active listing exclude result | In scope: Filter behavior, with non matching active listing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullActiveListing_ShouldHandleGracefully | Verifying that filter with null active listing handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null active listing handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## AdultOnlyFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingAdultOnly_ShouldIncludeResult | Verifying that filter with matching adult only include result | Setup with matching adult only -> Call Filter -> Assert include result | Filter with matching adult only include result | In scope: Filter behavior, with matching adult only scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingAdultOnly_ShouldExcludeResult | Verifying that filter with non matching adult only exclude result | Setup with non matching adult only -> Call Filter -> Assert exclude result | Filter with non matching adult only exclude result | In scope: Filter behavior, with non matching adult only scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullAdultOnly_ShouldHandleGracefully | Verifying that filter with null adult only handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null adult only handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## AgeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingAge_ShouldIncludeResult | Verifying that filter with matching age include result | Setup with matching age -> Call Filter -> Assert include result | Filter with matching age include result | In scope: Filter behavior, with matching age scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingAge_ShouldExcludeResult | Verifying that filter with non matching age exclude result | Setup with non matching age -> Call Filter -> Assert exclude result | Filter with non matching age exclude result | In scope: Filter behavior, with non matching age scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullAge_ShouldHandleGracefully | Verifying that filter with null age handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null age handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## AppointmentTypeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingAppointmentType_ShouldIncludeResult | Verifying that filter with matching appointment type include result | Setup with matching appointment type -> Call Filter -> Assert include result | Filter with matching appointment type include result | In scope: Filter behavior, with matching appointment type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingAppointmentType_ShouldExcludeResult | Verifying that filter with non matching appointment type exclude result | Setup with non matching appointment type -> Call Filter -> Assert exclude result | Filter with non matching appointment type exclude result | In scope: Filter behavior, with non matching appointment type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullAppointmentType_ShouldHandleGracefully | Verifying that filter with null appointment type handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null appointment type handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## AvailabilityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingAvailability_ShouldIncludeResult | Verifying that filter with matching availability include result | Setup with matching availability -> Call Filter -> Assert include result | Filter with matching availability include result | In scope: Filter behavior, with matching availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingAvailability_ShouldExcludeResult | Verifying that filter with non matching availability exclude result | Setup with non matching availability -> Call Filter -> Assert exclude result | Filter with non matching availability exclude result | In scope: Filter behavior, with non matching availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullAvailability_ShouldHandleGracefully | Verifying that filter with null availability handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null availability handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## BillingTypeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingBillingType_ShouldIncludeResult | Verifying that filter with matching billing type include result | Setup with matching billing type -> Call Filter -> Assert include result | Filter with matching billing type include result | In scope: Filter behavior, with matching billing type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingBillingType_ShouldExcludeResult | Verifying that filter with non matching billing type exclude result | Setup with non matching billing type -> Call Filter -> Assert exclude result | Filter with non matching billing type exclude result | In scope: Filter behavior, with non matching billing type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullBillingType_ShouldHandleGracefully | Verifying that filter with null billing type handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null billing type handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## BoardCertifiedFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingBoardCertified_ShouldIncludeResult | Verifying that filter with matching board certified include result | Setup with matching board certified -> Call Filter -> Assert include result | Filter with matching board certified include result | In scope: Filter behavior, with matching board certified scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingBoardCertified_ShouldExcludeResult | Verifying that filter with non matching board certified exclude result | Setup with non matching board certified -> Call Filter -> Assert exclude result | Filter with non matching board certified exclude result | In scope: Filter behavior, with non matching board certified scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullBoardCertified_ShouldHandleGracefully | Verifying that filter with null board certified handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null board certified handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## BookableOnlyFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingBookableOnly_ShouldIncludeResult | Verifying that filter with matching bookable only include result | Setup with matching bookable only -> Call Filter -> Assert include result | Filter with matching bookable only include result | In scope: Filter behavior, with matching bookable only scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingBookableOnly_ShouldExcludeResult | Verifying that filter with non matching bookable only exclude result | Setup with non matching bookable only -> Call Filter -> Assert exclude result | Filter with non matching bookable only exclude result | In scope: Filter behavior, with non matching bookable only scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullBookableOnly_ShouldHandleGracefully | Verifying that filter with null bookable only handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null bookable only handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## BookingWindowFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingBookingWindow_ShouldIncludeResult | Verifying that filter with matching booking window include result | Setup with matching booking window -> Call Filter -> Assert include result | Filter with matching booking window include result | In scope: Filter behavior, with matching booking window scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingBookingWindow_ShouldExcludeResult | Verifying that filter with non matching booking window exclude result | Setup with non matching booking window -> Call Filter -> Assert exclude result | Filter with non matching booking window exclude result | In scope: Filter behavior, with non matching booking window scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullBookingWindow_ShouldHandleGracefully | Verifying that filter with null booking window handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null booking window handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## BrandFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingBrand_ShouldIncludeResult | Verifying that filter with matching brand include result | Setup with matching brand -> Call Filter -> Assert include result | Filter with matching brand include result | In scope: Filter behavior, with matching brand scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingBrand_ShouldExcludeResult | Verifying that filter with non matching brand exclude result | Setup with non matching brand -> Call Filter -> Assert exclude result | Filter with non matching brand exclude result | In scope: Filter behavior, with non matching brand scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullBrand_ShouldHandleGracefully | Verifying that filter with null brand handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null brand handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## CashPriceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingCashPrice_ShouldIncludeResult | Verifying that filter with matching cash price include result | Setup with matching cash price -> Call Filter -> Assert include result | Filter with matching cash price include result | In scope: Filter behavior, with matching cash price scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingCashPrice_ShouldExcludeResult | Verifying that filter with non matching cash price exclude result | Setup with non matching cash price -> Call Filter -> Assert exclude result | Filter with non matching cash price exclude result | In scope: Filter behavior, with non matching cash price scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullCashPrice_ShouldHandleGracefully | Verifying that filter with null cash price handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null cash price handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## CityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingCity_ShouldIncludeResult | Verifying that filter with matching city include result | Setup with matching city -> Call Filter -> Assert include result | Filter with matching city include result | In scope: Filter behavior, with matching city scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingCity_ShouldExcludeResult | Verifying that filter with non matching city exclude result | Setup with non matching city -> Call Filter -> Assert exclude result | Filter with non matching city exclude result | In scope: Filter behavior, with non matching city scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullCity_ShouldHandleGracefully | Verifying that filter with null city handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null city handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ClinicTypeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingClinicType_ShouldIncludeResult | Verifying that filter with matching clinic type include result | Setup with matching clinic type -> Call Filter -> Assert include result | Filter with matching clinic type include result | In scope: Filter behavior, with matching clinic type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingClinicType_ShouldExcludeResult | Verifying that filter with non matching clinic type exclude result | Setup with non matching clinic type -> Call Filter -> Assert exclude result | Filter with non matching clinic type exclude result | In scope: Filter behavior, with non matching clinic type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullClinicType_ShouldHandleGracefully | Verifying that filter with null clinic type handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null clinic type handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ClinicalTrialFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingClinicalTrial_ShouldIncludeResult | Verifying that filter with matching clinical trial include result | Setup with matching clinical trial -> Call Filter -> Assert include result | Filter with matching clinical trial include result | In scope: Filter behavior, with matching clinical trial scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingClinicalTrial_ShouldExcludeResult | Verifying that filter with non matching clinical trial exclude result | Setup with non matching clinical trial -> Call Filter -> Assert exclude result | Filter with non matching clinical trial exclude result | In scope: Filter behavior, with non matching clinical trial scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullClinicalTrial_ShouldHandleGracefully | Verifying that filter with null clinical trial handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null clinical trial handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ConditionTreatedFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingConditionTreated_ShouldIncludeResult | Verifying that filter with matching condition treated include result | Setup with matching condition treated -> Call Filter -> Assert include result | Filter with matching condition treated include result | In scope: Filter behavior, with matching condition treated scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingConditionTreated_ShouldExcludeResult | Verifying that filter with non matching condition treated exclude result | Setup with non matching condition treated -> Call Filter -> Assert exclude result | Filter with non matching condition treated exclude result | In scope: Filter behavior, with non matching condition treated scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullConditionTreated_ShouldHandleGracefully | Verifying that filter with null condition treated handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null condition treated handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ContinuousCareFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingContinuousCare_ShouldIncludeResult | Verifying that filter with matching continuous care include result | Setup with matching continuous care -> Call Filter -> Assert include result | Filter with matching continuous care include result | In scope: Filter behavior, with matching continuous care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingContinuousCare_ShouldExcludeResult | Verifying that filter with non matching continuous care exclude result | Setup with non matching continuous care -> Call Filter -> Assert exclude result | Filter with non matching continuous care exclude result | In scope: Filter behavior, with non matching continuous care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullContinuousCare_ShouldHandleGracefully | Verifying that filter with null continuous care handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null continuous care handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## CoordinateFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingCoordinate_ShouldIncludeResult | Verifying that filter with matching coordinate include result | Setup with matching coordinate -> Call Filter -> Assert include result | Filter with matching coordinate include result | In scope: Filter behavior, with matching coordinate scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingCoordinate_ShouldExcludeResult | Verifying that filter with non matching coordinate exclude result | Setup with non matching coordinate -> Call Filter -> Assert exclude result | Filter with non matching coordinate exclude result | In scope: Filter behavior, with non matching coordinate scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullCoordinate_ShouldHandleGracefully | Verifying that filter with null coordinate handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null coordinate handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## CostPlanFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingCostPlan_ShouldIncludeResult | Verifying that filter with matching cost plan include result | Setup with matching cost plan -> Call Filter -> Assert include result | Filter with matching cost plan include result | In scope: Filter behavior, with matching cost plan scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingCostPlan_ShouldExcludeResult | Verifying that filter with non matching cost plan exclude result | Setup with non matching cost plan -> Call Filter -> Assert exclude result | Filter with non matching cost plan exclude result | In scope: Filter behavior, with non matching cost plan scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullCostPlan_ShouldHandleGracefully | Verifying that filter with null cost plan handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null cost plan handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## Covid19TestingFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingCovid19Testing_ShouldIncludeResult | Verifying that filter with matching covid19 testing include result | Setup with matching covid19 testing -> Call Filter -> Assert include result | Filter with matching covid19 testing include result | In scope: Filter behavior, with matching covid19 testing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingCovid19Testing_ShouldExcludeResult | Verifying that filter with non matching covid19 testing exclude result | Setup with non matching covid19 testing -> Call Filter -> Assert exclude result | Filter with non matching covid19 testing exclude result | In scope: Filter behavior, with non matching covid19 testing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullCovid19Testing_ShouldHandleGracefully | Verifying that filter with null covid19 testing handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null covid19 testing handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DateFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDate_ShouldIncludeResult | Verifying that filter with matching date include result | Setup with matching date -> Call Filter -> Assert include result | Filter with matching date include result | In scope: Filter behavior, with matching date scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDate_ShouldExcludeResult | Verifying that filter with non matching date exclude result | Setup with non matching date -> Call Filter -> Assert exclude result | Filter with non matching date exclude result | In scope: Filter behavior, with non matching date scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDate_ShouldHandleGracefully | Verifying that filter with null date handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null date handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DentalProcedureFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDentalProcedure_ShouldIncludeResult | Verifying that filter with matching dental procedure include result | Setup with matching dental procedure -> Call Filter -> Assert include result | Filter with matching dental procedure include result | In scope: Filter behavior, with matching dental procedure scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDentalProcedure_ShouldExcludeResult | Verifying that filter with non matching dental procedure exclude result | Setup with non matching dental procedure -> Call Filter -> Assert exclude result | Filter with non matching dental procedure exclude result | In scope: Filter behavior, with non matching dental procedure scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDentalProcedure_ShouldHandleGracefully | Verifying that filter with null dental procedure handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null dental procedure handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DigitalHealthFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDigitalHealth_ShouldIncludeResult | Verifying that filter with matching digital health include result | Setup with matching digital health -> Call Filter -> Assert include result | Filter with matching digital health include result | In scope: Filter behavior, with matching digital health scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDigitalHealth_ShouldExcludeResult | Verifying that filter with non matching digital health exclude result | Setup with non matching digital health -> Call Filter -> Assert exclude result | Filter with non matching digital health exclude result | In scope: Filter behavior, with non matching digital health scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDigitalHealth_ShouldHandleGracefully | Verifying that filter with null digital health handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null digital health handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DirectoryListingFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDirectoryListing_ShouldIncludeResult | Verifying that filter with matching directory listing include result | Setup with matching directory listing -> Call Filter -> Assert include result | Filter with matching directory listing include result | In scope: Filter behavior, with matching directory listing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDirectoryListing_ShouldExcludeResult | Verifying that filter with non matching directory listing exclude result | Setup with non matching directory listing -> Call Filter -> Assert exclude result | Filter with non matching directory listing exclude result | In scope: Filter behavior, with non matching directory listing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDirectoryListing_ShouldHandleGracefully | Verifying that filter with null directory listing handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null directory listing handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DistanceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDistance_ShouldIncludeResult | Verifying that filter with matching distance include result | Setup with matching distance -> Call Filter -> Assert include result | Filter with matching distance include result | In scope: Filter behavior, with matching distance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDistance_ShouldExcludeResult | Verifying that filter with non matching distance exclude result | Setup with non matching distance -> Call Filter -> Assert exclude result | Filter with non matching distance exclude result | In scope: Filter behavior, with non matching distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDistance_ShouldHandleGracefully | Verifying that filter with null distance handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null distance handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DiversityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDiversity_ShouldIncludeResult | Verifying that filter with matching diversity include result | Setup with matching diversity -> Call Filter -> Assert include result | Filter with matching diversity include result | In scope: Filter behavior, with matching diversity scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDiversity_ShouldExcludeResult | Verifying that filter with non matching diversity exclude result | Setup with non matching diversity -> Call Filter -> Assert exclude result | Filter with non matching diversity exclude result | In scope: Filter behavior, with non matching diversity scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDiversity_ShouldHandleGracefully | Verifying that filter with null diversity handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null diversity handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## DrugScreeningFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingDrugScreening_ShouldIncludeResult | Verifying that filter with matching drug screening include result | Setup with matching drug screening -> Call Filter -> Assert include result | Filter with matching drug screening include result | In scope: Filter behavior, with matching drug screening scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingDrugScreening_ShouldExcludeResult | Verifying that filter with non matching drug screening exclude result | Setup with non matching drug screening -> Call Filter -> Assert exclude result | Filter with non matching drug screening exclude result | In scope: Filter behavior, with non matching drug screening scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullDrugScreening_ShouldHandleGracefully | Verifying that filter with null drug screening handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null drug screening handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## EhrIntegrationFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingEhrIntegration_ShouldIncludeResult | Verifying that filter with matching ehr integration include result | Setup with matching ehr integration -> Call Filter -> Assert include result | Filter with matching ehr integration include result | In scope: Filter behavior, with matching ehr integration scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingEhrIntegration_ShouldExcludeResult | Verifying that filter with non matching ehr integration exclude result | Setup with non matching ehr integration -> Call Filter -> Assert exclude result | Filter with non matching ehr integration exclude result | In scope: Filter behavior, with non matching ehr integration scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullEhrIntegration_ShouldHandleGracefully | Verifying that filter with null ehr integration handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null ehr integration handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## EmergencyServiceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingEmergencyService_ShouldIncludeResult | Verifying that filter with matching emergency service include result | Setup with matching emergency service -> Call Filter -> Assert include result | Filter with matching emergency service include result | In scope: Filter behavior, with matching emergency service scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingEmergencyService_ShouldExcludeResult | Verifying that filter with non matching emergency service exclude result | Setup with non matching emergency service -> Call Filter -> Assert exclude result | Filter with non matching emergency service exclude result | In scope: Filter behavior, with non matching emergency service scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullEmergencyService_ShouldHandleGracefully | Verifying that filter with null emergency service handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null emergency service handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## EnterpriseFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingEnterprise_ShouldIncludeResult | Verifying that filter with matching enterprise include result | Setup with matching enterprise -> Call Filter -> Assert include result | Filter with matching enterprise include result | In scope: Filter behavior, with matching enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingEnterprise_ShouldExcludeResult | Verifying that filter with non matching enterprise exclude result | Setup with non matching enterprise -> Call Filter -> Assert exclude result | Filter with non matching enterprise exclude result | In scope: Filter behavior, with non matching enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullEnterprise_ShouldHandleGracefully | Verifying that filter with null enterprise handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null enterprise handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## EthnicityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingEthnicity_ShouldIncludeResult | Verifying that filter with matching ethnicity include result | Setup with matching ethnicity -> Call Filter -> Assert include result | Filter with matching ethnicity include result | In scope: Filter behavior, with matching ethnicity scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingEthnicity_ShouldExcludeResult | Verifying that filter with non matching ethnicity exclude result | Setup with non matching ethnicity -> Call Filter -> Assert exclude result | Filter with non matching ethnicity exclude result | In scope: Filter behavior, with non matching ethnicity scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullEthnicity_ShouldHandleGracefully | Verifying that filter with null ethnicity handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null ethnicity handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ExcludeProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingExcludeProvider_ShouldIncludeResult | Verifying that filter with matching exclude provider include result | Setup with matching exclude provider -> Call Filter -> Assert include result | Filter with matching exclude provider include result | In scope: Filter behavior, with matching exclude provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingExcludeProvider_ShouldExcludeResult | Verifying that filter with non matching exclude provider exclude result | Setup with non matching exclude provider -> Call Filter -> Assert exclude result | Filter with non matching exclude provider exclude result | In scope: Filter behavior, with non matching exclude provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullExcludeProvider_ShouldHandleGracefully | Verifying that filter with null exclude provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null exclude provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ExternalProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingExternalProvider_ShouldIncludeResult | Verifying that filter with matching external provider include result | Setup with matching external provider -> Call Filter -> Assert include result | Filter with matching external provider include result | In scope: Filter behavior, with matching external provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingExternalProvider_ShouldExcludeResult | Verifying that filter with non matching external provider exclude result | Setup with non matching external provider -> Call Filter -> Assert exclude result | Filter with non matching external provider exclude result | In scope: Filter behavior, with non matching external provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullExternalProvider_ShouldHandleGracefully | Verifying that filter with null external provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null external provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## FacetFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingFacet_ShouldIncludeResult | Verifying that filter with matching facet include result | Setup with matching facet -> Call Filter -> Assert include result | Filter with matching facet include result | In scope: Filter behavior, with matching facet scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingFacet_ShouldExcludeResult | Verifying that filter with non matching facet exclude result | Setup with non matching facet -> Call Filter -> Assert exclude result | Filter with non matching facet exclude result | In scope: Filter behavior, with non matching facet scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullFacet_ShouldHandleGracefully | Verifying that filter with null facet handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null facet handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## FeaturedProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingFeaturedProvider_ShouldIncludeResult | Verifying that filter with matching featured provider include result | Setup with matching featured provider -> Call Filter -> Assert include result | Filter with matching featured provider include result | In scope: Filter behavior, with matching featured provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingFeaturedProvider_ShouldExcludeResult | Verifying that filter with non matching featured provider exclude result | Setup with non matching featured provider -> Call Filter -> Assert exclude result | Filter with non matching featured provider exclude result | In scope: Filter behavior, with non matching featured provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullFeaturedProvider_ShouldHandleGracefully | Verifying that filter with null featured provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null featured provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## FemaleProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingFemaleProvider_ShouldIncludeResult | Verifying that filter with matching female provider include result | Setup with matching female provider -> Call Filter -> Assert include result | Filter with matching female provider include result | In scope: Filter behavior, with matching female provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingFemaleProvider_ShouldExcludeResult | Verifying that filter with non matching female provider exclude result | Setup with non matching female provider -> Call Filter -> Assert exclude result | Filter with non matching female provider exclude result | In scope: Filter behavior, with non matching female provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullFemaleProvider_ShouldHandleGracefully | Verifying that filter with null female provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null female provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## FluShotFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingFluShot_ShouldIncludeResult | Verifying that filter with matching flu shot include result | Setup with matching flu shot -> Call Filter -> Assert include result | Filter with matching flu shot include result | In scope: Filter behavior, with matching flu shot scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingFluShot_ShouldExcludeResult | Verifying that filter with non matching flu shot exclude result | Setup with non matching flu shot -> Call Filter -> Assert exclude result | Filter with non matching flu shot exclude result | In scope: Filter behavior, with non matching flu shot scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullFluShot_ShouldHandleGracefully | Verifying that filter with null flu shot handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null flu shot handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## GenderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingGender_ShouldIncludeResult | Verifying that filter with matching gender include result | Setup with matching gender -> Call Filter -> Assert include result | Filter with matching gender include result | In scope: Filter behavior, with matching gender scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingGender_ShouldExcludeResult | Verifying that filter with non matching gender exclude result | Setup with non matching gender -> Call Filter -> Assert exclude result | Filter with non matching gender exclude result | In scope: Filter behavior, with non matching gender scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullGender_ShouldHandleGracefully | Verifying that filter with null gender handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null gender handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## GeoDistanceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingGeoDistance_ShouldIncludeResult | Verifying that filter with matching geo distance include result | Setup with matching geo distance -> Call Filter -> Assert include result | Filter with matching geo distance include result | In scope: Filter behavior, with matching geo distance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingGeoDistance_ShouldExcludeResult | Verifying that filter with non matching geo distance exclude result | Setup with non matching geo distance -> Call Filter -> Assert exclude result | Filter with non matching geo distance exclude result | In scope: Filter behavior, with non matching geo distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullGeoDistance_ShouldHandleGracefully | Verifying that filter with null geo distance handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null geo distance handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## GeriatricCareFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingGeriatricCare_ShouldIncludeResult | Verifying that filter with matching geriatric care include result | Setup with matching geriatric care -> Call Filter -> Assert include result | Filter with matching geriatric care include result | In scope: Filter behavior, with matching geriatric care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingGeriatricCare_ShouldExcludeResult | Verifying that filter with non matching geriatric care exclude result | Setup with non matching geriatric care -> Call Filter -> Assert exclude result | Filter with non matching geriatric care exclude result | In scope: Filter behavior, with non matching geriatric care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullGeriatricCare_ShouldHandleGracefully | Verifying that filter with null geriatric care handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null geriatric care handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## GroupPracticeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingGroupPractice_ShouldIncludeResult | Verifying that filter with matching group practice include result | Setup with matching group practice -> Call Filter -> Assert include result | Filter with matching group practice include result | In scope: Filter behavior, with matching group practice scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingGroupPractice_ShouldExcludeResult | Verifying that filter with non matching group practice exclude result | Setup with non matching group practice -> Call Filter -> Assert exclude result | Filter with non matching group practice exclude result | In scope: Filter behavior, with non matching group practice scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullGroupPractice_ShouldHandleGracefully | Verifying that filter with null group practice handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null group practice handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## GroupVisitFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingGroupVisit_ShouldIncludeResult | Verifying that filter with matching group visit include result | Setup with matching group visit -> Call Filter -> Assert include result | Filter with matching group visit include result | In scope: Filter behavior, with matching group visit scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingGroupVisit_ShouldExcludeResult | Verifying that filter with non matching group visit exclude result | Setup with non matching group visit -> Call Filter -> Assert exclude result | Filter with non matching group visit exclude result | In scope: Filter behavior, with non matching group visit scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullGroupVisit_ShouldHandleGracefully | Verifying that filter with null group visit handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null group visit handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HasPhotoFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHasPhoto_ShouldIncludeResult | Verifying that filter with matching has photo include result | Setup with matching has photo -> Call Filter -> Assert include result | Filter with matching has photo include result | In scope: Filter behavior, with matching has photo scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHasPhoto_ShouldExcludeResult | Verifying that filter with non matching has photo exclude result | Setup with non matching has photo -> Call Filter -> Assert exclude result | Filter with non matching has photo exclude result | In scope: Filter behavior, with non matching has photo scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHasPhoto_ShouldHandleGracefully | Verifying that filter with null has photo handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null has photo handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HasReviewFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHasReview_ShouldIncludeResult | Verifying that filter with matching has review include result | Setup with matching has review -> Call Filter -> Assert include result | Filter with matching has review include result | In scope: Filter behavior, with matching has review scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHasReview_ShouldExcludeResult | Verifying that filter with non matching has review exclude result | Setup with non matching has review -> Call Filter -> Assert exclude result | Filter with non matching has review exclude result | In scope: Filter behavior, with non matching has review scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHasReview_ShouldHandleGracefully | Verifying that filter with null has review handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null has review handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HealthSystemFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHealthSystem_ShouldIncludeResult | Verifying that filter with matching health system include result | Setup with matching health system -> Call Filter -> Assert include result | Filter with matching health system include result | In scope: Filter behavior, with matching health system scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHealthSystem_ShouldExcludeResult | Verifying that filter with non matching health system exclude result | Setup with non matching health system -> Call Filter -> Assert exclude result | Filter with non matching health system exclude result | In scope: Filter behavior, with non matching health system scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHealthSystem_ShouldHandleGracefully | Verifying that filter with null health system handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null health system handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HearingTestFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHearingTest_ShouldIncludeResult | Verifying that filter with matching hearing test include result | Setup with matching hearing test -> Call Filter -> Assert include result | Filter with matching hearing test include result | In scope: Filter behavior, with matching hearing test scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHearingTest_ShouldExcludeResult | Verifying that filter with non matching hearing test exclude result | Setup with non matching hearing test -> Call Filter -> Assert exclude result | Filter with non matching hearing test exclude result | In scope: Filter behavior, with non matching hearing test scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHearingTest_ShouldHandleGracefully | Verifying that filter with null hearing test handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null hearing test handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HighlyRatedFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHighlyRated_ShouldIncludeResult | Verifying that filter with matching highly rated include result | Setup with matching highly rated -> Call Filter -> Assert include result | Filter with matching highly rated include result | In scope: Filter behavior, with matching highly rated scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHighlyRated_ShouldExcludeResult | Verifying that filter with non matching highly rated exclude result | Setup with non matching highly rated -> Call Filter -> Assert exclude result | Filter with non matching highly rated exclude result | In scope: Filter behavior, with non matching highly rated scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHighlyRated_ShouldHandleGracefully | Verifying that filter with null highly rated handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null highly rated handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HomeVisitFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHomeVisit_ShouldIncludeResult | Verifying that filter with matching home visit include result | Setup with matching home visit -> Call Filter -> Assert include result | Filter with matching home visit include result | In scope: Filter behavior, with matching home visit scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHomeVisit_ShouldExcludeResult | Verifying that filter with non matching home visit exclude result | Setup with non matching home visit -> Call Filter -> Assert exclude result | Filter with non matching home visit exclude result | In scope: Filter behavior, with non matching home visit scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHomeVisit_ShouldHandleGracefully | Verifying that filter with null home visit handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null home visit handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## HospitalAffiliationFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingHospitalAffiliation_ShouldIncludeResult | Verifying that filter with matching hospital affiliation include result | Setup with matching hospital affiliation -> Call Filter -> Assert include result | Filter with matching hospital affiliation include result | In scope: Filter behavior, with matching hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingHospitalAffiliation_ShouldExcludeResult | Verifying that filter with non matching hospital affiliation exclude result | Setup with non matching hospital affiliation -> Call Filter -> Assert exclude result | Filter with non matching hospital affiliation exclude result | In scope: Filter behavior, with non matching hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullHospitalAffiliation_ShouldHandleGracefully | Verifying that filter with null hospital affiliation handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null hospital affiliation handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ImmediateAvailabilityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingImmediateAvailability_ShouldIncludeResult | Verifying that filter with matching immediate availability include result | Setup with matching immediate availability -> Call Filter -> Assert include result | Filter with matching immediate availability include result | In scope: Filter behavior, with matching immediate availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingImmediateAvailability_ShouldExcludeResult | Verifying that filter with non matching immediate availability exclude result | Setup with non matching immediate availability -> Call Filter -> Assert exclude result | Filter with non matching immediate availability exclude result | In scope: Filter behavior, with non matching immediate availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullImmediateAvailability_ShouldHandleGracefully | Verifying that filter with null immediate availability handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null immediate availability handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## InPersonVisitFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingInPersonVisit_ShouldIncludeResult | Verifying that filter with matching in person visit include result | Setup with matching in person visit -> Call Filter -> Assert include result | Filter with matching in person visit include result | In scope: Filter behavior, with matching in person visit scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingInPersonVisit_ShouldExcludeResult | Verifying that filter with non matching in person visit exclude result | Setup with non matching in person visit -> Call Filter -> Assert exclude result | Filter with non matching in person visit exclude result | In scope: Filter behavior, with non matching in person visit scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullInPersonVisit_ShouldHandleGracefully | Verifying that filter with null in person visit handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null in person visit handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## InsuranceAcceptedFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingInsuranceAccepted_ShouldIncludeResult | Verifying that filter with matching insurance accepted include result | Setup with matching insurance accepted -> Call Filter -> Assert include result | Filter with matching insurance accepted include result | In scope: Filter behavior, with matching insurance accepted scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingInsuranceAccepted_ShouldExcludeResult | Verifying that filter with non matching insurance accepted exclude result | Setup with non matching insurance accepted -> Call Filter -> Assert exclude result | Filter with non matching insurance accepted exclude result | In scope: Filter behavior, with non matching insurance accepted scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullInsuranceAccepted_ShouldHandleGracefully | Verifying that filter with null insurance accepted handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null insurance accepted handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## JointCommissionFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingJointCommission_ShouldIncludeResult | Verifying that filter with matching joint commission include result | Setup with matching joint commission -> Call Filter -> Assert include result | Filter with matching joint commission include result | In scope: Filter behavior, with matching joint commission scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingJointCommission_ShouldExcludeResult | Verifying that filter with non matching joint commission exclude result | Setup with non matching joint commission -> Call Filter -> Assert exclude result | Filter with non matching joint commission exclude result | In scope: Filter behavior, with non matching joint commission scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullJointCommission_ShouldHandleGracefully | Verifying that filter with null joint commission handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null joint commission handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## LanguageFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingLanguage_ShouldIncludeResult | Verifying that filter with matching language include result | Setup with matching language -> Call Filter -> Assert include result | Filter with matching language include result | In scope: Filter behavior, with matching language scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingLanguage_ShouldExcludeResult | Verifying that filter with non matching language exclude result | Setup with non matching language -> Call Filter -> Assert exclude result | Filter with non matching language exclude result | In scope: Filter behavior, with non matching language scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullLanguage_ShouldHandleGracefully | Verifying that filter with null language handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null language handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## LateNightFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingLateNight_ShouldIncludeResult | Verifying that filter with matching late night include result | Setup with matching late night -> Call Filter -> Assert include result | Filter with matching late night include result | In scope: Filter behavior, with matching late night scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingLateNight_ShouldExcludeResult | Verifying that filter with non matching late night exclude result | Setup with non matching late night -> Call Filter -> Assert exclude result | Filter with non matching late night exclude result | In scope: Filter behavior, with non matching late night scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullLateNight_ShouldHandleGracefully | Verifying that filter with null late night handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null late night handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## LicenseTypeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingLicenseType_ShouldIncludeResult | Verifying that filter with matching license type include result | Setup with matching license type -> Call Filter -> Assert include result | Filter with matching license type include result | In scope: Filter behavior, with matching license type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingLicenseType_ShouldExcludeResult | Verifying that filter with non matching license type exclude result | Setup with non matching license type -> Call Filter -> Assert exclude result | Filter with non matching license type exclude result | In scope: Filter behavior, with non matching license type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullLicenseType_ShouldHandleGracefully | Verifying that filter with null license type handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null license type handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## LocationFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingLocation_ShouldIncludeResult | Verifying that filter with matching location include result | Setup with matching location -> Call Filter -> Assert include result | Filter with matching location include result | In scope: Filter behavior, with matching location scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingLocation_ShouldExcludeResult | Verifying that filter with non matching location exclude result | Setup with non matching location -> Call Filter -> Assert exclude result | Filter with non matching location exclude result | In scope: Filter behavior, with non matching location scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullLocation_ShouldHandleGracefully | Verifying that filter with null location handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null location handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## MentalHealthFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingMentalHealth_ShouldIncludeResult | Verifying that filter with matching mental health include result | Setup with matching mental health -> Call Filter -> Assert include result | Filter with matching mental health include result | In scope: Filter behavior, with matching mental health scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingMentalHealth_ShouldExcludeResult | Verifying that filter with non matching mental health exclude result | Setup with non matching mental health -> Call Filter -> Assert exclude result | Filter with non matching mental health exclude result | In scope: Filter behavior, with non matching mental health scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullMentalHealth_ShouldHandleGracefully | Verifying that filter with null mental health handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null mental health handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## MinRatingFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingMinRating_ShouldIncludeResult | Verifying that filter with matching min rating include result | Setup with matching min rating -> Call Filter -> Assert include result | Filter with matching min rating include result | In scope: Filter behavior, with matching min rating scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingMinRating_ShouldExcludeResult | Verifying that filter with non matching min rating exclude result | Setup with non matching min rating -> Call Filter -> Assert exclude result | Filter with non matching min rating exclude result | In scope: Filter behavior, with non matching min rating scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullMinRating_ShouldHandleGracefully | Verifying that filter with null min rating handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null min rating handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## MultiLocationFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingMultiLocation_ShouldIncludeResult | Verifying that filter with matching multi location include result | Setup with matching multi location -> Call Filter -> Assert include result | Filter with matching multi location include result | In scope: Filter behavior, with matching multi location scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingMultiLocation_ShouldExcludeResult | Verifying that filter with non matching multi location exclude result | Setup with non matching multi location -> Call Filter -> Assert exclude result | Filter with non matching multi location exclude result | In scope: Filter behavior, with non matching multi location scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullMultiLocation_ShouldHandleGracefully | Verifying that filter with null multi location handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null multi location handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## NearbyLocationFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingNearbyLocation_ShouldIncludeResult | Verifying that filter with matching nearby location include result | Setup with matching nearby location -> Call Filter -> Assert include result | Filter with matching nearby location include result | In scope: Filter behavior, with matching nearby location scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingNearbyLocation_ShouldExcludeResult | Verifying that filter with non matching nearby location exclude result | Setup with non matching nearby location -> Call Filter -> Assert exclude result | Filter with non matching nearby location exclude result | In scope: Filter behavior, with non matching nearby location scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullNearbyLocation_ShouldHandleGracefully | Verifying that filter with null nearby location handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null nearby location handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## NetworkFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingNetwork_ShouldIncludeResult | Verifying that filter with matching network include result | Setup with matching network -> Call Filter -> Assert include result | Filter with matching network include result | In scope: Filter behavior, with matching network scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingNetwork_ShouldExcludeResult | Verifying that filter with non matching network exclude result | Setup with non matching network -> Call Filter -> Assert exclude result | Filter with non matching network exclude result | In scope: Filter behavior, with non matching network scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullNetwork_ShouldHandleGracefully | Verifying that filter with null network handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null network handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## NewPatientFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingNewPatient_ShouldIncludeResult | Verifying that filter with matching new patient include result | Setup with matching new patient -> Call Filter -> Assert include result | Filter with matching new patient include result | In scope: Filter behavior, with matching new patient scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingNewPatient_ShouldExcludeResult | Verifying that filter with non matching new patient exclude result | Setup with non matching new patient -> Call Filter -> Assert exclude result | Filter with non matching new patient exclude result | In scope: Filter behavior, with non matching new patient scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullNewPatient_ShouldHandleGracefully | Verifying that filter with null new patient handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null new patient handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## NewProviderBoostFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingNewProviderBoost_ShouldIncludeResult | Verifying that filter with matching new provider boost include result | Setup with matching new provider boost -> Call Filter -> Assert include result | Filter with matching new provider boost include result | In scope: Filter behavior, with matching new provider boost scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingNewProviderBoost_ShouldExcludeResult | Verifying that filter with non matching new provider boost exclude result | Setup with non matching new provider boost -> Call Filter -> Assert exclude result | Filter with non matching new provider boost exclude result | In scope: Filter behavior, with non matching new provider boost scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullNewProviderBoost_ShouldHandleGracefully | Verifying that filter with null new provider boost handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null new provider boost handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## NextAvailableFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingNextAvailable_ShouldIncludeResult | Verifying that filter with matching next available include result | Setup with matching next available -> Call Filter -> Assert include result | Filter with matching next available include result | In scope: Filter behavior, with matching next available scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingNextAvailable_ShouldExcludeResult | Verifying that filter with non matching next available exclude result | Setup with non matching next available -> Call Filter -> Assert exclude result | Filter with non matching next available exclude result | In scope: Filter behavior, with non matching next available scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullNextAvailable_ShouldHandleGracefully | Verifying that filter with null next available handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null next available handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## NightAvailabilityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingNightAvailability_ShouldIncludeResult | Verifying that filter with matching night availability include result | Setup with matching night availability -> Call Filter -> Assert include result | Filter with matching night availability include result | In scope: Filter behavior, with matching night availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingNightAvailability_ShouldExcludeResult | Verifying that filter with non matching night availability exclude result | Setup with non matching night availability -> Call Filter -> Assert exclude result | Filter with non matching night availability exclude result | In scope: Filter behavior, with non matching night availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullNightAvailability_ShouldHandleGracefully | Verifying that filter with null night availability handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null night availability handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## OfficeHoursFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingOfficeHours_ShouldIncludeResult | Verifying that filter with matching office hours include result | Setup with matching office hours -> Call Filter -> Assert include result | Filter with matching office hours include result | In scope: Filter behavior, with matching office hours scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingOfficeHours_ShouldExcludeResult | Verifying that filter with non matching office hours exclude result | Setup with non matching office hours -> Call Filter -> Assert exclude result | Filter with non matching office hours exclude result | In scope: Filter behavior, with non matching office hours scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullOfficeHours_ShouldHandleGracefully | Verifying that filter with null office hours handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null office hours handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## OnlineSchedulingFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingOnlineScheduling_ShouldIncludeResult | Verifying that filter with matching online scheduling include result | Setup with matching online scheduling -> Call Filter -> Assert include result | Filter with matching online scheduling include result | In scope: Filter behavior, with matching online scheduling scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingOnlineScheduling_ShouldExcludeResult | Verifying that filter with non matching online scheduling exclude result | Setup with non matching online scheduling -> Call Filter -> Assert exclude result | Filter with non matching online scheduling exclude result | In scope: Filter behavior, with non matching online scheduling scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullOnlineScheduling_ShouldHandleGracefully | Verifying that filter with null online scheduling handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null online scheduling handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## OpenWeekendFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingOpenWeekend_ShouldIncludeResult | Verifying that filter with matching open weekend include result | Setup with matching open weekend -> Call Filter -> Assert include result | Filter with matching open weekend include result | In scope: Filter behavior, with matching open weekend scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingOpenWeekend_ShouldExcludeResult | Verifying that filter with non matching open weekend exclude result | Setup with non matching open weekend -> Call Filter -> Assert exclude result | Filter with non matching open weekend exclude result | In scope: Filter behavior, with non matching open weekend scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullOpenWeekend_ShouldHandleGracefully | Verifying that filter with null open weekend handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null open weekend handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PatientAgeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPatientAge_ShouldIncludeResult | Verifying that filter with matching patient age include result | Setup with matching patient age -> Call Filter -> Assert include result | Filter with matching patient age include result | In scope: Filter behavior, with matching patient age scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPatientAge_ShouldExcludeResult | Verifying that filter with non matching patient age exclude result | Setup with non matching patient age -> Call Filter -> Assert exclude result | Filter with non matching patient age exclude result | In scope: Filter behavior, with non matching patient age scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPatientAge_ShouldHandleGracefully | Verifying that filter with null patient age handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null patient age handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PatientPopulationFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPatientPopulation_ShouldIncludeResult | Verifying that filter with matching patient population include result | Setup with matching patient population -> Call Filter -> Assert include result | Filter with matching patient population include result | In scope: Filter behavior, with matching patient population scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPatientPopulation_ShouldExcludeResult | Verifying that filter with non matching patient population exclude result | Setup with non matching patient population -> Call Filter -> Assert exclude result | Filter with non matching patient population exclude result | In scope: Filter behavior, with non matching patient population scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPatientPopulation_ShouldHandleGracefully | Verifying that filter with null patient population handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null patient population handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PediatricCareFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPediatricCare_ShouldIncludeResult | Verifying that filter with matching pediatric care include result | Setup with matching pediatric care -> Call Filter -> Assert include result | Filter with matching pediatric care include result | In scope: Filter behavior, with matching pediatric care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPediatricCare_ShouldExcludeResult | Verifying that filter with non matching pediatric care exclude result | Setup with non matching pediatric care -> Call Filter -> Assert exclude result | Filter with non matching pediatric care exclude result | In scope: Filter behavior, with non matching pediatric care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPediatricCare_ShouldHandleGracefully | Verifying that filter with null pediatric care handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null pediatric care handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PhoneConsultFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPhoneConsult_ShouldIncludeResult | Verifying that filter with matching phone consult include result | Setup with matching phone consult -> Call Filter -> Assert include result | Filter with matching phone consult include result | In scope: Filter behavior, with matching phone consult scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPhoneConsult_ShouldExcludeResult | Verifying that filter with non matching phone consult exclude result | Setup with non matching phone consult -> Call Filter -> Assert exclude result | Filter with non matching phone consult exclude result | In scope: Filter behavior, with non matching phone consult scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPhoneConsult_ShouldHandleGracefully | Verifying that filter with null phone consult handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null phone consult handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PracticeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPractice_ShouldIncludeResult | Verifying that filter with matching practice include result | Setup with matching practice -> Call Filter -> Assert include result | Filter with matching practice include result | In scope: Filter behavior, with matching practice scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPractice_ShouldExcludeResult | Verifying that filter with non matching practice exclude result | Setup with non matching practice -> Call Filter -> Assert exclude result | Filter with non matching practice exclude result | In scope: Filter behavior, with non matching practice scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPractice_ShouldHandleGracefully | Verifying that filter with null practice handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null practice handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PracticeSizeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPracticeSize_ShouldIncludeResult | Verifying that filter with matching practice size include result | Setup with matching practice size -> Call Filter -> Assert include result | Filter with matching practice size include result | In scope: Filter behavior, with matching practice size scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPracticeSize_ShouldExcludeResult | Verifying that filter with non matching practice size exclude result | Setup with non matching practice size -> Call Filter -> Assert exclude result | Filter with non matching practice size exclude result | In scope: Filter behavior, with non matching practice size scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPracticeSize_ShouldHandleGracefully | Verifying that filter with null practice size handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null practice size handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PreferredProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPreferredProvider_ShouldIncludeResult | Verifying that filter with matching preferred provider include result | Setup with matching preferred provider -> Call Filter -> Assert include result | Filter with matching preferred provider include result | In scope: Filter behavior, with matching preferred provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPreferredProvider_ShouldExcludeResult | Verifying that filter with non matching preferred provider exclude result | Setup with non matching preferred provider -> Call Filter -> Assert exclude result | Filter with non matching preferred provider exclude result | In scope: Filter behavior, with non matching preferred provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPreferredProvider_ShouldHandleGracefully | Verifying that filter with null preferred provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null preferred provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PremiumListingFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPremiumListing_ShouldIncludeResult | Verifying that filter with matching premium listing include result | Setup with matching premium listing -> Call Filter -> Assert include result | Filter with matching premium listing include result | In scope: Filter behavior, with matching premium listing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPremiumListing_ShouldExcludeResult | Verifying that filter with non matching premium listing exclude result | Setup with non matching premium listing -> Call Filter -> Assert exclude result | Filter with non matching premium listing exclude result | In scope: Filter behavior, with non matching premium listing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPremiumListing_ShouldHandleGracefully | Verifying that filter with null premium listing handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null premium listing handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ProcedureFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingProcedure_ShouldIncludeResult | Verifying that filter with matching procedure include result | Setup with matching procedure -> Call Filter -> Assert include result | Filter with matching procedure include result | In scope: Filter behavior, with matching procedure scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingProcedure_ShouldExcludeResult | Verifying that filter with non matching procedure exclude result | Setup with non matching procedure -> Call Filter -> Assert exclude result | Filter with non matching procedure exclude result | In scope: Filter behavior, with non matching procedure scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullProcedure_ShouldHandleGracefully | Verifying that filter with null procedure handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null procedure handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingProvider_ShouldIncludeResult | Verifying that filter with matching provider include result | Setup with matching provider -> Call Filter -> Assert include result | Filter with matching provider include result | In scope: Filter behavior, with matching provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingProvider_ShouldExcludeResult | Verifying that filter with non matching provider exclude result | Setup with non matching provider -> Call Filter -> Assert exclude result | Filter with non matching provider exclude result | In scope: Filter behavior, with non matching provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullProvider_ShouldHandleGracefully | Verifying that filter with null provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ProviderTypeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingProviderType_ShouldIncludeResult | Verifying that filter with matching provider type include result | Setup with matching provider type -> Call Filter -> Assert include result | Filter with matching provider type include result | In scope: Filter behavior, with matching provider type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingProviderType_ShouldExcludeResult | Verifying that filter with non matching provider type exclude result | Setup with non matching provider type -> Call Filter -> Assert exclude result | Filter with non matching provider type exclude result | In scope: Filter behavior, with non matching provider type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullProviderType_ShouldHandleGracefully | Verifying that filter with null provider type handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null provider type handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## PublicTransportFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingPublicTransport_ShouldIncludeResult | Verifying that filter with matching public transport include result | Setup with matching public transport -> Call Filter -> Assert include result | Filter with matching public transport include result | In scope: Filter behavior, with matching public transport scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingPublicTransport_ShouldExcludeResult | Verifying that filter with non matching public transport exclude result | Setup with non matching public transport -> Call Filter -> Assert exclude result | Filter with non matching public transport exclude result | In scope: Filter behavior, with non matching public transport scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullPublicTransport_ShouldHandleGracefully | Verifying that filter with null public transport handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null public transport handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## QualityScoreFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingQualityScore_ShouldIncludeResult | Verifying that filter with matching quality score include result | Setup with matching quality score -> Call Filter -> Assert include result | Filter with matching quality score include result | In scope: Filter behavior, with matching quality score scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingQualityScore_ShouldExcludeResult | Verifying that filter with non matching quality score exclude result | Setup with non matching quality score -> Call Filter -> Assert exclude result | Filter with non matching quality score exclude result | In scope: Filter behavior, with non matching quality score scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullQualityScore_ShouldHandleGracefully | Verifying that filter with null quality score handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null quality score handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## RatingThresholdFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingRatingThreshold_ShouldIncludeResult | Verifying that filter with matching rating threshold include result | Setup with matching rating threshold -> Call Filter -> Assert include result | Filter with matching rating threshold include result | In scope: Filter behavior, with matching rating threshold scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingRatingThreshold_ShouldExcludeResult | Verifying that filter with non matching rating threshold exclude result | Setup with non matching rating threshold -> Call Filter -> Assert exclude result | Filter with non matching rating threshold exclude result | In scope: Filter behavior, with non matching rating threshold scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullRatingThreshold_ShouldHandleGracefully | Verifying that filter with null rating threshold handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null rating threshold handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## RelevanceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingRelevance_ShouldIncludeResult | Verifying that filter with matching relevance include result | Setup with matching relevance -> Call Filter -> Assert include result | Filter with matching relevance include result | In scope: Filter behavior, with matching relevance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingRelevance_ShouldExcludeResult | Verifying that filter with non matching relevance exclude result | Setup with non matching relevance -> Call Filter -> Assert exclude result | Filter with non matching relevance exclude result | In scope: Filter behavior, with non matching relevance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullRelevance_ShouldHandleGracefully | Verifying that filter with null relevance handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null relevance handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## SameDayAppointmentFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingSameDayAppointment_ShouldIncludeResult | Verifying that filter with matching same day appointment include result | Setup with matching same day appointment -> Call Filter -> Assert include result | Filter with matching same day appointment include result | In scope: Filter behavior, with matching same day appointment scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingSameDayAppointment_ShouldExcludeResult | Verifying that filter with non matching same day appointment exclude result | Setup with non matching same day appointment -> Call Filter -> Assert exclude result | Filter with non matching same day appointment exclude result | In scope: Filter behavior, with non matching same day appointment scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullSameDayAppointment_ShouldHandleGracefully | Verifying that filter with null same day appointment handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null same day appointment handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## SameDayFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingSameDay_ShouldIncludeResult | Verifying that filter with matching same day include result | Setup with matching same day -> Call Filter -> Assert include result | Filter with matching same day include result | In scope: Filter behavior, with matching same day scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingSameDay_ShouldExcludeResult | Verifying that filter with non matching same day exclude result | Setup with non matching same day -> Call Filter -> Assert exclude result | Filter with non matching same day exclude result | In scope: Filter behavior, with non matching same day scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullSameDay_ShouldHandleGracefully | Verifying that filter with null same day handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null same day handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## SeniorCareFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingSeniorCare_ShouldIncludeResult | Verifying that filter with matching senior care include result | Setup with matching senior care -> Call Filter -> Assert include result | Filter with matching senior care include result | In scope: Filter behavior, with matching senior care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingSeniorCare_ShouldExcludeResult | Verifying that filter with non matching senior care exclude result | Setup with non matching senior care -> Call Filter -> Assert exclude result | Filter with non matching senior care exclude result | In scope: Filter behavior, with non matching senior care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullSeniorCare_ShouldHandleGracefully | Verifying that filter with null senior care handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null senior care handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ServiceAreaFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingServiceArea_ShouldIncludeResult | Verifying that filter with matching service area include result | Setup with matching service area -> Call Filter -> Assert include result | Filter with matching service area include result | In scope: Filter behavior, with matching service area scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingServiceArea_ShouldExcludeResult | Verifying that filter with non matching service area exclude result | Setup with non matching service area -> Call Filter -> Assert exclude result | Filter with non matching service area exclude result | In scope: Filter behavior, with non matching service area scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullServiceArea_ShouldHandleGracefully | Verifying that filter with null service area handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null service area handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## SpecialtyFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingSpecialty_ShouldIncludeResult | Verifying that filter with matching specialty include result | Setup with matching specialty -> Call Filter -> Assert include result | Filter with matching specialty include result | In scope: Filter behavior, with matching specialty scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingSpecialty_ShouldExcludeResult | Verifying that filter with non matching specialty exclude result | Setup with non matching specialty -> Call Filter -> Assert exclude result | Filter with non matching specialty exclude result | In scope: Filter behavior, with non matching specialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullSpecialty_ShouldHandleGracefully | Verifying that filter with null specialty handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null specialty handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## StateFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingState_ShouldIncludeResult | Verifying that filter with matching state include result | Setup with matching state -> Call Filter -> Assert include result | Filter with matching state include result | In scope: Filter behavior, with matching state scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingState_ShouldExcludeResult | Verifying that filter with non matching state exclude result | Setup with non matching state -> Call Filter -> Assert exclude result | Filter with non matching state exclude result | In scope: Filter behavior, with non matching state scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullState_ShouldHandleGracefully | Verifying that filter with null state handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null state handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## SubspecialtyFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingSubspecialty_ShouldIncludeResult | Verifying that filter with matching subspecialty include result | Setup with matching subspecialty -> Call Filter -> Assert include result | Filter with matching subspecialty include result | In scope: Filter behavior, with matching subspecialty scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingSubspecialty_ShouldExcludeResult | Verifying that filter with non matching subspecialty exclude result | Setup with non matching subspecialty -> Call Filter -> Assert exclude result | Filter with non matching subspecialty exclude result | In scope: Filter behavior, with non matching subspecialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullSubspecialty_ShouldHandleGracefully | Verifying that filter with null subspecialty handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null subspecialty handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## TelehealthFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingTelehealth_ShouldIncludeResult | Verifying that filter with matching telehealth include result | Setup with matching telehealth -> Call Filter -> Assert include result | Filter with matching telehealth include result | In scope: Filter behavior, with matching telehealth scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingTelehealth_ShouldExcludeResult | Verifying that filter with non matching telehealth exclude result | Setup with non matching telehealth -> Call Filter -> Assert exclude result | Filter with non matching telehealth exclude result | In scope: Filter behavior, with non matching telehealth scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullTelehealth_ShouldHandleGracefully | Verifying that filter with null telehealth handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null telehealth handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## TelehealthPlatformFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingTelehealthPlatform_ShouldIncludeResult | Verifying that filter with matching telehealth platform include result | Setup with matching telehealth platform -> Call Filter -> Assert include result | Filter with matching telehealth platform include result | In scope: Filter behavior, with matching telehealth platform scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingTelehealthPlatform_ShouldExcludeResult | Verifying that filter with non matching telehealth platform exclude result | Setup with non matching telehealth platform -> Call Filter -> Assert exclude result | Filter with non matching telehealth platform exclude result | In scope: Filter behavior, with non matching telehealth platform scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullTelehealthPlatform_ShouldHandleGracefully | Verifying that filter with null telehealth platform handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null telehealth platform handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## TimeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingTime_ShouldIncludeResult | Verifying that filter with matching time include result | Setup with matching time -> Call Filter -> Assert include result | Filter with matching time include result | In scope: Filter behavior, with matching time scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingTime_ShouldExcludeResult | Verifying that filter with non matching time exclude result | Setup with non matching time -> Call Filter -> Assert exclude result | Filter with non matching time exclude result | In scope: Filter behavior, with non matching time scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullTime_ShouldHandleGracefully | Verifying that filter with null time handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null time handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## TopProviderFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingTopProvider_ShouldIncludeResult | Verifying that filter with matching top provider include result | Setup with matching top provider -> Call Filter -> Assert include result | Filter with matching top provider include result | In scope: Filter behavior, with matching top provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingTopProvider_ShouldExcludeResult | Verifying that filter with non matching top provider exclude result | Setup with non matching top provider -> Call Filter -> Assert exclude result | Filter with non matching top provider exclude result | In scope: Filter behavior, with non matching top provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullTopProvider_ShouldHandleGracefully | Verifying that filter with null top provider handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null top provider handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## UrgentAvailabilityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingUrgentAvailability_ShouldIncludeResult | Verifying that filter with matching urgent availability include result | Setup with matching urgent availability -> Call Filter -> Assert include result | Filter with matching urgent availability include result | In scope: Filter behavior, with matching urgent availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingUrgentAvailability_ShouldExcludeResult | Verifying that filter with non matching urgent availability exclude result | Setup with non matching urgent availability -> Call Filter -> Assert exclude result | Filter with non matching urgent availability exclude result | In scope: Filter behavior, with non matching urgent availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullUrgentAvailability_ShouldHandleGracefully | Verifying that filter with null urgent availability handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null urgent availability handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## UrgentCareFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingUrgentCare_ShouldIncludeResult | Verifying that filter with matching urgent care include result | Setup with matching urgent care -> Call Filter -> Assert include result | Filter with matching urgent care include result | In scope: Filter behavior, with matching urgent care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingUrgentCare_ShouldExcludeResult | Verifying that filter with non matching urgent care exclude result | Setup with non matching urgent care -> Call Filter -> Assert exclude result | Filter with non matching urgent care exclude result | In scope: Filter behavior, with non matching urgent care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullUrgentCare_ShouldHandleGracefully | Verifying that filter with null urgent care handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null urgent care handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## VaccineTypeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingVaccineType_ShouldIncludeResult | Verifying that filter with matching vaccine type include result | Setup with matching vaccine type -> Call Filter -> Assert include result | Filter with matching vaccine type include result | In scope: Filter behavior, with matching vaccine type scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingVaccineType_ShouldExcludeResult | Verifying that filter with non matching vaccine type exclude result | Setup with non matching vaccine type -> Call Filter -> Assert exclude result | Filter with non matching vaccine type exclude result | In scope: Filter behavior, with non matching vaccine type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullVaccineType_ShouldHandleGracefully | Verifying that filter with null vaccine type handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null vaccine type handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## VideoVisitFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingVideoVisit_ShouldIncludeResult | Verifying that filter with matching video visit include result | Setup with matching video visit -> Call Filter -> Assert include result | Filter with matching video visit include result | In scope: Filter behavior, with matching video visit scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingVideoVisit_ShouldExcludeResult | Verifying that filter with non matching video visit exclude result | Setup with non matching video visit -> Call Filter -> Assert exclude result | Filter with non matching video visit exclude result | In scope: Filter behavior, with non matching video visit scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullVideoVisit_ShouldHandleGracefully | Verifying that filter with null video visit handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null video visit handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## VirtualCareFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingVirtualCare_ShouldIncludeResult | Verifying that filter with matching virtual care include result | Setup with matching virtual care -> Call Filter -> Assert include result | Filter with matching virtual care include result | In scope: Filter behavior, with matching virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingVirtualCare_ShouldExcludeResult | Verifying that filter with non matching virtual care exclude result | Setup with non matching virtual care -> Call Filter -> Assert exclude result | Filter with non matching virtual care exclude result | In scope: Filter behavior, with non matching virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullVirtualCare_ShouldHandleGracefully | Verifying that filter with null virtual care handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null virtual care handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## WalkInClinicFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingWalkInClinic_ShouldIncludeResult | Verifying that filter with matching walk in clinic include result | Setup with matching walk in clinic -> Call Filter -> Assert include result | Filter with matching walk in clinic include result | In scope: Filter behavior, with matching walk in clinic scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingWalkInClinic_ShouldExcludeResult | Verifying that filter with non matching walk in clinic exclude result | Setup with non matching walk in clinic -> Call Filter -> Assert exclude result | Filter with non matching walk in clinic exclude result | In scope: Filter behavior, with non matching walk in clinic scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullWalkInClinic_ShouldHandleGracefully | Verifying that filter with null walk in clinic handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null walk in clinic handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## WalkInFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingWalkIn_ShouldIncludeResult | Verifying that filter with matching walk in include result | Setup with matching walk in -> Call Filter -> Assert include result | Filter with matching walk in include result | In scope: Filter behavior, with matching walk in scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingWalkIn_ShouldExcludeResult | Verifying that filter with non matching walk in exclude result | Setup with non matching walk in -> Call Filter -> Assert exclude result | Filter with non matching walk in exclude result | In scope: Filter behavior, with non matching walk in scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullWalkIn_ShouldHandleGracefully | Verifying that filter with null walk in handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null walk in handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## WeekendHoursFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingWeekendHours_ShouldIncludeResult | Verifying that filter with matching weekend hours include result | Setup with matching weekend hours -> Call Filter -> Assert include result | Filter with matching weekend hours include result | In scope: Filter behavior, with matching weekend hours scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingWeekendHours_ShouldExcludeResult | Verifying that filter with non matching weekend hours exclude result | Setup with non matching weekend hours -> Call Filter -> Assert exclude result | Filter with non matching weekend hours exclude result | In scope: Filter behavior, with non matching weekend hours scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullWeekendHours_ShouldHandleGracefully | Verifying that filter with null weekend hours handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null weekend hours handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## XRayServiceFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingXRayService_ShouldIncludeResult | Verifying that filter with matching x ray service include result | Setup with matching x ray service -> Call Filter -> Assert include result | Filter with matching x ray service include result | In scope: Filter behavior, with matching x ray service scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingXRayService_ShouldExcludeResult | Verifying that filter with non matching x ray service exclude result | Setup with non matching x ray service -> Call Filter -> Assert exclude result | Filter with non matching x ray service exclude result | In scope: Filter behavior, with non matching x ray service scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullXRayService_ShouldHandleGracefully | Verifying that filter with null x ray service handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null x ray service handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## YearEstablishedFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingYearEstablished_ShouldIncludeResult | Verifying that filter with matching year established include result | Setup with matching year established -> Call Filter -> Assert include result | Filter with matching year established include result | In scope: Filter behavior, with matching year established scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingYearEstablished_ShouldExcludeResult | Verifying that filter with non matching year established exclude result | Setup with non matching year established -> Call Filter -> Assert exclude result | Filter with non matching year established exclude result | In scope: Filter behavior, with non matching year established scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullYearEstablished_ShouldHandleGracefully | Verifying that filter with null year established handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null year established handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ZipCodeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingZipCode_ShouldIncludeResult | Verifying that filter with matching zip code include result | Setup with matching zip code -> Call Filter -> Assert include result | Filter with matching zip code include result | In scope: Filter behavior, with matching zip code scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingZipCode_ShouldExcludeResult | Verifying that filter with non matching zip code exclude result | Setup with non matching zip code -> Call Filter -> Assert exclude result | Filter with non matching zip code exclude result | In scope: Filter behavior, with non matching zip code scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullZipCode_ShouldHandleGracefully | Verifying that filter with null zip code handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null zip code handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

## ZoneRestrictionFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithMatchingZoneRestriction_ShouldIncludeResult | Verifying that filter with matching zone restriction include result | Setup with matching zone restriction -> Call Filter -> Assert include result | Filter with matching zone restriction include result | In scope: Filter behavior, with matching zone restriction scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithNonMatchingZoneRestriction_ShouldExcludeResult | Verifying that filter with non matching zone restriction exclude result | Setup with non matching zone restriction -> Call Filter -> Assert exclude result | Filter with non matching zone restriction exclude result | In scope: Filter behavior, with non matching zone restriction scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithNullZoneRestriction_ShouldHandleGracefully | Verifying that filter with null zone restriction handle gracefully | Setup with null input -> Call Filter -> Assert handle gracefully | Filter with null zone restriction handle gracefully | In scope: null input handling for Filter. Out of scope: valid input scenarios. |

# Search/Es/Scoring

## FunctionScorerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Score_ShouldApplyFunction | Verifying that score should apply function | Setup test data and mocks -> Call Score -> Assert expected behavior of Score | Score should apply function | In scope: Score behavior, should apply function scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_WithNoFunction_ShouldReturnOriginalScore | Verifying that score with no function returns original score | Setup with no function -> Call Score -> Assert return original score | Score with no function returns original score | In scope: Score behavior, with no function scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Score_ShouldCombineMultipleFunctions | Verifying that score should combine multiple functions | Setup test data and mocks -> Call Score -> Assert expected behavior of Score | Score should combine multiple functions | In scope: Score behavior, should combine multiple functions scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Score_WithZeroWeight_ShouldReturnZero | Verifying that score with zero weight returns zero | Setup with zero weight -> Call Score -> Assert return zero | Score with zero weight returns zero | In scope: Score behavior, with zero weight scenario. Out of scope: other scenarios and methods not under test. |

# Search/Grouping

## CommonGroupingsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetGrouping_WithInNetwork_ShouldReturnInNetworkGroup | Verifying that get grouping with in network returns in network group | Setup with in network -> Call GetGrouping -> Assert return in network group | GetGrouping with in network returns in network group | In scope: GetGrouping behavior, with in network scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetGrouping_WithOutOfNetwork_ShouldReturnOutOfNetworkGroup | Verifying that get grouping with out of network returns out of network group | Setup with out of network -> Call GetGrouping -> Assert return out of network group | GetGrouping with out of network returns out of network group | In scope: GetGrouping behavior, with out of network scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetGrouping_WithUnknownNetwork_ShouldReturnDefaultGroup | Verifying that get grouping with unknown network returns default group | Setup with unknown network -> Call GetGrouping -> Assert return default group | GetGrouping with unknown network returns default group | In scope: GetGrouping behavior, with unknown network scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AllGroupings_ShouldBeDistinct | Verifying that all groupings should be distinct | Setup test data and mocks -> Call AllGroupings -> Assert expected behavior of AllGroupings | AllGroupings should be distinct | In scope: AllGroupings behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |

## GroupMarkerProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Process_ShouldMarkGroupBoundaries | Verifying that process should mark group boundaries | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should mark group boundaries | In scope: Process behavior, should mark group boundaries scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Process_WithSingleGroup_ShouldNotMark | Verifying that process with single group does not mark | Setup with single group -> Call Process -> Assert not mark | Process with single group does not mark | In scope: Process behavior, with single group scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_WithEmptyResults_ShouldReturnEmpty | Verifying that process with empty results returns empty | Setup with empty input -> Call Process -> Assert returns empty collection | Process with empty results returns empty | In scope: empty input handling for Process. Out of scope: non-empty input scenarios. |
| 4 | | Process_ShouldPreserveOrder | Verifying that process should preserve order | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should preserve order | In scope: Process behavior, should preserve order scenario. Out of scope: other scenarios and methods not under test. |

## GroupRankerProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Process_ShouldRankGroupsByPriority | Verifying that process should rank groups by priority | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should rank groups by priority | In scope: Process behavior, should rank groups by priority scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Process_WithSingleGroup_ShouldReturnAsIs | Verifying that process with single group returns as is | Setup with single group -> Call Process -> Assert return as is | Process with single group returns as is | In scope: Process behavior, with single group scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_WithEmptyGroups_ShouldReturnEmpty | Verifying that process with empty groups returns empty | Setup with empty input -> Call Process -> Assert returns empty collection | Process with empty groups returns empty | In scope: empty input handling for Process. Out of scope: non-empty input scenarios. |
| 4 | | Process_ShouldPreserveWithinGroupOrder | Verifying that process should preserve within group order | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should preserve within group order | In scope: Process behavior, should preserve within group order scenario. Out of scope: other scenarios and methods not under test. |

## ResultGrouperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Group_ShouldGroupResultsByGroupKey | Verifying that group should group results by group key | Setup test data and mocks -> Call Group -> Assert expected behavior of Group | Group should group results by group key | In scope: Group behavior, should group results by group key scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Group_WithNoGroupKey_ShouldUseDefaultGroup | Verifying that group with no group key use default group | Setup with no group key -> Call Group -> Assert use default group | Group with no group key use default group | In scope: Group behavior, with no group key scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Group_WithEmptyResults_ShouldReturnEmpty | Verifying that group with empty results returns empty | Setup with empty input -> Call Group -> Assert returns empty collection | Group with empty results returns empty | In scope: empty input handling for Group. Out of scope: non-empty input scenarios. |
| 4 | | Group_ShouldPreserveResultOrder | Verifying that group should preserve result order | Setup test data and mocks -> Call Group -> Assert expected behavior of Group | Group should preserve result order | In scope: Group behavior, should preserve result order scenario. Out of scope: other scenarios and methods not under test. |

## SearchResultGroupTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Results_ShouldDefaultToEmptyList | Verifying that results should default to empty list | Setup with empty input -> Call Results -> Assert expected behavior of Results | Results should default to empty list | In scope: empty input handling for Results. Out of scope: non-empty input scenarios. |

# Search/Hydration

## EnterpriseHydrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Hydrate_ShouldPopulateEnterpriseFields | Verifying that hydrate should populate enterprise fields | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should populate enterprise fields | In scope: Hydrate behavior, should populate enterprise fields scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Hydrate_WithMissingData_ShouldHandleGracefully | Verifying that hydrate with missing data handle gracefully | Setup with missing data -> Call Hydrate -> Assert handle gracefully | Hydrate with missing data handle gracefully | In scope: Hydrate behavior, with missing data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Hydrate_ShouldCallEnterpriseService | Verifying that hydrate should call enterprise service | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should call enterprise service | In scope: Hydrate behavior, should call enterprise service scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Hydrate_WithNullResults_ShouldReturnEmpty | Verifying that hydrate with null results returns empty | Setup with null input -> Call Hydrate -> Assert returns empty collection | Hydrate with null results returns empty | In scope: null input handling for Hydrate. Out of scope: valid input scenarios. |

## HydrationProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Process_ShouldCallAllHydrators | Verifying that process should call all hydrators | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should call all hydrators | In scope: Process behavior, should call all hydrators scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Process_ShouldPassResultsToEachHydrator | Verifying that process should pass results to each hydrator | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should pass results to each hydrator | In scope: Process behavior, should pass results to each hydrator scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_WithNoHydrators_ShouldReturnOriginal | Verifying that process with no hydrators returns original | Setup with no hydrators -> Call Process -> Assert return original | Process with no hydrators returns original | In scope: Process behavior, with no hydrators scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Process_ShouldChainHydrators | Verifying that process should chain hydrators | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should chain hydrators | In scope: Process behavior, should chain hydrators scenario. Out of scope: other scenarios and methods not under test. |

## HydratorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Hydrate_ShouldPopulateFields | Verifying that hydrate should populate fields | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should populate fields | In scope: Hydrate behavior, should populate fields scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Hydrate_WithNullInput_ShouldHandleGracefully | Verifying that hydrate with null input handle gracefully | Setup with null input -> Call Hydrate -> Assert handle gracefully | Hydrate with null input handle gracefully | In scope: null input handling for Hydrate. Out of scope: valid input scenarios. |
| 3 | | Hydrate_ShouldCallDataSource | Verifying that hydrate should call data source | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should call data source | In scope: Hydrate behavior, should call data source scenario. Out of scope: other scenarios and methods not under test. |

## ListingAndEnterpriseHydrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Hydrate_ShouldPopulateBothListingAndEnterpriseFields | Verifying that hydrate should populate both listing and enterprise fields | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should populate both listing and enterprise fields | In scope: Hydrate behavior, should populate both listing and enterprise fields scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Hydrate_WithMissingListingData_ShouldStillHydrateEnterprise | Verifying that hydrate with missing listing data still hydrate enterprise | Setup with missing listing data -> Call Hydrate -> Assert still hydrate enterprise | Hydrate with missing listing data still hydrate enterprise | In scope: Hydrate behavior, with missing listing data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Hydrate_WithMissingEnterpriseData_ShouldStillHydrateListing | Verifying that hydrate with missing enterprise data still hydrate listing | Setup with missing enterprise data -> Call Hydrate -> Assert still hydrate listing | Hydrate with missing enterprise data still hydrate listing | In scope: Hydrate behavior, with missing enterprise data scenario. Out of scope: other scenarios and methods not under test. |

## ListingHydrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Hydrate_ShouldPopulateListingFields | Verifying that hydrate should populate listing fields | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should populate listing fields | In scope: Hydrate behavior, should populate listing fields scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Hydrate_WithMissingData_ShouldHandleGracefully | Verifying that hydrate with missing data handle gracefully | Setup with missing data -> Call Hydrate -> Assert handle gracefully | Hydrate with missing data handle gracefully | In scope: Hydrate behavior, with missing data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Hydrate_ShouldCallListingService | Verifying that hydrate should call listing service | Setup test data and mocks -> Call Hydrate -> Assert expected behavior of Hydrate | Hydrate should call listing service | In scope: Hydrate behavior, should call listing service scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Hydrate_WithNullResults_ShouldReturnEmpty | Verifying that hydrate with null results returns empty | Setup with null input -> Call Hydrate -> Assert returns empty collection | Hydrate with null results returns empty | In scope: null input handling for Hydrate. Out of scope: valid input scenarios. |

# Search/MarketIntelligence

## FilterSerializerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Serialize_ShouldConvertFiltersToJson | Verifying that serialize should convert filters to json | Setup test data and mocks -> Call Serialize -> Assert expected behavior of Serialize | Serialize should convert filters to json | In scope: Serialize behavior, should convert filters to json scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Deserialize_ShouldParseJsonToFilters | Verifying that deserialize should parse json to filters | Setup test data and mocks -> Call Deserialize -> Assert expected behavior of Deserialize | Deserialize should parse json to filters | In scope: Deserialize behavior, should parse json to filters scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | RoundTrip_ShouldPreserveFilters | Verifying that round trip should preserve filters | Setup test data and mocks -> Call RoundTrip -> Assert expected behavior of RoundTrip | RoundTrip should preserve filters | In scope: RoundTrip behavior, should preserve filters scenario. Out of scope: other scenarios and methods not under test. |

## MarketIntelligenceQueryValidatorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Validate_WithValidQuery_ShouldReturnTrue | Verifying that validate with valid query returns true | Setup with valid query -> Call Validate -> Assert returns true | Validate with valid query returns true | In scope: Validate behavior, with valid query scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Validate_WithInvalidQuery_ShouldReturnFalse | Verifying that validate with invalid query returns false | Setup with invalid query -> Call Validate -> Assert returns false | Validate with invalid query returns false | In scope: Validate behavior, with invalid query scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Validate_WithNullQuery_ShouldReturnFalse | Verifying that validate with null query returns false | Setup with null input -> Call Validate -> Assert returns false | Validate with null query returns false | In scope: null input handling for Validate. Out of scope: valid input scenarios. |

## MarketIntelligenceServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_ShouldCallSearchWithCorrectParams | Verifying that execute should call search with correct params | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should call search with correct params | In scope: Execute behavior, should call search with correct params scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_ShouldReturnMappedResults | Verifying that execute should return mapped results | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should return mapped results | In scope: Execute behavior, should return mapped results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Execute_WithNoResults_ShouldReturnEmpty | Verifying that execute with no results returns empty | Setup with no results -> Call Execute -> Assert returns empty collection | Execute with no results returns empty | In scope: Execute behavior, with no results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Execute_ShouldHandleErrors | Verifying that execute should handle errors | Setup mock to throw exception -> Call Execute -> Assert expected behavior of Execute | Execute should handle errors | In scope: error handling in Execute. Out of scope: successful execution paths. |

## PreviewModeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_ShouldReturnPreviewResults | Verifying that execute should return preview results | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should return preview results | In scope: Execute behavior, should return preview results scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_ShouldNotAffectProduction | Verifying that execute should not affect production | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should not affect production | In scope: Execute behavior, should not affect production scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | IsPreview_ShouldReturnTrue | Verifying that is preview should return true | Setup test data and mocks -> Call IsPreview -> Assert expected behavior of IsPreview | IsPreview should return true | In scope: IsPreview behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |

## PreviewSearchExecutorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_ShouldCallSearchAlgorithm | Verifying that execute should call search algorithm | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should call search algorithm | In scope: Execute behavior, should call search algorithm scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_ShouldReturnPreviewResults | Verifying that execute should return preview results | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should return preview results | In scope: Execute behavior, should return preview results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Execute_WithError_ShouldHandleGracefully | Verifying that execute with error handle gracefully | Setup mock to throw exception -> Call Execute -> Assert handle gracefully | Execute with error handle gracefully | In scope: error handling in Execute. Out of scope: successful execution paths. |

## RefinementAggregatorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Aggregate_ShouldCombineRefinements | Verifying that aggregate should combine refinements | Setup test data and mocks -> Call Aggregate -> Assert expected behavior of Aggregate | Aggregate should combine refinements | In scope: Aggregate behavior, should combine refinements scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Aggregate_WithEmptyRefinements_ShouldReturnEmpty | Verifying that aggregate with empty refinements returns empty | Setup with empty input -> Call Aggregate -> Assert returns empty collection | Aggregate with empty refinements returns empty | In scope: empty input handling for Aggregate. Out of scope: non-empty input scenarios. |
| 3 | | Aggregate_ShouldDeduplicateRefinements | Verifying that aggregate should deduplicate refinements | Setup test data and mocks -> Call Aggregate -> Assert expected behavior of Aggregate | Aggregate should deduplicate refinements | In scope: Aggregate behavior, should deduplicate refinements scenario. Out of scope: other scenarios and methods not under test. |

## SignalExtractorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnSupplySignals | Verifying that extract should return supply signals | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return supply signals | In scope: Extract behavior, should return supply signals scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_ShouldReturnDemandSignals | Verifying that extract should return demand signals | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return demand signals | In scope: Extract behavior, should return demand signals scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_WithNoData_ShouldReturnEmpty | Verifying that extract with no data returns empty | Setup with no data -> Call Extract -> Assert returns empty collection | Extract with no data returns empty | In scope: Extract behavior, with no data scenario. Out of scope: other scenarios and methods not under test. |

## SupplyOnlyModeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_ShouldReturnSupplyOnlyResults | Verifying that execute should return supply only results | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should return supply only results | In scope: Execute behavior, should return supply only results scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_ShouldNotIncludeDemandData | Verifying that execute should not include demand data | Setup test data and mocks -> Call Execute -> Assert expected behavior of Execute | Execute should not include demand data | In scope: Execute behavior, should not include demand data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | IsSupplyOnly_ShouldReturnTrue | Verifying that is supply only should return true | Setup test data and mocks -> Call IsSupplyOnly -> Assert expected behavior of IsSupplyOnly | IsSupplyOnly should return true | In scope: IsSupplyOnly behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |

## YassRequestCloneTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Clone_ShouldCreateDeepCopy | Verifying that clone should create deep copy | Setup test data and mocks -> Call Clone -> Assert expected behavior of Clone | Clone should create deep copy | In scope: Clone behavior, should create deep copy scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Clone_ShouldNotShareReferences | Verifying that clone should not share references | Setup test data and mocks -> Call Clone -> Assert expected behavior of Clone | Clone should not share references | In scope: Clone behavior, should not share references scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Clone_ShouldPreserveAllProperties | Verifying that clone should preserve all properties | Setup test data and mocks -> Call Clone -> Assert expected behavior of Clone | Clone should preserve all properties | In scope: Clone behavior, should preserve all properties scenario. Out of scope: other scenarios and methods not under test. |

# Search/Models

## BoxTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetCorners | Verifying that constructor should set corners | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set corners | In scope: Constructor behavior, should set corners scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Contains_WithPointInside_ShouldReturnTrue | Verifying that contains with point inside returns true | Setup with point inside -> Call Contains -> Assert returns true | Contains with point inside returns true | In scope: Contains behavior, with point inside scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Contains_WithPointOutside_ShouldReturnFalse | Verifying that contains with point outside returns false | Setup with point outside -> Call Contains -> Assert returns false | Contains with point outside returns false | In scope: Contains behavior, with point outside scenario. Out of scope: other scenarios and methods not under test. |

## CoordinateTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetLatLon | Verifying that constructor should set lat lon | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set lat lon | In scope: Constructor behavior, should set lat lon scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Equals_WithSameCoordinates_ShouldReturnTrue | Verifying that equals with same coordinates returns true | Setup with same coordinates -> Call Equals -> Assert returns true | Equals with same coordinates returns true | In scope: Equals behavior, with same coordinates scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Equals_WithDifferentCoordinates_ShouldReturnFalse | Verifying that equals with different coordinates returns false | Setup with different coordinates -> Call Equals -> Assert returns false | Equals with different coordinates returns false | In scope: Equals behavior, with different coordinates scenario. Out of scope: other scenarios and methods not under test. |

## CoordinateWithZipTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetCoordinateAndZip | Verifying that constructor should set coordinate and zip | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set coordinate and zip | In scope: Constructor behavior, should set coordinate and zip scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## LocationParamFactoryTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Create_WithValidInput_ShouldReturnLocationParam | Verifying that create with valid input returns location param | Setup with valid input -> Call Create -> Assert return location param | Create with valid input returns location param | In scope: Create behavior, with valid input scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Create_WithNullInput_ShouldReturnDefault | Verifying that create with null input returns default | Setup with null input -> Call Create -> Assert return default | Create with null input returns default | In scope: null input handling for Create. Out of scope: valid input scenarios. |
| 3 | | Create_ShouldMapCoordinatesCorrectly | Verifying that create should map coordinates correctly | Setup test data and mocks -> Call Create -> Assert expected behavior of Create | Create should map coordinates correctly | In scope: Create behavior, should map coordinates correctly scenario. Out of scope: other scenarios and methods not under test. |

# Search/Personalization

## DevicePersonalizationRetrieverProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Process_ShouldRetrievePersonalizationData | Verifying that process should retrieve personalization data | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should retrieve personalization data | In scope: Process behavior, should retrieve personalization data scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Process_WithNoData_ShouldReturnDefault | Verifying that process with no data returns default | Setup with no data -> Call Process -> Assert return default | Process with no data returns default | In scope: Process behavior, with no data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_ShouldPassDeviceId | Verifying that process should pass device id | Setup test data and mocks -> Call Process -> Assert expected behavior of Process | Process should pass device id | In scope: Process behavior, should pass device id scenario. Out of scope: other scenarios and methods not under test. |

## DynamoDbDevicePersonalizationRetrieverTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Get_ShouldCallDynamoDb | Verifying that get should call dynamo db | Setup test data and mocks -> Call Get -> Assert expected behavior of Get | Get should call dynamo db | In scope: Get behavior, should call dynamo db scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Get_ShouldReturnPersonalizationData | Verifying that get should return personalization data | Setup test data and mocks -> Call Get -> Assert expected behavior of Get | Get should return personalization data | In scope: Get behavior, should return personalization data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Get_WithMissingRecord_ShouldReturnNull | Verifying that get with missing record returns null | Setup with missing record -> Call Get -> Assert returns null | Get with missing record returns null | In scope: Get behavior, with missing record scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Get_WhenDynamoDbThrows_ShouldReturnNull | Verifying that get when dynamo db throws returns null | Setup mock to throw exception -> Call Get -> Assert returns null | Get when dynamo db throws returns null | In scope: error handling in Get. Out of scope: successful execution paths. |

## NullDevicePersonalizationRetrieverTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Get_ShouldReturnNull | Verifying that get should return null | Setup with null input -> Call Get -> Assert expected behavior of Get | Get should return null | In scope: null input handling for Get. Out of scope: valid input scenarios. |
| 2 | | Get_ShouldNotCallAnyService | Verifying that get should not call any service | Setup test data and mocks -> Call Get -> Assert expected behavior of Get | Get should not call any service | In scope: Get behavior, should not call any service scenario. Out of scope: other scenarios and methods not under test. |

# Search/Ranking

## BestSentenceEnricherTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case1 | Verifying that enrich with sentence extraction extract correctly_ case1 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case1 | Enrich with sentence extraction extract correctly_ case1 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case2 | Verifying that enrich with sentence extraction extract correctly_ case2 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case2 | Enrich with sentence extraction extract correctly_ case2 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case3 | Verifying that enrich with sentence extraction extract correctly_ case3 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case3 | Enrich with sentence extraction extract correctly_ case3 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case4 | Verifying that enrich with sentence extraction extract correctly_ case4 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case4 | Enrich with sentence extraction extract correctly_ case4 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case5 | Verifying that enrich with sentence extraction extract correctly_ case5 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case5 | Enrich with sentence extraction extract correctly_ case5 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case6 | Verifying that enrich with sentence extraction extract correctly_ case6 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case6 | Enrich with sentence extraction extract correctly_ case6 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case7 | Verifying that enrich with sentence extraction extract correctly_ case7 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case7 | Enrich with sentence extraction extract correctly_ case7 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case8 | Verifying that enrich with sentence extraction extract correctly_ case8 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case8 | Enrich with sentence extraction extract correctly_ case8 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case9 | Verifying that enrich with sentence extraction extract correctly_ case9 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case9 | Enrich with sentence extraction extract correctly_ case9 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case10 | Verifying that enrich with sentence extraction extract correctly_ case10 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case10 | Enrich with sentence extraction extract correctly_ case10 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Enrich_WithSentenceExtraction_ShouldExtractCorrectly_Case11 | Verifying that enrich with sentence extraction extract correctly_ case11 | Setup with sentence extraction -> Call Enrich -> Assert extract correctly_ case11 | Enrich with sentence extraction extract correctly_ case11 | In scope: Enrich behavior, with sentence extraction scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case1 | Verifying that enrich with sentence scoring score correctly_ case1 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case1 | Enrich with sentence scoring score correctly_ case1 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case2 | Verifying that enrich with sentence scoring score correctly_ case2 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case2 | Enrich with sentence scoring score correctly_ case2 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case3 | Verifying that enrich with sentence scoring score correctly_ case3 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case3 | Enrich with sentence scoring score correctly_ case3 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case4 | Verifying that enrich with sentence scoring score correctly_ case4 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case4 | Enrich with sentence scoring score correctly_ case4 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case5 | Verifying that enrich with sentence scoring score correctly_ case5 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case5 | Enrich with sentence scoring score correctly_ case5 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case6 | Verifying that enrich with sentence scoring score correctly_ case6 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case6 | Enrich with sentence scoring score correctly_ case6 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case7 | Verifying that enrich with sentence scoring score correctly_ case7 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case7 | Enrich with sentence scoring score correctly_ case7 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case8 | Verifying that enrich with sentence scoring score correctly_ case8 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case8 | Enrich with sentence scoring score correctly_ case8 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case9 | Verifying that enrich with sentence scoring score correctly_ case9 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case9 | Enrich with sentence scoring score correctly_ case9 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case10 | Verifying that enrich with sentence scoring score correctly_ case10 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case10 | Enrich with sentence scoring score correctly_ case10 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | Enrich_WithSentenceScoring_ShouldScoreCorrectly_Case11 | Verifying that enrich with sentence scoring score correctly_ case11 | Setup with sentence scoring -> Call Enrich -> Assert score correctly_ case11 | Enrich with sentence scoring score correctly_ case11 | In scope: Enrich behavior, with sentence scoring scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case1 | Verifying that enrich with medical abbreviations does not split incorrectly_ case1 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case1 | Enrich with medical abbreviations does not split incorrectly_ case1 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case2 | Verifying that enrich with medical abbreviations does not split incorrectly_ case2 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case2 | Enrich with medical abbreviations does not split incorrectly_ case2 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case3 | Verifying that enrich with medical abbreviations does not split incorrectly_ case3 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case3 | Enrich with medical abbreviations does not split incorrectly_ case3 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case4 | Verifying that enrich with medical abbreviations does not split incorrectly_ case4 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case4 | Enrich with medical abbreviations does not split incorrectly_ case4 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case5 | Verifying that enrich with medical abbreviations does not split incorrectly_ case5 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case5 | Enrich with medical abbreviations does not split incorrectly_ case5 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case6 | Verifying that enrich with medical abbreviations does not split incorrectly_ case6 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case6 | Enrich with medical abbreviations does not split incorrectly_ case6 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case7 | Verifying that enrich with medical abbreviations does not split incorrectly_ case7 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case7 | Enrich with medical abbreviations does not split incorrectly_ case7 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 30 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case8 | Verifying that enrich with medical abbreviations does not split incorrectly_ case8 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case8 | Enrich with medical abbreviations does not split incorrectly_ case8 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 31 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case9 | Verifying that enrich with medical abbreviations does not split incorrectly_ case9 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case9 | Enrich with medical abbreviations does not split incorrectly_ case9 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 32 | | Enrich_WithMedicalAbbreviations_ShouldNotSplitIncorrectly_Case10 | Verifying that enrich with medical abbreviations does not split incorrectly_ case10 | Setup with medical abbreviations -> Call Enrich -> Assert not split incorrectly_ case10 | Enrich with medical abbreviations does not split incorrectly_ case10 | In scope: Enrich behavior, with medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 33 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case1 | Verifying that enrich with edge cases handle gracefully_ case1 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case1 | Enrich with edge cases handle gracefully_ case1 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 34 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case2 | Verifying that enrich with edge cases handle gracefully_ case2 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case2 | Enrich with edge cases handle gracefully_ case2 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 35 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case3 | Verifying that enrich with edge cases handle gracefully_ case3 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case3 | Enrich with edge cases handle gracefully_ case3 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 36 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case4 | Verifying that enrich with edge cases handle gracefully_ case4 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case4 | Enrich with edge cases handle gracefully_ case4 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 37 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case5 | Verifying that enrich with edge cases handle gracefully_ case5 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case5 | Enrich with edge cases handle gracefully_ case5 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 38 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case6 | Verifying that enrich with edge cases handle gracefully_ case6 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case6 | Enrich with edge cases handle gracefully_ case6 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 39 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case7 | Verifying that enrich with edge cases handle gracefully_ case7 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case7 | Enrich with edge cases handle gracefully_ case7 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 40 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case8 | Verifying that enrich with edge cases handle gracefully_ case8 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case8 | Enrich with edge cases handle gracefully_ case8 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 41 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case9 | Verifying that enrich with edge cases handle gracefully_ case9 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case9 | Enrich with edge cases handle gracefully_ case9 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 42 | | Enrich_WithEdgeCases_ShouldHandleGracefully_Case10 | Verifying that enrich with edge cases handle gracefully_ case10 | Setup with edge cases -> Call Enrich -> Assert handle gracefully_ case10 | Enrich with edge cases handle gracefully_ case10 | In scope: Enrich behavior, with edge cases scenario. Out of scope: other scenarios and methods not under test. |
| 43 | | Enrich_WithRanking_ShouldRankByRelevance_Case1 | Verifying that enrich with ranking rank by relevance_ case1 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case1 | Enrich with ranking rank by relevance_ case1 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 44 | | Enrich_WithRanking_ShouldRankByRelevance_Case2 | Verifying that enrich with ranking rank by relevance_ case2 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case2 | Enrich with ranking rank by relevance_ case2 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 45 | | Enrich_WithRanking_ShouldRankByRelevance_Case3 | Verifying that enrich with ranking rank by relevance_ case3 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case3 | Enrich with ranking rank by relevance_ case3 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 46 | | Enrich_WithRanking_ShouldRankByRelevance_Case4 | Verifying that enrich with ranking rank by relevance_ case4 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case4 | Enrich with ranking rank by relevance_ case4 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 47 | | Enrich_WithRanking_ShouldRankByRelevance_Case5 | Verifying that enrich with ranking rank by relevance_ case5 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case5 | Enrich with ranking rank by relevance_ case5 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 48 | | Enrich_WithRanking_ShouldRankByRelevance_Case6 | Verifying that enrich with ranking rank by relevance_ case6 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case6 | Enrich with ranking rank by relevance_ case6 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 49 | | Enrich_WithRanking_ShouldRankByRelevance_Case7 | Verifying that enrich with ranking rank by relevance_ case7 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case7 | Enrich with ranking rank by relevance_ case7 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 50 | | Enrich_WithRanking_ShouldRankByRelevance_Case8 | Verifying that enrich with ranking rank by relevance_ case8 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case8 | Enrich with ranking rank by relevance_ case8 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 51 | | Enrich_WithRanking_ShouldRankByRelevance_Case9 | Verifying that enrich with ranking rank by relevance_ case9 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case9 | Enrich with ranking rank by relevance_ case9 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 52 | | Enrich_WithRanking_ShouldRankByRelevance_Case10 | Verifying that enrich with ranking rank by relevance_ case10 | Setup with ranking -> Call Enrich -> Assert rank by relevance_ case10 | Enrich with ranking rank by relevance_ case10 | In scope: Enrich behavior, with ranking scenario. Out of scope: other scenarios and methods not under test. |
| 53 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case1 | Verifying that enrich with real world text extract best sentence_ case1 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case1 | Enrich with real world text extract best sentence_ case1 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 54 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case2 | Verifying that enrich with real world text extract best sentence_ case2 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case2 | Enrich with real world text extract best sentence_ case2 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 55 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case3 | Verifying that enrich with real world text extract best sentence_ case3 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case3 | Enrich with real world text extract best sentence_ case3 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 56 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case4 | Verifying that enrich with real world text extract best sentence_ case4 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case4 | Enrich with real world text extract best sentence_ case4 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 57 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case5 | Verifying that enrich with real world text extract best sentence_ case5 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case5 | Enrich with real world text extract best sentence_ case5 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 58 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case6 | Verifying that enrich with real world text extract best sentence_ case6 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case6 | Enrich with real world text extract best sentence_ case6 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 59 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case7 | Verifying that enrich with real world text extract best sentence_ case7 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case7 | Enrich with real world text extract best sentence_ case7 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 60 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case8 | Verifying that enrich with real world text extract best sentence_ case8 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case8 | Enrich with real world text extract best sentence_ case8 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 61 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case9 | Verifying that enrich with real world text extract best sentence_ case9 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case9 | Enrich with real world text extract best sentence_ case9 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 62 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case10 | Verifying that enrich with real world text extract best sentence_ case10 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case10 | Enrich with real world text extract best sentence_ case10 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |
| 63 | | Enrich_WithRealWorldText_ShouldExtractBestSentence_Case11 | Verifying that enrich with real world text extract best sentence_ case11 | Setup with real world text -> Call Enrich -> Assert extract best sentence_ case11 | Enrich with real world text extract best sentence_ case11 | In scope: Enrich behavior, with real world text scenario. Out of scope: other scenarios and methods not under test. |

## ConstrainedScoreFusionProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Process_WithScoreFusion_Case1 | Verifying that process with score fusion case1 | Setup with score fusion -> Call Process -> Assert case1 | Process with score fusion case1 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Process_WithScoreFusion_Case2 | Verifying that process with score fusion case2 | Setup with score fusion -> Call Process -> Assert case2 | Process with score fusion case2 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_WithScoreFusion_Case3 | Verifying that process with score fusion case3 | Setup with score fusion -> Call Process -> Assert case3 | Process with score fusion case3 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Process_WithScoreFusion_Case4 | Verifying that process with score fusion case4 | Setup with score fusion -> Call Process -> Assert case4 | Process with score fusion case4 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Process_WithScoreFusion_Case5 | Verifying that process with score fusion case5 | Setup with score fusion -> Call Process -> Assert case5 | Process with score fusion case5 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Process_WithScoreFusion_Case6 | Verifying that process with score fusion case6 | Setup with score fusion -> Call Process -> Assert case6 | Process with score fusion case6 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Process_WithScoreFusion_Case7 | Verifying that process with score fusion case7 | Setup with score fusion -> Call Process -> Assert case7 | Process with score fusion case7 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Process_WithScoreFusion_Case8 | Verifying that process with score fusion case8 | Setup with score fusion -> Call Process -> Assert case8 | Process with score fusion case8 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Process_WithScoreFusion_Case9 | Verifying that process with score fusion case9 | Setup with score fusion -> Call Process -> Assert case9 | Process with score fusion case9 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Process_WithScoreFusion_Case10 | Verifying that process with score fusion case10 | Setup with score fusion -> Call Process -> Assert case10 | Process with score fusion case10 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Process_WithScoreFusion_Case11 | Verifying that process with score fusion case11 | Setup with score fusion -> Call Process -> Assert case11 | Process with score fusion case11 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Process_WithScoreFusion_Case12 | Verifying that process with score fusion case12 | Setup with score fusion -> Call Process -> Assert case12 | Process with score fusion case12 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Process_WithScoreFusion_Case13 | Verifying that process with score fusion case13 | Setup with score fusion -> Call Process -> Assert case13 | Process with score fusion case13 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |

## CrossEncoderRankerErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WhenServiceThrows_ShouldLogAndReturnOriginal | Verifying that rank when service throws log and return original | Setup mock to throw exception -> Call Rank -> Assert log and return original | Rank when service throws log and return original | In scope: error handling in Rank. Out of scope: successful execution paths. |
| 2 | | Rank_WhenServiceTimesOut_ShouldReturnOriginal | Verifying that rank when service times out returns original | Setup when service times out -> Call Rank -> Assert return original | Rank when service times out returns original | In scope: Rank behavior, when service times out scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WhenServiceReturnsNull_ShouldReturnOriginal | Verifying that rank when service returns null returns original | Setup with null input -> Call Rank -> Assert return original | Rank when service returns null returns original | In scope: null input handling for Rank. Out of scope: valid input scenarios. |
| 4 | | Rank_WhenDeserializationFails_ShouldReturnOriginal | Verifying that rank when deserialization fails returns original | Setup mock to throw exception -> Call Rank -> Assert return original | Rank when deserialization fails returns original | In scope: error handling in Rank. Out of scope: successful execution paths. |
| 5 | | Rank_ShouldEmitErrorMetric | Verifying that rank should emit error metric | Setup mock to throw exception -> Call Rank -> Assert expected behavior of Rank | Rank should emit error metric | In scope: error handling in Rank. Out of scope: successful execution paths. |

## CrossEncoderRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithCrossEncoderScoring_Case1 | Verifying that rank with cross encoder scoring case1 | Setup with cross encoder scoring -> Call Rank -> Assert case1 | Rank with cross encoder scoring case1 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithCrossEncoderScoring_Case2 | Verifying that rank with cross encoder scoring case2 | Setup with cross encoder scoring -> Call Rank -> Assert case2 | Rank with cross encoder scoring case2 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithCrossEncoderScoring_Case3 | Verifying that rank with cross encoder scoring case3 | Setup with cross encoder scoring -> Call Rank -> Assert case3 | Rank with cross encoder scoring case3 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithCrossEncoderScoring_Case4 | Verifying that rank with cross encoder scoring case4 | Setup with cross encoder scoring -> Call Rank -> Assert case4 | Rank with cross encoder scoring case4 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithCrossEncoderScoring_Case5 | Verifying that rank with cross encoder scoring case5 | Setup with cross encoder scoring -> Call Rank -> Assert case5 | Rank with cross encoder scoring case5 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithCrossEncoderScoring_Case6 | Verifying that rank with cross encoder scoring case6 | Setup with cross encoder scoring -> Call Rank -> Assert case6 | Rank with cross encoder scoring case6 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithCrossEncoderScoring_Case7 | Verifying that rank with cross encoder scoring case7 | Setup with cross encoder scoring -> Call Rank -> Assert case7 | Rank with cross encoder scoring case7 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithCrossEncoderScoring_Case8 | Verifying that rank with cross encoder scoring case8 | Setup with cross encoder scoring -> Call Rank -> Assert case8 | Rank with cross encoder scoring case8 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithCrossEncoderScoring_Case9 | Verifying that rank with cross encoder scoring case9 | Setup with cross encoder scoring -> Call Rank -> Assert case9 | Rank with cross encoder scoring case9 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithCrossEncoderScoring_Case10 | Verifying that rank with cross encoder scoring case10 | Setup with cross encoder scoring -> Call Rank -> Assert case10 | Rank with cross encoder scoring case10 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Rank_WithCrossEncoderScoring_Case11 | Verifying that rank with cross encoder scoring case11 | Setup with cross encoder scoring -> Call Rank -> Assert case11 | Rank with cross encoder scoring case11 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Rank_WithCrossEncoderScoring_Case12 | Verifying that rank with cross encoder scoring case12 | Setup with cross encoder scoring -> Call Rank -> Assert case12 | Rank with cross encoder scoring case12 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Rank_WithCrossEncoderScoring_Case13 | Verifying that rank with cross encoder scoring case13 | Setup with cross encoder scoring -> Call Rank -> Assert case13 | Rank with cross encoder scoring case13 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Rank_WithCrossEncoderScoring_Case14 | Verifying that rank with cross encoder scoring case14 | Setup with cross encoder scoring -> Call Rank -> Assert case14 | Rank with cross encoder scoring case14 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Rank_WithCrossEncoderScoring_Case15 | Verifying that rank with cross encoder scoring case15 | Setup with cross encoder scoring -> Call Rank -> Assert case15 | Rank with cross encoder scoring case15 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Rank_WithCrossEncoderScoring_Case16 | Verifying that rank with cross encoder scoring case16 | Setup with cross encoder scoring -> Call Rank -> Assert case16 | Rank with cross encoder scoring case16 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Rank_WithCrossEncoderScoring_Case17 | Verifying that rank with cross encoder scoring case17 | Setup with cross encoder scoring -> Call Rank -> Assert case17 | Rank with cross encoder scoring case17 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Rank_WithCrossEncoderScoring_Case18 | Verifying that rank with cross encoder scoring case18 | Setup with cross encoder scoring -> Call Rank -> Assert case18 | Rank with cross encoder scoring case18 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Rank_WithCrossEncoderScoring_Case19 | Verifying that rank with cross encoder scoring case19 | Setup with cross encoder scoring -> Call Rank -> Assert case19 | Rank with cross encoder scoring case19 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Rank_WithCrossEncoderScoring_Case20 | Verifying that rank with cross encoder scoring case20 | Setup with cross encoder scoring -> Call Rank -> Assert case20 | Rank with cross encoder scoring case20 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | Rank_WithCrossEncoderScoring_Case21 | Verifying that rank with cross encoder scoring case21 | Setup with cross encoder scoring -> Call Rank -> Assert case21 | Rank with cross encoder scoring case21 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | Rank_WithCrossEncoderScoring_Case22 | Verifying that rank with cross encoder scoring case22 | Setup with cross encoder scoring -> Call Rank -> Assert case22 | Rank with cross encoder scoring case22 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | Rank_WithCrossEncoderScoring_Case23 | Verifying that rank with cross encoder scoring case23 | Setup with cross encoder scoring -> Call Rank -> Assert case23 | Rank with cross encoder scoring case23 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | Rank_WithCrossEncoderScoring_Case24 | Verifying that rank with cross encoder scoring case24 | Setup with cross encoder scoring -> Call Rank -> Assert case24 | Rank with cross encoder scoring case24 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | Rank_WithCrossEncoderScoring_Case25 | Verifying that rank with cross encoder scoring case25 | Setup with cross encoder scoring -> Call Rank -> Assert case25 | Rank with cross encoder scoring case25 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | Rank_WithCrossEncoderScoring_Case26 | Verifying that rank with cross encoder scoring case26 | Setup with cross encoder scoring -> Call Rank -> Assert case26 | Rank with cross encoder scoring case26 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | Rank_WithCrossEncoderScoring_Case27 | Verifying that rank with cross encoder scoring case27 | Setup with cross encoder scoring -> Call Rank -> Assert case27 | Rank with cross encoder scoring case27 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | Rank_WithCrossEncoderScoring_Case28 | Verifying that rank with cross encoder scoring case28 | Setup with cross encoder scoring -> Call Rank -> Assert case28 | Rank with cross encoder scoring case28 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | Rank_WithCrossEncoderScoring_Case29 | Verifying that rank with cross encoder scoring case29 | Setup with cross encoder scoring -> Call Rank -> Assert case29 | Rank with cross encoder scoring case29 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 30 | | Rank_WithCrossEncoderScoring_Case30 | Verifying that rank with cross encoder scoring case30 | Setup with cross encoder scoring -> Call Rank -> Assert case30 | Rank with cross encoder scoring case30 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 31 | | Rank_WithCrossEncoderScoring_Case31 | Verifying that rank with cross encoder scoring case31 | Setup with cross encoder scoring -> Call Rank -> Assert case31 | Rank with cross encoder scoring case31 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 32 | | Rank_WithCrossEncoderScoring_Case32 | Verifying that rank with cross encoder scoring case32 | Setup with cross encoder scoring -> Call Rank -> Assert case32 | Rank with cross encoder scoring case32 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 33 | | Rank_WithCrossEncoderScoring_Case33 | Verifying that rank with cross encoder scoring case33 | Setup with cross encoder scoring -> Call Rank -> Assert case33 | Rank with cross encoder scoring case33 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 34 | | Rank_WithCrossEncoderScoring_Case34 | Verifying that rank with cross encoder scoring case34 | Setup with cross encoder scoring -> Call Rank -> Assert case34 | Rank with cross encoder scoring case34 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 35 | | Rank_WithCrossEncoderScoring_Case35 | Verifying that rank with cross encoder scoring case35 | Setup with cross encoder scoring -> Call Rank -> Assert case35 | Rank with cross encoder scoring case35 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 36 | | Rank_WithCrossEncoderScoring_Case36 | Verifying that rank with cross encoder scoring case36 | Setup with cross encoder scoring -> Call Rank -> Assert case36 | Rank with cross encoder scoring case36 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 37 | | Rank_WithCrossEncoderScoring_Case37 | Verifying that rank with cross encoder scoring case37 | Setup with cross encoder scoring -> Call Rank -> Assert case37 | Rank with cross encoder scoring case37 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 38 | | Rank_WithCrossEncoderScoring_Case38 | Verifying that rank with cross encoder scoring case38 | Setup with cross encoder scoring -> Call Rank -> Assert case38 | Rank with cross encoder scoring case38 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 39 | | Rank_WithCrossEncoderScoring_Case39 | Verifying that rank with cross encoder scoring case39 | Setup with cross encoder scoring -> Call Rank -> Assert case39 | Rank with cross encoder scoring case39 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 40 | | Rank_WithCrossEncoderScoring_Case40 | Verifying that rank with cross encoder scoring case40 | Setup with cross encoder scoring -> Call Rank -> Assert case40 | Rank with cross encoder scoring case40 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 41 | | Rank_WithCrossEncoderScoring_Case41 | Verifying that rank with cross encoder scoring case41 | Setup with cross encoder scoring -> Call Rank -> Assert case41 | Rank with cross encoder scoring case41 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 42 | | Rank_WithCrossEncoderScoring_Case42 | Verifying that rank with cross encoder scoring case42 | Setup with cross encoder scoring -> Call Rank -> Assert case42 | Rank with cross encoder scoring case42 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 43 | | Rank_WithCrossEncoderScoring_Case43 | Verifying that rank with cross encoder scoring case43 | Setup with cross encoder scoring -> Call Rank -> Assert case43 | Rank with cross encoder scoring case43 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 44 | | Rank_WithCrossEncoderScoring_Case44 | Verifying that rank with cross encoder scoring case44 | Setup with cross encoder scoring -> Call Rank -> Assert case44 | Rank with cross encoder scoring case44 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 45 | | Rank_WithCrossEncoderScoring_Case45 | Verifying that rank with cross encoder scoring case45 | Setup with cross encoder scoring -> Call Rank -> Assert case45 | Rank with cross encoder scoring case45 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |
| 46 | | Rank_WithCrossEncoderScoring_Case46 | Verifying that rank with cross encoder scoring case46 | Setup with cross encoder scoring -> Call Rank -> Assert case46 | Rank with cross encoder scoring case46 | In scope: Rank behavior, with cross encoder scoring scenario. Out of scope: other scenarios and methods not under test. |

## KeywordEnricherTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithKeywordProcessing_Case1 | Verifying that enrich with keyword processing case1 | Setup with keyword processing -> Call Enrich -> Assert case1 | Enrich with keyword processing case1 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithKeywordProcessing_Case2 | Verifying that enrich with keyword processing case2 | Setup with keyword processing -> Call Enrich -> Assert case2 | Enrich with keyword processing case2 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithKeywordProcessing_Case3 | Verifying that enrich with keyword processing case3 | Setup with keyword processing -> Call Enrich -> Assert case3 | Enrich with keyword processing case3 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithKeywordProcessing_Case4 | Verifying that enrich with keyword processing case4 | Setup with keyword processing -> Call Enrich -> Assert case4 | Enrich with keyword processing case4 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithKeywordProcessing_Case5 | Verifying that enrich with keyword processing case5 | Setup with keyword processing -> Call Enrich -> Assert case5 | Enrich with keyword processing case5 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithKeywordProcessing_Case6 | Verifying that enrich with keyword processing case6 | Setup with keyword processing -> Call Enrich -> Assert case6 | Enrich with keyword processing case6 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Enrich_WithKeywordProcessing_Case7 | Verifying that enrich with keyword processing case7 | Setup with keyword processing -> Call Enrich -> Assert case7 | Enrich with keyword processing case7 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Enrich_WithKeywordProcessing_Case8 | Verifying that enrich with keyword processing case8 | Setup with keyword processing -> Call Enrich -> Assert case8 | Enrich with keyword processing case8 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Enrich_WithKeywordProcessing_Case9 | Verifying that enrich with keyword processing case9 | Setup with keyword processing -> Call Enrich -> Assert case9 | Enrich with keyword processing case9 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Enrich_WithKeywordProcessing_Case10 | Verifying that enrich with keyword processing case10 | Setup with keyword processing -> Call Enrich -> Assert case10 | Enrich with keyword processing case10 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Enrich_WithKeywordProcessing_Case11 | Verifying that enrich with keyword processing case11 | Setup with keyword processing -> Call Enrich -> Assert case11 | Enrich with keyword processing case11 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Enrich_WithKeywordProcessing_Case12 | Verifying that enrich with keyword processing case12 | Setup with keyword processing -> Call Enrich -> Assert case12 | Enrich with keyword processing case12 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Enrich_WithKeywordProcessing_Case13 | Verifying that enrich with keyword processing case13 | Setup with keyword processing -> Call Enrich -> Assert case13 | Enrich with keyword processing case13 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Enrich_WithKeywordProcessing_Case14 | Verifying that enrich with keyword processing case14 | Setup with keyword processing -> Call Enrich -> Assert case14 | Enrich with keyword processing case14 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Enrich_WithKeywordProcessing_Case15 | Verifying that enrich with keyword processing case15 | Setup with keyword processing -> Call Enrich -> Assert case15 | Enrich with keyword processing case15 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Enrich_WithKeywordProcessing_Case16 | Verifying that enrich with keyword processing case16 | Setup with keyword processing -> Call Enrich -> Assert case16 | Enrich with keyword processing case16 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Enrich_WithKeywordProcessing_Case17 | Verifying that enrich with keyword processing case17 | Setup with keyword processing -> Call Enrich -> Assert case17 | Enrich with keyword processing case17 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Enrich_WithKeywordProcessing_Case18 | Verifying that enrich with keyword processing case18 | Setup with keyword processing -> Call Enrich -> Assert case18 | Enrich with keyword processing case18 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Enrich_WithKeywordProcessing_Case19 | Verifying that enrich with keyword processing case19 | Setup with keyword processing -> Call Enrich -> Assert case19 | Enrich with keyword processing case19 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Enrich_WithKeywordProcessing_Case20 | Verifying that enrich with keyword processing case20 | Setup with keyword processing -> Call Enrich -> Assert case20 | Enrich with keyword processing case20 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | Enrich_WithKeywordProcessing_Case21 | Verifying that enrich with keyword processing case21 | Setup with keyword processing -> Call Enrich -> Assert case21 | Enrich with keyword processing case21 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | Enrich_WithKeywordProcessing_Case22 | Verifying that enrich with keyword processing case22 | Setup with keyword processing -> Call Enrich -> Assert case22 | Enrich with keyword processing case22 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | Enrich_WithKeywordProcessing_Case23 | Verifying that enrich with keyword processing case23 | Setup with keyword processing -> Call Enrich -> Assert case23 | Enrich with keyword processing case23 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | Enrich_WithKeywordProcessing_Case24 | Verifying that enrich with keyword processing case24 | Setup with keyword processing -> Call Enrich -> Assert case24 | Enrich with keyword processing case24 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | Enrich_WithKeywordProcessing_Case25 | Verifying that enrich with keyword processing case25 | Setup with keyword processing -> Call Enrich -> Assert case25 | Enrich with keyword processing case25 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | Enrich_WithKeywordProcessing_Case26 | Verifying that enrich with keyword processing case26 | Setup with keyword processing -> Call Enrich -> Assert case26 | Enrich with keyword processing case26 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | Enrich_WithKeywordProcessing_Case27 | Verifying that enrich with keyword processing case27 | Setup with keyword processing -> Call Enrich -> Assert case27 | Enrich with keyword processing case27 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 28 | | Enrich_WithKeywordProcessing_Case28 | Verifying that enrich with keyword processing case28 | Setup with keyword processing -> Call Enrich -> Assert case28 | Enrich with keyword processing case28 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | Enrich_WithKeywordProcessing_Case29 | Verifying that enrich with keyword processing case29 | Setup with keyword processing -> Call Enrich -> Assert case29 | Enrich with keyword processing case29 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 30 | | Enrich_WithKeywordProcessing_Case30 | Verifying that enrich with keyword processing case30 | Setup with keyword processing -> Call Enrich -> Assert case30 | Enrich with keyword processing case30 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 31 | | Enrich_WithKeywordProcessing_Case31 | Verifying that enrich with keyword processing case31 | Setup with keyword processing -> Call Enrich -> Assert case31 | Enrich with keyword processing case31 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 32 | | Enrich_WithKeywordProcessing_Case32 | Verifying that enrich with keyword processing case32 | Setup with keyword processing -> Call Enrich -> Assert case32 | Enrich with keyword processing case32 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 33 | | Enrich_WithKeywordProcessing_Case33 | Verifying that enrich with keyword processing case33 | Setup with keyword processing -> Call Enrich -> Assert case33 | Enrich with keyword processing case33 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 34 | | Enrich_WithKeywordProcessing_Case34 | Verifying that enrich with keyword processing case34 | Setup with keyword processing -> Call Enrich -> Assert case34 | Enrich with keyword processing case34 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 35 | | Enrich_WithKeywordProcessing_Case35 | Verifying that enrich with keyword processing case35 | Setup with keyword processing -> Call Enrich -> Assert case35 | Enrich with keyword processing case35 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 36 | | Enrich_WithKeywordProcessing_Case36 | Verifying that enrich with keyword processing case36 | Setup with keyword processing -> Call Enrich -> Assert case36 | Enrich with keyword processing case36 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 37 | | Enrich_WithKeywordProcessing_Case37 | Verifying that enrich with keyword processing case37 | Setup with keyword processing -> Call Enrich -> Assert case37 | Enrich with keyword processing case37 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 38 | | Enrich_WithKeywordProcessing_Case38 | Verifying that enrich with keyword processing case38 | Setup with keyword processing -> Call Enrich -> Assert case38 | Enrich with keyword processing case38 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 39 | | Enrich_WithKeywordProcessing_Case39 | Verifying that enrich with keyword processing case39 | Setup with keyword processing -> Call Enrich -> Assert case39 | Enrich with keyword processing case39 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 40 | | Enrich_WithKeywordProcessing_Case40 | Verifying that enrich with keyword processing case40 | Setup with keyword processing -> Call Enrich -> Assert case40 | Enrich with keyword processing case40 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 41 | | Enrich_WithKeywordProcessing_Case41 | Verifying that enrich with keyword processing case41 | Setup with keyword processing -> Call Enrich -> Assert case41 | Enrich with keyword processing case41 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 42 | | Enrich_WithKeywordProcessing_Case42 | Verifying that enrich with keyword processing case42 | Setup with keyword processing -> Call Enrich -> Assert case42 | Enrich with keyword processing case42 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 43 | | Enrich_WithKeywordProcessing_Case43 | Verifying that enrich with keyword processing case43 | Setup with keyword processing -> Call Enrich -> Assert case43 | Enrich with keyword processing case43 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 44 | | Enrich_WithKeywordProcessing_Case44 | Verifying that enrich with keyword processing case44 | Setup with keyword processing -> Call Enrich -> Assert case44 | Enrich with keyword processing case44 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 45 | | Enrich_WithKeywordProcessing_Case45 | Verifying that enrich with keyword processing case45 | Setup with keyword processing -> Call Enrich -> Assert case45 | Enrich with keyword processing case45 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 46 | | Enrich_WithKeywordProcessing_Case46 | Verifying that enrich with keyword processing case46 | Setup with keyword processing -> Call Enrich -> Assert case46 | Enrich with keyword processing case46 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 47 | | Enrich_WithKeywordProcessing_Case47 | Verifying that enrich with keyword processing case47 | Setup with keyword processing -> Call Enrich -> Assert case47 | Enrich with keyword processing case47 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 48 | | Enrich_WithKeywordProcessing_Case48 | Verifying that enrich with keyword processing case48 | Setup with keyword processing -> Call Enrich -> Assert case48 | Enrich with keyword processing case48 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 49 | | Enrich_WithKeywordProcessing_Case49 | Verifying that enrich with keyword processing case49 | Setup with keyword processing -> Call Enrich -> Assert case49 | Enrich with keyword processing case49 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 50 | | Enrich_WithKeywordProcessing_Case50 | Verifying that enrich with keyword processing case50 | Setup with keyword processing -> Call Enrich -> Assert case50 | Enrich with keyword processing case50 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 51 | | Enrich_WithKeywordProcessing_Case51 | Verifying that enrich with keyword processing case51 | Setup with keyword processing -> Call Enrich -> Assert case51 | Enrich with keyword processing case51 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 52 | | Enrich_WithKeywordProcessing_Case52 | Verifying that enrich with keyword processing case52 | Setup with keyword processing -> Call Enrich -> Assert case52 | Enrich with keyword processing case52 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 53 | | Enrich_WithKeywordProcessing_Case53 | Verifying that enrich with keyword processing case53 | Setup with keyword processing -> Call Enrich -> Assert case53 | Enrich with keyword processing case53 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 54 | | Enrich_WithKeywordProcessing_Case54 | Verifying that enrich with keyword processing case54 | Setup with keyword processing -> Call Enrich -> Assert case54 | Enrich with keyword processing case54 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 55 | | Enrich_WithKeywordProcessing_Case55 | Verifying that enrich with keyword processing case55 | Setup with keyword processing -> Call Enrich -> Assert case55 | Enrich with keyword processing case55 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 56 | | Enrich_WithKeywordProcessing_Case56 | Verifying that enrich with keyword processing case56 | Setup with keyword processing -> Call Enrich -> Assert case56 | Enrich with keyword processing case56 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 57 | | Enrich_WithKeywordProcessing_Case57 | Verifying that enrich with keyword processing case57 | Setup with keyword processing -> Call Enrich -> Assert case57 | Enrich with keyword processing case57 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 58 | | Enrich_WithKeywordProcessing_Case58 | Verifying that enrich with keyword processing case58 | Setup with keyword processing -> Call Enrich -> Assert case58 | Enrich with keyword processing case58 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 59 | | Enrich_WithKeywordProcessing_Case59 | Verifying that enrich with keyword processing case59 | Setup with keyword processing -> Call Enrich -> Assert case59 | Enrich with keyword processing case59 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 60 | | Enrich_WithKeywordProcessing_Case60 | Verifying that enrich with keyword processing case60 | Setup with keyword processing -> Call Enrich -> Assert case60 | Enrich with keyword processing case60 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 61 | | Enrich_WithKeywordProcessing_Case61 | Verifying that enrich with keyword processing case61 | Setup with keyword processing -> Call Enrich -> Assert case61 | Enrich with keyword processing case61 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 62 | | Enrich_WithKeywordProcessing_Case62 | Verifying that enrich with keyword processing case62 | Setup with keyword processing -> Call Enrich -> Assert case62 | Enrich with keyword processing case62 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 63 | | Enrich_WithKeywordProcessing_Case63 | Verifying that enrich with keyword processing case63 | Setup with keyword processing -> Call Enrich -> Assert case63 | Enrich with keyword processing case63 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 64 | | Enrich_WithKeywordProcessing_Case64 | Verifying that enrich with keyword processing case64 | Setup with keyword processing -> Call Enrich -> Assert case64 | Enrich with keyword processing case64 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 65 | | Enrich_WithKeywordProcessing_Case65 | Verifying that enrich with keyword processing case65 | Setup with keyword processing -> Call Enrich -> Assert case65 | Enrich with keyword processing case65 | In scope: Enrich behavior, with keyword processing scenario. Out of scope: other scenarios and methods not under test. |

## KeywordSnippetHelperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GenerateSnippet_Case1 | Verifying that generate snippet case1 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case1 | In scope: GenerateSnippet behavior, case1 scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GenerateSnippet_Case2 | Verifying that generate snippet case2 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case2 | In scope: GenerateSnippet behavior, case2 scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GenerateSnippet_Case3 | Verifying that generate snippet case3 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case3 | In scope: GenerateSnippet behavior, case3 scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GenerateSnippet_Case4 | Verifying that generate snippet case4 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case4 | In scope: GenerateSnippet behavior, case4 scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GenerateSnippet_Case5 | Verifying that generate snippet case5 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case5 | In scope: GenerateSnippet behavior, case5 scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GenerateSnippet_Case6 | Verifying that generate snippet case6 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case6 | In scope: GenerateSnippet behavior, case6 scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GenerateSnippet_Case7 | Verifying that generate snippet case7 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case7 | In scope: GenerateSnippet behavior, case7 scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GenerateSnippet_Case8 | Verifying that generate snippet case8 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case8 | In scope: GenerateSnippet behavior, case8 scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GenerateSnippet_Case9 | Verifying that generate snippet case9 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case9 | In scope: GenerateSnippet behavior, case9 scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GenerateSnippet_Case10 | Verifying that generate snippet case10 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case10 | In scope: GenerateSnippet behavior, case10 scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GenerateSnippet_Case11 | Verifying that generate snippet case11 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case11 | In scope: GenerateSnippet behavior, case11 scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GenerateSnippet_Case12 | Verifying that generate snippet case12 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case12 | In scope: GenerateSnippet behavior, case12 scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GenerateSnippet_Case13 | Verifying that generate snippet case13 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case13 | In scope: GenerateSnippet behavior, case13 scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GenerateSnippet_Case14 | Verifying that generate snippet case14 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case14 | In scope: GenerateSnippet behavior, case14 scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GenerateSnippet_Case15 | Verifying that generate snippet case15 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case15 | In scope: GenerateSnippet behavior, case15 scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | GenerateSnippet_Case16 | Verifying that generate snippet case16 | Setup test data and mocks -> Call GenerateSnippet -> Assert expected behavior of GenerateSnippet | GenerateSnippet case16 | In scope: GenerateSnippet behavior, case16 scenario. Out of scope: other scenarios and methods not under test. |

## OrganicOnlyBoxRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_ShouldExcludeSpoResults | Verifying that rank should exclude spo results | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should exclude spo results | In scope: Rank behavior, should exclude spo results scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithAllOrganicResults_ShouldReturnAll | Verifying that rank with all organic results returns all | Setup with all organic results -> Call Rank -> Assert return all | Rank with all organic results returns all | In scope: Rank behavior, with all organic results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithAllSpoResults_ShouldReturnEmpty | Verifying that rank with all spo results returns empty | Setup with all spo results -> Call Rank -> Assert returns empty collection | Rank with all spo results returns empty | In scope: Rank behavior, with all spo results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_ShouldPreserveOrganicOrder | Verifying that rank should preserve organic order | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should preserve organic order | In scope: Rank behavior, should preserve organic order scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithMixedResults_ShouldReturnOnlyOrganic | Verifying that rank with mixed results returns only organic | Setup with mixed results -> Call Rank -> Assert return only organic | Rank with mixed results returns only organic | In scope: Rank behavior, with mixed results scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithEmptyResults_ShouldReturnEmpty | Verifying that rank with empty results returns empty | Setup with empty input -> Call Rank -> Assert returns empty collection | Rank with empty results returns empty | In scope: empty input handling for Rank. Out of scope: non-empty input scenarios. |
| 7 | | Rank_ShouldEmitMetrics | Verifying that rank should emit metrics | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should emit metrics | In scope: Rank behavior, should emit metrics scenario. Out of scope: other scenarios and methods not under test. |

## PageVectorSearchEnricherErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WhenServiceThrows_ShouldLogAndReturnOriginal | Verifying that enrich when service throws log and return original | Setup mock to throw exception -> Call Enrich -> Assert log and return original | Enrich when service throws log and return original | In scope: error handling in Enrich. Out of scope: successful execution paths. |
| 2 | | Enrich_WhenServiceTimesOut_ShouldReturnOriginal | Verifying that enrich when service times out returns original | Setup when service times out -> Call Enrich -> Assert return original | Enrich when service times out returns original | In scope: Enrich behavior, when service times out scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WhenServiceReturnsNull_ShouldReturnOriginal | Verifying that enrich when service returns null returns original | Setup with null input -> Call Enrich -> Assert return original | Enrich when service returns null returns original | In scope: null input handling for Enrich. Out of scope: valid input scenarios. |
| 4 | | Enrich_WhenDeserializationFails_ShouldReturnOriginal | Verifying that enrich when deserialization fails returns original | Setup mock to throw exception -> Call Enrich -> Assert return original | Enrich when deserialization fails returns original | In scope: error handling in Enrich. Out of scope: successful execution paths. |
| 5 | | Enrich_ShouldEmitErrorMetric | Verifying that enrich should emit error metric | Setup mock to throw exception -> Call Enrich -> Assert expected behavior of Enrich | Enrich should emit error metric | In scope: error handling in Enrich. Out of scope: successful execution paths. |
| 6 | | Enrich_WhenPartialFailure_ShouldReturnPartialResults | Verifying that enrich when partial failure returns partial results | Setup mock to throw exception -> Call Enrich -> Assert return partial results | Enrich when partial failure returns partial results | In scope: error handling in Enrich. Out of scope: successful execution paths. |
| 7 | | Enrich_WhenCancelled_ShouldThrowOperationCancelledException | Verifying that enrich when cancelled throw operation cancelled exception | Setup when cancelled -> Call Enrich -> Assert exception is thrown | Enrich when cancelled throw operation cancelled exception | In scope: Enrich behavior, when cancelled scenario. Out of scope: other scenarios and methods not under test. |

## PageVectorSearchEnricherTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithPageVectorSearch_Case1 | Verifying that enrich with page vector search case1 | Setup with page vector search -> Call Enrich -> Assert case1 | Enrich with page vector search case1 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithPageVectorSearch_Case2 | Verifying that enrich with page vector search case2 | Setup with page vector search -> Call Enrich -> Assert case2 | Enrich with page vector search case2 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithPageVectorSearch_Case3 | Verifying that enrich with page vector search case3 | Setup with page vector search -> Call Enrich -> Assert case3 | Enrich with page vector search case3 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithPageVectorSearch_Case4 | Verifying that enrich with page vector search case4 | Setup with page vector search -> Call Enrich -> Assert case4 | Enrich with page vector search case4 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithPageVectorSearch_Case5 | Verifying that enrich with page vector search case5 | Setup with page vector search -> Call Enrich -> Assert case5 | Enrich with page vector search case5 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithPageVectorSearch_Case6 | Verifying that enrich with page vector search case6 | Setup with page vector search -> Call Enrich -> Assert case6 | Enrich with page vector search case6 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Enrich_WithPageVectorSearch_Case7 | Verifying that enrich with page vector search case7 | Setup with page vector search -> Call Enrich -> Assert case7 | Enrich with page vector search case7 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Enrich_WithPageVectorSearch_Case8 | Verifying that enrich with page vector search case8 | Setup with page vector search -> Call Enrich -> Assert case8 | Enrich with page vector search case8 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Enrich_WithPageVectorSearch_Case9 | Verifying that enrich with page vector search case9 | Setup with page vector search -> Call Enrich -> Assert case9 | Enrich with page vector search case9 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Enrich_WithPageVectorSearch_Case10 | Verifying that enrich with page vector search case10 | Setup with page vector search -> Call Enrich -> Assert case10 | Enrich with page vector search case10 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Enrich_WithPageVectorSearch_Case11 | Verifying that enrich with page vector search case11 | Setup with page vector search -> Call Enrich -> Assert case11 | Enrich with page vector search case11 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Enrich_WithPageVectorSearch_Case12 | Verifying that enrich with page vector search case12 | Setup with page vector search -> Call Enrich -> Assert case12 | Enrich with page vector search case12 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Enrich_WithPageVectorSearch_Case13 | Verifying that enrich with page vector search case13 | Setup with page vector search -> Call Enrich -> Assert case13 | Enrich with page vector search case13 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Enrich_WithPageVectorSearch_Case14 | Verifying that enrich with page vector search case14 | Setup with page vector search -> Call Enrich -> Assert case14 | Enrich with page vector search case14 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Enrich_WithPageVectorSearch_Case15 | Verifying that enrich with page vector search case15 | Setup with page vector search -> Call Enrich -> Assert case15 | Enrich with page vector search case15 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Enrich_WithPageVectorSearch_Case16 | Verifying that enrich with page vector search case16 | Setup with page vector search -> Call Enrich -> Assert case16 | Enrich with page vector search case16 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Enrich_WithPageVectorSearch_Case17 | Verifying that enrich with page vector search case17 | Setup with page vector search -> Call Enrich -> Assert case17 | Enrich with page vector search case17 | In scope: Enrich behavior, with page vector search scenario. Out of scope: other scenarios and methods not under test. |

## PresortRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithPresort_Case1 | Verifying that rank with presort case1 | Setup with presort -> Call Rank -> Assert case1 | Rank with presort case1 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithPresort_Case2 | Verifying that rank with presort case2 | Setup with presort -> Call Rank -> Assert case2 | Rank with presort case2 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithPresort_Case3 | Verifying that rank with presort case3 | Setup with presort -> Call Rank -> Assert case3 | Rank with presort case3 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithPresort_Case4 | Verifying that rank with presort case4 | Setup with presort -> Call Rank -> Assert case4 | Rank with presort case4 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithPresort_Case5 | Verifying that rank with presort case5 | Setup with presort -> Call Rank -> Assert case5 | Rank with presort case5 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithPresort_Case6 | Verifying that rank with presort case6 | Setup with presort -> Call Rank -> Assert case6 | Rank with presort case6 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithPresort_Case7 | Verifying that rank with presort case7 | Setup with presort -> Call Rank -> Assert case7 | Rank with presort case7 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithPresort_Case8 | Verifying that rank with presort case8 | Setup with presort -> Call Rank -> Assert case8 | Rank with presort case8 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithPresort_Case9 | Verifying that rank with presort case9 | Setup with presort -> Call Rank -> Assert case9 | Rank with presort case9 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithPresort_Case10 | Verifying that rank with presort case10 | Setup with presort -> Call Rank -> Assert case10 | Rank with presort case10 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Rank_WithPresort_Case11 | Verifying that rank with presort case11 | Setup with presort -> Call Rank -> Assert case11 | Rank with presort case11 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Rank_WithPresort_Case12 | Verifying that rank with presort case12 | Setup with presort -> Call Rank -> Assert case12 | Rank with presort case12 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Rank_WithPresort_Case13 | Verifying that rank with presort case13 | Setup with presort -> Call Rank -> Assert case13 | Rank with presort case13 | In scope: Rank behavior, with presort scenario. Out of scope: other scenarios and methods not under test. |

## RankRandomizerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Randomize_ShouldShuffleResults | Verifying that randomize should shuffle results | Setup test data and mocks -> Call Randomize -> Assert expected behavior of Randomize | Randomize should shuffle results | In scope: Randomize behavior, should shuffle results scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Randomize_WithSeed_ShouldBeReproducible | Verifying that randomize with seed is reproducible | Setup with seed -> Call Randomize -> Assert be reproducible | Randomize with seed is reproducible | In scope: Randomize behavior, with seed scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Randomize_WithSingleResult_ShouldReturnAsIs | Verifying that randomize with single result returns as is | Setup with single result -> Call Randomize -> Assert return as is | Randomize with single result returns as is | In scope: Randomize behavior, with single result scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Randomize_WithEmptyResults_ShouldReturnEmpty | Verifying that randomize with empty results returns empty | Setup with empty input -> Call Randomize -> Assert returns empty collection | Randomize with empty results returns empty | In scope: empty input handling for Randomize. Out of scope: non-empty input scenarios. |
| 5 | | Randomize_ShouldPreserveAllResults | Verifying that randomize should preserve all results | Setup test data and mocks -> Call Randomize -> Assert expected behavior of Randomize | Randomize should preserve all results | In scope: Randomize behavior, should preserve all results scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Randomize_ShouldChangeOrder | Verifying that randomize should change order | Setup test data and mocks -> Call Randomize -> Assert expected behavior of Randomize | Randomize should change order | In scope: Randomize behavior, should change order scenario. Out of scope: other scenarios and methods not under test. |

## RankingHelpersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | NormalizeScores_ShouldNormalizeTo01Range | Verifying that normalize scores should normalize to01 range | Setup test data and mocks -> Call NormalizeScores -> Assert expected behavior of NormalizeScores | NormalizeScores should normalize to01 range | In scope: NormalizeScores behavior, should normalize to01 range scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | NormalizeScores_WithAllSameScores_ShouldReturnEqual | Verifying that normalize scores with all same scores returns equal | Setup with all same scores -> Call NormalizeScores -> Assert return equal | NormalizeScores with all same scores returns equal | In scope: NormalizeScores behavior, with all same scores scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | NormalizeScores_WithSingleScore_ShouldReturnOne | Verifying that normalize scores with single score returns one | Setup with single score -> Call NormalizeScores -> Assert return one | NormalizeScores with single score returns one | In scope: NormalizeScores behavior, with single score scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | NormalizeScores_WithEmptyScores_ShouldReturnEmpty | Verifying that normalize scores with empty scores returns empty | Setup with empty input -> Call NormalizeScores -> Assert returns empty collection | NormalizeScores with empty scores returns empty | In scope: empty input handling for NormalizeScores. Out of scope: non-empty input scenarios. |
| 5 | | NormalizeScores_WithNegativeScores_ShouldHandleCorrectly | Verifying that normalize scores with negative scores handle correctly | Setup with negative scores -> Call NormalizeScores -> Assert handle correctly | NormalizeScores with negative scores handle correctly | In scope: NormalizeScores behavior, with negative scores scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | CombineScores_ShouldWeightAndSum | Verifying that combine scores should weight and sum | Setup test data and mocks -> Call CombineScores -> Assert expected behavior of CombineScores | CombineScores should weight and sum | In scope: CombineScores behavior, should weight and sum scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | CombineScores_WithZeroWeights_ShouldReturnZero | Verifying that combine scores with zero weights returns zero | Setup with zero weights -> Call CombineScores -> Assert return zero | CombineScores with zero weights returns zero | In scope: CombineScores behavior, with zero weights scenario. Out of scope: other scenarios and methods not under test. |

## ScoreFusionProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Process_WithScoreFusion_Case1 | Verifying that process with score fusion case1 | Setup with score fusion -> Call Process -> Assert case1 | Process with score fusion case1 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Process_WithScoreFusion_Case2 | Verifying that process with score fusion case2 | Setup with score fusion -> Call Process -> Assert case2 | Process with score fusion case2 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Process_WithScoreFusion_Case3 | Verifying that process with score fusion case3 | Setup with score fusion -> Call Process -> Assert case3 | Process with score fusion case3 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Process_WithScoreFusion_Case4 | Verifying that process with score fusion case4 | Setup with score fusion -> Call Process -> Assert case4 | Process with score fusion case4 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Process_WithScoreFusion_Case5 | Verifying that process with score fusion case5 | Setup with score fusion -> Call Process -> Assert case5 | Process with score fusion case5 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Process_WithScoreFusion_Case6 | Verifying that process with score fusion case6 | Setup with score fusion -> Call Process -> Assert case6 | Process with score fusion case6 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Process_WithScoreFusion_Case7 | Verifying that process with score fusion case7 | Setup with score fusion -> Call Process -> Assert case7 | Process with score fusion case7 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Process_WithScoreFusion_Case8 | Verifying that process with score fusion case8 | Setup with score fusion -> Call Process -> Assert case8 | Process with score fusion case8 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Process_WithScoreFusion_Case9 | Verifying that process with score fusion case9 | Setup with score fusion -> Call Process -> Assert case9 | Process with score fusion case9 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Process_WithScoreFusion_Case10 | Verifying that process with score fusion case10 | Setup with score fusion -> Call Process -> Assert case10 | Process with score fusion case10 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Process_WithScoreFusion_Case11 | Verifying that process with score fusion case11 | Setup with score fusion -> Call Process -> Assert case11 | Process with score fusion case11 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Process_WithScoreFusion_Case12 | Verifying that process with score fusion case12 | Setup with score fusion -> Call Process -> Assert case12 | Process with score fusion case12 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Process_WithScoreFusion_Case13 | Verifying that process with score fusion case13 | Setup with score fusion -> Call Process -> Assert case13 | Process with score fusion case13 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Process_WithScoreFusion_Case14 | Verifying that process with score fusion case14 | Setup with score fusion -> Call Process -> Assert case14 | Process with score fusion case14 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Process_WithScoreFusion_Case15 | Verifying that process with score fusion case15 | Setup with score fusion -> Call Process -> Assert case15 | Process with score fusion case15 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Process_WithScoreFusion_Case16 | Verifying that process with score fusion case16 | Setup with score fusion -> Call Process -> Assert case16 | Process with score fusion case16 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Process_WithScoreFusion_Case17 | Verifying that process with score fusion case17 | Setup with score fusion -> Call Process -> Assert case17 | Process with score fusion case17 | In scope: Process behavior, with score fusion scenario. Out of scope: other scenarios and methods not under test. |

## ScorersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Score_WithScorerImplementation_Case1 | Verifying that score with scorer implementation case1 | Setup with scorer implementation -> Call Score -> Assert case1 | Score with scorer implementation case1 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_WithScorerImplementation_Case2 | Verifying that score with scorer implementation case2 | Setup with scorer implementation -> Call Score -> Assert case2 | Score with scorer implementation case2 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Score_WithScorerImplementation_Case3 | Verifying that score with scorer implementation case3 | Setup with scorer implementation -> Call Score -> Assert case3 | Score with scorer implementation case3 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Score_WithScorerImplementation_Case4 | Verifying that score with scorer implementation case4 | Setup with scorer implementation -> Call Score -> Assert case4 | Score with scorer implementation case4 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Score_WithScorerImplementation_Case5 | Verifying that score with scorer implementation case5 | Setup with scorer implementation -> Call Score -> Assert case5 | Score with scorer implementation case5 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Score_WithScorerImplementation_Case6 | Verifying that score with scorer implementation case6 | Setup with scorer implementation -> Call Score -> Assert case6 | Score with scorer implementation case6 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Score_WithScorerImplementation_Case7 | Verifying that score with scorer implementation case7 | Setup with scorer implementation -> Call Score -> Assert case7 | Score with scorer implementation case7 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Score_WithScorerImplementation_Case8 | Verifying that score with scorer implementation case8 | Setup with scorer implementation -> Call Score -> Assert case8 | Score with scorer implementation case8 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Score_WithScorerImplementation_Case9 | Verifying that score with scorer implementation case9 | Setup with scorer implementation -> Call Score -> Assert case9 | Score with scorer implementation case9 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Score_WithScorerImplementation_Case10 | Verifying that score with scorer implementation case10 | Setup with scorer implementation -> Call Score -> Assert case10 | Score with scorer implementation case10 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Score_WithScorerImplementation_Case11 | Verifying that score with scorer implementation case11 | Setup with scorer implementation -> Call Score -> Assert case11 | Score with scorer implementation case11 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Score_WithScorerImplementation_Case12 | Verifying that score with scorer implementation case12 | Setup with scorer implementation -> Call Score -> Assert case12 | Score with scorer implementation case12 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Score_WithScorerImplementation_Case13 | Verifying that score with scorer implementation case13 | Setup with scorer implementation -> Call Score -> Assert case13 | Score with scorer implementation case13 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Score_WithScorerImplementation_Case14 | Verifying that score with scorer implementation case14 | Setup with scorer implementation -> Call Score -> Assert case14 | Score with scorer implementation case14 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Score_WithScorerImplementation_Case15 | Verifying that score with scorer implementation case15 | Setup with scorer implementation -> Call Score -> Assert case15 | Score with scorer implementation case15 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Score_WithScorerImplementation_Case16 | Verifying that score with scorer implementation case16 | Setup with scorer implementation -> Call Score -> Assert case16 | Score with scorer implementation case16 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Score_WithScorerImplementation_Case17 | Verifying that score with scorer implementation case17 | Setup with scorer implementation -> Call Score -> Assert case17 | Score with scorer implementation case17 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Score_WithScorerImplementation_Case18 | Verifying that score with scorer implementation case18 | Setup with scorer implementation -> Call Score -> Assert case18 | Score with scorer implementation case18 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Score_WithScorerImplementation_Case19 | Verifying that score with scorer implementation case19 | Setup with scorer implementation -> Call Score -> Assert case19 | Score with scorer implementation case19 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Score_WithScorerImplementation_Case20 | Verifying that score with scorer implementation case20 | Setup with scorer implementation -> Call Score -> Assert case20 | Score with scorer implementation case20 | In scope: Score behavior, with scorer implementation scenario. Out of scope: other scenarios and methods not under test. |

## VectorSearchEnricherBatchTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithBatchVectorSearch_Case1 | Verifying that enrich with batch vector search case1 | Setup with batch vector search -> Call Enrich -> Assert case1 | Enrich with batch vector search case1 | In scope: Enrich behavior, with batch vector search scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithBatchVectorSearch_Case2 | Verifying that enrich with batch vector search case2 | Setup with batch vector search -> Call Enrich -> Assert case2 | Enrich with batch vector search case2 | In scope: Enrich behavior, with batch vector search scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithBatchVectorSearch_Case3 | Verifying that enrich with batch vector search case3 | Setup with batch vector search -> Call Enrich -> Assert case3 | Enrich with batch vector search case3 | In scope: Enrich behavior, with batch vector search scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithBatchVectorSearch_Case4 | Verifying that enrich with batch vector search case4 | Setup with batch vector search -> Call Enrich -> Assert case4 | Enrich with batch vector search case4 | In scope: Enrich behavior, with batch vector search scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithBatchVectorSearch_Case5 | Verifying that enrich with batch vector search case5 | Setup with batch vector search -> Call Enrich -> Assert case5 | Enrich with batch vector search case5 | In scope: Enrich behavior, with batch vector search scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithBatchVectorSearch_Case6 | Verifying that enrich with batch vector search case6 | Setup with batch vector search -> Call Enrich -> Assert case6 | Enrich with batch vector search case6 | In scope: Enrich behavior, with batch vector search scenario. Out of scope: other scenarios and methods not under test. |

## VectorSearchEnricherErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WhenServiceThrows_ShouldLogAndReturnOriginal | Verifying that enrich when service throws log and return original | Setup mock to throw exception -> Call Enrich -> Assert log and return original | Enrich when service throws log and return original | In scope: error handling in Enrich. Out of scope: successful execution paths. |
| 2 | | Enrich_WhenServiceTimesOut_ShouldReturnOriginal | Verifying that enrich when service times out returns original | Setup when service times out -> Call Enrich -> Assert return original | Enrich when service times out returns original | In scope: Enrich behavior, when service times out scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WhenServiceReturnsNull_ShouldReturnOriginal | Verifying that enrich when service returns null returns original | Setup with null input -> Call Enrich -> Assert return original | Enrich when service returns null returns original | In scope: null input handling for Enrich. Out of scope: valid input scenarios. |
| 4 | | Enrich_WhenPartialFailure_ShouldReturnPartialResults | Verifying that enrich when partial failure returns partial results | Setup mock to throw exception -> Call Enrich -> Assert return partial results | Enrich when partial failure returns partial results | In scope: error handling in Enrich. Out of scope: successful execution paths. |
| 5 | | Enrich_ShouldEmitErrorMetric | Verifying that enrich should emit error metric | Setup mock to throw exception -> Call Enrich -> Assert expected behavior of Enrich | Enrich should emit error metric | In scope: error handling in Enrich. Out of scope: successful execution paths. |

## VectorSearchEnricherTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithVectorSearchEnrichment_Case1 | Verifying that enrich with vector search enrichment case1 | Setup with vector search enrichment -> Call Enrich -> Assert case1 | Enrich with vector search enrichment case1 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithVectorSearchEnrichment_Case2 | Verifying that enrich with vector search enrichment case2 | Setup with vector search enrichment -> Call Enrich -> Assert case2 | Enrich with vector search enrichment case2 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithVectorSearchEnrichment_Case3 | Verifying that enrich with vector search enrichment case3 | Setup with vector search enrichment -> Call Enrich -> Assert case3 | Enrich with vector search enrichment case3 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithVectorSearchEnrichment_Case4 | Verifying that enrich with vector search enrichment case4 | Setup with vector search enrichment -> Call Enrich -> Assert case4 | Enrich with vector search enrichment case4 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithVectorSearchEnrichment_Case5 | Verifying that enrich with vector search enrichment case5 | Setup with vector search enrichment -> Call Enrich -> Assert case5 | Enrich with vector search enrichment case5 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithVectorSearchEnrichment_Case6 | Verifying that enrich with vector search enrichment case6 | Setup with vector search enrichment -> Call Enrich -> Assert case6 | Enrich with vector search enrichment case6 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Enrich_WithVectorSearchEnrichment_Case7 | Verifying that enrich with vector search enrichment case7 | Setup with vector search enrichment -> Call Enrich -> Assert case7 | Enrich with vector search enrichment case7 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Enrich_WithVectorSearchEnrichment_Case8 | Verifying that enrich with vector search enrichment case8 | Setup with vector search enrichment -> Call Enrich -> Assert case8 | Enrich with vector search enrichment case8 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Enrich_WithVectorSearchEnrichment_Case9 | Verifying that enrich with vector search enrichment case9 | Setup with vector search enrichment -> Call Enrich -> Assert case9 | Enrich with vector search enrichment case9 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Enrich_WithVectorSearchEnrichment_Case10 | Verifying that enrich with vector search enrichment case10 | Setup with vector search enrichment -> Call Enrich -> Assert case10 | Enrich with vector search enrichment case10 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Enrich_WithVectorSearchEnrichment_Case11 | Verifying that enrich with vector search enrichment case11 | Setup with vector search enrichment -> Call Enrich -> Assert case11 | Enrich with vector search enrichment case11 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Enrich_WithVectorSearchEnrichment_Case12 | Verifying that enrich with vector search enrichment case12 | Setup with vector search enrichment -> Call Enrich -> Assert case12 | Enrich with vector search enrichment case12 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Enrich_WithVectorSearchEnrichment_Case13 | Verifying that enrich with vector search enrichment case13 | Setup with vector search enrichment -> Call Enrich -> Assert case13 | Enrich with vector search enrichment case13 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Enrich_WithVectorSearchEnrichment_Case14 | Verifying that enrich with vector search enrichment case14 | Setup with vector search enrichment -> Call Enrich -> Assert case14 | Enrich with vector search enrichment case14 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Enrich_WithVectorSearchEnrichment_Case15 | Verifying that enrich with vector search enrichment case15 | Setup with vector search enrichment -> Call Enrich -> Assert case15 | Enrich with vector search enrichment case15 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Enrich_WithVectorSearchEnrichment_Case16 | Verifying that enrich with vector search enrichment case16 | Setup with vector search enrichment -> Call Enrich -> Assert case16 | Enrich with vector search enrichment case16 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Enrich_WithVectorSearchEnrichment_Case17 | Verifying that enrich with vector search enrichment case17 | Setup with vector search enrichment -> Call Enrich -> Assert case17 | Enrich with vector search enrichment case17 | In scope: Enrich behavior, with vector search enrichment scenario. Out of scope: other scenarios and methods not under test. |

## VectorSearchRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithVectorSearch_Case1 | Verifying that rank with vector search case1 | Setup with vector search -> Call Rank -> Assert case1 | Rank with vector search case1 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithVectorSearch_Case2 | Verifying that rank with vector search case2 | Setup with vector search -> Call Rank -> Assert case2 | Rank with vector search case2 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithVectorSearch_Case3 | Verifying that rank with vector search case3 | Setup with vector search -> Call Rank -> Assert case3 | Rank with vector search case3 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithVectorSearch_Case4 | Verifying that rank with vector search case4 | Setup with vector search -> Call Rank -> Assert case4 | Rank with vector search case4 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithVectorSearch_Case5 | Verifying that rank with vector search case5 | Setup with vector search -> Call Rank -> Assert case5 | Rank with vector search case5 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithVectorSearch_Case6 | Verifying that rank with vector search case6 | Setup with vector search -> Call Rank -> Assert case6 | Rank with vector search case6 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithVectorSearch_Case7 | Verifying that rank with vector search case7 | Setup with vector search -> Call Rank -> Assert case7 | Rank with vector search case7 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithVectorSearch_Case8 | Verifying that rank with vector search case8 | Setup with vector search -> Call Rank -> Assert case8 | Rank with vector search case8 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithVectorSearch_Case9 | Verifying that rank with vector search case9 | Setup with vector search -> Call Rank -> Assert case9 | Rank with vector search case9 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithVectorSearch_Case10 | Verifying that rank with vector search case10 | Setup with vector search -> Call Rank -> Assert case10 | Rank with vector search case10 | In scope: Rank behavior, with vector search scenario. Out of scope: other scenarios and methods not under test. |

## VirtualCareRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_ShouldBoostVirtualCareResults | Verifying that rank should boost virtual care results | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should boost virtual care results | In scope: Rank behavior, should boost virtual care results scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithNoVirtualCareResults_ShouldReturnOriginal | Verifying that rank with no virtual care results returns original | Setup with no virtual care results -> Call Rank -> Assert return original | Rank with no virtual care results returns original | In scope: Rank behavior, with no virtual care results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_ShouldPreserveNonVirtualCareOrder | Verifying that rank should preserve non virtual care order | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should preserve non virtual care order | In scope: Rank behavior, should preserve non virtual care order scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithAllVirtualCare_ShouldReturnAll | Verifying that rank with all virtual care returns all | Setup with all virtual care -> Call Rank -> Assert return all | Rank with all virtual care returns all | In scope: Rank behavior, with all virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_ShouldApplyBoostFactor | Verifying that rank should apply boost factor | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should apply boost factor | In scope: Rank behavior, should apply boost factor scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithEmptyResults_ShouldReturnEmpty | Verifying that rank with empty results returns empty | Setup with empty input -> Call Rank -> Assert returns empty collection | Rank with empty results returns empty | In scope: empty input handling for Rank. Out of scope: non-empty input scenarios. |
| 7 | | Rank_ShouldEmitMetrics | Verifying that rank should emit metrics | Setup test data and mocks -> Call Rank -> Assert expected behavior of Rank | Rank should emit metrics | In scope: Rank behavior, should emit metrics scenario. Out of scope: other scenarios and methods not under test. |

# Search/Ranking/Presort

## AvailabilityScorerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Score_WithAvailability_Case1 | Verifying that score with availability case1 | Setup with availability -> Call Score -> Assert case1 | Score with availability case1 | In scope: Score behavior, with availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_WithAvailability_Case2 | Verifying that score with availability case2 | Setup with availability -> Call Score -> Assert case2 | Score with availability case2 | In scope: Score behavior, with availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Score_WithAvailability_Case3 | Verifying that score with availability case3 | Setup with availability -> Call Score -> Assert case3 | Score with availability case3 | In scope: Score behavior, with availability scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Score_WithAvailability_Case4 | Verifying that score with availability case4 | Setup with availability -> Call Score -> Assert case4 | Score with availability case4 | In scope: Score behavior, with availability scenario. Out of scope: other scenarios and methods not under test. |

## DistanceScorerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Score_WithDistance_Case1 | Verifying that score with distance case1 | Setup with distance -> Call Score -> Assert case1 | Score with distance case1 | In scope: Score behavior, with distance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_WithDistance_Case2 | Verifying that score with distance case2 | Setup with distance -> Call Score -> Assert case2 | Score with distance case2 | In scope: Score behavior, with distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Score_WithDistance_Case3 | Verifying that score with distance case3 | Setup with distance -> Call Score -> Assert case3 | Score with distance case3 | In scope: Score behavior, with distance scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Score_WithDistance_Case4 | Verifying that score with distance case4 | Setup with distance -> Call Score -> Assert case4 | Score with distance case4 | In scope: Score behavior, with distance scenario. Out of scope: other scenarios and methods not under test. |

## PresortV3Tests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_WithPresortV3_Case1 | Verifying that execute with presort v3 case1 | Setup with presort v3 -> Call Execute -> Assert case1 | Execute with presort v3 case1 | In scope: Execute behavior, with presort v3 scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_WithPresortV3_Case2 | Verifying that execute with presort v3 case2 | Setup with presort v3 -> Call Execute -> Assert case2 | Execute with presort v3 case2 | In scope: Execute behavior, with presort v3 scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Execute_WithPresortV3_Case3 | Verifying that execute with presort v3 case3 | Setup with presort v3 -> Call Execute -> Assert case3 | Execute with presort v3 case3 | In scope: Execute behavior, with presort v3 scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Execute_WithPresortV3_Case4 | Verifying that execute with presort v3 case4 | Setup with presort v3 -> Call Execute -> Assert case4 | Execute with presort v3 case4 | In scope: Execute behavior, with presort v3 scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Execute_WithPresortV3_Case5 | Verifying that execute with presort v3 case5 | Setup with presort v3 -> Call Execute -> Assert case5 | Execute with presort v3 case5 | In scope: Execute behavior, with presort v3 scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Execute_WithPresortV3_Case6 | Verifying that execute with presort v3 case6 | Setup with presort v3 -> Call Execute -> Assert case6 | Execute with presort v3 case6 | In scope: Execute behavior, with presort v3 scenario. Out of scope: other scenarios and methods not under test. |

## ScoringFunctionTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Apply_WithScoringFunction_Case1 | Verifying that apply with scoring function case1 | Setup with scoring function -> Call Apply -> Assert case1 | Apply with scoring function case1 | In scope: Apply behavior, with scoring function scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Apply_WithScoringFunction_Case2 | Verifying that apply with scoring function case2 | Setup with scoring function -> Call Apply -> Assert case2 | Apply with scoring function case2 | In scope: Apply behavior, with scoring function scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Apply_WithScoringFunction_Case3 | Verifying that apply with scoring function case3 | Setup with scoring function -> Call Apply -> Assert case3 | Apply with scoring function case3 | In scope: Apply behavior, with scoring function scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Apply_WithScoringFunction_Case4 | Verifying that apply with scoring function case4 | Setup with scoring function -> Call Apply -> Assert case4 | Apply with scoring function case4 | In scope: Apply behavior, with scoring function scenario. Out of scope: other scenarios and methods not under test. |

## SpecialtyScorerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Score_WithSpecialty_Case1 | Verifying that score with specialty case1 | Setup with specialty -> Call Score -> Assert case1 | Score with specialty case1 | In scope: Score behavior, with specialty scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_WithSpecialty_Case2 | Verifying that score with specialty case2 | Setup with specialty -> Call Score -> Assert case2 | Score with specialty case2 | In scope: Score behavior, with specialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Score_WithSpecialty_Case3 | Verifying that score with specialty case3 | Setup with specialty -> Call Score -> Assert case3 | Score with specialty case3 | In scope: Score behavior, with specialty scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Score_WithSpecialty_Case4 | Verifying that score with specialty case4 | Setup with specialty -> Call Score -> Assert case4 | Score with specialty case4 | In scope: Score behavior, with specialty scenario. Out of scope: other scenarios and methods not under test. |

# Search/Ranking/Scoring

## RequestScoringInputsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |

# Search/Ranking/TheBox

## AlgoScoreTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | FeatureVector_ShouldExtractValues | Verifying that feature vector should extract values | Setup test data and mocks -> Call FeatureVector -> Assert expected behavior of FeatureVector | FeatureVector should extract values | In scope: FeatureVector behavior, should extract values scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ToString_ShouldReturnFormattedString | Verifying that to string should return formatted string | Setup test data and mocks -> Call ToString -> Assert expected behavior of ToString | ToString should return formatted string | In scope: ToString behavior, should return formatted string scenario. Out of scope: other scenarios and methods not under test. |

## AvailabilityFeaturizerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Featurize_ShouldExtractAvailabilityFeatures | Verifying that featurize should extract availability features | Setup test data and mocks -> Call Featurize -> Assert expected behavior of Featurize | Featurize should extract availability features | In scope: Featurize behavior, should extract availability features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Featurize_WithNoAvailability_ShouldReturnDefaults | Verifying that featurize with no availability returns defaults | Setup with no availability -> Call Featurize -> Assert return defaults | Featurize with no availability returns defaults | In scope: Featurize behavior, with no availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Featurize_ShouldMapDaysToFirstAvailability | Verifying that featurize should map days to first availability | Setup test data and mocks -> Call Featurize -> Assert expected behavior of Featurize | Featurize should map days to first availability | In scope: Featurize behavior, should map days to first availability scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Featurize_ShouldMapSlotCount | Verifying that featurize should map slot count | Setup test data and mocks -> Call Featurize -> Assert expected behavior of Featurize | Featurize should map slot count | In scope: Featurize behavior, should map slot count scenario. Out of scope: other scenarios and methods not under test. |

## BoxDistanceBandModeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetMode_WithCloseDistance_ShouldReturnNearby | Verifying that get mode with close distance returns nearby | Setup with close distance -> Call GetMode -> Assert return nearby | GetMode with close distance returns nearby | In scope: GetMode behavior, with close distance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetMode_WithFarDistance_ShouldReturnExtended | Verifying that get mode with far distance returns extended | Setup with far distance -> Call GetMode -> Assert return extended | GetMode with far distance returns extended | In scope: GetMode behavior, with far distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetMode_WithZeroDistance_ShouldReturnImmediate | Verifying that get mode with zero distance returns immediate | Setup with zero distance -> Call GetMode -> Assert return immediate | GetMode with zero distance returns immediate | In scope: GetMode behavior, with zero distance scenario. Out of scope: other scenarios and methods not under test. |

## BoxProviderLocationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Mapping_ShouldMapCorrectly | Verifying that mapping should map correctly | Setup test data and mocks -> Call Mapping -> Assert expected behavior of Mapping | Mapping should map correctly | In scope: Mapping behavior, should map correctly scenario. Out of scope: other scenarios and methods not under test. |

## BoxSearchParametersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeDefaults | Verifying that constructor should initialize defaults | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize defaults | In scope: Constructor behavior, should initialize defaults scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Validate_ShouldReturnTrue | Verifying that validate should return true | Setup test data and mocks -> Call Validate -> Assert expected behavior of Validate | Validate should return true | In scope: Validate behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |

## NoopScorerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Score_ShouldReturnZero | Verifying that score should return zero | Setup test data and mocks -> Call Score -> Assert expected behavior of Score | Score should return zero | In scope: Score behavior, should return zero scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_ShouldNotModifyInput | Verifying that score should not modify input | Setup test data and mocks -> Call Score -> Assert expected behavior of Score | Score should not modify input | In scope: Score behavior, should not modify input scenario. Out of scope: other scenarios and methods not under test. |

## RankAuditWriterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Write_ShouldPersistAuditData | Verifying that write should persist audit data | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should persist audit data | In scope: Write behavior, should persist audit data scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Write_WithNullData_ShouldSkip | Verifying that write with null data skip | Setup with null input -> Call Write -> Assert skip | Write with null data skip | In scope: null input handling for Write. Out of scope: valid input scenarios. |
| 3 | | Write_ShouldIncludeTimestamp | Verifying that write should include timestamp | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should include timestamp | In scope: Write behavior, should include timestamp scenario. Out of scope: other scenarios and methods not under test. |

## ScoringInputsConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Convert_ShouldMapAllFields | Verifying that convert should map all fields | Setup test data and mocks -> Call Convert -> Assert expected behavior of Convert | Convert should map all fields | In scope: Convert behavior, should map all fields scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Convert_WithNullInput_ShouldReturnDefaults | Verifying that convert with null input returns defaults | Setup with null input -> Call Convert -> Assert return defaults | Convert with null input returns defaults | In scope: null input handling for Convert. Out of scope: valid input scenarios. |
| 3 | | Convert_ShouldPreserveValues | Verifying that convert should preserve values | Setup test data and mocks -> Call Convert -> Assert expected behavior of Convert | Convert should preserve values | In scope: Convert behavior, should preserve values scenario. Out of scope: other scenarios and methods not under test. |

## SortOrderTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Ascending_ShouldSortAscending | Verifying that ascending should sort ascending | Setup test data and mocks -> Call Ascending -> Assert expected behavior of Ascending | Ascending should sort ascending | In scope: Ascending behavior, should sort ascending scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Descending_ShouldSortDescending | Verifying that descending should sort descending | Setup test data and mocks -> Call Descending -> Assert expected behavior of Descending | Descending should sort descending | In scope: Descending behavior, should sort descending scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Default_ShouldBeDescending | Verifying that default should be descending | Setup test data and mocks -> Call Default -> Assert expected behavior of Default | Default should be descending | In scope: Default behavior, should be descending scenario. Out of scope: other scenarios and methods not under test. |

## SpecialtyExtractorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnSpecialtyFromResult | Verifying that extract should return specialty from result | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return specialty from result | In scope: Extract behavior, should return specialty from result scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_WithNoSpecialty_ShouldReturnNull | Verifying that extract with no specialty returns null | Setup with no specialty -> Call Extract -> Assert returns null | Extract with no specialty returns null | In scope: Extract behavior, with no specialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldHandleMultipleSpecialties | Verifying that extract should handle multiple specialties | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should handle multiple specialties | In scope: Extract behavior, should handle multiple specialties scenario. Out of scope: other scenarios and methods not under test. |

# Search/Ranking/TheBox/MachineLearned/Features

## AvailabilityFeatureHelperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnAvailabilityFeatures | Verifying that extract should return availability features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return availability features | In scope: Extract behavior, should return availability features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_WithNoData_ShouldReturnDefaults | Verifying that extract with no data returns defaults | Setup with no data -> Call Extract -> Assert return defaults | Extract with no data returns defaults | In scope: Extract behavior, with no data scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldMapDaysToFirst | Verifying that extract should map days to first | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map days to first | In scope: Extract behavior, should map days to first scenario. Out of scope: other scenarios and methods not under test. |

## CommonFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnCommonFeatures | Verifying that extract should return common features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return common features | In scope: Extract behavior, should return common features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_ShouldIncludeAllExpectedFeatures | Verifying that extract should include all expected features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should include all expected features | In scope: Extract behavior, should include all expected features scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## DistanceFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnDistanceFeatures | Verifying that extract should return distance features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return distance features | In scope: Extract behavior, should return distance features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_WithZeroDistance_ShouldReturnZero | Verifying that extract with zero distance returns zero | Setup with zero distance -> Call Extract -> Assert return zero | Extract with zero distance returns zero | In scope: Extract behavior, with zero distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldConvertToMiles | Verifying that extract should convert to miles | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should convert to miles | In scope: Extract behavior, should convert to miles scenario. Out of scope: other scenarios and methods not under test. |

## EnchiladaFeaturesExtractorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnAllFeatures | Verifying that extract should return all features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return all features | In scope: Extract behavior, should return all features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_ShouldMapCorrectly | Verifying that extract should map correctly | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map correctly | In scope: Extract behavior, should map correctly scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_WithNullInput_ShouldReturnDefaults | Verifying that extract with null input returns defaults | Setup with null input -> Call Extract -> Assert return defaults | Extract with null input returns defaults | In scope: null input handling for Extract. Out of scope: valid input scenarios. |

## FeatureBinsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetBin_ShouldReturnCorrectBin | Verifying that get bin should return correct bin | Setup test data and mocks -> Call GetBin -> Assert expected behavior of GetBin | GetBin should return correct bin | In scope: GetBin behavior, should return correct bin scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetBin_WithEdgeValue_ShouldHandleCorrectly | Verifying that get bin with edge value handle correctly | Setup with edge value -> Call GetBin -> Assert handle correctly | GetBin with edge value handle correctly | In scope: GetBin behavior, with edge value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | AllBins_ShouldBeContinuous | Verifying that all bins should be continuous | Setup test data and mocks -> Call AllBins -> Assert expected behavior of AllBins | AllBins should be continuous | In scope: AllBins behavior, should be continuous scenario. Out of scope: other scenarios and methods not under test. |

## FeatureNamesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | AllNames_ShouldBeDistinct | Verifying that all names should be distinct | Setup test data and mocks -> Call AllNames -> Assert expected behavior of AllNames | AllNames should be distinct | In scope: AllNames behavior, should be distinct scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | AllNames_ShouldNotBeEmpty | Verifying that all names should not be empty | Setup with empty input -> Call AllNames -> Assert expected behavior of AllNames | AllNames should not be empty | In scope: empty input handling for AllNames. Out of scope: non-empty input scenarios. |
| 3 | | Count_ShouldMatchExpected | Verifying that count should match expected | Setup test data and mocks -> Call Count -> Assert expected behavior of Count | Count should match expected | In scope: Count behavior, should match expected scenario. Out of scope: other scenarios and methods not under test. |

## NearbyAvailabilityHelpersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Calculate_ShouldReturnNearbyAvailability | Verifying that calculate should return nearby availability | Setup test data and mocks -> Call Calculate -> Assert expected behavior of Calculate | Calculate should return nearby availability | In scope: Calculate behavior, should return nearby availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Calculate_WithNoNearbyProviders_ShouldReturnZero | Verifying that calculate with no nearby providers returns zero | Setup with no nearby providers -> Call Calculate -> Assert return zero | Calculate with no nearby providers returns zero | In scope: Calculate behavior, with no nearby providers scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Calculate_ShouldRespectRadius | Verifying that calculate should respect radius | Setup test data and mocks -> Call Calculate -> Assert expected behavior of Calculate | Calculate should respect radius | In scope: Calculate behavior, should respect radius scenario. Out of scope: other scenarios and methods not under test. |

## NewProviderFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnNewProviderFeatures | Verifying that extract should return new provider features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return new provider features | In scope: Extract behavior, should return new provider features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_WithEstablishedProvider_ShouldReturnZero | Verifying that extract with established provider returns zero | Setup with established provider -> Call Extract -> Assert return zero | Extract with established provider returns zero | In scope: Extract behavior, with established provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldMapTenureDays | Verifying that extract should map tenure days | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map tenure days | In scope: Extract behavior, should map tenure days scenario. Out of scope: other scenarios and methods not under test. |

## PersonalizationFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnPersonalizationFeatures | Verifying that extract should return personalization features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return personalization features | In scope: Extract behavior, should return personalization features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_WithNoHistory_ShouldReturnDefaults | Verifying that extract with no history returns defaults | Setup with no history -> Call Extract -> Assert return defaults | Extract with no history returns defaults | In scope: Extract behavior, with no history scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldMapInteractionCount | Verifying that extract should map interaction count | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map interaction count | In scope: Extract behavior, should map interaction count scenario. Out of scope: other scenarios and methods not under test. |

## RequestFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnRequestFeatures | Verifying that extract should return request features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return request features | In scope: Extract behavior, should return request features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_ShouldMapSearchQuery | Verifying that extract should map search query | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map search query | In scope: Extract behavior, should map search query scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldMapLocation | Verifying that extract should map location | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map location | In scope: Extract behavior, should map location scenario. Out of scope: other scenarios and methods not under test. |

## SpecialtyFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnSpecialtyFeatures | Verifying that extract should return specialty features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return specialty features | In scope: Extract behavior, should return specialty features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_WithMatchingSpecialty_ShouldReturnOne | Verifying that extract with matching specialty returns one | Setup with matching specialty -> Call Extract -> Assert return one | Extract with matching specialty returns one | In scope: Extract behavior, with matching specialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_WithNonMatchingSpecialty_ShouldReturnZero | Verifying that extract with non matching specialty returns zero | Setup with non matching specialty -> Call Extract -> Assert return zero | Extract with non matching specialty returns zero | In scope: Extract behavior, with non matching specialty scenario. Out of scope: other scenarios and methods not under test. |

## SupplyFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Extract_ShouldReturnSupplyFeatures | Verifying that extract should return supply features | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should return supply features | In scope: Extract behavior, should return supply features scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Extract_ShouldMapProviderCount | Verifying that extract should map provider count | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map provider count | In scope: Extract behavior, should map provider count scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Extract_ShouldMapCompetition | Verifying that extract should map competition | Setup test data and mocks -> Call Extract -> Assert expected behavior of Extract | Extract should map competition | In scope: Extract behavior, should map competition scenario. Out of scope: other scenarios and methods not under test. |

# Search/Ranking/TheBox/MachineLearned/Models

## MapleModelTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Predict_ShouldReturnScore | Verifying that predict should return score | Setup test data and mocks -> Call Predict -> Assert expected behavior of Predict | Predict should return score | In scope: Predict behavior, should return score scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Predict_WithValidFeatures_ShouldReturnPositiveScore | Verifying that predict with valid features returns positive score | Setup with valid features -> Call Predict -> Assert return positive score | Predict with valid features returns positive score | In scope: Predict behavior, with valid features scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Predict_WithNullFeatures_ShouldReturnDefault | Verifying that predict with null features returns default | Setup with null input -> Call Predict -> Assert return default | Predict with null features returns default | In scope: null input handling for Predict. Out of scope: valid input scenarios. |
| 4 | | Predict_ShouldHandleMissingFeatures | Verifying that predict should handle missing features | Setup test data and mocks -> Call Predict -> Assert expected behavior of Predict | Predict should handle missing features | In scope: Predict behavior, should handle missing features scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ModelVersion_ShouldBeCorrect | Verifying that model version should be correct | Setup test data and mocks -> Call ModelVersion -> Assert expected behavior of ModelVersion | ModelVersion should be correct | In scope: ModelVersion behavior, should be correct scenario. Out of scope: other scenarios and methods not under test. |

# Search/Semantic

## RetryingVectorSearchServiceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Search_WhenFirstCallSucceeds_ShouldReturnResponse | Verifying that search when first call succeeds returns response | Setup when first call succeeds -> Call Search -> Assert return response | Search when first call succeeds returns response | In scope: Search behavior, when first call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Search_WhenFirstCallFails_ShouldRetry | Verifying that search when first call fails retry | Setup mock to throw exception -> Call Search -> Assert retry | Search when first call fails retry | In scope: error handling in Search. Out of scope: successful execution paths. |
| 3 | | Search_WhenAllRetriesFail_ShouldThrow | Verifying that search when all retries fail throw | Setup mock to throw exception -> Call Search -> Assert exception is thrown | Search when all retries fail throw | In scope: error handling in Search. Out of scope: successful execution paths. |
| 4 | | Search_ShouldRetryUpToMaxAttempts | Verifying that search should retry up to max attempts | Setup test data and mocks -> Call Search -> Assert expected behavior of Search | Search should retry up to max attempts | In scope: Search behavior, should retry up to max attempts scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Search_WhenSecondCallSucceeds_ShouldReturnResponse | Verifying that search when second call succeeds returns response | Setup when second call succeeds -> Call Search -> Assert return response | Search when second call succeeds returns response | In scope: Search behavior, when second call succeeds scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Search_ShouldUseExponentialBackoff | Verifying that search should use exponential backoff | Setup test data and mocks -> Call Search -> Assert expected behavior of Search | Search should use exponential backoff | In scope: Search behavior, should use exponential backoff scenario. Out of scope: other scenarios and methods not under test. |

## VectorSearchResultTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Score_ShouldBeSettable | Verifying that score should be settable | Setup test data and mocks -> Call Score -> Assert expected behavior of Score | Score should be settable | In scope: Score behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Embedding_ShouldBeSettable | Verifying that embedding should be settable | Setup test data and mocks -> Call Embedding -> Assert expected behavior of Embedding | Embedding should be settable | In scope: Embedding behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |
| 6 | | Properties_CanBeZero | Verifying that properties can be zero | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties can be zero | In scope: Properties behavior, can be zero scenario. Out of scope: other scenarios and methods not under test. |

# Search/Spo

## AdsRetrieverCrosslistingTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAds_WithCrosslisting_Case1 | Verifying that get ads with crosslisting case1 | Setup with crosslisting -> Call GetAds -> Assert case1 | GetAds with crosslisting case1 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAds_WithCrosslisting_Case2 | Verifying that get ads with crosslisting case2 | Setup with crosslisting -> Call GetAds -> Assert case2 | GetAds with crosslisting case2 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAds_WithCrosslisting_Case3 | Verifying that get ads with crosslisting case3 | Setup with crosslisting -> Call GetAds -> Assert case3 | GetAds with crosslisting case3 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAds_WithCrosslisting_Case4 | Verifying that get ads with crosslisting case4 | Setup with crosslisting -> Call GetAds -> Assert case4 | GetAds with crosslisting case4 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAds_WithCrosslisting_Case5 | Verifying that get ads with crosslisting case5 | Setup with crosslisting -> Call GetAds -> Assert case5 | GetAds with crosslisting case5 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAds_WithCrosslisting_Case6 | Verifying that get ads with crosslisting case6 | Setup with crosslisting -> Call GetAds -> Assert case6 | GetAds with crosslisting case6 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAds_WithCrosslisting_Case7 | Verifying that get ads with crosslisting case7 | Setup with crosslisting -> Call GetAds -> Assert case7 | GetAds with crosslisting case7 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAds_WithCrosslisting_Case8 | Verifying that get ads with crosslisting case8 | Setup with crosslisting -> Call GetAds -> Assert case8 | GetAds with crosslisting case8 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAds_WithCrosslisting_Case9 | Verifying that get ads with crosslisting case9 | Setup with crosslisting -> Call GetAds -> Assert case9 | GetAds with crosslisting case9 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAds_WithCrosslisting_Case10 | Verifying that get ads with crosslisting case10 | Setup with crosslisting -> Call GetAds -> Assert case10 | GetAds with crosslisting case10 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAds_WithCrosslisting_Case11 | Verifying that get ads with crosslisting case11 | Setup with crosslisting -> Call GetAds -> Assert case11 | GetAds with crosslisting case11 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetAds_WithCrosslisting_Case12 | Verifying that get ads with crosslisting case12 | Setup with crosslisting -> Call GetAds -> Assert case12 | GetAds with crosslisting case12 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetAds_WithCrosslisting_Case13 | Verifying that get ads with crosslisting case13 | Setup with crosslisting -> Call GetAds -> Assert case13 | GetAds with crosslisting case13 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetAds_WithCrosslisting_Case14 | Verifying that get ads with crosslisting case14 | Setup with crosslisting -> Call GetAds -> Assert case14 | GetAds with crosslisting case14 | In scope: GetAds behavior, with crosslisting scenario. Out of scope: other scenarios and methods not under test. |

## CachedBannerCheckerErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Check_WhenCacheThrows_ShouldLogAndReturnFalse | Verifying that check when cache throws log and return false | Setup mock to throw exception -> Call Check -> Assert returns false | Check when cache throws log and return false | In scope: error handling in Check. Out of scope: successful execution paths. |

## SpoAdsIntersperserTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Intersperse_ShouldPlaceAdsAtCorrectPositions | Verifying that intersperse should place ads at correct positions | Setup test data and mocks -> Call Intersperse -> Assert expected behavior of Intersperse | Intersperse should place ads at correct positions | In scope: Intersperse behavior, should place ads at correct positions scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Intersperse_WithNoAds_ShouldReturnOriginal | Verifying that intersperse with no ads returns original | Setup with no ads -> Call Intersperse -> Assert return original | Intersperse with no ads returns original | In scope: Intersperse behavior, with no ads scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Intersperse_ShouldRespectMaxAdsPerPage | Verifying that intersperse should respect max ads per page | Setup test data and mocks -> Call Intersperse -> Assert expected behavior of Intersperse | Intersperse should respect max ads per page | In scope: Intersperse behavior, should respect max ads per page scenario. Out of scope: other scenarios and methods not under test. |

## SpoClientErrorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAds_WhenHttpClientThrows_ShouldLogAndReturnEmpty | Verifying that get ads when http client throws log and return empty | Setup mock to throw exception -> Call GetAds -> Assert returns empty collection | GetAds when http client throws log and return empty | In scope: error handling in GetAds. Out of scope: successful execution paths. |
| 2 | | GetAds_WhenDeserializationFails_ShouldReturnEmpty | Verifying that get ads when deserialization fails returns empty | Setup mock to throw exception -> Call GetAds -> Assert returns empty collection | GetAds when deserialization fails returns empty | In scope: error handling in GetAds. Out of scope: successful execution paths. |
| 3 | | GetAds_WhenTimeout_ShouldReturnEmpty | Verifying that get ads when timeout returns empty | Setup when timeout -> Call GetAds -> Assert returns empty collection | GetAds when timeout returns empty | In scope: GetAds behavior, when timeout scenario. Out of scope: other scenarios and methods not under test. |

## SpoEnhancedAvailabilityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithAvailableProvider_ShouldInclude | Verifying that filter with available provider include | Setup with available provider -> Call Filter -> Assert include | Filter with available provider include | In scope: Filter behavior, with available provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_WithUnavailableProvider_ShouldExclude | Verifying that filter with unavailable provider exclude | Setup with unavailable provider -> Call Filter -> Assert exclude | Filter with unavailable provider exclude | In scope: Filter behavior, with unavailable provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Filter_WithEnhancedAvailability_ShouldUseEnhancedLogic | Verifying that filter with enhanced availability use enhanced logic | Setup with enhanced availability -> Call Filter -> Assert use enhanced logic | Filter with enhanced availability use enhanced logic | In scope: Filter behavior, with enhanced availability scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Filter_WithNullAvailability_ShouldExclude | Verifying that filter with null availability exclude | Setup with null input -> Call Filter -> Assert exclude | Filter with null availability exclude | In scope: null input handling for Filter. Out of scope: valid input scenarios. |
| 5 | | Filter_WithEmptyResults_ShouldReturnEmpty | Verifying that filter with empty results returns empty | Setup with empty input -> Call Filter -> Assert returns empty collection | Filter with empty results returns empty | In scope: empty input handling for Filter. Out of scope: non-empty input scenarios. |
| 6 | | Filter_ShouldPreserveOrder | Verifying that filter should preserve order | Setup test data and mocks -> Call Filter -> Assert expected behavior of Filter | Filter should preserve order | In scope: Filter behavior, should preserve order scenario. Out of scope: other scenarios and methods not under test. |

## SpoProvLocGetterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetProvLocs_ShouldCallSpoService | Verifying that get prov locs should call spo service | Setup test data and mocks -> Call GetProvLocs -> Assert expected behavior of GetProvLocs | GetProvLocs should call spo service | In scope: GetProvLocs behavior, should call spo service scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetProvLocs_ShouldReturnMappedResults | Verifying that get prov locs should return mapped results | Setup test data and mocks -> Call GetProvLocs -> Assert expected behavior of GetProvLocs | GetProvLocs should return mapped results | In scope: GetProvLocs behavior, should return mapped results scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetProvLocs_WithEmptyResponse_ShouldReturnEmpty | Verifying that get prov locs with empty response returns empty | Setup with empty input -> Call GetProvLocs -> Assert returns empty collection | GetProvLocs with empty response returns empty | In scope: empty input handling for GetProvLocs. Out of scope: non-empty input scenarios. |

## SpogorithmRankerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithSpogorithm_Case1 | Verifying that rank with spogorithm case1 | Setup with spogorithm -> Call Rank -> Assert case1 | Rank with spogorithm case1 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithSpogorithm_Case2 | Verifying that rank with spogorithm case2 | Setup with spogorithm -> Call Rank -> Assert case2 | Rank with spogorithm case2 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithSpogorithm_Case3 | Verifying that rank with spogorithm case3 | Setup with spogorithm -> Call Rank -> Assert case3 | Rank with spogorithm case3 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithSpogorithm_Case4 | Verifying that rank with spogorithm case4 | Setup with spogorithm -> Call Rank -> Assert case4 | Rank with spogorithm case4 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithSpogorithm_Case5 | Verifying that rank with spogorithm case5 | Setup with spogorithm -> Call Rank -> Assert case5 | Rank with spogorithm case5 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithSpogorithm_Case6 | Verifying that rank with spogorithm case6 | Setup with spogorithm -> Call Rank -> Assert case6 | Rank with spogorithm case6 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithSpogorithm_Case7 | Verifying that rank with spogorithm case7 | Setup with spogorithm -> Call Rank -> Assert case7 | Rank with spogorithm case7 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithSpogorithm_Case8 | Verifying that rank with spogorithm case8 | Setup with spogorithm -> Call Rank -> Assert case8 | Rank with spogorithm case8 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithSpogorithm_Case9 | Verifying that rank with spogorithm case9 | Setup with spogorithm -> Call Rank -> Assert case9 | Rank with spogorithm case9 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithSpogorithm_Case10 | Verifying that rank with spogorithm case10 | Setup with spogorithm -> Call Rank -> Assert case10 | Rank with spogorithm case10 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Rank_WithSpogorithm_Case11 | Verifying that rank with spogorithm case11 | Setup with spogorithm -> Call Rank -> Assert case11 | Rank with spogorithm case11 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Rank_WithSpogorithm_Case12 | Verifying that rank with spogorithm case12 | Setup with spogorithm -> Call Rank -> Assert case12 | Rank with spogorithm case12 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Rank_WithSpogorithm_Case13 | Verifying that rank with spogorithm case13 | Setup with spogorithm -> Call Rank -> Assert case13 | Rank with spogorithm case13 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Rank_WithSpogorithm_Case14 | Verifying that rank with spogorithm case14 | Setup with spogorithm -> Call Rank -> Assert case14 | Rank with spogorithm case14 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Rank_WithSpogorithm_Case15 | Verifying that rank with spogorithm case15 | Setup with spogorithm -> Call Rank -> Assert case15 | Rank with spogorithm case15 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Rank_WithSpogorithm_Case16 | Verifying that rank with spogorithm case16 | Setup with spogorithm -> Call Rank -> Assert case16 | Rank with spogorithm case16 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Rank_WithSpogorithm_Case17 | Verifying that rank with spogorithm case17 | Setup with spogorithm -> Call Rank -> Assert case17 | Rank with spogorithm case17 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Rank_WithSpogorithm_Case18 | Verifying that rank with spogorithm case18 | Setup with spogorithm -> Call Rank -> Assert case18 | Rank with spogorithm case18 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Rank_WithSpogorithm_Case19 | Verifying that rank with spogorithm case19 | Setup with spogorithm -> Call Rank -> Assert case19 | Rank with spogorithm case19 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Rank_WithSpogorithm_Case20 | Verifying that rank with spogorithm case20 | Setup with spogorithm -> Call Rank -> Assert case20 | Rank with spogorithm case20 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | Rank_WithSpogorithm_Case21 | Verifying that rank with spogorithm case21 | Setup with spogorithm -> Call Rank -> Assert case21 | Rank with spogorithm case21 | In scope: Rank behavior, with spogorithm scenario. Out of scope: other scenarios and methods not under test. |

# Search/Statsd

## EnchiladaMetricsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | EmitMetric_WithEnchilada_Case1 | Verifying that emit metric with enchilada case1 | Setup with enchilada -> Call EmitMetric -> Assert case1 | EmitMetric with enchilada case1 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | EmitMetric_WithEnchilada_Case2 | Verifying that emit metric with enchilada case2 | Setup with enchilada -> Call EmitMetric -> Assert case2 | EmitMetric with enchilada case2 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | EmitMetric_WithEnchilada_Case3 | Verifying that emit metric with enchilada case3 | Setup with enchilada -> Call EmitMetric -> Assert case3 | EmitMetric with enchilada case3 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | EmitMetric_WithEnchilada_Case4 | Verifying that emit metric with enchilada case4 | Setup with enchilada -> Call EmitMetric -> Assert case4 | EmitMetric with enchilada case4 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | EmitMetric_WithEnchilada_Case5 | Verifying that emit metric with enchilada case5 | Setup with enchilada -> Call EmitMetric -> Assert case5 | EmitMetric with enchilada case5 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | EmitMetric_WithEnchilada_Case6 | Verifying that emit metric with enchilada case6 | Setup with enchilada -> Call EmitMetric -> Assert case6 | EmitMetric with enchilada case6 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | EmitMetric_WithEnchilada_Case7 | Verifying that emit metric with enchilada case7 | Setup with enchilada -> Call EmitMetric -> Assert case7 | EmitMetric with enchilada case7 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | EmitMetric_WithEnchilada_Case8 | Verifying that emit metric with enchilada case8 | Setup with enchilada -> Call EmitMetric -> Assert case8 | EmitMetric with enchilada case8 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | EmitMetric_WithEnchilada_Case9 | Verifying that emit metric with enchilada case9 | Setup with enchilada -> Call EmitMetric -> Assert case9 | EmitMetric with enchilada case9 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | EmitMetric_WithEnchilada_Case10 | Verifying that emit metric with enchilada case10 | Setup with enchilada -> Call EmitMetric -> Assert case10 | EmitMetric with enchilada case10 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | EmitMetric_WithEnchilada_Case11 | Verifying that emit metric with enchilada case11 | Setup with enchilada -> Call EmitMetric -> Assert case11 | EmitMetric with enchilada case11 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | EmitMetric_WithEnchilada_Case12 | Verifying that emit metric with enchilada case12 | Setup with enchilada -> Call EmitMetric -> Assert case12 | EmitMetric with enchilada case12 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | EmitMetric_WithEnchilada_Case13 | Verifying that emit metric with enchilada case13 | Setup with enchilada -> Call EmitMetric -> Assert case13 | EmitMetric with enchilada case13 | In scope: EmitMetric behavior, with enchilada scenario. Out of scope: other scenarios and methods not under test. |

## SearchFunnelMetricsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | EmitMetric_WithSearchFunnel_Case1 | Verifying that emit metric with search funnel case1 | Setup with search funnel -> Call EmitMetric -> Assert case1 | EmitMetric with search funnel case1 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | EmitMetric_WithSearchFunnel_Case2 | Verifying that emit metric with search funnel case2 | Setup with search funnel -> Call EmitMetric -> Assert case2 | EmitMetric with search funnel case2 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | EmitMetric_WithSearchFunnel_Case3 | Verifying that emit metric with search funnel case3 | Setup with search funnel -> Call EmitMetric -> Assert case3 | EmitMetric with search funnel case3 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | EmitMetric_WithSearchFunnel_Case4 | Verifying that emit metric with search funnel case4 | Setup with search funnel -> Call EmitMetric -> Assert case4 | EmitMetric with search funnel case4 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | EmitMetric_WithSearchFunnel_Case5 | Verifying that emit metric with search funnel case5 | Setup with search funnel -> Call EmitMetric -> Assert case5 | EmitMetric with search funnel case5 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | EmitMetric_WithSearchFunnel_Case6 | Verifying that emit metric with search funnel case6 | Setup with search funnel -> Call EmitMetric -> Assert case6 | EmitMetric with search funnel case6 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | EmitMetric_WithSearchFunnel_Case7 | Verifying that emit metric with search funnel case7 | Setup with search funnel -> Call EmitMetric -> Assert case7 | EmitMetric with search funnel case7 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | EmitMetric_WithSearchFunnel_Case8 | Verifying that emit metric with search funnel case8 | Setup with search funnel -> Call EmitMetric -> Assert case8 | EmitMetric with search funnel case8 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | EmitMetric_WithSearchFunnel_Case9 | Verifying that emit metric with search funnel case9 | Setup with search funnel -> Call EmitMetric -> Assert case9 | EmitMetric with search funnel case9 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | EmitMetric_WithSearchFunnel_Case10 | Verifying that emit metric with search funnel case10 | Setup with search funnel -> Call EmitMetric -> Assert case10 | EmitMetric with search funnel case10 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | EmitMetric_WithSearchFunnel_Case11 | Verifying that emit metric with search funnel case11 | Setup with search funnel -> Call EmitMetric -> Assert case11 | EmitMetric with search funnel case11 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | EmitMetric_WithSearchFunnel_Case12 | Verifying that emit metric with search funnel case12 | Setup with search funnel -> Call EmitMetric -> Assert case12 | EmitMetric with search funnel case12 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | EmitMetric_WithSearchFunnel_Case13 | Verifying that emit metric with search funnel case13 | Setup with search funnel -> Call EmitMetric -> Assert case13 | EmitMetric with search funnel case13 | In scope: EmitMetric behavior, with search funnel scenario. Out of scope: other scenarios and methods not under test. |

## SearchLatencyMetricsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | EmitLatency_WithSearchLatency_Case1 | Verifying that emit latency with search latency case1 | Setup with search latency -> Call EmitLatency -> Assert case1 | EmitLatency with search latency case1 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | EmitLatency_WithSearchLatency_Case2 | Verifying that emit latency with search latency case2 | Setup with search latency -> Call EmitLatency -> Assert case2 | EmitLatency with search latency case2 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | EmitLatency_WithSearchLatency_Case3 | Verifying that emit latency with search latency case3 | Setup with search latency -> Call EmitLatency -> Assert case3 | EmitLatency with search latency case3 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | EmitLatency_WithSearchLatency_Case4 | Verifying that emit latency with search latency case4 | Setup with search latency -> Call EmitLatency -> Assert case4 | EmitLatency with search latency case4 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | EmitLatency_WithSearchLatency_Case5 | Verifying that emit latency with search latency case5 | Setup with search latency -> Call EmitLatency -> Assert case5 | EmitLatency with search latency case5 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | EmitLatency_WithSearchLatency_Case6 | Verifying that emit latency with search latency case6 | Setup with search latency -> Call EmitLatency -> Assert case6 | EmitLatency with search latency case6 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | EmitLatency_WithSearchLatency_Case7 | Verifying that emit latency with search latency case7 | Setup with search latency -> Call EmitLatency -> Assert case7 | EmitLatency with search latency case7 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | EmitLatency_WithSearchLatency_Case8 | Verifying that emit latency with search latency case8 | Setup with search latency -> Call EmitLatency -> Assert case8 | EmitLatency with search latency case8 | In scope: EmitLatency behavior, with search latency scenario. Out of scope: other scenarios and methods not under test. |

## SearchMetricTagsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetTag_WithSearchMetricTags_Case1 | Verifying that get tag with search metric tags case1 | Setup with search metric tags -> Call GetTag -> Assert case1 | GetTag with search metric tags case1 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetTag_WithSearchMetricTags_Case2 | Verifying that get tag with search metric tags case2 | Setup with search metric tags -> Call GetTag -> Assert case2 | GetTag with search metric tags case2 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetTag_WithSearchMetricTags_Case3 | Verifying that get tag with search metric tags case3 | Setup with search metric tags -> Call GetTag -> Assert case3 | GetTag with search metric tags case3 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetTag_WithSearchMetricTags_Case4 | Verifying that get tag with search metric tags case4 | Setup with search metric tags -> Call GetTag -> Assert case4 | GetTag with search metric tags case4 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetTag_WithSearchMetricTags_Case5 | Verifying that get tag with search metric tags case5 | Setup with search metric tags -> Call GetTag -> Assert case5 | GetTag with search metric tags case5 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetTag_WithSearchMetricTags_Case6 | Verifying that get tag with search metric tags case6 | Setup with search metric tags -> Call GetTag -> Assert case6 | GetTag with search metric tags case6 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetTag_WithSearchMetricTags_Case7 | Verifying that get tag with search metric tags case7 | Setup with search metric tags -> Call GetTag -> Assert case7 | GetTag with search metric tags case7 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetTag_WithSearchMetricTags_Case8 | Verifying that get tag with search metric tags case8 | Setup with search metric tags -> Call GetTag -> Assert case8 | GetTag with search metric tags case8 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetTag_WithSearchMetricTags_Case9 | Verifying that get tag with search metric tags case9 | Setup with search metric tags -> Call GetTag -> Assert case9 | GetTag with search metric tags case9 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetTag_WithSearchMetricTags_Case10 | Verifying that get tag with search metric tags case10 | Setup with search metric tags -> Call GetTag -> Assert case10 | GetTag with search metric tags case10 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetTag_WithSearchMetricTags_Case11 | Verifying that get tag with search metric tags case11 | Setup with search metric tags -> Call GetTag -> Assert case11 | GetTag with search metric tags case11 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetTag_WithSearchMetricTags_Case12 | Verifying that get tag with search metric tags case12 | Setup with search metric tags -> Call GetTag -> Assert case12 | GetTag with search metric tags case12 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetTag_WithSearchMetricTags_Case13 | Verifying that get tag with search metric tags case13 | Setup with search metric tags -> Call GetTag -> Assert case13 | GetTag with search metric tags case13 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetTag_WithSearchMetricTags_Case14 | Verifying that get tag with search metric tags case14 | Setup with search metric tags -> Call GetTag -> Assert case14 | GetTag with search metric tags case14 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetTag_WithSearchMetricTags_Case15 | Verifying that get tag with search metric tags case15 | Setup with search metric tags -> Call GetTag -> Assert case15 | GetTag with search metric tags case15 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | GetTag_WithSearchMetricTags_Case16 | Verifying that get tag with search metric tags case16 | Setup with search metric tags -> Call GetTag -> Assert case16 | GetTag with search metric tags case16 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | GetTag_WithSearchMetricTags_Case17 | Verifying that get tag with search metric tags case17 | Setup with search metric tags -> Call GetTag -> Assert case17 | GetTag with search metric tags case17 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | GetTag_WithSearchMetricTags_Case18 | Verifying that get tag with search metric tags case18 | Setup with search metric tags -> Call GetTag -> Assert case18 | GetTag with search metric tags case18 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | GetTag_WithSearchMetricTags_Case19 | Verifying that get tag with search metric tags case19 | Setup with search metric tags -> Call GetTag -> Assert case19 | GetTag with search metric tags case19 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | GetTag_WithSearchMetricTags_Case20 | Verifying that get tag with search metric tags case20 | Setup with search metric tags -> Call GetTag -> Assert case20 | GetTag with search metric tags case20 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | GetTag_WithSearchMetricTags_Case21 | Verifying that get tag with search metric tags case21 | Setup with search metric tags -> Call GetTag -> Assert case21 | GetTag with search metric tags case21 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | GetTag_WithSearchMetricTags_Case22 | Verifying that get tag with search metric tags case22 | Setup with search metric tags -> Call GetTag -> Assert case22 | GetTag with search metric tags case22 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | GetTag_WithSearchMetricTags_Case23 | Verifying that get tag with search metric tags case23 | Setup with search metric tags -> Call GetTag -> Assert case23 | GetTag with search metric tags case23 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | GetTag_WithSearchMetricTags_Case24 | Verifying that get tag with search metric tags case24 | Setup with search metric tags -> Call GetTag -> Assert case24 | GetTag with search metric tags case24 | In scope: GetTag behavior, with search metric tags scenario. Out of scope: other scenarios and methods not under test. |

## SpoOutcomeMetricsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | EmitSpoCallOutcome_WithSuccess_ShouldEmitSuccessMetric | Verifying that emit spo call outcome with success emit success metric | Setup with success -> Call EmitSpoCallOutcome -> Assert emit success metric | EmitSpoCallOutcome with success emit success metric | In scope: EmitSpoCallOutcome behavior, with success scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | EmitSpoCallOutcome_WithFailure_ShouldEmitFailureMetric | Verifying that emit spo call outcome with failure emit failure metric | Setup mock to throw exception -> Call EmitSpoCallOutcome -> Assert emit failure metric | EmitSpoCallOutcome with failure emit failure metric | In scope: error handling in EmitSpoCallOutcome. Out of scope: successful execution paths. |

## SupplyHealthMetricsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | EmitEmptyResults_ShouldIncrement | Verifying that emit empty results should increment | Setup test data and mocks -> Call EmitEmptyResults -> Assert expected behavior of EmitEmptyResults | EmitEmptyResults should increment | In scope: EmitEmptyResults behavior, should increment scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | EmitBaseSupplySignal_ShouldCallGauge | Verifying that emit base supply signal should call gauge | Setup test data and mocks -> Call EmitBaseSupplySignal -> Assert expected behavior of EmitBaseSupplySignal | EmitBaseSupplySignal should call gauge | In scope: EmitBaseSupplySignal behavior, should call gauge scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | EmitInsuranceSignal_ShouldCallGauge | Verifying that emit insurance signal should call gauge | Setup test data and mocks -> Call EmitInsuranceSignal -> Assert expected behavior of EmitInsuranceSignal | EmitInsuranceSignal should call gauge | In scope: EmitInsuranceSignal behavior, should call gauge scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | EmitPageResultAssembly_ShouldCallTimer | Verifying that emit page result assembly should call timer | Setup test data and mocks -> Call EmitPageResultAssembly -> Assert expected behavior of EmitPageResultAssembly | EmitPageResultAssembly should call timer | In scope: EmitPageResultAssembly behavior, should call timer scenario. Out of scope: other scenarios and methods not under test. |

# Search/Supplementing

## SupplementersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SpoProvidersSupplementer_Instance_ShouldBeSingleton | Verifying that spo providers supplementer instance is singleton | Setup test data and mocks -> Call SpoProvidersSupplementer -> Assert be singleton | SpoProvidersSupplementer instance is singleton | In scope: SpoProvidersSupplementer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | MapleSupplementer_Instance_ShouldBeSingleton | Verifying that maple supplementer instance is singleton | Setup test data and mocks -> Call MapleSupplementer -> Assert be singleton | MapleSupplementer instance is singleton | In scope: MapleSupplementer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | VirtualCareSupplementer_Instance_ShouldBeSingleton | Verifying that virtual care supplementer instance is singleton | Setup test data and mocks -> Call VirtualCareSupplementer -> Assert be singleton | VirtualCareSupplementer instance is singleton | In scope: VirtualCareSupplementer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ResultsDeduper_Instance_ShouldBeSingleton | Verifying that results deduper instance is singleton | Setup test data and mocks -> Call ResultsDeduper -> Assert be singleton | ResultsDeduper instance is singleton | In scope: ResultsDeduper behavior, instance scenario. Out of scope: other scenarios and methods not under test. |

# Search/Types/Elastic

## CostPlanTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | State_CanBeNull | Verifying that state can be null | Setup with null input -> Call State -> Assert expected behavior of State | State can be null | In scope: null input handling for State. Out of scope: valid input scenarios. |

## EmbeddingTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | EmbeddingValues_CanBeNull | Verifying that embedding values can be null | Setup with null input -> Call EmbeddingValues -> Assert expected behavior of EmbeddingValues | EmbeddingValues can be null | In scope: null input handling for EmbeddingValues. Out of scope: valid input scenarios. |

## EsAvailabilityTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## EsCoordinateTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeMutable | Verifying that properties should be mutable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be mutable | In scope: Properties behavior, should be mutable scenario. Out of scope: other scenarios and methods not under test. |

## EsExternalProviderTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ConvertToEsProviderLocation_WithEmptyLocations_ShouldCreateBasicProviderLocation | Verifying that convert to es provider location with empty locations create basic provider location | Setup with empty input -> Call ConvertToEsProviderLocation -> Assert create basic provider location | ConvertToEsProviderLocation with empty locations create basic provider location | In scope: empty input handling for ConvertToEsProviderLocation. Out of scope: non-empty input scenarios. |
| 2 | | ConvertToEsProviderLocation_WithSingleLocation_ShouldUseLocationData | Verifying that convert to es provider location with single location use location data | Setup with single location -> Call ConvertToEsProviderLocation -> Assert use location data | ConvertToEsProviderLocation with single location use location data | In scope: ConvertToEsProviderLocation behavior, with single location scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ConvertToEsProviderLocation_WithMultipleLocations_ShouldUseFirstLocation | Verifying that convert to es provider location with multiple locations use first location | Setup with multiple locations -> Call ConvertToEsProviderLocation -> Assert use first location | ConvertToEsProviderLocation with multiple locations use first location | In scope: ConvertToEsProviderLocation behavior, with multiple locations scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ConvertToEsProviderLocation_WithMainSpecialty_ShouldConvertMainSpecialty | Verifying that convert to es provider location with main specialty convert main specialty | Setup with main specialty -> Call ConvertToEsProviderLocation -> Assert convert main specialty | ConvertToEsProviderLocation with main specialty convert main specialty | In scope: ConvertToEsProviderLocation behavior, with main specialty scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ConvertToEsProviderLocation_WithNullMainSpecialty_ShouldSetMainSpecialtyToNull | Verifying that convert to es provider location with null main specialty set main specialty to null | Setup with null input -> Call ConvertToEsProviderLocation -> Assert set main specialty to null | ConvertToEsProviderLocation with null main specialty set main specialty to null | In scope: null input handling for ConvertToEsProviderLocation. Out of scope: valid input scenarios. |
| 6 | | ConvertToEsProviderLocation_WithSpecialties_ShouldConvertSpecialties | Verifying that convert to es provider location with specialties convert specialties | Setup with specialties -> Call ConvertToEsProviderLocation -> Assert convert specialties | ConvertToEsProviderLocation with specialties convert specialties | In scope: ConvertToEsProviderLocation behavior, with specialties scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ConvertToEsProviderLocation_WithNullSpecialties_ShouldSetSpecialtiesToEmpty | Verifying that convert to es provider location with null specialties set specialties to empty | Setup with null input -> Call ConvertToEsProviderLocation -> Assert set specialties to empty | ConvertToEsProviderLocation with null specialties set specialties to empty | In scope: null input handling for ConvertToEsProviderLocation. Out of scope: valid input scenarios. |
| 8 | | ConvertToEsProviderLocation_WithNullLocationCoordinate_ShouldUseZeroCoordinates | Verifying that convert to es provider location with null location coordinate use zero coordinates | Setup with null input -> Call ConvertToEsProviderLocation -> Assert use zero coordinates | ConvertToEsProviderLocation with null location coordinate use zero coordinates | In scope: null input handling for ConvertToEsProviderLocation. Out of scope: valid input scenarios. |
| 9 | | ConvertToEsProviderLocation_WithNullCity_ShouldUseEmptyString | Verifying that convert to es provider location with null city use empty string | Setup with null input -> Call ConvertToEsProviderLocation -> Assert use empty string | ConvertToEsProviderLocation with null city use empty string | In scope: null input handling for ConvertToEsProviderLocation. Out of scope: valid input scenarios. |
| 10 | | ConvertToEsProviderLocation_ShouldSetAllExpectedFields | Verifying that convert to es provider location should set all expected fields | Setup test data and mocks -> Call ConvertToEsProviderLocation -> Assert expected behavior of ConvertToEsProviderLocation | ConvertToEsProviderLocation should set all expected fields | In scope: ConvertToEsProviderLocation behavior, should set all expected fields scenario. Out of scope: other scenarios and methods not under test. |

## EsLanguageTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## EsSpecialtyTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Name_CanBeNull | Verifying that name can be null | Setup with null input -> Call Name -> Assert expected behavior of Name | Name can be null | In scope: null input handling for Name. Out of scope: valid input scenarios. |

## FacetTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeEmpty | Verifying that properties can be empty | Setup with empty input -> Call Properties -> Assert expected behavior of Properties | Properties can be empty | In scope: empty input handling for Properties. Out of scope: non-empty input scenarios. |

## InsuranceSettingsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## InteractionTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeZero | Verifying that properties can be zero | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties can be zero | In scope: Properties behavior, can be zero scenario. Out of scope: other scenarios and methods not under test. |

## LocationSummaryTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | TimeZone_CanBeNull | Verifying that time zone can be null | Setup with null input -> Call TimeZone -> Assert expected behavior of TimeZone | TimeZone can be null | In scope: null input handling for TimeZone. Out of scope: valid input scenarios. |

## PracticeDetailsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## PracticeFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeZero | Verifying that properties can be zero | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties can be zero | In scope: Properties behavior, can be zero scenario. Out of scope: other scenarios and methods not under test. |

## ProvLocResultProviderQualitiesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## ProviderLocationRuleTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## ProviderQualitiesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeFalse | Verifying that properties can be false | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties can be false | In scope: Properties behavior, can be false scenario. Out of scope: other scenarios and methods not under test. |

## RealizationPracticeFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## RealizationProviderFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeZero | Verifying that properties can be zero | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties can be zero | In scope: Properties behavior, can be zero scenario. Out of scope: other scenarios and methods not under test. |

# Search/Utils

## AuditWriterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Persist_WritesLocalFile_UnderEndpointDir_WithCsharpSuffix | Verifying that persist writes local file under endpoint dir_ with csharp suffix | Setup test data and mocks -> Call Persist -> Assert under endpoint dir_ with csharp suffix | Persist writes local file under endpoint dir_ with csharp suffix | In scope: Persist behavior, writes local file scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Persist_WhenStaging_WritesToS3_WithExpectedKey | Verifying that persist when staging writes to s3_ with expected key | Setup when staging -> Call Persist -> Assert writes to s3_ with expected key | Persist when staging writes to s3_ with expected key | In scope: Persist behavior, when staging scenario. Out of scope: other scenarios and methods not under test. |

## AvailabilityUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailabilityFieldName_WithDefaultParams_ReturnsAvailabilityField | Verifying that get availability field name with default params returns availability field | Setup with default params -> Call GetAvailabilityFieldName -> Assert returns availability field | GetAvailabilityFieldName with default params returns availability field | In scope: GetAvailabilityFieldName behavior, with default params scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_WithDefaultParams_ReturnsAvailability | Verifying that get availability with default params returns availability | Setup with default params -> Call GetAvailability -> Assert returns availability | GetAvailability with default params returns availability | In scope: GetAvailability behavior, with default params scenario. Out of scope: other scenarios and methods not under test. |

## BrandFilterUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ExtractBrandSearchFilters_WithNull_ShouldReturnEmptyList | Verifying that extract brand search filters with null returns empty list | Setup with null input -> Call ExtractBrandSearchFilters -> Assert returns empty collection | ExtractBrandSearchFilters with null returns empty list | In scope: null input handling for ExtractBrandSearchFilters. Out of scope: valid input scenarios. |
| 2 | | ExtractBrandSearchFilters_WithEmptyString_ShouldReturnEmptyList | Verifying that extract brand search filters with empty string returns empty list | Setup with empty input -> Call ExtractBrandSearchFilters -> Assert returns empty collection | ExtractBrandSearchFilters with empty string returns empty list | In scope: empty input handling for ExtractBrandSearchFilters. Out of scope: non-empty input scenarios. |
| 3 | | ExtractBrandSearchFilters_WithBrandId_ShouldReturnFilter | Verifying that extract brand search filters with brand id returns filter | Setup with brand id -> Call ExtractBrandSearchFilters -> Assert return filter | ExtractBrandSearchFilters with brand id returns filter | In scope: ExtractBrandSearchFilters behavior, with brand id scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ExtractBrandSearchFilters_WithPlacemarkId_ShouldReturnFilter | Verifying that extract brand search filters with placemark id returns filter | Setup with placemark id -> Call ExtractBrandSearchFilters -> Assert return filter | ExtractBrandSearchFilters with placemark id returns filter | In scope: ExtractBrandSearchFilters behavior, with placemark id scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ExtractBrandSearchFilters_WithOtherField_ShouldReturnEmptyList | Verifying that extract brand search filters with other field returns empty list | Setup with other field -> Call ExtractBrandSearchFilters -> Assert returns empty collection | ExtractBrandSearchFilters with other field returns empty list | In scope: ExtractBrandSearchFilters behavior, with other field scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ExtractBrandSearchFilters_WithMultipleFilters_ShouldReturnOnlyBrandAndPlacemark | Verifying that extract brand search filters with multiple filters returns only brand and placemark | Setup with multiple filters -> Call ExtractBrandSearchFilters -> Assert return only brand and placemark | ExtractBrandSearchFilters with multiple filters returns only brand and placemark | In scope: ExtractBrandSearchFilters behavior, with multiple filters scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ExtractBrandSearchFilters_WithInvalidJson_ShouldReturnEmptyList | Verifying that extract brand search filters with invalid json returns empty list | Setup with invalid json -> Call ExtractBrandSearchFilters -> Assert returns empty collection | ExtractBrandSearchFilters with invalid json returns empty list | In scope: ExtractBrandSearchFilters behavior, with invalid json scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ExtractBrandSearchFilters_WithEmptyArray_ShouldReturnEmptyList | Verifying that extract brand search filters with empty array returns empty list | Setup with empty input -> Call ExtractBrandSearchFilters -> Assert returns empty collection | ExtractBrandSearchFilters with empty array returns empty list | In scope: empty input handling for ExtractBrandSearchFilters. Out of scope: non-empty input scenarios. |

## ClockTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SystemClock_Instance_ShouldBeSingleton | Verifying that system clock instance is singleton | Setup test data and mocks -> Call SystemClock -> Assert be singleton | SystemClock instance is singleton | In scope: SystemClock behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | SystemClock_Now_ShouldReturnCurrentTime | Verifying that system clock now returns current time | Setup test data and mocks -> Call SystemClock -> Assert return current time | SystemClock now returns current time | In scope: SystemClock behavior, now scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | SystemClock_NowOffset_ShouldReturnCurrentTimeOffset | Verifying that system clock now offset returns current time offset | Setup test data and mocks -> Call SystemClock -> Assert return current time offset | SystemClock now offset returns current time offset | In scope: SystemClock behavior, now offset scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | FakeClock_Constructor_ShouldSetInitialTime | Verifying that fake clock constructor set initial time | Setup test data and mocks -> Call FakeClock -> Assert set initial time | FakeClock constructor set initial time | In scope: FakeClock behavior, constructor scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | FakeClock_Now_ShouldReturnSetTime | Verifying that fake clock now returns set time | Setup test data and mocks -> Call FakeClock -> Assert return set time | FakeClock now returns set time | In scope: FakeClock behavior, now scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | FakeClock_NowOffset_ShouldReturnTimeAsOffset | Verifying that fake clock now offset returns time as offset | Setup test data and mocks -> Call FakeClock -> Assert return time as offset | FakeClock now offset returns time as offset | In scope: FakeClock behavior, now offset scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | FakeClock_SetNow_ShouldUpdateTime | Verifying that fake clock set now update time | Setup test data and mocks -> Call FakeClock -> Assert update time | FakeClock set now update time | In scope: FakeClock behavior, set now scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | FakeClock_Advance_ShouldAddDuration | Verifying that fake clock advance add duration | Setup test data and mocks -> Call FakeClock -> Assert add duration | FakeClock advance add duration | In scope: FakeClock behavior, advance scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | FakeClock_Advance_WithNegativeDuration_ShouldSubtractTime | Verifying that fake clock advance with negative duration_ should subtract time | Setup test data and mocks -> Call FakeClock -> Assert with negative duration_ subtract time | FakeClock advance with negative duration_ should subtract time | In scope: FakeClock behavior, advance scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | FakeClock_Advance_WithZeroDuration_ShouldNotChangeTime | Verifying that fake clock advance with zero duration_ should not change time | Setup test data and mocks -> Call FakeClock -> Assert with zero duration_ not change time | FakeClock advance with zero duration_ should not change time | In scope: FakeClock behavior, advance scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | FakeClock_MultipleAdvance_ShouldAccumulate | Verifying that fake clock multiple advance accumulate | Setup test data and mocks -> Call FakeClock -> Assert accumulate | FakeClock multiple advance accumulate | In scope: FakeClock behavior, multiple advance scenario. Out of scope: other scenarios and methods not under test. |

## ConversionExtensionsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ToIntOption_WithValidInteger_ShouldReturnValue | Verifying that to int option with valid integer returns value | Setup with valid integer -> Call ToIntOption -> Assert return value | ToIntOption with valid integer returns value | In scope: ToIntOption behavior, with valid integer scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ToIntOption_WithInvalidString_ShouldReturnNull | Verifying that to int option with invalid string returns null | Setup with invalid string -> Call ToIntOption -> Assert returns null | ToIntOption with invalid string returns null | In scope: ToIntOption behavior, with invalid string scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ToIntOption_WithNull_ShouldReturnNull | Verifying that to int option with null returns null | Setup with null input -> Call ToIntOption -> Assert returns null | ToIntOption with null returns null | In scope: null input handling for ToIntOption. Out of scope: valid input scenarios. |
| 4 | | ToIntOption_WithNegativeNumber_ShouldReturnValue | Verifying that to int option with negative number returns value | Setup with negative number -> Call ToIntOption -> Assert return value | ToIntOption with negative number returns value | In scope: ToIntOption behavior, with negative number scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ToDouble_WithTrue_ShouldReturnOne | Verifying that to double with true returns one | Setup with true -> Call ToDouble -> Assert return one | ToDouble with true returns one | In scope: ToDouble behavior, with true scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ToDouble_WithFalse_ShouldReturnZero | Verifying that to double with false returns zero | Setup with false -> Call ToDouble -> Assert return zero | ToDouble with false returns zero | In scope: ToDouble behavior, with false scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | TwoDigits_WithSingleDigit_ShouldAddLeadingZero | Verifying that two digits with single digit add leading zero | Setup with single digit -> Call TwoDigits -> Assert add leading zero | TwoDigits with single digit add leading zero | In scope: TwoDigits behavior, with single digit scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | TwoDigits_WithTwoDigits_ShouldReturnAsIs | Verifying that two digits with two digits returns as is | Setup with two digits -> Call TwoDigits -> Assert return as is | TwoDigits with two digits returns as is | In scope: TwoDigits behavior, with two digits scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | TwoDigits_WithThreeDigits_ShouldReturnFullNumber | Verifying that two digits with three digits returns full number | Setup with three digits -> Call TwoDigits -> Assert return full number | TwoDigits with three digits returns full number | In scope: TwoDigits behavior, with three digits scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | TwoDigits_WithZero_ShouldReturnZeroZero | Verifying that two digits with zero returns zero zero | Setup with zero -> Call TwoDigits -> Assert return zero zero | TwoDigits with zero returns zero zero | In scope: TwoDigits behavior, with zero scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | ToBool_WithOne_ShouldReturnTrue | Verifying that to bool with one returns true | Setup with one -> Call ToBool -> Assert returns true | ToBool with one returns true | In scope: ToBool behavior, with one scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | ToBool_WithZero_ShouldReturnFalse | Verifying that to bool with zero returns false | Setup with zero -> Call ToBool -> Assert returns false | ToBool with zero returns false | In scope: ToBool behavior, with zero scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | ToBool_WithNonNumeric_ShouldReturnFalse | Verifying that to bool with non numeric returns false | Setup with non numeric -> Call ToBool -> Assert returns false | ToBool with non numeric returns false | In scope: ToBool behavior, with non numeric scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | ToBool_WithNull_ShouldReturnFalse | Verifying that to bool with null returns false | Setup with null input -> Call ToBool -> Assert returns false | ToBool with null returns false | In scope: null input handling for ToBool. Out of scope: valid input scenarios. |
| 15 | | ToBool_WithTwo_ShouldReturnFalse | Verifying that to bool with two returns false | Setup with two -> Call ToBool -> Assert returns false | ToBool with two returns false | In scope: ToBool behavior, with two scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | IdToIntOption_WithPrefix_ShouldRemovePrefixAndParse | Verifying that id to int option with prefix remove prefix and parse | Setup with prefix -> Call IdToIntOption -> Assert remove prefix and parse | IdToIntOption with prefix remove prefix and parse | In scope: IdToIntOption behavior, with prefix scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | IdToIntOption_WithNoPrefix_ShouldReturnNull | Verifying that id to int option with no prefix returns null | Setup with no prefix -> Call IdToIntOption -> Assert returns null | IdToIntOption with no prefix returns null | In scope: IdToIntOption behavior, with no prefix scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | IdToIntOption_WithNull_ShouldReturnNull | Verifying that id to int option with null returns null | Setup with null input -> Call IdToIntOption -> Assert returns null | IdToIntOption with null returns null | In scope: null input handling for IdToIntOption. Out of scope: valid input scenarios. |
| 19 | | IdToIntOption_WithMultiplePrefixes_ShouldRemoveAll | Verifying that id to int option with multiple prefixes remove all | Setup with multiple prefixes -> Call IdToIntOption -> Assert remove all | IdToIntOption with multiple prefixes remove all | In scope: IdToIntOption behavior, with multiple prefixes scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | LongConverter_Convert_ShouldParseLong | Verifying that long converter convert parse long | Setup test data and mocks -> Call LongConverter -> Assert parse long | LongConverter convert parse long | In scope: LongConverter behavior, convert scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | StringConverter_Convert_ShouldReturnOriginal | Verifying that string converter convert returns original | Setup test data and mocks -> Call StringConverter -> Assert return original | StringConverter convert returns original | In scope: StringConverter behavior, convert scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | IntConverter_Convert_ShouldParseInt | Verifying that int converter convert parse int | Setup test data and mocks -> Call IntConverter -> Assert parse int | IntConverter convert parse int | In scope: IntConverter behavior, convert scenario. Out of scope: other scenarios and methods not under test. |

## ConvertersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | LongConverter_WithValidString_ShouldConvert | Verifying that long converter with valid string convert | Setup with valid string -> Call LongConverter -> Assert convert | LongConverter with valid string convert | In scope: LongConverter behavior, with valid string scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | LongConverter_WithNegativeNumber_ShouldConvert | Verifying that long converter with negative number convert | Setup with negative number -> Call LongConverter -> Assert convert | LongConverter with negative number convert | In scope: LongConverter behavior, with negative number scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | StringConverter_ShouldReturnSameString | Verifying that string converter should return same string | Setup test data and mocks -> Call StringConverter -> Assert expected behavior of StringConverter | StringConverter should return same string | In scope: StringConverter behavior, should return same string scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | IntConverter_WithValidString_ShouldConvert | Verifying that int converter with valid string convert | Setup with valid string -> Call IntConverter -> Assert convert | IntConverter with valid string convert | In scope: IntConverter behavior, with valid string scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | IntConverter_WithNegativeNumber_ShouldConvert | Verifying that int converter with negative number convert | Setup with negative number -> Call IntConverter -> Assert convert | IntConverter with negative number convert | In scope: IntConverter behavior, with negative number scenario. Out of scope: other scenarios and methods not under test. |

## PercentileUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ComputeP50AndMin_WithEmptyCollection_ShouldReturnZeros | Verifying that compute p50 and min with empty collection returns zeros | Setup with empty input -> Call ComputeP50AndMin -> Assert return zeros | ComputeP50AndMin with empty collection returns zeros | In scope: empty input handling for ComputeP50AndMin. Out of scope: non-empty input scenarios. |
| 2 | | ComputeP50AndMin_WithSingleValue_ShouldReturnThatValueForBoth | Verifying that compute p50 and min with single value returns that value for both | Setup with single value -> Call ComputeP50AndMin -> Assert return that value for both | ComputeP50AndMin with single value returns that value for both | In scope: ComputeP50AndMin behavior, with single value scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ComputeP50AndMin_WithTwoValues_ShouldReturnCorrectMedianAndMin | Verifying that compute p50 and min with two values returns correct median and min | Setup with two values -> Call ComputeP50AndMin -> Assert return correct median and min | ComputeP50AndMin with two values returns correct median and min | In scope: ComputeP50AndMin behavior, with two values scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ComputeP50AndMin_WithOddNumberOfValues_ShouldReturnCorrectMedian | Verifying that compute p50 and min with odd number of values returns correct median | Setup with odd number of values -> Call ComputeP50AndMin -> Assert return correct median | ComputeP50AndMin with odd number of values returns correct median | In scope: ComputeP50AndMin behavior, with odd number of values scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ComputeP50AndMin_WithEvenNumberOfValues_ShouldReturnUpperMedian | Verifying that compute p50 and min with even number of values returns upper median | Setup with even number of values -> Call ComputeP50AndMin -> Assert return upper median | ComputeP50AndMin with even number of values returns upper median | In scope: ComputeP50AndMin behavior, with even number of values scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ComputeP50AndMin_WithUnsortedValues_ShouldSortAndReturnCorrectValues | Verifying that compute p50 and min with unsorted values sort and return correct values | Setup with unsorted values -> Call ComputeP50AndMin -> Assert sort and return correct values | ComputeP50AndMin with unsorted values sort and return correct values | In scope: ComputeP50AndMin behavior, with unsorted values scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ComputeP50AndMin_WithNegativeValues_ShouldHandleCorrectly | Verifying that compute p50 and min with negative values handle correctly | Setup with negative values -> Call ComputeP50AndMin -> Assert handle correctly | ComputeP50AndMin with negative values handle correctly | In scope: ComputeP50AndMin behavior, with negative values scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ComputeP50AndMin_WithAllSameValues_ShouldReturnThatValue | Verifying that compute p50 and min with all same values returns that value | Setup with all same values -> Call ComputeP50AndMin -> Assert return that value | ComputeP50AndMin with all same values returns that value | In scope: ComputeP50AndMin behavior, with all same values scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | ComputeP50AndMin_WithFloats_ShouldReturnCorrectValues | Verifying that compute p50 and min with floats returns correct values | Setup with floats -> Call ComputeP50AndMin -> Assert return correct values | ComputeP50AndMin with floats returns correct values | In scope: ComputeP50AndMin behavior, with floats scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | ComputeP50AndMin_WithLargeCollection_ShouldReturnCorrectValues | Verifying that compute p50 and min with large collection returns correct values | Setup with large collection -> Call ComputeP50AndMin -> Assert return correct values | ComputeP50AndMin with large collection returns correct values | In scope: ComputeP50AndMin behavior, with large collection scenario. Out of scope: other scenarios and methods not under test. |

## QueryValidationUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetFtsSearchQuery_WhenOnlySearchQuery_ShouldReturnSearchQuery | Verifying that get fts search query when only search query returns search query | Setup when only search query -> Call GetFtsSearchQuery -> Assert return search query | GetFtsSearchQuery when only search query returns search query | In scope: GetFtsSearchQuery behavior, when only search query scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetFtsSearchQuery_WhenFtsSearchQuerySet_ShouldPreferFtsOverSearchQuery | Verifying that get fts search query when fts search query set prefer fts over search query | Setup when fts search query set -> Call GetFtsSearchQuery -> Assert prefer fts over search query | GetFtsSearchQuery when fts search query set prefer fts over search query | In scope: GetFtsSearchQuery behavior, when fts search query set scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetFtsSearchQuery_WhenFtsIsEmpty_ShouldFallbackToSearchQuery | Verifying that get fts search query when fts is empty fallback to search query | Setup with empty input -> Call GetFtsSearchQuery -> Assert fallback to search query | GetFtsSearchQuery when fts is empty fallback to search query | In scope: empty input handling for GetFtsSearchQuery. Out of scope: non-empty input scenarios. |
| 4 | | GetFtsSearchQuery_WhenFtsIsWhitespaceOnly_ShouldFallbackToSearchQuery | Verifying that get fts search query when fts is whitespace only fallback to search query | Setup when fts is whitespace only -> Call GetFtsSearchQuery -> Assert fallback to search query | GetFtsSearchQuery when fts is whitespace only fallback to search query | In scope: GetFtsSearchQuery behavior, when fts is whitespace only scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetFtsSearchQuery_WhenAllNull_ShouldReturnNull | Verifying that get fts search query when all null returns null | Setup with null input -> Call GetFtsSearchQuery -> Assert returns null | GetFtsSearchQuery when all null returns null | In scope: null input handling for GetFtsSearchQuery. Out of scope: valid input scenarios. |
| 6 | | GetFtsSearchQuery_ShouldIgnoreCeSearchQuery | Verifying that get fts search query should ignore ce search query | Setup test data and mocks -> Call GetFtsSearchQuery -> Assert expected behavior of GetFtsSearchQuery | GetFtsSearchQuery should ignore ce search query | In scope: GetFtsSearchQuery behavior, should ignore ce search query scenario. Out of scope: other scenarios and methods not under test. |

## S3UtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetS3Client_WhenCalledFirstTime_ReturnsNewClient | Verifying that get s3 client when called first time returns new client | Setup when called first time -> Call GetS3Client -> Assert returns new client | GetS3Client when called first time returns new client | In scope: GetS3Client behavior, when called first time scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetS3Client_WhenCalledMultipleTimes_ReturnsSameInstance | Verifying that get s3 client when called multiple times returns same instance | Setup when called multiple times -> Call GetS3Client -> Assert returns same instance | GetS3Client when called multiple times returns same instance | In scope: GetS3Client behavior, when called multiple times scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetS3Client_WhenDynamoDbEndpointIsSet_UsesLocalStack | Verifying that get s3 client when dynamo db endpoint is set uses local stack | Setup when dynamo db endpoint is set -> Call GetS3Client -> Assert uses local stack | GetS3Client when dynamo db endpoint is set uses local stack | In scope: GetS3Client behavior, when dynamo db endpoint is set scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetS3Client_WhenS3EndpointIsSet_UsesLocalStack | Verifying that get s3 client when s3 endpoint is set uses local stack | Setup when s3 endpoint is set -> Call GetS3Client -> Assert uses local stack | GetS3Client when s3 endpoint is set uses local stack | In scope: GetS3Client behavior, when s3 endpoint is set scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetS3Client_WhenS3EndpointTakesPrecedence_OverDynamoDbEndpoint | Verifying that get s3 client when s3 endpoint takes precedence over dynamo db endpoint | Setup when s3 endpoint takes precedence -> Call GetS3Client -> Assert over dynamo db endpoint | GetS3Client when s3 endpoint takes precedence over dynamo db endpoint | In scope: GetS3Client behavior, when s3 endpoint takes precedence scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetS3Client_WhenNoEndpointIsSet_UsesRealAWS | Verifying that get s3 client when no endpoint is set uses real a w s | Setup when no endpoint is set -> Call GetS3Client -> Assert uses real a w s | GetS3Client when no endpoint is set uses real a w s | In scope: GetS3Client behavior, when no endpoint is set scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetS3Client_WhenEmptyEndpointIsSet_UsesRealAWS | Verifying that get s3 client when empty endpoint is set uses real a w s | Setup with empty input -> Call GetS3Client -> Assert uses real a w s | GetS3Client when empty endpoint is set uses real a w s | In scope: empty input handling for GetS3Client. Out of scope: non-empty input scenarios. |
| 8 | | GetS3Client_IsThreadSafe | Verifying that get s3 client is thread safe | Setup test data and mocks -> Call GetS3Client -> Assert expected behavior of GetS3Client | GetS3Client is thread safe | In scope: GetS3Client behavior, is thread safe scenario. Out of scope: other scenarios and methods not under test. |

## SpendLockStatusUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | CalculateSpendLockStatus_WhenHasBudgetFromIsNull_ShouldReturnInBudget | Verifying that calculate spend lock status when has budget from is null returns in budget | Setup with null input -> Call CalculateSpendLockStatus -> Assert return in budget | CalculateSpendLockStatus when has budget from is null returns in budget | In scope: null input handling for CalculateSpendLockStatus. Out of scope: valid input scenarios. |
| 2 | | CalculateSpendLockStatus_WhenHasBudgetFromIsInYear3000_ShouldReturnIndefiniteSpendLocked | Verifying that calculate spend lock status when has budget from is in year3000 returns indefinite spend locked | Setup when has budget from is in year3000 -> Call CalculateSpendLockStatus -> Assert return indefinite spend locked | CalculateSpendLockStatus when has budget from is in year3000 returns indefinite spend locked | In scope: CalculateSpendLockStatus behavior, when has budget from is in year3000 scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | CalculateSpendLockStatus_WhenHasBudgetFromIsInFuture_ShouldReturnSpendCapped | Verifying that calculate spend lock status when has budget from is in future returns spend capped | Setup when has budget from is in future -> Call CalculateSpendLockStatus -> Assert return spend capped | CalculateSpendLockStatus when has budget from is in future returns spend capped | In scope: CalculateSpendLockStatus behavior, when has budget from is in future scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | CalculateSpendLockStatus_WhenHasBudgetFromIsInPast_ShouldReturnInBudget | Verifying that calculate spend lock status when has budget from is in past returns in budget | Setup when has budget from is in past -> Call CalculateSpendLockStatus -> Assert return in budget | CalculateSpendLockStatus when has budget from is in past returns in budget | In scope: CalculateSpendLockStatus behavior, when has budget from is in past scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | CalculateSpendLockStatus_WhenHasBudgetFromEqualsCurrentTimestamp_ShouldReturnInBudget | Verifying that calculate spend lock status when has budget from equals current timestamp returns in budget | Setup when has budget from equals current timestamp -> Call CalculateSpendLockStatus -> Assert return in budget | CalculateSpendLockStatus when has budget from equals current timestamp returns in budget | In scope: CalculateSpendLockStatus behavior, when has budget from equals current timestamp scenario. Out of scope: other scenarios and methods not under test. |

## UserAgentUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | IsMobileApp_WithNull_ShouldReturnFalse | Verifying that is mobile app with null returns false | Setup with null input -> Call IsMobileApp -> Assert returns false | IsMobileApp with null returns false | In scope: null input handling for IsMobileApp. Out of scope: valid input scenarios. |
| 2 | | IsMobileApp_WithEmptyString_ShouldReturnFalse | Verifying that is mobile app with empty string returns false | Setup with empty input -> Call IsMobileApp -> Assert returns false | IsMobileApp with empty string returns false | In scope: empty input handling for IsMobileApp. Out of scope: non-empty input scenarios. |
| 3 | | IsMobileApp_WithZocdocApp_ShouldReturnTrue | Verifying that is mobile app with zocdoc app returns true | Setup with zocdoc app -> Call IsMobileApp -> Assert returns true | IsMobileApp with zocdoc app returns true | In scope: IsMobileApp behavior, with zocdoc app scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | IsMobileApp_WithZocdocAppLowerCase_ShouldReturnTrue | Verifying that is mobile app with zocdoc app lower case returns true | Setup with zocdoc app lower case -> Call IsMobileApp -> Assert returns true | IsMobileApp with zocdoc app lower case returns true | In scope: IsMobileApp behavior, with zocdoc app lower case scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | IsMobileApp_WithZocdocSlash_ShouldReturnFalse | Verifying that is mobile app with zocdoc slash returns false | Setup with zocdoc slash -> Call IsMobileApp -> Assert returns false | IsMobileApp with zocdoc slash returns false | In scope: IsMobileApp behavior, with zocdoc slash scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | IsMobileApp_WithGqlProxy_ShouldReturnFalse | Verifying that is mobile app with gql proxy returns false | Setup with gql proxy -> Call IsMobileApp -> Assert returns false | IsMobileApp with gql proxy returns false | In scope: IsMobileApp behavior, with gql proxy scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | IsMobileApp_WithRealMobileApp_ShouldReturnTrue | Verifying that is mobile app with real mobile app returns true | Setup with real mobile app -> Call IsMobileApp -> Assert returns true | IsMobileApp with real mobile app returns true | In scope: IsMobileApp behavior, with real mobile app scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | IsMobileApp_WithRegularBrowser_ShouldReturnFalse | Verifying that is mobile app with regular browser returns false | Setup with regular browser -> Call IsMobileApp -> Assert returns false | IsMobileApp with regular browser returns false | In scope: IsMobileApp behavior, with regular browser scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | IsMobileApp_WithMobileWeb_ShouldReturnFalse | Verifying that is mobile app with mobile web returns false | Setup with mobile web -> Call IsMobileApp -> Assert returns false | IsMobileApp with mobile web returns false | In scope: IsMobileApp behavior, with mobile web scenario. Out of scope: other scenarios and methods not under test. |

## ZdSearchRadiusUtilsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetSearchRadiusInMiles_ShouldReturnExpectedRadius | Verifying that get search radius in miles should return expected radius | Setup test data and mocks -> Call GetSearchRadiusInMiles -> Assert expected behavior of GetSearchRadiusInMiles | GetSearchRadiusInMiles should return expected radius | In scope: GetSearchRadiusInMiles behavior, should return expected radius scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetSearchDistanceBandSize_ShouldReturnExpectedBandSize | Verifying that get search distance band size should return expected band size | Setup test data and mocks -> Call GetSearchDistanceBandSize -> Assert expected behavior of GetSearchDistanceBandSize | GetSearchDistanceBandSize should return expected band size | In scope: GetSearchDistanceBandSize behavior, should return expected band size scenario. Out of scope: other scenarios and methods not under test. |

# Search/Yass

## AlgoScoreTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | FeatureVector_ShouldExtractValues | Verifying that feature vector should extract values | Setup test data and mocks -> Call FeatureVector -> Assert expected behavior of FeatureVector | FeatureVector should extract values | In scope: FeatureVector behavior, should extract values scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | FeatureNames_ShouldExtractNames | Verifying that feature names should extract names | Setup test data and mocks -> Call FeatureNames -> Assert expected behavior of FeatureNames | FeatureNames should extract names | In scope: FeatureNames behavior, should extract names scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | FeatureVector_WithEmptySequence_ShouldReturnEmpty | Verifying that feature vector with empty sequence returns empty | Setup with empty input -> Call FeatureVector -> Assert returns empty collection | FeatureVector with empty sequence returns empty | In scope: empty input handling for FeatureVector. Out of scope: non-empty input scenarios. |

## AvailabilityFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## AvailabilityFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | OfficeHoursFilterer_Instance_ShouldBeSingleton | Verifying that office hours filterer instance is singleton | Setup test data and mocks -> Call OfficeHoursFilterer -> Assert be singleton | OfficeHoursFilterer instance is singleton | In scope: OfficeHoursFilterer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | OfficeHoursFilterer_ProcessorType_ShouldReturnOfficeHoursFilterer | Verifying that office hours filterer processor type returns office hours filterer | Setup test data and mocks -> Call OfficeHoursFilterer -> Assert return office hours filterer | OfficeHoursFilterer processor type returns office hours filterer | In scope: OfficeHoursFilterer behavior, processor type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | OfficeHoursFilterer_ProcessorName_ShouldReturnOfficeHoursFilterer | Verifying that office hours filterer processor name returns office hours filterer | Setup test data and mocks -> Call OfficeHoursFilterer -> Assert return office hours filterer | OfficeHoursFilterer processor name returns office hours filterer | In scope: OfficeHoursFilterer behavior, processor name scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | DayAvailabilityFilterer_Instance_ShouldBeSingleton | Verifying that day availability filterer instance is singleton | Setup test data and mocks -> Call DayAvailabilityFilterer -> Assert be singleton | DayAvailabilityFilterer instance is singleton | In scope: DayAvailabilityFilterer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | DayAvailabilityFilterer_ProcessorType_ShouldReturnDayAvailabilityFilterer | Verifying that day availability filterer processor type returns day availability filterer | Setup test data and mocks -> Call DayAvailabilityFilterer -> Assert return day availability filterer | DayAvailabilityFilterer processor type returns day availability filterer | In scope: DayAvailabilityFilterer behavior, processor type scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | DayAvailabilityFilterer_ProcessorName_ShouldReturnDayAvailabilityFilterer | Verifying that day availability filterer processor name returns day availability filterer | Setup test data and mocks -> Call DayAvailabilityFilterer -> Assert return day availability filterer | DayAvailabilityFilterer processor name returns day availability filterer | In scope: DayAvailabilityFilterer behavior, processor name scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | EnhancedAvailabilityFilterer_Instance_ShouldBeSingleton | Verifying that enhanced availability filterer instance is singleton | Setup test data and mocks -> Call EnhancedAvailabilityFilterer -> Assert be singleton | EnhancedAvailabilityFilterer instance is singleton | In scope: EnhancedAvailabilityFilterer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | EnhancedAvailabilityFilterer_ProcessorType_ShouldReturnEnhancedAvailabilityFilterer | Verifying that enhanced availability filterer processor type returns enhanced availability filterer | Setup test data and mocks -> Call EnhancedAvailabilityFilterer -> Assert return enhanced availability filterer | EnhancedAvailabilityFilterer processor type returns enhanced availability filterer | In scope: EnhancedAvailabilityFilterer behavior, processor type scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | EnhancedAvailabilityFilterer_ProcessorName_ShouldReturnEnhancedAvailabilityFilterer | Verifying that enhanced availability filterer processor name returns enhanced availability filterer | Setup test data and mocks -> Call EnhancedAvailabilityFilterer -> Assert return enhanced availability filterer | EnhancedAvailabilityFilterer processor name returns enhanced availability filterer | In scope: EnhancedAvailabilityFilterer behavior, processor name scenario. Out of scope: other scenarios and methods not under test. |

## BannerInfoTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldHaveDefaultValues | Verifying that properties should have default values | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should have default values | In scope: Properties behavior, should have default values scenario. Out of scope: other scenarios and methods not under test. |

## DailySummaryTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## DayRangeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetStartAndEndDate | Verifying that constructor should set start and end date | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set start and end date | In scope: Constructor behavior, should set start and end date scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Contains_WhenDateIsBeforeStart_ShouldReturnFalse | Verifying that contains when date is before start returns false | Setup when date is before start -> Call Contains -> Assert returns false | Contains when date is before start returns false | In scope: Contains behavior, when date is before start scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Contains_WhenDateIsAfterEnd_ShouldReturnFalse | Verifying that contains when date is after end returns false | Setup when date is after end -> Call Contains -> Assert returns false | Contains when date is after end returns false | In scope: Contains behavior, when date is after end scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Contains_WhenDateIsAtStart_ShouldReturnTrue | Verifying that contains when date is at start returns true | Setup when date is at start -> Call Contains -> Assert returns true | Contains when date is at start returns true | In scope: Contains behavior, when date is at start scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Contains_WhenDateIsAtEnd_ShouldReturnTrue | Verifying that contains when date is at end returns true | Setup when date is at end -> Call Contains -> Assert returns true | Contains when date is at end returns true | In scope: Contains behavior, when date is at end scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Contains_WhenDateIsWithinRange_ShouldReturnTrue | Verifying that contains when date is within range returns true | Setup when date is within range -> Call Contains -> Assert returns true | Contains when date is within range returns true | In scope: Contains behavior, when date is within range scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Contains_WithInvalidStartDate_ShouldReturnFalse | Verifying that contains with invalid start date returns false | Setup with invalid start date -> Call Contains -> Assert returns false | Contains with invalid start date returns false | In scope: Contains behavior, with invalid start date scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Contains_WithInvalidEndDate_ShouldReturnFalse | Verifying that contains with invalid end date returns false | Setup with invalid end date -> Call Contains -> Assert returns false | Contains with invalid end date returns false | In scope: Contains behavior, with invalid end date scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Contains_WithSingleDayRange_ShouldWork | Verifying that contains with single day range work | Setup with single day range -> Call Contains -> Assert work | Contains with single day range work | In scope: Contains behavior, with single day range scenario. Out of scope: other scenarios and methods not under test. |

## DentalPracticeSpecialtyRemapperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Instance_ShouldBeSingleton | Verifying that instance should be singleton | Setup test data and mocks -> Call Instance -> Assert expected behavior of Instance | Instance should be singleton | In scope: Instance behavior, should be singleton scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProcessorType_ShouldReturnDentalPracticeSpecialtyRemapper | Verifying that processor type should return dental practice specialty remapper | Setup test data and mocks -> Call ProcessorType -> Assert expected behavior of ProcessorType | ProcessorType should return dental practice specialty remapper | In scope: ProcessorType behavior, should return dental practice specialty remapper scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ProcessorName_ShouldReturnDentalPracticeSpecialtyRemapper | Verifying that processor name should return dental practice specialty remapper | Setup test data and mocks -> Call ProcessorName -> Assert expected behavior of ProcessorName | ProcessorName should return dental practice specialty remapper | In scope: ProcessorName behavior, should return dental practice specialty remapper scenario. Out of scope: other scenarios and methods not under test. |

## DuplicateProviderLocationsFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | NextUpdate_ShouldFilterOutProvidersWithMultipleLocations | Verifying that next update should filter out providers with multiple locations | Setup test data and mocks -> Call NextUpdate -> Assert expected behavior of NextUpdate | NextUpdate should filter out providers with multiple locations | In scope: NextUpdate behavior, should filter out providers with multiple locations scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | NextUpdate_WhenNoDuplicates_ShouldReturnNoOp | Verifying that next update when no duplicates returns no op | Setup when no duplicates -> Call NextUpdate -> Assert return no op | NextUpdate when no duplicates returns no op | In scope: NextUpdate behavior, when no duplicates scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | NextUpdate_ShouldPreserveInputOrder | Verifying that next update should preserve input order | Setup test data and mocks -> Call NextUpdate -> Assert expected behavior of NextUpdate | NextUpdate should preserve input order | In scope: NextUpdate behavior, should preserve input order scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | NextUpdate_WhenTiedScores_ShouldUseSmallerIdAsTiebreaker | Verifying that next update when tied scores use smaller id as tiebreaker | Setup when tied scores -> Call NextUpdate -> Assert use smaller id as tiebreaker | NextUpdate when tied scores use smaller id as tiebreaker | In scope: NextUpdate behavior, when tied scores scenario. Out of scope: other scenarios and methods not under test. |

## EnhancedAvailabilityMatchingEnricherTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Instance_ShouldBeSingleton | Verifying that instance should be singleton | Setup test data and mocks -> Call Instance -> Assert expected behavior of Instance | Instance should be singleton | In scope: Instance behavior, should be singleton scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProcessorType_ShouldReturnCorrectType | Verifying that processor type should return correct type | Setup test data and mocks -> Call ProcessorType -> Assert expected behavior of ProcessorType | ProcessorType should return correct type | In scope: ProcessorType behavior, should return correct type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ProcessorName_ShouldReturnEnhancedAvailabilityMatchingEnricher | Verifying that processor name should return enhanced availability matching enricher | Setup test data and mocks -> Call ProcessorName -> Assert expected behavior of ProcessorName | ProcessorName should return enhanced availability matching enricher | In scope: ProcessorName behavior, should return enhanced availability matching enricher scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Validate_ShouldReturnTrue_WhenPresentInResultEnrichers | Verifying that validate should return true when present in result enrichers | Setup test data and mocks -> Call Validate -> Assert when present in result enrichers | Validate should return true when present in result enrichers | In scope: Validate behavior, should return true scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Validate_ShouldReturnFalse_WhenNotPresentInResultEnrichers | Verifying that validate should return false when not present in result enrichers | Setup test data and mocks -> Call Validate -> Assert when not present in result enrichers | Validate should return false when not present in result enrichers | In scope: Validate behavior, should return false scenario. Out of scope: other scenarios and methods not under test. |

## FacetBucketTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## GroupsDictionaryConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Write_ShouldFormatAsObjectWithStringKeys | Verifying that write should format as object with string keys | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should format as object with string keys | In scope: Write behavior, should format as object with string keys scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Read_ShouldParseObjectWithStringKeys | Verifying that read should parse object with string keys | Setup test data and mocks -> Call Read -> Assert expected behavior of Read | Read should parse object with string keys | In scope: Read behavior, should parse object with string keys scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Read_WithEmptyObject_ShouldReturnEmptyDictionary | Verifying that read with empty object returns empty dictionary | Setup with empty input -> Call Read -> Assert returns empty collection | Read with empty object returns empty dictionary | In scope: empty input handling for Read. Out of scope: non-empty input scenarios. |
| 4 | | Write_WithEmptyDictionary_ShouldWriteEmptyObject | Verifying that write with empty dictionary write empty object | Setup with empty input -> Call Write -> Assert write empty object | Write with empty dictionary write empty object | In scope: empty input handling for Write. Out of scope: non-empty input scenarios. |
| 5 | | Read_WithInvalidEnumKey_ShouldSkipEntry | Verifying that read with invalid enum key skip entry | Setup with invalid enum key -> Call Read -> Assert skip entry | Read with invalid enum key skip entry | In scope: Read behavior, with invalid enum key scenario. Out of scope: other scenarios and methods not under test. |

## HourlySummaryTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## InMemoryPagerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ProcessorType_ShouldReturnInMemoryPager | Verifying that processor type should return in memory pager | Setup test data and mocks -> Call ProcessorType -> Assert expected behavior of ProcessorType | ProcessorType should return in memory pager | In scope: ProcessorType behavior, should return in memory pager scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProcessorName_ShouldReturnInMemoryPager | Verifying that processor name should return in memory pager | Setup test data and mocks -> Call ProcessorName -> Assert expected behavior of ProcessorName | ProcessorName should return in memory pager | In scope: ProcessorName behavior, should return in memory pager scenario. Out of scope: other scenarios and methods not under test. |

## InferenceRequestTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | SearchParams_ShouldBeSettable | Verifying that search params should be settable | Setup test data and mocks -> Call SearchParams -> Assert expected behavior of SearchParams | SearchParams should be settable | In scope: SearchParams behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ResponseInfo_ShouldBeSettable | Verifying that response info should be settable | Setup test data and mocks -> Call ResponseInfo -> Assert expected behavior of ResponseInfo | ResponseInfo should be settable | In scope: ResponseInfo behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | AlgorithmName_ShouldBeSettable | Verifying that algorithm name should be settable | Setup test data and mocks -> Call AlgorithmName -> Assert expected behavior of AlgorithmName | AlgorithmName should be settable | In scope: AlgorithmName behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | RankerName_ShouldDefaultToTheBoxRanker | Verifying that ranker name should default to the box ranker | Setup test data and mocks -> Call RankerName -> Assert expected behavior of RankerName | RankerName should default to the box ranker | In scope: RankerName behavior, should default to the box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | RankerName_ShouldBeSettable | Verifying that ranker name should be settable | Setup test data and mocks -> Call RankerName -> Assert expected behavior of RankerName | RankerName should be settable | In scope: RankerName behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Headers_ShouldBeSettable | Verifying that headers should be settable | Setup test data and mocks -> Call Headers -> Assert expected behavior of Headers | Headers should be settable | In scope: Headers behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## InsuranceFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## LocalDateTimeConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Write_ShouldFormatAsIsoString | Verifying that write should format as iso string | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should format as iso string | In scope: Write behavior, should format as iso string scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Read_ShouldParseIsoString | Verifying that read should parse iso string | Setup test data and mocks -> Call Read -> Assert expected behavior of Read | Read should parse iso string | In scope: Read behavior, should parse iso string scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Read_WithEmptyString_ShouldReturnDefault | Verifying that read with empty string returns default | Setup with empty input -> Call Read -> Assert return default | Read with empty string returns default | In scope: empty input handling for Read. Out of scope: non-empty input scenarios. |

## NoAvailabilityReasonTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enum_ShouldHaveExpectedValues | Verifying that enum should have expected values | Setup test data and mocks -> Call Enum -> Assert expected behavior of Enum | Enum should have expected values | In scope: Enum behavior, should have expected values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enum_ShouldBeComparable | Verifying that enum should be comparable | Setup test data and mocks -> Call Enum -> Assert expected behavior of Enum | Enum should be comparable | In scope: Enum behavior, should be comparable scenario. Out of scope: other scenarios and methods not under test. |

## NullableLocalDateTimeConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Write_ShouldFormatAsIsoString | Verifying that write should format as iso string | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should format as iso string | In scope: Write behavior, should format as iso string scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Write_WithNull_ShouldWriteNull | Verifying that write with null write null | Setup with null input -> Call Write -> Assert write null | Write with null write null | In scope: null input handling for Write. Out of scope: valid input scenarios. |
| 3 | | Read_ShouldParseIsoString | Verifying that read should parse iso string | Setup test data and mocks -> Call Read -> Assert expected behavior of Read | Read should parse iso string | In scope: Read behavior, should parse iso string scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Read_WithNull_ShouldReturnNull | Verifying that read with null returns null | Setup with null input -> Call Read -> Assert returns null | Read with null returns null | In scope: null input handling for Read. Out of scope: valid input scenarios. |
| 5 | | Read_WithEmptyString_ShouldReturnNull | Verifying that read with empty string returns null | Setup with empty input -> Call Read -> Assert returns null | Read with empty string returns null | In scope: empty input handling for Read. Out of scope: non-empty input scenarios. |

## NullableZonedDateTimeConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Write_ShouldFormatAsIsoStringWithTimezone | Verifying that write should format as iso string with timezone | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should format as iso string with timezone | In scope: Write behavior, should format as iso string with timezone scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Write_WithNull_ShouldWriteNull | Verifying that write with null write null | Setup with null input -> Call Write -> Assert write null | Write with null write null | In scope: null input handling for Write. Out of scope: valid input scenarios. |
| 3 | | Read_ShouldParseIsoString | Verifying that read should parse iso string | Setup test data and mocks -> Call Read -> Assert expected behavior of Read | Read should parse iso string | In scope: Read behavior, should parse iso string scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Read_WithNull_ShouldReturnNull | Verifying that read with null returns null | Setup with null input -> Call Read -> Assert returns null | Read with null returns null | In scope: null input handling for Read. Out of scope: valid input scenarios. |
| 5 | | Read_WithEmptyString_ShouldReturnNull | Verifying that read with empty string returns null | Setup with empty input -> Call Read -> Assert returns null | Read with empty string returns null | In scope: empty input handling for Read. Out of scope: non-empty input scenarios. |

## PatientFriendlinessCategoryTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enum_ShouldHaveExpectedValues | Verifying that enum should have expected values | Setup test data and mocks -> Call Enum -> Assert expected behavior of Enum | Enum should have expected values | In scope: Enum behavior, should have expected values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enum_ShouldBeComparable | Verifying that enum should be comparable | Setup test data and mocks -> Call Enum -> Assert expected behavior of Enum | Enum should be comparable | In scope: Enum behavior, should be comparable scenario. Out of scope: other scenarios and methods not under test. |

## PostEsAuditProcessorTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_WithStepNameAndNumber_ShouldSetProperties | Verifying that constructor with step name and number set properties | Setup with step name and number -> Call Constructor -> Assert set properties | Constructor with step name and number set properties | In scope: Constructor behavior, with step name and number scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProcessorType_ShouldReturnAuditProcessor | Verifying that processor type should return audit processor | Setup test data and mocks -> Call ProcessorType -> Assert expected behavior of ProcessorType | ProcessorType should return audit processor | In scope: ProcessorType behavior, should return audit processor scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ProcessorName_ShouldIncludeStepName | Verifying that processor name should include step name | Setup test data and mocks -> Call ProcessorName -> Assert expected behavior of ProcessorName | ProcessorName should include step name | In scope: ProcessorName behavior, should include step name scenario. Out of scope: other scenarios and methods not under test. |

## PostEsFilterersTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | UnbookableFilterer_Instance_ShouldBeSingleton | Verifying that unbookable filterer instance is singleton | Setup test data and mocks -> Call UnbookableFilterer -> Assert be singleton | UnbookableFilterer instance is singleton | In scope: UnbookableFilterer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | UnbookableFilterer_ProcessorType_ShouldReturnUnbookableFilterer | Verifying that unbookable filterer processor type returns unbookable filterer | Setup test data and mocks -> Call UnbookableFilterer -> Assert return unbookable filterer | UnbookableFilterer processor type returns unbookable filterer | In scope: UnbookableFilterer behavior, processor type scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | UnbookableFilterer_ProcessorName_ShouldReturnUnbookableFilterer | Verifying that unbookable filterer processor name returns unbookable filterer | Setup test data and mocks -> Call UnbookableFilterer -> Assert return unbookable filterer | UnbookableFilterer processor name returns unbookable filterer | In scope: UnbookableFilterer behavior, processor name scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ProviderBadgesFilterer_Instance_ShouldBeSingleton | Verifying that provider badges filterer instance is singleton | Setup test data and mocks -> Call ProviderBadgesFilterer -> Assert be singleton | ProviderBadgesFilterer instance is singleton | In scope: ProviderBadgesFilterer behavior, instance scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ProviderBadgesFilterer_ProcessorType_ShouldReturnProviderBadgesFilterer | Verifying that provider badges filterer processor type returns provider badges filterer | Setup test data and mocks -> Call ProviderBadgesFilterer -> Assert return provider badges filterer | ProviderBadgesFilterer processor type returns provider badges filterer | In scope: ProviderBadgesFilterer behavior, processor type scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ProviderBadgesFilterer_ProcessorName_ShouldReturnProviderBadgesFilterer | Verifying that provider badges filterer processor name returns provider badges filterer | Setup test data and mocks -> Call ProviderBadgesFilterer -> Assert return provider badges filterer | ProviderBadgesFilterer processor name returns provider badges filterer | In scope: ProviderBadgesFilterer behavior, processor name scenario. Out of scope: other scenarios and methods not under test. |

## PresortAvailabilityFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | DaysToFirstAvailability_ShouldDefaultTo1000 | Verifying that days to first availability should default to1000 | Setup test data and mocks -> Call DaysToFirstAvailability -> Assert expected behavior of DaysToFirstAvailability | DaysToFirstAvailability should default to1000 | In scope: DaysToFirstAvailability behavior, should default to1000 scenario. Out of scope: other scenarios and methods not under test. |

## PreviewProvLocResultTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Id_ShouldBeSettable | Verifying that id should be settable | Setup test data and mocks -> Call Id -> Assert expected behavior of Id | Id should be settable | In scope: Id behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ProvLoc_ShouldBeSettable | Verifying that prov loc should be settable | Setup test data and mocks -> Call ProvLoc -> Assert expected behavior of ProvLoc | ProvLoc should be settable | In scope: ProvLoc behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | MatchedQueries_ShouldBeSettable | Verifying that matched queries should be settable | Setup test data and mocks -> Call MatchedQueries -> Assert expected behavior of MatchedQueries | MatchedQueries should be settable | In scope: MatchedQueries behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Score_ShouldBeSettable | Verifying that score should be settable | Setup test data and mocks -> Call Score -> Assert expected behavior of Score | Score should be settable | In scope: Score behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | PresortScore_ShouldBeSettable | Verifying that presort score should be settable | Setup test data and mocks -> Call PresortScore -> Assert expected behavior of PresortScore | PresortScore should be settable | In scope: PresortScore behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Groups_ShouldBeSettable | Verifying that groups should be settable | Setup test data and mocks -> Call Groups -> Assert expected behavior of Groups | Groups should be settable | In scope: Groups behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Ranks_ShouldBeSettable | Verifying that ranks should be settable | Setup test data and mocks -> Call Ranks -> Assert expected behavior of Ranks | Ranks should be settable | In scope: Ranks behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | ScoringInputs_ShouldBeSettable | Verifying that scoring inputs should be settable | Setup test data and mocks -> Call ScoringInputs -> Assert expected behavior of ScoringInputs | ScoringInputs should be settable | In scope: ScoringInputs behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | ArcDistanceMeters_ShouldBeSettable | Verifying that arc distance meters should be settable | Setup test data and mocks -> Call ArcDistanceMeters -> Assert expected behavior of ArcDistanceMeters | ArcDistanceMeters should be settable | In scope: ArcDistanceMeters behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | HasSpecialty_ShouldBeSettable | Verifying that has specialty should be settable | Setup test data and mocks -> Call HasSpecialty -> Assert expected behavior of HasSpecialty | HasSpecialty should be settable | In scope: HasSpecialty behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | AvailabilityScore_ShouldBeSettable | Verifying that availability score should be settable | Setup test data and mocks -> Call AvailabilityScore -> Assert expected behavior of AvailabilityScore | AvailabilityScore should be settable | In scope: AvailabilityScore behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | PresortRank_ShouldBeSettable | Verifying that presort rank should be settable | Setup test data and mocks -> Call PresortRank -> Assert expected behavior of PresortRank | PresortRank should be settable | In scope: PresortRank behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## ProvLocDotTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## ProvLocFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## ProvLocGeoFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## ProvLocResultTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | FromEsHit_ShouldCreateProvLocResultWithBasicProperties | Verifying that from es hit should create prov loc result with basic properties | Setup test data and mocks -> Call FromEsHit -> Assert expected behavior of FromEsHit | FromEsHit should create prov loc result with basic properties | In scope: FromEsHit behavior, should create prov loc result with basic properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | FromEsHit_WithNullMatchedQueries_ShouldUseEmptyList | Verifying that from es hit with null matched queries use empty list | Setup with null input -> Call FromEsHit -> Assert use empty list | FromEsHit with null matched queries use empty list | In scope: null input handling for FromEsHit. Out of scope: valid input scenarios. |
| 3 | | FromEsHit_WithHasBudgetFromInPast_ShouldSetSpendLockStatusToInBudget | Verifying that from es hit with has budget from in past set spend lock status to in budget | Setup with has budget from in past -> Call FromEsHit -> Assert set spend lock status to in budget | FromEsHit with has budget from in past set spend lock status to in budget | In scope: FromEsHit behavior, with has budget from in past scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | FromEsHit_WithHasBudgetFromInFuture_ShouldSetSpendLockStatusToSpendCapped | Verifying that from es hit with has budget from in future set spend lock status to spend capped | Setup with has budget from in future -> Call FromEsHit -> Assert set spend lock status to spend capped | FromEsHit with has budget from in future set spend lock status to spend capped | In scope: FromEsHit behavior, with has budget from in future scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | FromEsHit_WithHasBudgetFromYear3000_ShouldSetSpendLockStatusToIndefiniteSpendLocked | Verifying that from es hit with has budget from year3000 set spend lock status to indefinite spend locked | Setup with has budget from year3000 -> Call FromEsHit -> Assert set spend lock status to indefinite spend locked | FromEsHit with has budget from year3000 set spend lock status to indefinite spend locked | In scope: FromEsHit behavior, with has budget from year3000 scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | FromEsHit_WithVirtualLocation_ShouldSetIsVirtualLocation | Verifying that from es hit with virtual location set is virtual location | Setup with virtual location -> Call FromEsHit -> Assert set is virtual location | FromEsHit with virtual location set is virtual location | In scope: FromEsHit behavior, with virtual location scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | FromEsHit_WithAvailability_ShouldSetHasAvailability | Verifying that from es hit with availability set has availability | Setup with availability -> Call FromEsHit -> Assert set has availability | FromEsHit with availability set has availability | In scope: FromEsHit behavior, with availability scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | WithAvailabilityScore_ShouldCreateCopyWithNewScore | Verifying that with availability score should create copy with new score | Setup test data and mocks -> Call WithAvailabilityScore -> Assert expected behavior of WithAvailabilityScore | WithAvailabilityScore should create copy with new score | In scope: WithAvailabilityScore behavior, should create copy with new score scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | WithPresortScore_ShouldUpdateBothPresortScoreAndScore | Verifying that with presort score should update both presort score and score | Setup test data and mocks -> Call WithPresortScore -> Assert expected behavior of WithPresortScore | WithPresortScore should update both presort score and score | In scope: WithPresortScore behavior, should update both presort score and score scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | WithHasSpecialty_ShouldCreateCopyWithNewValue | Verifying that with has specialty should create copy with new value | Setup test data and mocks -> Call WithHasSpecialty -> Assert expected behavior of WithHasSpecialty | WithHasSpecialty should create copy with new value | In scope: WithHasSpecialty behavior, should create copy with new value scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | WithArcDistanceMeters_ShouldCreateCopyWithNewValue | Verifying that with arc distance meters should create copy with new value | Setup test data and mocks -> Call WithArcDistanceMeters -> Assert expected behavior of WithArcDistanceMeters | WithArcDistanceMeters should create copy with new value | In scope: WithArcDistanceMeters behavior, should create copy with new value scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | WithPresortRank_ShouldCreateCopyWithNewValue | Verifying that with presort rank should create copy with new value | Setup test data and mocks -> Call WithPresortRank -> Assert expected behavior of WithPresortRank | WithPresortRank should create copy with new value | In scope: WithPresortRank behavior, should create copy with new value scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | WithNoAvailabilityReason_ShouldCreateCopyWithNewValue | Verifying that with no availability reason should create copy with new value | Setup test data and mocks -> Call WithNoAvailabilityReason -> Assert expected behavior of WithNoAvailabilityReason | WithNoAvailabilityReason should create copy with new value | In scope: WithNoAvailabilityReason behavior, should create copy with new value scenario. Out of scope: other scenarios and methods not under test. |

## ProvLocResultsContainerTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldInitializeProperties | Verifying that constructor should initialize properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should initialize properties | In scope: Constructor behavior, should initialize properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Results_ShouldBeSettable | Verifying that results should be settable | Setup test data and mocks -> Call Results -> Assert expected behavior of Results | Results should be settable | In scope: Results behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Results_ShouldDefaultToEmptyList | Verifying that results should default to empty list | Setup with empty input -> Call Results -> Assert expected behavior of Results | Results should default to empty list | In scope: empty input handling for Results. Out of scope: non-empty input scenarios. |

## ProvLocScoringInputsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | HasBudgetFrom_CanBeNull | Verifying that has budget from can be null | Setup with null input -> Call HasBudgetFrom -> Assert expected behavior of HasBudgetFrom | HasBudgetFrom can be null | In scope: null input handling for HasBudgetFrom. Out of scope: valid input scenarios. |

## ProviderDeduperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | NextUpdate_ShouldGroupResultsByProviderIdAndDedupeToAdditionalProvLocs | Verifying that next update should group results by provider id and dedupe to additional prov locs | Setup test data and mocks -> Call NextUpdate -> Assert expected behavior of NextUpdate | NextUpdate should group results by provider id and dedupe to additional prov locs | In scope: NextUpdate behavior, should group results by provider id and dedupe to additional prov locs scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | NextUpdate_ShouldDedupeSeparatelyByInNetworkGroups | Verifying that next update should dedupe separately by in network groups | Setup test data and mocks -> Call NextUpdate -> Assert expected behavior of NextUpdate | NextUpdate should dedupe separately by in network groups | In scope: NextUpdate behavior, should dedupe separately by in network groups scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | NextUpdate_ShouldUpdateDistinctInNetworkAggregationsCount | Verifying that next update should update distinct in network aggregations count | Setup test data and mocks -> Call NextUpdate -> Assert expected behavior of NextUpdate | NextUpdate should update distinct in network aggregations count | In scope: NextUpdate behavior, should update distinct in network aggregations count scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | NextUpdate_ShouldNotUpdateAggregationsWhenUndefined | Verifying that next update should not update aggregations when undefined | Setup test data and mocks -> Call NextUpdate -> Assert expected behavior of NextUpdate | NextUpdate should not update aggregations when undefined | In scope: NextUpdate behavior, should not update aggregations when undefined scenario. Out of scope: other scenarios and methods not under test. |

## RanksTupleListConverterTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Write_ShouldFormatAsNestedArrays | Verifying that write should format as nested arrays | Setup test data and mocks -> Call Write -> Assert expected behavior of Write | Write should format as nested arrays | In scope: Write behavior, should format as nested arrays scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Read_ShouldParseNestedArrays | Verifying that read should parse nested arrays | Setup test data and mocks -> Call Read -> Assert expected behavior of Read | Read should parse nested arrays | In scope: Read behavior, should parse nested arrays scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Read_WithEmptyArray_ShouldReturnEmptyList | Verifying that read with empty array returns empty list | Setup with empty input -> Call Read -> Assert returns empty collection | Read with empty array returns empty list | In scope: empty input handling for Read. Out of scope: non-empty input scenarios. |
| 4 | | Write_WithEmptyList_ShouldWriteEmptyArray | Verifying that write with empty list write empty array | Setup with empty input -> Call Write -> Assert write empty array | Write with empty list write empty array | In scope: empty input handling for Write. Out of scope: non-empty input scenarios. |

## ResponseInfoTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | FromOrganicResults_ShouldCreateResponseInfoWithCorrectProperties | Verifying that from organic results should create response info with correct properties | Setup test data and mocks -> Call FromOrganicResults -> Assert expected behavior of FromOrganicResults | FromOrganicResults should create response info with correct properties | In scope: FromOrganicResults behavior, should create response info with correct properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | FromResultsContainer_ShouldCreateResponseInfo | Verifying that from results container should create response info | Setup test data and mocks -> Call FromResultsContainer -> Assert expected behavior of FromResultsContainer | FromResultsContainer should create response info | In scope: FromResultsContainer behavior, should create response info scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | WithResults_ShouldCreateCopyWithNewResults | Verifying that with results should create copy with new results | Setup test data and mocks -> Call WithResults -> Assert expected behavior of WithResults | WithResults should create copy with new results | In scope: WithResults behavior, should create copy with new results scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | WithSpoResults_ShouldCreateCopyWithNewSpoResults | Verifying that with spo results should create copy with new spo results | Setup test data and mocks -> Call WithSpoResults -> Assert expected behavior of WithSpoResults | WithSpoResults should create copy with new spo results | In scope: WithSpoResults behavior, should create copy with new spo results scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | WithFinalScorerName_ShouldCreateCopyWithNewScorerName | Verifying that with final scorer name should create copy with new scorer name | Setup test data and mocks -> Call WithFinalScorerName -> Assert expected behavior of WithFinalScorerName | WithFinalScorerName should create copy with new scorer name | In scope: WithFinalScorerName behavior, should create copy with new scorer name scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | WithProcessorInfoChain_ShouldCreateCopyWithNewChain | Verifying that with processor info chain should create copy with new chain | Setup test data and mocks -> Call WithProcessorInfoChain -> Assert expected behavior of WithProcessorInfoChain | WithProcessorInfoChain should create copy with new chain | In scope: WithProcessorInfoChain behavior, should create copy with new chain scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | WithProvLocDotsOnMap_ShouldCreateCopyWithNewDots | Verifying that with prov loc dots on map should create copy with new dots | Setup test data and mocks -> Call WithProvLocDotsOnMap -> Assert expected behavior of WithProvLocDotsOnMap | WithProvLocDotsOnMap should create copy with new dots | In scope: WithProvLocDotsOnMap behavior, should create copy with new dots scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Copy_WithNoParameters_ShouldCreateExactCopy | Verifying that copy with no parameters create exact copy | Setup with no parameters -> Call Copy -> Assert create exact copy | Copy with no parameters create exact copy | In scope: Copy behavior, with no parameters scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Copy_WithPartialParameters_ShouldUpdateOnlySpecifiedFields | Verifying that copy with partial parameters update only specified fields | Setup with partial parameters -> Call Copy -> Assert update only specified fields | Copy with partial parameters update only specified fields | In scope: Copy behavior, with partial parameters scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Copy_ShouldPreserveQueryEmbedding | Verifying that copy should preserve query embedding | Setup test data and mocks -> Call Copy -> Assert expected behavior of Copy | Copy should preserve query embedding | In scope: Copy behavior, should preserve query embedding scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | BucketAggregation_WhenAggregationsIsNull_ShouldReturnNull | Verifying that bucket aggregation when aggregations is null returns null | Setup with null input -> Call BucketAggregation -> Assert returns null | BucketAggregation when aggregations is null returns null | In scope: null input handling for BucketAggregation. Out of scope: valid input scenarios. |
| 12 | | BucketAggregation_WhenAggregationsExists_ShouldCallGetBuckets | Verifying that bucket aggregation when aggregations exists call get buckets | Setup when aggregations exists -> Call BucketAggregation -> Assert call get buckets | BucketAggregation when aggregations exists call get buckets | In scope: BucketAggregation behavior, when aggregations exists scenario. Out of scope: other scenarios and methods not under test. |

## ResponseUpdateTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetProperties | Verifying that constructor should set properties | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set properties | In scope: Constructor behavior, should set properties scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Response_ShouldAddProcessorToChain | Verifying that response should add processor to chain | Setup test data and mocks -> Call Response -> Assert expected behavior of Response | Response should add processor to chain | In scope: Response behavior, should add processor to chain scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Response_ShouldPreserveExistingChain | Verifying that response should preserve existing chain | Setup test data and mocks -> Call Response -> Assert expected behavior of Response | Response should preserve existing chain | In scope: Response behavior, should preserve existing chain scenario. Out of scope: other scenarios and methods not under test. |

## ReviewsFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_CanBeNull | Verifying that properties can be null | Setup with null input -> Call Properties -> Assert expected behavior of Properties | Properties can be null | In scope: null input handling for Properties. Out of scope: valid input scenarios. |

## SearchParamsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetDefaultValues | Verifying that constructor should set default values | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set default values | In scope: Constructor behavior, should set default values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | PageSize_ShouldDefaultToConstant | Verifying that page size should default to constant | Setup test data and mocks -> Call PageSize -> Assert expected behavior of PageSize | PageSize should default to constant | In scope: PageSize behavior, should default to constant scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ElasticSize_ShouldDefaultToConstant | Verifying that elastic size should default to constant | Setup test data and mocks -> Call ElasticSize -> Assert expected behavior of ElasticSize | ElasticSize should default to constant | In scope: ElasticSize behavior, should default to constant scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetExperimentAssignment_WithValidExperimentId_ShouldReturnAssignment | Verifying that get experiment assignment with valid experiment id returns assignment | Setup with valid experiment id -> Call GetExperimentAssignment -> Assert return assignment | GetExperimentAssignment with valid experiment id returns assignment | In scope: GetExperimentAssignment behavior, with valid experiment id scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetExperimentAssignment_WithInvalidExperimentId_ShouldReturnNull | Verifying that get experiment assignment with invalid experiment id returns null | Setup with invalid experiment id -> Call GetExperimentAssignment -> Assert returns null | GetExperimentAssignment with invalid experiment id returns null | In scope: GetExperimentAssignment behavior, with invalid experiment id scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetExperimentAssignment_WithNullAssignments_ShouldReturnNull | Verifying that get experiment assignment with null assignments returns null | Setup with null input -> Call GetExperimentAssignment -> Assert returns null | GetExperimentAssignment with null assignments returns null | In scope: null input handling for GetExperimentAssignment. Out of scope: valid input scenarios. |
| 8 | | IsFlagOn_WithTrueFlag_ShouldReturnTrue | Verifying that is flag on with true flag returns true | Setup with true flag -> Call IsFlagOn -> Assert returns true | IsFlagOn with true flag returns true | In scope: IsFlagOn behavior, with true flag scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | IsFlagOn_WithFalseFlag_ShouldReturnFalse | Verifying that is flag on with false flag returns false | Setup with false flag -> Call IsFlagOn -> Assert returns false | IsFlagOn with false flag returns false | In scope: IsFlagOn behavior, with false flag scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | IsFlagOn_WithNullFlag_ShouldReturnFalse | Verifying that is flag on with null flag returns false | Setup with null input -> Call IsFlagOn -> Assert returns false | IsFlagOn with null flag returns false | In scope: null input handling for IsFlagOn. Out of scope: valid input scenarios. |
| 11 | | IsFlagOn_WithStringKey_ShouldReturnCorrectValue | Verifying that is flag on with string key returns correct value | Setup with string key -> Call IsFlagOn -> Assert return correct value | IsFlagOn with string key returns correct value | In scope: IsFlagOn behavior, with string key scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | IsFlagOn_WithIYassExperiment_ShouldReturnCorrectValue | Verifying that is flag on with i yass experiment returns correct value | Setup with i yass experiment -> Call IsFlagOn -> Assert return correct value | IsFlagOn with i yass experiment returns correct value | In scope: IsFlagOn behavior, with i yass experiment scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | SetAssignmentsFromResponse_ShouldMapAssignments | Verifying that set assignments from response should map assignments | Setup test data and mocks -> Call SetAssignmentsFromResponse -> Assert expected behavior of SetAssignmentsFromResponse | SetAssignmentsFromResponse should map assignments | In scope: SetAssignmentsFromResponse behavior, should map assignments scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | SetAssignmentsFromDictionary_ShouldMapAssignments | Verifying that set assignments from dictionary should map assignments | Setup test data and mocks -> Call SetAssignmentsFromDictionary -> Assert expected behavior of SetAssignmentsFromDictionary | SetAssignmentsFromDictionary should map assignments | In scope: SetAssignmentsFromDictionary behavior, should map assignments scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | IsFeatureCategorySearch_WithFeatureCategory_ShouldReturnTrue | Verifying that is feature category search with feature category returns true | Setup with feature category -> Call IsFeatureCategorySearch -> Assert returns true | IsFeatureCategorySearch with feature category returns true | In scope: IsFeatureCategorySearch behavior, with feature category scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | IsFeatureCategorySearch_WithoutFeatureCategory_ShouldReturnFalse | Verifying that is feature category search with out feature category returns false | Setup with out feature category -> Call IsFeatureCategorySearch -> Assert returns false | IsFeatureCategorySearch with out feature category returns false | In scope: IsFeatureCategorySearch behavior, with out feature category scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | HasEnhancedAvailabilityFilter_WithFilter_ShouldReturnTrue | Verifying that has enhanced availability filter with filter returns true | Setup with filter -> Call HasEnhancedAvailabilityFilter -> Assert returns true | HasEnhancedAvailabilityFilter with filter returns true | In scope: HasEnhancedAvailabilityFilter behavior, with filter scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | HasEnhancedAvailabilityFilter_WithoutFilter_ShouldReturnFalse | Verifying that has enhanced availability filter with out filter returns false | Setup with out filter -> Call HasEnhancedAvailabilityFilter -> Assert returns false | HasEnhancedAvailabilityFilter with out filter returns false | In scope: HasEnhancedAvailabilityFilter behavior, with out filter scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | HasVideoVisitFilter_WithFilter_ShouldReturnTrue | Verifying that has video visit filter with filter returns true | Setup with filter -> Call HasVideoVisitFilter -> Assert returns true | HasVideoVisitFilter with filter returns true | In scope: HasVideoVisitFilter behavior, with filter scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | HasVideoVisitFilter_WithoutFilter_ShouldReturnFalse | Verifying that has video visit filter with out filter returns false | Setup with out filter -> Call HasVideoVisitFilter -> Assert returns false | HasVideoVisitFilter with out filter returns false | In scope: HasVideoVisitFilter behavior, with out filter scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | DayRange_WithValidJson_ShouldParse | Verifying that day range with valid json parse | Setup with valid json -> Call DayRange -> Assert parse | DayRange with valid json parse | In scope: DayRange behavior, with valid json scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | DayRange_WithInvalidJson_ShouldReturnNull | Verifying that day range with invalid json returns null | Setup with invalid json -> Call DayRange -> Assert returns null | DayRange with invalid json returns null | In scope: DayRange behavior, with invalid json scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | TimeRange_WithValidJson_ShouldParse | Verifying that time range with valid json parse | Setup with valid json -> Call TimeRange -> Assert parse | TimeRange with valid json parse | In scope: TimeRange behavior, with valid json scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | TimeRange_WithInvalidJson_ShouldReturnNull | Verifying that time range with invalid json returns null | Setup with invalid json -> Call TimeRange -> Assert returns null | TimeRange with invalid json returns null | In scope: TimeRange behavior, with invalid json scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | GetAllowedValuesForFilter_WithIntersection_ShouldReturnIntersection | Verifying that get allowed values for filter with intersection returns intersection | Setup with intersection -> Call GetAllowedValuesForFilter -> Assert return intersection | GetAllowedValuesForFilter with intersection returns intersection | In scope: GetAllowedValuesForFilter behavior, with intersection scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | GetAllowedValuesForFilter_WithNoIntersection_ShouldReturnEmpty | Verifying that get allowed values for filter with no intersection returns empty | Setup with no intersection -> Call GetAllowedValuesForFilter -> Assert returns empty collection | GetAllowedValuesForFilter with no intersection returns empty | In scope: GetAllowedValuesForFilter behavior, with no intersection scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | GetAllowedValuesForFilter_WithNullFilter_ShouldReturnNull | Verifying that get allowed values for filter with null filter returns null | Setup with null input -> Call GetAllowedValuesForFilter -> Assert returns null | GetAllowedValuesForFilter with null filter returns null | In scope: null input handling for GetAllowedValuesForFilter. Out of scope: valid input scenarios. |
| 28 | | GetExperimentValue_WithValidKey_ShouldReturnValue | Verifying that get experiment value with valid key returns value | Setup with valid key -> Call GetExperimentValue -> Assert return value | GetExperimentValue with valid key returns value | In scope: GetExperimentValue behavior, with valid key scenario. Out of scope: other scenarios and methods not under test. |
| 29 | | GetExperimentValue_WithInvalidKey_ShouldReturnDefault | Verifying that get experiment value with invalid key returns default | Setup with invalid key -> Call GetExperimentValue -> Assert return default | GetExperimentValue with invalid key returns default | In scope: GetExperimentValue behavior, with invalid key scenario. Out of scope: other scenarios and methods not under test. |
| 30 | | GetExperimentValue_WithNullKey_ShouldReturnDefault | Verifying that get experiment value with null key returns default | Setup with null input -> Call GetExperimentValue -> Assert return default | GetExperimentValue with null key returns default | In scope: null input handling for GetExperimentValue. Out of scope: valid input scenarios. |
| 31 | | NullHandling_AllNullableProperties_ShouldHandleNull | Verifying that null handling all nullable properties handle null | Setup with null input -> Call NullHandling -> Assert handle null | NullHandling all nullable properties handle null | In scope: null input handling for NullHandling. Out of scope: valid input scenarios. |
| 32 | | ElasticSizeIsDefined_WithDefinedSize_ShouldReturnTrue | Verifying that elastic size is defined with defined size returns true | Setup with defined size -> Call ElasticSizeIsDefined -> Assert returns true | ElasticSizeIsDefined with defined size returns true | In scope: ElasticSizeIsDefined behavior, with defined size scenario. Out of scope: other scenarios and methods not under test. |
| 33 | | ElasticSizeIsDefined_WithUndefinedSize_ShouldReturnFalse | Verifying that elastic size is defined with undefined size returns false | Setup with undefined size -> Call ElasticSizeIsDefined -> Assert returns false | ElasticSizeIsDefined with undefined size returns false | In scope: ElasticSizeIsDefined behavior, with undefined size scenario. Out of scope: other scenarios and methods not under test. |
| 34 | | DateSearchedForIsDefined_WithDefinedDate_ShouldReturnTrue | Verifying that date searched for is defined with defined date returns true | Setup with defined date -> Call DateSearchedForIsDefined -> Assert returns true | DateSearchedForIsDefined with defined date returns true | In scope: DateSearchedForIsDefined behavior, with defined date scenario. Out of scope: other scenarios and methods not under test. |
| 35 | | DateSearchedForIsDefined_WithUndefinedDate_ShouldReturnFalse | Verifying that date searched for is defined with undefined date returns false | Setup with undefined date -> Call DateSearchedForIsDefined -> Assert returns false | DateSearchedForIsDefined with undefined date returns false | In scope: DateSearchedForIsDefined behavior, with undefined date scenario. Out of scope: other scenarios and methods not under test. |
| 36 | | ShouldFilterSpendCappedProviders_WithCommercialInsurance_ShouldReturnTrue | Verifying that should filter spend capped providers with commercial insurance returns true | Setup with commercial insurance -> Call ShouldFilterSpendCappedProviders -> Assert returns true | ShouldFilterSpendCappedProviders with commercial insurance returns true | In scope: ShouldFilterSpendCappedProviders behavior, with commercial insurance scenario. Out of scope: other scenarios and methods not under test. |
| 37 | | ShouldFilterSpendCappedProviders_WithSelfPay_ShouldReturnFalse | Verifying that should filter spend capped providers with self pay returns false | Setup with self pay -> Call ShouldFilterSpendCappedProviders -> Assert returns false | ShouldFilterSpendCappedProviders with self pay returns false | In scope: ShouldFilterSpendCappedProviders behavior, with self pay scenario. Out of scope: other scenarios and methods not under test. |
| 38 | | ShouldFilterSpendCappedProviders_WithNonCommercialInsurance_ShouldReturnFalse | Verifying that should filter spend capped providers with non commercial insurance returns false | Setup with non commercial insurance -> Call ShouldFilterSpendCappedProviders -> Assert returns false | ShouldFilterSpendCappedProviders with non commercial insurance returns false | In scope: ShouldFilterSpendCappedProviders behavior, with non commercial insurance scenario. Out of scope: other scenarios and methods not under test. |
| 39 | | ReplayNodeId_ShouldBeSettable | Verifying that replay node id should be settable | Setup test data and mocks -> Call ReplayNodeId -> Assert expected behavior of ReplayNodeId | ReplayNodeId should be settable | In scope: ReplayNodeId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 40 | | ReplayNodeId_ShouldDefaultToNull | Verifying that replay node id should default to null | Setup with null input -> Call ReplayNodeId -> Assert expected behavior of ReplayNodeId | ReplayNodeId should default to null | In scope: null input handling for ReplayNodeId. Out of scope: valid input scenarios. |
| 41 | | FtsSearchQuery_ShouldBeSettable | Verifying that fts search query should be settable | Setup test data and mocks -> Call FtsSearchQuery -> Assert expected behavior of FtsSearchQuery | FtsSearchQuery should be settable | In scope: FtsSearchQuery behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 42 | | FtsSearchQuery_ShouldDefaultToNull | Verifying that fts search query should default to null | Setup with null input -> Call FtsSearchQuery -> Assert expected behavior of FtsSearchQuery | FtsSearchQuery should default to null | In scope: null input handling for FtsSearchQuery. Out of scope: valid input scenarios. |
| 43 | | CeSearchQuery_ShouldBeSettable | Verifying that ce search query should be settable | Setup test data and mocks -> Call CeSearchQuery -> Assert expected behavior of CeSearchQuery | CeSearchQuery should be settable | In scope: CeSearchQuery behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 44 | | CeSearchQuery_ShouldDefaultToNull | Verifying that ce search query should default to null | Setup with null input -> Call CeSearchQuery -> Assert expected behavior of CeSearchQuery | CeSearchQuery should default to null | In scope: null input handling for CeSearchQuery. Out of scope: valid input scenarios. |
| 45 | | SearchQuery_ShouldBeSettable | Verifying that search query should be settable | Setup test data and mocks -> Call SearchQuery -> Assert expected behavior of SearchQuery | SearchQuery should be settable | In scope: SearchQuery behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 46 | | Latitude_ShouldBeSettable | Verifying that latitude should be settable | Setup test data and mocks -> Call Latitude -> Assert expected behavior of Latitude | Latitude should be settable | In scope: Latitude behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 47 | | Longitude_ShouldBeSettable | Verifying that longitude should be settable | Setup test data and mocks -> Call Longitude -> Assert expected behavior of Longitude | Longitude should be settable | In scope: Longitude behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 48 | | InsuranceCarrierId_ShouldBeSettable | Verifying that insurance carrier id should be settable | Setup test data and mocks -> Call InsuranceCarrierId -> Assert expected behavior of InsuranceCarrierId | InsuranceCarrierId should be settable | In scope: InsuranceCarrierId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 49 | | InsurancePlanId_ShouldBeSettable | Verifying that insurance plan id should be settable | Setup test data and mocks -> Call InsurancePlanId -> Assert expected behavior of InsurancePlanId | InsurancePlanId should be settable | In scope: InsurancePlanId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 50 | | SpecialtyId_ShouldBeSettable | Verifying that specialty id should be settable | Setup test data and mocks -> Call SpecialtyId -> Assert expected behavior of SpecialtyId | SpecialtyId should be settable | In scope: SpecialtyId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 51 | | ProcedureId_ShouldBeSettable | Verifying that procedure id should be settable | Setup test data and mocks -> Call ProcedureId -> Assert expected behavior of ProcedureId | ProcedureId should be settable | In scope: ProcedureId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 52 | | Platform_ShouldBeSettable | Verifying that platform should be settable | Setup test data and mocks -> Call Platform -> Assert expected behavior of Platform | Platform should be settable | In scope: Platform behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 53 | | DeviceId_ShouldBeSettable | Verifying that device id should be settable | Setup test data and mocks -> Call DeviceId -> Assert expected behavior of DeviceId | DeviceId should be settable | In scope: DeviceId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 54 | | UserId_ShouldBeSettable | Verifying that user id should be settable | Setup test data and mocks -> Call UserId -> Assert expected behavior of UserId | UserId should be settable | In scope: UserId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 55 | | SessionId_ShouldBeSettable | Verifying that session id should be settable | Setup test data and mocks -> Call SessionId -> Assert expected behavior of SessionId | SessionId should be settable | In scope: SessionId behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 56 | | Page_ShouldBeSettable | Verifying that page should be settable | Setup test data and mocks -> Call Page -> Assert expected behavior of Page | Page should be settable | In scope: Page behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 57 | | SortBy_ShouldBeSettable | Verifying that sort by should be settable | Setup test data and mocks -> Call SortBy -> Assert expected behavior of SortBy | SortBy should be settable | In scope: SortBy behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 58 | | SearchType_ShouldBeSettable | Verifying that search type should be settable | Setup test data and mocks -> Call SearchType -> Assert expected behavior of SearchType | SearchType should be settable | In scope: SearchType behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |
| 59 | | Distance_ShouldBeSettable | Verifying that distance should be settable | Setup test data and mocks -> Call Distance -> Assert expected behavior of Distance | Distance should be settable | In scope: Distance behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## SpecialtyFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## SpendLockStatusTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enum_ShouldHaveExpectedValues | Verifying that enum should have expected values | Setup test data and mocks -> Call Enum -> Assert expected behavior of Enum | Enum should have expected values | In scope: Enum behavior, should have expected values scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enum_ShouldBeComparable | Verifying that enum should be comparable | Setup test data and mocks -> Call Enum -> Assert expected behavior of Enum | Enum should be comparable | In scope: Enum behavior, should be comparable scenario. Out of scope: other scenarios and methods not under test. |

## TimeFeaturesTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Properties_ShouldBeSettable | Verifying that properties should be settable | Setup test data and mocks -> Call Properties -> Assert expected behavior of Properties | Properties should be settable | In scope: Properties behavior, should be settable scenario. Out of scope: other scenarios and methods not under test. |

## TimeRangeTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Constructor_ShouldSetStartAndEndMinutes | Verifying that constructor should set start and end minutes | Setup test data and mocks -> Call Constructor -> Assert expected behavior of Constructor | Constructor should set start and end minutes | In scope: Constructor behavior, should set start and end minutes scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Contains_WhenTimeIsBeforeStart_ShouldReturnFalse | Verifying that contains when time is before start returns false | Setup when time is before start -> Call Contains -> Assert returns false | Contains when time is before start returns false | In scope: Contains behavior, when time is before start scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Contains_WhenTimeIsAfterEnd_ShouldReturnFalse | Verifying that contains when time is after end returns false | Setup when time is after end -> Call Contains -> Assert returns false | Contains when time is after end returns false | In scope: Contains behavior, when time is after end scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Contains_WhenTimeIsAtStart_ShouldReturnTrue | Verifying that contains when time is at start returns true | Setup when time is at start -> Call Contains -> Assert returns true | Contains when time is at start returns true | In scope: Contains behavior, when time is at start scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Contains_WhenTimeIsAtEnd_ShouldReturnTrue | Verifying that contains when time is at end returns true | Setup when time is at end -> Call Contains -> Assert returns true | Contains when time is at end returns true | In scope: Contains behavior, when time is at end scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Contains_WhenTimeIsWithinRange_ShouldReturnTrue | Verifying that contains when time is within range returns true | Setup when time is within range -> Call Contains -> Assert returns true | Contains when time is within range returns true | In scope: Contains behavior, when time is within range scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Contains_WhenTimeIsMidnight_ShouldHandleCorrectly | Verifying that contains when time is midnight handle correctly | Setup when time is midnight -> Call Contains -> Assert handle correctly | Contains when time is midnight handle correctly | In scope: Contains behavior, when time is midnight scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Contains_WhenTimeIsEndOfDay_ShouldHandleCorrectly | Verifying that contains when time is end of day handle correctly | Setup when time is end of day -> Call Contains -> Assert handle correctly | Contains when time is end of day handle correctly | In scope: Contains behavior, when time is end of day scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Contains_WhenRangeSpansMultipleHours_ShouldWorkCorrectly | Verifying that contains when range spans multiple hours work correctly | Setup when range spans multiple hours -> Call Contains -> Assert work correctly | Contains when range spans multiple hours work correctly | In scope: Contains behavior, when range spans multiple hours scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Contains_WhenTimeHasMinutes_ShouldCalculateCorrectly | Verifying that contains when time has minutes calculate correctly | Setup when time has minutes -> Call Contains -> Assert calculate correctly | Contains when time has minutes calculate correctly | In scope: Contains behavior, when time has minutes scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Contains_WhenRangeIsSingleMinute_ShouldWork | Verifying that contains when range is single minute work | Setup when range is single minute -> Call Contains -> Assert work | Contains when range is single minute work | In scope: Contains behavior, when range is single minute scenario. Out of scope: other scenarios and methods not under test. |

# Utils

## StringExtensionsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | StripAccents_WithNull_ShouldReturnNull | Verifying that strip accents with null returns null | Setup with null input -> Call StripAccents -> Assert returns null | StripAccents with null returns null | In scope: null input handling for StripAccents. Out of scope: valid input scenarios. |
| 2 | | StripAccents_WithEmptyString_ShouldReturnEmptyString | Verifying that strip accents with empty string returns empty string | Setup with empty input -> Call StripAccents -> Assert returns empty collection | StripAccents with empty string returns empty string | In scope: empty input handling for StripAccents. Out of scope: non-empty input scenarios. |
| 3 | | StripAccents_WithCafe_ShouldRemoveAccent | Verifying that strip accents with cafe remove accent | Setup with cafe -> Call StripAccents -> Assert remove accent | StripAccents with cafe remove accent | In scope: StripAccents behavior, with cafe scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | StripAccents_WithNaive_ShouldRemoveDiaeresis | Verifying that strip accents with naive remove diaeresis | Setup with naive -> Call StripAccents -> Assert remove diaeresis | StripAccents with naive remove diaeresis | In scope: StripAccents behavior, with naive scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | StripAccents_WithZurich_ShouldRemoveUmlaut | Verifying that strip accents with zurich remove umlaut | Setup with zurich -> Call StripAccents -> Assert remove umlaut | StripAccents with zurich remove umlaut | In scope: StripAccents behavior, with zurich scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | StripAccents_WithNoAccents_ShouldReturnOriginal | Verifying that strip accents with no accents returns original | Setup with no accents -> Call StripAccents -> Assert return original | StripAccents with no accents returns original | In scope: StripAccents behavior, with no accents scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | StripAccents_WithMultipleAccents_ShouldRemoveAll | Verifying that strip accents with multiple accents remove all | Setup with multiple accents -> Call StripAccents -> Assert remove all | StripAccents with multiple accents remove all | In scope: StripAccents behavior, with multiple accents scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | StripAccents_WithSpanishAccents_ShouldRemoveAccents | Verifying that strip accents with spanish accents remove accents | Setup with spanish accents -> Call StripAccents -> Assert remove accents | StripAccents with spanish accents remove accents | In scope: StripAccents behavior, with spanish accents scenario. Out of scope: other scenarios and methods not under test. |

## TextHelperTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ExtractSentences_WithNull_ShouldReturnEmptyList | Verifying that extract sentences with null returns empty list | Setup with null input -> Call ExtractSentences -> Assert returns empty collection | ExtractSentences with null returns empty list | In scope: null input handling for ExtractSentences. Out of scope: valid input scenarios. |
| 2 | | ExtractSentences_WithEmptyString_ShouldReturnEmptyList | Verifying that extract sentences with empty string returns empty list | Setup with empty input -> Call ExtractSentences -> Assert returns empty collection | ExtractSentences with empty string returns empty list | In scope: empty input handling for ExtractSentences. Out of scope: non-empty input scenarios. |
| 3 | | ExtractSentences_WithWhitespace_ShouldReturnEmptyList | Verifying that extract sentences with whitespace returns empty list | Setup with whitespace -> Call ExtractSentences -> Assert returns empty collection | ExtractSentences with whitespace returns empty list | In scope: ExtractSentences behavior, with whitespace scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ExtractSentences_WithSingleSentence_ShouldReturnOneSentence | Verifying that extract sentences with single sentence returns one sentence | Setup with single sentence -> Call ExtractSentences -> Assert return one sentence | ExtractSentences with single sentence returns one sentence | In scope: ExtractSentences behavior, with single sentence scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ExtractSentences_WithMultipleSentences_ShouldReturnAllSentences | Verifying that extract sentences with multiple sentences returns all sentences | Setup with multiple sentences -> Call ExtractSentences -> Assert return all sentences | ExtractSentences with multiple sentences returns all sentences | In scope: ExtractSentences behavior, with multiple sentences scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ExtractSentences_WithExclamationAndQuestion_ShouldSplitOnAllPunctuation | Verifying that extract sentences with exclamation and question split on all punctuation | Setup with exclamation and question -> Call ExtractSentences -> Assert split on all punctuation | ExtractSentences with exclamation and question split on all punctuation | In scope: ExtractSentences behavior, with exclamation and question scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ExtractSentences_WithDoctorAbbreviation_ShouldNotSplitOnDr | Verifying that extract sentences with doctor abbreviation does not split on dr | Setup with doctor abbreviation -> Call ExtractSentences -> Assert not split on dr | ExtractSentences with doctor abbreviation does not split on dr | In scope: ExtractSentences behavior, with doctor abbreviation scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ExtractSentences_WithMDDegree_ShouldSplitOnMD | Verifying that extract sentences with m d degree split on m d | Setup with m d degree -> Call ExtractSentences -> Assert split on m d | ExtractSentences with m d degree split on m d | In scope: ExtractSentences behavior, with m d degree scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | ExtractSentences_WithMDDegreeWithPeriods_ShouldSplitOnMD | Verifying that extract sentences with m d degree with periods split on m d | Setup with m d degree with periods -> Call ExtractSentences -> Assert split on m d | ExtractSentences with m d degree with periods split on m d | In scope: ExtractSentences behavior, with m d degree with periods scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | ExtractSentences_WithDODegree_ShouldSplitOnDO | Verifying that extract sentences with d o degree split on d o | Setup with d o degree -> Call ExtractSentences -> Assert split on d o | ExtractSentences with d o degree split on d o | In scope: ExtractSentences behavior, with d o degree scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | ExtractSentences_WithPhDAbbreviation_ShouldNotSplitOnPhD | Verifying that extract sentences with ph d abbreviation does not split on ph d | Setup with ph d abbreviation -> Call ExtractSentences -> Assert not split on ph d | ExtractSentences with ph d abbreviation does not split on ph d | In scope: ExtractSentences behavior, with ph d abbreviation scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | ExtractSentences_WithMultipleMedicalAbbreviations_ShouldHandleAll | Verifying that extract sentences with multiple medical abbreviations handle all | Setup with multiple medical abbreviations -> Call ExtractSentences -> Assert handle all | ExtractSentences with multiple medical abbreviations handle all | In scope: ExtractSentences behavior, with multiple medical abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | ExtractSentences_WithDDSAndDMDAbbreviations_ShouldNotSplit | Verifying that extract sentences with d d s and d m d abbreviations does not split | Setup with d d s and d m d abbreviations -> Call ExtractSentences -> Assert not split | ExtractSentences with d d s and d m d abbreviations does not split | In scope: ExtractSentences behavior, with d d s and d m d abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | ExtractSentences_WithNPAndPAAbbreviations_ShouldNotSplit | Verifying that extract sentences with n p and p a abbreviations does not split | Setup with n p and p a abbreviations -> Call ExtractSentences -> Assert not split | ExtractSentences with n p and p a abbreviations does not split | In scope: ExtractSentences behavior, with n p and p a abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | ExtractSentences_WithStreetAddressAbbreviation_ShouldNotSplitOnSt | Verifying that extract sentences with street address abbreviation does not split on st | Setup with street address abbreviation -> Call ExtractSentences -> Assert not split on st | ExtractSentences with street address abbreviation does not split on st | In scope: ExtractSentences behavior, with street address abbreviation scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | ExtractSentences_WithUSAbbreviation_ShouldNotSplitOnUS | Verifying that extract sentences with u s abbreviation does not split on u s | Setup with u s abbreviation -> Call ExtractSentences -> Assert not split on u s | ExtractSentences with u s abbreviation does not split on u s | In scope: ExtractSentences behavior, with u s abbreviation scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | ExtractSentences_WithEtcAbbreviation_ShouldSplitOnEtc | Verifying that extract sentences with etc abbreviation split on etc | Setup with etc abbreviation -> Call ExtractSentences -> Assert split on etc | ExtractSentences with etc abbreviation split on etc | In scope: ExtractSentences behavior, with etc abbreviation scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | ExtractSentences_WithNoPunctuation_ShouldReturnWholeSentence | Verifying that extract sentences with no punctuation returns whole sentence | Setup with no punctuation -> Call ExtractSentences -> Assert return whole sentence | ExtractSentences with no punctuation returns whole sentence | In scope: ExtractSentences behavior, with no punctuation scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | ExtractSentences_WithMultipleSpacesBetweenSentences_ShouldHandleGracefully | Verifying that extract sentences with multiple spaces between sentences handle gracefully | Setup with multiple spaces between sentences -> Call ExtractSentences -> Assert handle gracefully | ExtractSentences with multiple spaces between sentences handle gracefully | In scope: ExtractSentences behavior, with multiple spaces between sentences scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | ExtractSentences_WithNewlines_ShouldHandleNewlines | Verifying that extract sentences with newlines handle newlines | Setup with newlines -> Call ExtractSentences -> Assert handle newlines | ExtractSentences with newlines handle newlines | In scope: ExtractSentences behavior, with newlines scenario. Out of scope: other scenarios and methods not under test. |
| 21 | | ExtractSentences_WithLowercaseAfterPeriod_ShouldNotSplit | Verifying that extract sentences with lowercase after period does not split | Setup with lowercase after period -> Call ExtractSentences -> Assert not split | ExtractSentences with lowercase after period does not split | In scope: ExtractSentences behavior, with lowercase after period scenario. Out of scope: other scenarios and methods not under test. |
| 22 | | ExtractSentences_WithMixedCase_ShouldHandleCorrectly | Verifying that extract sentences with mixed case handle correctly | Setup with mixed case -> Call ExtractSentences -> Assert handle correctly | ExtractSentences with mixed case handle correctly | In scope: ExtractSentences behavior, with mixed case scenario. Out of scope: other scenarios and methods not under test. |
| 23 | | ExtractSentences_WithJrAndSrAbbreviations_ShouldNotSplit | Verifying that extract sentences with jr and sr abbreviations does not split | Setup with jr and sr abbreviations -> Call ExtractSentences -> Assert not split | ExtractSentences with jr and sr abbreviations does not split | In scope: ExtractSentences behavior, with jr and sr abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 24 | | ExtractSentences_WithIeAndEgAbbreviations_ShouldNotSplit | Verifying that extract sentences with ie and eg abbreviations does not split | Setup with ie and eg abbreviations -> Call ExtractSentences -> Assert not split | ExtractSentences with ie and eg abbreviations does not split | In scope: ExtractSentences behavior, with ie and eg abbreviations scenario. Out of scope: other scenarios and methods not under test. |
| 25 | | ExtractSentences_RealWorldMedicalText_ShouldHandleComplex | Verifying that extract sentences real world medical text handle complex | Setup test data and mocks -> Call ExtractSentences -> Assert handle complex | ExtractSentences real world medical text handle complex | In scope: ExtractSentences behavior, real world medical text scenario. Out of scope: other scenarios and methods not under test. |
| 26 | | ExtractSentences_WithNewlinesWithinSentence_ShouldNormalizeToSpaces | Verifying that extract sentences with newlines within sentence normalize to spaces | Setup with newlines within sentence -> Call ExtractSentences -> Assert normalize to spaces | ExtractSentences with newlines within sentence normalize to spaces | In scope: ExtractSentences behavior, with newlines within sentence scenario. Out of scope: other scenarios and methods not under test. |
| 27 | | ExtractSentences_WithMultipleWhitespaceTypes_ShouldNormalizeAll | Verifying that extract sentences with multiple whitespace types normalize all | Setup with multiple whitespace types -> Call ExtractSentences -> Assert normalize all | ExtractSentences with multiple whitespace types normalize all | In scope: ExtractSentences behavior, with multiple whitespace types scenario. Out of scope: other scenarios and methods not under test. |

# Search/Es/Filtering

## AcceptedInsuranceFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_AcceptedInsurance_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter accepted insurance with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter accepted insurance with multiple values_ should filter correctly | In scope: Filter behavior, accepted insurance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_AcceptedInsurance_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter accepted insurance with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter accepted insurance with edge case values_ should handle gracefully | In scope: Filter behavior, accepted insurance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_AcceptedInsurance_ShouldReturnCorrectEsQuery | Verifying that build query accepted insurance returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery accepted insurance returns correct es query | In scope: BuildQuery behavior, accepted insurance scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_AcceptedInsurance_WithNullParam_ShouldReturnMatchAll | Verifying that build query accepted insurance with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery accepted insurance with null param_ should return match all | In scope: BuildQuery behavior, accepted insurance scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_AcceptedInsurance_ShouldEmitFilterMetrics | Verifying that filter accepted insurance emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter accepted insurance emit filter metrics | In scope: Filter behavior, accepted insurance scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## AgeFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Age_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter age with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter age with multiple values_ should filter correctly | In scope: Filter behavior, age scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Age_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter age with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter age with edge case values_ should handle gracefully | In scope: Filter behavior, age scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Age_ShouldReturnCorrectEsQuery | Verifying that build query age returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery age returns correct es query | In scope: BuildQuery behavior, age scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Age_WithNullParam_ShouldReturnMatchAll | Verifying that build query age with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery age with null param_ should return match all | In scope: BuildQuery behavior, age scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Age_ShouldEmitFilterMetrics | Verifying that filter age emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter age emit filter metrics | In scope: Filter behavior, age scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## AvailabilityFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Availability_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter availability with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter availability with multiple values_ should filter correctly | In scope: Filter behavior, availability scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Availability_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter availability with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter availability with edge case values_ should handle gracefully | In scope: Filter behavior, availability scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Availability_ShouldReturnCorrectEsQuery | Verifying that build query availability returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery availability returns correct es query | In scope: BuildQuery behavior, availability scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Availability_WithNullParam_ShouldReturnMatchAll | Verifying that build query availability with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery availability with null param_ should return match all | In scope: BuildQuery behavior, availability scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Availability_ShouldEmitFilterMetrics | Verifying that filter availability emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter availability emit filter metrics | In scope: Filter behavior, availability scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## BookableOnlyFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_BookableOnly_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter bookable only with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter bookable only with multiple values_ should filter correctly | In scope: Filter behavior, bookable only scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_BookableOnly_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter bookable only with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter bookable only with edge case values_ should handle gracefully | In scope: Filter behavior, bookable only scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_BookableOnly_ShouldReturnCorrectEsQuery | Verifying that build query bookable only returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery bookable only returns correct es query | In scope: BuildQuery behavior, bookable only scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_BookableOnly_WithNullParam_ShouldReturnMatchAll | Verifying that build query bookable only with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery bookable only with null param_ should return match all | In scope: BuildQuery behavior, bookable only scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_BookableOnly_ShouldEmitFilterMetrics | Verifying that filter bookable only emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter bookable only emit filter metrics | In scope: Filter behavior, bookable only scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## BrandFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Brand_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter brand with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter brand with multiple values_ should filter correctly | In scope: Filter behavior, brand scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Brand_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter brand with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter brand with edge case values_ should handle gracefully | In scope: Filter behavior, brand scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Brand_ShouldReturnCorrectEsQuery | Verifying that build query brand returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery brand returns correct es query | In scope: BuildQuery behavior, brand scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Brand_WithNullParam_ShouldReturnMatchAll | Verifying that build query brand with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery brand with null param_ should return match all | In scope: BuildQuery behavior, brand scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Brand_ShouldEmitFilterMetrics | Verifying that filter brand emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter brand emit filter metrics | In scope: Filter behavior, brand scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## CityFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_City_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter city with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter city with multiple values_ should filter correctly | In scope: Filter behavior, city scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_City_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter city with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter city with edge case values_ should handle gracefully | In scope: Filter behavior, city scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_City_ShouldReturnCorrectEsQuery | Verifying that build query city returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery city returns correct es query | In scope: BuildQuery behavior, city scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_City_WithNullParam_ShouldReturnMatchAll | Verifying that build query city with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery city with null param_ should return match all | In scope: BuildQuery behavior, city scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_City_ShouldEmitFilterMetrics | Verifying that filter city emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter city emit filter metrics | In scope: Filter behavior, city scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## CoordinateFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Coordinate_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter coordinate with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter coordinate with multiple values_ should filter correctly | In scope: Filter behavior, coordinate scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Coordinate_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter coordinate with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter coordinate with edge case values_ should handle gracefully | In scope: Filter behavior, coordinate scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Coordinate_ShouldReturnCorrectEsQuery | Verifying that build query coordinate returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery coordinate returns correct es query | In scope: BuildQuery behavior, coordinate scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Coordinate_WithNullParam_ShouldReturnMatchAll | Verifying that build query coordinate with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery coordinate with null param_ should return match all | In scope: BuildQuery behavior, coordinate scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Coordinate_ShouldEmitFilterMetrics | Verifying that filter coordinate emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter coordinate emit filter metrics | In scope: Filter behavior, coordinate scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## CostPlanFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_CostPlan_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter cost plan with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter cost plan with multiple values_ should filter correctly | In scope: Filter behavior, cost plan scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_CostPlan_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter cost plan with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter cost plan with edge case values_ should handle gracefully | In scope: Filter behavior, cost plan scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_CostPlan_ShouldReturnCorrectEsQuery | Verifying that build query cost plan returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery cost plan returns correct es query | In scope: BuildQuery behavior, cost plan scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_CostPlan_WithNullParam_ShouldReturnMatchAll | Verifying that build query cost plan with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery cost plan with null param_ should return match all | In scope: BuildQuery behavior, cost plan scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_CostPlan_ShouldEmitFilterMetrics | Verifying that filter cost plan emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter cost plan emit filter metrics | In scope: Filter behavior, cost plan scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## DateFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Date_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter date with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter date with multiple values_ should filter correctly | In scope: Filter behavior, date scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Date_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter date with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter date with edge case values_ should handle gracefully | In scope: Filter behavior, date scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Date_ShouldReturnCorrectEsQuery | Verifying that build query date returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery date returns correct es query | In scope: BuildQuery behavior, date scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Date_WithNullParam_ShouldReturnMatchAll | Verifying that build query date with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery date with null param_ should return match all | In scope: BuildQuery behavior, date scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Date_ShouldEmitFilterMetrics | Verifying that filter date emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter date emit filter metrics | In scope: Filter behavior, date scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## DistanceFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Distance_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter distance with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter distance with multiple values_ should filter correctly | In scope: Filter behavior, distance scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Distance_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter distance with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter distance with edge case values_ should handle gracefully | In scope: Filter behavior, distance scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Distance_ShouldReturnCorrectEsQuery | Verifying that build query distance returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery distance returns correct es query | In scope: BuildQuery behavior, distance scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Distance_WithNullParam_ShouldReturnMatchAll | Verifying that build query distance with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery distance with null param_ should return match all | In scope: BuildQuery behavior, distance scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Distance_ShouldEmitFilterMetrics | Verifying that filter distance emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter distance emit filter metrics | In scope: Filter behavior, distance scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## DiversityFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Diversity_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter diversity with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter diversity with multiple values_ should filter correctly | In scope: Filter behavior, diversity scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Diversity_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter diversity with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter diversity with edge case values_ should handle gracefully | In scope: Filter behavior, diversity scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Diversity_ShouldReturnCorrectEsQuery | Verifying that build query diversity returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery diversity returns correct es query | In scope: BuildQuery behavior, diversity scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Diversity_WithNullParam_ShouldReturnMatchAll | Verifying that build query diversity with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery diversity with null param_ should return match all | In scope: BuildQuery behavior, diversity scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Diversity_ShouldEmitFilterMetrics | Verifying that filter diversity emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter diversity emit filter metrics | In scope: Filter behavior, diversity scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## EnterpriseFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Enterprise_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter enterprise with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter enterprise with multiple values_ should filter correctly | In scope: Filter behavior, enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Enterprise_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter enterprise with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter enterprise with edge case values_ should handle gracefully | In scope: Filter behavior, enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Enterprise_ShouldReturnCorrectEsQuery | Verifying that build query enterprise returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery enterprise returns correct es query | In scope: BuildQuery behavior, enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Enterprise_WithNullParam_ShouldReturnMatchAll | Verifying that build query enterprise with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery enterprise with null param_ should return match all | In scope: BuildQuery behavior, enterprise scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Enterprise_ShouldEmitFilterMetrics | Verifying that filter enterprise emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter enterprise emit filter metrics | In scope: Filter behavior, enterprise scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## ExternalProviderFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_ExternalProvider_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter external provider with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter external provider with multiple values_ should filter correctly | In scope: Filter behavior, external provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_ExternalProvider_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter external provider with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter external provider with edge case values_ should handle gracefully | In scope: Filter behavior, external provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_ExternalProvider_ShouldReturnCorrectEsQuery | Verifying that build query external provider returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery external provider returns correct es query | In scope: BuildQuery behavior, external provider scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_ExternalProvider_WithNullParam_ShouldReturnMatchAll | Verifying that build query external provider with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery external provider with null param_ should return match all | In scope: BuildQuery behavior, external provider scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_ExternalProvider_ShouldEmitFilterMetrics | Verifying that filter external provider emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter external provider emit filter metrics | In scope: Filter behavior, external provider scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## FacetFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Facet_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter facet with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter facet with multiple values_ should filter correctly | In scope: Filter behavior, facet scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Facet_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter facet with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter facet with edge case values_ should handle gracefully | In scope: Filter behavior, facet scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Facet_ShouldReturnCorrectEsQuery | Verifying that build query facet returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery facet returns correct es query | In scope: BuildQuery behavior, facet scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Facet_WithNullParam_ShouldReturnMatchAll | Verifying that build query facet with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery facet with null param_ should return match all | In scope: BuildQuery behavior, facet scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Facet_ShouldEmitFilterMetrics | Verifying that filter facet emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter facet emit filter metrics | In scope: Filter behavior, facet scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## GenderFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Gender_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter gender with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter gender with multiple values_ should filter correctly | In scope: Filter behavior, gender scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Gender_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter gender with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter gender with edge case values_ should handle gracefully | In scope: Filter behavior, gender scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Gender_ShouldReturnCorrectEsQuery | Verifying that build query gender returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery gender returns correct es query | In scope: BuildQuery behavior, gender scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Gender_WithNullParam_ShouldReturnMatchAll | Verifying that build query gender with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery gender with null param_ should return match all | In scope: BuildQuery behavior, gender scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Gender_ShouldEmitFilterMetrics | Verifying that filter gender emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter gender emit filter metrics | In scope: Filter behavior, gender scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## HighlyRatedFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_HighlyRated_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter highly rated with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter highly rated with multiple values_ should filter correctly | In scope: Filter behavior, highly rated scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_HighlyRated_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter highly rated with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter highly rated with edge case values_ should handle gracefully | In scope: Filter behavior, highly rated scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_HighlyRated_ShouldReturnCorrectEsQuery | Verifying that build query highly rated returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery highly rated returns correct es query | In scope: BuildQuery behavior, highly rated scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_HighlyRated_WithNullParam_ShouldReturnMatchAll | Verifying that build query highly rated with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery highly rated with null param_ should return match all | In scope: BuildQuery behavior, highly rated scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_HighlyRated_ShouldEmitFilterMetrics | Verifying that filter highly rated emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter highly rated emit filter metrics | In scope: Filter behavior, highly rated scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## HospitalAffiliationFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_HospitalAffiliation_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter hospital affiliation with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter hospital affiliation with multiple values_ should filter correctly | In scope: Filter behavior, hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_HospitalAffiliation_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter hospital affiliation with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter hospital affiliation with edge case values_ should handle gracefully | In scope: Filter behavior, hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_HospitalAffiliation_ShouldReturnCorrectEsQuery | Verifying that build query hospital affiliation returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery hospital affiliation returns correct es query | In scope: BuildQuery behavior, hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_HospitalAffiliation_WithNullParam_ShouldReturnMatchAll | Verifying that build query hospital affiliation with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery hospital affiliation with null param_ should return match all | In scope: BuildQuery behavior, hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_HospitalAffiliation_ShouldEmitFilterMetrics | Verifying that filter hospital affiliation emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter hospital affiliation emit filter metrics | In scope: Filter behavior, hospital affiliation scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## LanguageFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Language_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter language with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter language with multiple values_ should filter correctly | In scope: Filter behavior, language scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Language_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter language with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter language with edge case values_ should handle gracefully | In scope: Filter behavior, language scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Language_ShouldReturnCorrectEsQuery | Verifying that build query language returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery language returns correct es query | In scope: BuildQuery behavior, language scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Language_WithNullParam_ShouldReturnMatchAll | Verifying that build query language with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery language with null param_ should return match all | In scope: BuildQuery behavior, language scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Language_ShouldEmitFilterMetrics | Verifying that filter language emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter language emit filter metrics | In scope: Filter behavior, language scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## LocationFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Location_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter location with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter location with multiple values_ should filter correctly | In scope: Filter behavior, location scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Location_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter location with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter location with edge case values_ should handle gracefully | In scope: Filter behavior, location scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Location_ShouldReturnCorrectEsQuery | Verifying that build query location returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery location returns correct es query | In scope: BuildQuery behavior, location scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Location_WithNullParam_ShouldReturnMatchAll | Verifying that build query location with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery location with null param_ should return match all | In scope: BuildQuery behavior, location scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Location_ShouldEmitFilterMetrics | Verifying that filter location emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter location emit filter metrics | In scope: Filter behavior, location scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## NetworkFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Network_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter network with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter network with multiple values_ should filter correctly | In scope: Filter behavior, network scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Network_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter network with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter network with edge case values_ should handle gracefully | In scope: Filter behavior, network scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Network_ShouldReturnCorrectEsQuery | Verifying that build query network returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery network returns correct es query | In scope: BuildQuery behavior, network scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Network_WithNullParam_ShouldReturnMatchAll | Verifying that build query network with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery network with null param_ should return match all | In scope: BuildQuery behavior, network scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Network_ShouldEmitFilterMetrics | Verifying that filter network emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter network emit filter metrics | In scope: Filter behavior, network scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## NewPatientFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_NewPatient_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter new patient with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter new patient with multiple values_ should filter correctly | In scope: Filter behavior, new patient scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_NewPatient_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter new patient with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter new patient with edge case values_ should handle gracefully | In scope: Filter behavior, new patient scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_NewPatient_ShouldReturnCorrectEsQuery | Verifying that build query new patient returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery new patient returns correct es query | In scope: BuildQuery behavior, new patient scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_NewPatient_WithNullParam_ShouldReturnMatchAll | Verifying that build query new patient with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery new patient with null param_ should return match all | In scope: BuildQuery behavior, new patient scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_NewPatient_ShouldEmitFilterMetrics | Verifying that filter new patient emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter new patient emit filter metrics | In scope: Filter behavior, new patient scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## OfficeHoursFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_OfficeHours_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter office hours with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter office hours with multiple values_ should filter correctly | In scope: Filter behavior, office hours scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_OfficeHours_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter office hours with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter office hours with edge case values_ should handle gracefully | In scope: Filter behavior, office hours scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_OfficeHours_ShouldReturnCorrectEsQuery | Verifying that build query office hours returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery office hours returns correct es query | In scope: BuildQuery behavior, office hours scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_OfficeHours_WithNullParam_ShouldReturnMatchAll | Verifying that build query office hours with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery office hours with null param_ should return match all | In scope: BuildQuery behavior, office hours scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_OfficeHours_ShouldEmitFilterMetrics | Verifying that filter office hours emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter office hours emit filter metrics | In scope: Filter behavior, office hours scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## OnlineSchedulingFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_OnlineScheduling_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter online scheduling with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter online scheduling with multiple values_ should filter correctly | In scope: Filter behavior, online scheduling scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_OnlineScheduling_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter online scheduling with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter online scheduling with edge case values_ should handle gracefully | In scope: Filter behavior, online scheduling scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_OnlineScheduling_ShouldReturnCorrectEsQuery | Verifying that build query online scheduling returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery online scheduling returns correct es query | In scope: BuildQuery behavior, online scheduling scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_OnlineScheduling_WithNullParam_ShouldReturnMatchAll | Verifying that build query online scheduling with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery online scheduling with null param_ should return match all | In scope: BuildQuery behavior, online scheduling scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_OnlineScheduling_ShouldEmitFilterMetrics | Verifying that filter online scheduling emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter online scheduling emit filter metrics | In scope: Filter behavior, online scheduling scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## PracticeFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Practice_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter practice with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter practice with multiple values_ should filter correctly | In scope: Filter behavior, practice scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Practice_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter practice with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter practice with edge case values_ should handle gracefully | In scope: Filter behavior, practice scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Practice_ShouldReturnCorrectEsQuery | Verifying that build query practice returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery practice returns correct es query | In scope: BuildQuery behavior, practice scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Practice_WithNullParam_ShouldReturnMatchAll | Verifying that build query practice with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery practice with null param_ should return match all | In scope: BuildQuery behavior, practice scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Practice_ShouldEmitFilterMetrics | Verifying that filter practice emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter practice emit filter metrics | In scope: Filter behavior, practice scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## ProcedureFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Procedure_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter procedure with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter procedure with multiple values_ should filter correctly | In scope: Filter behavior, procedure scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Procedure_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter procedure with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter procedure with edge case values_ should handle gracefully | In scope: Filter behavior, procedure scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Procedure_ShouldReturnCorrectEsQuery | Verifying that build query procedure returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery procedure returns correct es query | In scope: BuildQuery behavior, procedure scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Procedure_WithNullParam_ShouldReturnMatchAll | Verifying that build query procedure with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery procedure with null param_ should return match all | In scope: BuildQuery behavior, procedure scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Procedure_ShouldEmitFilterMetrics | Verifying that filter procedure emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter procedure emit filter metrics | In scope: Filter behavior, procedure scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## ProviderFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Provider_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter provider with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter provider with multiple values_ should filter correctly | In scope: Filter behavior, provider scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Provider_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter provider with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter provider with edge case values_ should handle gracefully | In scope: Filter behavior, provider scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Provider_ShouldReturnCorrectEsQuery | Verifying that build query provider returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery provider returns correct es query | In scope: BuildQuery behavior, provider scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Provider_WithNullParam_ShouldReturnMatchAll | Verifying that build query provider with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery provider with null param_ should return match all | In scope: BuildQuery behavior, provider scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Provider_ShouldEmitFilterMetrics | Verifying that filter provider emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter provider emit filter metrics | In scope: Filter behavior, provider scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## SpecialtyFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Specialty_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter specialty with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter specialty with multiple values_ should filter correctly | In scope: Filter behavior, specialty scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Specialty_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter specialty with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter specialty with edge case values_ should handle gracefully | In scope: Filter behavior, specialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Specialty_ShouldReturnCorrectEsQuery | Verifying that build query specialty returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery specialty returns correct es query | In scope: BuildQuery behavior, specialty scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Specialty_WithNullParam_ShouldReturnMatchAll | Verifying that build query specialty with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery specialty with null param_ should return match all | In scope: BuildQuery behavior, specialty scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Specialty_ShouldEmitFilterMetrics | Verifying that filter specialty emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter specialty emit filter metrics | In scope: Filter behavior, specialty scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## StateFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_State_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter state with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter state with multiple values_ should filter correctly | In scope: Filter behavior, state scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_State_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter state with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter state with edge case values_ should handle gracefully | In scope: Filter behavior, state scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_State_ShouldReturnCorrectEsQuery | Verifying that build query state returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery state returns correct es query | In scope: BuildQuery behavior, state scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_State_WithNullParam_ShouldReturnMatchAll | Verifying that build query state with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery state with null param_ should return match all | In scope: BuildQuery behavior, state scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_State_ShouldEmitFilterMetrics | Verifying that filter state emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter state emit filter metrics | In scope: Filter behavior, state scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## SubspecialtyFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Subspecialty_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter subspecialty with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter subspecialty with multiple values_ should filter correctly | In scope: Filter behavior, subspecialty scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Subspecialty_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter subspecialty with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter subspecialty with edge case values_ should handle gracefully | In scope: Filter behavior, subspecialty scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Subspecialty_ShouldReturnCorrectEsQuery | Verifying that build query subspecialty returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery subspecialty returns correct es query | In scope: BuildQuery behavior, subspecialty scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Subspecialty_WithNullParam_ShouldReturnMatchAll | Verifying that build query subspecialty with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery subspecialty with null param_ should return match all | In scope: BuildQuery behavior, subspecialty scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Subspecialty_ShouldEmitFilterMetrics | Verifying that filter subspecialty emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter subspecialty emit filter metrics | In scope: Filter behavior, subspecialty scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## TelehealthFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Telehealth_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter telehealth with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter telehealth with multiple values_ should filter correctly | In scope: Filter behavior, telehealth scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Telehealth_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter telehealth with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter telehealth with edge case values_ should handle gracefully | In scope: Filter behavior, telehealth scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Telehealth_ShouldReturnCorrectEsQuery | Verifying that build query telehealth returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery telehealth returns correct es query | In scope: BuildQuery behavior, telehealth scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Telehealth_WithNullParam_ShouldReturnMatchAll | Verifying that build query telehealth with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery telehealth with null param_ should return match all | In scope: BuildQuery behavior, telehealth scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Telehealth_ShouldEmitFilterMetrics | Verifying that filter telehealth emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter telehealth emit filter metrics | In scope: Filter behavior, telehealth scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## TimeFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_Time_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter time with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter time with multiple values_ should filter correctly | In scope: Filter behavior, time scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_Time_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter time with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter time with edge case values_ should handle gracefully | In scope: Filter behavior, time scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_Time_ShouldReturnCorrectEsQuery | Verifying that build query time returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery time returns correct es query | In scope: BuildQuery behavior, time scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_Time_WithNullParam_ShouldReturnMatchAll | Verifying that build query time with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery time with null param_ should return match all | In scope: BuildQuery behavior, time scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_Time_ShouldEmitFilterMetrics | Verifying that filter time emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter time emit filter metrics | In scope: Filter behavior, time scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## VirtualCareFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_VirtualCare_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter virtual care with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter virtual care with multiple values_ should filter correctly | In scope: Filter behavior, virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_VirtualCare_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter virtual care with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter virtual care with edge case values_ should handle gracefully | In scope: Filter behavior, virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_VirtualCare_ShouldReturnCorrectEsQuery | Verifying that build query virtual care returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery virtual care returns correct es query | In scope: BuildQuery behavior, virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_VirtualCare_WithNullParam_ShouldReturnMatchAll | Verifying that build query virtual care with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery virtual care with null param_ should return match all | In scope: BuildQuery behavior, virtual care scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_VirtualCare_ShouldEmitFilterMetrics | Verifying that filter virtual care emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter virtual care emit filter metrics | In scope: Filter behavior, virtual care scenario. Out of scope: other scenarios and methods not under test. |


# Search/Es/Filtering

## ZipCodeFiltererAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_ZipCode_WithMultipleValues_ShouldFilterCorrectly | Verifying that filter zip code with multiple values_ should filter correctly | Setup test data and mocks -> Call Filter -> Assert with multiple values_ filter correctly | Filter zip code with multiple values_ should filter correctly | In scope: Filter behavior, zip code scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Filter_ZipCode_WithEdgeCaseValues_ShouldHandleGracefully | Verifying that filter zip code with edge case values_ should handle gracefully | Setup test data and mocks -> Call Filter -> Assert with edge case values_ handle gracefully | Filter zip code with edge case values_ should handle gracefully | In scope: Filter behavior, zip code scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | BuildQuery_ZipCode_ShouldReturnCorrectEsQuery | Verifying that build query zip code returns correct es query | Setup test data and mocks -> Call BuildQuery -> Assert return correct es query | BuildQuery zip code returns correct es query | In scope: BuildQuery behavior, zip code scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | BuildQuery_ZipCode_WithNullParam_ShouldReturnMatchAll | Verifying that build query zip code with null param_ should return match all | Setup test data and mocks -> Call BuildQuery -> Assert with null param_ return match all | BuildQuery zip code with null param_ should return match all | In scope: BuildQuery behavior, zip code scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Filter_ZipCode_ShouldEmitFilterMetrics | Verifying that filter zip code emit filter metrics | Setup test data and mocks -> Call Filter -> Assert emit filter metrics | Filter zip code emit filter metrics | In scope: Filter behavior, zip code scenario. Out of scope: other scenarios and methods not under test. |


# Search/Ranking

## BestSentenceEnricherAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithAdvancedSentenceProcessing_Case1 | Verifying that enrich with advanced sentence processing case1 | Setup with advanced sentence processing -> Call Enrich -> Assert case1 | Enrich with advanced sentence processing case1 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithAdvancedSentenceProcessing_Case2 | Verifying that enrich with advanced sentence processing case2 | Setup with advanced sentence processing -> Call Enrich -> Assert case2 | Enrich with advanced sentence processing case2 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithAdvancedSentenceProcessing_Case3 | Verifying that enrich with advanced sentence processing case3 | Setup with advanced sentence processing -> Call Enrich -> Assert case3 | Enrich with advanced sentence processing case3 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithAdvancedSentenceProcessing_Case4 | Verifying that enrich with advanced sentence processing case4 | Setup with advanced sentence processing -> Call Enrich -> Assert case4 | Enrich with advanced sentence processing case4 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithAdvancedSentenceProcessing_Case5 | Verifying that enrich with advanced sentence processing case5 | Setup with advanced sentence processing -> Call Enrich -> Assert case5 | Enrich with advanced sentence processing case5 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithAdvancedSentenceProcessing_Case6 | Verifying that enrich with advanced sentence processing case6 | Setup with advanced sentence processing -> Call Enrich -> Assert case6 | Enrich with advanced sentence processing case6 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Enrich_WithAdvancedSentenceProcessing_Case7 | Verifying that enrich with advanced sentence processing case7 | Setup with advanced sentence processing -> Call Enrich -> Assert case7 | Enrich with advanced sentence processing case7 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Enrich_WithAdvancedSentenceProcessing_Case8 | Verifying that enrich with advanced sentence processing case8 | Setup with advanced sentence processing -> Call Enrich -> Assert case8 | Enrich with advanced sentence processing case8 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Enrich_WithAdvancedSentenceProcessing_Case9 | Verifying that enrich with advanced sentence processing case9 | Setup with advanced sentence processing -> Call Enrich -> Assert case9 | Enrich with advanced sentence processing case9 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Enrich_WithAdvancedSentenceProcessing_Case10 | Verifying that enrich with advanced sentence processing case10 | Setup with advanced sentence processing -> Call Enrich -> Assert case10 | Enrich with advanced sentence processing case10 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Enrich_WithAdvancedSentenceProcessing_Case11 | Verifying that enrich with advanced sentence processing case11 | Setup with advanced sentence processing -> Call Enrich -> Assert case11 | Enrich with advanced sentence processing case11 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Enrich_WithAdvancedSentenceProcessing_Case12 | Verifying that enrich with advanced sentence processing case12 | Setup with advanced sentence processing -> Call Enrich -> Assert case12 | Enrich with advanced sentence processing case12 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Enrich_WithAdvancedSentenceProcessing_Case13 | Verifying that enrich with advanced sentence processing case13 | Setup with advanced sentence processing -> Call Enrich -> Assert case13 | Enrich with advanced sentence processing case13 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Enrich_WithAdvancedSentenceProcessing_Case14 | Verifying that enrich with advanced sentence processing case14 | Setup with advanced sentence processing -> Call Enrich -> Assert case14 | Enrich with advanced sentence processing case14 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Enrich_WithAdvancedSentenceProcessing_Case15 | Verifying that enrich with advanced sentence processing case15 | Setup with advanced sentence processing -> Call Enrich -> Assert case15 | Enrich with advanced sentence processing case15 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Enrich_WithAdvancedSentenceProcessing_Case16 | Verifying that enrich with advanced sentence processing case16 | Setup with advanced sentence processing -> Call Enrich -> Assert case16 | Enrich with advanced sentence processing case16 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Enrich_WithAdvancedSentenceProcessing_Case17 | Verifying that enrich with advanced sentence processing case17 | Setup with advanced sentence processing -> Call Enrich -> Assert case17 | Enrich with advanced sentence processing case17 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Enrich_WithAdvancedSentenceProcessing_Case18 | Verifying that enrich with advanced sentence processing case18 | Setup with advanced sentence processing -> Call Enrich -> Assert case18 | Enrich with advanced sentence processing case18 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Enrich_WithAdvancedSentenceProcessing_Case19 | Verifying that enrich with advanced sentence processing case19 | Setup with advanced sentence processing -> Call Enrich -> Assert case19 | Enrich with advanced sentence processing case19 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Enrich_WithAdvancedSentenceProcessing_Case20 | Verifying that enrich with advanced sentence processing case20 | Setup with advanced sentence processing -> Call Enrich -> Assert case20 | Enrich with advanced sentence processing case20 | In scope: Enrich behavior, with advanced sentence processing scenario. Out of scope: other scenarios and methods not under test. |


# Search/Ranking

## CrossEncoderRankerAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithAdvancedCrossEncoder_Case1 | Verifying that rank with advanced cross encoder case1 | Setup with advanced cross encoder -> Call Rank -> Assert case1 | Rank with advanced cross encoder case1 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithAdvancedCrossEncoder_Case2 | Verifying that rank with advanced cross encoder case2 | Setup with advanced cross encoder -> Call Rank -> Assert case2 | Rank with advanced cross encoder case2 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithAdvancedCrossEncoder_Case3 | Verifying that rank with advanced cross encoder case3 | Setup with advanced cross encoder -> Call Rank -> Assert case3 | Rank with advanced cross encoder case3 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithAdvancedCrossEncoder_Case4 | Verifying that rank with advanced cross encoder case4 | Setup with advanced cross encoder -> Call Rank -> Assert case4 | Rank with advanced cross encoder case4 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithAdvancedCrossEncoder_Case5 | Verifying that rank with advanced cross encoder case5 | Setup with advanced cross encoder -> Call Rank -> Assert case5 | Rank with advanced cross encoder case5 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithAdvancedCrossEncoder_Case6 | Verifying that rank with advanced cross encoder case6 | Setup with advanced cross encoder -> Call Rank -> Assert case6 | Rank with advanced cross encoder case6 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithAdvancedCrossEncoder_Case7 | Verifying that rank with advanced cross encoder case7 | Setup with advanced cross encoder -> Call Rank -> Assert case7 | Rank with advanced cross encoder case7 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithAdvancedCrossEncoder_Case8 | Verifying that rank with advanced cross encoder case8 | Setup with advanced cross encoder -> Call Rank -> Assert case8 | Rank with advanced cross encoder case8 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithAdvancedCrossEncoder_Case9 | Verifying that rank with advanced cross encoder case9 | Setup with advanced cross encoder -> Call Rank -> Assert case9 | Rank with advanced cross encoder case9 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithAdvancedCrossEncoder_Case10 | Verifying that rank with advanced cross encoder case10 | Setup with advanced cross encoder -> Call Rank -> Assert case10 | Rank with advanced cross encoder case10 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Rank_WithAdvancedCrossEncoder_Case11 | Verifying that rank with advanced cross encoder case11 | Setup with advanced cross encoder -> Call Rank -> Assert case11 | Rank with advanced cross encoder case11 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Rank_WithAdvancedCrossEncoder_Case12 | Verifying that rank with advanced cross encoder case12 | Setup with advanced cross encoder -> Call Rank -> Assert case12 | Rank with advanced cross encoder case12 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Rank_WithAdvancedCrossEncoder_Case13 | Verifying that rank with advanced cross encoder case13 | Setup with advanced cross encoder -> Call Rank -> Assert case13 | Rank with advanced cross encoder case13 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Rank_WithAdvancedCrossEncoder_Case14 | Verifying that rank with advanced cross encoder case14 | Setup with advanced cross encoder -> Call Rank -> Assert case14 | Rank with advanced cross encoder case14 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Rank_WithAdvancedCrossEncoder_Case15 | Verifying that rank with advanced cross encoder case15 | Setup with advanced cross encoder -> Call Rank -> Assert case15 | Rank with advanced cross encoder case15 | In scope: Rank behavior, with advanced cross encoder scenario. Out of scope: other scenarios and methods not under test. |


# Search/Ranking

## KeywordEnricherAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Enrich_WithAdvancedKeywordProcessing_Case1 | Verifying that enrich with advanced keyword processing case1 | Setup with advanced keyword processing -> Call Enrich -> Assert case1 | Enrich with advanced keyword processing case1 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Enrich_WithAdvancedKeywordProcessing_Case2 | Verifying that enrich with advanced keyword processing case2 | Setup with advanced keyword processing -> Call Enrich -> Assert case2 | Enrich with advanced keyword processing case2 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Enrich_WithAdvancedKeywordProcessing_Case3 | Verifying that enrich with advanced keyword processing case3 | Setup with advanced keyword processing -> Call Enrich -> Assert case3 | Enrich with advanced keyword processing case3 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Enrich_WithAdvancedKeywordProcessing_Case4 | Verifying that enrich with advanced keyword processing case4 | Setup with advanced keyword processing -> Call Enrich -> Assert case4 | Enrich with advanced keyword processing case4 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Enrich_WithAdvancedKeywordProcessing_Case5 | Verifying that enrich with advanced keyword processing case5 | Setup with advanced keyword processing -> Call Enrich -> Assert case5 | Enrich with advanced keyword processing case5 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Enrich_WithAdvancedKeywordProcessing_Case6 | Verifying that enrich with advanced keyword processing case6 | Setup with advanced keyword processing -> Call Enrich -> Assert case6 | Enrich with advanced keyword processing case6 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Enrich_WithAdvancedKeywordProcessing_Case7 | Verifying that enrich with advanced keyword processing case7 | Setup with advanced keyword processing -> Call Enrich -> Assert case7 | Enrich with advanced keyword processing case7 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Enrich_WithAdvancedKeywordProcessing_Case8 | Verifying that enrich with advanced keyword processing case8 | Setup with advanced keyword processing -> Call Enrich -> Assert case8 | Enrich with advanced keyword processing case8 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Enrich_WithAdvancedKeywordProcessing_Case9 | Verifying that enrich with advanced keyword processing case9 | Setup with advanced keyword processing -> Call Enrich -> Assert case9 | Enrich with advanced keyword processing case9 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Enrich_WithAdvancedKeywordProcessing_Case10 | Verifying that enrich with advanced keyword processing case10 | Setup with advanced keyword processing -> Call Enrich -> Assert case10 | Enrich with advanced keyword processing case10 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Enrich_WithAdvancedKeywordProcessing_Case11 | Verifying that enrich with advanced keyword processing case11 | Setup with advanced keyword processing -> Call Enrich -> Assert case11 | Enrich with advanced keyword processing case11 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Enrich_WithAdvancedKeywordProcessing_Case12 | Verifying that enrich with advanced keyword processing case12 | Setup with advanced keyword processing -> Call Enrich -> Assert case12 | Enrich with advanced keyword processing case12 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Enrich_WithAdvancedKeywordProcessing_Case13 | Verifying that enrich with advanced keyword processing case13 | Setup with advanced keyword processing -> Call Enrich -> Assert case13 | Enrich with advanced keyword processing case13 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Enrich_WithAdvancedKeywordProcessing_Case14 | Verifying that enrich with advanced keyword processing case14 | Setup with advanced keyword processing -> Call Enrich -> Assert case14 | Enrich with advanced keyword processing case14 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Enrich_WithAdvancedKeywordProcessing_Case15 | Verifying that enrich with advanced keyword processing case15 | Setup with advanced keyword processing -> Call Enrich -> Assert case15 | Enrich with advanced keyword processing case15 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | Enrich_WithAdvancedKeywordProcessing_Case16 | Verifying that enrich with advanced keyword processing case16 | Setup with advanced keyword processing -> Call Enrich -> Assert case16 | Enrich with advanced keyword processing case16 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | Enrich_WithAdvancedKeywordProcessing_Case17 | Verifying that enrich with advanced keyword processing case17 | Setup with advanced keyword processing -> Call Enrich -> Assert case17 | Enrich with advanced keyword processing case17 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | Enrich_WithAdvancedKeywordProcessing_Case18 | Verifying that enrich with advanced keyword processing case18 | Setup with advanced keyword processing -> Call Enrich -> Assert case18 | Enrich with advanced keyword processing case18 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | Enrich_WithAdvancedKeywordProcessing_Case19 | Verifying that enrich with advanced keyword processing case19 | Setup with advanced keyword processing -> Call Enrich -> Assert case19 | Enrich with advanced keyword processing case19 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | Enrich_WithAdvancedKeywordProcessing_Case20 | Verifying that enrich with advanced keyword processing case20 | Setup with advanced keyword processing -> Call Enrich -> Assert case20 | Enrich with advanced keyword processing case20 | In scope: Enrich behavior, with advanced keyword processing scenario. Out of scope: other scenarios and methods not under test. |


# Search/Yass

## SearchParamsAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SearchParams_WithAdvancedScenario_Case1 | Verifying that search params with advanced scenario case1 | Setup with advanced scenario -> Call SearchParams -> Assert case1 | SearchParams with advanced scenario case1 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | SearchParams_WithAdvancedScenario_Case2 | Verifying that search params with advanced scenario case2 | Setup with advanced scenario -> Call SearchParams -> Assert case2 | SearchParams with advanced scenario case2 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | SearchParams_WithAdvancedScenario_Case3 | Verifying that search params with advanced scenario case3 | Setup with advanced scenario -> Call SearchParams -> Assert case3 | SearchParams with advanced scenario case3 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | SearchParams_WithAdvancedScenario_Case4 | Verifying that search params with advanced scenario case4 | Setup with advanced scenario -> Call SearchParams -> Assert case4 | SearchParams with advanced scenario case4 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | SearchParams_WithAdvancedScenario_Case5 | Verifying that search params with advanced scenario case5 | Setup with advanced scenario -> Call SearchParams -> Assert case5 | SearchParams with advanced scenario case5 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | SearchParams_WithAdvancedScenario_Case6 | Verifying that search params with advanced scenario case6 | Setup with advanced scenario -> Call SearchParams -> Assert case6 | SearchParams with advanced scenario case6 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | SearchParams_WithAdvancedScenario_Case7 | Verifying that search params with advanced scenario case7 | Setup with advanced scenario -> Call SearchParams -> Assert case7 | SearchParams with advanced scenario case7 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | SearchParams_WithAdvancedScenario_Case8 | Verifying that search params with advanced scenario case8 | Setup with advanced scenario -> Call SearchParams -> Assert case8 | SearchParams with advanced scenario case8 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | SearchParams_WithAdvancedScenario_Case9 | Verifying that search params with advanced scenario case9 | Setup with advanced scenario -> Call SearchParams -> Assert case9 | SearchParams with advanced scenario case9 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | SearchParams_WithAdvancedScenario_Case10 | Verifying that search params with advanced scenario case10 | Setup with advanced scenario -> Call SearchParams -> Assert case10 | SearchParams with advanced scenario case10 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | SearchParams_WithAdvancedScenario_Case11 | Verifying that search params with advanced scenario case11 | Setup with advanced scenario -> Call SearchParams -> Assert case11 | SearchParams with advanced scenario case11 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | SearchParams_WithAdvancedScenario_Case12 | Verifying that search params with advanced scenario case12 | Setup with advanced scenario -> Call SearchParams -> Assert case12 | SearchParams with advanced scenario case12 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | SearchParams_WithAdvancedScenario_Case13 | Verifying that search params with advanced scenario case13 | Setup with advanced scenario -> Call SearchParams -> Assert case13 | SearchParams with advanced scenario case13 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | SearchParams_WithAdvancedScenario_Case14 | Verifying that search params with advanced scenario case14 | Setup with advanced scenario -> Call SearchParams -> Assert case14 | SearchParams with advanced scenario case14 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | SearchParams_WithAdvancedScenario_Case15 | Verifying that search params with advanced scenario case15 | Setup with advanced scenario -> Call SearchParams -> Assert case15 | SearchParams with advanced scenario case15 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 16 | | SearchParams_WithAdvancedScenario_Case16 | Verifying that search params with advanced scenario case16 | Setup with advanced scenario -> Call SearchParams -> Assert case16 | SearchParams with advanced scenario case16 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 17 | | SearchParams_WithAdvancedScenario_Case17 | Verifying that search params with advanced scenario case17 | Setup with advanced scenario -> Call SearchParams -> Assert case17 | SearchParams with advanced scenario case17 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 18 | | SearchParams_WithAdvancedScenario_Case18 | Verifying that search params with advanced scenario case18 | Setup with advanced scenario -> Call SearchParams -> Assert case18 | SearchParams with advanced scenario case18 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 19 | | SearchParams_WithAdvancedScenario_Case19 | Verifying that search params with advanced scenario case19 | Setup with advanced scenario -> Call SearchParams -> Assert case19 | SearchParams with advanced scenario case19 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 20 | | SearchParams_WithAdvancedScenario_Case20 | Verifying that search params with advanced scenario case20 | Setup with advanced scenario -> Call SearchParams -> Assert case20 | SearchParams with advanced scenario case20 | In scope: SearchParams behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Algorithm/Container

## ContainerConfigurationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Configure_WithContainerConfig_Case1 | Verifying that configure with container config case1 | Setup with container config -> Call Configure -> Assert case1 | Configure with container config case1 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Configure_WithContainerConfig_Case2 | Verifying that configure with container config case2 | Setup with container config -> Call Configure -> Assert case2 | Configure with container config case2 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Configure_WithContainerConfig_Case3 | Verifying that configure with container config case3 | Setup with container config -> Call Configure -> Assert case3 | Configure with container config case3 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Configure_WithContainerConfig_Case4 | Verifying that configure with container config case4 | Setup with container config -> Call Configure -> Assert case4 | Configure with container config case4 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Configure_WithContainerConfig_Case5 | Verifying that configure with container config case5 | Setup with container config -> Call Configure -> Assert case5 | Configure with container config case5 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Configure_WithContainerConfig_Case6 | Verifying that configure with container config case6 | Setup with container config -> Call Configure -> Assert case6 | Configure with container config case6 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Configure_WithContainerConfig_Case7 | Verifying that configure with container config case7 | Setup with container config -> Call Configure -> Assert case7 | Configure with container config case7 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Configure_WithContainerConfig_Case8 | Verifying that configure with container config case8 | Setup with container config -> Call Configure -> Assert case8 | Configure with container config case8 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Configure_WithContainerConfig_Case9 | Verifying that configure with container config case9 | Setup with container config -> Call Configure -> Assert case9 | Configure with container config case9 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Configure_WithContainerConfig_Case10 | Verifying that configure with container config case10 | Setup with container config -> Call Configure -> Assert case10 | Configure with container config case10 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Configure_WithContainerConfig_Case11 | Verifying that configure with container config case11 | Setup with container config -> Call Configure -> Assert case11 | Configure with container config case11 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Configure_WithContainerConfig_Case12 | Verifying that configure with container config case12 | Setup with container config -> Call Configure -> Assert case12 | Configure with container config case12 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Configure_WithContainerConfig_Case13 | Verifying that configure with container config case13 | Setup with container config -> Call Configure -> Assert case13 | Configure with container config case13 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Configure_WithContainerConfig_Case14 | Verifying that configure with container config case14 | Setup with container config -> Call Configure -> Assert case14 | Configure with container config case14 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Configure_WithContainerConfig_Case15 | Verifying that configure with container config case15 | Setup with container config -> Call Configure -> Assert case15 | Configure with container config case15 | In scope: Configure behavior, with container config scenario. Out of scope: other scenarios and methods not under test. |


# Search/Availability

## AvailabilityClientAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailability_WithAdvancedScenario_Case1 | Verifying that get availability with advanced scenario case1 | Setup with advanced scenario -> Call GetAvailability -> Assert case1 | GetAvailability with advanced scenario case1 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_WithAdvancedScenario_Case2 | Verifying that get availability with advanced scenario case2 | Setup with advanced scenario -> Call GetAvailability -> Assert case2 | GetAvailability with advanced scenario case2 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAvailability_WithAdvancedScenario_Case3 | Verifying that get availability with advanced scenario case3 | Setup with advanced scenario -> Call GetAvailability -> Assert case3 | GetAvailability with advanced scenario case3 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAvailability_WithAdvancedScenario_Case4 | Verifying that get availability with advanced scenario case4 | Setup with advanced scenario -> Call GetAvailability -> Assert case4 | GetAvailability with advanced scenario case4 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAvailability_WithAdvancedScenario_Case5 | Verifying that get availability with advanced scenario case5 | Setup with advanced scenario -> Call GetAvailability -> Assert case5 | GetAvailability with advanced scenario case5 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAvailability_WithAdvancedScenario_Case6 | Verifying that get availability with advanced scenario case6 | Setup with advanced scenario -> Call GetAvailability -> Assert case6 | GetAvailability with advanced scenario case6 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAvailability_WithAdvancedScenario_Case7 | Verifying that get availability with advanced scenario case7 | Setup with advanced scenario -> Call GetAvailability -> Assert case7 | GetAvailability with advanced scenario case7 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAvailability_WithAdvancedScenario_Case8 | Verifying that get availability with advanced scenario case8 | Setup with advanced scenario -> Call GetAvailability -> Assert case8 | GetAvailability with advanced scenario case8 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAvailability_WithAdvancedScenario_Case9 | Verifying that get availability with advanced scenario case9 | Setup with advanced scenario -> Call GetAvailability -> Assert case9 | GetAvailability with advanced scenario case9 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAvailability_WithAdvancedScenario_Case10 | Verifying that get availability with advanced scenario case10 | Setup with advanced scenario -> Call GetAvailability -> Assert case10 | GetAvailability with advanced scenario case10 | In scope: GetAvailability behavior, with advanced scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Availability

## ProviderLocationAvailabilityServiceAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailability_WithServiceScenario_Case1 | Verifying that get availability with service scenario case1 | Setup with service scenario -> Call GetAvailability -> Assert case1 | GetAvailability with service scenario case1 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_WithServiceScenario_Case2 | Verifying that get availability with service scenario case2 | Setup with service scenario -> Call GetAvailability -> Assert case2 | GetAvailability with service scenario case2 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAvailability_WithServiceScenario_Case3 | Verifying that get availability with service scenario case3 | Setup with service scenario -> Call GetAvailability -> Assert case3 | GetAvailability with service scenario case3 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAvailability_WithServiceScenario_Case4 | Verifying that get availability with service scenario case4 | Setup with service scenario -> Call GetAvailability -> Assert case4 | GetAvailability with service scenario case4 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAvailability_WithServiceScenario_Case5 | Verifying that get availability with service scenario case5 | Setup with service scenario -> Call GetAvailability -> Assert case5 | GetAvailability with service scenario case5 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAvailability_WithServiceScenario_Case6 | Verifying that get availability with service scenario case6 | Setup with service scenario -> Call GetAvailability -> Assert case6 | GetAvailability with service scenario case6 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAvailability_WithServiceScenario_Case7 | Verifying that get availability with service scenario case7 | Setup with service scenario -> Call GetAvailability -> Assert case7 | GetAvailability with service scenario case7 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAvailability_WithServiceScenario_Case8 | Verifying that get availability with service scenario case8 | Setup with service scenario -> Call GetAvailability -> Assert case8 | GetAvailability with service scenario case8 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAvailability_WithServiceScenario_Case9 | Verifying that get availability with service scenario case9 | Setup with service scenario -> Call GetAvailability -> Assert case9 | GetAvailability with service scenario case9 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAvailability_WithServiceScenario_Case10 | Verifying that get availability with service scenario case10 | Setup with service scenario -> Call GetAvailability -> Assert case10 | GetAvailability with service scenario case10 | In scope: GetAvailability behavior, with service scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Ranking/TheBox

## BoxRankerIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithBoxRanker_Case1 | Verifying that rank with box ranker case1 | Setup with box ranker -> Call Rank -> Assert case1 | Rank with box ranker case1 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithBoxRanker_Case2 | Verifying that rank with box ranker case2 | Setup with box ranker -> Call Rank -> Assert case2 | Rank with box ranker case2 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithBoxRanker_Case3 | Verifying that rank with box ranker case3 | Setup with box ranker -> Call Rank -> Assert case3 | Rank with box ranker case3 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithBoxRanker_Case4 | Verifying that rank with box ranker case4 | Setup with box ranker -> Call Rank -> Assert case4 | Rank with box ranker case4 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithBoxRanker_Case5 | Verifying that rank with box ranker case5 | Setup with box ranker -> Call Rank -> Assert case5 | Rank with box ranker case5 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithBoxRanker_Case6 | Verifying that rank with box ranker case6 | Setup with box ranker -> Call Rank -> Assert case6 | Rank with box ranker case6 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithBoxRanker_Case7 | Verifying that rank with box ranker case7 | Setup with box ranker -> Call Rank -> Assert case7 | Rank with box ranker case7 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithBoxRanker_Case8 | Verifying that rank with box ranker case8 | Setup with box ranker -> Call Rank -> Assert case8 | Rank with box ranker case8 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithBoxRanker_Case9 | Verifying that rank with box ranker case9 | Setup with box ranker -> Call Rank -> Assert case9 | Rank with box ranker case9 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithBoxRanker_Case10 | Verifying that rank with box ranker case10 | Setup with box ranker -> Call Rank -> Assert case10 | Rank with box ranker case10 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Rank_WithBoxRanker_Case11 | Verifying that rank with box ranker case11 | Setup with box ranker -> Call Rank -> Assert case11 | Rank with box ranker case11 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Rank_WithBoxRanker_Case12 | Verifying that rank with box ranker case12 | Setup with box ranker -> Call Rank -> Assert case12 | Rank with box ranker case12 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Rank_WithBoxRanker_Case13 | Verifying that rank with box ranker case13 | Setup with box ranker -> Call Rank -> Assert case13 | Rank with box ranker case13 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Rank_WithBoxRanker_Case14 | Verifying that rank with box ranker case14 | Setup with box ranker -> Call Rank -> Assert case14 | Rank with box ranker case14 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Rank_WithBoxRanker_Case15 | Verifying that rank with box ranker case15 | Setup with box ranker -> Call Rank -> Assert case15 | Rank with box ranker case15 | In scope: Rank behavior, with box ranker scenario. Out of scope: other scenarios and methods not under test. |


# Search/Spo

## SpogorithmRankerAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rank_WithAdvancedSpogorithm_Case1 | Verifying that rank with advanced spogorithm case1 | Setup with advanced spogorithm -> Call Rank -> Assert case1 | Rank with advanced spogorithm case1 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rank_WithAdvancedSpogorithm_Case2 | Verifying that rank with advanced spogorithm case2 | Setup with advanced spogorithm -> Call Rank -> Assert case2 | Rank with advanced spogorithm case2 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rank_WithAdvancedSpogorithm_Case3 | Verifying that rank with advanced spogorithm case3 | Setup with advanced spogorithm -> Call Rank -> Assert case3 | Rank with advanced spogorithm case3 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rank_WithAdvancedSpogorithm_Case4 | Verifying that rank with advanced spogorithm case4 | Setup with advanced spogorithm -> Call Rank -> Assert case4 | Rank with advanced spogorithm case4 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rank_WithAdvancedSpogorithm_Case5 | Verifying that rank with advanced spogorithm case5 | Setup with advanced spogorithm -> Call Rank -> Assert case5 | Rank with advanced spogorithm case5 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rank_WithAdvancedSpogorithm_Case6 | Verifying that rank with advanced spogorithm case6 | Setup with advanced spogorithm -> Call Rank -> Assert case6 | Rank with advanced spogorithm case6 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rank_WithAdvancedSpogorithm_Case7 | Verifying that rank with advanced spogorithm case7 | Setup with advanced spogorithm -> Call Rank -> Assert case7 | Rank with advanced spogorithm case7 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rank_WithAdvancedSpogorithm_Case8 | Verifying that rank with advanced spogorithm case8 | Setup with advanced spogorithm -> Call Rank -> Assert case8 | Rank with advanced spogorithm case8 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rank_WithAdvancedSpogorithm_Case9 | Verifying that rank with advanced spogorithm case9 | Setup with advanced spogorithm -> Call Rank -> Assert case9 | Rank with advanced spogorithm case9 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rank_WithAdvancedSpogorithm_Case10 | Verifying that rank with advanced spogorithm case10 | Setup with advanced spogorithm -> Call Rank -> Assert case10 | Rank with advanced spogorithm case10 | In scope: Rank behavior, with advanced spogorithm scenario. Out of scope: other scenarios and methods not under test. |


# Search/Statsd

## SearchMetricTagsAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetTag_WithAdvancedMetricTag_Case1 | Verifying that get tag with advanced metric tag case1 | Setup with advanced metric tag -> Call GetTag -> Assert case1 | GetTag with advanced metric tag case1 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetTag_WithAdvancedMetricTag_Case2 | Verifying that get tag with advanced metric tag case2 | Setup with advanced metric tag -> Call GetTag -> Assert case2 | GetTag with advanced metric tag case2 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetTag_WithAdvancedMetricTag_Case3 | Verifying that get tag with advanced metric tag case3 | Setup with advanced metric tag -> Call GetTag -> Assert case3 | GetTag with advanced metric tag case3 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetTag_WithAdvancedMetricTag_Case4 | Verifying that get tag with advanced metric tag case4 | Setup with advanced metric tag -> Call GetTag -> Assert case4 | GetTag with advanced metric tag case4 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetTag_WithAdvancedMetricTag_Case5 | Verifying that get tag with advanced metric tag case5 | Setup with advanced metric tag -> Call GetTag -> Assert case5 | GetTag with advanced metric tag case5 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetTag_WithAdvancedMetricTag_Case6 | Verifying that get tag with advanced metric tag case6 | Setup with advanced metric tag -> Call GetTag -> Assert case6 | GetTag with advanced metric tag case6 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetTag_WithAdvancedMetricTag_Case7 | Verifying that get tag with advanced metric tag case7 | Setup with advanced metric tag -> Call GetTag -> Assert case7 | GetTag with advanced metric tag case7 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetTag_WithAdvancedMetricTag_Case8 | Verifying that get tag with advanced metric tag case8 | Setup with advanced metric tag -> Call GetTag -> Assert case8 | GetTag with advanced metric tag case8 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetTag_WithAdvancedMetricTag_Case9 | Verifying that get tag with advanced metric tag case9 | Setup with advanced metric tag -> Call GetTag -> Assert case9 | GetTag with advanced metric tag case9 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetTag_WithAdvancedMetricTag_Case10 | Verifying that get tag with advanced metric tag case10 | Setup with advanced metric tag -> Call GetTag -> Assert case10 | GetTag with advanced metric tag case10 | In scope: GetTag behavior, with advanced metric tag scenario. Out of scope: other scenarios and methods not under test. |

# Search/Algorithm/Base

## AvailabilityRetrieverAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetAvailability_WithAdditionalScenario_Case1 | Verifying that get availability with additional scenario case1 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case1 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetAvailability_WithAdditionalScenario_Case2 | Verifying that get availability with additional scenario case2 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case2 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetAvailability_WithAdditionalScenario_Case3 | Verifying that get availability with additional scenario case3 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case3 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetAvailability_WithAdditionalScenario_Case4 | Verifying that get availability with additional scenario case4 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case4 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetAvailability_WithAdditionalScenario_Case5 | Verifying that get availability with additional scenario case5 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case5 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetAvailability_WithAdditionalScenario_Case6 | Verifying that get availability with additional scenario case6 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case6 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetAvailability_WithAdditionalScenario_Case7 | Verifying that get availability with additional scenario case7 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case7 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetAvailability_WithAdditionalScenario_Case8 | Verifying that get availability with additional scenario case8 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case8 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetAvailability_WithAdditionalScenario_Case9 | Verifying that get availability with additional scenario case9 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case9 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetAvailability_WithAdditionalScenario_Case10 | Verifying that get availability with additional scenario case10 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case10 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetAvailability_WithAdditionalScenario_Case11 | Verifying that get availability with additional scenario case11 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case11 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetAvailability_WithAdditionalScenario_Case12 | Verifying that get availability with additional scenario case12 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case12 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetAvailability_WithAdditionalScenario_Case13 | Verifying that get availability with additional scenario case13 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case13 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetAvailability_WithAdditionalScenario_Case14 | Verifying that get availability with additional scenario case14 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case14 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetAvailability_WithAdditionalScenario_Case15 | Verifying that get availability with additional scenario case15 | Setup with additional scenario -> Call GetAvailability -> Assert expected behavior | GetAvailability with additional scenario case15 | In scope: GetAvailability behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Yass

## ProvLocResultAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ProvLocResult_WithProperty_Case1 | Verifying that prov loc result with property case1 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case1 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ProvLocResult_WithProperty_Case2 | Verifying that prov loc result with property case2 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case2 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ProvLocResult_WithProperty_Case3 | Verifying that prov loc result with property case3 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case3 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ProvLocResult_WithProperty_Case4 | Verifying that prov loc result with property case4 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case4 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ProvLocResult_WithProperty_Case5 | Verifying that prov loc result with property case5 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case5 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ProvLocResult_WithProperty_Case6 | Verifying that prov loc result with property case6 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case6 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ProvLocResult_WithProperty_Case7 | Verifying that prov loc result with property case7 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case7 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ProvLocResult_WithProperty_Case8 | Verifying that prov loc result with property case8 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case8 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | ProvLocResult_WithProperty_Case9 | Verifying that prov loc result with property case9 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case9 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | ProvLocResult_WithProperty_Case10 | Verifying that prov loc result with property case10 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case10 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | ProvLocResult_WithProperty_Case11 | Verifying that prov loc result with property case11 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case11 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | ProvLocResult_WithProperty_Case12 | Verifying that prov loc result with property case12 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case12 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | ProvLocResult_WithProperty_Case13 | Verifying that prov loc result with property case13 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case13 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | ProvLocResult_WithProperty_Case14 | Verifying that prov loc result with property case14 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case14 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | ProvLocResult_WithProperty_Case15 | Verifying that prov loc result with property case15 | Setup with property -> Call ProvLocResult -> Assert expected behavior | ProvLocResult with property case15 | In scope: ProvLocResult behavior, with property scenario. Out of scope: other scenarios and methods not under test. |


# Search/Yass

## ResponseInfoAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ResponseInfo_WithScenario_Case1 | Verifying that response info with scenario case1 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case1 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ResponseInfo_WithScenario_Case2 | Verifying that response info with scenario case2 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case2 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ResponseInfo_WithScenario_Case3 | Verifying that response info with scenario case3 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case3 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ResponseInfo_WithScenario_Case4 | Verifying that response info with scenario case4 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case4 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ResponseInfo_WithScenario_Case5 | Verifying that response info with scenario case5 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case5 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ResponseInfo_WithScenario_Case6 | Verifying that response info with scenario case6 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case6 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ResponseInfo_WithScenario_Case7 | Verifying that response info with scenario case7 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case7 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ResponseInfo_WithScenario_Case8 | Verifying that response info with scenario case8 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case8 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | ResponseInfo_WithScenario_Case9 | Verifying that response info with scenario case9 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case9 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | ResponseInfo_WithScenario_Case10 | Verifying that response info with scenario case10 | Setup with scenario -> Call ResponseInfo -> Assert expected behavior | ResponseInfo with scenario case10 | In scope: ResponseInfo behavior, with scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/DynamoDb

## PracticeFeaturesRetrieverAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetFeatures_WithAdditionalScenario_Case1 | Verifying that get features with additional scenario case1 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case1 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetFeatures_WithAdditionalScenario_Case2 | Verifying that get features with additional scenario case2 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case2 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetFeatures_WithAdditionalScenario_Case3 | Verifying that get features with additional scenario case3 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case3 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetFeatures_WithAdditionalScenario_Case4 | Verifying that get features with additional scenario case4 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case4 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetFeatures_WithAdditionalScenario_Case5 | Verifying that get features with additional scenario case5 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case5 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetFeatures_WithAdditionalScenario_Case6 | Verifying that get features with additional scenario case6 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case6 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetFeatures_WithAdditionalScenario_Case7 | Verifying that get features with additional scenario case7 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case7 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetFeatures_WithAdditionalScenario_Case8 | Verifying that get features with additional scenario case8 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case8 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetFeatures_WithAdditionalScenario_Case9 | Verifying that get features with additional scenario case9 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case9 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetFeatures_WithAdditionalScenario_Case10 | Verifying that get features with additional scenario case10 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case10 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | GetFeatures_WithAdditionalScenario_Case11 | Verifying that get features with additional scenario case11 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case11 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | GetFeatures_WithAdditionalScenario_Case12 | Verifying that get features with additional scenario case12 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case12 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | GetFeatures_WithAdditionalScenario_Case13 | Verifying that get features with additional scenario case13 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case13 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | GetFeatures_WithAdditionalScenario_Case14 | Verifying that get features with additional scenario case14 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case14 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | GetFeatures_WithAdditionalScenario_Case15 | Verifying that get features with additional scenario case15 | Setup with additional scenario -> Call GetFeatures -> Assert expected behavior | GetFeatures with additional scenario case15 | In scope: GetFeatures behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/MarketIntelligence

## MarketIntelligenceServiceAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Execute_WithAdvancedQuery_Case1 | Verifying that execute with advanced query case1 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case1 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Execute_WithAdvancedQuery_Case2 | Verifying that execute with advanced query case2 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case2 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Execute_WithAdvancedQuery_Case3 | Verifying that execute with advanced query case3 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case3 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Execute_WithAdvancedQuery_Case4 | Verifying that execute with advanced query case4 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case4 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Execute_WithAdvancedQuery_Case5 | Verifying that execute with advanced query case5 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case5 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Execute_WithAdvancedQuery_Case6 | Verifying that execute with advanced query case6 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case6 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Execute_WithAdvancedQuery_Case7 | Verifying that execute with advanced query case7 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case7 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Execute_WithAdvancedQuery_Case8 | Verifying that execute with advanced query case8 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case8 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Execute_WithAdvancedQuery_Case9 | Verifying that execute with advanced query case9 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case9 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Execute_WithAdvancedQuery_Case10 | Verifying that execute with advanced query case10 | Setup with advanced query -> Call Execute -> Assert expected behavior | Execute with advanced query case10 | In scope: Execute behavior, with advanced query scenario. Out of scope: other scenarios and methods not under test. |


# Search/Grouping

## GroupingIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Group_WithIntegrationScenario_Case1 | Verifying that group with integration scenario case1 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case1 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Group_WithIntegrationScenario_Case2 | Verifying that group with integration scenario case2 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case2 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Group_WithIntegrationScenario_Case3 | Verifying that group with integration scenario case3 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case3 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Group_WithIntegrationScenario_Case4 | Verifying that group with integration scenario case4 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case4 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Group_WithIntegrationScenario_Case5 | Verifying that group with integration scenario case5 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case5 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Group_WithIntegrationScenario_Case6 | Verifying that group with integration scenario case6 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case6 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Group_WithIntegrationScenario_Case7 | Verifying that group with integration scenario case7 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case7 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Group_WithIntegrationScenario_Case8 | Verifying that group with integration scenario case8 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case8 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Group_WithIntegrationScenario_Case9 | Verifying that group with integration scenario case9 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case9 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Group_WithIntegrationScenario_Case10 | Verifying that group with integration scenario case10 | Setup with integration scenario -> Call Group -> Assert expected behavior | Group with integration scenario case10 | In scope: Group behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Hydration

## HydrationIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Hydrate_WithIntegrationScenario_Case1 | Verifying that hydrate with integration scenario case1 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case1 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Hydrate_WithIntegrationScenario_Case2 | Verifying that hydrate with integration scenario case2 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case2 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Hydrate_WithIntegrationScenario_Case3 | Verifying that hydrate with integration scenario case3 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case3 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Hydrate_WithIntegrationScenario_Case4 | Verifying that hydrate with integration scenario case4 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case4 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Hydrate_WithIntegrationScenario_Case5 | Verifying that hydrate with integration scenario case5 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case5 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Hydrate_WithIntegrationScenario_Case6 | Verifying that hydrate with integration scenario case6 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case6 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Hydrate_WithIntegrationScenario_Case7 | Verifying that hydrate with integration scenario case7 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case7 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Hydrate_WithIntegrationScenario_Case8 | Verifying that hydrate with integration scenario case8 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case8 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Hydrate_WithIntegrationScenario_Case9 | Verifying that hydrate with integration scenario case9 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case9 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Hydrate_WithIntegrationScenario_Case10 | Verifying that hydrate with integration scenario case10 | Setup with integration scenario -> Call Hydrate -> Assert expected behavior | Hydrate with integration scenario case10 | In scope: Hydrate behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Decorating

## DecoratorAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Decorate_WithAdditionalScenario_Case1 | Verifying that decorate with additional scenario case1 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case1 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Decorate_WithAdditionalScenario_Case2 | Verifying that decorate with additional scenario case2 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case2 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Decorate_WithAdditionalScenario_Case3 | Verifying that decorate with additional scenario case3 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case3 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Decorate_WithAdditionalScenario_Case4 | Verifying that decorate with additional scenario case4 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case4 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Decorate_WithAdditionalScenario_Case5 | Verifying that decorate with additional scenario case5 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case5 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Decorate_WithAdditionalScenario_Case6 | Verifying that decorate with additional scenario case6 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case6 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Decorate_WithAdditionalScenario_Case7 | Verifying that decorate with additional scenario case7 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case7 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Decorate_WithAdditionalScenario_Case8 | Verifying that decorate with additional scenario case8 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case8 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Decorate_WithAdditionalScenario_Case9 | Verifying that decorate with additional scenario case9 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case9 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Decorate_WithAdditionalScenario_Case10 | Verifying that decorate with additional scenario case10 | Setup with additional scenario -> Call Decorate -> Assert expected behavior | Decorate with additional scenario case10 | In scope: Decorate behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Datalake

## FirehoseServiceAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | PutRecord_WithAdditionalScenario_Case1 | Verifying that put record with additional scenario case1 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case1 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | PutRecord_WithAdditionalScenario_Case2 | Verifying that put record with additional scenario case2 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case2 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | PutRecord_WithAdditionalScenario_Case3 | Verifying that put record with additional scenario case3 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case3 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | PutRecord_WithAdditionalScenario_Case4 | Verifying that put record with additional scenario case4 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case4 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | PutRecord_WithAdditionalScenario_Case5 | Verifying that put record with additional scenario case5 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case5 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | PutRecord_WithAdditionalScenario_Case6 | Verifying that put record with additional scenario case6 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case6 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | PutRecord_WithAdditionalScenario_Case7 | Verifying that put record with additional scenario case7 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case7 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | PutRecord_WithAdditionalScenario_Case8 | Verifying that put record with additional scenario case8 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case8 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | PutRecord_WithAdditionalScenario_Case9 | Verifying that put record with additional scenario case9 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case9 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | PutRecord_WithAdditionalScenario_Case10 | Verifying that put record with additional scenario case10 | Setup with additional scenario -> Call PutRecord -> Assert expected behavior | PutRecord with additional scenario case10 | In scope: PutRecord behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Canoe

## CanoeProvLocGetterAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetProvLocs_WithAdditionalScenario_Case1 | Verifying that get prov locs with additional scenario case1 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case1 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetProvLocs_WithAdditionalScenario_Case2 | Verifying that get prov locs with additional scenario case2 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case2 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetProvLocs_WithAdditionalScenario_Case3 | Verifying that get prov locs with additional scenario case3 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case3 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetProvLocs_WithAdditionalScenario_Case4 | Verifying that get prov locs with additional scenario case4 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case4 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetProvLocs_WithAdditionalScenario_Case5 | Verifying that get prov locs with additional scenario case5 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case5 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetProvLocs_WithAdditionalScenario_Case6 | Verifying that get prov locs with additional scenario case6 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case6 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetProvLocs_WithAdditionalScenario_Case7 | Verifying that get prov locs with additional scenario case7 | Setup with additional scenario -> Call GetProvLocs -> Assert expected behavior | GetProvLocs with additional scenario case7 | In scope: GetProvLocs behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Personalization

## PersonalizationIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Personalize_WithIntegrationScenario_Case1 | Verifying that personalize with integration scenario case1 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case1 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Personalize_WithIntegrationScenario_Case2 | Verifying that personalize with integration scenario case2 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case2 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Personalize_WithIntegrationScenario_Case3 | Verifying that personalize with integration scenario case3 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case3 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Personalize_WithIntegrationScenario_Case4 | Verifying that personalize with integration scenario case4 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case4 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Personalize_WithIntegrationScenario_Case5 | Verifying that personalize with integration scenario case5 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case5 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Personalize_WithIntegrationScenario_Case6 | Verifying that personalize with integration scenario case6 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case6 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Personalize_WithIntegrationScenario_Case7 | Verifying that personalize with integration scenario case7 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case7 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Personalize_WithIntegrationScenario_Case8 | Verifying that personalize with integration scenario case8 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case8 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Personalize_WithIntegrationScenario_Case9 | Verifying that personalize with integration scenario case9 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case9 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Personalize_WithIntegrationScenario_Case10 | Verifying that personalize with integration scenario case10 | Setup with integration scenario -> Call Personalize -> Assert expected behavior | Personalize with integration scenario case10 | In scope: Personalize behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Models

## LocationParamFactoryAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Create_WithAdditionalScenario_Case1 | Verifying that create with additional scenario case1 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case1 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Create_WithAdditionalScenario_Case2 | Verifying that create with additional scenario case2 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case2 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Create_WithAdditionalScenario_Case3 | Verifying that create with additional scenario case3 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case3 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Create_WithAdditionalScenario_Case4 | Verifying that create with additional scenario case4 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case4 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Create_WithAdditionalScenario_Case5 | Verifying that create with additional scenario case5 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case5 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Create_WithAdditionalScenario_Case6 | Verifying that create with additional scenario case6 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case6 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Create_WithAdditionalScenario_Case7 | Verifying that create with additional scenario case7 | Setup with additional scenario -> Call Create -> Assert expected behavior | Create with additional scenario case7 | In scope: Create behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/CrossEncoder

## CrossEncoderIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Rerank_WithIntegrationScenario_Case1 | Verifying that rerank with integration scenario case1 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case1 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Rerank_WithIntegrationScenario_Case2 | Verifying that rerank with integration scenario case2 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case2 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Rerank_WithIntegrationScenario_Case3 | Verifying that rerank with integration scenario case3 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case3 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Rerank_WithIntegrationScenario_Case4 | Verifying that rerank with integration scenario case4 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case4 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Rerank_WithIntegrationScenario_Case5 | Verifying that rerank with integration scenario case5 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case5 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Rerank_WithIntegrationScenario_Case6 | Verifying that rerank with integration scenario case6 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case6 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Rerank_WithIntegrationScenario_Case7 | Verifying that rerank with integration scenario case7 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case7 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Rerank_WithIntegrationScenario_Case8 | Verifying that rerank with integration scenario case8 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case8 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Rerank_WithIntegrationScenario_Case9 | Verifying that rerank with integration scenario case9 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case9 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Rerank_WithIntegrationScenario_Case10 | Verifying that rerank with integration scenario case10 | Setup with integration scenario -> Call Rerank -> Assert expected behavior | Rerank with integration scenario case10 | In scope: Rerank behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Embeddings

## EmbeddingServiceIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetEmbedding_WithIntegrationScenario_Case1 | Verifying that get embedding with integration scenario case1 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case1 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | GetEmbedding_WithIntegrationScenario_Case2 | Verifying that get embedding with integration scenario case2 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case2 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | GetEmbedding_WithIntegrationScenario_Case3 | Verifying that get embedding with integration scenario case3 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case3 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | GetEmbedding_WithIntegrationScenario_Case4 | Verifying that get embedding with integration scenario case4 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case4 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | GetEmbedding_WithIntegrationScenario_Case5 | Verifying that get embedding with integration scenario case5 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case5 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | GetEmbedding_WithIntegrationScenario_Case6 | Verifying that get embedding with integration scenario case6 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case6 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | GetEmbedding_WithIntegrationScenario_Case7 | Verifying that get embedding with integration scenario case7 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case7 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | GetEmbedding_WithIntegrationScenario_Case8 | Verifying that get embedding with integration scenario case8 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case8 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | GetEmbedding_WithIntegrationScenario_Case9 | Verifying that get embedding with integration scenario case9 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case9 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | GetEmbedding_WithIntegrationScenario_Case10 | Verifying that get embedding with integration scenario case10 | Setup with integration scenario -> Call GetEmbedding -> Assert expected behavior | GetEmbedding with integration scenario case10 | In scope: GetEmbedding behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Semantic

## VectorSearchIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Search_WithVectorSearchIntegration_Case1 | Verifying that search with vector search integration case1 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case1 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Search_WithVectorSearchIntegration_Case2 | Verifying that search with vector search integration case2 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case2 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Search_WithVectorSearchIntegration_Case3 | Verifying that search with vector search integration case3 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case3 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Search_WithVectorSearchIntegration_Case4 | Verifying that search with vector search integration case4 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case4 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Search_WithVectorSearchIntegration_Case5 | Verifying that search with vector search integration case5 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case5 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Search_WithVectorSearchIntegration_Case6 | Verifying that search with vector search integration case6 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case6 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Search_WithVectorSearchIntegration_Case7 | Verifying that search with vector search integration case7 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case7 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Search_WithVectorSearchIntegration_Case8 | Verifying that search with vector search integration case8 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case8 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Search_WithVectorSearchIntegration_Case9 | Verifying that search with vector search integration case9 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case9 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Search_WithVectorSearchIntegration_Case10 | Verifying that search with vector search integration case10 | Setup with vector search integration -> Call Search -> Assert expected behavior | Search with vector search integration case10 | In scope: Search behavior, with vector search integration scenario. Out of scope: other scenarios and methods not under test. |


# Search/Supplementing

## SupplementersAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Supplement_WithAdditionalScenario_Case1 | Verifying that supplement with additional scenario case1 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case1 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Supplement_WithAdditionalScenario_Case2 | Verifying that supplement with additional scenario case2 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case2 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Supplement_WithAdditionalScenario_Case3 | Verifying that supplement with additional scenario case3 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case3 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Supplement_WithAdditionalScenario_Case4 | Verifying that supplement with additional scenario case4 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case4 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Supplement_WithAdditionalScenario_Case5 | Verifying that supplement with additional scenario case5 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case5 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Supplement_WithAdditionalScenario_Case6 | Verifying that supplement with additional scenario case6 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case6 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Supplement_WithAdditionalScenario_Case7 | Verifying that supplement with additional scenario case7 | Setup with additional scenario -> Call Supplement -> Assert expected behavior | Supplement with additional scenario case7 | In scope: Supplement behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Annotation

## RequiredEsFiltererAttributeAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Attribute_WithAdditionalScenario_Case1 | Verifying that attribute with additional scenario case1 | Setup with additional scenario -> Call Attribute -> Assert expected behavior | Attribute with additional scenario case1 | In scope: Attribute behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Attribute_WithAdditionalScenario_Case2 | Verifying that attribute with additional scenario case2 | Setup with additional scenario -> Call Attribute -> Assert expected behavior | Attribute with additional scenario case2 | In scope: Attribute behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Attribute_WithAdditionalScenario_Case3 | Verifying that attribute with additional scenario case3 | Setup with additional scenario -> Call Attribute -> Assert expected behavior | Attribute with additional scenario case3 | In scope: Attribute behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Attribute_WithAdditionalScenario_Case4 | Verifying that attribute with additional scenario case4 | Setup with additional scenario -> Call Attribute -> Assert expected behavior | Attribute with additional scenario case4 | In scope: Attribute behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Attribute_WithAdditionalScenario_Case5 | Verifying that attribute with additional scenario case5 | Setup with additional scenario -> Call Attribute -> Assert expected behavior | Attribute with additional scenario case5 | In scope: Attribute behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |


# Search/Utils

## SearchUtilsIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Utility_WithIntegrationScenario_Case1 | Verifying that utility with integration scenario case1 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case1 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | Utility_WithIntegrationScenario_Case2 | Verifying that utility with integration scenario case2 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case2 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | Utility_WithIntegrationScenario_Case3 | Verifying that utility with integration scenario case3 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case3 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | Utility_WithIntegrationScenario_Case4 | Verifying that utility with integration scenario case4 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case4 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | Utility_WithIntegrationScenario_Case5 | Verifying that utility with integration scenario case5 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case5 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | Utility_WithIntegrationScenario_Case6 | Verifying that utility with integration scenario case6 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case6 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | Utility_WithIntegrationScenario_Case7 | Verifying that utility with integration scenario case7 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case7 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | Utility_WithIntegrationScenario_Case8 | Verifying that utility with integration scenario case8 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case8 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | Utility_WithIntegrationScenario_Case9 | Verifying that utility with integration scenario case9 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case9 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | Utility_WithIntegrationScenario_Case10 | Verifying that utility with integration scenario case10 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case10 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 11 | | Utility_WithIntegrationScenario_Case11 | Verifying that utility with integration scenario case11 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case11 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 12 | | Utility_WithIntegrationScenario_Case12 | Verifying that utility with integration scenario case12 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case12 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 13 | | Utility_WithIntegrationScenario_Case13 | Verifying that utility with integration scenario case13 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case13 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 14 | | Utility_WithIntegrationScenario_Case14 | Verifying that utility with integration scenario case14 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case14 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |
| 15 | | Utility_WithIntegrationScenario_Case15 | Verifying that utility with integration scenario case15 | Setup with integration scenario -> Call Utility -> Assert expected behavior | Utility with integration scenario case15 | In scope: Utility behavior, with integration scenario scenario. Out of scope: other scenarios and methods not under test. |


# Utils

## TextHelperAdditionalTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ExtractSentences_WithAdditionalScenario_Case1 | Verifying that extract sentences with additional scenario case1 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case1 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 2 | | ExtractSentences_WithAdditionalScenario_Case2 | Verifying that extract sentences with additional scenario case2 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case2 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 3 | | ExtractSentences_WithAdditionalScenario_Case3 | Verifying that extract sentences with additional scenario case3 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case3 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 4 | | ExtractSentences_WithAdditionalScenario_Case4 | Verifying that extract sentences with additional scenario case4 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case4 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 5 | | ExtractSentences_WithAdditionalScenario_Case5 | Verifying that extract sentences with additional scenario case5 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case5 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 6 | | ExtractSentences_WithAdditionalScenario_Case6 | Verifying that extract sentences with additional scenario case6 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case6 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 7 | | ExtractSentences_WithAdditionalScenario_Case7 | Verifying that extract sentences with additional scenario case7 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case7 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 8 | | ExtractSentences_WithAdditionalScenario_Case8 | Verifying that extract sentences with additional scenario case8 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case8 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 9 | | ExtractSentences_WithAdditionalScenario_Case9 | Verifying that extract sentences with additional scenario case9 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case9 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |
| 10 | | ExtractSentences_WithAdditionalScenario_Case10 | Verifying that extract sentences with additional scenario case10 | Setup with additional scenario -> Call ExtractSentences -> Assert expected behavior | ExtractSentences with additional scenario case10 | In scope: ExtractSentences behavior, with additional scenario scenario. Out of scope: other scenarios and methods not under test. |

# Search/Es/Filtering

## CompositeFiltererTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | Filter_WithCompositeFilter_Case1 | Verifying that filter with composite filter case1 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case1 | In scope: Filter behavior. Out of scope: other scenarios. |
| 2 | | Filter_WithCompositeFilter_Case2 | Verifying that filter with composite filter case2 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case2 | In scope: Filter behavior. Out of scope: other scenarios. |
| 3 | | Filter_WithCompositeFilter_Case3 | Verifying that filter with composite filter case3 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case3 | In scope: Filter behavior. Out of scope: other scenarios. |
| 4 | | Filter_WithCompositeFilter_Case4 | Verifying that filter with composite filter case4 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case4 | In scope: Filter behavior. Out of scope: other scenarios. |
| 5 | | Filter_WithCompositeFilter_Case5 | Verifying that filter with composite filter case5 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case5 | In scope: Filter behavior. Out of scope: other scenarios. |
| 6 | | Filter_WithCompositeFilter_Case6 | Verifying that filter with composite filter case6 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case6 | In scope: Filter behavior. Out of scope: other scenarios. |
| 7 | | Filter_WithCompositeFilter_Case7 | Verifying that filter with composite filter case7 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case7 | In scope: Filter behavior. Out of scope: other scenarios. |
| 8 | | Filter_WithCompositeFilter_Case8 | Verifying that filter with composite filter case8 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case8 | In scope: Filter behavior. Out of scope: other scenarios. |
| 9 | | Filter_WithCompositeFilter_Case9 | Verifying that filter with composite filter case9 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case9 | In scope: Filter behavior. Out of scope: other scenarios. |
| 10 | | Filter_WithCompositeFilter_Case10 | Verifying that filter with composite filter case10 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case10 | In scope: Filter behavior. Out of scope: other scenarios. |
| 11 | | Filter_WithCompositeFilter_Case11 | Verifying that filter with composite filter case11 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case11 | In scope: Filter behavior. Out of scope: other scenarios. |
| 12 | | Filter_WithCompositeFilter_Case12 | Verifying that filter with composite filter case12 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case12 | In scope: Filter behavior. Out of scope: other scenarios. |
| 13 | | Filter_WithCompositeFilter_Case13 | Verifying that filter with composite filter case13 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case13 | In scope: Filter behavior. Out of scope: other scenarios. |
| 14 | | Filter_WithCompositeFilter_Case14 | Verifying that filter with composite filter case14 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case14 | In scope: Filter behavior. Out of scope: other scenarios. |
| 15 | | Filter_WithCompositeFilter_Case15 | Verifying that filter with composite filter case15 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case15 | In scope: Filter behavior. Out of scope: other scenarios. |
| 16 | | Filter_WithCompositeFilter_Case16 | Verifying that filter with composite filter case16 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case16 | In scope: Filter behavior. Out of scope: other scenarios. |
| 17 | | Filter_WithCompositeFilter_Case17 | Verifying that filter with composite filter case17 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case17 | In scope: Filter behavior. Out of scope: other scenarios. |
| 18 | | Filter_WithCompositeFilter_Case18 | Verifying that filter with composite filter case18 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case18 | In scope: Filter behavior. Out of scope: other scenarios. |
| 19 | | Filter_WithCompositeFilter_Case19 | Verifying that filter with composite filter case19 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case19 | In scope: Filter behavior. Out of scope: other scenarios. |
| 20 | | Filter_WithCompositeFilter_Case20 | Verifying that filter with composite filter case20 | Setup with composite filter -> Call Filter -> Assert expected behavior | Filter with composite filter case20 | In scope: Filter behavior. Out of scope: other scenarios. |
