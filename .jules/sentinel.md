## 2024-10-18 - GitHub Actions Command Injection via string interpolation
**Vulnerability:** Direct string interpolation of `${{github.event.inputs}}` inside `run` blocks in GitHub Actions workflows.
**Learning:** Using `${{ }}` syntax in a `run` block evaluates the variables as strings *before* executing the shell script, allowing for arbitrary shell command injection if the inputs are user-controllable.
**Prevention:** Pass user inputs using environment variables (e.g. `env: FORMULA: ${{github.event.inputs.formula}}`) and reference them in the script as `$FORMULA` to rely on shell variable protections instead of string interpolation.
