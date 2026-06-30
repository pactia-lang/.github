# Pactia

### The intent language for the AI era

**You write what must stay true. AI writes how it works.**

Like Rust is compiled by `rustc` and shared on crates.io — Pactia is an **AI-native programming language** compiled by **pactiac**, managed by **pactia**, with packages on **pactia.io**.

---

### The problem

Every AI coding session starts cold. Agents re-read scattered READMEs, stale OpenAPI, old ADRs, and Slack threads — then guess. Auth drifts. Pagination diverges. Event shapes disagree. Senior engineers fix what the model invented instead of shaping what matters.

The model is not the problem. **Durable product intent lives nowhere.**

---

### A new paradigm

| Era | You write | The machine |
| --- | --- | --- |
| 3GL — C, Rust | Algorithms + types | Executes |
| 4GL — SQL, Terraform | Desired state | Reconciles |
| **Pactia** | **Intent — what must stay true** | **Implements; tooling verifies** |

Pactia does not replace Rust, TypeScript, or Swift. It sits **above** them — a versioned layer between humans, AI agents, and generated code.

---

### The intent line

```
┌─────────────────────────────────────────────┐
│  ABOVE THE LINE — Intent                    │
│  Entities · APIs · Roles · Policy · Stack   │
│  Prose · Tags · Packages · Provenance       │
└─────────────────────────────────────────────┘
────────────── conformance gate ───────────────
┌─────────────────────────────────────────────┐
│  BELOW THE LINE — Implementation            │
│  Logic · indexes · edge cases · tuning      │
│  Owned by AI and engineers. Free.           │
└─────────────────────────────────────────────┘
```

Above the line: what every session must inherit — regardless of model, engineer, or sprint.  
Below the line: how it works today. Pactia never owns it.

---

### Prose is programming

The most deliberate choice in Pactia: **natural language is not a comment to discard — it is a first-class input.**

Lines that are not `@tags` or macros are prose. `pactiac` preserves them, tags them with provenance, and tooling turns them into grounded agent context — alongside deterministic facts from tags.

A product owner can describe the product in plain English. An architect adds `@entity`, `@api`, `@auth`, `@test`. **Same language. Same pipeline. Same repository.**

---

### Share intent like code

The prompt is not the package. Chat history dies. **`import @pactia/kyc-compliance;`** pins the same intent in every repo, every session, every agent.

| Package kind | Example | Purpose |
| --- | --- | --- |
| **Stack** | `@pactia/rust-stack` | Platform law — language, errors, pagination |
| **Kernel** | `@pactia/kernel` | Core tags, macros, and registry defaults |
| **Surface** | `@pactia/html-css-js` | UI / static-site stack macros |

Immutable versions. Digest-pinned lockfiles. Publisher identity. **Users fork packages, not the language.**

---

## See it

Fleet management in **Pactia 1.2** — tags and macros where structure matters, prose-only with `#rust-stack`:

```pactia
pactia 1.0

import @pactia/kernel;
import @pactia/rust-stack;

product FleetManagement {
  > Track vehicles and fleets. Customers see only their own vehicles.

  context fleet_audit_policy {
    path: "./context/fleet/audit-policy.md",
  }

  #rust-stack

  @topology { mode: microservices, }
  @guide {
    > Cursor pagination on every list — never offset
  }

  module fleet {
    @actor admins { role: Admin, capabilities: [manage_fleets], }
    @actor customers { role: Customer, capabilities: [track_vehicles], }

    model {
      @entity Vehicle {
        @@pk
        id: uuid,
        customerId: uuid,
        vin: string,
        label: string,
        status: VehicleStatus,
      }
    }

    service FleetService {
      #database
      @auth { roles: [Customer, Admin] }

      #list
      @api list_vehicles {
        method: GET,
        path: "/api/v1/vehicles",
      }

      @auth { roles: [Admin] }
      #create
      @api create_vehicle {
        method: POST,
        path: "/api/v1/vehicles",
      }
    }
  }
}
```

[Full mini example](https://github.com/pactia-lang/.github/blob/main/profile/examples/fleet-management-mini.pactia)
· [Prose-only variant](https://github.com/pactia-lang/.github/blob/main/profile/examples/fleet-management-prose.pactia)
· [Relay fixture (pactiac)](https://github.com/pactia-lang/pactiac/blob/main/test/fixtures/kernel/relay.pactia)
· [Marketplace example](https://github.com/pactia-lang/examples/tree/main/marketplace)
· [Language spec](https://github.com/pactia-lang/spec/blob/main/docs/language-spec.md)

---

### Get started

```bash
# Install pactia package manager (includes compiler)
curl -fsSL https://raw.githubusercontent.com/pactia-lang/pactia/main/scripts/install-pactia.sh | bash -s v0.4.0

# VS Code / Cursor extension
code --install-extension pactia-lang.pactia
```

```bash
pactia init my-product --name MyProduct
pactia add @pactia/rust-stack ^1.0
pactia build -C my-product
```

Compiler-only: [pactiac v0.4.0](https://github.com/pactia-lang/pactiac/releases/tag/v0.4.0).

---

### The stack

```
*.pactia  ──pactiac──▶  AI-neutral IR  ──▶  agent context + specifications
              ▲
         pactia — init, add, install, update, build, lockfiles
```

| | Repo | Role |
| --- | --- | --- |
| Language | [spec](https://github.com/pactia-lang/spec) | Pactia 1.2 — grammar, tags, packages, attach |
| Compiler | [pactiac](https://github.com/pactia-lang/pactiac) | Deterministic compile to module-scoped IR |
| Packages | [pactia](https://github.com/pactia-lang/pactia) | `pactia init`, `add`, `install`, `update`, `build` |
| Editor | [vscode-pactia](https://github.com/pactia-lang/vscode-pactia) | Syntax highlighting (`pactia-lang.pactia`) |
| Examples | [examples/marketplace](https://github.com/pactia-lang/examples) | Multi-module attach workspace |

**Model-agnostic by design.** Switch Cursor, Claude Code, or Copilot — your `.pactia` files and lockfile stay the same.

---

### In one sentence

Pactia is the durable, versioned layer between human intent and AI implementation — so every agent, every session, every model starts from the same ground truth about what your product must be.

---

**Get involved** — [spec issues](https://github.com/pactia-lang/spec/issues/new?template=spec_clarification.yml) · [pactiac](https://github.com/pactia-lang/pactiac/issues) · [vscode-pactia](https://github.com/pactia-lang/vscode-pactia/issues)

[pactia.io](https://pactia.io) · [docs.pactia.io](https://docs.pactia.io) *(coming soon)*
