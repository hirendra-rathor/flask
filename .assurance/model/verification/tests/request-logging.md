# Test request error-stream logging and overrides

## verification-approach

### test-kind

integration

### test-description

Tests supply real StringIO error streams through the request environment and invoke a logging view or a view raising an exception. A Flask subclass replaces log_exception with a no-op. Explicit request contexts also resolve wsgi_errors_stream.

### intended-focus

The family intends to exercise request-aware diagnostic stream selection and the request exception-logging extension point. The in-memory sink replaces external output; no production log transport or logging adequacy is established.

### evidence

- [Request logging scenarios](corpus:flask:evidence/ref-7f5b6b29dd89cb78)
- [Subclass override](corpus:flask:evidence/ref-6cae1729b50deecc)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | The tested portion selects request diagnostics and calls exception logging. | None. | [Logging](corpus:flask:evidence/ref-7f5b6b29dd89cb78) [Override](corpus:flask:evidence/ref-6cae1729b50deecc) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Handle request](corpus:/subsystem-design/local-capabilities/handle-request.md#capability-description) | An exception-raising view deliberately exercises request error processing. | None. | [Logging](corpus:flask:evidence/ref-7f5b6b29dd89cb78) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Its request diagnostic coordination and replaceable logging method are intended targets. | None. | [Logging](corpus:flask:evidence/ref-7f5b6b29dd89cb78) [Override](corpus:flask:evidence/ref-6cae1729b50deecc) |
