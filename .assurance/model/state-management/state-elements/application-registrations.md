# Application registrations

## state-definition

### state-description

Application registrations associate URL rules and endpoint names with views, callbacks, error handlers, blueprints, and extension data. They supply the application-specific behavior that Flask selects while handling requests and preparing other framework work.

### evidence

- [Setup](corpus:flask:evidence/c57b8f34cffef994)
- [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd)

## state-implementation

### structure-and-representation

The application holds a Werkzeug URL map and Python mappings/lists such as `view_functions`, scoped callback registries, `blueprints`, and `extensions`, plus its application CLI command group. Blueprint-local registries and command definitions are attached to the application when the blueprint is registered.

### state-operations

Scaffold registration methods store handlers; `App.add_url_rule` adds URL rules and endpoint bindings. Blueprint registration merges its recorded behavior. Dispatch selects views and hooks, template context assembly reads context processors, URL generation uses defaults and the map, and the route-list command reads rules. Extension contents are supplied by application extensions rather than interpreted by Flask.

### evidence

- [Setup](corpus:flask:evidence/c57b8f34cffef994)
- [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [Blueprint replay](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Dispatch and URL generation](corpus:flask:evidence/d3e0349504081bb5)
- [Route listing](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| maintained-coordinator | [Registrations](#state-implementation) | state-management:maintained-by | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Framework setup stores handlers, rules and blueprint bindings and replays deferred setup; this does not assign exclusive authority over application-supplied extension contents. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| used-coordinator | [Registrations](#state-implementation) | state-management:used-by-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Dispatch, URL construction and context matching use registered views, hooks and routing data. | None. | [Application](corpus:flask:evidence/d3e0349504081bb5) [Matching](corpus:flask:evidence/d8838a605f9ff504) |
| used-templates | [Registrations](#state-implementation) | state-management:used-by-participant | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Context assembly reads registered processors and source lookup visits registered blueprints. | None. | [Processors](corpus:flask:evidence/d3e0349504081bb5) [Loader](corpus:flask:evidence/e4655695c5cdbf67) |
| used-cli | [Registrations](#state-implementation) | state-management:used-by-participant | [CLI](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | Command lookup, route listing and shell preparation use registered commands, rules and processors. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| used-toolkit | [Registrations](#state-implementation) | state-management:used-by-participant | [Werkzeug](corpus:/architecture/architectural-participants/werkzeug.md#role-and-scope) | The bound toolkit map and adapter consume route rules for matching and URL building; other application registries are not assigned to the toolkit. | None. | [Map/rules](corpus:flask:evidence/c57b8f34cffef994) [Match](corpus:flask:evidence/d8838a605f9ff504) [Build](corpus:flask:evidence/d3e0349504081bb5) |
| used-developer | [Registrations](#state-implementation) | state-management:used-by-participant | [Developer](corpus:/architecture/architectural-participants/developer.md#role-and-scope) | The routes command exposes endpoint/method/path information to the command user, a partial observation of routing registrations rather than the complete registry. | None. | [Route output](corpus:flask:evidence/fed8939d1905b99b) |
| used-click | [Registrations](#state-implementation) | state-management:used-by-participant | [Click](corpus:/architecture/architectural-participants/click.md#role-and-scope) | AppGroup/FlaskGroup delegate lookup and invocation of retained command definitions to Click machinery; view and hook registries are outside this use. | None. | [Group lookup/registration](corpus:flask:evidence/fed8939d1905b99b) [Application command binding](corpus:flask:evidence/d3e0349504081bb5) |
| represents-registrations | [Registrations](#state-definition) | state-management:represents-concept | [Behavior registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | The retained view/hook/processor/handler declarations represent the application's available registered behavior, not its execution. | None. | [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd) [App](corpus:flask:evidence/c57b8f34cffef994) |
| represents-routes | [Registrations](#state-definition) | state-management:represents-concept | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | URL map rules and view-function bindings represent the registered route/endpoint portion. | None. | [add_url_rule](corpus:flask:evidence/c57b8f34cffef994) |
| represents-blueprint-attachments | [Registrations](#state-definition) | state-management:represents-concept | [Blueprint](corpus:/domain/domain-concepts/blueprint.md#concept-definition) | The application's blueprint bindings record attached bundles; their deferred definitions remain with the blueprint state. | None. | [Blueprint binding/replay](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| represents-command-definitions | [Registrations](#state-definition) | state-management:represents-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Retained application/blueprint command definitions supply the available command work, not completed invocation results. | None. | [App CLI](corpus:flask:evidence/d3e0349504081bb5) [Blueprint commands](corpus:flask:evidence/ref-500e23fcccfdcddd) |
