## 2024-10-24 - Prevent Command Injection in GitHub Actions Workflows
**Vulnerability:** String interpolation (`${{ }}`) inside GitHub Actions `run:` blocks was used to pass user-controlled inputs (e.g., `github.event.inputs.*`) into bash scripts. This exposes the workflows to command injection if an attacker includes bash commands or malicious variables in the input.
**Learning:** GitHub Actions resolves `${{ }}` blocks before creating the shell script, so unescaped bash control characters entered into these blocks become part of the bash execution syntax rather than string literals.
**Prevention:** Always pass user-controlled inputs via environment variables using the `env:` block. Within the `run:` block, reference the variables using bash syntax (e.g., `$INPUT_VAR`).
