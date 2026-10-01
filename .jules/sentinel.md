## 2025-02-18 - Prevent Command Injection in Github Actions workflows

**Vulnerability:** User controlled input like `github.event.inputs` can be used to inject arbitrary shell commands in Github Actions workflow files, since it was interpolated directly as string inside the `run:` block.
**Learning:** String interpolation of user input variables inside scripts run as `run:` action allows malicious shell command execution, because GitHub performs replacement before launching the script.
**Prevention:** Pass user input values into the shell environment using the `env:` block. This exposes inputs as variables which are accessed natively using `$var` inside the shell, mitigating command injection risks entirely.
