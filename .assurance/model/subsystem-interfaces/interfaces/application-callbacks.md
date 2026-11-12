# Application callback interface

## interface-definition

### interface-kind

callback

### process-locality

- in-process

### purpose-and-boundary

Flask invokes application-supplied behavior at registered extension points: views, request/teardown hooks, error handlers, template context processors, URL defaults/build-error handlers, and command/shell callbacks. The family groups framework-to-application invocation; the differing arguments and results stay explicit in the exchange account.

### providers-and-consumers

Application and extension code provides the behavior. The Flask application coordinator, template integrator and developer CLI consume it at their respective extension points. Registration binds handlers but does not make Flask the provider of their application-specific results.

### evidence

- [Runtime invocation](corpus:flask:evidence/d3e0349504081bb5)
- [URL callbacks](corpus:flask:evidence/c57b8f34cffef994)
- [Commands](corpus:flask:evidence/fed8939d1905b99b)
- [View adapter](corpus:flask:evidence/ref-98249c1107548796)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-application | [Callback interface](#interface-definition) | subsystem-interfaces:binds-provider | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | Application/extension handlers, hooks, processors and custom commands supply their behavior at registered callback points. | None. | [Invocation](corpus:flask:evidence/d3e0349504081bb5) [Commands](corpus:flask:evidence/fed8939d1905b99b) |
| consumer-coordinator | [Callback interface](#interface-definition) | subsystem-interfaces:binds-consumer | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | Dispatch, teardown and URL construction consume supplied views/hooks/defaults/error behavior; sending arguments does not make Flask their behavior provider. | None. | [Calls](corpus:flask:evidence/d3e0349504081bb5) [URL defaults](corpus:flask:evidence/c57b8f34cffef994) |
| consumer-templates | [Callback interface](#interface-definition) | subsystem-interfaces:binds-consumer | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Template context assembly invokes registered processors to obtain context contributions. | None. | [Processors](corpus:flask:evidence/d3e0349504081bb5) |
| consumer-cli | [Callback interface](#interface-definition) | subsystem-interfaces:binds-consumer | [CLI](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | Command discovery invokes application factories, command callbacks and shell-context processors through its application integration. | None. | [Commands](corpus:flask:evidence/fed8939d1905b99b) [Shell context](corpus:flask:evidence/d3e0349504081bb5) |
