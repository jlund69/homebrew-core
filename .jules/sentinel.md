## 2023-10-27 - Command Injection in Workflows
**Vulnerability:** Direct string interpolation of `${{ github.event.inputs.* }}` inside bash `run:` blocks in `.github/workflows/`.
**Learning:** GitHub Actions string substitution happens before bash parsing, allowing users to inject arbitrary shell commands if inputs contain quotes or semicolons.
**Prevention:** Always pass user-controlled inputs to shell scripts using the `env:` block, and access them as `$ENV_VAR` in the script.
