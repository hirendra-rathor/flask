# Developer command user

## role-and-scope

### role

The developer chooses application selection, commands and options to inspect routes, work in an application shell, request local serving or invoke custom command behavior.

### classifications

- external consumer

### scope

The command user's independent development or management goal initiates command use. This role is distinct from the command callback implementation and the serving environment requested by the run command.

### implementation-mapping

The command group's options, command declarations, shell/routes callbacks and main entry establish the user-facing contract and returned output. The person or external command invoker is outside Flask implementation.

### evidence

- [Command contract](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Developer](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The external developer selects command work for development or management outcomes. | None. | [Commands](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-command-choice | [Developer](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | The user supplies application selection, command and options and consumes output; command execution remains with its providers. | None. | [CLI input/output contract](corpus:flask:evidence/fed8939d1905b99b) |
| corresponds-operator | [Developer](#role-and-scope) | architecture:corresponds-to-domain-participant | [Application operator](corpus:/domain/domain-participants/application-operator.md#role-and-contribution) | The command user realizes the operator's selection/invocation and route/shell inspection contribution in the supported development setting. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
