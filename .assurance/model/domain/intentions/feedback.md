# I want application feedback available for a later response

## intended-outcome

### desired-outcome

An application author should be able to retain categorized feedback during one interaction and retrieve it when producing a later response. Pending messages are consumed from the session on retrieval and remain available within the current context for repeated presentation.

### evidence

- [Flash storage and retrieval](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-message | [Feedback](#intended-outcome) | domain:concerns-concept | [Flashed message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | Categorized messages carry the application feedback for later retrieval. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-session | [Feedback](#intended-outcome) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Pending feedback is retained in session content between interactions. | None. | [flash](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| concerns-context | [Feedback](#intended-outcome) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | A retrieval caches consumed messages in the active context for repeated access. | None. | [get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
