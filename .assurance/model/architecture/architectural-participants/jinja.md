# Jinja template engine

## role-and-scope

### role

Jinja selects or compiles templates and executes their rendering or generation using Flask-supplied context and source loaders.

### classifications

- external dependency

### scope

Jinja supplies the rendering engine even when it calls back to Flask's loader for template sources. Application template behavior remains application-supplied content; Flask owns its integration, not the engine's interpretation implementation.

### implementation-mapping

Flask's Environment extends Jinja Environment and installs a loader. Render/stream functions invoke get_or_select_template, from_string, render and generate.

### evidence

- [Engine consumption](corpus:flask:evidence/e4655695c5cdbf67)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Jinja](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The external engine renders templates and consumes Flask's source-loader contribution as part of that service. | None. | [Binding/calls](corpus:flask:evidence/e4655695c5cdbf67) |
| allocates-template-engine | [Jinja](#role-and-scope) | architecture:allocates-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | The consumed engine selects/compiles templates and renders/generates text from prepared values; Flask supplies lookup/context integration. | None. | [Jinja calls](corpus:flask:evidence/e4655695c5cdbf67) |
