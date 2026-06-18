# Pactia

**Write the pact. AI stays below the contract line.**

Pactia is a contract language for software products: humans author durable intent (prose + `@tags`); AI implements below the line; tooling checks conformance.

## Repositories

| Repo | Status | Description |
| --- | --- | --- |
| [spec](https://github.com/pactia-lang/spec) | Active | Normative language specification (human kernel, tag registry, intent line) |
| [pactiac](https://github.com/pactia-lang/pactiac) | Active | Compiler — `pactiac compile` |
| [vscode-pactia](https://github.com/pactia-lang/vscode-pactia) | Active | VS Code / Cursor extension (syntax, tags, diagnostics) |
| [pactia](https://github.com/pactia-lang/pactia) | Planned | Package manager — `pactia init`, `pactia add`, `pactia build` |
| [examples](https://github.com/pactia-lang/examples) | Planned | Canonical workspaces and sample `.pactia` programs |

## Toolchain

| Tool | Role |
| --- | --- |
| **Pactia** | Contract language — humans write law above the contract line |
| **pactiac** | Compiler — parse, lower, emit module-scoped IR |
| **pactia** | Package manager — `pactia.toml`, `pactia.lock`, publish |

## Quick start

```bash
git clone https://github.com/pactia-lang/spec.git
git clone https://github.com/pactia-lang/pactiac.git
cd pactiac && npm install && npm run build
node packages/pactiac/dist/cli.js compile -i test/fixtures/kernel/fleet-management-v2.pactia -o ./out
```

Package manager workflows (`pactia init`, `pactia build`) are under active development.

## Specification

- Current normative version: **Pactia 1.0**
- Authoring reference: [language spec](https://github.com/pactia-lang/spec/blob/main/docs/language-spec.md)
- Contract boundary: [intent line](https://github.com/pactia-lang/spec/blob/main/docs/overview.md#the-intent-line)
- Compatibility matrix: [spec README](https://github.com/pactia-lang/spec/blob/main/README.md)

## Contributing

- Spec clarifications and RFCs: [spec issues](https://github.com/pactia-lang/spec/issues/new?template=spec_clarification.yml)
- Compiler bugs: [pactiac issues](https://github.com/pactia-lang/pactiac/issues/new?template=bug_report.yml)
- Extension bugs: [vscode-pactia issues](https://github.com/pactia-lang/vscode-pactia/issues)
- Package manager: [pactia issues](https://github.com/pactia-lang/pactia/issues) (when published)

## Links

- Documentation: https://docs.pactia.io (planned)
- Package registry: https://pactia.io (planned)
