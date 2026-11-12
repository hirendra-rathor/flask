# Jinja template engine

## role-and-implementation

### role-kind

external dependency

### role

Jinja supplies template selection, compilation, rendering and generation for Flask's template integration. Flask contributes the application loaders and context; Jinja performs the requested template work.

### implementation-mapping

Flask's Environment subclasses Jinja Environment and supplies the dispatching loader. Rendering calls get_or_select_template or from_string, then Template.render or generate. The retained contribution is evidenced at these calls, without claiming dependency-internal coverage.

### evidence

- [Engine binding and calls](corpus:flask:evidence/e4655695c5cdbf67)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| requests-template-source | [Engine](#role-and-implementation) | subsystem-design:delegates-to | [Template renderer](corpus:/subsystem-design/components/template-renderer.md#role-and-implementation) | Flask installs its DispatchingJinjaLoader as the environment loader, supplying template-source lookup to the engine. The claim is limited to this callback binding. | None. | [Loader binding](corpus:flask:evidence/e4655695c5cdbf67) |
| belongs-jinja | [Engine contribution](#role-and-implementation) | subsystem-design:belongs-to-participant | [Jinja](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | The consumed selection/compilation/rendering contribution is supplied by the external engine, even when it uses Flask's loader. | None. | [Binding/calls](corpus:flask:evidence/e4655695c5cdbf67) |
