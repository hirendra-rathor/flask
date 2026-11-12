# I want requests to receive application-defined responses

## intended-outcome

### desired-outcome

Application authors and web requesters should be able to obtain responses from registered application behavior through Flask's request handling. Flask selects hooks, views or error handling and adapts supported results; the serving host remains responsible for delivery.

### evidence

- [Request dispatch and response conversion](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-request | [Response aim](#intended-outcome) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Each handled request supplies the work to which selected behavior responds. | None. | [WSGI/dispatch](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-response | [Response aim](#intended-outcome) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Supported handler results become response status, headers and body for the caller. | None. | [make_response](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-route | [Response aim](#intended-outcome) | domain:concerns-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | Matched endpoint and route values select the normal view contribution. | None. | [dispatch_request](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-registration | [Response aim](#intended-outcome) | domain:concerns-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Registered hooks and handlers determine the application-supplied response work. | None. | [Preprocessing/dispatch/error handling](corpus:flask:evidence/d3e0349504081bb5) |
