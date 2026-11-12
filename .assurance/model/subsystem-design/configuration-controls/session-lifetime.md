# Permanent session lifetime

## configuration-description

### configuration

The permanent-session lifetime supplies a maximum age for loading the default signed session cookie and an expiry offset when a session is marked permanent. It is a duration choice distinct from whether permanent cookies are refreshed on each request.

### usage-and-effect

The application exposes PERMANENT_SESSION_LIFETIME as permanent_session_lifetime. The backend passes its seconds as max_age during loads; get_expiration_time adds it to the current time for permanent sessions before save_session sets the response cookie.

### evidence

- [Lifetime use](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-backend | [Lifetime](#configuration-description) | subsystem-design:used-by-component | [Backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | The backend reads the duration for loads and permanent cookie expiry. | None. | [Lifetime](corpus:flask:evidence/be4c249245e3745e) |
| qualifies-session | [Lifetime](#configuration-description) | subsystem-design:qualifies-capability | [Load/save](corpus:/subsystem-design/local-capabilities/load-save-session.md#capability-description) | The duration qualifies accepted cookie age and permanent-session outgoing expiry. | None. | [Lifetime](corpus:flask:evidence/be4c249245e3745e) |
