## 2025-02-28 - GitHub Actions Command Injection
**Vulnerability:** Command injection in GitHub Actions workflow `dispatch-rebottle.yml` where user-controlled input (`${{ github.event.inputs.* }}`) was directly interpolated into `run:` scripts.
**Learning:** Direct string interpolation of untrusted input in shell scripts (like inside GitHub Actions `run:` blocks) allows an attacker to inject arbitrary commands, executing code within the runner's environment.
**Prevention:** Always pass user-controlled inputs into shell scripts using environment variables (`env:` block) and reference them securely (e.g., `"$FORMULA"`) instead of direct `${{ }}` interpolation.
