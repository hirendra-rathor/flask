# Form field memory limit

## configuration-description

### configuration

MAX_FORM_MEMORY_SIZE selects the size limit exposed for non-file form fields in multipart request bodies. A request's max_form_memory_size property can override the application setting.

### usage-and-effect

Request.max_form_memory_size supplies the per-request or application value to its inherited request implementation. The inspected boundary establishes the parsing-limit binding; Werkzeug parser internals are not examined.

### evidence

- [Form limit](corpus:flask:evidence/ref-4ace0d7548306bf6)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-dispatch | [Field limit](#configuration-description) | subsystem-design:used-by-component | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | Flask's request wrapper reads the field-memory choice. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| used-toolkit | [Field limit](#configuration-description) | subsystem-design:used-by-component | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | The subclass exposes the limit to Werkzeug request parsing behavior. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| qualifies-request | [Field limit](#configuration-description) | subsystem-design:qualifies-capability | [Handle request](corpus:/subsystem-design/local-capabilities/handle-request.md#capability-description) | Multipart field reading receives this configured memory limit or its per-request override. | None. | [Wrapper](corpus:flask:evidence/ref-4ace0d7548306bf6) |
