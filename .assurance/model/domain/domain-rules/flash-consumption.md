# Feedback retrieval MUST consume pending messages once per context cache

## rule-definition

### rule-statement

The first get_flashed_messages retrieval in a context without cached messages MUST remove the pending session messages and retain them in that context's cache. Later retrievals in the same context MUST use the cache rather than consume pending session messages again.

### scope-and-conditions

Category filtering and omission of categories affect the returned presentation rather than what the initial retrieval consumes. Messages flashed after the cache is populated remain pending in the session for a later context. Repeated retrieval in the same context can return cached values again; this is not a once-only display guarantee.

### evidence

- [Flash/retrieval implementation](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-feedback | [Consumption rule](#rule-definition) | domain:protects-intent | [Later feedback](corpus:/domain/intentions/feedback.md#intended-outcome) | The session-to-context transfer consumes pending feedback while preserving repeated access during the current presentation. | None. | [get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| applies-message | [Consumption rule](#rule-definition) | domain:applies-to | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | Pending messages are transferred once to the context cache, independent of returned category filtering. | None. | [get_flashed_messages](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| applies-session | [Consumption rule](#rule-definition) | domain:applies-to | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The initial retrieval removes the session's pending flash collection. | None. | [Session pop](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| applies-context | [Consumption rule](#rule-definition) | domain:applies-to | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | The active context owns the cache that later retrievals reuse. | None. | [Cache use](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| applies-feedback | [Consumption rule](#rule-definition) | domain:applies-to | [Feedback capability](corpus:/domain/required-capabilities/flash-feedback.md#capability-description) | This rule qualifies when retained feedback is consumed and repeated retrieval remains possible. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
