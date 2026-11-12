# Template engine API

## interface-definition

### interface-kind

API

### process-locality

- in-process

### purpose-and-boundary

Flask's template integration asks Jinja to obtain or compile templates and render them with context values. Flask also installs an environment loader that supplies application/blueprint template sources back to the engine. The boundary retains this engine contract rather than describing all application template behavior.

### providers-and-consumers

Jinja provides template selection, compilation and render/generate operations consumed by Flask's template integrator. The integrator supplies the source-loader contribution consumed by the configured engine. Both complementary roles have participant bindings below.

### evidence

- [Jinja API and loader binding](corpus:flask:evidence/e4655695c5cdbf67)
- [Environment construction](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-jinja | [Engine API](#interface-definition) | subsystem-interfaces:binds-provider | [Jinja](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | Jinja supplies template selection, compilation and render/generate operations. | None. | [Engine calls](corpus:flask:evidence/e4655695c5cdbf67) |
| consumer-templates | [Engine API](#interface-definition) | subsystem-interfaces:binds-consumer | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Flask's renderer requests the engine's template work with prepared context. | None. | [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| provider-loader | [Engine API](#interface-definition) | subsystem-interfaces:binds-provider | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | The installed DispatchingJinjaLoader supplies application/blueprint source lookup to the engine; this is a complementary loader service role. | None. | [Loader binding](corpus:flask:evidence/e4655695c5cdbf67) |
| consumer-loader | [Engine API](#interface-definition) | subsystem-interfaces:binds-consumer | [Jinja](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | The configured engine consumes the source loader installed by Flask while supplying rendering. | None. | [Environment loader](corpus:flask:evidence/e4655695c5cdbf67) |
