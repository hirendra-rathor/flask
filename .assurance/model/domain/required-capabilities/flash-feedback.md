# Retain and retrieve application feedback

## capability-description

### capability

An application author records a categorized message in the session and later requests pending feedback for application or template presentation.

### expected-result

The session retains the pending message; retrieval removes pending messages into the active context's cache and returns values with selected categories or filtering. Presentation and business meaning remain application work.

### evidence

- [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-feedback | [Feedback](#capability-description) | domain:contributes-to-intent | [Later feedback](corpus:/domain/intentions/feedback.md#intended-outcome) | Session retention and later retrieval make feedback available across interactions. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-message | [Feedback](#capability-description) | domain:concerns-concept | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | Calls store or return the categorized feedback values. | None. | [flash/get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-session | [Feedback](#capability-description) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The pending message collection is added to and removed from session content. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-context | [Feedback](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Retrieval caches messages for repeated access in the active context. | None. | [get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-notice | [Feedback](#capability-description) | domain:concerns-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | Flashing emits a notice of the categorized feedback just retained, separately from later retrieval. | None. | [flash send](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
