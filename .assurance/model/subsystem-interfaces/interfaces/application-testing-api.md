# Application testing API

## interface-definition

### interface-kind

API

### process-locality

- in-process

### purpose-and-boundary

Shipped application test clients accept request or command invocations and expose result objects and session transactions for application tests. This boundary separates test-code control from the framework's client integration; assertions and adequacy of tests belong to their authors.

### providers-and-consumers

Flask's application testing tools provide the framework-aware API to application test code through FlaskClient and FlaskCliRunner. They consume Werkzeug and Click test support underneath it. Repository test scenarios remain reserved for Verification.

### evidence

- [Factory binding](corpus:flask:evidence/d3e0349504081bb5)
- [Client and runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-testing | [Testing API](#interface-definition) | subsystem-interfaces:binds-provider | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | Client/runner integration supplies requests, commands, results and session transactions to application tests. | None. | [Clients](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| consumer-test-code | [Testing API](#interface-definition) | subsystem-interfaces:binds-consumer | [Test code](corpus:/architecture/architectural-participants/test-code.md#role-and-scope) | Test callers supply invocations and receive responses, session mappings and command results for their own checks. | None. | [Caller contract](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
