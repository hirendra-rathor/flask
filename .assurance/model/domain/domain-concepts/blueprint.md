# Blueprint

## concept-definition

### definition

A blueprint is a reusable bundle of application setup declarations. Its author records routes, hooks, templates/static resources and optionally nested blueprints or commands; attaching it applies that bundle to an application under selected naming and URL options. It is a setup contribution rather than a separately serving application.

### evidence

- [Blueprint recording and attachment](corpus:flask:evidence/ref-500e23fcccfdcddd)
- [Concrete resource/command integration](corpus:flask:evidence/ref-30595964c383760a)

## relationships

| Key | Source | Predicate | Target | Context | Conditions | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| blueprint-registration | [Blueprint](#concept-definition) | domain:builds-upon | [Behavior registration](corpus:/domain/domain-concepts/behavior-registration.md#concept-definition) | Recorded behavior declarations supply the reusable work that attachment applies to the target application. | None. | [Deferred setup and replay](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| blueprint-template-form | [Blueprint](#concept-definition) | domain:builds-upon | [Template](corpus:/domain/domain-concepts/template.md#concept-definition) | A template-bearing blueprint supplies template sources to the application's dispatching loader. | None. | [Blueprint template_folder](corpus:flask:evidence/ref-500e23fcccfdcddd) [Loader iteration](corpus:flask:evidence/e4655695c5cdbf67) |
| blueprint-static-form | [Blueprint](#concept-definition) | domain:builds-upon | [File resource](corpus:/domain/domain-concepts/file-resource.md#concept-definition) | A static-enabled blueprint contributes files through its selected static directory and attached route. | None. | [Concrete static handling](corpus:flask:evidence/ref-30595964c383760a) [Static registration](corpus:flask:evidence/ref-500e23fcccfdcddd) |
| blueprint-command-form | [Blueprint](#concept-definition) | domain:builds-upon | [Command](corpus:/domain/domain-concepts/developer-command.md#concept-definition) | A command-bearing blueprint retains a CLI group that attachment merges or registers under chosen naming options. | None. | [CLI creation](corpus:flask:evidence/ref-30595964c383760a) [CLI attachment](corpus:flask:evidence/ref-500e23fcccfdcddd) |
