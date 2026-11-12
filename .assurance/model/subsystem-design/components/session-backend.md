# Session backend

## role-and-implementation

### role-kind

internal

### role

The default session backend turns client cookies into mutable session mappings and writes changed session data into response cookies. Flask supplies a replaceable SessionInterface contract and a signed-cookie implementation; an application may provide a different backend.

### implementation-mapping

`SecureCookieSessionInterface.open_session` and `save_session` implement the default storage boundary. `SecureCookieSession` tracks dictionary access and modification; `TaggedJSONSerializer` encodes additional value types before the itsdangerous serializer signs the cookie representation.

### evidence

- [Sessions](corpus:flask:evidence/be4c249245e3745e)
- [Tagged serializer](corpus:flask:evidence/ref-809a1a0be75dbb21)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-session | [Backend](#role-and-implementation) | subsystem-design:offers-capability | [Load and save sessions](corpus:/subsystem-design/local-capabilities/load-save-session.md#capability-description) | The default backend opens mappings and updates response cookies. | None. | [Session operations](corpus:flask:evidence/be4c249245e3745e) |
| maintains-session | [Backend](#role-and-implementation) | subsystem-design:maintains-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | The backend derives the request mapping from cookies and creates its outgoing serialized representation; application callers can also modify mapping values. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| delegates-signing | [Backend](#role-and-implementation) | subsystem-design:delegates-to | [Cookie signer](corpus:/subsystem-design/components/cookie-signer.md#role-and-implementation) | The backend constructs a timed serializer and requests loads/dumps of the session representation. | None. | [Signer use](corpus:flask:evidence/be4c249245e3745e) |
| belongs-session | [Backend](#role-and-implementation) | subsystem-design:belongs-to-participant | [Session backend](corpus:/architecture/architectural-participants/session-backend.md#role-and-scope) | The shipped session mapping and cookie implementation realize the internal backend responsibility, not arbitrary custom backends. | None. | [Backend](corpus:flask:evidence/be4c249245e3745e) |
