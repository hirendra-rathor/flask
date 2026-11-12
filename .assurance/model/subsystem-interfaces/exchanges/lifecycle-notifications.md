# Lifecycle and message notifications

## exchange-behavior

### exchange-description

Named signals report request start/finish/exception/teardown, context push/pop/teardown, template rendering, and message flashing. Event payloads differ: a request-finished notice carries the response, template notices carry template/context, and message_flashed carries the stored message and category.

### sender-and-receiver

Flask dispatch, context, rendering and flash operations send the application as signal sender and supply event-specific values to Blinker. Connected receivers obtain those notices through signal delivery. Their interpretation or resulting work is not established by the send sites.

### implementation-mapping

signals.py creates the named signals. Their send sites reside in app, ctx, templating and helpers and supply ensure_sync as the asynchronous receiver adapter. A template-rendered notice for streaming is sent during generation after iteration completes.

### evidence

- [Definitions](corpus:flask:evidence/ref-3b3fcb2407028958)
- [Request sends](corpus:flask:evidence/d3e0349504081bb5)
- [Context sends](corpus:flask:evidence/d8838a605f9ff504)
- [Rendering sends](corpus:flask:evidence/e4655695c5cdbf67)
- [Flash sends](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-signals | [Notifications](#exchange-behavior) | subsystem-interfaces:uses-interface | [Signals](corpus:/subsystem-interfaces/interfaces/lifecycle-signals.md#interface-definition) | The family uses named Blinker signals to notify connected observers. | None. | [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) |
| carries-context | [Notifications](#exchange-behavior) | subsystem-interfaces:carries-state | [Execution context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Template notices pass the rendering context dictionary, whose default values include g and an available request; the notice does not carry the complete AppContext. | None. | [Default context and sends](corpus:flask:evidence/e4655695c5cdbf67) |
| carries-flash | [Notifications](#exchange-behavior) | subsystem-interfaces:carries-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | message_flashed supplies the message/category just appended to the session's flash content, rather than the complete session. | None. | [Flash](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concept-notification | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | Named signal sends communicate framework events to connected observers, not proof of observer work. | None. | [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
| concept-application | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Each examined send supplies the application as event sender. | None. | [App sends](corpus:flask:evidence/d3e0349504081bb5) [Context sends](corpus:flask:evidence/d8838a605f9ff504) [Rendering sends](corpus:flask:evidence/e4655695c5cdbf67) [Flash sends](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concept-response | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | request_finished supplies the framework response object to observers. | None. | [finalize_request](corpus:flask:evidence/d3e0349504081bb5) |
| concept-template | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Rendering notices supply the template and its context values. | None. | [Rendering sends](corpus:flask:evidence/e4655695c5cdbf67) |
| concept-context | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Rendering payloads include request/g portions of the prepared values; context push/pop notices instead identify the event/application without passing the full context. | None. | [Default processor/sends](corpus:flask:evidence/e4655695c5cdbf67) [Context sends](corpus:flask:evidence/d8838a605f9ff504) |
| concept-request | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Template notices carry the request object when the default processor adds it for request-bound rendering. | None. | [Default processor/render sends](corpus:flask:evidence/e4655695c5cdbf67) |
| concept-feedback | [Notices](#exchange-behavior) | subsystem-interfaces:carries-concept | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | message_flashed sends only the newly stored categorized feedback value, rather than the whole session. | None. | [flash](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
