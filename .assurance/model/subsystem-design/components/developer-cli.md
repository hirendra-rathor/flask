# Developer CLI

## role-and-implementation

### role-kind

internal

### role

The shipped CLI discovers a Flask application and makes built-in, application, and plugin commands available to developers. Built-in commands request a development server, prepare an interactive application shell, or display registered routes. Application commands run with an application context.

### implementation-mapping

`FlaskGroup` discovers commands; `ScriptInfo.load_app` loads or creates and caches the application. `AppGroup` and `with_appcontext` wrap application command callbacks. `run_command`, `shell_command`, and `routes_command` supply the built-ins; `main` invokes the Click group.

### evidence

- [CLI](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| offers-commands | [CLI](#role-and-implementation) | subsystem-design:offers-capability | [Run developer commands](corpus:/subsystem-design/local-capabilities/run-commands.md#capability-description) | The shipped group selects and invokes framework/application commands. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| delegates-click | [CLI](#role-and-implementation) | subsystem-design:delegates-to | [Click](corpus:/subsystem-design/components/click-runtime.md#role-and-implementation) | FlaskGroup/AppGroup use Click group lookup, argument parsing and callback invocation. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| delegates-context | [CLI](#role-and-implementation) | subsystem-design:delegates-to | [Context manager](corpus:/subsystem-design/components/context-manager.md#role-and-implementation) | with_appcontext and command lookup enter the selected application's context. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| delegates-development-server | [CLI](#role-and-implementation) | subsystem-design:delegates-to | [Werkzeug](corpus:/subsystem-design/components/werkzeug.md#role-and-implementation) | run_command hands the application and development-server options to run_simple. | None. | [Run command](corpus:flask:evidence/fed8939d1905b99b) |
| maintains-debug-setting | [CLI](#role-and-implementation) | subsystem-design:maintains-state | [Application settings](corpus:/state-management/state-elements/application-settings.md#state-definition) | ScriptInfo.load_app sets the application's debug flag when its set_debug_flag option permits. | None. | [Application loading](corpus:flask:evidence/fed8939d1905b99b) |
| belongs-cli | [CLI component](#role-and-implementation) | subsystem-design:belongs-to-participant | [CLI participant](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | Application discovery, contexts and built-in command integration realize the shipped command responsibility. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
