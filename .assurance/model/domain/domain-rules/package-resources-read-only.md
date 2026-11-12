# Application package-resource opening MUST reject write modes

## rule-definition

### rule-statement

Flask's application open_resource operation MUST reject modes other than r, rt and rb, so this package-resource operation opens files only for reading.

### scope-and-conditions

The constraint applies to the inspected application method's mode check. The separate open_instance_resource operation permits write modes. It is not a general filesystem access policy or a guarantee that all code treats package files as immutable.

### evidence

- [Resource mode checks](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| protects-composition | [Read-only rule](#rule-definition) | domain:protects-intent | [Assemble application](corpus:/domain/intentions/compose-application.md#intended-outcome) | Package-resource reading supports application setup data without this API permitting a write mode. | None. | [open_resource](corpus:flask:evidence/d3e0349504081bb5) |
| applies-file | [Read-only rule](#rule-definition) | domain:applies-to | [File resource](corpus:/domain/domain-concepts/file-resource.md#concept-definition) | Package-relative resources opened through this method are restricted to read modes. | None. | [open_resource](corpus:flask:evidence/d3e0349504081bb5) |
| applies-access | [Read-only rule](#rule-definition) | domain:applies-to | [Access resources](corpus:/domain/required-capabilities/access-resources.md#capability-description) | The package-root form is read-only while the distinct instance-root form permits caller-selected write modes. | None. | [Resource methods](corpus:flask:evidence/d3e0349504081bb5) |
