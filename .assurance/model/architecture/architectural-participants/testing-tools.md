# Flask application testing tools

## role-and-scope

### role

The testing tools let test code invoke application requests and commands and access results, contexts and session transactions through Flask-aware clients.

### classifications

- internal

### scope

Flask provides client/runner integration with the application's context, JSON and session services. Werkzeug and Click supply underlying test execution tools. Test code chooses scenarios and checks outcomes; availability of these tools establishes no test execution or adequacy.

### implementation-mapping

`Flask.test_client` and `test_cli_runner` bind the application to `FlaskClient` and `FlaskCliRunner`. `testing.EnvironBuilder`, client context handling, `session_transaction` and runner invocation implement framework integration.

### evidence

- [Factories](corpus:flask:evidence/d3e0349504081bb5)
- [Testing tools](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Tools](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The shipped framework-aware testing API is internal even when driven by external test code. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-exercise | [Tools](#role-and-scope) | architecture:allocates-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | Flask-aware clients/runners expose caller-selected scenario results and session/context access; the caller supplies assertions. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-session-arrangement | [Tools](#role-and-scope) | architecture:allocates-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Session transactions expose a backend mapping and save caller-arranged values to simulated cookies. | None. | [session_transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-test-commands | [Tools](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | FlaskCliRunner supplies application-aware invocation in the test arrangement, using Click's runner. | None. | [FlaskCliRunner.invoke](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-json-input-binding | [Tools](#role-and-scope) | architecture:allocates-capability | [Convert JSON](corpus:/domain/required-capabilities/convert-json.md#capability-description) | The builder/response bindings route simulated JSON input and decoding to the application provider; they do not implement conversion. | None. | [Testing JSON binding](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-context-preservation | [Tools](#role-and-scope) | architecture:allocates-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Client context collection and re-entry expose selected request bindings after execution; maintenance remains coordinator work. | None. | [Client context management](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
