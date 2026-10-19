## 2024-05-16 - Prevent Command Injection in GitHub Actions
**Vulnerability:** Direct string interpolation of `github.event.inputs` into bash scripts (e.g. `run:` blocks). This exposes workflows to command injection.
**Learning:** `github.event.inputs` can contain arbitrary strings provided by the user triggering the workflow. When these are directly injected using `${{ }}` into a `run:` script block, a malicious user can escape the context and execute arbitrary code on the GitHub runner, potentially exfiltrating secrets.
**Prevention:** Pass user-controlled data into `run:` scripts via environment variables (`env:` block) and reference them as bash variables (e.g., `"$MY_ENV_VAR"`).
