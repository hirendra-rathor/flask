# Developer command line

## interface-definition

### interface-kind

command line

### purpose-and-boundary

The shipped flask command accepts application selection and subcommands/options. It can display routes, enter an application shell, request a development server, or dispatch application/plugin commands. Click supplies parsing and output; the interface remains Flask's developer-facing command surface.

### providers-and-consumers

The Flask developer CLI provides the command surface to the developer command user and Flask's testing tools. Application/extension code supplies additional app/plugin command behavior. The delegated WSGI host supplies serving rather than the command surface.

### evidence

- [Command entry and built-ins](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| provider-cli | [Command surface](#interface-definition) | subsystem-interfaces:binds-provider | [CLI](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | Flask supplies application discovery, built-in command integration and the command surface. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| provider-application | [Command surface](#interface-definition) | subsystem-interfaces:binds-provider | [Application code](corpus:/architecture/architectural-participants/application-code.md#role-and-scope) | For app/plugin commands the external provider supplies the selected command's additional behavior, rather than Flask's built-in outcomes. | None. | [Command loading](corpus:flask:evidence/fed8939d1905b99b) |
| consumer-developer | [Command surface](#interface-definition) | subsystem-interfaces:binds-consumer | [Developer](corpus:/architecture/architectural-participants/developer.md#role-and-scope) | The command invoker chooses the application, command and options for development/management work. | None. | [Command options/built-ins](corpus:flask:evidence/fed8939d1905b99b) |
| consumer-testing | [Command surface](#interface-definition) | subsystem-interfaces:binds-consumer | [Testing tools](corpus:/architecture/architectural-participants/testing-tools.md#role-and-scope) | FlaskCliRunner selects app.cli and invokes it with ScriptInfo for test callers. | None. | [Runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
