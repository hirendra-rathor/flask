# I want to run and inspect my selected application

## intended-outcome

### desired-outcome

Application operators should be able to select a Flask application, inspect its routes, enter its interactive shell and request development serving or custom command work. Built-in command output and serving handoffs support these operations without establishing production deployment or the success of arbitrary custom work.

### evidence

- [Application-aware command interface](corpus:flask:evidence/fed8939d1905b99b)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| concerns-application | [Operations](#intended-outcome) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The command user selects the application to inspect or run. | None. | [ScriptInfo/load_app](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-command | [Operations](#intended-outcome) | domain:concerns-concept | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | Built-in and application/plugin command invocations supply the requested work. | None. | [FlaskGroup and commands](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-route | [Operations](#intended-outcome) | domain:concerns-concept | [Route](corpus:/domain/domain-concepts/route.md#concept-definition) | The route listing exposes endpoint, method and rule information for inspection. | None. | [routes_command](corpus:flask:evidence/fed8939d1905b99b) |
| concerns-context | [Operations](#intended-outcome) | domain:concerns-concept | [Context](corpus:/domain/domain-concepts/execution-context.md#concept-definition) | Application commands and shell work receive the selected application's context. | None. | [with_appcontext/shell](corpus:flask:evidence/fed8939d1905b99b) |
