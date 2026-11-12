# Flask session backend

## role-and-scope

### role

The Flask session backend opens a request's session mapping and saves its representation through the configured response policy. The shipped backend interprets signed client cookies and supplies the mutable session object, using a separately supplied signer.

### classifications

- internal

### scope

Flask implements the default cookie backend and the replaceable session contract. A custom backend belongs to its application or extension supplier; its unseen storage behavior is not assigned to this participant. Application code chooses the session values while framework helpers can add or retrieve flash messages.

### implementation-mapping

`SessionInterface` defines opening, saving and cookie-policy operations. `SecureCookieSessionInterface`, `SecureCookieSession` and tagged JSON serialization implement the shipped backend. The application binds a default interface and context/response/test operations call it.

### evidence

- [Backend](corpus:flask:evidence/be4c249245e3745e)
- [Tagged values](corpus:flask:evidence/ref-809a1a0be75dbb21)
- [Application binding](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Backend](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The shipped backend supplies internal session interpretation and cookie-response work; custom replacements remain externally supplied behavior. | None. | [Backend](corpus:flask:evidence/be4c249245e3745e) |
| allocates-session | [Backend](#role-and-scope) | architecture:allocates-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | The default backend opens mappings and writes/removes signed cookie representations according to configured acceptance/emission policy; custom storage is separately supplied. | None. | [Session backend](corpus:flask:evidence/be4c249245e3745e) |
