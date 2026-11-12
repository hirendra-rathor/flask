# Application setup declarations

## exchange-behavior

### exchange-description

Setup calls communicate route rules, endpoint handlers, callback functions, blueprint definitions/options and configuration values to Flask. These are declarations to retain or apply, rather than evidence that the registered application behavior has executed.

### sender-and-receiver

Application/extension code supplies declarations to Scaffold, App, Blueprint and Config methods. During blueprint attachment, the blueprint registrar passes BlueprintSetupState to its deferred functions, which apply the recorded registrations to the application.

### implementation-mapping

Scaffold decorators retain function arguments; App.add_url_rule binds rules/views. Blueprint.record and register connect deferred callbacks to setup state and application methods. Config loading methods receive values or loader results and populate settings.

### evidence

- [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [App](corpus:flask:evidence/c57b8f34cffef994)
- [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Config](corpus:flask:evidence/eefcbaf3dbb10788)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-setup | [Declarations](#exchange-behavior) | subsystem-interfaces:uses-interface | [Setup API](corpus:/subsystem-interfaces/interfaces/setup-api.md#interface-definition) | Application declarations and blueprint replay use the setup surface. | None. | [Setup](corpus:flask:evidence/c57b8f34cffef994) [Blueprint](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| carries-blueprint | [Declarations](#exchange-behavior) | subsystem-interfaces:carries-state | [Deferred registrations](corpus:/state-management/state-elements/blueprint-registrations.md#state-definition) | Attachment receives a Blueprint whose deferred operations and registries are read and applied to the application; the claim concerns that bundle, rather than every registration call. | None. | [Attachment and replay](corpus:flask:evidence/c57b8f34cffef994) [Replay](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| concept-registration | [Declarations](#exchange-behavior) | subsystem-interfaces:carries-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Caller-supplied hooks/views/processors are declarations for later selection rather than reports of execution. | None. | [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd) |
| concept-route | [Declarations](#exchange-behavior) | subsystem-interfaces:carries-concept | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | Rule text, endpoint names and views communicate the requested route binding. | None. | [add_url_rule](corpus:flask:evidence/c57b8f34cffef994) |
| concept-blueprint | [Declarations](#exchange-behavior) | subsystem-interfaces:carries-concept | [Blueprint](corpus:/domain/domain-concepts/blueprint.md#concept-definition) | Attachment receives a reusable bundle with naming/URL options and applies its recorded declarations. | None. | [Blueprint.register](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| concept-settings | [Declarations](#exchange-behavior) | subsystem-interfaces:carries-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Configuration-loader input supplies selected application behavior values. | None. | [Config loaders](corpus:flask:evidence/eefcbaf3dbb10788) |
| concept-application | [Declarations](#exchange-behavior) | subsystem-interfaces:carries-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Blueprint replay's setup state supplies the target application to its recorded setup callbacks. | None. | [BlueprintSetupState/register](corpus:flask:evidence/ref-500e23fcccfdcddd) |
