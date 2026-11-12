# Click command runtime

## role-and-scope

### role

Click supplies command declaration, parsing, lookup, invocation and output, together with isolated command testing used by Flask's clients.

### classifications

- external dependency

### scope

Flask augments this separately supplied command runtime with application loading and contexts. The framework and application command callbacks retain their own responsibilities.

### implementation-mapping

`FlaskGroup` and `AppGroup` extend Click groups and use inherited lookup/invocation. Decorators define command parameters. `FlaskCliRunner` extends Click's CliRunner and delegates invocation.

### evidence

- [CLI integration](corpus:flask:evidence/fed8939d1905b99b)
- [Test runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Click](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | Click provides external command machinery in command and test invocation settings. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) [Testing](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
| allocates-command-runtime | [Click](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | Click supplies consumed parsing, lookup, invocation and output while Flask binds application discovery/context. | None. | [CLI decorators/groups/calls](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-command-testing | [Click](#role-and-scope) | architecture:allocates-capability | [Exercise applications](corpus:/domain/required-capabilities/exercise-application.md#capability-description) | The consumed CliRunner supplies isolated command invocation/results under Flask's application binding. | None. | [FlaskCliRunner inheritance/invoke](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
