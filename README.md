# PolicyPress Template

[![Build Policies](https://github.com/sc2in/policypress-template/actions/workflows/build.yml/badge.svg)](https://github.com/sc2in/policypress-template/actions/workflows/build.yml)

Write policies in Markdown. Push to GitHub. Get a PDF library and a policy website automatically.

## Quickstart

1. **[Use this template](https://github.com/sc2in/policypress-template/generate)** to create your own repo
2. Edit `config.toml` - set your organization name, base URL, and brand color
3. Replace `static/logo.png` with your logo
4. Push to `main` - GitHub Actions builds your PDFs and deploys your policy site

GitHub Pages must be enabled in your repo settings (Settings → Pages → Source: GitHub Actions).

## What's included

| Path | Purpose |
|---|---|
| `config.toml` | Site and PDF configuration |
| `content/policies/` | Example policies in Markdown |
| `.github/workflows/build.yml` | CI/CD: builds PDFs, deploys to GitHub Pages |
| `static/logo.png` | Placeholder logo - replace with yours |

### Example policies

- **Access Control** - user provisioning, MFA, access reviews, revocation
- **Incident Response** - severity tiers, IR phases, escalation, evidence handling
- **Data Classification** - four-tier classification framework, handling requirements

Add your own policies as Markdown files in `content/policies/`. Each file uses YAML frontmatter for metadata (owner, review date, revision history, compliance mappings).

## Configuration

Open `config.toml` and update at minimum:

```toml
base_url = "https://policies.yourcompany.com"   # your GitHub Pages URL

[extra.policypress]
organization = "Your Company Name"
pdf_color = "#your-brand-color"

[extra.author]
email = "security@yourcompany.com"
```

## Policy frontmatter

Each policy file starts with metadata:

```yaml
---
title: "Policy Name"
description: "One-line description"
date: 2025-01-01
weight: 10          # controls sort order
taxonomies:
  SCF: [IAC-01]     # compliance framework mappings (optional)
extra:
  owner: Security Team
  last_reviewed: 2025-01-01
  major_revisions:
    - date: 2025-01-01
      description: Initial policy.
      version: "1.0"
---
```

## Features

- `{{ org() }}` - inserts your organization name anywhere in policy text
- `{% redact() %}...{% end %}` - marks blocks for PDF redaction (run with `--redact`)
- `{% admonition(type="note") %}...{% end %}` - styled callout boxes (note, tip, warning)
- Draft watermark - run the workflow with `draft: true` to stamp PDFs

## Full documentation

See [sc2in/PolicyPress](https://github.com/sc2in/PolicyPress) for the full action reference, CLI usage, and advanced configuration.
