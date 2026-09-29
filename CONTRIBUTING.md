# 🤝 Contributing

Thanks for your interest in **45 Days of DevOps**! This is primarily a personal learning repository, but corrections, improvements, and new incident scenarios are welcome.

## Ways to Contribute

- Fix typos, broken commands, or outdated versions
- Improve explanations or diagrams
- Add new **incident scenarios** (the most valuable contribution)
- Suggest better practices for any lab
- Report security concerns in the sample configs

## Getting Started

1. Fork the repository
2. Create a branch:
   ```bash
   git checkout -b feat/short-description
   ```
3. Make your changes
4. Test them locally (see below)
5. Commit using the convention below
6. Open a pull request against `main`

## Commit Convention

Use [Conventional Commits](https://www.conventionalcommits.org/):

| Type | Use for |
|------|---------|
| `feat` | New lab, incident, or module |
| `fix` | Correcting an error in a lab or doc |
| `docs` | README, notes, and write-ups |
| `chore` | Tooling, repo housekeeping |
| `ci` | Workflow changes |

Examples:

```text
feat(kubernetes): add OOMKilled incident drill
fix(docker): correct healthcheck command in compose file
docs(sre): expand error budget explanation
```

## Adding an Incident

Place it in the relevant `incidents/` folder (for example `02-kubernetes/incidents/`) and use this format:

```markdown
# Incident: <short title>

## Symptom
What was observed.

## Reproduce
Exact commands or manifests that trigger the failure.

## Investigation
Commands used and what they revealed (logs, events, describe, metrics).

## Root Cause
Why it happened.

## Fix
What resolved it.

## Prevention
How to avoid or detect it earlier (probes, alerts, policy, tests).
```

## Guidelines

- **Keep labs reproducible.** Someone should be able to run them from a clean state.
- **Pin versions** where practical instead of using `latest`.
- **Never commit secrets**, credentials, `.env` files, or Terraform state.
- **Mark cost.** If a lab creates billable AWS resources, say so and include cleanup steps.
- **Explain the why**, not only the commands.
- Keep pull requests small and focused.

## Testing Your Changes

| Area | Check |
|------|-------|
| Docker | `docker compose up --build` runs cleanly |
| Kubernetes | `kubectl apply --dry-run=client -f <file>` passes |
| Terraform | `terraform fmt -check` and `terraform validate` pass |
| Helm | `helm lint <chart>` passes |
| Python | `python -m compileall .` passes |

## Code of Conduct

Be respectful, constructive, and welcoming. Feedback should be specific and kind. Harassment or discrimination of any kind is not tolerated.

## Questions

Open an issue with the `question` label and include as much context as you can.