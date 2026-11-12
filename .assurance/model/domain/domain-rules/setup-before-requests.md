# Application setup methods MUST reject changes after request handling starts

## rule-definition

### rule-statement

Once a Flask application has entered full request dispatch, its setup-decorated methods MUST reject later setup calls rather than apply them.

### scope-and-conditions

The guard applies to methods wrapped by Flask's setupmethod mechanism and the application's first-request marker. It does not make every attribute or configuration mapping immutable, and it does not establish cross-process consistency. Blueprint setup has its own registration guard.

### evidence

- [Application setup guard](corpus:flask:evidence/c57b8f34cffef994)
- [Decorator guard call](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [First-request marker](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-composition | [Setup rule](#rule-definition) | domain:protects-intent | [Assemble behavior](corpus:/domain/intentions/compose-application.md#intended-outcome) | Rejecting late guarded setup preserves the setup/handling boundary for the configured application; it is not a proof of consistency across workers. | None. | [Guard](corpus:flask:evidence/c57b8f34cffef994) [Marker](corpus:flask:evidence/d3e0349504081bb5) |
| applies-compose | [Setup rule](#rule-definition) | domain:applies-to | [Compose](corpus:/domain/required-capabilities/compose-application.md#capability-description) | Calls through guarded application setup methods are rejected after the marker is set. | None. | [setupmethod](corpus:flask:evidence/ref-426c9d8938b9fecd) [Guard](corpus:flask:evidence/c57b8f34cffef994) |
| applies-application | [Setup rule](#rule-definition) | domain:applies-to | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The marker and guard belong to the particular application being configured. | None. | [App guard](corpus:flask:evidence/c57b8f34cffef994) |
| applies-registration | [Setup rule](#rule-definition) | domain:applies-to | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Guarded registration operations cannot apply new declarations after full dispatch has begun. | None. | [Registration decorators](corpus:flask:evidence/ref-426c9d8938b9fecd) [App setup](corpus:flask:evidence/c57b8f34cffef994) |
