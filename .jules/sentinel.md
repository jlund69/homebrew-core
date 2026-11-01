## 2025-01-01 - Prevent Command Injection in GitHub Actions
**Vulnerability:** Direct interpolation of user-controlled inputs (`${{ github.event.inputs... }}`) in shell scripts within GitHub Actions `run` blocks allows command injection.
**Learning:** GitHub Actions processes `${{ }}` substitutions before passing the script to the shell, making it vulnerable to injection if the input contains malicious shell commands or characters.
**Prevention:** Always assign user-controlled `github.event.inputs` to environment variables in an `env:` block and reference them using standard shell syntax (e.g., `$VAR`) inside the `run:` script.
