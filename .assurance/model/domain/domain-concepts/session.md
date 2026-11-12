# Client session

## concept-definition

### definition

A client session is application information available across related client requests. Application code reads and changes the current session mapping; the configured backend decides how its representation is opened and saved. Flask's default representation is a signed client cookie with lifetime and refresh choices. The session's continuity differs from a request context's temporary binding, and its arbitrary values acquire their business meaning from the application.

### evidence

- [Session contract and default backend](corpus:flask:evidence/be4c249245e3745e)
- [Context access](corpus:flask:evidence/d8838a605f9ff504)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| session-interactions | [Session](#concept-definition) | domain:builds-upon | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Session continuity relates the application information opened for one client request to information represented for later related requests. | None. | [open_session/save_session](corpus:flask:evidence/be4c249245e3745e) |
