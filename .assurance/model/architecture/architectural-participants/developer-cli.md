# Flask developer CLI

## role-and-scope

### role

The developer CLI discovers an application and combines built-in, application and plugin commands into a developer-facing command surface. It requests the development server, prepares a shell and lists routes, while application commands receive an application context.

### classifications

- internal

### scope

Application selection and framework command integration belong to Flask. Click supplies parsing and invocation, the host supplies serving, and custom commands supply their own outcomes. The optional dotenv loader is a consumed setting-loading aid within this integration account.

### implementation-mapping

`ScriptInfo`, `FlaskGroup`, `AppGroup`, `with_appcontext`, built-in command callbacks and `main` implement discovery, registration and invocation. The module command calls this entry point.

### evidence

- [CLI](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [CLI](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | The shipped application-aware command integration is internal framework work. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-commands | [CLI](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | Application discovery and built-in/application/plugin command integration supply command selection, output and serving/shell handoffs; Click owns its runtime. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-context-entry | [CLI](#role-and-scope) | architecture:allocates-capability | [Contextual work](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Wrapping application commands and entering the shell request the selected app's context. | None. | [with_appcontext/shell](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-debug-binding | [CLI](#role-and-scope) | architecture:allocates-capability | [Compose/settings](corpus:/domain/required-capabilities/compose-application.md#capability-description) | When enabled, ScriptInfo loading assigns the selected debug setting to the application; this is not the whole application-setup responsibility. | None. | [ScriptInfo.load_app](corpus:flask:evidence/fed8939d1905b99b) |
