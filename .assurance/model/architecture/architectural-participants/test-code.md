# Application test code

## role-and-scope

### role

Application test code chooses requests, commands and session transactions and obtains results through the Flask testing API so its own tests can inspect application behavior.

### classifications

- external consumer

### scope

Test authors supply scenarios and assertions outside the framework testing tools. This participant identifies the caller role exposed by production APIs; it does not claim that any repository test was examined or executed.

### implementation-mapping

`FlaskClient.open`, `session_transaction`, context preservation and `FlaskCliRunner.invoke` accept caller work and return responses, session objects or command results. The application factories construct the tools bound to the tested application.

### evidence

- [Test API](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)
- [Factories](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Test code](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | External test code drives framework-aware clients for its application's checking purposes. | None. | [Test API](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-scenarios | [Test code](#role-and-scope) | architecture:allocates-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | The caller supplies scenario inputs/session arrangement and receives results for its own checking; this does not establish assertion execution. | None. | [Testing API](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| corresponds-test-author | [Test code](#role-and-scope) | architecture:corresponds-to-domain-participant | [Test author](corpus:/domain/domain-participants/test-author.md#role-and-contribution) | Client/runner callers realize the test author's chosen inputs and outcome-inspection contribution. | None. | [Testing API](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
