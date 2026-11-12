# Template renderer

## role-and-implementation

### role-kind

internal

### role

The renderer combines application template context with a selected template and provides rendered text or a stream. It locates templates across the application and its blueprints, exposes framework globals, and sends rendering notifications.

### implementation-mapping

The render/stream functions in `templating` call the application's Jinja environment. `Environment` and `DispatchingJinjaLoader` integrate application and blueprint loaders. `Flask.create_jinja_environment` binds framework globals, JSON dumping and reload settings; `update_template_context` calls registered processors. Template-loading diagnostics use `debughelpers` and the application logger.

### evidence

- [Rendering](corpus:flask:evidence/e4655695c5cdbf67)
- [Environment and context assembly](corpus:flask:evidence/d3e0349504081bb5)
- [Diagnostics](corpus:flask:evidence/ref-0082669d1582bc33)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-render | [Renderer](#role-and-implementation) | subsystem-design:offers-capability | [Render templates](corpus:/subsystem-design/local-capabilities/render-template.md#capability-description) | Render and stream functions expose completed text or iteration to callers. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| delegates-jinja | [Renderer](#role-and-implementation) | subsystem-design:delegates-to | [Jinja engine](corpus:/subsystem-design/components/jinja-engine.md#role-and-implementation) | Flask asks Jinja to select or compile a template and render/generate it. | None. | [Engine calls](corpus:flask:evidence/e4655695c5cdbf67) |
| delegates-context | [Renderer](#role-and-implementation) | subsystem-design:delegates-to | [Context manager](corpus:/subsystem-design/components/context-manager.md#role-and-implementation) | Streaming templates wrap generated text in stream_with_context to retain current bindings. | None. | [Streaming](corpus:flask:evidence/e4655695c5cdbf67) |
| delegates-json | [Renderer](#role-and-implementation) | subsystem-design:delegates-to | [JSON provider](corpus:/subsystem-design/components/json-provider.md#role-and-implementation) | The Jinja environment's JSON dump policy uses the application's JSON dumps method. | None. | [Environment policy](corpus:flask:evidence/d3e0349504081bb5) |
| delegates-signals | [Renderer](#role-and-implementation) | subsystem-design:delegates-to | [Signal delivery](corpus:/subsystem-design/components/signal-delivery.md#role-and-implementation) | Rendering sends before/after template notifications. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| belongs-templates | [Renderer](#role-and-implementation) | subsystem-design:belongs-to-participant | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Context preparation, loader integration and rendering entry points implement the framework's template responsibility. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) [Binding](corpus:flask:evidence/d3e0349504081bb5) |
