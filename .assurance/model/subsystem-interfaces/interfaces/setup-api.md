# Application setup API

## interface-definition

### interface-kind

API

### process-locality

- in-process

### purpose-and-boundary

Application and extension code declare routes, hooks, blueprint bundles and settings through Flask setup methods. This boundary separates declaring application behavior from Flask retaining it and later selecting it for execution.

### providers-and-consumers

The Flask application coordinator supplies Scaffold/App/Blueprint methods and Config loaders. Application and extension code consumes them by supplying declarations and configuration. Deferred blueprint callbacks receive setup state when a bundle is attached.

### evidence

- [Scaffold registration](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [App registration](corpus:flask:evidence/c57b8f34cffef994)
- [Blueprint replay](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Config loading](corpus:flask:evidence/eefcbaf3dbb10788)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-coordinator | [Setup API](#interface-definition) | subsystem-interfaces:binds-provider | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Scaffold/App/Blueprint registration and Config loaders supply framework setup services. | None. | [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd) [Setup](corpus:flask:evidence/c57b8f34cffef994) [Config](corpus:flask:evidence/eefcbaf3dbb10788) |
| consumer-application | [Setup API](#interface-definition) | subsystem-interfaces:binds-consumer | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | Application/extension callers supply behavior declarations and configuration through the public setup contract for their application. | None. | [Registration contract](corpus:flask:evidence/ref-426c9d8938b9fecd) [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
