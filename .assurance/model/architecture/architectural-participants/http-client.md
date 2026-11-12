# HTTP client

## role-and-scope

### role

The HTTP client exchanges requests and responses with the application and carries the default session cookie between requests.

### classifications

- external consumer

### scope

The client's application purpose drives HTTP requests. Flask's cookie backend observes incoming cookie values and constructs outgoing cookie instructions; the client's actual storage, transport and enforcement behavior is outside that evidence.

### implementation-mapping

`SecureCookieSessionInterface.open_session` reads the request cookie. `save_session` constructs set/delete cookie responses. These operations establish the client-facing role through Flask's side of the boundary.

### evidence

- [Cookie contract](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Client](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The external client consumes application responses and carries cookie session representations; client internals are unestablished. | None. | [Cookies](corpus:flask:evidence/be4c249245e3745e) |
| allocates-web-interaction | [Client](#role-and-scope) | architecture:allocates-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | The client supplies the request and consumes the application's response through the host; Flask does not implement client transport/display. | None. | [WSGI boundary](corpus:flask:evidence/d3e0349504081bb5) [Cookie boundary](corpus:flask:evidence/be4c249245e3745e) |
| allocates-cookie-carriage | [Client](#role-and-scope) | architecture:allocates-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Default continuity depends on the client returning the session cookie and receiving update/deletion instructions; actual retention/enforcement remain unestablished. | None. | [Cookie read/write](corpus:flask:evidence/be4c249245e3745e) |
| corresponds-requester | [Client](#role-and-scope) | architecture:corresponds-to-domain-participant | [Web requester](corpus:/domain/domain-participants/web-requester.md#role-and-contribution) | The HTTP client realizes the requester's web-input/response and optional cookie-carriage contribution; its business purpose is application-specific. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) [Cookies](corpus:flask:evidence/be4c249245e3745e) |
