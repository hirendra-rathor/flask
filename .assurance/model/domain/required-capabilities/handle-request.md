# Handle application requests

## capability-description

### capability

A web requester supplies a request through a serving host; Flask selects registered application behavior, performs framework request processing and adapts supported results.

### expected-result

The WSGI caller receives response status, headers and body iteration. Hooks and error handling can alter which result is produced. Serving transport and the success of application-specific work remain with the host and application.

### evidence

- [Dispatch and WSGI](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-responses | [Handle](#capability-description) | domain:contributes-to-intent | [Application-defined responses](corpus:/domain/intentions/respond-to-requests.md#intended-outcome) | Framework selection/conversion supplies the request's response result to the host. | None. | [Dispatch/make_response/WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-request | [Handle](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The request environment supplies the interaction being handled. | None. | [wsgi_app](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-response | [Handle](#capability-description) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Supported handler values become the response returned to the caller. | None. | [Finalization](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-route | [Handle](#capability-description) | domain:concerns-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | Matched endpoint/view arguments select the normal view. | None. | [dispatch_request](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-registration | [Handle](#capability-description) | domain:concerns-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Registered views, preprocessing hooks and error/response handlers supply application behavior. | None. | [Request processing](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-context | [Handle](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Request handling enters and releases a context and uses its matched request/session bindings. | None. | [wsgi_app/process_response](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-session | [Handle](#capability-description) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Context opening obtains the current session and response processing requests saving of non-null sessions. | None. | [Opening](corpus:flask:evidence/d8838a605f9ff504) [Saving](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-settings | [Handle](#capability-description) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Dispatch and request wrappers use selected application behavior choices, including exception propagation and request parsing bounds. | None. | [Dispatch](corpus:flask:evidence/d3e0349504081bb5) [Wrappers](corpus:flask:evidence/ref-4ace0d7548306bf6) |
| concerns-notices | [Handle](#capability-description) | domain:concerns-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | The framework handling path emits its named start/finish/exception/teardown notices under their actual send conditions. | None. | [Request sends](corpus:flask:evidence/d3e0349504081bb5) |
