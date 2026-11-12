# Active application context

## concept-definition

### definition

An active application context makes a selected Flask application and a temporary `g` namespace available to contextual work. A request context additionally exposes its current request and session. The binding can exist for an explicit application block, a request, a command or preserved streaming/test work; an application-only context has no request. Context access identifies the work's current application rather than a global application shared by all work.

### evidence

- [Context binding](corpus:flask:evidence/d8838a605f9ff504)
- [Context proxies](corpus:flask:evidence/ref-594a138991de4d96)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| context-application | [Context](#concept-definition) | domain:builds-upon | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Every context binds the application whose contextual work is being performed. | None. | [AppContext](corpus:flask:evidence/d8838a605f9ff504) |
| context-request | [Context](#concept-definition) | domain:builds-upon | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The request-context form adds the current request; this foundation does not apply to application-only contexts. | None. | [Request binding](corpus:flask:evidence/d8838a605f9ff504) |
| context-session | [Context](#concept-definition) | domain:builds-upon | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The request-context form provides the session mapping opened for that request; an application-only context has no session. | None. | [Session property/opening](corpus:flask:evidence/d8838a605f9ff504) |
