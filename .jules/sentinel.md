## 2024-05-23 - Command Injection in GitHub Actions Workflows
**Vulnerability:** Command injection vulnerability in multiple GitHub Actions workflow files due to direct interpolation of `${{ github.event.inputs.* }}` into shell `run:` scripts.
**Learning:** GitHub Actions directly substitutes `${{ }}` expressions into the generated shell script before execution. If the user input contains shell metacharacters (e.g., `;`, `|`, `$()`, `` ` ``), it allows executing arbitrary commands on the runner.
**Prevention:** To prevent command injection in GitHub Actions workflows, always pass user-controlled inputs (e.g., `github.event.inputs`) into shell scripts using environment variables (`env:` block) instead of direct `${{ }}` string interpolation within `run:` blocks.
