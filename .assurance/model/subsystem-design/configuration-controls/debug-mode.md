# Debug mode

## configuration-description

### configuration

Debug mode selects development-oriented behavior for a Flask application. It can affect development-server debugging/reloading, template auto-reload when no explicit reload choice is set, JSON response formatting, exception propagation, and default logger level.

### usage-and-effect

DEBUG is exposed through app.debug. The CLI maps --debug and FLASK_DEBUG into the application's flag and development server options. The template environment, default JSON provider, exception handler and logger read debug mode for their respective choices.

### evidence

- [Debug property](corpus:flask:evidence/c57b8f34cffef994)
- [CLI](corpus:flask:evidence/fed8939d1905b99b)
- [Exception/environment handling](corpus:flask:evidence/d3e0349504081bb5)
- [JSON formatting](corpus:flask:evidence/c2956553392ff9ef)
- [Logger](corpus:flask:evidence/ref-7d6f91d952bb5e04)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| used-cli | [Debug](#configuration-description) | subsystem-design:used-by-component | [CLI](corpus:/subsystem-design/components/developer-cli.md#role-and-implementation) | CLI loading binds debug and run_command selects debugger/reloader choices from it. | None. | [CLI](corpus:flask:evidence/fed8939d1905b99b) |
| used-dispatch | [Debug](#configuration-description) | subsystem-design:used-by-component | [Dispatcher](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | Exception handling and integrated request/logging diagnostics read debug mode. | None. | [Errors](corpus:flask:evidence/d3e0349504081bb5) [Logging](corpus:flask:evidence/ref-7d6f91d952bb5e04) |
| used-template | [Debug](#configuration-description) | subsystem-design:used-by-component | [Renderer](corpus:/subsystem-design/components/template-renderer.md#role-and-implementation) | Template reload inherits debug when TEMPLATES_AUTO_RELOAD is unspecified. | None. | [Environment](corpus:flask:evidence/d3e0349504081bb5) |
| used-json | [Debug](#configuration-description) | subsystem-design:used-by-component | [JSON provider](corpus:/subsystem-design/components/json-provider.md#role-and-implementation) | Default provider chooses indented JSON in debug mode when compact is unspecified. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
| qualifies-run | [Debug](#configuration-description) | subsystem-design:qualifies-capability | [Run commands](corpus:/subsystem-design/local-capabilities/run-commands.md#capability-description) | Debug supplies development-server debugger/reloader selections unless explicitly chosen. | None. | [Run](corpus:flask:evidence/fed8939d1905b99b) |
| qualifies-dispatch | [Debug](#configuration-description) | subsystem-design:qualifies-capability | [Handle request](corpus:/subsystem-design/local-capabilities/handle-request.md#capability-description) | Debug affects exception propagation when PROPAGATE_EXCEPTIONS is unspecified. | None. | [Error handling](corpus:flask:evidence/d3e0349504081bb5) |
| qualifies-render | [Debug](#configuration-description) | subsystem-design:qualifies-capability | [Render template](corpus:/subsystem-design/local-capabilities/render-template.md#capability-description) | Debug supplies auto_reload only without an explicit reload choice. | None. | [Environment](corpus:flask:evidence/d3e0349504081bb5) |
| qualifies-json | [Debug](#configuration-description) | subsystem-design:qualifies-capability | [JSON](corpus:/subsystem-design/local-capabilities/encode-decode-json.md#capability-description) | Debug affects the default provider's response formatting when compact is unspecified. | None. | [Provider](corpus:flask:evidence/c2956553392ff9ef) |
