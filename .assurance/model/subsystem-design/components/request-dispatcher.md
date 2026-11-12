# Request dispatcher

## role-and-implementation

### role-kind

internal

### role

The dispatcher accepts a WSGI invocation, selects registered application behavior, and converts its result into a response for the WSGI caller. It invokes request hooks and error handlers and requests session saving during response processing. Class-based view adapters participate in selecting application methods; they remain part of this dispatch job.

### implementation-mapping

`Flask.wsgi_app`, `full_dispatch_request`, `dispatch_request`, `make_response`, and `process_response` implement dispatch and response adaptation. `View.as_view` and `MethodView.dispatch_request` adapt class-based views. Request/response subclasses integrate Werkzeug HTTP objects; `ensure_sync` adapts asynchronous callbacks when the required adapter is installed. Logging and debug helpers supply dispatch diagnostics.

### evidence

- [Dispatch](corpus:flask:evidence/d3e0349504081bb5)
- [View adapters](corpus:flask:evidence/ref-98249c1107548796)
- [Wrappers](corpus:flask:evidence/ref-4ace0d7548306bf6)
- [Logging](corpus:flask:evidence/ref-7d6f91d952bb5e04)
- [Debug helpers](corpus:flask:evidence/ref-0082669d1582bc33)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-dispatch | [Dispatcher](#role-and-implementation) | subsystem-design:offers-capability | [Handle request](corpus:/subsystem-design/local-capabilities/handle-request.md#capability-description) | WSGI invocation enters the dispatch and response-processing work. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-context | [Dispatcher](#role-and-implementation) | subsystem-design:delegates-to | [Context manager](corpus:/subsystem-design/components/context-manager.md#role-and-implementation) | WSGI handling constructs, pushes and pops AppContext. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-session | [Dispatcher](#role-and-implementation) | subsystem-design:delegates-to | [Session backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | Response processing requests saving from the configured SessionInterface for a non-null session. | None. | [Response processing](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-json | [Dispatcher](#role-and-implementation) | subsystem-design:delegates-to | [JSON provider](corpus:/subsystem-design/components/json-provider.md#role-and-implementation) | Dictionary and list view results are passed to the application's JSON provider for response creation. | None. | [Response conversion](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-static-response | [Dispatcher](#role-and-implementation) | subsystem-design:delegates-to | [Application helpers](corpus:/subsystem-design/components/application-helpers.md#role-and-implementation) | The automatically registered application static route binds dispatch to send_static_file and its file-response helpers. This claim concerns that built-in handler rather than arbitrary application callbacks. | None. | [Static route and dispatch](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-http | [Dispatcher](#role-and-implementation) | subsystem-design:delegates-to | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | Request/response subclasses use Werkzeug HTTP behavior and the response is invoked as WSGI. | None. | [Wrappers](corpus:flask:evidence/ref-4ace0d7548306bf6) [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-signals | [Dispatcher](#role-and-implementation) | subsystem-design:delegates-to | [Signal delivery](corpus:/subsystem-design/components/signal-delivery.md#role-and-implementation) | Dispatch and teardown send lifecycle signals through Blinker signal objects. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) |
| belongs-coordinator | [Dispatcher](#role-and-implementation) | subsystem-design:belongs-to-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | WSGI dispatch and response adaptation implement the coordinator's request-facing responsibility while application handler results remain outside it. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) |
