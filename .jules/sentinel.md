## 2025-01-20 - Prevent Command Injection in GitHub Actions

**Vulnerability:** Found direct string interpolation of user-controlled inputs (`github.event.inputs.args`, `github.event.inputs.pull_request`) inside a `run:` block in `.github/workflows/publish-commit-bottles.yml` (`${{github.event.inputs.args}}`). This allows command injection if a user provides malicious input like `; rm -rf /`.

**Learning:** It existed because it is convenient and common to use `${{ }}` syntax in GitHub Actions to inject variables, without realizing that when used inside a `run:` block, it is evaluated as a raw shell command string before execution, opening up the shell script to injection attacks.

**Prevention:** Always pass user-controlled inputs (like `github.event.inputs`, `github.head_ref`, etc.) into shell scripts using intermediate environment variables defined in the `env:` block. Then, reference these environment variables in the `run:` block using standard shell syntax (e.g., `$MY_VAR` or `"$MY_VAR"`).
