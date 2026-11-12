# Session cookie representation

## exchange-behavior

### exchange-description

The default backend reads a signed encoded mapping from the named request cookie and can write an updated signed representation or deletion instruction into response headers. This communicates client-carried session data between requests; cookie attributes specify client instructions rather than proving client retention.

### sender-and-receiver

The client returns its cookie through the HTTP request. Flask's default backend decodes it into the session and supplies an updated Set-Cookie or deletion header to the response for the client. Actual transport and browser storage are outside the inspected implementation.

### implementation-mapping

SecureCookieSessionInterface.open_session reads request.cookies and serializer.loads. save_session calls serializer.dumps and response.set_cookie/delete_cookie. Cookie getters and lifetime/refresh checks qualify the outgoing representation.

### evidence

- [Cookie operations](corpus:flask:evidence/be4c249245e3745e)
- [Payload serializer](corpus:flask:evidence/ref-809a1a0be75dbb21)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-cookie | [Cookie representation](#exchange-behavior) | subsystem-interfaces:uses-interface | [Cookie interface](corpus:/subsystem-interfaces/interfaces/session-cookie.md#interface-definition) | The exchange uses request cookies and outgoing response cookie headers. | None. | [Cookies](corpus:flask:evidence/be4c249245e3745e) |
| carries-session | [Cookie representation](#exchange-behavior) | subsystem-interfaces:carries-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | The signed payload represents the default backend's session mapping, including flash values when present. | None. | [Serialization](corpus:flask:evidence/be4c249245e3745e) |
| concept-session | [Cookie](#exchange-behavior) | subsystem-interfaces:carries-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The signed cookie is the default backend's client-carried session representation; client enforcement/retention are outside this evidence. | None. | [Cookie operations](corpus:flask:evidence/be4c249245e3745e) |
| concept-feedback | [Cookie](#exchange-behavior) | subsystem-interfaces:carries-concept | [Message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | When pending flash values are present, session serialization carries their categorized feedback portion in the default cookie. | None. | [Session serialization](corpus:flask:evidence/be4c249245e3745e) [Flash storage](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
