## 2024-05-31 - GitHub Actions Command Injection Risk
**Vulnerability:** Command injection in GitHub Actions workflows due to unsafe interpolation of `github.event.inputs` into bash scripts (e.g., `${{ github.event.inputs.formula }}`).
**Learning:** Using direct string interpolation like `${{ }}` in the `run:` block of a workflow file evaluates the input and treats it as part of the script syntax, exposing the runner to command injection attacks.
**Prevention:** Pass user inputs as environment variables (using `env:`) and reference them safely via `$VARIABLE` or `"$VARIABLE"` within the script to ensure they are treated as strings.
