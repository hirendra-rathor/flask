# Blinker signal delivery

## role-and-scope

### role

Blinker signal objects deliver Flask's lifecycle and message notifications to connected receivers.

### classifications

- external dependency

### scope

Flask names its signals and supplies sender/event values; Blinker supplies delivery. Receiver behavior belongs to application or extension code and is not implemented by this participant.

### implementation-mapping

`signals` creates a Blinker namespace and named signals. Application, context, rendering and flash operations call send with event values and the application's async receiver adapter.

### evidence

- [Definitions](corpus:flask:evidence/ref-3b3fcb2407028958)
- [Request sends](corpus:flask:evidence/d3e0349504081bb5)
- [Context sends](corpus:flask:evidence/d8838a605f9ff504)
- [Template sends](corpus:flask:evidence/e4655695c5cdbf67)
- [Flash sends](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Delivery](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | Blinker provides external delivery for framework-produced event information. | None. | [Definitions](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-notification-delivery | [Blinker](#role-and-scope) | architecture:allocates-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Signal objects provide delivery of Flask-supplied notices/values to connected receivers; receiver outcomes remain external. | None. | [Signal construction](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
