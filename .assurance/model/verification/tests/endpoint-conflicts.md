# Test conflicting endpoint view registration

## verification-approach

### test-kind

component

### test-description

The class-view endpoint-override scenario registers one as_view result, then registers another generated callable using the same endpoint under a different URL. It subsequently invokes the original route through the client.

### intended-focus

The test intends to exercise endpoint-to-view conflicts and the existing endpoint's continued use. The duplicate binding establishes the intended rule target without interpreting the exception/result predicates or promising URL-map rollback.

### evidence

- [Endpoint override](corpus:flask:evidence/bbc49e4202aabab5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| rule | [Approach](#verification-approach) | verification:targets-for-testing | [Endpoint rule](corpus:/domain/domain-rules/endpoint-view-binding.md#rule-definition) | Distinct generated functions are supplied under the same endpoint. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
| route | [Approach](#verification-approach) | verification:targets-for-testing | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | The endpoint-to-view binding is the direct subject. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Register behavior](corpus:/subsystem-design/local-capabilities/register-behavior.md#capability-description) | add_url_rule receives the conflicting view declaration. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [Setup](corpus:/subsystem-design/components/application-setup.md#role-and-implementation) | Endpoint registration is deliberately exercised. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | The intended portion retains endpoint/view setup. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
| api | [Approach](#verification-approach) | verification:targets-for-testing | [Setup API](corpus:/subsystem-interfaces/interfaces/setup-api.md#interface-definition) | Both bindings are submitted through the setup surface. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
| ability | [Approach](#verification-approach) | verification:targets-for-testing | [Compose application](corpus:/domain/required-capabilities/compose-application.md#capability-description) | The intended ability portion is constrained view composition. | None. | [Conflict](corpus:flask:evidence/bbc49e4202aabab5) |
