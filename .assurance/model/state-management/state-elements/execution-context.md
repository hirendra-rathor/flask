# Active execution context

## state-definition

### state-description

The active execution context associates framework work with an application, its `g` namespace, and optionally a request, session, and URL adapter. Context proxies let application code access those bindings while the context is active. Request and application contexts use the same `AppContext` representation; an application-only context has no request.

### evidence

- [Context](corpus:flask:evidence/d8838a605f9ff504)
- [Proxies](corpus:flask:evidence/ref-594a138991de4d96)

## state-implementation

### structure-and-representation

`AppContext` stores application and optional request/session objects, `g`, URL matching results through its request, per-context after-request callbacks, and flashed-message cache. A `ContextVar` named `_cv_app` holds the active context; `LocalProxy` objects expose its application, request, session, and `g`.

### state-operations

Context construction binds a URL adapter. `push` installs the context, opens a request's session, and matches its URL; `pop` invokes teardown and restores the prior binding. WSGI handling and CLI commands establish contexts; streaming helpers and the test client can preserve or re-enter them. Rendering, JSON helpers, resource helpers, and view dispatch read the active bindings.

### evidence

- [Context operations](corpus:flask:evidence/d8838a605f9ff504)
- [Proxies](corpus:flask:evidence/ref-594a138991de4d96)
- [WSGI](corpus:flask:evidence/d3e0349504081bb5)
- [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| maintained-coordinator | [Context](#state-implementation) | state-management:maintained-by | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Context construction/push/matching/pop maintain active bindings and routing data; flashed-message retrieval fills the context cache. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| used-coordinator | [Context](#state-implementation) | state-management:used-by-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Dispatch and contextual URL/file/flash helpers use the active application, request, adapter and session bindings. | None. | [Application](corpus:flask:evidence/d3e0349504081bb5) [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| used-templates | [Context](#state-implementation) | state-management:used-by-participant | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Rendering selects the bound application and supplies request/g portions; streaming preserves the binding while generating text. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| used-json | [Context](#state-implementation) | state-management:used-by-participant | [JSON provider](corpus:/architecture/architectural-participants/json-provider.md#role-and-scope) | Public JSON helpers select the bound application's provider; dumps/loads can instead use Python JSON without a context. | None. | [Public helpers](corpus:flask:evidence/d130c1228070cc92) |
| used-cli | [Context](#state-implementation) | state-management:used-by-participant | [CLI](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | Application commands and shell preparation enter/use the selected application's context. | None. | [Command context](corpus:flask:evidence/fed8939d1905b99b) |
| used-testing | [Context](#state-implementation) | state-management:used-by-participant | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | Client preservation and session transactions retain/re-enter or create temporary contexts; context maintenance remains with the coordinator. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| used-jinja | [Context](#state-implementation) | state-management:used-by-participant | [Jinja](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | Rendering supplies request/g values and contextual proxies as engine inputs; only those portions are connected, without claiming arbitrary template reads. | None. | [Processor/render](corpus:flask:evidence/e4655695c5cdbf67) [Globals](corpus:flask:evidence/d3e0349504081bb5) |
| used-toolkit | [Context](#state-implementation) | state-management:used-by-participant | [Werkzeug](corpus:/architecture/architectural-participants/werkzeug.md#role-and-scope) | File response helpers pass the active request environment to toolkit file operations; no whole-context disclosure is inferred. | None. | [File binding](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| used-application | [Context](#state-implementation) | state-management:used-by-participant | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | Views and URL preprocessors receive matched endpoint/argument portions; connected template observers can receive request/g portions of rendering context. This does not establish arbitrary reads of other active bindings. | None. | [Dispatch arguments](corpus:flask:evidence/d3e0349504081bb5) [Template notification](corpus:flask:evidence/e4655695c5cdbf67) |
| used-developer | [Context](#state-implementation) | state-management:used-by-participant | [Developer](corpus:/architecture/architectural-participants/developer.md#role-and-scope) | The shell command supplies the selected application and g namespace for interactive use; other context portions are not implied. | None. | [Shell](corpus:flask:evidence/fed8939d1905b99b) [Namespace](corpus:flask:evidence/d3e0349504081bb5) |
| used-signals | [Context](#state-implementation) | state-management:used-by-participant | [Blinker](corpus:/architecture/architectural-participants/signal-delivery.md#role-and-scope) | Template notices pass rendering context values including default g/request portions to signal delivery; the whole AppContext is not sent. | None. | [Context processor/sends](corpus:flask:evidence/e4655695c5cdbf67) |
| represents-context | [Execution context](#state-definition) | state-management:represents-concept | [Active context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | The active binding and per-context values represent the application/request data available to the current work. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Proxies](corpus:flask:evidence/ref-594a138991de4d96) |
| represents-current-application | [Execution context](#state-definition) | state-management:represents-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The app binding identifies the selected configured application; the context is not its full registration/settings representation. | None. | [AppContext](corpus:flask:evidence/d8838a605f9ff504) |
| represents-current-request | [Execution context](#state-definition) | state-management:represents-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | When request-bound, its request and matching data represent the current interaction. | None. | [Request/matching](corpus:flask:evidence/d8838a605f9ff504) |
| represents-current-session | [Execution context](#state-definition) | state-management:represents-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The request-context session binding retains the opened mapping rather than establishing a separate cross-request store. | None. | [_get_session/push](corpus:flask:evidence/d8838a605f9ff504) |
| represents-cached-feedback | [Execution context](#state-definition) | state-management:represents-concept | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | The _flashes cache represents feedback already consumed from pending session content for repeated access in this context. | None. | [Retrieval](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| represents-matched-route | [Execution context](#state-definition) | state-management:represents-concept | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | In a matched request context, the request's selected rule and view arguments represent the current route selection, not the whole application's route catalogue. | None. | [match_request](corpus:flask:evidence/d8838a605f9ff504) |
