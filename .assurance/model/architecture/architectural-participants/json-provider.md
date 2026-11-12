# Flask JSON provider

## role-and-scope

### role

The JSON provider supplies application-aware JSON conversion and response formatting used by request, response, template and testing work.

### classifications

- internal

### scope

Flask supplies the provider contract and default implementation. Applications can replace the provider; such replacements keep their application-specific behavior outside the shipped provider responsibility. The default provider consumes Python's JSON library.

### implementation-mapping

`JSONProvider` and `DefaultJSONProvider` implement conversion and response construction. Sans-I/O application construction instantiates the selected class; public JSON helpers select the active application's provider when bound.

### evidence

- [Provider](corpus:flask:evidence/c2956553392ff9ef)
- [Binding](corpus:flask:evidence/c57b8f34cffef994)
- [Helpers](corpus:flask:evidence/d130c1228070cc92)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Provider](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The contract, default conversion and application-aware helpers are internal framework work. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) [Helpers](corpus:flask:evidence/d130c1228070cc92) |
| allocates-json | [Provider](#role-and-scope) | architecture:allocates-capability | [Convert JSON](corpus:/domain/required-capabilities/convert-json.md#capability-description) | Its contract/default implementation supply application value conversion and response formatting. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| allocates-response-conversion | [Provider](#role-and-scope) | architecture:allocates-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Dict/list handler results are converted to application responses by the selected provider. | None. | [make_response](corpus:flask:evidence/d3e0349504081bb5) [Provider.response](corpus:flask:evidence/c2956553392ff9ef) |
| allocates-template-json | [Provider](#role-and-scope) | architecture:allocates-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Its dumps contribution is installed for template JSON output; no arbitrary template use is inferred. | None. | [JSON policy binding](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-testing-json | [Provider](#role-and-scope) | architecture:allocates-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | The test builder uses the application provider to encode JSON input and client responses bind its decoding. | None. | [Testing JSON bindings](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
