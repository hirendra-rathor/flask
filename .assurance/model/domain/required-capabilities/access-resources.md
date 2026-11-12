# Access application resource files

## capability-description

### capability

An application author opens a resource relative to the application's package root for reading, or opens a file relative to its instance directory with a selected mode.

### expected-result

The caller receives a file handle in the requested supported text/binary form. Package-resource opening restricts modes to reading; instance-resource opening permits write modes. The caller interprets the contents, as when an application reads its own schema for initialization.

### evidence

- [Resource methods](corpus:flask:evidence/d3e0349504081bb5)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| supports-composition | [Resources](#capability-description) | domain:contributes-to-intent | [Assemble application](corpus:/domain/intentions/compose-application.md#intended-outcome) | Application-relative resource access supplies authored application data for its own setup and support work; it does not interpret schemas itself. | None. | [open_resource/open_instance_resource](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-file | [Resources](#capability-description) | domain:concerns-concept | [File resource](corpus:/domain/domain-concepts/file-resource.md#concept-definition) | Resource methods open the selected content relative to application package/instance roots. | None. | [Resource methods](corpus:flask:evidence/d3e0349504081bb5) |
| concerns-application | [Resources](#capability-description) | domain:concerns-concept | [Application](corpus:/domain/domain-concepts/application.md#concept-definition) | The application's roots determine which location is used for the supplied resource path. | None. | [Resource methods](corpus:flask:evidence/d3e0349504081bb5) |
