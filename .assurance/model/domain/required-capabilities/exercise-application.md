# Exercise applications under chosen conditions

## capability-description

### capability

A test author selects simulated requests, command arguments or session values through Flask's application-aware testing tools.

### expected-result

The caller obtains test responses, command results and session/context access for its own checks. Session transactions save arranged values into the simulated client. The caller's assertions and whether any test executes remain separate from availability of this ability.

### evidence

- [Testing support](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-observation | [Exercise](#capability-description) | domain:contributes-to-intent | [Observe behavior](corpus:/domain/intentions/observe-application.md#intended-outcome) | Caller-chosen inputs and returned results make application outcomes available for inspection. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-exercise | [Exercise](#capability-description) | domain:concerns-concept | [Application exercise](corpus:/domain/domain-concepts/application-exercise.md#concept-definition) | The API performs the caller-selected simulated scenario and exposes its result. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-request | [Exercise](#capability-description) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The client constructs and submits chosen request data. | None. | [FlaskClient/EnvironBuilder](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-response | [Exercise](#capability-description) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Client calls return test response objects with the application's JSON decoding binding. | None. | [FlaskClient.open](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-command | [Exercise](#capability-description) | domain:concerns-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | The command runner invokes the selected command with supplied arguments. | None. | [FlaskCliRunner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-session | [Exercise](#capability-description) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | A session transaction exposes the mapping for caller arrangement and saves it into client cookies. | None. | [session_transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-context | [Exercise](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Client context preservation permits contextual inspection after the request. | None. | [Context preservation](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
