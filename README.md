# pactia-lang organization repository

This repository configures the [pactia-lang](https://github.com/pactia-lang) GitHub organization.

## Contents

| Path | Purpose |
| --- | --- |
| `profile/README.md` | Organization profile — shown on `github.com/pactia-lang` |
| `SECURITY.md` | Security reporting policy |
| `ISSUE_TEMPLATE/` | Default issue forms for this repo only |
| `LICENSE` | MIT |

Repository-specific templates live in each project repo (for example `spec/.github/ISSUE_TEMPLATE/`).

## Publishing

```bash
cd .github   # from workspace root: cd /path/to/pactia-lang/.github
git init
git add .
git commit -m "Add organization profile and security policy"
git branch -M main
git remote add origin git@github.com:pactia-lang/.github.git
git push -u origin main
```

The GitHub repo name must be exactly `.github`.
