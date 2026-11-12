# WSGI application service

## interface-definition

### interface-kind

API

### process-locality

- in-process

### purpose-and-boundary

A WSGI caller invokes a Flask application with an environment and start_response callback and consumes the returned body iterable. This is the application-serving callable boundary; the host remains responsible for translating its client transport into WSGI calls and delivering returned data.

### providers-and-consumers

The Flask application coordinator supplies the callable through __call__/wsgi_app. The WSGI serving host consumes it for serving. Flask's application testing tools bind it to the consumed Werkzeug client for simulated requests; middleware can wrap the callable without becoming its application behavior provider.

### evidence

- [WSGI callable](corpus:flask:evidence/d3e0349504081bb5)
- [Client binding](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-coordinator | [WSGI service](#interface-definition) | subsystem-interfaces:binds-provider | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | The coordinator supplies Flask.__call__/wsgi_app and its response iterable contract; application views supply results through a different callback boundary. | None. | [Callable](corpus:flask:evidence/d3e0349504081bb5) |
| consumer-host | [WSGI service](#interface-definition) | subsystem-interfaces:binds-consumer | [WSGI host](corpus:/architecture/architectural-participants/wsgi-host.md#role-and-scope) | Serving invokes the application with environ/start_response and consumes its returned iterable; the host still supplies execution and transport. | None. | [Callable and run binding](corpus:flask:evidence/d3e0349504081bb5) [CLI host binding](corpus:flask:evidence/fed8939d1905b99b) |
| consumer-testing | [WSGI service](#interface-definition) | subsystem-interfaces:binds-consumer | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | The client is bound to the Flask application and delegates simulated request invocation, without requiring a network server. | None. | [Factory](corpus:flask:evidence/d3e0349504081bb5) [Client](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| consumer-toolkit | [WSGI service](#interface-definition) | subsystem-interfaces:binds-consumer | [Werkzeug](corpus:/architecture/architectural-participants/werkzeug.md#role-and-scope) | Flask binds its callable to the external HTTP Client implementation consumed by FlaskClient; this claims the bound test-caller role, not dependency-internal coverage. | None. | [Factory binding](corpus:flask:evidence/d3e0349504081bb5) [Client delegation](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
