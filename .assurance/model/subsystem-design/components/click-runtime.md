# Click command runtime

## role-and-implementation

### role-kind

external dependency

### role

Click supplies command groups, options, callback invocation, output and command testing that Flask augments with application discovery and context. Flask's command classes inherit Click behavior, while its CLI runner delegates isolated invocation to Click's testing support.

### implementation-mapping

AppGroup and FlaskGroup subclass Click groups and invoke inherited command lookup/registration. Decorators declare built-in commands and options; cli.main dispatches them. FlaskCliRunner subclasses Click CliRunner and invokes its implementation with application-aware ScriptInfo.

### evidence

- [Command runtime use](corpus:flask:evidence/fed8939d1905b99b)
- [Runner use](corpus:flask:evidence/ref-8b6ebc456dd7ce1a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| belongs-click | [Command runtime contribution](#role-and-implementation) | subsystem-design:belongs-to-participant | [Click](corpus:/architecture/architectural-participants/click.md#role-and-scope) | Click supplies command and runner machinery, while Flask's context/discovery integration remains internal work. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) [Runner](corpus:flask:evidence/ref-8b6ebc456dd7ce1a) |
