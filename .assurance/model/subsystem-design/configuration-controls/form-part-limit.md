# Multipart form part limit

## configuration-description

### configuration

MAX_FORM_PARTS selects the maximum multipart field count exposed by Flask's Request wrapper. The max_form_parts property permits a request-specific choice.

### usage-and-effect

Request.max_form_parts reads its override or the active application's setting and otherwise uses the Werkzeug base. The property supplies the value for inherited request parsing; the external parser implementation is outside the retained evidence.

### evidence

- [Part limit](corpus:flask:evidence/ref-4ace0d7548306bf6)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-dispatch | [Part limit](#configuration-description) | subsystem-design:used-by-component | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | Flask's request wrapper binds this count limit. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| used-toolkit | [Part limit](#configuration-description) | subsystem-design:used-by-component | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | The subclass exposes this value to inherited request parsing. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| qualifies-request | [Part limit](#configuration-description) | subsystem-design:qualifies-capability | [Handle request](corpus:/subsystem-design/local-capabilities/handle-request.md#capability-description) | Multipart parsing is configured with this part-count limit, with a request override when supplied. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
