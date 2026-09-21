## 2024-05-24 - GitHub Actions Command Injection via User Inputs
**Vulnerability:** Command injection vulnerability in multiple GitHub Actions workflows due to unsafe string interpolation of `${{ github.event.inputs.* }}` and `${{ github.event.sender.login }}` directly within `run:` blocks.
**Learning:** In GitHub Actions, expressions like `${{ }}` are evaluated before the shell script runs. This allows an attacker to inject arbitrary shell commands if the input contains shell metacharacters (e.g., `;`, `|`, `$()`).
**Prevention:** Always map user-controlled inputs to environment variables via the `env:` block and access them safely within the shell script using `$ENV_VAR` or `${ENV_VAR}`. Avoid direct interpolation of untrusted data in `run:` blocks.
