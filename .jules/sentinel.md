## 2024-05-24 - GitHub Actions Command Injection
**Vulnerability:** Command injection via direct string interpolation of github.event.inputs in run blocks
**Learning:** GitHub Actions templating (${{ }}) happens before the shell script runs, meaning untrusted input can break out of quotes and execute arbitrary shell commands
**Prevention:** Pass all untrusted inputs as environment variables (env:) and reference them in the shell script using standard shell variables (e.g., $VARIABLE)
