# Application JSON provider API

## interface-definition

### interface-kind

API

### process-locality

- in-process

### purpose-and-boundary

The application's JSON provider exposes conversion between application values and JSON representations and construction of JSON responses. Framework consumers call this boundary so replacement providers can change the conversion policy without changing request or response dispatch.

### providers-and-consumers

The Flask JSON provider supplies default conversion work, while application/extension code can provide a replacement. The application coordinator, template integrator and testing tools consume it, and public JSON helpers expose it to application code. Python JSON library calls belong inside the default provider's implementation mapping.

### evidence

- [Provider contract](corpus:flask:evidence/c2956553392ff9ef)
- [Application consumers](corpus:flask:evidence/d3e0349504081bb5)
- [Request binding](corpus:flask:evidence/d8838a605f9ff504)
- [Testing consumer](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-json | [JSON API](#interface-definition) | subsystem-interfaces:binds-provider | [JSON provider](corpus:/architecture/architectural-participants/json-provider.md#role-and-scope) | The default provider supplies conversion and JSON response construction. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| provider-application | [JSON API](#interface-definition) | subsystem-interfaces:binds-provider | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | Applications selecting a replacement provider supply conversion through the same contract; the replacement's implementation is outside this account. | None. | [Provider binding](corpus:flask:evidence/c57b8f34cffef994) [Contract](corpus:flask:evidence/c2956553392ff9ef) |
| consumer-coordinator | [JSON API](#interface-definition) | subsystem-interfaces:binds-consumer | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Request construction assigns its JSON module and response conversion asks the selected provider to handle list/dict results. | None. | [Request](corpus:flask:evidence/d8838a605f9ff504) [Response](corpus:flask:evidence/d3e0349504081bb5) |
| consumer-templates | [JSON API](#interface-definition) | subsystem-interfaces:binds-consumer | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | The environment's json.dumps_function policy is bound to the application's provider. | None. | [Policy binding](corpus:flask:evidence/d3e0349504081bb5) |
| consumer-testing | [JSON API](#interface-definition) | subsystem-interfaces:binds-consumer | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | EnvironBuilder delegates JSON encoding and test responses receive the selected JSON module. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| consumer-application | [JSON API](#interface-definition) | subsystem-interfaces:binds-consumer | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | The public dumps/loads/jsonify contract offers application callers the current provider's conversion/response work; context-free dumps/loads can use Python JSON instead. | None. | [Public API](corpus:flask:evidence/d130c1228070cc92) |
