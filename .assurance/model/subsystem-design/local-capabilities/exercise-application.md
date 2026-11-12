# Exercise an application

## capability-description

### capability

Application test code can submit HTTP requests, invoke application CLI commands and edit the test client's session through shipped testing helpers. It receives test response or command result objects for its own checks, and can preserve request context access inside a client context block.

### implementation-mapping

FlaskClient.open builds a request and delegates execution to Werkzeug Client, then restores preserved contexts and binds JSON decoding. session_transaction opens and saves session changes through the configured backend. FlaskCliRunner.invoke passes the selected command and ScriptInfo to Click's test runner.

### evidence

- [Testing support](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-context | [Exercise](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Client context preservation retains and re-enters application contexts; session transactions use a temporary request context. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| uses-session | [Exercise](#capability-description) | subsystem-design:uses-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | session_transaction exposes a backend mapping to the caller and saves it to the test client's cookies. | None. | [Transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| uses-settings | [Exercise](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Test EnvironBuilder reads SERVER_NAME, APPLICATION_ROOT and PREFERRED_URL_SCHEME when building a default request base URL. | None. | [Builder](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| json-exchange | [Exercise](#capability-description) | subsystem-design:participates-in-exchange | [JSON conversion](corpus:/subsystem-interfaces/exchanges/json-conversion.md#exchange-behavior) | EnvironBuilder.json_dumps supplies test input values to the application JSON provider. | None. | [Builder JSON](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| command-exchange | [Exercise](#capability-description) | subsystem-design:participates-in-exchange | [Developer commands](corpus:/subsystem-interfaces/exchanges/developer-commands.md#exchange-behavior) | FlaskCliRunner submits command arguments to app.cli through the bound Click runner. | None. | [Runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| test-exchange | [Exercise](#capability-description) | subsystem-design:participates-in-exchange | [Test invocations and results](corpus:/subsystem-interfaces/exchanges/test-invocation.md#exchange-behavior) | The shipped client accepts request/command inputs and returns result objects for application tests. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| session-exchange | [Exercise](#capability-description) | subsystem-design:participates-in-exchange | [Session load/save](corpus:/subsystem-interfaces/exchanges/session-load-save.md#exchange-behavior) | The transaction helper invokes backend open/save directly. | None. | [Transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| wsgi-exchange | [Exercise](#capability-description) | subsystem-design:participates-in-exchange | [WSGI request and response](corpus:/subsystem-interfaces/exchanges/wsgi-request-response.md#exchange-behavior) | FlaskClient supplies a request to the inherited Werkzeug Client for the bound Flask application. The claim covers the observed client submission and returned response, not dependency-internal execution. | None. | [Client binding](corpus:flask:evidence/d3e0349504081bb5) [Client use](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| domain-exercise | [Exercise](#capability-description) | subsystem-design:contributes-to-required-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | Client and runner calls expose chosen request/command results and session/context access for caller checks. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| domain-session | [Exercise](#capability-description) | subsystem-design:contributes-to-required-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | The simulated client's transaction opens a mapping and saves caller-arranged values into its cookies. | None. | [session_transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| domain-commands | [Exercise](#capability-description) | subsystem-design:contributes-to-required-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | FlaskCliRunner invokes selected application commands with supplied arguments in a test arrangement. | None. | [FlaskCliRunner.invoke](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| domain-json | [Exercise](#capability-description) | subsystem-design:contributes-to-required-capability | [Convert JSON](corpus:/domain/required-capabilities/convert-json.md#capability-description) | Test request construction binds the application's provider for encoding chosen JSON input. | None. | [EnvironBuilder.json_dumps](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
