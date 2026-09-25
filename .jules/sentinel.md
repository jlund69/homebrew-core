## 2024-05-20 - Command Injection in GitHub Actions
**Vulnerability:** Command injection vulnerability in GitHub Action workflows due to direct string interpolation of `${{ github.event.inputs.* }}` inside `run:` blocks.
**Learning:** GitHub Actions string interpolation happens before the bash script is executed. If a user provides an input containing shell metacharacters (like `"; ls -la"`), it can break out of the intended command and execute arbitrary code on the runner.
**Prevention:** To prevent command injection, user-controlled inputs should be passed into shell scripts via environment variables (`env:` block) and referenced as `$ENV_VAR` or `"$ENV_VAR"` inside the `run:` script.
