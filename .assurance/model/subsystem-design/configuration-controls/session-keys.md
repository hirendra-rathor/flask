# Session signing keys

## configuration-description

### configuration

The application's secret key and fallback keys supply the key material passed to the default session cookie serializer. Without a current secret key, that backend cannot create its signing serializer and opening returns no session mapping.

### usage-and-effect

SecureCookieSessionInterface.get_signing_serializer reads app.secret_key and SECRET_KEY_FALLBACKS and constructs URLSafeTimedSerializer. The resulting object is used by open_session and save_session. Fallback-key behavior is established through Flask's supplied key list; the dependency's signing internals are outside this account.

### evidence

- [Signing configuration](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-backend | [Keys](#configuration-description) | subsystem-design:used-by-component | [Backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | The backend reads the current and fallback keys. | None. | [Keys](corpus:flask:evidence/be4c249245e3745e) |
| used-signer | [Keys](#configuration-description) | subsystem-design:used-by-component | [Signer](corpus:/subsystem-design/components/cookie-signer.md#role-and-implementation) | The backend passes the key list to the timed serializer constructor. | None. | [Constructor](corpus:flask:evidence/be4c249245e3745e) |
| qualifies-session | [Keys](#configuration-description) | subsystem-design:qualifies-capability | [Load/save](corpus:/subsystem-design/local-capabilities/load-save-session.md#capability-description) | Keys configure signed cookie load/save; absence of a current key prevents a default serializer. | None. | [Backend](corpus:flask:evidence/be4c249245e3745e) |
