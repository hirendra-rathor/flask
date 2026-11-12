# Context manager

## role-and-implementation

### role-kind

internal

### role

The context manager makes an application and optional request available to framework work and application callbacks, then restores the prior context when work exits. For request contexts it obtains the session and URL match. It also supports explicit contexts, context copying, and preserving bindings during streamed responses.

### implementation-mapping

`AppContext` constructs and binds context data, performs URL matching, and coordinates teardown. `_cv_app` and the public proxies in `globals` expose the active binding. `stream_with_context` re-enters the captured context while yielding application data.

### evidence

- [Context](corpus:flask:evidence/d8838a605f9ff504)
- [Proxies](corpus:flask:evidence/ref-594a138991de4d96)
- [Streaming wrapper](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-context | [Manager](#role-and-implementation) | subsystem-design:offers-capability | [Bind context](corpus:/subsystem-design/local-capabilities/bind-context.md#capability-description) | AppContext and context wrappers make bindings available for bounded work. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) |
| maintains-context | [Manager](#role-and-implementation) | subsystem-design:maintains-state | [Execution context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Context creation, push, URL matching and pop create, derive and replace the active bindings. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) |
| marks-session-access | [Manager](#role-and-implementation) | subsystem-design:maintains-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | The session property sets the mapping's accessed marker; it does not claim responsibility for arbitrary application session values. | None. | [Session property](corpus:flask:evidence/d8838a605f9ff504) |
| delegates-session | [Manager](#role-and-implementation) | subsystem-design:delegates-to | [Session backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | A request context asks SessionInterface to open its session, with null fallback. | None. | [Session access](corpus:flask:evidence/d8838a605f9ff504) |
| delegates-routing | [Manager](#role-and-implementation) | subsystem-design:delegates-to | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | Context URL matching asks the bound map adapter for a rule and arguments. | None. | [Matching](corpus:flask:evidence/d8838a605f9ff504) |
| delegates-teardown | [Manager](#role-and-implementation) | subsystem-design:delegates-to | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | Context pop requests application teardown hooks; this direction does not imply containment. | None. | [Pop](corpus:flask:evidence/d8838a605f9ff504) |
| delegates-signals | [Manager](#role-and-implementation) | subsystem-design:delegates-to | [Signal delivery](corpus:/subsystem-design/components/signal-delivery.md#role-and-implementation) | Context push/pop send application-context notifications. | None. | [Context signals](corpus:flask:evidence/d8838a605f9ff504) |
| belongs-coordinator | [Context manager](#role-and-implementation) | subsystem-design:belongs-to-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Binding active execution data and arranging teardown belong to framework application coordination. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) |
