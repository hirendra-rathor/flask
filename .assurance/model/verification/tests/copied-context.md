# Test copied request context in thread work

## verification-approach

### test-kind

integration

### test-description

A view decorates work with copy_current_request_context and submits it to a real ThreadPoolExecutor. The scenario arranges session and query data in the originating request and consumes the returned work iterator.

### intended-focus

The test intends to exercise copied context availability during separately submitted thread work. It targets the context wrapper's contribution; the executor's scheduling and a general concurrency guarantee are outside the focus.

### evidence

- [Copied context scenario](corpus:flask:evidence/ref-2eaab6666f98f986)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| ability | [Approach](#verification-approach) | verification:targets-for-testing | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Copied request data is made available to the decorated submitted work. | None. | [Copy](corpus:flask:evidence/ref-2eaab6666f98f986) |
| intention | [Approach](#verification-approach) | verification:targets-for-testing | [Current data aim](corpus:/domain/intentions/contextual-work.md#intended-outcome) | The deliberate separate-work arrangement identifies context continuity as the aim. | None. | [Copy](corpus:flask:evidence/ref-2eaab6666f98f986) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Bind context](corpus:/subsystem-design/local-capabilities/bind-context.md#capability-description) | Decorated work enters its captured binding. | None. | [Copy](corpus:flask:evidence/ref-2eaab6666f98f986) |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [Context manager](corpus:/subsystem-design/components/context-manager.md#role-and-implementation) | Its explicit copying support is the tested portion. | None. | [Copy](corpus:flask:evidence/ref-2eaab6666f98f986) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | The framework's contextual binding responsibility is exercised across submitted work. | None. | [Copy](corpus:flask:evidence/ref-2eaab6666f98f986) |
