# Flask application security assessor

## role-and-contribution

### role-kind

AppSec engineer

### role

The security assessor evaluates the security properties on which a Flask application's use of the default session backend relies.

### contribution

The assessor needs to distinguish restored cookie session values from `BadSignature` rejection and understand which keys and maximum age Flask supplies for validation. This supported stake is session acceptance at the framework's serializer boundary; it grants no authority over operator keys or application access policy.

### evidence

- [Default session acceptance](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| needs-session-validation | [Assessor](#role-and-contribution) | domain:requires-capability | [Session work](corpus:/domain/required-capabilities/retain-session.md#capability-description) | The role relies on the default backend's acceptance operation before restored values reach application work. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) |
| stake-integrity | [Assessor](#role-and-contribution) | domain:has-stake-in-intention | [Validated session values](corpus:/domain/intentions/session-integrity.md#intended-outcome) | Rejection of serializer-invalid cookies is the bounded security expectation evidenced by this backend. | None. | [Serializer/open_session](corpus:flask:evidence/be4c249245e3745e) |
| concerned-session | [Assessor](#role-and-contribution) | domain:is-concerned-with-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Restored client-carried values are the subject of the acceptance constraint. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) |
| concerned-settings | [Assessor](#role-and-contribution) | domain:is-concerned-with-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Configured key material and lifetime qualify the acceptance operation the assessor evaluates. | None. | [Serializer keys/max_age](corpus:flask:evidence/be4c249245e3745e) |
