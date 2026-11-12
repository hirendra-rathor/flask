# Request body size limit

## configuration-description

### configuration

MAX_CONTENT_LENGTH selects the application-level byte limit exposed to request body reading. A request can override its max_content_length property.

### usage-and-effect

Request.max_content_length returns its per-request override or the current application's configured value, falling back to its Werkzeug base when no app is active. Werkzeug performs the request-reading work; the inspected Flask code establishes the value binding, rather than independently validating the external parser.

### evidence

- [Request property](corpus:flask:evidence/ref-4ace0d7548306bf6)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-dispatch | [Body limit](#configuration-description) | subsystem-design:used-by-component | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | The Flask request wrapper supplies this limit for dispatched request access. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| used-toolkit | [Body limit](#configuration-description) | subsystem-design:used-by-component | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | The Request subclass exposes the configured value to inherited Werkzeug request behavior. | None. | [Wrapper contract](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| qualifies-request | [Body limit](#configuration-description) | subsystem-design:qualifies-capability | [Handle request](corpus:/subsystem-design/local-capabilities/handle-request.md#capability-description) | Request body access is configured with this byte limit, subject to a request override. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
