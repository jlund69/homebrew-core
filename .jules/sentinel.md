## 2024-10-07 - Prevent command injection in GitHub Actions
**Vulnerability:** Command injection vulnerability via `github.event.inputs` being evaluated directly in bash `run:` scripts within `.github/workflows/publish-commit-bottles.yml` and `.github/workflows/dispatch-rebottle.yml`.
**Learning:** Evaluating untrusted inputs directly using string interpolation (`${{ ... }}`) in workflow scripts allows execution of arbitrary code if a malicious user crafts malicious inputs.
**Prevention:** Pass all `github.event.inputs` to the `run:` environment using an `env:` block and access them safely as shell environment variables (e.g., `$HOMEBREW_GITHUB_EVENT_INPUTS_ARGS`).
