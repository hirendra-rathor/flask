# CLI application selection

## configuration-description

### configuration

The --app option or FLASK_APP selects the import path, object or factory that the developer CLI loads. ScriptInfo can instead receive a create_app callable. The choice determines which application's commands, routes and context the CLI uses.

### usage-and-effect

The option callback stores app_import_path in ScriptInfo. load_app calls the supplied factory or resolves the selected module/object, caching the resulting app for subsequent command work. FlaskGroup uses a FLASK environment prefix for options.

### evidence

- [Selection and loading](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-cli | [Selection](#configuration-description) | subsystem-design:used-by-component | [CLI](corpus:/subsystem-design/components/developer-cli.md#role-and-implementation) | ScriptInfo reads the selected path/factory during loading. | None. | [Loader](corpus:flask:evidence/fed8939d1905b99b) |
| qualifies-run | [Selection](#configuration-description) | subsystem-design:qualifies-capability | [Run commands](corpus:/subsystem-design/local-capabilities/run-commands.md#capability-description) | Application selection determines the app available to application and built-in commands that need one. | None. | [Commands](corpus:flask:evidence/fed8939d1905b99b) |
