# Session cookie attributes

## configuration-description

### configuration

The session cookie policy selects its name and outgoing domain, path, Secure, HttpOnly, SameSite and Partitioned attributes. These bindings collectively describe which cookie the default backend reads and how it instructs the client to scope and handle the outgoing cookie.

### usage-and-effect

SessionInterface cookie getters read SESSION_COOKIE settings, with APPLICATION_ROOT supplying a path fallback. The default backend uses the name to find request data and passes the attributes to response.set_cookie or delete_cookie. Client enforcement is outside Flask's inspected source.

### evidence

- [Cookie binding and use](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-backend | [Cookie policy](#configuration-description) | subsystem-design:used-by-component | [Backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | The backend reads cookie identity and applies outgoing attributes. | None. | [Cookies](corpus:flask:evidence/be4c249245e3745e) |
| qualifies-session | [Cookie policy](#configuration-description) | subsystem-design:qualifies-capability | [Load/save](corpus:/subsystem-design/local-capabilities/load-save-session.md#capability-description) | The settings select the incoming cookie name and attributes of outgoing updates/deletions. | None. | [Cookies](corpus:flask:evidence/be4c249245e3745e) |
