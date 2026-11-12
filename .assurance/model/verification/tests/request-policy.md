# Test request limit and host settings

## verification-approach

### test-kind

component

### test-description

Tests select MAX_CONTENT_LENGTH and submit a large form body, inspect Request limit bindings with and without application context, set request-specific overrides, and submit hosts under a TRUSTED_HOSTS choice. The real request wrapper/toolkit is used through Flask.

### intended-focus

The family intends to exercise application/request policy bindings and request handling under selected body/form/host conditions. It does not supply an independent parser-enforcement analysis or a new universal host-security requirement.

### evidence

- [Request policy scenarios](corpus:flask:evidence/bd349e6112b08d91)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| settings | [Approach](#verification-approach) | verification:targets-for-testing | [Settings](corpus:/domain/domain-concepts/settings.md#concept-definition) | Explicit application and per-request choices qualify the request. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| request | [Approach](#verification-approach) | verification:targets-for-testing | [Request](corpus:/domain/domain-concepts/request.md#concept-definition) | Body/form data and incoming host vary the request condition. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| body | [Approach](#verification-approach) | verification:targets-for-testing | [Body limit](corpus:/subsystem-design/configuration-controls/request-body-limit.md#configuration-description) | MAX_CONTENT_LENGTH and wrapper overrides are deliberate inputs. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| fields | [Approach](#verification-approach) | verification:targets-for-testing | [Form field limit](corpus:/subsystem-design/configuration-controls/form-field-limit.md#configuration-description) | The scenario selects application values and request-specific overrides. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| parts | [Approach](#verification-approach) | verification:targets-for-testing | [Form part limit](corpus:/subsystem-design/configuration-controls/form-part-limit.md#configuration-description) | MAX_FORM_PARTS binding/override is a direct scenario subject. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [Dispatcher/wrappers](corpus:/subsystem-design/components/request-dispatcher.md#role-and-implementation) | Wrapper integration and host-qualified request handling are the tested portions. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [Coordinator](corpus:/architecture/architectural-participants/application-coordinator.md#role-and-scope) | The intended responsibility is application settings applied to incoming requests. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
| handling | [Approach](#verification-approach) | verification:targets-for-testing | [Handle requests](corpus:/domain/required-capabilities/handle-request.md#capability-description) | Form-body and selected-host requests exercise qualified handling. | None. | [Policy](corpus:flask:evidence/bd349e6112b08d91) |
