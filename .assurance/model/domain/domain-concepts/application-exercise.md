# Application exercise

## concept-definition

### definition

An application exercise is a caller-selected simulated request, command invocation or session setup performed through Flask's testing tools. It makes responses, command results and selected contextual/session data available for the test author's checks. The exercise and its observable result differ from an assertion about correctness or evidence that a repository test has run.

### evidence

- [Testing API](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| exercise-request | [Exercise](#concept-definition) | domain:builds-upon | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | In its HTTP form the exercise chooses simulated request data and exposes the response. | None. | [FlaskClient.open](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| exercise-command | [Exercise](#concept-definition) | domain:builds-upon | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | In its command form the exercise selects an application-aware invocation and exposes its result. | None. | [FlaskCliRunner.invoke](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| exercise-session | [Exercise](#concept-definition) | domain:builds-upon | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | In its session-arrangement form the exercise opens a mapping for caller edits and saves it into the simulated client. | None. | [session_transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
