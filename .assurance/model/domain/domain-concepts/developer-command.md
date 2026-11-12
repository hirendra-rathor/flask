# Application-aware command

## concept-definition

### definition

An application-aware command is named developer or management work selected through Flask's command interface. The user supplies command arguments and application selection; built-ins request development serving, enter an application shell or list routes. Application/plugin commands supply their own results and can run with the chosen application's context. A command definition differs from an invocation and its output.

### evidence

- [Command definitions/loading/invocation](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| command-application | [Command](#concept-definition) | domain:builds-upon | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Application-aware invocation selects an application for app commands, shell or route inspection; command discovery can also expose commands that do not require loading it. | None. | [FlaskGroup/ScriptInfo/commands](corpus:flask:evidence/fed8939d1905b99b) |
