# Render a template

## capability-description

### capability

Application code requests rendering by template name, template object or source string with context values. It can receive completed text or an iterator of text for a streaming response. Flask adds registered application/blueprint context values and framework globals before Jinja performs template work.

### implementation-mapping

render_template and render_template_string select/compile templates and call _render. Stream counterparts call _stream and preserve the context during generation. Flask.update_template_context invokes registered context processors, and DispatchingJinjaLoader supplies application/blueprint template lookup.

### evidence

- [Rendering functions](corpus:flask:evidence/e4655695c5cdbf67)
- [Context processors](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-context | [Render](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Rendering selects the active app and supplies g and, when present, request access; streaming preserves that context. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| uses-registrations | [Render](#capability-description) | subsystem-design:uses-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | Template context assembly calls scoped processors and template lookup visits registered blueprints. | None. | [Context](corpus:flask:evidence/d3e0349504081bb5) [Loader](corpus:flask:evidence/e4655695c5cdbf67) |
| uses-settings | [Render](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Environment construction reads reload configuration and exposes app.config as a template global. | None. | [Environment](corpus:flask:evidence/d3e0349504081bb5) |
| engine-exchange | [Render](#capability-description) | subsystem-design:participates-in-exchange | [Template rendering](corpus:/subsystem-interfaces/exchanges/template-rendering.md#exchange-behavior) | Rendering supplies template selection/source and context to Jinja and returns rendered text or iteration. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| processor-exchange | [Render](#capability-description) | subsystem-design:participates-in-exchange | [Handler calls and results](corpus:/subsystem-interfaces/exchanges/handler-invocation.md#exchange-behavior) | Context processors are application callbacks whose returned mappings augment template values. | None. | [Context processors](corpus:flask:evidence/d3e0349504081bb5) |
| lifecycle-exchange | [Render](#capability-description) | subsystem-design:participates-in-exchange | [Lifecycle notices](corpus:/subsystem-interfaces/exchanges/lifecycle-notifications.md#exchange-behavior) | The renderer emits before/after template notices carrying template and context. | None. | [Signals](corpus:flask:evidence/e4655695c5cdbf67) |
| domain-render | [Render](#capability-description) | subsystem-design:contributes-to-required-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Source lookup, values and engine calls supply the text/iteration rendering result. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| domain-context | [Render](#capability-description) | subsystem-design:contributes-to-required-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Streaming rendering preserves the captured context while generation uses it. | None. | [_stream](corpus:flask:evidence/e4655695c5cdbf67) |
| domain-observe | [Render](#capability-description) | subsystem-design:contributes-to-required-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Before/after rendering sends supply template/context information, with the streaming completion send after generation completes. | None. | [_render/_stream](corpus:flask:evidence/e4655695c5cdbf67) |
