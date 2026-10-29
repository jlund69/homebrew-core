## 2024-05-24 - Command Injection Risk in GitHub Actions Workflows
**Vulnerability:** Shell script interpolation (`${{ github.event.inputs... }}`) of user-provided inputs directly inside `run:` blocks in `.github/workflows/dispatch-rebottle.yml`, `.github/workflows/dispatch-build-bottle.yml`, and `.github/workflows/publish-commit-bottles.yml` workflows.
**Learning:** This exposes the CI environment to command injection attacks because malicious inputs (e.g., `formula: "foo; rm -rf /"`) will be expanded as text before the shell parses the command.
**Prevention:** Instead of string interpolation (`${{ ... }}`) in run scripts for untrusted input, bind variables in the `env:` block and read them as environment variables (e.g., `$FORMULA`) inside the script.
