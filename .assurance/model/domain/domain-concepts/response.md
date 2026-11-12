# Application response

## concept-definition

### definition

An application response is the status, headers and body made available as the result of handling a web request. Flask adapts supported handler values into this form and gives the result to its WSGI caller for delivery. A response can carry text, JSON, file content or streamed body data; constructing it does not establish delivery to the client.

### evidence

- [Response conversion and WSGI](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| response-request | [Response](#concept-definition) | domain:builds-upon | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | In web handling the response is the result for a particular application request, including framework-generated responses and adapted handler results. | None. | [Dispatch/finalization](corpus:flask:evidence/d3e0349504081bb5) |
| response-json-form | [Response](#concept-definition) | domain:builds-upon | [JSON](corpus:/domain/domain-concepts/json-representation.md#concept-definition) | In its JSON form the response body is an encoded application value produced by the selected provider. | None. | [make_response](corpus:flask:evidence/d3e0349504081bb5) [Provider.response](corpus:flask:evidence/c2956553392ff9ef) |
| response-file-form | [Response](#concept-definition) | domain:builds-upon | [File resource](corpus:/domain/domain-concepts/file-resource.md#concept-definition) | In the file-response form, selected file content and delivery options define the response contribution. | None. | [File helpers](corpus:flask:evidence/ref-1f51c8ded4d4ff7e) |
