# Retain client session information

## capability-description

### capability

An application author reads and changes session information during related client interactions. The configured backend opens its mapping and saves an appropriate representation; operators choose default-backend signing, lifetime and cookie policy.

### expected-result

The current request obtains a session mapping and saving can update or delete a representation for later requests. The default backend validates signed cookies and issues signed data under its selected policy, using configured current/fallback keys. A replacement backend owns its own persistence, and actual client retention remains external.

### evidence

- [Session contract/open/save](corpus:flask:evidence/be4c249245e3745e)
- [Context and response integration](corpus:flask:evidence/d8838a605f9ff504)
- [Response integration](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-continuity | [Retain session](#capability-description) | domain:contributes-to-intent | [Continuity](corpus:/domain/intentions/session-continuity.md#intended-outcome) | Opening/saving supplies session information across requests under backend and client conditions. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| supports-integrity | [Retain session](#capability-description) | domain:contributes-to-intent | [Validation](corpus:/domain/intentions/session-integrity.md#intended-outcome) | Default restoration depends on timed serializer acceptance and discards rejected cookie contents. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) |
| supports-rotation | [Retain session](#capability-description) | domain:contributes-to-intent | [Rotation](corpus:/domain/intentions/session-key-rotation.md#intended-outcome) | The default backend passes configured previous/current keys to its serializer and uses it for opening and new cookies. | None. | [Serializer binding/use](corpus:flask:evidence/be4c249245e3745e) |
| supports-adaptation | [Retain session](#capability-description) | domain:contributes-to-intent | [Service adaptation](corpus:/domain/intentions/adapt-services.md#intended-outcome) | Opening and saving through SessionInterface allow an application-selected backend to supply different storage. | None. | [SessionInterface](corpus:flask:evidence/be4c249245e3745e) |
| concerns-session | [Retain session](#capability-description) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The mapping and its representation are the information retained or removed. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
| concerns-request | [Retain session](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The default backend reads the incoming request cookie. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) |
| concerns-response | [Retain session](#capability-description) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Saving can set or remove a response cookie and its policy headers. | None. | [save_session](corpus:flask:evidence/be4c249245e3745e) |
| concerns-settings | [Retain session](#capability-description) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Keys, age, cookie attributes and refresh choices qualify default session work. | None. | [Session settings reads](corpus:flask:evidence/be4c249245e3745e) |
