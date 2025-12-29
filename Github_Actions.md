# Introduction to GitHub Actions

**Date:** 29 December 2024
**Lecture Topic:** Building Pipelines

## 1. Concepts
- **Workflow:** Configurable automated process defined by a YAML file.
- **Event:** Triggers a workflow (e.g., `push`, `pull_request`).
- **Job:** Set of steps that execute on the same runner.
- **Step:** Individual task (shell command or action).
- **Runner:** Server that runs the workflow.

## 2. Example Workflow
`.github/workflows/main.yml`

```yaml
name: CI
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run a one-line script
        run: echo Hello, world!
```

## 3. Runners
- **Hosted Runners:** Provided by GitHub (Ubuntu, Windows, macOS).
- **Self-Hosted Runners:** Your own machines.
