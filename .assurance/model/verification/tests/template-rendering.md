# Test template rendering and contextual values

## verification-approach

### test-kind

integration

### test-description

Scenarios render named or source-string templates using real Jinja, explicitly supplied values and context processors. They arrange framework globals, application-only rendering, filename-sensitive escaping, markup, macros and streamed template output. Template fixture files supply authored rendering content.

### intended-focus

The family intends to exercise Flask/Jinja value assembly and text/stream production, including explicit values alongside framework/context-processor values. It targets integration and rendering forms, without assessing the application's template policy or assertion adequacy.

### evidence

- [Rendering scenarios](corpus:flask:evidence/b9a40085d1c441ed)
- [Context-value fixture](corpus:flask:evidence/ref-5354e1694b7dde35)
- [Macro fixture](corpus:flask:evidence/f54a3cd7a5e94fe9)
- [Blueprint template scenarios](corpus:flask:evidence/ref-3555f61ca01a0199)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| ability | [Approach](#verification-approach) | verification:targets-for-testing | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Names, source strings and value mappings directly request generated text. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| intention | [Approach](#verification-approach) | verification:targets-for-testing | [Useful content forms](corpus:/domain/intentions/produce-representations.md#intended-outcome) | Rendered text and streams identify the intended output form. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| template | [Approach](#verification-approach) | verification:targets-for-testing | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Named/source-string and macro scenarios deliberately use authored template forms. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| context | [Approach](#verification-approach) | verification:targets-for-testing | [Contextual data ability](corpus:/domain/required-capabilities/contextual-work.md#capability-description) | Standard-context and request-less rendering explicitly exercise contextual value availability. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Local render](corpus:/subsystem-design/local-capabilities/render-template.md#capability-description) | Context assembly and render/stream entry points are directly called. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| renderer | [Approach](#verification-approach) | verification:targets-for-testing | [Renderer](corpus:/subsystem-design/components/template-renderer.md#role-and-implementation) | The intended responsibility integrates globals, processor values and engine work. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| engine | [Approach](#verification-approach) | verification:targets-for-testing | [Jinja component](corpus:/subsystem-design/components/jinja-engine.md#role-and-implementation) | Real template compilation/rendering and macro invocation deliberately cross this boundary. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [Integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Value preparation and rendered text/iteration are intended framework contributions. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| jinja | [Approach](#verification-approach) | verification:targets-for-testing | [Jinja role](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | The actual engine interprets deliberately selected template forms. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| api | [Approach](#verification-approach) | verification:targets-for-testing | [Engine API](corpus:/subsystem-interfaces/interfaces/template-engine-api.md#interface-definition) | Compilation/render/generate work uses the real engine boundary. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| exchange | [Approach](#verification-approach) | verification:targets-for-testing | [Template exchange](corpus:/subsystem-interfaces/exchanges/template-rendering.md#exchange-behavior) | Selection/source/value inputs and rendered text/iteration identify the exchange. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| callbacks | [Approach](#verification-approach) | verification:targets-for-testing | [Processor callback API](corpus:/subsystem-interfaces/interfaces/application-callbacks.md#interface-definition) | Registered context processors are an intentional arrangement. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
| processor-values | [Approach](#verification-approach) | verification:targets-for-testing | [Handler exchange](corpus:/subsystem-interfaces/exchanges/handler-invocation.md#exchange-behavior) | Processor mapping results deliberately contribute rendering values. | None. | [Templates](corpus:flask:evidence/b9a40085d1c441ed) |
