# Render application templates

## capability-description

### capability

An application author supplies a template name/object or source text and values to produce application text through Flask's rendering integration.

### expected-result

The caller receives completed text or a text iterator. Flask supplies application/blueprint lookup, framework globals and registered context values; the selected engine interprets the template. Streaming can preserve the active context while text is generated.

### evidence

- [Rendering and lookup](corpus:flask:evidence/e4655695c5cdbf67)
- [Environment/context preparation](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-content | [Render](#capability-description) | domain:contributes-to-intent | [Content forms](corpus:/domain/intentions/produce-representations.md#intended-outcome) | Template interpretation supplies application text or iteration to its caller. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| supports-adaptation | [Render](#capability-description) | domain:contributes-to-intent | [Adapt services](corpus:/domain/intentions/adapt-services.md#intended-outcome) | Application environment choices, blueprint loaders and registered context processors adapt rendering integration. | None. | [Environment/processors](corpus:flask:evidence/d3e0349504081bb5) [Loader](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-template | [Render](#capability-description) | domain:concerns-concept | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Template source and values are selected and rendered to text. | None. | [render/stream functions](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-context | [Render](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Rendering uses the active application and default request/g values; streaming preserves bindings. | None. | [Context processor/rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-settings | [Render](#capability-description) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Environment creation uses application choices and exposes config to templates. | None. | [create_jinja_environment](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-blueprint | [Render](#capability-description) | domain:concerns-concept | [Blueprint](corpus:/domain/domain-concepts/blueprint.md#concept-definition) | Source lookup considers attached blueprint template loaders. | None. | [DispatchingJinjaLoader](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-registration | [Render](#capability-description) | domain:concerns-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Scoped context processors supply registered application values. | None. | [update_template_context](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-request | [Render](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The default processor adds the request object when rendering is request-bound. | None. | [Default processor](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-session-access | [Render](#capability-description) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The environment installs a contextual session proxy for template access; actual template reads are application-dependent. | None. | [Globals](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-notices | [Render](#capability-description) | domain:concerns-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | Rendering emits named before/after events, with streaming's after-event occurring after generation completes. | None. | [_render/_stream](corpus:flask:evidence/e4655695c5cdbf67) |
