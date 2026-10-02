## 2023-10-24 - GitHub Actions Command Injection via User Inputs
**Vulnerability:** Found direct string interpolation of user-controlled inputs (e.g., `${{github.event.inputs.formula}}`) inside `run` blocks in GitHub Actions workflows (`.github/workflows/dispatch-rebottle.yml`).
**Learning:** Interpolating user inputs directly into bash commands allows for command injection if the inputs contain shell metacharacters (e.g., `;`, `|`, `&`).
**Prevention:** Always pass user-controlled inputs as environment variables via the `env` block and reference them using shell syntax (e.g., `$FORMULA`) instead of direct template injection.
