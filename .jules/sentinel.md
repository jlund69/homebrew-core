## 2024-11-06 - Prevent GitHub Actions Command Injection
**Vulnerability:** User-controlled inputs via `github.event.inputs` were directly interpolated into bash scripts using `${{ ... }}` syntax within `run:` blocks, making the workflows vulnerable to command injection.
**Learning:** Directly embedding untrusted input into scripts allows attackers to close the quotes and execute arbitrary commands.
**Prevention:** Always pass user-controlled inputs via environment variables (in the `env:` block) and reference those variables in bash scripts as standard environment variables (e.g. `$MY_VAR`).
