# Application and extension code

## role-and-scope

### role

Application and extension code defines the application behavior that Flask hosts: setup declarations, views, hooks, template content/processors, custom commands and optional service replacements. It also initiates framework API use to build and run its own application.

### classifications

- external consumer
- external dependency

### scope

As an external consumer, application code uses setup, contexts and helpers for its own application outcomes. As an external dependency, it supplies callbacks and optional session/JSON implementations on which requested framework work relies. Signal observers consume notices. These are distinct interactions across the same application-supplied software boundary; Flask does not implement their application-specific results.

### implementation-mapping

`Scaffold` registration methods accept supplied callables; dispatch and context/template processing invoke them. `ScriptInfo` loads an application factory and FlaskGroup loads plugin commands. Session and JSON bindings permit supplied replacements, and Blinker signal sends expose observer calls. Application implementations are identified through these consumed contracts rather than inspected outside this checkout.

### evidence

- [Registration](corpus:flask:evidence/ref-426c9d8938b9fecd)
- [Invocation and replacements](corpus:flask:evidence/d3e0349504081bb5)
- [JSON binding](corpus:flask:evidence/c57b8f34cffef994)
- [Command loading](corpus:flask:evidence/fed8939d1905b99b)
- [Template processing](corpus:flask:evidence/e4655695c5cdbf67)
- [Notifications](corpus:flask:evidence/ref-3b3fcb2407028958)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| framework-context | [Application code](#role-and-scope) | architecture:participates-in-context | [Flask setting](corpus:/architecture/system-context/flask-in-applications.md#system-boundary-and-context) | External code consumes setup/helper services for its application and separately supplies the behavior Flask invokes, including command plugins and selected service replacements. | None. | [Registration](corpus:flask:evidence/ref-426c9d8938b9fecd) [Calls](corpus:flask:evidence/d3e0349504081bb5) [Commands](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-declarations | [Application code](#role-and-scope) | architecture:allocates-capability | [Compose application](corpus:/domain/required-capabilities/compose-application.md#capability-description) | Application/extension code supplies declarations, blueprint bundles, configuration and selected service implementations; Flask retains/applies them. | None. | [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd) [Application choices](corpus:flask:evidence/d3e0349504081bb5) [Provider selection](corpus:flask:evidence/c57b8f34cffef994) |
| allocates-application-behavior | [Application code](#role-and-scope) | architecture:allocates-capability | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Supplied views/hooks/error handlers provide the application-specific behavior/results selected by dispatch; Flask owns selection/conversion. | None. | [Handler invocation](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-template-content | [Application code](#role-and-scope) | architecture:allocates-capability | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Supplied template sources and registered processors contribute content/values; Flask and Jinja perform their integration/engine work. | None. | [Loaders/rendering](corpus:flask:evidence/e4655695c5cdbf67) [Processors](corpus:flask:evidence/d3e0349504081bb5) |
| allocates-custom-session | [Application code](#role-and-scope) | architecture:allocates-capability | [Retain session](corpus:/domain/required-capabilities/retain-session.md#capability-description) | When the application selects a replacement backend, that supplied implementation owns its opening/saving behavior; unseen storage details are not inferred. | None. | [session_interface binding](corpus:flask:evidence/d3e0349504081bb5) [SessionInterface](corpus:flask:evidence/be4c249245e3745e) |
| allocates-custom-json | [Application code](#role-and-scope) | architecture:allocates-capability | [Convert JSON](corpus:/domain/required-capabilities/convert-json.md#capability-description) | A selected application-supplied provider supplies its conversion/formatting through the supported contract. | None. | [Provider selection](corpus:flask:evidence/c57b8f34cffef994) [Contract](corpus:flask:evidence/c2956553392ff9ef) |
| allocates-custom-commands | [Application code](#role-and-scope) | architecture:allocates-capability | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | Application/plugin command callbacks supply custom work beyond Flask's loading/context and Click's invocation. | None. | [Command lookup/wrapping](corpus:flask:evidence/fed8939d1905b99b) |
| allocates-observers | [Application code](#role-and-scope) | architecture:allocates-capability | [Observe events](corpus:/domain/required-capabilities/observe-notifications.md#capability-description) | Connected receivers supply the observer end of notification delivery; their subsequent interpretation is outside Flask's work. | None. | [Signals](corpus:flask:evidence/ref-3b3fcb2407028958) [Sends](corpus:flask:evidence/d3e0349504081bb5) |
| corresponds-author | [Application code](#role-and-scope) | architecture:corresponds-to-domain-participant | [Application author](corpus:/domain/domain-participants/application-author.md#role-and-contribution) | Supplied declarations, handlers, templates, callbacks and observers realize the author's framework-consuming/application-behavior contribution. | None. | [Scaffold](corpus:flask:evidence/ref-426c9d8938b9fecd) [Calls](corpus:flask:evidence/d3e0349504081bb5) [Rendering](corpus:flask:evidence/e4655695c5cdbf67) |
| corresponds-architect | [Application code](#role-and-scope) | architecture:corresponds-to-domain-participant | [Application architect](corpus:/domain/domain-participants/application-architect.md#role-and-contribution) | Blueprint grouping and application-supplied service choices realize the architect's division/integration decisions, without equating the code and Human role. | None. | [Blueprints](corpus:flask:evidence/ref-500e23fcccfdcddd) [Service selection](corpus:flask:evidence/d3e0349504081bb5) [JSON selection](corpus:flask:evidence/c57b8f34cffef994) |
