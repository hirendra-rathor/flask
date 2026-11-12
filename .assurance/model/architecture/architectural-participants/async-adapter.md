# Asynchronous callback adapter

## role-and-scope

### role

The optional asgiref adapter makes a coroutine callback callable from Flask's synchronous invocation path.

### classifications

- external dependency

### scope

Flask selects the adapter when its ensure_sync operation receives an asynchronous function. The adapter's internal task/thread scheduling is outside the consumed source and supplies no separate retained runtime-unit placement claim.

### implementation-mapping

`Flask.ensure_sync` calls `async_to_sync` for coroutine functions. The default implementation imports asgiref.sync.async_to_sync and returns its wrapper; applications may override this adaptation.

### evidence

- [Adapter binding](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Adapter](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | When coroutine callbacks use Flask's default adaptation, the external adapter supplies synchronous-call integration. | None. | [ensure_sync](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-async-handlers | [Adapter](#role-and-scope) | architecture:allocates-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | When selected callbacks are coroutines and default adaptation is used, the consumed wrapper makes their synchronous invocation possible; scheduling is not established. | None. | [ensure_sync/async_to_sync and dispatch](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-async-processors | [Adapter](#role-and-scope) | architecture:allocates-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | update_template_context invokes registered processors through ensure_sync, using default adaptation for coroutine processors. | None. | [update_template_context/ensure_sync](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-async-teardown | [Adapter](#role-and-scope) | architecture:allocates-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Context teardown calls application handlers through ensure_sync, adapting coroutine callbacks under the default arrangement. | None. | [Teardown/ensure_sync](corpus:flask:evidence/d3e0349504081bb5) [Context pop](corpus:flask:evidence/d8838a605f9ff504) |
| allocates-async-observers | [Adapter](#role-and-scope) | architecture:allocates-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Send sites supply ensure_sync as the async-receiver wrapper, whose default coroutine adaptation is consumed when needed; observer completion and scheduling are not inferred. | None. | [Signal sends/ensure_sync](corpus:flask:evidence/d3e0349504081bb5) |
