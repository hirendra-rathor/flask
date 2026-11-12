# The default session backend MUST discard rejected cookie contents

## rule-definition

### rule-statement

When its timed serializer rejects a supplied session cookie with `BadSignature`, the default backend MUST return an empty session instead of restoring that cookie's submitted values.

### scope-and-conditions

The constraint applies to `SecureCookieSessionInterface.open_session` with configured signing support. Flask supplies the configured maximum age to the serializer and restores its returned values only after that call succeeds. No cookie also yields an empty session. No signing key yields no opened mapping and the context's null fallback. A replacement backend has its own contract; this rule establishes Flask's acceptance decision rather than an independent proof of signature or age enforcement.

### evidence

- [Serializer/open_session](corpus:flask:evidence/be4c249245e3745e)
- [Null fallback](corpus:flask:evidence/d8838a605f9ff504)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-integrity | [Validation rule](#rule-definition) | domain:protects-intent | [Validated values](corpus:/domain/intentions/session-integrity.md#intended-outcome) | Rejected cookie contents are not restored into application session values by the default backend. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) |
| applies-session | [Validation rule](#rule-definition) | domain:applies-to | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The session mapping is empty after the consumed serializer rejects the submitted representation. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) |
| applies-retention | [Validation rule](#rule-definition) | domain:applies-to | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Only the default cookie-opening leg is constrained; custom backend behavior is not generalized. | None. | [Default implementation](corpus:flask:evidence/be4c249245e3745e) |
