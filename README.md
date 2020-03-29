# Projectional coding (or projection driven development)

1. Code all external calls, contracts, and integrations interactively in original language of involved systems.
2. Generate F# centric integration code.
3. Write F# idiomatic wiring-logic code.

## Related

- [Language projection generators for Windows Runtime](https://docs.microsoft.com/en-us/uwp/winrt-cref/winmd-files) to feel it as native as possible, but for broader set of problems

- Absolute `opposite` of [embbeded DLS](https://martinfowler.com/bliki/InternalDslStyle.html)

- Do not create custom languages and parsers as in [Language Workbenchs](https://en.wikipedia.org/wiki/Language_workbench), but use only existing standards; if there is not standard - just do raw F# coding

- Programs are texts, not binary ASTs as in [Intentional Programming](https://en.wikipedia.org/wiki/Intentional_programming)

- `Contract/api first` is subset of `Projectional coding`

# Examples

## Problem 1

You are tasked to create microservice wich aggregates data from SQL native and JSON native databases.

### Possible steps

- Create SQL scripts which do the job against first database
- Create JSON scripts to run agains JSON database
- Write definion of OpenAPI
- Validate queries and data they return with with parties (Data Engineers for queries and frontend developers for API)
- Template original queries (any custom-adhoc templating will work fine) and/or generate F# stubs-types-entries
- Code wiring logic
- Write tests in Gherking language (provide these to Testers)

### Analysis

- We use as much of discovery phase artifacts as possibe
- We communicate as effectively as possible (we will have iterate many times as system evolves)
- We get F# generated from which we can start domain modelling (if we need to)
- We write as few mappers as possible (hence can be concurrent on market with TypeScript considering speed of development)

## Problem 2

You have to read configurations in microservice in hosted environment. 

### Steps
- Generate configuration from known files (as these will be provided) in JSON
- Generate configuration from environment variables (provide all these as part of local build-run scripts)
- Wire custom hierarchy of choices
- Change wiring and configuration if host changes

### Analysis

We could delegate merging work to `Microsoft.Extensions.Configuration`, but ... (I have several pros and cons for these, need to recall, but proposed solution with compile time configuration still makes sense - software is much harded to break because of miss configuration)

## Projects

- https://github.com/Szer/GiraffeGenerator - API
- https://github.com/panesofglass/FSharp.Data.JsonSchema - API

- https://github.com/Zaid-Ajaj/Npgsql.FSharp.Analyzer - SQL
- https://github.com/rspeele/rezoom.sql - SQL

- https://github.com/fsharp/FSharp.Data - CSV, JSON, XML (these still lack generation of lenses for immutable and mutable variants)

- https://github.com/fsprojects/FSharp.Interop.Dynamic - to work with JSON as properties instead of hash maps

- https://github.com/fsprojects/FSharp.Text.RegexProvider 

- https://github.com/fsprojects/TickSpec - tests
- https://github.com/SpecFlowOSS/SpecFlow-Examples/tree/master/BowlingKata/BowlingKata-Fsharp - tests
 
- https://github.com/Fable-Fauna/Fable.Flora - styling user interfaces
- https://github.com/fable-compiler/ts2fable - web native APIs
 
- https://github.com/fsprojects/FsXaml - windows user interfaces
 
- https://github.com/fsprojects/FSharp.Configuration - YAML, INI, AppSettings, ResX
 
- https://github.com/fsprojects/SQLProvider - DDL applied to database -> schema
 
- https://github.com/Tarmil/FSharp.Data.LiteralProviders - environment variables

- https://github.com/kzu/GitInfo

- https://github.com/ctaggart/froto 

- https://github.com/fsprojects/FSharp.Data.GraphQL/

## Possible patterns

- Avoid mapping native_case or `property name with spaces` to NativeCase during code generation to improve searchability

### Possible projects
 
 - generator for ElasticSearch queries
 - F# native GRPC generator
 - GC free untyped C bindings with calli
 - Some modelling languages
 
## Why now?

- acceptancy of polyglot programming
- opensource of parsers-compilers-ides
- ide first language features
- possibility to extend build and generation via packages
- unrestanding the need to projection specific for language and richness of  F# for that 
 
## List of related concepts

- https://en.wikipedia.org/wiki/Grammar-oriented_programming
- https://en.wikipedia.org/wiki/Language-oriented_programming
- https://en.wikipedia.org/wiki/Domain-specific_language
- https://en.wikipedia.org/wiki/Data-driven_programming
- https://en.wikipedia.org/wiki/Extensible_programming
- https://arxiv.org/pdf/1904.11254.pdf 
