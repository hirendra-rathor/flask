# Build endpoint URLs

## capability-description

### capability

An application or template author supplies an endpoint and values to obtain a URL for registered application work.

### expected-result

The caller receives a URL under the current adapter, blueprint-relative naming and selected external-address options, or the configured build-error handling applies. The address can be used in links, redirects or other application content.

### evidence

- [URL generation](corpus:flask:evidence/d3e0349504081bb5)
- [Public helper](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-content | [Build URL](#capability-description) | domain:contributes-to-intent | [Content forms](corpus:/domain/intentions/produce-representations.md#intended-outcome) | Generated addresses let content refer to registered work without reproducing route patterns. | None. | [url_for/template global](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-url | [Build URL](#capability-description) | domain:concerns-concept | [Endpoint URL](corpus:/domain/domain-concepts/endpoint-url.md#concept-definition) | URL construction produces the address returned to the caller. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-route | [Build URL](#capability-description) | domain:concerns-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | Endpoint and supplied route values select the generated address. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-context | [Build URL](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | A bound request supplies adapter and blueprint name; app-only work uses its adapter. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-settings | [Build URL](#capability-description) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Outside a request, adapter creation uses configured server, root and scheme choices. | None. | [create_url_adapter/url_for](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-registration | [Build URL](#capability-description) | domain:concerns-concept | [Registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Registered defaults and build-error handlers can alter the URL result. | None. | [inject_url_defaults/handle_url_build_error](corpus:flask:evidence/c57b8f34cffef994) [Calls](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-blueprint | [Build URL](#capability-description) | domain:concerns-concept | [Blueprint](corpus:/domain/domain-concepts/blueprint.md#concept-definition) | A request's current blueprint registration name resolves a leading-dot endpoint reference. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
