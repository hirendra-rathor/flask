# I want application information available across client requests

## intended-outcome

### desired-outcome

Application authors and clients should be able to continue related interactions using session information opened and saved through the configured backend. The default backend carries that information in a signed client cookie under its configured lifetime and emission policy; continuity depends on client carriage and the backend's acceptance conditions.

### evidence

- [Session opening/saving](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-session | [Continuity](#intended-outcome) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Current session values can be represented for later related requests. | None. | [open_session/save_session](corpus:flask:evidence/be4c249245e3745e) |
| concerns-request | [Continuity](#intended-outcome) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The default backend reads the cookie supplied with each new request. | None. | [Cookie read](corpus:flask:evidence/be4c249245e3745e) |
| concerns-response | [Continuity](#intended-outcome) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Saving can set or delete the response cookie under the selected policy. | None. | [Cookie write/delete](corpus:flask:evidence/be4c249245e3745e) |
| concerns-settings | [Continuity](#intended-outcome) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Cookie scope, lifetime and refresh choices qualify the supported continuity. | None. | [Session policy getters](corpus:flask:evidence/be4c249245e3745e) |
