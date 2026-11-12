# Application testing support

## role-and-implementation

### role-kind

internal

### role

The shipped testing support lets application developers invoke requests and commands and inspect results through framework-aware clients. It integrates cookies, session transactions, JSON behavior, and optional context preservation with external test runners. It supplies test tools; it does not establish that a test assertion ran or passed.

### implementation-mapping

`Flask.test_client` and `test_cli_runner` construct `FlaskClient` and `FlaskCliRunner`. `EnvironBuilder` creates application-aware request environments, `FlaskClient.open` delegates request execution, and `session_transaction` exposes editable session data. `FlaskCliRunner.invoke` supplies ScriptInfo to Click's runner.

### evidence

- [Factories](corpus:flask:evidence/d3e0349504081bb5)
- [Clients](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-exercise | [Support](#role-and-implementation) | subsystem-design:offers-capability | [Exercise applications](corpus:/subsystem-design/local-capabilities/exercise-application.md#capability-description) | Test clients offer request, command and session-transaction work. | None. | [Clients](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-http | [Support](#role-and-implementation) | subsystem-design:delegates-to | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | FlaskClient subclasses Client and delegates open to its HTTP testing implementation. | None. | [Client](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-json | [Support](#role-and-implementation) | subsystem-design:delegates-to | [JSON provider](corpus:/subsystem-design/components/json-provider.md#role-and-implementation) | EnvironBuilder.json_dumps calls the application's provider and returned test responses receive it as json_module. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-application | [Support](#role-and-implementation) | subsystem-design:delegates-to | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | Flask.test_client binds the Flask application as the target of the external Client used by open. This establishes delegated application invocation at the binding, without claiming external client internals. | None. | [Binding](corpus:flask:evidence/d3e0349504081bb5) [Open](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-commands | [Support](#role-and-implementation) | subsystem-design:delegates-to | [Developer CLI](corpus:/subsystem-design/components/developer-cli.md#role-and-implementation) | The CLI runner selects app.cli and provides ScriptInfo for the application-aware command group. | None. | [Runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-click | [Support](#role-and-implementation) | subsystem-design:delegates-to | [Click](corpus:/subsystem-design/components/click-runtime.md#role-and-implementation) | FlaskCliRunner delegates command execution to Click's CliRunner. | None. | [Runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-session | [Support](#role-and-implementation) | subsystem-design:delegates-to | [Session backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | session_transaction requests session opening and saving from app.session_interface. | None. | [Transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| delegates-context | [Support](#role-and-implementation) | subsystem-design:delegates-to | [Context manager](corpus:/subsystem-design/components/context-manager.md#role-and-implementation) | Test support creates temporary contexts and re-enters contexts preserved by the application. | None. | [Context handling](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| belongs-testing | [Testing support](#role-and-implementation) | subsystem-design:belongs-to-participant | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | Framework-aware client, runner and transaction integration belong to shipped testing tools rather than to external test assertions. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
