## 2024-05-24 - Prevent GitHub Actions Command Injection
**Vulnerability:** Command injection in GitHub Actions workflows via direct string interpolation of user-controlled inputs (e.g., `${{ github.event.inputs.* }}`) within `run:` blocks.
**Learning:** GitHub Actions replaces `${{ }}` expressions before running the script. An attacker can inject shell commands by submitting a crafted payload (e.g., `"; rm -rf /; echo "`) in an input field.
**Prevention:** Pass user-controlled inputs into the shell execution context as environment variables (using the `env:` block) and access them using shell variable syntax (e.g., `$MY_VAR`). This ensures the input is treated as data, not executable code.
