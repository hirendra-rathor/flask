# Flask application operator

## role-and-contribution

### role-kind

Operator

### role

The application operator selects configuration and invokes supported operations for a chosen Flask application, including local development work.

### contribution

The operator supplies application selection, commands/options and behavior settings such as session keys and cookie policy. The supported stakes are inspecting/running selected work and rotating signing material while retaining configured prior-key compatibility; actual production deployment arrangements are outside this role's inspected interactions.

### evidence

- [Commands](corpus:flask:evidence/fed8939d1905b99b)
- [Configuration loading](corpus:flask:evidence/eefcbaf3dbb10788)
- [Session policy/key consumption](corpus:flask:evidence/be4c249245e3745e)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| needs-commands | [Operator](#role-and-contribution) | domain:requires-capability | [Commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | Command invocation supplies route inspection, shell and requested development serving or custom work. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| needs-configuration | [Operator](#role-and-contribution) | domain:requires-capability | [Compose/settings](corpus:/domain/required-capabilities/compose-application.md#capability-description) | Loaded behavior settings let the operator choose application policy, including signing material. | None. | [Config](corpus:flask:evidence/eefcbaf3dbb10788) [Session reads](corpus:flask:evidence/be4c249245e3745e) |
| needs-session-policy | [Operator](#role-and-contribution) | domain:requires-capability | [Sessions](corpus:/domain/required-capabilities/retain-session.md#capability-description) | Default session opening/saving must consume current/fallback keys for the operator's selected rotation. | None. | [Key binding/open/save](corpus:flask:evidence/be4c249245e3745e) |
| stake-operations | [Operator](#role-and-contribution) | domain:has-stake-in-intention | [Run/inspect](corpus:/domain/intentions/developer-operations.md#intended-outcome) | The command user chooses application work and consumes route/shell output or serving handoff. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| stake-rotation | [Operator](#role-and-contribution) | domain:has-stake-in-intention | [Key rotation](corpus:/domain/intentions/session-key-rotation.md#intended-outcome) | Configurable previous/current keys support the operator's continuity during key changes. | None. | [Serializer keys](corpus:flask:evidence/be4c249245e3745e) |
| concerned-app | [Operator](#role-and-contribution) | domain:is-concerned-with-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Application selection identifies the instance that commands load or create. | None. | [ScriptInfo](corpus:flask:evidence/fed8939d1905b99b) |
| concerned-command | [Operator](#role-and-contribution) | domain:is-concerned-with-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | The operator chooses commands and options and receives their output. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| concerned-route | [Operator](#role-and-contribution) | domain:is-concerned-with-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | The routes command exposes endpoint/method/path information to this user. | None. | [routes_command](corpus:flask:evidence/fed8939d1905b99b) |
| concerned-context | [Operator](#role-and-contribution) | domain:is-concerned-with-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | The application shell supplies application/g data in its active context. | None. | [shell_command](corpus:flask:evidence/fed8939d1905b99b) [Shell namespace](corpus:flask:evidence/d3e0349504081bb5) |
| concerned-settings | [Operator](#role-and-contribution) | domain:is-concerned-with-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Environment/file/mapping inputs supply behavior policy and session material. | None. | [Config](corpus:flask:evidence/eefcbaf3dbb10788) [Session reads](corpus:flask:evidence/be4c249245e3745e) |
| concerned-session | [Operator](#role-and-contribution) | domain:is-concerned-with-concept | [Session](corpus:/domain/domain-concepts/session.md#concept-definition) | Session acceptance/signing and cookie emission are qualified by the operator's configured policy. | None. | [Sessions](corpus:flask:evidence/be4c249245e3745e) |
