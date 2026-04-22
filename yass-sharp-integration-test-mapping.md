# YassSharp Integration Tests - Test Case Mapping

**Repository:** https://github.com/Zocdoc/yass-sharp/tree/main/tests/YassSharp.IntegrationTests  
**Framework:** NUnit  
**Total Test Files:** 26  
**Total Test Cases:** 166  

---

# (root)

## ExampleTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | TokenEmptyTest | Placeholder sanity check using FluentAssertions | Compute 1 + 1 -> Assert result equals 2 | Trivial smoke check to verify test harness compiles and runs | In scope: NUnit runner + FluentAssertions plumbing. Out of scope: any YASS Sharp behavior |

## BrandRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | FiltersByBrandUsingFunctionScoreFiltersAndReturnsBrandAffiliations | Brand-affiliation boosting via function_score_filters returns hits whose BrandAffiliations match a specific legacy brand id | Setup PCP-in-NYC request with insurance ic_307/ip_2280, procedure 75, rolled-up, and a function_score_filters term on BrandAffiliations.legacyId -> Apply YASS-Use-Es7=on via X-ZD-ABOverrides header -> Call debuggable-search and ValidateSnapshot | Verifies brand filtering + aggregations against snapshot | In scope: brand function-score filter, rolled-up mode, facet list. Out of scope: non-ES7 path, non-NYC locales |

## CallerTypeRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ReturnsLocationsForProviderReferralsCallerType | Routing/response for caller_type=providerReferrals | Setup Full-debug request with caller_type=providerReferrals -> Apply YASS-Use-Es7 + YASS-Streaming-Index-Test overrides -> ValidateSnapshot | Confirms provider-referrals algorithm returns expected locations snapshot | In scope: providerReferrals routing. Out of scope: listing/booking caller types |
| 2 | | SortsPreviewProvidersForListingCallerTypeAndNewFlavorListingAlgoV1 | caller_type=listing with flavor=listing-algo-v1 preview-provider sorting | Setup Full-debug request with caller_type=listing and flavor=listing-algo-v1 -> Apply ES7 + streaming-index AB overrides -> ValidateSnapshot | Validates listing-algo-v1 preview sort snapshot | In scope: listing-algo-v1 flavor. Out of scope: default listing algo |
| 3 | | RoutesBookingCallerTypeToListingMapleContainerWithHardAvailabilityFilter | caller_type=booking routing to listing-maple container with hard availability filter | Setup Full-debug request with caller_type=booking -> Apply ES7 + streaming-index AB overrides -> ValidateSnapshot | Ensures booking caller type enforces hard availability filter via listing-maple | In scope: booking caller type routing. Out of scope: soft availability filtering |

## CovidRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | DoesNotBlockMedicaidInFPStateNJIfSearchedForCOVID19Procedure | Medicaid in a flipped-state (NJ) is not blocked for COVID-19 procedure 5028 | Setup NJ jersey-city request with Medicaid ip_18395/ic_358 and procedure 5028 -> Apply YASS-Use-Es7=on -> ValidateSnapshot | Confirms COVID testing overrides government-insurance block in NJ | In scope: FP-state Medicaid + COVID procedure. Out of scope: non-COVID procedures |
| 2 | | DoesNotCheckForGovInsuranceIfSearchedForCOVID19Testing | Government-insurance gating bypassed when searching COVID-19 testing (procedure 5028) | Setup request with specialty 153 + procedure 5028 -> Apply ES7 override -> ValidateSnapshot | Ensures gov-insurance check is skipped for COVID testing | In scope: gov-insurance branch for procedure 5028. Out of scope: other specialties |
| 3 | | DoesNotFilterOutProvLocsOutOfBudgetIfSearchedForCOVID19Testing | Out-of-budget filtering disabled for COVID-19 testing | Setup request with specialty 153 + procedure 5028 -> Apply ES7 override -> ValidateSnapshot | Verifies budget filter bypassed for COVID testing | In scope: budget filter for COVID procedure. Out of scope: budget filter in general flow |

## DependencyFailuresTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | HandlesAbFailure | Graceful handling when AB service fails (CAUSE_AB_FAILURE marker) | Setup basic request -> Apply ES7 AB override -> Set X-ZD-Session-Id=CAUSE_AB_FAILURE to trigger mock AB failure -> ValidateSnapshot | Ensures request still succeeds when AB client fails | In scope: AB client failure path. Out of scope: real AB assignments |
| 2 | | HandlesAvailabilitySlowness | Availability service slowness path via magic procedure 1600 (constipation) | Setup Full-debug request with specialty 153 + procedure 1600 -> Apply ES7 override -> ValidateSnapshot | Validates response when availability is slow | In scope: availability-slow branch. Out of scope: availability-fast path |
| 3 | | HandlesAvailabilityFailure | Availability service hard failure via magic procedure 1063 | Setup request with procedure 1063 + specialty 153 -> Apply ES7 override -> ValidateSnapshot | Confirms graceful degradation when availability errors | In scope: availability-failure path. Out of scope: partial-failure modes |
| 4 | | ElasticsearchQueryError_Returns500 | Invalid ES query (negative distance_radius_miles) surfaces as HTTP 500 | Early-return if IsSmokeTest() -> Setup request with distance_radius_miles=-1 -> Call debuggable search -> Assert HttpRequestException thrown and LastResponseStatusCode == 500 | Verifies ES query errors propagate to 500 status | In scope: ES error -> HTTP 500 mapping. Out of scope: smoke tests (auto-skipped to avoid staging alerts) |

## ElasticTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | HasAGoodElasticQueryForDentist | ES query generation for dentist procedure 12 at NYC location with Full debug | Setup Full-debug request with NYC location, specialty 98, procedure 12 -> ValidateSnapshot | Snapshots generated ES query for dentist search | In scope: ES query structure for dentist. Out of scope: downstream ranking |
| 2 | | ReturnsAggregatedHitsWhenInsuranceInformationIsProvided | Aggregations grouped by insurance with filter/facets and ic_307/ip_2280 | Setup Processors-debug request with sex/procedures/hospital_affiliations facets, procedures/sex filter, insurance ic_307/ip_2280 -> ValidateSnapshot | Confirms aggregation behavior when insurance is provided | In scope: facet aggregations with insurance context. Out of scope: uninsured path |

## FacetFilterRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ShowsVirtualLocationAggregations | is_virtual_location facet aggregations appear in response | Setup request with facets=is_virtual_location -> Apply ES7 override -> ValidateSnapshot | Facet returns virtual-location counts | In scope: is_virtual_location facet without filter. Out of scope: in_person_or_video_visit facet |
| 2 | | ShowsVirtualLocationAggregationsWhenFilterIsApplied | is_virtual_location aggregations still present when filter is_virtual_location=offers video visits applied | Setup request with facets + filter is_virtual_location:b64_... -> Apply ES7 override -> ValidateSnapshot | Facet survives active filter | In scope: facet-with-filter behavior. Out of scope: other facet types |
| 3 | | ShowsInPersonOrVideoVisitAggregations | in_person_or_video_visit facet aggregations returned | Setup request with facets=in_person_or_video_visit -> Apply ES7 override -> ValidateSnapshot | Returns visit-type facet counts | In scope: visit-type facet shape. Out of scope: filter variants |
| 4 | | ShowsInPersonOrVideoVisitAggregationsWhenInPersonFilterIsApplied | Same facet with filter=in_person_or_video_visit:in_person | Setup request with in_person filter + facet -> ES7 override -> ValidateSnapshot | Facet counts correct under in_person filter | In scope: in-person filter + facet. Out of scope: video filter |
| 5 | | ShowsInPersonOrVideoVisitAggregationsWhenVideoVisitFilterIsApplied | Same facet with filter=in_person_or_video_visit:video_visit | Setup request with video_visit filter + facet -> ES7 override -> ValidateSnapshot | Facet counts correct under video-visit filter | In scope: video-visit filter + facet. Out of scope: in-person filter |

## GoodRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | LocalDateSerializationShouldWorkProperly | NodaTime LocalDate serialization via date_searched_for parameter | Setup request with page_size=1 and date_searched_for=2018-09-06 -> ValidateSnapshot | Ensures LocalDate is serialized correctly on the wire | In scope: date_searched_for serialization. Out of scope: timezone/zoned-date handling |
| 2 | | ReturnsMapDotsInResponse | mapDots payload present on default request | Setup request with page_size=10 page=0 -> ValidateSnapshot | Baseline mapDots presence snapshot | In scope: mapDots default path. Out of scope: enterprise map-dots parameter |
| 3 | | ReturnsProviderQualitiesInResponse | Provider qualities returned when debug=Full | Setup Full-debug request with page_size=10 page=0 -> ValidateSnapshot | Snapshots provider-qualities payload | In scope: Full debug provider qualities. Out of scope: Summary debug |
| 4 | | ReturnsAggregatedHitsWhenInsuranceInformationIsProvided | Aggregated hits with insurance (ic_300/ip_2280) and procedure 75 | Setup Summary-debug request with NYC location, filter procedures:75, insurance -> ValidateSnapshot | Confirms aggregation under insurance context | In scope: insurance-backed aggregation. Out of scope: uninsured path |

## IncludeMapDotsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | EnterpriseDirectory_WithIncludeMapDots_ReturnsProviderLocationsMapDots | include_map_dots_for_default_enterprise_algo=true returns providerLocationsMapDots for Schweiger dir 459 | Setup Manhattan request for specialty 101 with include_map_dots_for_default_enterprise_algo=true -> Apply ES7 + streaming-index overrides -> If smoke: call against dir 459 and assert HTTP 200 + audit data -> Otherwise: load snapshot searchRequestId, call CallDebuggableSearch(459), save-if-update or AssertSnapshotsMatch | Verifies enterprise map-dots feature for directory 459 | In scope: enterprise directory (Schweiger/459) map-dots. Out of scope: non-enterprise directories |

## InsuranceRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | NoLongerBlocksMedicareInsurance | Medicare (ic_1419/ip_16458) no longer blocked in Atlanta | Setup request with page_size=10, Medicare insurance, Atlanta location -> Apply ES7 override -> ValidateSnapshot | Validates Medicare is not blocked | In scope: Medicare non-blocking behavior. Out of scope: Medicaid |
| 2 | | DoesNotBlockNegativeInsurances | Negative insurance ids (ip_-2 / ic_358) are not blocked | Setup request with negative insurance ids + Atlanta location -> Apply ES7 override -> ValidateSnapshot | Ensures synthetic/negative ids not blocked | In scope: negative insurance id handling. Out of scope: positive id edge cases |
| 3 | | DoesNotDisplayGovernmentInsuranceBannerIfSearchedFromNonFlippedStateMAWithMedicaid | No gov-insurance banner in non-flipped state MA with MassHealth | Setup Boston request with ip_18386/ic_358 -> Apply ES7 override -> ValidateSnapshot | Confirms banner suppression in non-FP state | In scope: MA gov-insurance banner logic. Out of scope: FP states |
| 4 | | DoesNotDisplayGovernmentInsuranceBannerIfSearchedFromNJWithNoInsurance | No gov-insurance banner in NJ when insurance not provided | Setup Newport NJ request without insurance -> Apply ES7 override -> ValidateSnapshot | Banner suppressed for NJ uninsured | In scope: NJ uninsured banner rule. Out of scope: NJ with insurance |
| 5 | | DoesNotDisplayGovernmentInsuranceBannerIfSearchedFromNYWithNoInsurance | No gov-insurance banner in NY when insurance not provided | Setup WTC NY request without insurance -> Apply ES7 override -> ValidateSnapshot | Banner suppressed for NY uninsured | In scope: NY uninsured banner rule. Out of scope: NY with insurance |
| 6 | | ReturnsProvidersIfSearchedWithCommercialInsuranceFromPlaceAdjacentToOtherStates | Providers returned for Aetna search near multi-state border (NJ/PA/DE) | Setup Bridgeport NJ request with ic_212 (Aetna) -> Apply ES7 override -> ValidateSnapshot | Commercial-insurance cross-border coverage | In scope: cross-border commercial search. Out of scope: single-state commercial |
| 7 | | CorrectlyGroupsByInsuranceForVirtualAndOrganicResults | Insurance grouping for virtual + organic results | Setup Summary-debug request with ic_300/ip_2224 -> Apply ES7 override -> ValidateSnapshot | Grouping snapshot for virtual+organic under insurance | In scope: insurance grouping logic. Out of scope: non-insurance grouping |

## MarketIntelligenceTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | SingleSpecialtyQuery_ReturnsValidResponse | POST /market-intelligence happy path for specialty 117 at Manhattan | Setup MI body with specialty_id=117 -> POST to endpoint -> Assert 200 + results[0] shape (supply, refinements monotonic distance/availability, gender non-negative, error null) -> ValidateMiSnapshot | End-to-end MI happy path validation | In scope: single-specialty MI response contract. Out of scope: procedure_id path |
| 2 | | MultipleSpecialtyQueries_ReturnsResultPerQuery | Three specialty queries in one request return three ordered results | Setup body with specialties 117/110/105 -> POST -> Assert 200, 3 results, query_index 0/1/2, specialty_id echoed, supply/page_estimates/refinements present | MI supports batched queries | In scope: multi-query result ordering + echo. Out of scope: query-level errors |
| 3 | | QueryWithProcedureId_ReturnsResultWithProcedure | procedure_id=75 + specialty_id=117 echoed back in result | Setup body with specialty 117 + procedure 75 -> POST -> Assert 200, results[0] echoes specialty_id and procedure_id, supply/refinements present | MI accepts procedure scoping | In scope: specialty+procedure scoping. Out of scope: discover_visit_reasons combo |
| 4 | | SingleSpecialtyQuery_SupplyCountsAreReasonable | provider_location_count > 0 and availability counts non-negative for specialty 117 | Setup body specialty 117 -> POST -> Assert supply.provider_location_count > 0 and available_within_7_days >= 0 | Supply signals are sane | In scope: supply sanity. Out of scope: refinements |
| 5 | | SingleSpecialtyQuery_RefinementCountsAreMonotonic | Distance/availability refinement windows are monotonically non-decreasing | Setup body specialty 117 -> POST -> Assert distance within_1_mi <= within_5_mi <= within_10_mi and today <= within_3_days <= within_7_days; gender/visit_type counts >= 0 | Refinement window monotonicity invariant | In scope: monotonicity check. Out of scope: absolute counts |
| 6 | | QueryWithFilter_ReducesSupplyComparedToUnfiltered | Applying sex=female filter does not increase supply count vs unfiltered | Issue unfiltered query for specialty 117 -> Issue filtered query with filters.sex=female -> Assert filtered count <= unfiltered count | Filter-reduces-supply invariant | In scope: filter effect on supply. Out of scope: non-sex filters |
| 7 | | TooManyQueries_ReturnsBadRequest | 11 queries exceeds maxItems=10 so Plinth returns 400 | Build 11-query body -> POST -> Assert 400 BadRequest | Validates plinth-level array max enforcement | In scope: maxItems validation. Out of scope: other schema constraints |
| 8 | | ProcedureIdWithDiscoverVisitReasons_ReturnsValidationError | Mutually exclusive procedure_id + discover_visit_reasons returns per-query VALIDATION_ERROR | Setup body with both procedure_id and discover_visit_reasons -> POST -> Assert 200 with results[0].error.code=VALIDATION_ERROR and message contains "mutually exclusive" | Per-query validation error contract | In scope: MI validation errors. Out of scope: endpoint-level 400 |
| 9 | | ResponseRefinements_ContainAllExpectedDimensions | Response refinements include distance (1/5/10mi), availability (today/3d/7d), gender, visit_type | Setup body specialty 117 -> POST -> Assert all expected refinement dimensions non-null -> ValidateMiSnapshot | Schema completeness check | In scope: refinement schema. Out of scope: dimension-specific values |
| 10 | | MarketIntelligence_WithBaseFilter_ReturnsResults | Base filter (sex=female) still returns non-empty results | Setup body with filters.sex=female + specialty 117 -> POST -> Assert 200 and non-empty results | Base filter works end-to-end | In scope: base filter integration. Out of scope: refinement validation |
| 11 | | SupplyOnlyScope_ReturnsSupplyAndRefinementsWithoutPageEstimates | evaluation_scope=supply_only: supply + refinements populated, page_estimates null | Setup body with evaluation_scope=supply_only + specialty 117 -> POST -> Assert scope echoed, supply/refinements present, page_estimates null, error null -> ValidateMiSnapshot | Supply-only scope contract | In scope: supply_only scope. Out of scope: full-scope SPO |
| 12 | | FullScope_EchoesEvaluationScopeInResponse | evaluation_scope=full echoed and supply/page_estimates/refinements all populated | Setup body with evaluation_scope=full + specialty 117 -> POST -> Assert 200, scope echoed, all three blocks present -> ValidateMiSnapshot | Full-scope contract | In scope: full scope. Out of scope: supply-only |

## MarketIntelligenceValidationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | CommonSpecialty_SupplySignalsValid | MI supply + refinements self-consistent for Dentist (110) in Manhattan | POST MI body specialty 110 -> AssertSupplyValid -> AssertRefinementsConsistent with supply | Consistency invariants for common specialty | In scope: common specialty consistency. Out of scope: insurance-aware counts |
| 2 | | WithInsurance_InNetworkValid | in_network counts behave correctly with insc_2 (Aetna) for Dermatologist (104) | POST with insurance_carrier_id=insc_2 specialty 104 -> AssertSupplyValid -> If in_network_count > 0 assert combinations.in_network_within_5_mi <= in_network_count | In-network consistency under insurance | In scope: insurance-aware supply. Out of scope: plan-level filtering |
| 3 | | FullScope_PageEstimatesValid | evaluation_scope=full produces valid page_estimates for PCP (126) | POST with scope=full specialty 126 -> AssertSupplyValid -> AssertPageEstimatesValidIfPresent (pconv in (0,1], revenue >= 0) | Full-scope page-estimate sanity | In scope: page_estimates validity. Out of scope: supply_only scope |
| 4 | | SupplyOnly_NoPageEstimates | evaluation_scope=supply_only in Brooklyn has refinements but no page_estimates | POST with scope=supply_only specialty 126 at Brooklyn -> AssertSupplyValid -> Assert refinements present and page_estimates null | Supply-only suppresses page estimates | In scope: supply-only scope. Out of scope: full scope |
| 5 | | CrossValidate_SupplyMatchesCoreSearch | MI supply.provider_location_count matches core /provider-locations total_hits within 5 | POST MI specialty 110 -> GET /provider-locations with equivalent params -> Assert both > 0 and \|diff\| <= 5 | MI and core search use same ES TotalHits | In scope: MI-vs-core consistency. Out of scope: large drift scenarios |
| 6 | | DebuggableEndpoint_ReturnsDebugInfo | POST /debuggable-search MI populates debug_info (algorithm_name, scope, total_hits, organic_results_count) | POST debuggable MI body specialty 110 -> Assert debug_info.algorithm_name non-empty, evaluation_scope=full, total_hits > 0, organic_results_count > 0; AssertSupplyValid | Debug endpoint exposes diagnostics | In scope: debuggable MI debug_info. Out of scope: non-debug endpoint fields |

## MobileRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | FlipsCoinOnMobileAppSearchPage0 | Mobile-app coin-flip behavior on page 0 (iPhoneApp) | Setup Summary-debug request page_size=15 page=0 -> Add iOS X-ZD-User-Agent + X-ZD-Application=iPhoneApp headers -> ValidateSnapshot | Mobile page-0 coin flip | In scope: iOS native-app path page 0. Out of scope: web path |
| 2 | | FlipsCoinForMapleMobileExperimentFromAndroidThatComesFromTheGQL | Android GQL directory-service request flips Maple mobile experiment on page 1 | Setup Summary-debug request page_size=15 page=1 -> Add Android UA + X-ZD-Application=directory-service headers -> ValidateSnapshot | Android GQL Maple mobile coin flip | In scope: Android + GQL caller. Out of scope: iOS direct app |
| 3 | | ReturnsOrganicPlusVirtualLocationsForMobile | NYC dermatologist mobile search returns organic + virtual locations | Setup full NYC dermatologist request (procedure 84, specialty 101) -> Apply ES7 + iOS UA headers -> ValidateSnapshot | Mobile organic + virtual mix | In scope: mobile organic+virtual. Out of scope: web organic-only |
| 4 | | ReturnsOrganicPlusVirtualLocationsWithProviderQualitiesForMobile | Same as above but with show_provider_qualities_app=true | Setup dermatologist request with show_provider_qualities_app=true -> Apply ES7 + iOS UA headers -> ValidateSnapshot | Mobile payload includes provider qualities | In scope: provider qualities on mobile app. Out of scope: mobile without qualities |

## OpenSearchTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | CanConnectToOpenSearchCluster | Basic connectivity to vpc-ci001 OpenSearch /_cluster/health | GET /_cluster/health -> Assert cluster_name present and status in {green,yellow,red} | OpenSearch cluster is reachable | In scope: VPN-gated live cluster connectivity. Out of scope: auth |
| 2 | | CanListAllIndices | /_cat/indices returns at least one index with expected fields | GET /_cat/indices?format=json -> Assert array non-empty and first has index/health/status/docs.count | Index catalog is accessible | In scope: index listing shape. Out of scope: specific index contents |
| 3 | | CanGetClusterStats | /_cluster/stats returns nodes.count.total > 0 and indices.count >= 0 | GET /_cluster/stats -> Assert nodes.count.total > 0 and indices.count >= 0 | Cluster stats endpoint healthy | In scope: cluster stats shape. Out of scope: per-node metrics |
| 4 | | CanGetSampleDocumentsFromProviderInfoEmbeddingsIndex | Fetch 2 docs from provider-locations-streaming-v0.5 embeddings index with ProviderId/FirstName/LastName | GET /{index}/_search?size=2 -> Assert hits non-empty, first has _source.ProviderId non-empty and FirstName/LastName present | Embeddings index contains expected provider fields | In scope: embeddings index doc shape. Out of scope: kNN search |
| 5 | | CanFindProviderStatementWithEmbeddings | exists-query on ProviderStatement returns docs with non-empty statement + embedding vector | POST _search exists:ProviderStatement size=5 -> For each hit assert ProviderStatement non-empty and embedding array non-empty | ProviderStatement + embedding populated together | In scope: ProviderStatement + embedding pairing. Out of scope: embedding quality |
| 6 | | GetIndexMappingAndModelInfo | Index mapping exposes embedding as knn_vector and has settings | GET /{index}/_mapping -> Assert properties.ProviderId + properties.embedding.type == "knn_vector" -> GET /{index}/_settings -> Assert settings node | Index configured for kNN | In scope: knn_vector mapping + settings access. Out of scope: runtime kNN queries |
| 7 | | InspectSpecificProvider | Fetch any provider with ProviderStatement and assert core identity fields populated | POST _search exists:ProviderStatement size=1 -> Assert hits non-empty, FirstName/LastName/ProviderId/ProviderStatement all non-empty | Provider identity fields are populated | In scope: identity field population. Out of scope: match quality |

## ParametersRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | MatchesForParameter("basic") | Snapshot baseline for default request with no overrides | Build base request (page_size=10, debug=Summary) with no overrides -> Load snapshot searchRequestId -> CallDebuggableSearch -> AssertSnapshotsMatch | Baseline parameter snapshot | In scope: default parameters. Out of scope: smoke mode (HTTP 200 only) |
| 2 | | MatchesForParameter("distance") | rank_by=Distance sort behavior | Override rank_by=Distance -> CallDebuggableSearch -> AssertSnapshotsMatch | Distance ranking snapshot | In scope: distance ranker. Out of scope: other rankers |
| 3 | | MatchesForParameter("female") | provider_gender=Female filter | Override provider_gender=Female -> CallDebuggableSearch -> snapshot | Female gender filter | In scope: female filter. Out of scope: male filter |
| 4 | | MatchesForParameter("male") | provider_gender=Male filter | Override provider_gender=Male -> snapshot | Male gender filter | In scope: male filter. Out of scope: female filter |
| 5 | | MatchesForParameter("dentist") | specialty_id=98 dentist search | Override specialty_id=98 -> snapshot | Dentist specialty search | In scope: dentist baseline. Out of scope: procedures |
| 6 | | MatchesForParameter("psychiatryConsultation") | specialty 122 + procedure 171 | Override specialty_id=122, procedure_id=171 -> snapshot | Psychiatry consultation | In scope: psych consult. Out of scope: other specialties |
| 7 | | MatchesForParameter("obygynExam") | specialty 104 + procedure 130 | Override specialty_id=104, procedure_id=130 -> snapshot | OB-GYN exam | In scope: OB-GYN exam. Out of scope: OB-GYN other procedures |
| 8 | | MatchesForParameter("dermConsult") | specialty 101 + procedure 84 | Override specialty/procedure -> snapshot | Derm consult | In scope: derm consult. Out of scope: other derm procedures |
| 9 | | MatchesForParameter("entConsult") | specialty 130 + procedure 110 | Override specialty/procedure -> snapshot | ENT consult | In scope: ENT consult. Out of scope: other ENT procedures |
| 10 | | MatchesForParameter("eyeDocConsult") | specialty 386 + procedure 92 | Override specialty/procedure -> snapshot | Eye doctor consult | In scope: eye consult. Out of scope: optometry vs ophthalmology distinctions |
| 11 | | MatchesForParameter("orthoConsult") | specialty 117 + procedure 104 | Override specialty/procedure -> snapshot | Orthopedic consult | In scope: ortho consult. Out of scope: orthopedic surgeries |
| 12 | | MatchesForParameter("nephrologist") | specialty_id=107 nephrologist | Override specialty_id=107 -> snapshot | Nephrologist specialty | In scope: nephrologist. Out of scope: procedures |
| 13 | | MatchesForParameter("nephrologyConsultation") | specialty 107 + procedure 387 | Override specialty/procedure -> snapshot | Nephrology consult | In scope: nephrology consult. Out of scope: other nephrology procedures |
| 14 | | MatchesForParameter("spanishRheumatologyConsultation") | Spanish rheumatology consult (specialty 109, procedure 190, language 3) | Override specialty/procedure/search_type/language_id -> snapshot | Multilingual rheumatology consult | In scope: language_id+specialty_search_type. Out of scope: other languages |
| 15 | | MatchesForParameter("broadway") | zip_code=10012 | Override zip_code=10012 -> snapshot | Zip-code geocoding | In scope: zip as primary geo. Out of scope: coords |
| 16 | | MatchesForParameter("kids") | sees_children=true filter | Override sees_children=true -> snapshot | Pediatric-friendly filter | In scope: sees_children filter. Out of scope: age-range filters |
| 17 | | MatchesForParameter("late") | time_filter=After5PM | Override time_filter=After5PM -> snapshot | After-hours availability | In scope: After5PM time filter. Out of scope: other time windows |
| 18 | | MatchesForParameter("today") | day_filter=Today | Override day_filter=Today -> snapshot | Same-day availability filter | In scope: Today day filter. Out of scope: other day filters |
| 19 | | MatchesForParameter("spanish") | language_id=3 | Override language_id=3 -> snapshot | Spanish language filter | In scope: language 3. Out of scope: other languages |
| 20 | | MatchesForParameter("illness") | procedure 75 + specialty 153 illness visit | Override procedure/specialty -> snapshot | Illness visit | In scope: PCP illness search. Out of scope: wellness search |
| 21 | | MatchesForParameter("aetna") | insurance_carrier_id=ic_212 Aetna | Override insurance_carrier_id=ic_212 -> snapshot | Aetna carrier search | In scope: Aetna carrier. Out of scope: Aetna specific plans |
| 22 | | MatchesForParameter("elect") | insurance ic_300/ip_2229 | Override carrier+plan -> snapshot | Elect plan search | In scope: carrier+plan pair. Out of scope: carrier-only |
| 23 | | MatchesForParameter("location") | location_id=lo_oHFqVVUGB0GmW3yitFeFPh | Override location_id -> snapshot | Explicit location-id search | In scope: location_id path. Out of scope: coordinate/zip paths |
| 24 | | MatchesForParameter("practice") — **Ignored** (MarketplaceSearchPracticeAlgoContainer.Algorithm needs implementation) | practice_id=3201 search | Override location/practice_id/specialty/procedure -> snapshot | Practice-id search (not yet implemented) | In scope: practice algo once implemented. Out of scope: currently disabled |
| 25 | | MatchesForParameter("facets") | facets=hospital_affiliations | Override facets=hospital_affiliations -> snapshot | Hospital-affiliations facet | In scope: hospital_affiliations facet. Out of scope: filter |
| 26 | | MatchesForParameter("filters") | filter=hospital_affiliations:b64_VGhlIE1vdW50IFNpbmFpIEhvc3BpdGFs | Override filter -> snapshot | Hospital-affiliations filter | In scope: Mount Sinai filter. Out of scope: facet-only |
| 27 | | MatchesForParameter("maxPageSize") | page_size=50 | Override page_size=50 -> snapshot | Max page size | In scope: page_size=50 limit. Out of scope: page_size>50 |
| 28 | | MatchesForParameter("excluded") | excluded_specialty_ids=104,105 | Override excluded_specialty_ids -> snapshot | Excluded specialties | In scope: exclusion-only path. Out of scope: include+exclude combo |
| 29 | | MatchesForParameter("excludedAndIncluded") | excluded 102,104,105 with specialty 153 | Override excluded+specialty -> snapshot | Include+exclude combination | In scope: combined include/exclude. Out of scope: exclusion-only |
| 30 | | MatchesForParameter("averageWaitTime") | rank_by=WaitTimeRating | Override rank_by=WaitTimeRating -> snapshot | Wait-time ranker | In scope: WaitTimeRating ranker. Out of scope: Default ranker |
| 31 | | MatchesForParameter("stupidZipCode") | zip_code="hello!" | Override zip_code=hello! -> snapshot | Invalid zip handling | In scope: bad-zip fallback. Out of scope: other malformed inputs |
| 32 | | MatchesForParameter("boxLocation") | Bounding-box location "40.750,-74.000:40.740,-73.900" | Override location to bbox -> snapshot | Bounding-box search | In scope: bbox geo. Out of scope: point-radius |
| 33 | | MatchesForParameter("legacyWhitelabel") | flavor=legacy-whitelabel | Override flavor=legacy-whitelabel -> snapshot | Legacy whitelabel flavor | In scope: legacy-whitelabel routing. Out of scope: modern whitelabel |
| 34 | | MatchesForParameter("page0") | page=0 page_size=10 | Override pagination -> snapshot | First page | In scope: page 0 baseline. Out of scope: deep pages |
| 35 | | MatchesForParameter("page1") | page=1 page_size=10 | Override pagination -> snapshot | Second page default size | In scope: page 1 default size. Out of scope: custom size |
| 36 | | MatchesForParameter("page1CustomSize") | page=1 page_size=15 | Override pagination -> snapshot | Second page custom size | In scope: non-default page_size. Out of scope: page 0 |
| 37 | | MatchesForParameter("specialtyString") | specialty_id=sp_98 (string form) | Override specialty_id=sp_98 -> snapshot | Stringy specialty id parsing | In scope: sp_* form. Out of scope: numeric form |
| 38 | | MatchesForParameter("placemark") | location_type=placemark NYC | Override location/city/state/location_type -> snapshot | Placemark location type | In scope: placemark. Out of scope: seo_placemark |
| 39 | | MatchesForParameter("seoPlacemark") | location_type=seo_placemark NYC | Override location/city/state/location_type -> snapshot | SEO placemark type | In scope: seo_placemark. Out of scope: plain placemark |

## PlacemarkRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | CorrectlyUpdatesESQueryForPlacemarkSearch | ES query shape when location_type=placemark in NYC | Setup Full-debug request with placemark, NYC -> Apply ES7 override -> ValidateSnapshot | Placemark ES-query snapshot | In scope: placemark ES query. Out of scope: seo_placemark |
| 2 | | OnlyHasNYCDoctorsForANYNYPlacemarkSearch | NY placemark search returns only NYC doctors (page_size=100) | Setup Summary-debug request with placemark NYC page_size=100 -> Apply ES7 override -> ValidateSnapshot | NY placemark geography tight | In scope: NY placemark geographic scoping. Out of scope: other states |

## PostEndpointTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | PostEndpoint_WithBodyParams_ShouldReturnResults | POST /provider-locations accepts sensitive search_query/fts_search_query/ce_search_query in body | Build query string (location/specialty/rank_by/caller_type/page_size) -> POST with JSON body containing the three sensitive fields -> Assert success + provider_locations + total_hits present | POST endpoint accepts body params | In scope: body-param routing + response shape. Out of scope: logging-redaction verification |
| 2 | | PostEndpoint_WithEmptyBody_ShouldStillWork | POST with empty JSON body still returns success | Setup query-only request with Default ranker + search caller_type -> POST with body "{}" -> Assert success | Empty body falls back to query params | In scope: empty-body path. Out of scope: missing Content-Type |
| 3 | | PostEndpoint_WithPartialBody_ShouldApplyProvidedFields | POST with only fts_search_query in body | Setup ScoreFusion aisearch query -> POST with body containing only fts_search_query -> Assert success | Partial-body merging works | In scope: partial body. Out of scope: conflicting body-vs-query fields |

## ScopedRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ReturnsVirtualProvLocsUsingMarketplaceVirtualVisitAlgo | visit_type=virtualVisit routes to marketplace-virtual-visit algo | Setup request visit_type=virtualVisit -> Apply ES7 override -> ValidateSnapshot | Virtual-only routing | In scope: virtualVisit routing. Out of scope: in-person |
| 2 | | DoesNotReturnAnyVirtualProvlocWhenVisitTypeIsInPersonVisit | visit_type=inPersonVisit excludes virtual provlocs | Setup request visit_type=inPersonVisit -> Apply ES7 override -> ValidateSnapshot | In-person-only excludes virtual | In scope: inPersonVisit filter. Out of scope: mixed |
| 3 | | VerifiesInPersonAndVirtualVisitsReturnsVirtualAndInPersonProviderLocations | visit_type=inPersonAndVirtualVisits returns both | Setup request visit_type=inPersonAndVirtualVisits -> Apply ES7 override -> ValidateSnapshot | Mixed visit-type returns both | In scope: mixed visit_type. Out of scope: single-modal |

## SearchCountRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ShouldReturnCorrectResponseWithTotalCountOfProvLocs — **Ignored** (Count endpoint /search/v1/.../provider-locations/count does not exist in C# implementation) | GET /provider-locations/count returns total provloc count | Build query string from basic request -> GET count endpoint with X-ZD-WebRequest-Id -> Snapshot response | Count endpoint snapshot (disabled) | In scope: once endpoint is implemented. Out of scope: currently not implemented in C# |
| 2 | | ShouldReturnCorrectResponseWithTotalCountOf0WhenNoProvLocsExist — **Ignored** (Count endpoint /search/v1/.../provider-locations/count does not exist in C# implementation) | Count endpoint returns 0 when location has no provlocs | Build request with location="0,-1" (ocean) -> GET count -> Snapshot | Zero-count snapshot (disabled) | In scope: once endpoint is implemented. Out of scope: currently not implemented in C# |

## SpoRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ShouldReturnSpoAdDecisionsOnlyWhenInsuranceProgramTypeNameIsSet | SPO ad decisions appear only when insurance program type name is set (maple_v21) | Setup Full-debug request -> Apply ES7 + YASS_Maple_V21_vs_V22=maple_v21 + X-ZD-Tracking-Id -> ValidateSnapshot | SPO gating by insurance program type | In scope: SPO-with-insurance branch. Out of scope: SPO-without-insurance |
| 2 | | ShouldWorkOnTestDirectory | SPO works end-to-end against test directory -2 | Setup Full-debug request -> Apply ES7 + maple_v21 + tracking id -> If smoke: CallDebuggableSearch(-2) and assert HTTP 200 -> Otherwise: load snapshot searchRequestId, call against dir -2, save-or-assert snapshot | SPO flow on test dir -2 | In scope: SPO on directory -2. Out of scope: production directories |

## UnsuccessfulRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | MatchesForBadRequest("procedureWithoutSpecialty") | procedure_id=75 with no specialty_id | Override procedure_id=75 -> CallDebuggableSearch (or capture HTTP/exception error) -> AssertSnapshotsMatch | Procedure requires specialty | In scope: missing-specialty validation. Out of scope: other combos |
| 2 | | MatchesForBadRequest("negativeDistanceRadius") — **Ignored** (Non-deterministic ES query structure causing error message differences) | distance_radius_miles=-1 | Override distance_radius_miles=-1 -> capture error -> snapshot | Negative distance radius handling (flaky) | In scope: once ES error is deterministic. Out of scope: currently disabled |
| 3 | | MatchesForBadRequest("negativeDistanceBand") | distance_band_size=-1 | Override distance_band_size=-1 -> snapshot error | Negative distance band rejection | In scope: distance_band_size validation. Out of scope: positive values |
| 4 | | MatchesForBadRequest("negativePage") | page=-1 | Override page=-1 -> snapshot error | Negative page rejected | In scope: page < 0. Out of scope: large page |
| 5 | | MatchesForBadRequest("bigPage") | page_size=151 exceeds cap | Override page_size=151 -> snapshot error | Over-cap page_size | In scope: page_size > 150. Out of scope: page_size <= 150 |
| 6 | | MatchesForBadRequest("noLocation") | location="" (removed) | Remove location override -> snapshot error | Missing location rejection | In scope: missing location. Out of scope: malformed location |
| 7 | | MatchesForBadRequest("coordLatTooSmall") | location="-90.001,0" | Override location -> snapshot error | Latitude < -90 | In scope: lat out of range. Out of scope: lon |
| 8 | | MatchesForBadRequest("coordLatTooLarge") | location="90.001,0" | Override location -> snapshot error | Latitude > 90 | In scope: lat > 90. Out of scope: lon |
| 9 | | MatchesForBadRequest("coordLonTooSmall") | location="0,-180.001" | Override location -> snapshot error | Longitude < -180 | In scope: lon < -180. Out of scope: lat |
| 10 | | MatchesForBadRequest("coordLonTooLarge") | location="0,180.001" | Override location -> snapshot error | Longitude > 180 | In scope: lon > 180. Out of scope: lat |
| 11 | | MatchesForBadRequest("boxLatTooSmall") | bbox with latitude < -90 | Override location to "0,1:-90.001,0" -> snapshot error | Bbox lat out of range (low) | In scope: bbox lat validation. Out of scope: point validation |
| 12 | | MatchesForBadRequest("boxLatTooLarge") | bbox with latitude > 90 | Override location to "0,1:90.001,0" -> snapshot error | Bbox lat out of range (high) | In scope: bbox lat validation. Out of scope: point validation |
| 13 | | MatchesForBadRequest("boxLonTooSmall") | bbox with longitude < -180 | Override location to "1,0:0,-180.001" -> snapshot error | Bbox lon out of range (low) | In scope: bbox lon validation. Out of scope: point validation |
| 14 | | MatchesForBadRequest("boxLonTooLarge") | bbox with longitude > 180 | Override location to "1,0:0,180.001" -> snapshot error | Bbox lon out of range (high) | In scope: bbox lon validation. Out of scope: point validation |
| 15 | | MatchesForBadRequest("malformedFilter") | filter refers to non-existent facet | Override filter=not_in_facet_list:foo -> snapshot error | Unknown-facet filter rejected | In scope: unknown-facet filter. Out of scope: valid facets |
| 16 | | MatchesForBadRequest("malformedSpecialty") | specialty_id with quote injection | Override specialty_id=sp_75' -> snapshot error | Malformed specialty id | In scope: bad-specialty-id format. Out of scope: unknown-but-valid ids |
| 17 | | MatchesForBadRequest("negativeLimit") | limit=-1 | Override limit=-1 -> snapshot error | Negative limit rejected | In scope: negative limit. Out of scope: offset |
| 18 | | MatchesForBadRequest("negativeOffset") | offset=-1 | Override offset=-1 -> snapshot error | Negative offset rejected | In scope: negative offset. Out of scope: limit |
| 19 | | MatchesForBadRequest("bigLimit") | offset=1 limit=151 | Override offset/limit -> snapshot error | Limit > 150 rejected | In scope: limit cap. Out of scope: offset cap |
| 20 | | MatchesForBadRequest("bigOffset") | offset=1500 limit=150 | Override offset/limit -> snapshot error | Offset too large | In scope: offset cap. Out of scope: limit cap |
| 21 | | MatchesForBadRequest("missingLimit") | offset without limit | Override offset=17 -> snapshot error | Limit is required alongside offset | In scope: limit-required validation. Out of scope: offset-required validation |
| 22 | | MatchesForBadRequest("missingOffset") | limit without offset | Override limit=20 -> snapshot error | Offset is required alongside limit | In scope: offset-required validation. Out of scope: limit-required validation |

## VoyageTests.cs

_Note: entire fixture is `[Explicit]` — only runs when explicitly requested._

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | GetEmbeddingAsync_WithValidQuery_ReturnsEmbedding | Voyage-4 returns 1024-dim non-zero embedding for a valid query | Instantiate VoyageEmbeddingService (input=query) -> GetEmbeddingAsync("dentist near me") -> Assert non-null, length==1024, at least one non-zero dimension | Voyage-4 happy path | In scope: Voyage-4 query embedding shape. Out of scope: offline/mock endpoints (requires live SageMaker endpoint + AWS creds) |
| 2 | | GetEmbeddingAsync_WithDifferentQueries_ReturnsDifferentEmbeddings | Semantically different queries produce cosine similarity < 0.9 | Embed "dentist for tooth pain" and "cardiologist heart checkup" -> Assert both length 1024 -> Compute cosine similarity -> Assert < 0.9 | Different concepts -> lower similarity | In scope: semantic dissimilarity. Out of scope: exact thresholds (requires live SageMaker) |
| 3 | | GetEmbeddingAsync_WithSimilarQueries_ReturnsHighSimilarity | Semantically similar queries produce cosine similarity > 0.7 | Embed "dentist for tooth pain" and "dental doctor for toothache" -> Compute cosine similarity -> Assert > 0.7 | Similar concepts -> higher similarity | In scope: semantic similarity floor. Out of scope: precise scoring (requires live SageMaker) |
| 4 | | GetEmbeddingAsync_WithDocumentInputType_Works | input_type="document" path succeeds with 1024-dim output | Construct VoyageEmbeddingService with inputType=document -> Embed long doctor bio -> Assert length 1024 | Document input type supported | In scope: document input type. Out of scope: quality (requires live SageMaker) |
| 5 | | GetEmbeddingAsync_WithLongQuery_Succeeds | Long (50x repeated) query still returns 1024-dim embedding | Build long query by repeating a sentence 50x -> Embed -> Assert length 1024 | Long inputs handled natively | In scope: long-input handling. Out of scope: token-count limits (requires live SageMaker) |
| 6 | | GetEmbeddingAsync_WithSpecialCharacters_HandlesCorrectly | Query with punctuation/special chars returns valid 1024-dim embedding | Embed "dentist for: pain, swelling, & bleeding (urgent!)" -> Assert length 1024 | Special-character robustness | In scope: punctuation tolerance. Out of scope: emoji/markdown (requires live SageMaker) |
| 7 | | GetEmbeddingAsync_WithUnicodeCharacters_HandlesCorrectly | Spanish/unicode query returns 1024-dim embedding | Embed "dentista para dolor de muelas" -> Assert length 1024 | Multilingual input support | In scope: Spanish input. Out of scope: CJK scripts (requires live SageMaker) |
| 8 | | GetEmbeddingAsync_MultilingualSimilarity_Works | English and Spanish of same concept produce cosine similarity > 0.6 | Embed "dentist for tooth pain" and "dentista para dolor de muelas" -> Compute cosine similarity -> Assert > 0.6 | Cross-lingual semantic alignment | In scope: EN-ES alignment. Out of scope: other language pairs (requires live SageMaker) |
| 9 | | GetEmbeddingAsync_WithNullQuery_ThrowsArgumentException | null query throws ArgumentException with "cannot be null or empty" message | Call GetEmbeddingAsync(null) -> Assert ArgumentException with expected message | Null guard clause | In scope: null validation. Out of scope: other invalid inputs |
| 10 | | GetEmbeddingAsync_WithEmptyQuery_ThrowsArgumentException | empty string throws ArgumentException | Call GetEmbeddingAsync("") -> Assert ArgumentException with expected message | Empty-string guard clause | In scope: empty-string validation. Out of scope: whitespace-only |
| 11 | | GetEmbeddingAsync_ConcurrentRequests_AllSucceed | 5 concurrent embedding calls all succeed | Build 5 queries -> Task.WhenAll -> Assert 5 results each length 1024 | Concurrency safety | In scope: concurrent calls. Out of scope: throughput measurements (requires live SageMaker) |
| 12 | | GetEmbeddingAsync_PerformanceTest_10Queries | Sequentially embed 10 queries, each must complete < 5s | Sequentially embed 10 specialty queries with Stopwatch -> Print timings -> Assert every call < 5000ms | Per-query latency budget | In scope: sequential latency. Out of scope: cold-start (requires live SageMaker) |

## WarpspeedRequestsTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ShowsResultsForVaccineInsideIL — **Ignored** (Vaccine algorithm (YassJrVaccineAlgoContainer) is not implemented in C#) | Vaccine-search caller_type in Illinois | Setup caller_type=vaccineSearch, Chicago location, rank_by=Default -> ES7 override -> ValidateSnapshot | Vaccine search results (disabled) | In scope: vaccine algo once implemented. Out of scope: currently not implemented in C# |
| 2 | | ShowsNoFacetsEvenIfTheyAreRequestedForVaccineSearch — **Ignored** (Vaccine algorithm (YassJrVaccineAlgoContainer) is not implemented in C#) | Vaccine search suppresses facets even when requested | Setup caller_type=vaccineSearch, Chicago, facets=sex -> ValidateSnapshot | Vaccine facets suppression (disabled) | In scope: vaccine facet-suppression once implemented. Out of scope: currently not implemented in C# |

## WhiteLabelTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | AllowsBasicGphSearch | GPH (Grady Primary Health) whitelabel basic search in Atlanta (dir 963) | Setup Processors-debug request Atlanta procedure 493 specialty 122 -> Apply ES7 + streaming-index -> If smoke: call dir 963 and assert HTTP 200 -> Otherwise: snapshot-driven call with searchRequestId extracted, save-or-assert | GPH whitelabel baseline | In scope: directory 963 routing. Out of scope: other whitelabels |
| 2 | | AllowsBasicSchweigerSearch | Schweiger whitelabel basic search in Manhattan (dir 459) | Setup Manhattan request specialty 101 procedure 84 -> Apply ES7 + streaming-index -> If smoke: call dir 459 and assert HTTP 200 -> Otherwise: snapshot-driven call with searchRequestId extracted, save-or-assert | Schweiger whitelabel baseline | In scope: directory 459 routing. Out of scope: other whitelabels |

## ZeroEntropyTests.cs

_Note: entire fixture is `[Explicit]` — only runs when explicitly requested._

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | ScoreAsync_WithValidQueryAndDocuments_ReturnsScores | zerank-2 returns a valid (non-NaN) score per document | Instantiate ZeroEntropyCrossEncoderService -> ScoreAsync("apple jam steps", 6 docs) -> Assert 6 non-NaN scores | Cross-encoder happy path | In scope: scores-per-doc contract. Out of scope: offline/mock endpoints (requires live SageMaker endpoint + AWS creds) |
| 2 | | ScoreAsync_RelevantDocumentScoresHigher_ThanIrrelevant | Relevant docs outrank irrelevant ones | Build 4 docs (2 relevant, 2 irrelevant for "dentist for tooth pain") -> Score -> Assert min(relevant) > max(irrelevant) | Relevance-ordering invariant | In scope: relevance ranking. Out of scope: exact margins (requires live SageMaker) |
| 3 | | ScoreAsync_WithSingleDocument_ReturnsOneScore | Single-doc scoring returns exactly one score | Score "dentist near me" against 1 document -> Assert 1 score | Single-doc path | In scope: array-of-one behavior. Out of scope: zero-doc (see other test) |
| 4 | | ScoreAsync_WithManyDocuments_ScalesCorrectly | 20-doc scoring returns 20 scores and prints top-5 ranking | Build 20 docs (alternating relevant/irrelevant for "cardiologist") -> Score -> Assert 20 scores -> Print inference ms + top 5 | Mid-size batch scales | In scope: 20-doc batch. Out of scope: >1000 docs (covered by dedicated test) |
| 5 | | ScoreAsync_WithSpecialCharacters_HandlesCorrectly | Query with punctuation scores matching doc higher | Score "dentist for: pain, swelling, & bleeding (urgent!)" against 2 docs -> Assert matching doc scored higher | Special-char tolerance | In scope: punctuation queries. Out of scope: emoji (requires live SageMaker) |
| 6 | | ScoreAsync_WithLongDocument_Succeeds | Long (20x repeated) document scored alongside a short one | Build long repeated doc + short unrelated doc -> Score -> Assert 2 scores -> Print both | Long-document robustness | In scope: long-doc handling. Out of scope: token-cap behavior (requires live SageMaker) |
| 7 | | ScoreAsync_WithNullQuery_ThrowsArgumentException | null query throws ArgumentException | Call ScoreAsync(null, docs) -> Assert ArgumentException with expected message | Null-query guard | In scope: null validation. Out of scope: other nulls |
| 8 | | ScoreAsync_WithEmptyQuery_ThrowsArgumentException | Empty query throws ArgumentException | Call ScoreAsync("", docs) -> Assert ArgumentException | Empty-query guard | In scope: empty-string validation. Out of scope: whitespace-only |
| 9 | | ScoreAsync_WithNullDocuments_ThrowsArgumentException | null documents array throws ArgumentException | Call ScoreAsync("dentist", null) -> Assert ArgumentException | Null-docs guard | In scope: null-docs validation. Out of scope: null elements within array |
| 10 | | ScoreAsync_WithEmptyDocuments_ThrowsArgumentException | Empty documents array throws ArgumentException | Call ScoreAsync("dentist", Array.Empty<string>()) -> Assert ArgumentException | Empty-docs guard | In scope: empty-array validation. Out of scope: single-empty-string element |
| 11 | | ScoreAsync_ConcurrentRequests_AllSucceed | 3 concurrent ScoreAsync calls all succeed and return 2 scores each | Build 3 (query, docs) tuples -> Task.WhenAll -> Assert 3 results each with 2 scores | Concurrency safety | In scope: concurrent scoring. Out of scope: throughput |
| 12 | | ScoreAsync_PerformanceTest_VariousDocumentCounts | Measure latency for doc counts 1/5/10/20/50 | For each count: build docs, Stopwatch ScoreAsync, assert expected score count -> Print table | Latency-by-batch-size benchmark | In scope: latency reporting. Out of scope: SLA gates (requires live SageMaker) |
| 13 | | ScoreAsync_ReturnsModelInfo | Returned result.Model=="zerank-2" and InferenceMs > 0 | Score trivial query/doc -> Assert result.Model=="zerank-2" and InferenceMs > 0 | Response metadata contract | In scope: model id + timing. Out of scope: payload contents |
| 14 | | ScoreAsync_With1000Documents_Succeeds | 1000-doc batch succeeds across 3 iterations | Build 1000 docs (cycled from 5 templates) -> Run 3 iterations with Stopwatch -> Assert 1000 scores each iteration | Large-batch robustness | In scope: 1000-doc scoring. Out of scope: >1000 batches (requires live SageMaker) |

# Search/Datalake

## FirehoseIntegrationTests.cs

| # | Do we need these? | Test Name | What It Tests | Steps | Summary | Scope |
|---|-------------------|-----------|---------------|-------|---------|-------|
| 1 | | LogAsync_SearchLog_SuccessfullyPutsRecord | FirehoseService.LogAsync puts a SearchLog record to the LocalStack Firehose stream | If LocalStack unavailable Assert.Ignore -> Arrange SearchLog (AlgoName, Count, Scorer, ResultName, Headers) -> Call LogAsync -> Assert.Pass if no exception | SearchLog round-trip to Firehose | In scope: LocalStack Firehose PutRecord for SearchLog. Out of scope: runs only when LocalStack is up (docker compose up localstack) |
| 2 | | LogAsync_ScoringAuditLog_SuccessfullyPutsRecord | FirehoseService.LogAsync puts a ScoringAuditLog record with ProvLocFeatureScores | If LocalStack unavailable Assert.Ignore -> Arrange ScoringAuditLog (Scorer, ProvLocFeatureScores with ProviderId/LocationId/Score/FeatureVector) -> Call LogAsync -> Assert.Pass if no exception | ScoringAuditLog round-trip to Firehose | In scope: LocalStack Firehose PutRecord for ScoringAuditLog. Out of scope: runs only when LocalStack is up |
| 3 | | LogBatchAsync_MultipleRecords_SuccessfullyPutsBatch | FirehoseService.LogBatchAsync puts 3 SearchLog records in a batch | If LocalStack unavailable Assert.Ignore -> Arrange 3 SearchLog entries -> Call LogBatchAsync -> Assert.Pass if no exception | Firehose batch put | In scope: LocalStack Firehose PutRecordBatch. Out of scope: runs only when LocalStack is up |
| 4 | | IsEnabled_ReturnsTrue_WhenConfiguredCorrectly | FirehoseService.IsEnabled is true when Enabled=true is configured | If LocalStack unavailable Assert.Ignore -> Assert _firehoseService.IsEnabled is true | Enabled-flag plumbing | In scope: IsEnabled property. Out of scope: disabled-config path (runs only when LocalStack is up) |
