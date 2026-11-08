## 2024-05-24 - Command Injection in GitHub Actions
**Vulnerability:** Command injection via direct string interpolation of user-controlled inputs (`${{ github.event.inputs.pull_request }}` and `${{ github.event.inputs.args }}`) within `run:` blocks in GitHub Actions workflows.
**Learning:** GitHub Actions string interpolation happens before the shell script is generated, allowing a malicious actor to break out of the command and execute arbitrary code on the CI runner if they control the input payload.
**Prevention:** Always pass user-controlled inputs to shell scripts using environment variables (the `env:` block) and reference them safely within the script (e.g., `"$MY_VAR"` or `$MY_ARGS` for word splitting), preventing the shell from evaluating them as code.
