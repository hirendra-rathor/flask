# Web application requester

## role-and-contribution

### role-kind

End user

### role

The web requester is the person or client agent that asks the application for web work and consumes its response for an application-specific purpose.

### contribution

The requester supplies HTTP request data through a serving host and receives application output. A client can carry the default session cookie between interactions. Flask's side of this interaction establishes these contributions while leaving the client's business goal, storage enforcement and display behavior to that client.

### evidence

- [WSGI request/response boundary](corpus:flask:evidence/d3e0349504081bb5)
- [Client cookie boundary](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| needs-handling | [Requester](#role-and-contribution) | domain:requires-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | The requested application work needs a response supplied through the host. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| needs-session | [Requester](#role-and-contribution) | domain:requires-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | When related interactions use the default cookie session, returning its representation supports continuity. | None. | [Cookie open/save](corpus:flask:evidence/be4c249245e3745e) |
| stake-responses | [Requester](#role-and-contribution) | domain:has-stake-in-intention | [Application responses](corpus:/domain/intentions/respond-to-requests.md#intended-outcome) | Client requests have an independent application purpose and consume returned output. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| stake-continuity | [Requester](#role-and-contribution) | domain:has-stake-in-intention | [Continuity](corpus:/domain/intentions/session-continuity.md#intended-outcome) | Cookie carriage supports related interactions under the backend/client conditions. | None. | [Cookies](corpus:flask:evidence/be4c249245e3745e) |
| concerned-request | [Requester](#role-and-contribution) | domain:is-concerned-with-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Client-supplied web input reaches Flask through its WSGI caller. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| concerned-response | [Requester](#role-and-contribution) | domain:is-concerned-with-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Response status/headers/body are made available to the serving caller for client delivery. | None. | [WSGI](corpus:flask:evidence/d3e0349504081bb5) |
| concerned-session | [Requester](#role-and-contribution) | domain:is-concerned-with-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The client-facing cookie represents default session information; this does not imply client interpretation of the payload. | None. | [Cookie operations](corpus:flask:evidence/be4c249245e3745e) |
