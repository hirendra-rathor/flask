# Test CLI application discovery

## verification-approach

### test-kind

component

### test-description

Tests call find_best_app, prepare_import, locate_app and ScriptInfo.load_app with module-like objects, real fixture modules, object/factory expressions and changed working directories. Repeated loading and missing/ambiguous/invalid selections distinguish the scenarios.

### intended-focus

The family intends to exercise application selection, import-path preparation and cached discovery for CLI use. Fixture factories provide applications; their arbitrary names and bodies do not become separate framework requirements.

### evidence

- [CLI discovery scenarios](corpus:flask:evidence/ref-4e8715c7a425ee52)
- [Selected fixture factories](corpus:flask:evidence/b5b1a0bf39d1ff82)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| ability | [Approach](#verification-approach) | verification:targets-for-testing | [Run commands](corpus:/domain/required-capabilities/run-commands.md#capability-description) | The intended portion selects the application for subsequent command work. | None. | [Discovery](corpus:flask:evidence/ref-4e8715c7a425ee52) |
| intention | [Approach](#verification-approach) | verification:targets-for-testing | [Selected application operations](corpus:/domain/intentions/developer-operations.md#intended-outcome) | Application discovery is directly selected by module/factory inputs. | None. | [Discovery](corpus:flask:evidence/ref-4e8715c7a425ee52) |
| control | [Approach](#verification-approach) | verification:targets-for-testing | [CLI application selection](corpus:/subsystem-design/configuration-controls/cli-application.md#configuration-description) | Import paths, object/factory selections and create_app are explicit inputs. | None. | [Discovery](corpus:flask:evidence/ref-4e8715c7a425ee52) |
| local | [Approach](#verification-approach) | verification:targets-for-testing | [Run developer commands](corpus:/subsystem-design/local-capabilities/run-commands.md#capability-description) | Application loading/caching is the tested portion of command preparation. | None. | [Discovery](corpus:flask:evidence/ref-4e8715c7a425ee52) |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [Developer CLI](corpus:/subsystem-design/components/developer-cli.md#role-and-implementation) | ScriptInfo and discovery helpers are invoked directly. | None. | [Discovery](corpus:flask:evidence/ref-4e8715c7a425ee52) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [CLI role](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | The intended responsibility discovers the selected application. | None. | [Discovery](corpus:flask:evidence/ref-4e8715c7a425ee52) |
