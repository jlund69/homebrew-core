## 2024-10-04 - Fix Command Injection in GitHub Actions
**Vulnerability:** Found direct interpolation of user-controlled variables (e.g. `${{github.event.inputs.formula}}`, `${{github.event.inputs.args}}`) inside `run:` scripts in GitHub Actions workflows. This can lead to command injection if a user submits malicious input.
**Learning:** GitHub Actions performs macro replacement on `${{ }}` blocks before running the shell script. Passing untrusted input this way allows escaping the script and executing arbitrary shell commands on the runner.
**Prevention:** Always pass user-controlled inputs via environment variables using the `env:` block in GitHub Actions and reference them as shell variables (e.g., `$FORMULA` or `${FORMULA}`) inside the `run:` script.
