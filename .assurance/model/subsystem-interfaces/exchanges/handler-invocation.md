# Application handler calls and results

## exchange-behavior

### exchange-description

Flask asks registered application behavior to handle a request or extension point. Views receive matched URL values and return response values; before-request hooks can return an early response; after-request hooks receive/return a response. Error and teardown handlers receive exception information. Template/shell processors return value mappings, URL-default handlers receive mutable URL values, and command callbacks receive parsed command arguments.

### sender-and-receiver

The dispatcher, template context assembly, URL builder or CLI sends the extension point's arguments to the selected application handler. The handler returns the response, mapping, replacement URL or command result appropriate to that contract; teardown/default hooks can act without supplying a result. Their downstream application effects remain outside inspected Flask source.

### implementation-mapping

Flask dispatch/preprocess/process_response/teardown methods invoke stored handlers, using ensure_sync where appropriate. update_template_context and make_shell_context call processors. inject_url_defaults/handle_url_build_error invoke URL callbacks; AppGroup/with_appcontext connect command callbacks to Click.

### evidence

- [Runtime and processor calls](corpus:flask:evidence/d3e0349504081bb5)
- [URL callbacks](corpus:flask:evidence/c57b8f34cffef994)
- [Command calls](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-callbacks | [Calls/results](#exchange-behavior) | subsystem-interfaces:uses-interface | [Callbacks](corpus:/subsystem-interfaces/interfaces/application-callbacks.md#interface-definition) | The family uses Flask's registered application extension points with the stated per-hook arguments/results. | None. | [Calls](corpus:flask:evidence/d3e0349504081bb5) [Commands](corpus:flask:evidence/fed8939d1905b99b) |
| carries-url-match | [Calls/results](#exchange-behavior) | subsystem-interfaces:carries-state | [Execution context](corpus:/state-management/state-elements/execution-context.md#state-definition) | View dispatch sends the request's matched view_args and URL preprocessors receive endpoint/view_args. Other context bindings remain accessible through proxies rather than being wholly passed as arguments. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) |
| concept-route | [Handlers](#exchange-behavior) | subsystem-interfaces:carries-concept | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | View arguments and URL-preprocessor/default arguments communicate matched endpoint and route values under their per-hook contracts. | None. | [Dispatch/preprocess](corpus:flask:evidence/d3e0349504081bb5) [Defaults](corpus:flask:evidence/c57b8f34cffef994) |
| concept-response | [Handlers](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Views/before hooks return response values, and after-request hooks receive and return response objects; not every hook supplies a response. | None. | [Request processing](corpus:flask:evidence/d3e0349504081bb5) |
| concept-url | [Handlers](#exchange-behavior) | subsystem-interfaces:carries-concept | [Endpoint URL](corpus:/domain/domain-concepts/endpoint-url.md#concept-definition) | A URL-build-error handler can return the replacement address consumed by the builder. | None. | [url_for/handle_url_build_error](corpus:flask:evidence/d3e0349504081bb5) [Error-handler contract](corpus:flask:evidence/c57b8f34cffef994) |
| concept-command | [Handlers](#exchange-behavior) | subsystem-interfaces:carries-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Wrapped application command callbacks receive the selected invocation's parsed arguments. | None. | [AppGroup/with_appcontext](corpus:flask:evidence/fed8939d1905b99b) |
