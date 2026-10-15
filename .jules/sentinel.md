## 2024-05-01 - Prevent Command Injection in GitHub Actions
**Vulnerability:** Command injection in GitHub Actions due to direct string interpolation of `github.event.inputs` inside `run:` blocks in `.github/workflows/dispatch-rebottle.yml`, `.github/workflows/publish-commit-bottles.yml`, and `.github/workflows/dispatch-build-bottle.yml`.
**Learning:** Using `${{ github.event.inputs.* }}` directly in bash scripts allows malicious input to execute arbitrary commands.
**Prevention:** Always pass user-controlled inputs to shell scripts via environment variables (in the `env:` block) and reference them safely using standard bash variables (e.g., `$FORMULA`).
