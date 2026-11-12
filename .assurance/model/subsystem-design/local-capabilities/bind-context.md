# Bind an execution context

## capability-description

### capability

Framework operations and application code can enter a context that exposes the selected application and, for request work, its request and session. Exiting restores the prior binding and invokes teardown. Streaming wrappers let a caller consume generated data while the captured context remains available.

### implementation-mapping

AppContext construction/push/pop implement binding and cleanup; Flask context factories choose application-only or request data. Globals use ContextVar-backed proxies. stream_with_context wraps iteration in the captured context.

### evidence

- [Context](corpus:flask:evidence/d8838a605f9ff504)
- [Globals](corpus:flask:evidence/ref-594a138991de4d96)
- [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-context | [Bind](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Push/pop install and restore active bindings and request matching derives request routing data. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) |
| uses-session | [Bind](#capability-description) | subsystem-design:uses-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | Request contexts retain the opened session mapping and mark access through the session property. | None. | [Session binding](corpus:flask:evidence/d8838a605f9ff504) |
| uses-settings | [Bind](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Adapter creation reads host, server name, application root and scheme choices. | None. | [Adapter](corpus:flask:evidence/d3e0349504081bb5) |
| uses-registrations | [Bind](#capability-description) | subsystem-design:uses-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | Context matching uses the bound application's URL map. | None. | [Matching](corpus:flask:evidence/d8838a605f9ff504) [Adapter](corpus:flask:evidence/d3e0349504081bb5) |
| session-exchange | [Bind](#capability-description) | subsystem-design:participates-in-exchange | [Session load/save](corpus:/subsystem-interfaces/exchanges/session-load-save.md#exchange-behavior) | The context supplies app/request to open_session and receives the mapping or null fallback. | None. | [Opening](corpus:flask:evidence/d8838a605f9ff504) |
| lifecycle-exchange | [Bind](#capability-description) | subsystem-design:participates-in-exchange | [Lifecycle notices](corpus:/subsystem-interfaces/exchanges/lifecycle-notifications.md#exchange-behavior) | Context binding emits push/pop lifecycle notices and initiates teardown notifications. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) |
| domain-context | [Bind](#capability-description) | subsystem-design:contributes-to-required-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Active binding, restoration and preserved iteration supply the current application's contextual data. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| domain-handle | [Bind](#capability-description) | subsystem-design:contributes-to-required-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Request push opens the session and matches the URL before the dispatcher selects behavior. | None. | [push/match_request](corpus:flask:evidence/d8838a605f9ff504) [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| domain-session | [Bind](#capability-description) | subsystem-design:contributes-to-required-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | The request context obtains the backend's current mapping and supplies null fallback when needed. | None. | [_get_session](corpus:flask:evidence/d8838a605f9ff504) |
| domain-commands | [Bind](#capability-description) | subsystem-design:contributes-to-required-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | Application-context entry supplies selected app data for wrapped commands and shell work. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [with_appcontext/shell](corpus:flask:evidence/fed8939d1905b99b) |
| domain-testing | [Bind](#capability-description) | subsystem-design:contributes-to-required-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | Preserved/re-entered contexts and temporary transaction contexts supply the testing API's contextual access. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| domain-observe | [Bind](#capability-description) | subsystem-design:contributes-to-required-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Context send sites report push/pop and teardown events to connected observers. | None. | [Context signal sends](corpus:flask:evidence/d8838a605f9ff504) |
