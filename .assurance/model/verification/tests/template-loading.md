# Test template loader integration

## verification-approach

### test-kind

integration

### test-description

Tests install a real Jinja DictLoader through a Flask override, select from an iterable of template names, list application/blueprint templates and use customized Environment classes. A missing-template scenario enables loading diagnostics with a capturing log handler.

### intended-focus

The family intends to exercise complementary Flask-loader/Jinja selection, replaceable environment/loader choices and lookup diagnostics. The fixture applications locate template sources; their application business behavior is not a target.

### evidence

- [Loader scenarios](corpus:flask:evidence/b9a40085d1c441ed)
- [Fixture bundle composition](corpus:flask:evidence/ref-9c061590a6da3d25)
- [Admin template source](corpus:flask:evidence/ref-714e2fae71cf06ac)
- [Frontend template source](corpus:flask:evidence/ref-27d62f0e979309a8)
- [Blueprint sources/listing](corpus:flask:evidence/ref-3555f61ca01a0199)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| ability | [Approach](#verification-approach) | verification:targets-for-testing | [Render templates](corpus:/domain/required-capabilities/render-template.md#capability-description) | Named/alternative source lookup is the targeted rendering portion. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| adaptation | [Approach](#verification-approach) | verification:targets-for-testing | [Adapt services](corpus:/domain/intentions/adapt-services.md#intended-outcome) | Custom environment and loader classes deliberately replace integration choices. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| template | [Approach](#verification-approach) | verification:targets-for-testing | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | Application/blueprint source identity and selected alternatives are intended subjects. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) [Blueprints](corpus:flask:evidence/ref-3555f61ca01a0199) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Render](corpus:/subsystem-design/local-capabilities/render-template.md#capability-description) | Template selection is exercised through rendering entry points. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [Renderer](corpus:/subsystem-design/components/template-renderer.md#role-and-implementation) | Source lookup, environment binding and diagnostics are the intended portion. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| engine | [Approach](#verification-approach) | verification:targets-for-testing | [Jinja component](corpus:/subsystem-design/components/jinja-engine.md#role-and-implementation) | Real engine selection/listing calls deliberately use configured loaders. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| integrator | [Approach](#verification-approach) | verification:targets-for-testing | [Integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | The framework's loader contribution is a direct focus. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| jinja | [Approach](#verification-approach) | verification:targets-for-testing | [Jinja](corpus:/architecture/architectural-participants/jinja.md#role-and-scope) | The real engine consumes source lookup and returns selected templates. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| api | [Approach](#verification-approach) | verification:targets-for-testing | [Engine API](corpus:/subsystem-interfaces/interfaces/template-engine-api.md#interface-definition) | Both engine selection and complementary loader roles are exercised. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
| exchange | [Approach](#verification-approach) | verification:targets-for-testing | [Template exchange](corpus:/subsystem-interfaces/exchanges/template-rendering.md#exchange-behavior) | Source selection and loader results identify the exercised exchange. | None. | [Loaders](corpus:flask:evidence/b9a40085d1c441ed) |
