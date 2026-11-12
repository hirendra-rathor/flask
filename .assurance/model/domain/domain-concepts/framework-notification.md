# Framework notification

## concept-definition

### definition

A framework notification reports a named event in request handling, context use, template rendering or message flashing to connected observers. The event identifies the application and carries the values relevant to that event, such as a response, template/context values or flashed message/category. Receiving a notification does not itself establish the observer's resulting work or the completion of unrelated application activity.

### evidence

- [Named signals](corpus:flask:evidence/ref-3b3fcb2407028958)
- [Request event values](corpus:flask:evidence/d3e0349504081bb5)
- [Rendering event values](corpus:flask:evidence/e4655695c5cdbf67)
- [Flash event values](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| notice-application | [Notice](#concept-definition) | domain:builds-upon | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The application supplied as sender identifies which application's framework event is reported. | None. | [Signal send sites](corpus:flask:evidence/d3e0349504081bb5) |
| notice-request-form | [Notice](#concept-definition) | domain:builds-upon | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Request lifecycle notices report events in handling an application request, without necessarily carrying the request object. | None. | [Request sends](corpus:flask:evidence/d3e0349504081bb5) |
| notice-response-form | [Notice](#concept-definition) | domain:builds-upon | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | The request-finished form reports and carries the framework response. | None. | [finalize_request](corpus:flask:evidence/d3e0349504081bb5) |
| notice-context-form | [Notice](#concept-definition) | domain:builds-upon | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Context notices report binding/teardown events; they do not imply the full context record is transmitted. | None. | [Context sends](corpus:flask:evidence/d8838a605f9ff504) |
| notice-template-form | [Notice](#concept-definition) | domain:builds-upon | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Rendering notices report the selected template and prepared rendering values. | None. | [Rendering sends](corpus:flask:evidence/e4655695c5cdbf67) |
| notice-feedback-form | [Notice](#concept-definition) | domain:builds-upon | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | The message-flashed form reports the categorized feedback that was just stored. | None. | [flash send](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
