# JSON values and representations

## exchange-behavior

### exchange-description

Provider calls communicate Python values for encoding or JSON text/bytes for decoding and return converted data. The response operation receives values and returns an application response carrying encoded JSON. This is the conversion boundary, without a claim about the application's domain meaning of arbitrary values.

### sender-and-receiver

Framework consumers and application callers send values or encoded input to the selected JSON provider. The provider returns JSON text, decoded values or a JSON response to those callers. Template JSON output and test request building use the same provider's dumps method.

### implementation-mapping

JSONProvider defines conversion/file/response operations; DefaultJSONProvider implements them through Python JSON and app.response_class. Flask.make_response calls response for dictionary/list results; AppContext binds request.json_module to the provider, environment policy binds dumps, and test EnvironBuilder calls dumps.

### evidence

- [Provider](corpus:flask:evidence/c2956553392ff9ef)
- [Response/template consumers](corpus:flask:evidence/d3e0349504081bb5)
- [Request binding](corpus:flask:evidence/d8838a605f9ff504)
- [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-provider | [JSON exchange](#exchange-behavior) | subsystem-interfaces:uses-interface | [JSON API](corpus:/subsystem-interfaces/interfaces/json-provider-api.md#interface-definition) | These calls use the replaceable application JSON provider contract. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| concept-json | [JSON exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [JSON](corpus:/domain/domain-concepts/json-representation.md#concept-definition) | Caller values or encoded input cross conversion and return as JSON text or decoded values; arbitrary application business meaning is not inferred. | None. | [Provider operations](corpus:flask:evidence/c2956553392ff9ef) |
| concept-response | [JSON exchange](#exchange-behavior) | subsystem-interfaces:carries-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | The response operation returns the application's response containing encoded JSON. | None. | [JSONProvider.response](corpus:flask:evidence/c2956553392ff9ef) |
