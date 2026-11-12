# I want framework services to fit my application's needs

## intended-outcome

### desired-outcome

Application architects should be able to supply session, JSON and other supported framework service choices while retaining Flask's application-facing contracts. Authors can integrate feature bundles, processors and callbacks without transferring the application's business responsibilities into the framework.

### evidence

- [Replaceable application services](corpus:flask:evidence/d3e0349504081bb5)
- [Provider selection](corpus:flask:evidence/c57b8f34cffef994)
- [Session contract](corpus:flask:evidence/be4c249245e3745e)
- [JSON contract](corpus:flask:evidence/c2956553392ff9ef)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-application | [Adaptation](#intended-outcome) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Service choices are bound to the application instance that consumes them. | None. | [Construction and service attributes](corpus:flask:evidence/d3e0349504081bb5) [JSON selection](corpus:flask:evidence/c57b8f34cffef994) |
| concerns-session | [Adaptation](#intended-outcome) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | The replaceable backend preserves session opening/saving as the application-facing contract. | None. | [SessionInterface](corpus:flask:evidence/be4c249245e3745e) |
| concerns-json | [Adaptation](#intended-outcome) | domain:concerns-concept | [JSON](corpus:/domain/domain-concepts/json-representation.md#concept-definition) | An application-selected provider supplies conversion and response formatting. | None. | [JSONProvider](corpus:flask:evidence/c2956553392ff9ef) [Binding](corpus:flask:evidence/c57b8f34cffef994) |
| concerns-template | [Adaptation](#intended-outcome) | domain:concerns-concept | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Configurable environment/loader integration and registered processors connect application template sources and values. | None. | [Environment/processor binding](corpus:flask:evidence/d3e0349504081bb5) [Loader](corpus:flask:evidence/e4655695c5cdbf67) |
| concerns-registration | [Adaptation](#intended-outcome) | domain:concerns-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Supported callbacks and processors supply application behavior through retained registrations. | None. | [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd) |
