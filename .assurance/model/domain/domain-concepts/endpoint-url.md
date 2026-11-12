# Endpoint URL

## concept-definition

### definition

An endpoint URL is the address constructed for a registered endpoint and supplied route values. It can be relative to the request's location or include an external scheme and host. It lets application and template authors refer to registered work without reproducing its URL pattern; blueprint-relative names are resolved in the current request when applicable.

### evidence

- [URL construction](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| url-route | [URL](#concept-definition) | domain:builds-upon | [Route/endpoint](corpus:/domain/domain-concepts/route.md#concept-definition) | The registered endpoint and route values determine which URL the builder constructs, qualified by the selected adapter and external-address options. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
