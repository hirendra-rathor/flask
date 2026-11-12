# Handle a WSGI request

## capability-description

### capability

A WSGI caller supplies request environment and response-start callback to Flask and receives the response body iterable. Flask selects registered hooks, views or error handlers and adapts their results into a response. This offered work establishes response handling within Flask, while network delivery remains with the host.

### implementation-mapping

Flask.__call__ delegates to wsgi_app. That operation enters a context, performs full_dispatch_request, invokes the response as WSGI and pops the context. Preprocessing, dispatch_request, make_response and process_response select application behavior and adapt its output. Class-based view adapters convert registered classes into callable handlers.

### evidence

- [WSGI dispatch](corpus:flask:evidence/d3e0349504081bb5)
- [Class views](corpus:flask:evidence/ref-98249c1107548796)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-registrations | [Handle](#capability-description) | subsystem-design:uses-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | Dispatch selects views and hooks from application registrations. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) |
| uses-context | [Handle](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Request handling uses the context's request, URL result and after-request callbacks. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) |
| uses-session | [Handle](#capability-description) | subsystem-design:uses-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | Response processing obtains the current session and requests saving if it is not null. | None. | [Response](corpus:flask:evidence/d3e0349504081bb5) |
| uses-settings | [Handle](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | The dispatcher and request wrappers read application choices such as debug and request parsing limits. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) [Wrappers](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| wsgi-exchange | [Handle](#capability-description) | subsystem-design:participates-in-exchange | [WSGI request and response](corpus:/subsystem-interfaces/exchanges/wsgi-request-response.md#exchange-behavior) | Flask receives the environment and hands response status, headers and body to the WSGI caller through the response object. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| callback-exchange | [Handle](#capability-description) | subsystem-design:participates-in-exchange | [Handler calls and results](corpus:/subsystem-interfaces/exchanges/handler-invocation.md#exchange-behavior) | Dispatch invokes selected views/hooks and consumes returned response values. | None. | [Handlers](corpus:flask:evidence/d3e0349504081bb5) |
| session-exchange | [Handle](#capability-description) | subsystem-design:participates-in-exchange | [Session load/save](corpus:/subsystem-interfaces/exchanges/session-load-save.md#exchange-behavior) | Response processing supplies application, mapping and response to the configured save_session operation. | None. | [Response](corpus:flask:evidence/d3e0349504081bb5) |
| lifecycle-exchange | [Handle](#capability-description) | subsystem-design:participates-in-exchange | [Lifecycle notices](corpus:/subsystem-interfaces/exchanges/lifecycle-notifications.md#exchange-behavior) | Request handling emits start, finish, exception and teardown notices under their applicable execution paths. | None. | [Signals](corpus:flask:evidence/d3e0349504081bb5) |
| domain-handle | [Handle](#capability-description) | subsystem-design:contributes-to-required-capability | [Handle application requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Selection, handler invocation, result conversion and WSGI response supply the framework request-handling result; transport remains external. | None. | [Dispatch/WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| domain-context | [Handle](#capability-description) | subsystem-design:contributes-to-required-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | The WSGI path enters and releases the request context around application work. | None. | [wsgi_app](corpus:flask:evidence/d3e0349504081bb5) |
| domain-session | [Handle](#capability-description) | subsystem-design:contributes-to-required-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Response processing asks the configured backend to save a non-null current session into the response. | None. | [process_response](corpus:flask:evidence/d3e0349504081bb5) |
| domain-observe | [Handle](#capability-description) | subsystem-design:contributes-to-required-capability | [Observe framework events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Request lifecycle send sites supply notices and event values to connected observers. | None. | [Request signal sends](corpus:flask:evidence/d3e0349504081bb5) |
