## 2026-09-27 - Command Injection via GitHub Event Inputs in Workflows
**Vulnerability:** Untrusted user input (`github.event.inputs.*` and `github.event.sender.login`) was directly interpolated using `${{ }}` into bash `run:` scripts in GitHub Actions workflows (e.g., `dispatch-rebottle.yml`).
**Learning:** Direct string interpolation of context expressions into workflow shell steps allows attackers to execute arbitrary commands by submitting inputs with shell metacharacters (e.g., `"; command;"`).
**Prevention:** Always bind untrusted context data to environment variables using the `env:` block and reference those environment variables (e.g., `$FORMULA`) within the script execution context.
