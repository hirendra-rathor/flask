# Template auto-reload

## configuration-description

### configuration

TEMPLATES_AUTO_RELOAD selects whether the created Jinja environment reloads templates. An unspecified choice follows application debug mode, unless auto_reload was already supplied in the application's Jinja options.

### usage-and-effect

Flask.create_jinja_environment resolves this setting into the auto_reload option passed to the environment. The debug setter also updates the environment's auto_reload when this setting is unspecified. The retained effect is the engine option binding.

### evidence

- [Environment](corpus:flask:evidence/d3e0349504081bb5)
- [Debug setter](corpus:flask:evidence/c57b8f34cffef994)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-renderer | [Reload](#configuration-description) | subsystem-design:used-by-component | [Renderer](corpus:/subsystem-design/components/template-renderer.md#role-and-implementation) | The renderer constructs its environment with the resolved reload choice. | None. | [Environment](corpus:flask:evidence/d3e0349504081bb5) |
| used-engine | [Reload](#configuration-description) | subsystem-design:used-by-component | [Jinja](corpus:/subsystem-design/components/jinja-engine.md#role-and-implementation) | Environment construction passes auto_reload to Jinja. | None. | [Environment](corpus:flask:evidence/d3e0349504081bb5) |
| qualifies-render | [Reload](#configuration-description) | subsystem-design:qualifies-capability | [Render templates](corpus:/subsystem-design/local-capabilities/render-template.md#capability-description) | The choice supplies reload behavior for template lookup in the created environment. | None. | [Environment](corpus:flask:evidence/d3e0349504081bb5) |
