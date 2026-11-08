# Shared Agent Instructions

Apply these instructions alongside the consuming repository's instructions.
Project-specific instructions provide the context and verification requirements
for that project. Surface conflicts instead of silently choosing an interpretation.

- Inspect relevant requirements, existing code, tests, and configuration before
  making assumptions or changes.
- Preserve unrelated work and avoid destructive operations. Ask before actions
  that need explicit authorization, including commits and pushes.
- Prefer small, understandable changes and clarify consequential ambiguity.
- Verify changes with appropriate available checks. Report what was run, failures,
  skipped checks, and remaining uncertainty; never invent results.
- Treat secrets and persistent data carefully. Establish that database or other
  destructive test targets are isolated before running such checks.
- Record agent work according to the consuming project's journal conventions.
  Do not invent model usage, tools, time, or cost; report unknown details as such.
