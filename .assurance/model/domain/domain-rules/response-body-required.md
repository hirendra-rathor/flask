# Response conversion MUST reject a missing handler result

## rule-definition

### rule-statement

Flask's response conversion MUST reject a handler result whose body is None, including a handler that ends without returning a result.

### scope-and-conditions

The constraint applies when make_response converts the chosen result, after any supported response-tuple unpacking. It does not require every hook to return a response: a before-request hook may return None to continue processing, and later selected behavior supplies the final result.

### evidence

- [Response conversion](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-response | [Response rule](#rule-definition) | domain:protects-intent | [Application responses](corpus:/domain/intentions/respond-to-requests.md#intended-outcome) | The final selected result must supply a supported body rather than silently treating None as a valid response. | None. | [make_response/full_dispatch_request](corpus:flask:evidence/d3e0349504081bb5) |
| applies-response | [Response rule](#rule-definition) | domain:applies-to | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Missing body results cannot be converted as a valid application response. | None. | [make_response](corpus:flask:evidence/d3e0349504081bb5) |
| applies-handling | [Response rule](#rule-definition) | domain:applies-to | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | The selected final result passes through this conversion in request finalization. | None. | [finalize_request/make_response](corpus:flask:evidence/d3e0349504081bb5) |
