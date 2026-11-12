# Build an endpoint URL

## capability-description

### capability

Application code requests a URL for an endpoint and supplied values. Flask handles blueprint-relative endpoint names, applies registered URL defaults, and asks the URL adapter to build the URL, with an optional anchor and external scheme/host choices.

### implementation-mapping

The public url_for helper calls Flask.url_for. That method selects a context adapter or creates an application adapter, applies defaults, calls adapter.build, and can invoke registered build-error handlers.

### evidence

- [URL construction](corpus:flask:evidence/d3e0349504081bb5)
- [Public helper](corpus:flask:evidence/ref-1f51c8ded4d4ff7e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-registrations | [Build URL](#capability-description) | subsystem-design:uses-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | The adapter uses route registrations and Flask invokes registered defaults/build-error handlers. | None. | [URL](corpus:flask:evidence/d3e0349504081bb5) |
| uses-context | [Build URL](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | A current request supplies adapter and blueprint name; application-only context can also supply an adapter. | None. | [URL](corpus:flask:evidence/d3e0349504081bb5) |
| uses-settings | [Build URL](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Adapter creation outside a request uses configured server name, application root and preferred scheme. | None. | [Adapter](corpus:flask:evidence/d3e0349504081bb5) |
| callback-exchange | [Build URL](#capability-description) | subsystem-design:participates-in-exchange | [Handler calls and results](corpus:/subsystem-interfaces/exchanges/handler-invocation.md#exchange-behavior) | URL defaults receive endpoint/value arguments and build-error handlers may supply an alternate URL. | None. | [URL callbacks](corpus:flask:evidence/d3e0349504081bb5) [Registration](corpus:flask:evidence/c57b8f34cffef994) |
| helper-exchange | [Build URL](#capability-description) | subsystem-design:participates-in-exchange | [Helper requests/results](corpus:/subsystem-interfaces/exchanges/helper-requests-results.md#exchange-behavior) | URL construction receives endpoint/value arguments and returns a generated URL to the caller. | None. | [URL](corpus:flask:evidence/d3e0349504081bb5) |
| domain-url | [Build URL](#capability-description) | subsystem-design:contributes-to-required-capability | [Build URLs](corpus:/domain/required-capabilities/build-url.md#capability-description) | Adapter selection, defaults and URL construction supply the requested endpoint address. | None. | [url_for](corpus:flask:evidence/d3e0349504081bb5) |
