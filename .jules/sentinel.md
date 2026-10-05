## 2024-05-15 - GitHub Actions Command Injection Prevention
**Vulnerability:** Command injection via direct string interpolation in `run:` blocks (e.g., `${{github.event.inputs.formula}}`).
**Learning:** GitHub Actions interpolates `${{ }}` expressions before running the script. If a user inputs something like `formula; ls -la;`, the generated script directly executes it, leading to a command injection vulnerability.
**Prevention:** Always pass user-controlled input (like `github.event.inputs`) into scripts by mapping them to environment variables in the `env:` block, and then referencing the environment variable inside the `run:` block (e.g., `"$FORMULA"`).
