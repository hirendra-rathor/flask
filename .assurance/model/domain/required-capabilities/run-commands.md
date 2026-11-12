# Run application-aware commands

## capability-description

### capability

An application operator selects an application, command and options for built-in, application or plugin developer work.

### expected-result

Built-ins expose route information, prepare an interactive application shell or request a development server. Application commands receive a selected application context and their parsed arguments. A serving request or custom-command invocation establishes its handoff rather than production readiness or arbitrary completion.

### evidence

- [CLI](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-operations | [Commands](#capability-description) | domain:contributes-to-intent | [Run/inspect application](corpus:/domain/intentions/developer-operations.md#intended-outcome) | Discovery and application-aware invocation expose the selected developer work and output. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| supports-context | [Commands](#capability-description) | domain:contributes-to-intent | [Contextual access](corpus:/domain/intentions/contextual-work.md#intended-outcome) | Application command wrapping and shell setup bind the chosen application's context. | None. | [with_appcontext/shell](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-command | [Commands](#capability-description) | domain:concerns-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Command selection and arguments cause the requested invocation. | None. | [FlaskGroup](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-application | [Commands](#capability-description) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | Loading selects or creates the application whose work is invoked. | None. | [ScriptInfo](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-route | [Commands](#capability-description) | domain:concerns-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | Route listing prints the chosen application's rule and endpoint information. | None. | [routes_command](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-context | [Commands](#capability-description) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Shell and application commands use the selected app binding. | None. | [Command context](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-settings | [Commands](#capability-description) | domain:concerns-concept | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Application loading can set debug and the development-server request uses debug-related choices. | None. | [ScriptInfo/run_command](corpus:flask:evidence/fed8939d1905b99b) |
