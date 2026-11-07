## 2024-05-31 - GitHub Actions Command Injection Risk
**Vulnerability:** Command injection in GitHub Actions workflows due to unsafe interpolation of `github.event.inputs` into bash scripts (e.g., `${{ github.event.inputs.formula }}`).
**Learning:** Using direct string interpolation like `${{ }}` in the `run:` block of a workflow file evaluates the input and treats it as part of the script syntax, exposing the runner to command injection attacks.
**Prevention:** Pass user inputs as environment variables (using `env:`) and reference them safely via `$VARIABLE` or `"$VARIABLE"` within the script to ensure they are treated as strings.
## 2024-05-31 - GitHub Actions Missing Action Version
**Vulnerability:** Workflows are referencing a non-existent version of a remote action (`homebrew/actions@master`), causing total failure of automation, which represents an Availability impact.
**Learning:** Default branches can be renamed on upstream repositories, breaking dependents if they are hardcoded to the branch name instead of a semantic version or commit SHA.
**Prevention:** Avoid relying on mutable branch names (like `master` or `main`) and instead pin to a specific release tag or commit hash to ensure deterministic pipeline execution.
