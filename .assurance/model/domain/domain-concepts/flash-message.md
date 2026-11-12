# Flashed message

## concept-definition

### definition

A flashed message is categorized application feedback retained in the client session for later retrieval, commonly while producing a subsequent response. Retrieval consumes the pending session messages into the current context's cache, where repeated retrieval can return them again with category selection. A flashed message is feedback content; a signal reporting its creation is a separate notification.

### evidence

- [Flash and retrieval](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| flash-session | [Message](#concept-definition) | domain:builds-upon | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Pending messages use the session to remain available for later retrieval across client interactions; current-context caching does not make them newly pending again. | None. | [flash/get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| feedback-context-form | [Message](#concept-definition) | domain:builds-upon | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | After retrieval, the message's current-presentation form is retained in the active context's cache rather than remaining pending in session content. | None. | [get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
