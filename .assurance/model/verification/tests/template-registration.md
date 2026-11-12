# Test template filter, test and global registration

## verification-approach

### test-kind

component

### test-description

Tests register application or blueprint filters, template tests and globals through decorators and explicit methods, using default or supplied names. They access registered callables through jinja_env and use them from real templates; blueprint cases apply the bundle before consumption.

### intended-focus

The family intends to exercise registration and naming of application-supplied template behavior, including deferred blueprint application. The callable's reversal/boolean/example result is fixture work rather than a framework business capability.

### evidence

- [Application registration](corpus:flask:evidence/b9a40085d1c441ed)
- [Blueprint registration](corpus:flask:evidence/ref-3555f61ca01a0199)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| compose | [Approach](#verification-approach) | verification:targets-for-testing | [Compose application](corpus:/domain/required-capabilities/compose-application.md#capability-description) | Declarations install named template behavior directly or through a bundle. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) [Bundle](corpus:flask:evidence/ref-3555f61ca01a0199) |
| adaptation | [Approach](#verification-approach) | verification:targets-for-testing | [Adaptation aim](corpus:/domain/intentions/adapt-services.md#intended-outcome) | Authors deliberately add template behavior through supported extension points. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
| registration | [Approach](#verification-approach) | verification:targets-for-testing | [Behavior registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Callable registration and chosen name are the intended subjects. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Register behavior](corpus:/subsystem-design/local-capabilities/register-behavior.md#capability-description) | Direct and deferred template declarations are applied. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) [Bundle](corpus:flask:evidence/ref-3555f61ca01a0199) |
| setup | [Approach](#verification-approach) | verification:targets-for-testing | [Setup](corpus:/subsystem-design/components/application-setup.md#role-and-implementation) | The intended portion retains and applies template registrations. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
| renderer | [Approach](#verification-approach) | verification:targets-for-testing | [Renderer](corpus:/subsystem-design/components/template-renderer.md#role-and-implementation) | Its environment integration exposes named behavior to templates. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
| integrator | [Approach](#verification-approach) | verification:targets-for-testing | [Template integrator](corpus:/architecture/architectural-participants/template-integrator.md#role-and-scope) | Registered environment behavior is deliberately consumed during rendering. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
| api | [Approach](#verification-approach) | verification:targets-for-testing | [Setup API](corpus:/subsystem-interfaces/interfaces/setup-api.md#interface-definition) | Callers submit filter/test/global declarations through setup methods. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
| exchange | [Approach](#verification-approach) | verification:targets-for-testing | [Setup declarations](corpus:/subsystem-interfaces/exchanges/setup-declarations.md#exchange-behavior) | Names and supplied functions cross the registration boundary. | None. | [Registration](corpus:flask:evidence/b9a40085d1c441ed) |
