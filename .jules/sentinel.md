## 2024-10-31 - GitHub Actions Command Injection via Context Interpolation
**Vulnerability:** GitHub Actions workflow `.github/workflows/publish-commit-bottles.yml` passed user-controlled context variables (`${{ github.event.inputs.* }}`) directly into a `run` block.
**Learning:** GitHub Actions evaluates `${{ }}` expressions before executing the shell script, meaning injected shell commands within the input string would be executed by the runner, leading to command injection.
**Prevention:** Always pass user-controlled inputs to shell scripts using intermediate environment variables defined in the `env` block, and reference them in the script using standard shell variables (e.g., `$VAR`).
