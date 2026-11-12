# Use application data during contextual work

## capability-description

### capability

Application authors enter application or request contexts, directly or through framework entry points, to use the selected application and temporary data. Request-bound work can use its request and session, and a streaming wrapper can preserve the captured context during iteration.

### expected-result

Contextual access resolves against the active binding for the work; leaving restores the prior binding and requests teardown. Application-only contexts support work outside HTTP requests without inventing request data.

### evidence

- [Context management](corpus:flask:evidence/d8838a605f9ff504)
- [Globals](corpus:flask:evidence/ref-594a138991de4d96)
- [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [External task context use](corpus:flask:evidence/ref-5bfc195e3435f10b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-context | [Contextual work](#capability-description) | domain:contributes-to-intent | [Current data](corpus:/domain/intentions/contextual-work.md#intended-outcome) | Binding/proxies and preserved iteration make the chosen work's data available for its context lifetime. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-context | [Contextual work](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Enter/exit and captured streaming work create or preserve the active binding. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-application | [Contextual work](#capability-description) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Both application-only and request contexts expose the selected application. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) |
| concerns-request | [Contextual work](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Request data is available only in the request-context form. | None. | [request/has_request](corpus:flask:evidence/d8838a605f9ff504) |
| concerns-session | [Contextual work](#capability-description) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | A request context opens and exposes the request's session mapping. | None. | [_get_session/push](corpus:flask:evidence/d8838a605f9ff504) |
| concerns-notices | [Contextual work](#capability-description) | domain:concerns-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | Context binding and teardown emit their named notices; a notice is separate from application work performed in that context. | None. | [Context sends](corpus:flask:evidence/d8838a605f9ff504) |
