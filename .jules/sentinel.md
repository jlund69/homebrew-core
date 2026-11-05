## 2024-05-18 - Command Injection via GitHub Actions inputs
**Vulnerability:** GitHub Action inputs interpolated directly into inline shell scripts using `${{ github.event.inputs... }}` can result in command injection.
**Learning:** GitHub Actions performs macro substitution on these values before executing the script, meaning user input can prematurely close quotes or insert operators like `;` to execute arbitrary commands.
**Prevention:** Pass GitHub action inputs into the execution environment as variables via the `env:` block.
