# Flask template integrator

## role-and-scope

### role

The template integrator connects application and blueprint template sources, context values and framework globals to Jinja rendering. It returns rendered text or a stream and publishes rendering notifications.

### classifications

- internal

### scope

Flask supplies source lookup, context preparation and rendering entry points. Jinja supplies template interpretation and execution; application templates and context processors retain their own behavior.

### implementation-mapping

`templating.Environment`, `DispatchingJinjaLoader` and the render/stream functions implement integration. `Flask.create_jinja_environment` binds globals and JSON policy, and `update_template_context` invokes registered processors.

### evidence

- [Template integration](corpus:flask:evidence/e4655695c5cdbf67)
- [Environment and processors](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Integrator](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | Template preparation, source lookup and rendering integration are internal framework work. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| allocates-render | [Integrator](#role-and-scope) | architecture:allocates-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | It supplies source lookup, context preparation and render/stream invocation; Jinja interprets supplied templates. | None. | [Rendering/loader](corpus:flask:evidence/e4655695c5cdbf67) |
| allocates-event-sources | [Integrator](#role-and-scope) | architecture:allocates-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Before/after template send sites supply event notices and template/context values, including the bounded streaming completion condition. | None. | [_render/_stream sends](corpus:flask:evidence/e4655695c5cdbf67) |
| allocates-stream-context | [Integrator](#role-and-scope) | architecture:allocates-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Streaming rendering preserves the captured context while generating text; context binding internals remain coordinator work. | None. | [_stream](corpus:flask:evidence/e4655695c5cdbf67) |
