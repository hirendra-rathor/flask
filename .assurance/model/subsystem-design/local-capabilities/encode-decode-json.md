# Encode and decode JSON

## capability-description

### capability

Application callers and framework consumers can convert values to JSON text, decode JSON input, and construct a JSON response through the application's provider. The default provider uses Python JSON operations with its supported extra-type conversion and response formatting choices.

### implementation-mapping

JSONProvider exposes dumps/loads, file operations and response; DefaultJSONProvider implements those conversions and creates app.response_class with the JSON media type. The application binds its provider to request decoding and response creation; template JSON output receives its dumps method.

### evidence

- [Provider](corpus:flask:evidence/c2956553392ff9ef)
- [Consumers](corpus:flask:evidence/d3e0349504081bb5)
- [Request provider binding](corpus:flask:evidence/d8838a605f9ff504)
- [Context-aware public helpers](corpus:flask:evidence/d130c1228070cc92)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-settings | [JSON](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Default JSON response formatting reads app.debug when compact is unspecified. | None. | [Formatting](corpus:flask:evidence/c2956553392ff9ef) |
| uses-context | [JSON](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Public JSON helpers select the current application's provider through current_app; dumps/loads can use Python JSON without an active app, while jsonify requires the app. | None. | [Public helpers](corpus:flask:evidence/d130c1228070cc92) |
| json-exchange | [JSON](#capability-description) | subsystem-design:participates-in-exchange | [JSON values and representations](corpus:/subsystem-interfaces/exchanges/json-conversion.md#exchange-behavior) | Provider methods receive application values or encoded input and return converted values or a JSON response. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| domain-json | [JSON](#capability-description) | subsystem-design:contributes-to-required-capability | [Convert JSON](corpus:/domain/required-capabilities/convert-json.md#capability-description) | Provider conversion/formatting supplies JSON values, representations and responses. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| domain-handle | [JSON](#capability-description) | subsystem-design:contributes-to-required-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Dict/list handler results use provider.response and request JSON decoding uses the selected provider. | None. | [make_response](corpus:flask:evidence/d3e0349504081bb5) [Request binding](corpus:flask:evidence/d8838a605f9ff504) |
| domain-render | [JSON](#capability-description) | subsystem-design:contributes-to-required-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Environment policy supplies the provider's dumps method for template JSON output; arbitrary template use is not asserted. | None. | [Jinja policy binding](corpus:flask:evidence/d3e0349504081bb5) |
| domain-exercise | [JSON](#capability-description) | subsystem-design:contributes-to-required-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | Test request construction encodes JSON with the application provider. | None. | [EnvironBuilder.json_dumps](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
