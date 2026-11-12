# Flash and retrieve messages

## capability-description

### capability

Application code stores a categorized message in the session for later retrieval, then can retrieve messages with optional category information and filtering. Retrieval removes pending messages from the session once and retains their values in the current context for repeated access.

### implementation-mapping

flash updates the session's _flashes value and sends message_flashed. get_flashed_messages transfers those values into AppContext._flashes and returns the requested presentation. Templates receive the helper through the application Jinja globals.

### evidence

- [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [Template global](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-session | [Flash](#capability-description) | subsystem-design:uses-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | Flashing appends categorized messages and retrieval removes the pending session value. | None. | [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| uses-context | [Flash](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Retrieval caches messages in the active context and flashing uses the current application as signal sender. | None. | [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| lifecycle-exchange | [Flash](#capability-description) | subsystem-design:participates-in-exchange | [Lifecycle notices](corpus:/subsystem-interfaces/exchanges/lifecycle-notifications.md#exchange-behavior) | flash sends the message and category to connected signal receivers. | None. | [Signal send](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| helper-exchange | [Flash](#capability-description) | subsystem-design:participates-in-exchange | [Helper requests/results](corpus:/subsystem-interfaces/exchanges/helper-requests-results.md#exchange-behavior) | Flashing receives message/category values and retrieval supplies pending message values to the application caller. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| domain-feedback | [Flash](#capability-description) | subsystem-design:contributes-to-required-capability | [Retain/retrieve feedback](corpus:/domain/required-capabilities/flash-feedback.md#capability-description) | Session storage and context-cached retrieval supply pending categorized feedback. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| domain-observe | [Flash](#capability-description) | subsystem-design:contributes-to-required-capability | [Observe framework events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | message_flashed supplies the newly retained message/category to connected observers. | None. | [flash signal send](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
