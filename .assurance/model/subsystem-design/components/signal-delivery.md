# Lifecycle signal delivery

## role-and-implementation

### role-kind

external dependency

### role

Blinker signal objects deliver Flask lifecycle and message notifications to connected receivers. Flask defines a private namespace of public signals and sends them with the application as sender plus event-specific values.

### implementation-mapping

signals.py creates named signal objects from Blinker Namespace. Dispatch, context, template and flash operations call their send methods, providing Flask's ensure_sync as the asynchronous receiver adapter. Receiver implementations are supplied outside Flask's source boundary.

### evidence

- [Signal definitions](corpus:flask:evidence/ref-3b3fcb2407028958)
- [Request notifications](corpus:flask:evidence/d3e0349504081bb5)
- [Context notifications](corpus:flask:evidence/d8838a605f9ff504)
- [Template notifications](corpus:flask:evidence/e4655695c5cdbf67)
- [Flash notification](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| belongs-signals | [Delivery contribution](#role-and-implementation) | subsystem-design:belongs-to-participant | [Blinker](corpus:/architecture/architectural-participants/signal-delivery.md#role-and-scope) | Blinker supplies signal delivery; Flask supplies named signals and event values. | None. | [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
