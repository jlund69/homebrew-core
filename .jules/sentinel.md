## 2024-05-24 - [Command Injection in GitHub Actions]
**Vulnerability:** Command injection vulnerability via `github.event.inputs` inside `run:` blocks in multiple workflow files (`dispatch-rebottle.yml`, `dispatch-build-bottle.yml`, `publish-commit-bottles.yml`).
**Learning:** Using direct string interpolation like `${{github.event.inputs.formula}}` inside a shell script block (`run:`) allows an attacker to inject shell commands if they can control the input.
**Prevention:** Pass user-controlled inputs via environment variables (`env:`) instead of direct interpolation. For example, `env: FORMULA: ${{ github.event.inputs.formula }}`, then use `$FORMULA` in the script.
