# Request and session access MUST require request data in the active context

## rule-definition

### rule-statement

Access through the active context's request or session properties MUST raise an error when that context has no request data. Contextual current-application and temporary-namespace access MUST resolve through an active application binding.

### scope-and-conditions

This constraint concerns Flask's context properties and proxy bindings. An application-only context supports application/g access while lacking request/session data. It does not prohibit application code from retaining explicit object references outside contextual access.

### evidence

- [Request/session property guards](corpus:flask:evidence/d8838a605f9ff504)
- [Proxy bindings](corpus:flask:evidence/ref-594a138991de4d96)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-context | [Access rule](#rule-definition) | domain:protects-intent | [Current data](corpus:/domain/intentions/contextual-work.md#intended-outcome) | Context properties reject unavailable request data rather than substitute an unrelated request/session. | None. | [Context properties](corpus:flask:evidence/d8838a605f9ff504) |
| applies-context | [Access rule](#rule-definition) | domain:applies-to | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Application-only and request contexts differ in which bindings are available. | None. | [has_request/request/session](corpus:flask:evidence/d8838a605f9ff504) |
| applies-request | [Access rule](#rule-definition) | domain:applies-to | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The contextual request property requires the current context's request data. | None. | [request](corpus:flask:evidence/d8838a605f9ff504) |
| applies-session | [Access rule](#rule-definition) | domain:applies-to | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Session property access requires a request context before opening/accessing its mapping. | None. | [_get_session/session](corpus:flask:evidence/d8838a605f9ff504) |
| applies-contextual-work | [Access rule](#rule-definition) | domain:applies-to | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | The exposed data is bounded by the active context's application/request form. | None. | [Properties/proxies](corpus:flask:evidence/d8838a605f9ff504) [Globals](corpus:flask:evidence/ref-594a138991de4d96) |
