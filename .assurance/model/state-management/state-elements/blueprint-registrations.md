# Deferred blueprint registrations

## state-definition

### state-description

A blueprint retains a reusable collection of setup operations and nested blueprints to apply when attached to an application. The retained operations separate defining a feature bundle from choosing its application registration name and URL placement.

### evidence

- [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd)

## state-implementation

### structure-and-representation

`Blueprint.deferred_functions` stores setup callables, while `_blueprints` stores nested blueprint objects with options. The blueprint also has scoped handler registries inherited from `Scaffold`, registration defaults, and a CLI command group.

### state-operations

`record`, `record_once`, and route decorators append deferred work. `register_blueprint` records nesting. `Blueprint.register` builds setup state, merges handlers into the application, invokes deferred functions, attaches commands, and registers nested blueprints with combined options.

### evidence

- [Deferred work and replay](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Concrete blueprint CLI](corpus:flask:evidence/ref-30595964c383760a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| maintained-coordinator | [Blueprint definitions](#state-implementation) | state-management:maintained-by | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Blueprint record/nesting methods retain deferred operations and registration options. | None. | [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| used-coordinator | [Blueprint definitions](#state-implementation) | state-management:used-by-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Registration reads deferred operations, handlers, commands and nesting to configure an application. | None. | [Replay](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| represents-blueprint | [Deferred registrations](#state-definition) | state-management:represents-concept | [Blueprint](corpus:/domain/domain-concepts/blueprint.md#concept-definition) | Deferred callables, local registries and nested bundles represent the reusable blueprint setup contribution before or during attachment. | None. | [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| represents-declarations | [Deferred registrations](#state-definition) | state-management:represents-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Recorded setup callables and registries retain the declarations to apply to an application, without implying handler execution. | None. | [Record/replay](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| represents-commands | [Deferred registrations](#state-definition) | state-management:represents-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | The blueprint's retained CLI group supplies command definitions when attachment binds them to the application. | None. | [Concrete CLI binding](corpus:flask:evidence/ref-30595964c383760a) [Registration](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| represents-route-declarations | [Deferred registrations](#state-definition) | state-management:represents-concept | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | Recorded rule/endpoint/view setup retains pending route declarations until attachment applies them to the chosen application. | None. | [Blueprint.add_url_rule/record](corpus:flask:evidence/ref-500e23fcccfdcddd) |
