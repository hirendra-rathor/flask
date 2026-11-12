# Session load and save calls

## exchange-behavior

### exchange-description

An open_session call supplies the application and request and receives a session mapping or no mapping. A save_session call supplies the application, current mapping and response for the backend to update or persist. No returned mapping causes the context to use a null session; custom backend completion beyond this contract is not inferred.

### sender-and-receiver

AppContext sends opening arguments to the configured backend and receives the mapping. Response processing sends the mapping and response to its saving operation. The test client's session transaction also makes these calls around caller edits.

### implementation-mapping

AppContext._get_session calls open_session and make_null_session. Flask.process_response calls save_session for non-null sessions; FlaskClient.session_transaction directly opens/saves and updates its cookie store. SessionInterface supplies the contract and SecureCookieSessionInterface its default implementation.

### evidence

- [Context caller](corpus:flask:evidence/d8838a605f9ff504)
- [Response caller](corpus:flask:evidence/d3e0349504081bb5)
- [Testing caller](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)
- [Backend](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-backend | [Calls](#exchange-behavior) | subsystem-interfaces:uses-interface | [Backend API](corpus:/subsystem-interfaces/interfaces/session-backend-api.md#interface-definition) | The exchange invokes the configured session contract. | None. | [Contract](corpus:flask:evidence/be4c249245e3745e) |
| carries-session | [Calls](#exchange-behavior) | subsystem-interfaces:carries-state | [Session](corpus:/state-management/state-elements/client-session.md#state-definition) | The open reply provides the current mapping and save receives its current contents and flags. | None. | [Contract and implementation](corpus:flask:evidence/be4c249245e3745e) |
| carries-settings | [Calls](#exchange-behavior) | subsystem-interfaces:carries-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Both calls pass the application whose settings the default backend reads for signing and cookie behavior. This is an object reference to the settings' owner, not a copied configuration document. | None. | [Backend parameters and reads](corpus:flask:evidence/be4c249245e3745e) |
| concept-application | [Backend calls](#exchange-behavior) | subsystem-interfaces:carries-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Opening/saving receive the configured application whose backend/policy is in use. | None. | [SessionInterface and calls](corpus:flask:evidence/be4c249245e3745e) |
| concept-request | [Backend calls](#exchange-behavior) | subsystem-interfaces:carries-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Opening receives the current request from which the default backend reads cookies. | None. | [open_session](corpus:flask:evidence/be4c249245e3745e) [Caller](corpus:flask:evidence/d8838a605f9ff504) |
| concept-session | [Backend calls](#exchange-behavior) | subsystem-interfaces:carries-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The open reply supplies a session mapping and the save call supplies its current values/flags. | None. | [Session contract](corpus:flask:evidence/be4c249245e3745e) |
| concept-response | [Backend calls](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Saving receives the response to which the default backend adds or removes cookie information. | None. | [save_session](corpus:flask:evidence/be4c249245e3745e) |
| concept-settings | [Backend calls](#exchange-behavior) | subsystem-interfaces:carries-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | The supplied application is an object reference through which the default backend reads signing/cookie policy, rather than a copied settings document. | None. | [Backend parameters/reads](corpus:flask:evidence/be4c249245e3745e) |
