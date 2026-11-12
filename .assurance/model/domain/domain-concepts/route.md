# Route and endpoint

## concept-definition

### definition

A route is an application's rule connecting a URL pattern and allowed methods to an endpoint. The endpoint is the name by which Flask selects a registered view and application code requests URL construction. Several rules can use an endpoint; the endpoint name and the concrete URL requested by a client have different meanings.

### evidence

- [Rules and endpoint bindings](corpus:flask:evidence/c57b8f34cffef994)
- [Dispatch and URL building](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| route-registration | [Route](#concept-definition) | domain:builds-upon | [Behavior registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | A route is the form of behavior registration that associates URL/method matching with an endpoint and its view. | None. | [add_url_rule](corpus:flask:evidence/c57b8f34cffef994) |
