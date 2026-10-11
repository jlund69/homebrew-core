## 2024-10-11 - [Command Injection via github.event.inputs]
**Vulnerability:** Found direct interpolation of `${{ github.event.inputs }}` in `run:` blocks within GitHub Actions workflows (e.g., `dispatch-rebottle.yml`).
**Learning:** `github.event.inputs` values are user-controllable (via `workflow_dispatch`). Directly interpolating them in shell scripts (`run:`) allows an attacker to inject arbitrary shell commands.
**Prevention:** Always pass user-controllable inputs to shell scripts via environment variables (`env:` block) and access them using standard shell environment variable syntax (e.g., `$FORMULA`).
