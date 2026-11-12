# I want to rotate session keys while accepting configured previous keys

## intended-outcome

### desired-outcome

An application operator should be able to configure a current session signing key together with selected previous keys so the default backend can request validation compatible with older valid session cookies while issuing cookies using the current key. This effect depends on the consumed serializer's key-selection contract.

### evidence

- [Current and fallback key binding](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-session | [Rotation](#intended-outcome) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Key rotation concerns continued acceptance and new signing of default cookie session representations. | None. | [Serializer/open/save](corpus:flask:evidence/be4c249245e3745e) |
| concerns-settings | [Rotation](#intended-outcome) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | The current secret and configured fallback list supply the rotation choice; Flask passes their ordered combination to the serializer. | None. | [get_signing_serializer](corpus:flask:evidence/be4c249245e3745e) |
