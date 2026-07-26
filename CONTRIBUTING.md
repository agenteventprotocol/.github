# Contributing to AEP (org-wide default)

This file applies to any AEP-org repository without its own `CONTRIBUTING.md`.

- **Spec, schema, conformance, or docs changes** → the standard repository,
  [agent-event-protocol](https://github.com/agenteventprotocol/agent-event-protocol).
  AEP is spec-first: anything normative goes through the AEP proposal process
  (see its
  [GOVERNANCE.md](https://github.com/agenteventprotocol/agent-event-protocol/blob/main/GOVERNANCE.md)),
  and **a normative change lands with its conformance fixtures in the same
  change** — the fixtures are the arbiter.
- **Code changes** → the repository that owns the code:
  [reference](https://github.com/agenteventprotocol/reference) (relay, CLI, adapters,
  bridges, MCP server, demo),
  [mission-control](https://github.com/agenteventprotocol/mission-control) (the fleet
  console),
  [typescript-sdk](https://github.com/agenteventprotocol/typescript-sdk), or
  [python-sdk](https://github.com/agenteventprotocol/python-sdk). Each repo's README
  documents its verification commands; CI must be green.

The full contribution guide (ground rules, dev setup, AEP proposal template)
is the standard repo's
[CONTRIBUTING.md](https://github.com/agenteventprotocol/agent-event-protocol/blob/main/CONTRIBUTING.md).
