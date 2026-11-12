# Application setup

## role-and-implementation

### role-kind

internal

### role

Application setup accepts the application's routes, hooks, configuration, and blueprints so runtime work can locate application-specific behavior. It also replays reusable blueprint definitions into an application. This responsibility includes configuration loading and registration rather than executing the registered views.

### implementation-mapping

`Scaffold` supplies shared registration methods and registries. Sans-I/O `App` owns application configuration, URL rules, and blueprint attachment; sans-I/O `Blueprint` records and applies deferred setup. Concrete `Flask` and `Blueprint` add runtime-bound resources and command groups. `Config` supplies the configuration loaders.

### evidence

- [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [App](corpus:flask:evidence/c57b8f34cffef994)
- [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Config](corpus:flask:evidence/eefcbaf3dbb10788)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-registration | [Setup](#role-and-implementation) | subsystem-design:offers-capability | [Register behavior](corpus:/subsystem-design/local-capabilities/register-behavior.md#capability-description) | Setup stores routes and callbacks and replays blueprints into the application. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| maintains-registration | [Setup](#role-and-implementation) | subsystem-design:maintains-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | Registration methods add rules, handlers, and blueprint bindings. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) |
| maintains-settings | [Setup](#role-and-implementation) | subsystem-design:maintains-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Application construction creates Config and its loaders populate settings. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Config](corpus:flask:evidence/eefcbaf3dbb10788) |
| maintains-blueprint | [Setup](#role-and-implementation) | subsystem-design:maintains-state | [Blueprint definitions](corpus:/state-management/state-elements/blueprint-registrations.md#state-definition) | Blueprint methods retain deferred setup and nesting. | None. | [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| delegates-routing | [Setup](#role-and-implementation) | subsystem-design:delegates-to | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | Setup adds constructed rules to the Werkzeug URL map. | None. | [Rules](corpus:flask:evidence/c57b8f34cffef994) |
| delegates-command-group | [Setup](#role-and-implementation) | subsystem-design:delegates-to | [Developer CLI](corpus:/subsystem-design/components/developer-cli.md#role-and-implementation) | Concrete application/blueprint construction creates AppGroup instances for application command registration. | None. | [Application construction](corpus:flask:evidence/d3e0349504081bb5) [Blueprint construction](corpus:flask:evidence/ref-30595964c383760a) |
| belongs-coordinator | [Setup](#role-and-implementation) | subsystem-design:belongs-to-participant | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Retaining application definitions and replaying blueprints are the coordinator's framework setup responsibility. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
