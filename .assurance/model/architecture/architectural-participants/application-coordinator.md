# Flask application coordinator

## role-and-scope

### role

The Flask application coordinator retains an application's setup, selects its registered behavior for incoming requests, and binds the context that framework and application work use. Its contextual helpers build URLs, construct file responses and manage flashed messages. Application resource methods also open package or instance files for caller use. It coordinates separately responsible session, template and JSON services while application callbacks supply application-specific results.

### classifications

- internal

### scope

This responsibility covers framework registration and blueprint replay, WSGI dispatch and response adaptation, execution-context binding, and application conveniences. It does not absorb the application handlers or the supplied service implementations it calls. Explicit contexts and streamed responses use the same context responsibility outside ordinary request dispatch.

### implementation-mapping

`Flask` and sans-I/O `App`/`Scaffold` retain configuration and registration and implement dispatch. `Flask.open_resource` and `open_instance_resource` supply the application resource-file handles. Blueprint classes retain and replay feature setup. `AppContext`, globals and context wrappers bind active execution data. `helpers`, wrappers and view adapters supply the corresponding conveniences, HTTP integration and callable adaptation.

### evidence

- [Application](corpus:flask:evidence/d3e0349504081bb5)
- [Setup](corpus:flask:evidence/c57b8f34cffef994)
- [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Context](corpus:flask:evidence/d8838a605f9ff504)
- [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Coordinator](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The coordinator supplies the internal framework setup, dispatch, binding and helper work in applications, commands and testing. | None. | [Application](corpus:flask:evidence/d3e0349504081bb5) [Context](corpus:flask:evidence/d8838a605f9ff504) |
| allocates-compose | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Compose application](corpus:/domain/required-capabilities/compose-application.md#capability-description) | The coordinator retains registrations/settings, replays blueprints and binds selected framework services; authors supply declarations. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) [Application](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-handling | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | It matches/selects application behavior, adapts results and returns WSGI response work; application callbacks and host transport remain separately assigned. | None. | [Dispatch/WSGI](corpus:flask:evidence/d3e0349504081bb5) [Matching](corpus:flask:evidence/d8838a605f9ff504) |
| allocates-context | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Context construction, binding/proxies and streaming wrappers provide current application/request data and restoration. | None. | [Contexts](corpus:flask:evidence/d8838a605f9ff504) [Streaming](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| allocates-session-integration | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Context/response integration requests backend opening and saving; it does not absorb backend storage/signing responsibility. | None. | [Opening](corpus:flask:evidence/d8838a605f9ff504) [Saving](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-template-binding | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Application environment/global/provider binding and scoped context-processor invocation supply integration inputs to the separately responsible renderer. | None. | [Environment/processors](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-json-binding | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Convert JSON](corpus:/domain/required-capabilities/convert-json.md#capability-description) | Application selection binds the provider to request decoding, response adaptation and template JSON policy; conversion remains provider work. | None. | [Request binding](corpus:flask:evidence/d8838a605f9ff504) [Response/template binding](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-url | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Build URLs](corpus:/domain/required-capabilities/build-url.md#capability-description) | Context adapter selection, defaults and toolkit construction supply endpoint addresses. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-files | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Produce file responses](corpus:/domain/required-capabilities/serve-file.md#capability-description) | Contextual helpers and static-route adapters bind application/request options to toolkit file work. | None. | [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) [Statics](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-feedback | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Retain/retrieve feedback](corpus:/domain/required-capabilities/flash-feedback.md#capability-description) | Flash helpers add pending session feedback and transfer retrieval into the active-context cache. | None. | [Helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| allocates-resources | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Access resources](corpus:/domain/required-capabilities/access-resources.md#capability-description) | Application resource methods open package-relative or instance-relative files under their supported modes. | None. | [open_resource/open_instance_resource](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-event-sources | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Request/context/message send sites supply named notices and values; delivery and observer work remain separate. | None. | [App sends](corpus:flask:evidence/d3e0349504081bb5) [Context sends](corpus:flask:evidence/d8838a605f9ff504) [Flash sends](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
| allocates-command-context | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | The coordinator supplies application context and shell namespace used by CLI integration, without owning command discovery/parsing. | None. | [Context factories/shell namespace](corpus:flask:evidence/d3e0349504081bb5) [CLI use](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-testing-bindings | [Coordinator](#role-and-scope) | architecture:allocates-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | Application factories bind selected test-client/runner classes and request-context construction for testing tools. | None. | [test_client/test_cli_runner/test_request_context](corpus:flask:evidence/d3e0349504081bb5) |
