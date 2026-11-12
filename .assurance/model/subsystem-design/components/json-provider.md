# JSON provider

## role-and-implementation

### role-kind

internal

### role

The application's JSON provider encodes and decodes application values and creates JSON responses. It is replaceable per application, so request decoding, JSON helpers, response conversion, and template JSON output can share that application's policy.

### implementation-mapping

`JSONProvider` defines the provider contract and common operations; `DefaultJSONProvider` delegates encoding and decoding to Python's JSON module and handles response formatting. Application construction instantiates its selected provider. Public `flask.json` helpers use the current provider when a context exists.

### evidence

- [Provider](corpus:flask:evidence/c2956553392ff9ef)
- [Binding](corpus:flask:evidence/c57b8f34cffef994)
- [Public helpers](corpus:flask:evidence/d130c1228070cc92)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-json | [Provider](#role-and-implementation) | subsystem-design:offers-capability | [Encode and decode JSON](corpus:/subsystem-design/local-capabilities/encode-decode-json.md#capability-description) | Provider methods supply conversion and JSON response work. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| belongs-json | [Provider](#role-and-implementation) | subsystem-design:belongs-to-participant | [JSON provider](corpus:/architecture/architectural-participants/json-provider.md#role-and-scope) | The shipped provider and application-aware helpers realize Flask's conversion responsibility; custom provider behavior remains external. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) [Helpers](corpus:flask:evidence/d130c1228070cc92) |
