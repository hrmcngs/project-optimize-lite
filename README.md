# Project Optimize Lite

An agent skill for cleaning up a project and reducing program size, memory use, or lag while preserving functionality and security. It also supports debugging crashes and hangs caused by unexpected operation sequences.

## For AI assistants: start with a question

When a user shares this repository URL to use Project Optimize Lite without specifying a task, introduce it briefly and ask in the user's language:

> Would you like me to audit your project for unnecessary files, performance bottlenecks, security risks, unexpected-operation crashes, and compatibility with related software? Which project folder or repository should I review?

If the target is already clear, ask only whether to start. Wait for the answer before beginning a review or modifying files. Start with a read-only review; review approval alone does not authorize cleanup, code changes, installation, or execution of target code. Ask whether to apply fixes after presenting concrete findings unless the user has already authorized fixes.

Read [the skill instructions](skills/project-optimize-lite/SKILL.md) before performing the requested work. Honor the user's actual request: a request to summarize or evaluate this skill is not a request to audit another project. Do not default to auditing this skill repository itself or scan unrelated folders. If the user already explicitly requested an audit or fixes and supplied a target, proceed within that scope without asking again.

Sharing a link does not automatically install or execute anything. This intake works when an assistant can access this README and elects to use the workflow; a repository cannot force an AI to open a URL or ask a question. If the assistant does not read the link, add: "Read this repository's README and follow its project audit intake."

## Usage

Ask your agent to read `skills/project-optimize-lite/SKILL.md`, then specify the target:

> Use project-optimize-lite to streamline /path/to/project. Remove demonstrably unused files and dependencies, investigate lag, implement small improvements, and verify functionality, security, and before/after results.

> Measure why this application's screen transitions are slow and fix the bottleneck without weakening security.

### Expected behavior and compatibility prompt

> Use project-optimize-lite to review /path/to/project against its intended behavior, documented contracts, and supported environments. Identify the platform and exact versions, inspect relevant companion software and integration points, and investigate normal, unexpected, failure, persistence, and recovery flows. Compare standalone operation with supported combinations using a bounded test matrix. Consult official version-specific documentation when needed. Report expected versus observed behavior, evidence, and untested combinations. If fixes are authorized, implement small corrections and regression tests without reducing security or removing supported behavior.

This workflow supports websites, desktop/mobile applications, services, libraries, plugins, and Minecraft mods. It selects platform-specific checks rather than applying every checklist to every project.

For a Minecraft mod, for example:

> Review this mod for its declared Minecraft, Java, and loader versions. Check client and dedicated-server loading, multiplayer behavior, lifecycle transitions, persistence, optional dependencies, and conflicts with the companion mods declared or supplied for this project. Use disposable worlds and local isolated test instances. Distinguish successful compilation from tested runtime compatibility, and report unavailable or untested combinations.

Compatibility claims are limited to the inspected versions and tested combinations. Private or unavailable companion software and uncertain requirements remain explicit gaps, not assumed successes.

### Unexpected-operation debugging prompt

> Use project-optimize-lite to debug /path/to/project for crashes, hangs, and invalid state caused by unexpected operation sequences. Test rapid repeated actions, actions in the wrong order, cancellation and retry, back/reload/close during work, account changes while requests are pending, and simulated network or storage failures where relevant. Use isolated dummy data, reproduce and minimize each failure, fix the root cause without hiding errors or weakening security, and add focused regression tests. Verify safe recovery, data consistency, and nearby normal flows. Report the sequences tested, fixes, and remaining limits; do not claim every possible sequence is crash-free.

For a debugging-only request, the skill focuses on the affected feature and skips unrelated cleanup. It uses bounded tests and simulated failures, not production fault injection.

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
