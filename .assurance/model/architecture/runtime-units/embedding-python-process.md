# Embedding Python process

## execution-context

### runtime-kind

process

### execution-unit

A caller-supplied Python process runs Flask's directly invoked setup, WSGI, context, session, rendering, JSON, command and testing work. The same family includes module-command execution and application/test embedding: their host choices differ while direct framework calls share the caller's process. Synchronous application callbacks run through those calls; streaming work runs when its iterator is consumed.

### execution-environment

The application launcher, WSGI host, command interpreter or test driver supplies execution. The module command invokes Flask's CLI inside its Python execution, and the CLI/development run operation hands an application to Werkzeug. Flask source delegates host and worker placement: threaded/reloader options establish requested server behavior, not a separately inspected thread/process topology. Optional async adaptation similarly leaves coroutine scheduling to its supplier. No fixed container or machine placement is established.

### evidence

- [WSGI/direct calls and server binding](corpus:flask:evidence/d3e0349504081bb5)
- [Module command](corpus:flask:evidence/d0c29c92fc4e77a1)
- [Commands](corpus:flask:evidence/fed8939d1905b99b)
- [Testing calls](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)
- [Rendering calls](corpus:flask:evidence/e4655695c5cdbf67)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| occurs-framework | [Process](#execution-context) | architecture:occurs-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | Python module invocation and direct application/test embedding run framework work in the caller-supplied process; no fixed deployment host is inferred. | None. | [Module command](corpus:flask:evidence/d0c29c92fc4e77a1) [Application](corpus:flask:evidence/d3e0349504081bb5) [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| hosts-coordinator | [Process](#execution-context) | architecture:hosts-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Direct setup, WSGI dispatch, context operations and contextual helpers execute in their invoking Python process, including iterator-driven work when consumed there. | None. | [Application](corpus:flask:evidence/d3e0349504081bb5) [Context](corpus:flask:evidence/d8838a605f9ff504) [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| hosts-sessions | [Process](#execution-context) | architecture:hosts-participant | [Session backend](corpus:/architecture/architectural-participants/session-backend.md#role-and-scope) | Context and response/test operations call the shipped session backend directly; remote storage in custom backends is outside this placement. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| hosts-templates | [Process](#execution-context) | architecture:hosts-participant | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Render and stream entry points perform context/source integration in the calling process, with streaming work deferred to consumption. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| hosts-json | [Process](#execution-context) | architecture:hosts-participant | [JSON provider](corpus:/architecture/architectural-participants/json-provider.md#role-and-scope) | Shipped conversion and response methods run by direct invocation in the embedding process. | None. | [JSON](corpus:flask:evidence/c2956553392ff9ef) |
| hosts-cli | [Process](#execution-context) | architecture:hosts-participant | [CLI](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | Module execution calls main and command integration directly; delegated development-server workers are not enumerated. | None. | [Module](corpus:flask:evidence/d0c29c92fc4e77a1) [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| hosts-testing | [Process](#execution-context) | architecture:hosts-participant | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | Client/runner methods and temporary context/session integration execute through direct calls in the test caller's process. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| hosts-application-callbacks | [Process](#execution-context) | architecture:hosts-participant | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | Synchronous registered views, hooks, factories, processors and commands run through direct callback invocation. Unseen application execution and async-adapter scheduling are excluded. | None. | [Calls](corpus:flask:evidence/d3e0349504081bb5) [Commands](corpus:flask:evidence/fed8939d1905b99b) |
| hosts-toolkit-calls | [Process](#execution-context) | architecture:hosts-participant | [Werkzeug](corpus:/architecture/architectural-participants/werkzeug.md#role-and-scope) | The consumed map-adapter, wrapper and file/test helper calls share the invoking process. Development-server worker topology is unestablished. | None. | [Calls](corpus:flask:evidence/d3e0349504081bb5) [Files](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| hosts-jinja-calls | [Process](#execution-context) | architecture:hosts-participant | [Jinja](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | The bound engine's direct selection/compilation/rendering and loader calls run in the caller's process; unseen extension execution is excluded. | None. | [Engine calls](corpus:flask:evidence/e4655695c5cdbf67) |
| hosts-signing-calls | [Process](#execution-context) | architecture:hosts-participant | [Signer](corpus:/architecture/architectural-participants/cookie-signer.md#role-and-scope) | Default session handling directly constructs and calls the timed serializer in the calling process. | None. | [Signer calls](corpus:flask:evidence/be4c249245e3745e) |
| hosts-click-calls | [Process](#execution-context) | architecture:hosts-participant | [Click](corpus:/architecture/architectural-participants/click.md#role-and-scope) | Flask directly invokes inherited command/group machinery and its isolated test runner in the calling process; arbitrary command descendants are outside this claim. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) [Runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| hosts-signal-calls | [Process](#execution-context) | architecture:hosts-participant | [Signal delivery](corpus:/architecture/architectural-participants/signal-delivery.md#role-and-scope) | Framework operations directly call signal objects in their process. Async receiver scheduling and receiver internals are excluded. | None. | [Sends](corpus:flask:evidence/d3e0349504081bb5) [Context sends](corpus:flask:evidence/d8838a605f9ff504) |
| hosts-adapter-binding | [Process](#execution-context) | architecture:hosts-participant | [Async adapter](corpus:/architecture/architectural-participants/async-adapter.md#role-and-scope) | The caller directly invokes adapter construction to obtain a synchronous wrapper; this places only that consumed binding operation, not the coroutine's scheduling. | None. | [Binding](corpus:flask:evidence/d3e0349504081bb5) |
