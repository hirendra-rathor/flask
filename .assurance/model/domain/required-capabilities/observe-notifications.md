# Observe framework events

## capability-description

### capability

Application or extension authors connect observers to Flask's named request, context, rendering and message signals.

### expected-result

Connected receivers obtain the application's event notice and its event-specific values when the relevant send occurs. Their interpretation and resulting application work remain observer responsibilities; a notice does not establish unrelated completion.

### evidence

- [Signals](corpus:flask:evidence/ref-3b3fcb2407028958)
- [Request sends](corpus:flask:evidence/d3e0349504081bb5)
- [Context sends](corpus:flask:evidence/d8838a605f9ff504)
- [Template sends](corpus:flask:evidence/e4655695c5cdbf67)
- [Message sends](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-observation | [Observe](#capability-description) | domain:contributes-to-intent | [Observe behavior](corpus:/domain/intentions/observe-application.md#intended-outcome) | Named event payloads make selected framework activity observable to connected receivers. | None. | [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-notification | [Observe](#capability-description) | domain:concerns-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | Signal sends produce the notices received by connected observers. | None. | [Signals/sends](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-application | [Observe](#capability-description) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The application is supplied as the signal sender. | None. | [Send sites](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-response | [Observe](#capability-description) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Request-finished sends include the completed framework response object. | None. | [finalize_request](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-template | [Observe](#capability-description) | domain:concerns-concept | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Rendering notices include the template and rendering values. | None. | [Rendering sends](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-context | [Observe](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Context push/pop are reported, and rendering notices can include request/g value portions. | None. | [Context sends](corpus:flask:evidence/d8838a605f9ff504) [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-message | [Observe](#capability-description) | domain:concerns-concept | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | A message-flashed notice communicates the retained message/category. | None. | [flash](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-request | [Observe](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Request lifecycle notices report selected request events, and request-bound template notices can carry the request object through default rendering values. | None. | [Request sends](corpus:flask:evidence/d3e0349504081bb5) [Default processor/render sends](corpus:flask:evidence/e4655695c5cdbf67) |
