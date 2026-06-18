# Pactia

**Write the pact. AI stays below the contract line.**

---

### The problem

AI can ship code fast — but product intent scatters across prompts, tickets, and stale docs.  
Teams lose the line between *what the product must do* and *how an agent chose to implement it today*.

### The idea

**Pactia** is a contract language for whole products. Humans write durable law above the line — prose plus `@tags` for stack, API, data, security, and tests. Tooling lowers that law to IR. AI implements **below** the line and is checked against the pact.

One source of truth. One compile path. Conformance you can audit.

---

## See it

Fleet management in Pactia 1.0 — product rules, stack binding, tenancy, and module actors in a single `.pactia` file:

<p align="center">
  <img
    src="./assets/fleet-management-example.png"
    alt="Pactia 1.0 example: FleetManagement product with @stack, @topology, @tenancy, @guide, and fleet module @actor"
    width="720"
    style="border: 1px solid #d1d9e0; border-radius: 12px; max-width: 100%;"
  />
</p>

<p align="center">
  <a href="https://github.com/pactia-lang/spec/blob/main/fixtures/kernel/fleet-management-v2.pactia">View full fixture in spec →</a>
</p>

---

## What you get

| Layer | Repo | What it does |
| --- | --- | --- |
| **Law** | [spec](https://github.com/pactia-lang/spec) | Normative Pactia 1.0 — language, tag registry, intent line |
| **Compiler** | [pactiac](https://github.com/pactia-lang/pactiac) | `pactiac compile` — parse, lower, emit module-scoped IR |
| **Editor** | [vscode-pactia](https://github.com/pactia-lang/vscode-pactia) | Syntax, tags, and diagnostics in VS Code / Cursor |
| **Packages** | [pactia](https://github.com/pactia-lang/pactia) | `pactia.toml`, lockfiles, publish *(in progress)* |
| **Examples** | [examples](https://github.com/pactia-lang/examples) | Canonical workspaces *(planned)* |

---

## Try the compiler

```bash
git clone https://github.com/pactia-lang/pactiac.git
cd pactiac && npm install && npm run build
node packages/pactiac/dist/cli.js compile \
  -i test/fixtures/kernel/fleet-management-v2.pactia \
  -o ./out
```

Read the spec: [language reference](https://github.com/pactia-lang/spec/blob/main/docs/language-spec.md) · [intent line](https://github.com/pactia-lang/spec/blob/main/docs/overview.md#the-intent-line)

---

## Get involved

- Spec design and clarifications → [open an issue in spec](https://github.com/pactia-lang/spec/issues/new?template=spec_clarification.yml)
- Compiler bugs → [pactiac issues](https://github.com/pactia-lang/pactiac/issues/new?template=bug_report.yml)
- Extension feedback → [vscode-pactia issues](https://github.com/pactia-lang/vscode-pactia/issues)

**docs.pactia.io** and **pactia.io** (registry) — coming soon.
