## 2023-10-30 - GitHub Actions Command Injection
**Vulnerability:** User-controlled inputs (`github.event.inputs.args` and `github.event.inputs.pull_request`) were interpolated directly into a bash command within a GitHub Actions workflow.
**Learning:** Direct interpolation of inputs via `${{ }}` in `run:` blocks allows attackers to execute arbitrary shell commands if the inputs contain shell metacharacters.
**Prevention:** Always pass user-controlled inputs via environment variables in the `env:` block and reference them as shell variables (e.g., `$VAR_NAME`) within the `run:` script.
