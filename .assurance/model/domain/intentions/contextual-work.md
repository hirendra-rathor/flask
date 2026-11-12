# I want current application data available during contextual work

## intended-outcome

### desired-outcome

Application authors should be able to use the selected application's data during requests, explicit context blocks, application commands and preserved streaming work. Request and session access should identify that work's request when one is bound, while application-only work can use the application and temporary namespace.

### evidence

- [Contexts](corpus:flask:evidence/d8838a605f9ff504)
- [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [Commands](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-context | [Context aim](#intended-outcome) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Active bindings make the selected data available for the bounded work lifetime. | None. | [Push/pop/properties](corpus:flask:evidence/d8838a605f9ff504) |
| concerns-application | [Context aim](#intended-outcome) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The active application is available for application-only as well as request work. | None. | [AppContext/proxies](corpus:flask:evidence/d8838a605f9ff504) [Globals](corpus:flask:evidence/ref-594a138991de4d96) |
| concerns-request | [Context aim](#intended-outcome) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | A request context exposes its current request, including when preserved for streaming. | None. | [Request property](corpus:flask:evidence/d8838a605f9ff504) [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-session | [Context aim](#intended-outcome) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Request-bound work obtains that request's opened session mapping. | None. | [Session access](corpus:flask:evidence/d8838a605f9ff504) |
