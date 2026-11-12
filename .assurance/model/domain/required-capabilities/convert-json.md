# Convert application JSON

## capability-description

### capability

Application authors and framework consumers encode application values, decode JSON input and request JSON responses through the selected application's provider.

### expected-result

Callers obtain encoded text, decoded values or a JSON response. Request decoding, template JSON output and testing can use the application provider; public dumps/loads can use default conversion without a bound application. Provider replacement changes conversion under the same offered contract.

### evidence

- [Provider](corpus:flask:evidence/c2956553392ff9ef)
- [Public helpers](corpus:flask:evidence/d130c1228070cc92)
- [Bindings](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-content | [JSON](#capability-description) | domain:contributes-to-intent | [Content forms](corpus:/domain/intentions/produce-representations.md#intended-outcome) | JSON conversion supplies a useful application interchange/output form. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| supports-adaptation | [JSON](#capability-description) | domain:contributes-to-intent | [Service adaptation](corpus:/domain/intentions/adapt-services.md#intended-outcome) | The application-selected provider supplies conversion and response formatting. | None. | [Provider contract](corpus:flask:evidence/c2956553392ff9ef) [Selection](corpus:flask:evidence/c57b8f34cffef994) |
| concerns-json | [JSON](#capability-description) | domain:concerns-concept | [JSON representation](corpus:/domain/domain-concepts/json-representation.md#concept-definition) | Encoding and decoding produce or consume JSON representations. | None. | [dumps/loads](corpus:flask:evidence/c2956553392ff9ef) |
| concerns-response | [JSON](#capability-description) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | The provider's response operation creates an application response containing JSON. | None. | [response](corpus:flask:evidence/c2956553392ff9ef) |
| concerns-request | [JSON](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Context construction binds request JSON decoding to the application's provider. | None. | [Request json_module binding](corpus:flask:evidence/d8838a605f9ff504) |
| concerns-application | [JSON](#capability-description) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Application-bound calls use that instance's provider and response class. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) [Binding](corpus:flask:evidence/c57b8f34cffef994) |
| concerns-context | [JSON](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Public helpers select the active application's provider; dumps/loads can use default conversion without an application context. | None. | [Public JSON helpers](corpus:flask:evidence/d130c1228070cc92) |
| concerns-settings | [JSON](#capability-description) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Default response formatting consults application debug when compact formatting is unspecified. | None. | [DefaultJSONProvider.response](corpus:flask:evidence/c2956553392ff9ef) |
