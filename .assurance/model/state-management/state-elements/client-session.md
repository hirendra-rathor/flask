# Client session

## state-definition

### state-description

The session is a mutable mapping of application data associated with a sequence of client requests. The default backend obtains that mapping from a signed client cookie and can emit an updated cookie in a response. Flash messages are application-visible session content retained for later retrieval; session storage is replaceable through `SessionInterface`.

### evidence

- [Sessions](corpus:flask:evidence/be4c249245e3745e)
- [Flashing](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## state-implementation

### structure-and-representation

`SecureCookieSession` is a callback dictionary with access, modification, and permanence markers. `AppContext._session` holds the current mapping. The default backend serializes its values with `TaggedJSONSerializer` and an itsdangerous timed serializer into a cookie. `NullSession` supplies a fallback mapping when the backend cannot open a session.

### state-operations

`open_session` decodes the request cookie into a session mapping; application code and flash helpers read or change it. Response processing calls `save_session` for non-null sessions to set or remove the cookie under the backend's policy. `FlaskClient.session_transaction` opens a session for caller edits and saves it into the test client's cookies.

### evidence

- [Backend](corpus:flask:evidence/be4c249245e3745e)
- [Context binding](corpus:flask:evidence/d8838a605f9ff504)
- [Tagged serialization](corpus:flask:evidence/ref-809a1a0be75dbb21)
- [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)
- [Session transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| maintained-session | [Session](#state-implementation) | state-management:maintained-by | [Session backend](corpus:/architecture/architectural-participants/session-backend.md#role-and-scope) | The shipped backend derives the request mapping, tracks dictionary mutation and creates the outgoing cookie representation. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| maintained-coordinator | [Session](#state-implementation) | state-management:maintained-by | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Context session access sets the accessed marker, while flash helpers append/remove pending messages. Other application values are not assigned to the coordinator. | None. | [Access](corpus:flask:evidence/d8838a605f9ff504) [Flash](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| used-session | [Session](#state-implementation) | state-management:used-by-participant | [Session backend](corpus:/architecture/architectural-participants/session-backend.md#role-and-scope) | Backend policy reads values and access/modification/permanence markers to produce or remove the cookie representation. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| used-coordinator | [Session](#state-implementation) | state-management:used-by-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Contexts retain the current mapping, flash helpers use it, and response processing checks null status before requesting saving. | None. | [Context](corpus:flask:evidence/d8838a605f9ff504) [Response](corpus:flask:evidence/d3e0349504081bb5) [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| used-testing | [Session](#state-implementation) | state-management:used-by-participant | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | session_transaction exposes the backend mapping and requests saving into simulated client cookies. | None. | [Transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| used-test-code | [Session](#state-implementation) | state-management:used-by-participant | [Test code](corpus:/architecture/architectural-participants/test-code.md#role-and-scope) | The transaction yields the opened mapping to its caller for inspection/editing; actual caller edits and assertions are not established. | None. | [Yield contract](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| used-signer | [Session](#state-implementation) | state-management:used-by-participant | [Signer](corpus:/architecture/architectural-participants/cookie-signer.md#role-and-scope) | The backend passes current mapping values to dumps and receives decoded data from loads; only this serialization contribution is assigned to the signer. | None. | [Serializer calls](corpus:flask:evidence/be4c249245e3745e) |
| used-signals | [Session](#state-implementation) | state-management:used-by-participant | [Blinker](corpus:/architecture/architectural-participants/signal-delivery.md#role-and-scope) | message_flashed passes only the newly retained message and category to signal delivery, not the whole session mapping. | None. | [Flash send](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| used-application-observer | [Session](#state-implementation) | state-management:used-by-participant | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | Connected message_flashed observers receive the message/category just retained in session content. Their later behavior or arbitrary session reads are unestablished. | None. | [Flash boundary](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| represents-session | [Session](#state-definition) | state-management:represents-concept | [Client session](corpus:/domain/domain-concepts/session.md#concept-definition) | The mapping and default signed-cookie form represent information carried across related client requests under backend policy. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| represents-flash | [Session](#state-definition) | state-management:represents-concept | [Flashed message](corpus:/domain/domain-concepts/flash-message.md#concept-definition) | The pending _flashes portion represents categorized feedback awaiting retrieval; arbitrary other session values have application-defined meaning. | None. | [Flash helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
