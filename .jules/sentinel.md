## 2024-05-24 - Command Injection in GitHub Actions
**Vulnerability:** Found unescaped `${{ github.event.inputs.* }}` interpolation within `run:` script blocks in GitHub Actions workflows.
**Learning:** Using direct template substitution within shell contexts allows attackers to inject arbitrary bash commands if they can control the input string.
**Prevention:** Always pass user-controlled variables into the script via environment variables (e.g., `env:`) rather than inline substitution.
