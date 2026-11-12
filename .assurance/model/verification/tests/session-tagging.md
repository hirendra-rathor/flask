# Test tagged session value serialization

## verification-approach

### test-kind

unit

### test-description

Tests construct TaggedJSONSerializer directly, call dumps/loads for additional Python value types and tag-shaped dictionaries, and register custom or duplicate tag classes at selected positions. No request, cookie signing or session persistence is arranged.

### intended-focus

The family intends to exercise the backend's small tagged-payload responsibility and tag extension interface. Direct serializer calls do not make the default JSON provider or cookie-signature acceptance an intended target.

### evidence

- [Tag scenarios](corpus:flask:evidence/ref-1f0ffcfa98a9ab7f)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| backend | [Approach](#verification-approach) | verification:targets-for-testing | [Session backend](corpus:/subsystem-design/components/session-backend.md#role-and-implementation) | Only its tagged-value serializer portion is exercised directly. | None. | [Tags](corpus:flask:evidence/ref-1f0ffcfa98a9ab7f) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [Backend role](corpus:/architecture/architectural-participants/session-backend.md#role-and-scope) | The role's shipped tagged serialization contribution is the intended subresponsibility. | None. | [Tags](corpus:flask:evidence/ref-1f0ffcfa98a9ab7f) |
