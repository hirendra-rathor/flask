# Route registration MUST NOT replace an endpoint's different view

## rule-definition

### rule-statement

When add_url_rule receives a view for an endpoint already bound to a different view, it MUST reject that replacement without changing the existing endpoint-to-view mapping.

### scope-and-conditions

The constraint applies to the inspected application registration operation. Reusing the same view for an endpoint is permitted. The operation adds a URL rule before checking the view conflict, so rejection does not promise rollback of the URL map or arbitrary direct edits.

### evidence

- [add_url_rule binding check](corpus:flask:evidence/c57b8f34cffef994)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-composition | [Endpoint rule](#rule-definition) | domain:protects-intent | [Assemble behavior](corpus:/domain/intentions/compose-application.md#intended-outcome) | Rejection protects the existing endpoint's view selection against a conflicting registration through this operation. | None. | [add_url_rule](corpus:flask:evidence/c57b8f34cffef994) |
| applies-route | [Endpoint rule](#rule-definition) | domain:applies-to | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | An already-bound endpoint cannot acquire a different view through this call. | None. | [Endpoint mapping check](corpus:flask:evidence/c57b8f34cffef994) |
| applies-compose | [Endpoint rule](#rule-definition) | domain:applies-to | [Compose](corpus:/domain/required-capabilities/compose-application.md#capability-description) | The application's rule-registration leg checks the existing view before assigning the supplied view. | None. | [add_url_rule](corpus:flask:evidence/c57b8f34cffef994) |
