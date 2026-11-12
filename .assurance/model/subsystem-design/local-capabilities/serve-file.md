# Construct a file response

## capability-description

### capability

Application code can request a response for a file or a path within a selected directory. Application and blueprint static routes offer the same file-serving work for their configured static directories. Flask supplies its request environment, response class and application file-delivery choices to Werkzeug.

### implementation-mapping

send_file and send_from_directory forward to Werkzeug utilities after _prepare_send_file_kwargs supplies application context. Flask.send_static_file and Blueprint.send_static_file select their static folder and cache age. The response remains subject to WSGI host delivery.

### evidence

- [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [Application static response](corpus:flask:evidence/d3e0349504081bb5)
- [Blueprint adapter](corpus:flask:evidence/ref-30595964c383760a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-context | [File response](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Helpers pass the active request environment and application's response class/root to Werkzeug. | None. | [Helper arguments](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| uses-settings | [File response](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | File preparation reads USE_X_SENDFILE and the application's cache-age selector. | None. | [Helper preparation](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) [Cache age](corpus:flask:evidence/d3e0349504081bb5) |
| helper-exchange | [File response](#capability-description) | subsystem-design:participates-in-exchange | [Helper requests/results](corpus:/subsystem-interfaces/exchanges/helper-requests-results.md#exchange-behavior) | File helpers receive file/path options and return the adapted response to application callers. | None. | [File helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| domain-files | [File response](#capability-description) | subsystem-design:contributes-to-required-capability | [Produce file responses](corpus:/domain/required-capabilities/serve-file.md#capability-description) | Request/application adaptation and toolkit calls construct the selected file response. | None. | [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| domain-handle-static | [File response](#capability-description) | subsystem-design:contributes-to-required-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Application/blueprint static-route callbacks supply a file response for matched static requests. | None. | [Application static binding](corpus:flask:evidence/d3e0349504081bb5) [Blueprint static binding](corpus:flask:evidence/ref-30595964c383760a) |
