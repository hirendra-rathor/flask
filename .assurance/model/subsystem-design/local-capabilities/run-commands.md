# Run developer commands

## capability-description

### capability

A developer selects a Flask application and invokes a built-in, application or plugin command. Built-ins request a local development server, enter a shell with application globals, or print registered route information. Application commands receive an application context; invoking the server command hands serving work to Werkzeug.

### implementation-mapping

FlaskGroup resolves commands and ScriptInfo.load_app selects or creates the application. run_command calls run_simple, shell_command prepares context then calls code.interact, and routes_command renders map rules to Click output. AppGroup and with_appcontext supply application context for callbacks.

### evidence

- [Commands](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| uses-context | [Commands](#capability-description) | subsystem-design:uses-state | [Context](corpus:/state-management/state-elements/execution-context.md#state-definition) | Application commands and the shell enter the selected application's context. | None. | [Context wrapping](corpus:flask:evidence/fed8939d1905b99b) |
| uses-registrations | [Commands](#capability-description) | subsystem-design:uses-state | [Registrations](corpus:/state-management/state-elements/application-registrations.md#state-definition) | Route listing reads the map, shell context reads registered processors, and command lookup reads application command groups. | None. | [Commands](corpus:flask:evidence/fed8939d1905b99b) [Shell context](corpus:flask:evidence/d3e0349504081bb5) |
| uses-settings | [Commands](#capability-description) | subsystem-design:uses-state | [Settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | Application loading sets debug configuration when requested; developer server choices use debug mode. | None. | [Loading and run](corpus:flask:evidence/fed8939d1905b99b) |
| command-exchange | [Commands](#capability-description) | subsystem-design:participates-in-exchange | [Developer commands and output](corpus:/subsystem-interfaces/exchanges/developer-commands.md#exchange-behavior) | The CLI receives command/options and emits route information or initiates requested developer work. | None. | [Commands](corpus:flask:evidence/fed8939d1905b99b) |
| callback-exchange | [Commands](#capability-description) | subsystem-design:participates-in-exchange | [Handler calls and results](corpus:/subsystem-interfaces/exchanges/handler-invocation.md#exchange-behavior) | Application command callbacks and shell processors provide application-supplied behavior to the CLI. | None. | [Command wrapping](corpus:flask:evidence/fed8939d1905b99b) [Processors](corpus:flask:evidence/d3e0349504081bb5) |
| domain-commands | [Commands](#capability-description) | subsystem-design:contributes-to-required-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | Application discovery and built-in/application/plugin invocation provide command output and bounded serving/shell handoffs. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| domain-context | [Commands](#capability-description) | subsystem-design:contributes-to-required-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Application command wrapping and shell entry supply an application context for the selected work. | None. | [with_appcontext/shell](corpus:flask:evidence/fed8939d1905b99b) |
