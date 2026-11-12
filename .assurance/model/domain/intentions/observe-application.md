# I want to observe application behavior under chosen conditions

## intended-outcome

### desired-outcome

Test authors should be able to exercise application requests, commands and session conditions and inspect returned results. Application or extension authors can also connect observers to named framework events. These facilities make selected outcomes observable; the caller supplies assertions and any interpretation of notices.

### evidence

- [Testing tools](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)
- [Named notifications](corpus:flask:evidence/ref-3b3fcb2407028958)
- [Notification sends](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-exercise | [Observation](#intended-outcome) | domain:concerns-concept | [Application exercise](corpus:/domain/domain-concepts/application-exercise.md#concept-definition) | Caller-selected exercise inputs make result objects available for checking. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-request | [Observation](#intended-outcome) | domain:concerns-concept | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | The test client accepts request choices and request lifecycle signals report related events. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-response | [Observation](#intended-outcome) | domain:concerns-concept | [Response](corpus:/domain/domain-concepts/response.md#concept-definition) | Returned test responses and request-finished notices make response data available. | None. | [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) [Finalization](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-command | [Observation](#intended-outcome) | domain:concerns-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Command testing returns the chosen invocation's result for inspection. | None. | [FlaskCliRunner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-session | [Observation](#intended-outcome) | domain:concerns-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Session transactions let test callers arrange and inspect session values. | None. | [session_transaction](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| concerns-notification | [Observation](#intended-outcome) | domain:concerns-concept | [Notification](corpus:/domain/domain-concepts/framework-notification.md#concept-definition) | Connected observers obtain named framework event information under the event's stated conditions. | None. | [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
