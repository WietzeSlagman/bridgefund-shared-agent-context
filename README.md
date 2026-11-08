# Shared Agent Context

This repository contains reusable instructions for agents working across projects.
`AGENTS.md` holds shared rules, and `workflows/planning.md` describes a reusable
planning procedure. Each consuming repository retains its own project-specific
rules, agent definitions, and verification requirements.

No shared skill is defined yet. Add one when a concrete reusable workflow warrants
it, rather than assuming every project uses the same tools or technology.

## Consume From Another Repository

Add this repository as a submodule from the consuming repository's root:

```sh
git submodule add git@github.com:WietzeSlagman/bridgefund-shared-agent-context.git shared/agent-context
```

The consumer's `AGENTS.md` should explicitly instruct agents to read
`shared/agent-context/AGENTS.md`, in addition to its own project instructions.
For example, a frontend repository can use the same submodule while maintaining
its own accessibility, browser testing, and frontend-specific rules locally.

To use the shared planning workflow in OpenCode, keep a project-specific planning
agent in `.opencode/agent/` and instruct it to read both
`shared/agent-context/AGENTS.md` and `shared/agent-context/workflows/planning.md`.
The local agent supplies project-specific sources, constraints, and artifact
formats. The workflow file is an instruction document, not a separately discovered
OpenCode agent or skill. Restart OpenCode after changing the agent definition and
verify in a fresh session that it reads and applies both shared and local context.

Reviewers and CI need access to this private repository and working Git credentials.
For a fresh clone, initialize submodules:

```sh
git clone --recurse-submodules <consumer-repository-url>
```

For an existing clone, run `git submodule update --init --recursive` from its root.
The consumer records a specific shared-context commit; update and review that
pointer deliberately when adopting shared changes. Commit the consumer's
`.gitmodules` and submodule pointer as part of its own integration.

If shared OpenCode skills are added later, configure each consumer to discover
their directory using OpenCode's `skills.paths` setting and document the tested
configuration. Restart OpenCode after changing its configuration or skills.

Verify clone access, instruction loading, and any skill configuration when setting
up a consuming repository.
