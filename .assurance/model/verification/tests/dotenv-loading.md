# Test optional dotenv loading

## verification-approach

### test-kind

integration

### test-description

When python-dotenv is available, scenarios use real fixture .env/.flaskenv files, selected paths, an existing environment value and a changed working directory. They call load_dotenv or FlaskGroup with skip selection. A separate condition replaces the optional module with an unavailable binding.

### intended-focus

The family intends to exercise the CLI's optional environment-loading collaboration and opt-out/path choices. The optional-dependency arrangement belongs to this focus; it is not evidence of an actual command run or installed dependency in the modeled user's environment.

### evidence

- [Dotenv scenarios](corpus:flask:evidence/ref-4e8715c7a425ee52)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| component | [Approach](#verification-approach) | verification:targets-for-testing | [CLI](corpus:/subsystem-design/components/developer-cli.md#role-and-implementation) | Optional dotenv integration and skip choice are the intended subresponsibility. | None. | [Dotenv](corpus:flask:evidence/ref-4e8715c7a425ee52) |
| participant | [Approach](#verification-approach) | verification:targets-for-testing | [CLI role](corpus:/architecture/architectural-participants/developer-cli.md#role-and-scope) | The role's consumed environment-loading aid is deliberately exercised. | None. | [Dotenv](corpus:flask:evidence/ref-4e8715c7a425ee52) |
