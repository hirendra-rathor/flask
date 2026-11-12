# WSGI request and response

## exchange-behavior

### exchange-description

The WSGI invocation supplies a request environment and a response-start callback. Flask returns the response body iterable after its response object uses the supplied environment/callback. For context-preserving debug/test callers, Flask can also pass the completed request's context to the preservation callback supplied in the environment.

### sender-and-receiver

The WSGI host, middleware or test client sends the environment and start_response to Flask. Flask's response supplies status/headers through that callback and body iteration to the caller. If werkzeug.debug.preserve_context is present, Flask sends its AppContext to that callback before popping it.

### implementation-mapping

Flask.__call__ forwards to wsgi_app, which constructs the request context, dispatches, invokes response(environ, start_response), and optionally calls the preservation hook. FlaskClient installs its context-collection callback when preserving context.

### evidence

- [WSGI and preservation](corpus:flask:evidence/d3e0349504081bb5)
- [Client hook](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-wsgi | [Request/response](#exchange-behavior) | subsystem-interfaces:uses-interface | [WSGI](corpus:/subsystem-interfaces/interfaces/wsgi-service.md#interface-definition) | The exchange uses the WSGI application callable and response-start contract. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| carries-preserved-context | [Request/response](#exchange-behavior) | subsystem-interfaces:carries-state | [Execution context](corpus:/state-management/state-elements/execution-context.md#state-definition) | When the environment supplies the preservation callback, Flask passes the current AppContext object to it. This does not imply that normal WSGI response bodies expose context bindings. | None. | [Preservation](corpus:flask:evidence/d3e0349504081bb5) |
| carries-session-cookie | [Request/response](#exchange-behavior) | subsystem-interfaces:carries-state | [Client session](corpus:/state-management/state-elements/client-session.md#state-definition) | With the default session backend, incoming request cookies and outgoing response cookie headers carry the encoded session portion; the host transports these HTTP fields. | None. | [Cookie operations](corpus:flask:evidence/be4c249245e3745e) [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| concept-request | [WSGI](#exchange-behavior) | subsystem-interfaces:carries-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The caller supplies the web request as its environment data. | None. | [wsgi_app](corpus:flask:evidence/d3e0349504081bb5) |
| concept-response | [WSGI](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | The response supplies status/headers via start_response and body iteration to the host; this is not proof of delivery. | None. | [Response WSGI invocation](corpus:flask:evidence/d3e0349504081bb5) |
| concept-context | [WSGI](#exchange-behavior) | subsystem-interfaces:carries-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Only when a preservation callback is present does Flask pass the current context object to that caller-supplied hook. | None. | [Preservation callback](corpus:flask:evidence/d3e0349504081bb5) |
| concept-session | [WSGI](#exchange-behavior) | subsystem-interfaces:carries-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | With the default backend, request/response cookie fields carry the signed session representation through the host. | None. | [Cookies](corpus:flask:evidence/be4c249245e3745e) [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
