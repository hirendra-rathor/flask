# WSGI serving host

## role-and-scope

### role

The WSGI serving host supplies the serving environment that calls a Flask application with request environment data and a response-start callback, then consumes its returned body iterable for delivery.

### classifications

- external dependency

### scope

Calling into Flask supplies execution and transport for serving rather than making the host the independent application consumer. Flask can hand its application to Werkzeug's development server; other WSGI hosts and middleware supply the same callable boundary. Their worker placement and transport implementations are outside inspected source.

### implementation-mapping

`Flask.__call__` forwards the WSGI contract to `wsgi_app`. `Flask.run` and the CLI run callback pass the application to `run_simple`; the host implementation is consumed at that binding.

### evidence

- [Callable and development binding](corpus:flask:evidence/d3e0349504081bb5)
- [CLI server binding](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Host](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The external host provides serving execution and transport, including the requested Werkzeug development-host arrangement. | None. | [Callable/run](corpus:flask:evidence/d3e0349504081bb5) [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-serving-boundary | [Host](#role-and-scope) | architecture:allocates-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | The serving host supplies WSGI execution/input and consumes response output for transport; only the consumed boundary is established. | None. | [WSGI callable](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-development-serving | [Host](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | For the development-server command, the host receives the selected application and serving options; deployment success/topology are unestablished. | None. | [run_command/run_simple](corpus:flask:evidence/fed8939d1905b99b) |
