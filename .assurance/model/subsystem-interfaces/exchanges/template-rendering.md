# Template inputs and rendered text

## exchange-behavior

### exchange-description

Flask supplies a template name/object or source string to Jinja and supplies context values for rendering. Jinja returns template objects and rendered text or text iteration. The configured Flask loader can supply template source, filename and freshness callback in response to the environment's lookup.

### sender-and-receiver

Flask's renderer sends template selection/source and value mappings to Jinja and receives templates and generated text. Jinja's configured loader contract requests template source from Flask's dispatching loader; that loader returns source information found in application or blueprint loaders.

### implementation-mapping

render_template and source/stream variants call get_or_select_template/from_string then render/generate. Environment binds DispatchingJinjaLoader; get_source dispatches to application/blueprint loaders and returns their result. create_jinja_environment installs config and context globals.

### evidence

- [Template calls and loader](corpus:flask:evidence/e4655695c5cdbf67)
- [Environment globals](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-engine | [Template exchange](#exchange-behavior) | subsystem-interfaces:uses-interface | [Engine API](corpus:/subsystem-interfaces/interfaces/template-engine-api.md#interface-definition) | The exchange uses Jinja selection/rendering and its configured loader contract. | None. | [Engine calls](corpus:flask:evidence/e4655695c5cdbf67) |
| carries-context | [Template exchange](#exchange-behavior) | subsystem-interfaces:carries-state | [Execution context](corpus:/state-management/state-elements/execution-context.md#state-definition) | The default context processor supplies g and, for a request context, the request object to template values. It does not send the complete AppContext record. | None. | [Default processor](corpus:flask:evidence/e4655695c5cdbf67) |
| carries-settings | [Template exchange](#exchange-behavior) | subsystem-interfaces:carries-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | The created Jinja environment exposes the application's Config object as the config global. | None. | [Environment globals](corpus:flask:evidence/d3e0349504081bb5) |
| concept-template | [Rendering](#exchange-behavior) | subsystem-interfaces:carries-concept | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Selection/source values identify the template to interpret; loader replies supply its source and the engine returns its generated text/iteration. | None. | [Lookup/render/loader](corpus:flask:evidence/e4655695c5cdbf67) |
| concept-context | [Rendering](#exchange-behavior) | subsystem-interfaces:carries-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Prepared rendering values include g and an available request, plus contextual proxies; no complete AppContext record is sent by normal rendering. | None. | [Default processor](corpus:flask:evidence/e4655695c5cdbf67) [Globals](corpus:flask:evidence/d3e0349504081bb5) |
| concept-request | [Rendering](#exchange-behavior) | subsystem-interfaces:carries-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The default processor supplies the request object when a request context exists. | None. | [Default processor](corpus:flask:evidence/e4655695c5cdbf67) |
| concept-settings | [Rendering](#exchange-behavior) | subsystem-interfaces:carries-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | The environment exposes the application's configuration object as a global for template use, without proving a template reads it. | None. | [create_jinja_environment](corpus:flask:evidence/d3e0349504081bb5) |
| concept-session-access | [Rendering](#exchange-behavior) | subsystem-interfaces:carries-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Environment globals supply the contextual session proxy as an access reference; this does not establish transmission or reading of session values by a particular template. | None. | [Session global binding](corpus:flask:evidence/d3e0349504081bb5) |
