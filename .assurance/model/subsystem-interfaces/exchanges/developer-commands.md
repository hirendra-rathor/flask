# Developer commands and output

## exchange-behavior

### exchange-description

The command invocation communicates a subcommand, application selection and options to Flask. For example, routes requests the application's registered endpoint/method/rule information and prints it; run requests development serving with host/port choices; shell requests an interactive namespace. Their output and handoffs differ, so a server request is not a report that deployment succeeded.

### sender-and-receiver

A developer or command invoker supplies command tokens/options to the CLI. The CLI prints route information and diagnostics to the invoker, gives serving arguments to Werkzeug for run, or gives an application namespace to the Python shell for shell. Application/plugin commands receive their own parsed arguments.

### implementation-mapping

FlaskGroup's options and command lookup bind input through Click. routes_command prints selected map rules; run_command passes the app/options to run_simple; shell_command calls code.interact with make_shell_context results.

### evidence

- [CLI commands](corpus:flask:evidence/fed8939d1905b99b)
- [Shell context](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-cli | [Commands/output](#exchange-behavior) | subsystem-interfaces:uses-interface | [Command line](corpus:/subsystem-interfaces/interfaces/developer-command-line.md#interface-definition) | Developer input selects command work and receives its output. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| carries-routes | [Commands/output](#exchange-behavior) | subsystem-interfaces:carries-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | The routes command prints registered rule endpoint/method/path information; this is a view of the URL map rather than the complete registration state. | None. | [Route listing](corpus:flask:evidence/fed8939d1905b99b) |
| carries-shell-context | [Commands/output](#exchange-behavior) | subsystem-interfaces:carries-state | [Execution context](corpus:/state-management/state-elements/execution-context.md#state-definition) | The shell namespace includes the selected application and g from the active context, with additional processor values when supplied. | None. | [Shell](corpus:flask:evidence/fed8939d1905b99b) [Namespace](corpus:flask:evidence/d3e0349504081bb5) |
| concept-command | [Commands](#exchange-behavior) | subsystem-interfaces:carries-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Input tokens/options select named developer work and its invocation arguments; output/handoffs have the selected command's meaning. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| concept-route | [Commands](#exchange-behavior) | subsystem-interfaces:carries-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | routes output communicates registered endpoint/method/path information to the user. | None. | [routes_command](corpus:flask:evidence/fed8939d1905b99b) |
| concept-application | [Commands](#exchange-behavior) | subsystem-interfaces:carries-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Serving requests pass the chosen application to the host, and shell setup supplies it in the interactive namespace. | None. | [run_command/shell_command](corpus:flask:evidence/fed8939d1905b99b) [Namespace](corpus:flask:evidence/d3e0349504081bb5) |
| concept-context | [Commands](#exchange-behavior) | subsystem-interfaces:carries-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Shell preparation exposes the selected app and g portions of its active context. | None. | [shell_command](corpus:flask:evidence/fed8939d1905b99b) [make_shell_context](corpus:flask:evidence/d3e0349504081bb5) |
| concept-settings | [Commands](#exchange-behavior) | subsystem-interfaces:carries-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Development serving passes debugger/reloader choices derived from selected debug state; the whole configuration is not printed or copied. | None. | [run_command](corpus:flask:evidence/fed8939d1905b99b) |
