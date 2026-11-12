# Flask embedded in applications

## system-boundary-and-context

### system-boundary

Flask supplies the application framework that retains setup declarations, dispatches WSGI requests to application behavior, binds execution context, and integrates sessions, templates and JSON. Its shipped developer command integration and application testing tools are also inside the boundary. Application-specific handlers, templates, extensions and commands supply their own behavior outside that framework responsibility.

### external-context

Application and extension code configure and call the framework and supply callbacks. A WSGI host invokes the application callable to serve requests; Flask returns a body iterable while the host supplies transport and serving execution. HTTP clients carry the default session cookie. Developers choose commands and test code chooses simulated requests or commands. Werkzeug, Jinja, itsdangerous, Click and Blinker supply the consumed toolkit, rendering, signing, command and signal services. Optional asynchronous callbacks use an external adapter. These interactions share the framework boundary even though their callers and deployment arrangements differ.

### evidence

- [Application composition and WSGI](corpus:flask:evidence/d3e0349504081bb5)
- [Setup](corpus:flask:evidence/c57b8f34cffef994)
- [Developer commands](corpus:flask:evidence/fed8939d1905b99b)
- [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)
- [Sessions](corpus:flask:evidence/be4c249245e3745e)
- [Templates](corpus:flask:evidence/e4655695c5cdbf67)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| serves-application-building | [Flask setting](#system-boundary-and-context) | architecture:serves-pursuit | [Build/support web applications](corpus:/domain/purpose-and-scope/build-web-applications.md#purpose-and-context) | The framework boundary supports application setup, request/context/session/content integration and application-aware developer/test tools. Application business policy, transport and assertions remain external responsibilities. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Application](corpus:flask:evidence/d3e0349504081bb5) [CLI](corpus:flask:evidence/fed8939d1905b99b) [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
