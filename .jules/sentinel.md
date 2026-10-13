## 2024-10-13 - GitHub Actions Script Injection
**Vulnerability:** Direct interpolation of user-controlled input (`${{ github.event.inputs.* }}`) into bash scripts within GitHub Actions `run:` blocks.
**Learning:** This occurs because GitHub evaluates `${{ }}` expressions before the runner executes the bash script. An attacker could inject malicious bash commands via workflow dispatch inputs.
**Prevention:** Pass GitHub contexts (like `github.event.inputs`) to shell scripts via environment variables (`env:` block) and reference the variables safely in the bash script (e.g., `"$HOMEBREW_FORMULA"`).
