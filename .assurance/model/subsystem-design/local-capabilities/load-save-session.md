# Load and save a session

## capability-description

### capability

The session backend supplies a mapping for request handling and can update the response's client cookie from that mapping. The default implementation uses signed cookies; an application-supplied backend can implement the same opening and saving contract with other storage.

### implementation-mapping

SecureCookieSessionInterface.open_session reads the request cookie and uses its configured serializer. save_session serializes nonempty data or removes the cookie when appropriate and applies cookie attributes. SessionInterface defines the replacement boundary; AppContext and response processing call it.

### evidence

- [Backend](corpus:flask:evidence/be4c249245e3745e)
- [Opening caller](corpus:flask:evidence/d8838a605f9ff504)
- [Saving caller](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-session | [Load/save](#capability-description) | subsystem-design:uses-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | The default backend derives a mapping from incoming cookies and serializes its current content for outgoing cookies. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| uses-settings | [Load/save](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | The backend reads signing keys, lifetime, cookie attributes and refresh selection. | None. | [Settings use](corpus:flask:evidence/be4c249245e3745e) |
| backend-exchange | [Load/save](#capability-description) | subsystem-design:participates-in-exchange | [Session load/save](corpus:/subsystem-interfaces/exchanges/session-load-save.md#exchange-behavior) | The backend receives open/save calls and supplies mappings or changes to the provided response. | None. | [Contract](corpus:flask:evidence/be4c249245e3745e) |
| cookie-exchange | [Load/save](#capability-description) | subsystem-design:participates-in-exchange | [Session cookie](corpus:/subsystem-interfaces/exchanges/session-cookie.md#exchange-behavior) | The default backend consumes the incoming session cookie and writes or removes the outgoing cookie representation. | None. | [Cookie operations](corpus:flask:evidence/be4c249245e3745e) |
| domain-session | [Load/save](#capability-description) | subsystem-design:contributes-to-required-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Backend opening supplies the current mapping and saving updates its representation according to selected policy; other storage remains replacement work. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| domain-handle | [Load/save](#capability-description) | subsystem-design:contributes-to-required-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Default saving can add/delete the response's session cookie during response processing. | None. | [save_session](corpus:flask:evidence/be4c249245e3745e) [process_response](corpus:flask:evidence/d3e0349504081bb5) |
