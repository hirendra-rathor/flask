# Permanent session refresh

## configuration-description

### configuration

SESSION_REFRESH_EACH_REQUEST chooses whether a permanent, otherwise unchanged session should have its cookie set again during response processing.

### usage-and-effect

SessionInterface.should_set_cookie returns true when the mapping was modified or when it is permanent and the refresh setting is enabled. SecureCookieSessionInterface.save_session uses that choice before setting a nonempty session cookie.

### evidence

- [Refresh use](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-backend | [Refresh](#configuration-description) | subsystem-design:used-by-component | [Backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | The backend reads the refresh choice through should_set_cookie. | None. | [Refresh](corpus:flask:evidence/be4c249245e3745e) |
| qualifies-session | [Refresh](#configuration-description) | subsystem-design:qualifies-capability | [Load/save](corpus:/subsystem-design/local-capabilities/load-save-session.md#capability-description) | Refresh can cause an unchanged nonempty permanent session to emit a cookie. | None. | [Save](corpus:flask:evidence/be4c249245e3745e) |
