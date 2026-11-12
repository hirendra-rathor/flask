# Test invocations and results

## exchange-behavior

### exchange-description

Test code supplies request parameters or command arguments and receives a test response or command Result. A session transaction additionally yields the backend's mutable session mapping for caller edits and then writes its cookie representation into the test client.

### sender-and-receiver

Application test code sends inputs to FlaskClient or FlaskCliRunner. Those helpers return the corresponding result objects. session_transaction yields the session mapping to the test caller and consumes its edited mapping when the context manager exits.

### implementation-mapping

FlaskClient.open delegates the built request to Werkzeug Client and returns its response with app JSON binding. FlaskCliRunner.invoke passes command/args and app-aware ScriptInfo to Click. session_transaction brackets caller edits with backend open/save calls.

### evidence

- [Testing operations](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-testing | [Invocations/results](#exchange-behavior) | subsystem-interfaces:uses-interface | [Test API](corpus:/subsystem-interfaces/interfaces/application-testing-api.md#interface-definition) | This exchange uses the shipped application testing helpers. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| carries-session | [Invocations/results](#exchange-behavior) | subsystem-interfaces:carries-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | session_transaction yields the mapping for caller mutation and saves its resulting content to client cookies. | None. | [Transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concept-exercise | [Test exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Exercise](corpus:/domain/domain-concepts/application-exercise.md#concept-definition) | Caller-selected request/command/session inputs and returned results describe the chosen simulated application exercise, without asserting checks passed. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concept-request | [Test exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The client accepts request data selected by test callers. | None. | [FlaskClient.open](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concept-response | [Test exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Client calls return test responses to the caller for inspection. | None. | [FlaskClient.open](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concept-command | [Test exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Runner calls accept selected command/arguments and return that invocation's result. | None. | [FlaskCliRunner.invoke](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concept-session | [Test exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | A session transaction yields the backend mapping to test code and consumes its arranged content on exit. | None. | [session_transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
