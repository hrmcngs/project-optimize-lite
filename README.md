# Project Optimize Lite

An agent skill for cleaning up a project and reducing program size, memory use, or lag while preserving functionality and security.

## Usage

Ask your agent to read `skills/project-optimize-lite/SKILL.md`, then specify the target:

> Use project-optimize-lite to streamline /path/to/project. Remove demonstrably unused files and dependencies, investigate lag, implement small improvements, and verify functionality, security, and before/after results.

> Measure why this application's screen transitions are slow and fix the bottleneck without weakening security.

The workflow checks references and dynamic usage before deleting files, measures actual bottlenecks, and distinguishes disk cleanup from runtime speedups. It preserves authentication, authorization, validation, and other protective controls. Changes to sensitive paths require appropriate positive and negative regression checks, including tenant and cache isolation when relevant. Known security regressions must be corrected or reverted.

This is an instruction-based skill, not a standalone executable. Creating this folder does not install it automatically. Copy `skills/project-optimize-lite` into your agent's skill directory, or ask the agent to read its path directly.

## Files

- `skills/project-optimize-lite/SKILL.md`: Inspection, cleanup, optimization, security, and verification workflow.
- `README.md`: Usage instructions.
- `LICENSE`: Upstream MIT license and copyright notice.

No runtime dependencies, helper executables, or background processes are included. Results depend on the reviewed scope and available checks; this skill does not guarantee the absence of vulnerabilities.

## Attribution

Informed by the evidence-based verification, false-positive rejection, and explicit uncertainty principles in [Cloudflare's security-audit-skill](https://github.com/cloudflare/security-audit-skill), reference commit `c1c8a8c1471069fb0e188eeaff69b8e8db6564a8`.

This adaptation focuses on project cleanup and performance improvements. It does not implement the upstream complete audit workflow or independent verification guarantees. The original MIT license is retained.
