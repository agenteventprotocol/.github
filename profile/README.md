# AEP: Agent Event Protocol

**An open, vendor-neutral protocol for agent activity events and control.**

Any agent emits lifecycle, tool, progress, and **attention** events once —
over stdio, HTTP, SSE, or WebSocket — and any dashboard, bridge, logger, or
automation consumes them once, for every agent. AEP adds three things no
incumbent protocol carries: a routable attention lifecycle
(*agent-needs-a-human* as a first-class event), an acknowledged control
round-trip (approve/cancel/pause/answer from anywhere, audit-logged by
construction), and spec-guaranteed session replay (`(epoch, seq)` resume with
no gaps). CloudEvents and OpenTelemetry shops are served by normative
day-one bridges — you never choose between AEP and your existing pipeline.

> **Status: pre-release.** The v0.1 suite is pre-tag (three specifications
> Accepted, the rest Draft); nothing is published to any package registry
> yet. How versions work across the org — the protocol version, package
> SemVer, and the compatibility commitments between them — is stated in
> [VERSIONING](https://github.com/agenteventprotocol/agent-event-protocol/blob/main/VERSIONING.md).

## Repositories

| Repo | What |
|---|---|
| [agent-event-protocol](https://github.com/agenteventprotocol/agent-event-protocol) | **The standard**: specification suite, schema registry + codegen, conformance corpus (incl. a live endpoint checker), documentation, governance |
| [reference](https://github.com/agenteventprotocol/reference) | Runnable reference stack: relay, `aep` CLI with a durable capture sink and a shell control sender (`aep respond` / `aep cancel`), Claude Code + Codex + Gemini CLI + Qwen Code + OpenCode + Kilo Code + Cline + Hermes + Antigravity + pi + VS Code agent + Kimi Code adapters, CloudEvents/OTLP/SSE/AG-UI/ACP/OpenHands bridges (outbound projections + six inbound capture channels), MCP server, one-command demo, published benchmarks |
| [mission-control](https://github.com/agenteventprotocol/mission-control) | Mission Control — real-time fleet operator console: several relays in one window, live session lanes, attention inbox with tap-to-respond, run cancel with stream-settled outcomes, replay scrubber, causal graphs |
| [typescript-sdk](https://github.com/agenteventprotocol/typescript-sdk) | `@aep/sdk` — typed emit/consume/control helpers (Node ≥ 22, zero dependencies) |
| [python-sdk](https://github.com/agenteventprotocol/python-sdk) | `aep-sdk` — pydantic v2 models + emit/consume/control helpers, sync and asyncio (Python ≥ 3.10, fully typed) |
| [.github](https://github.com/agenteventprotocol/.github) | This repo: org profile + community health defaults |

## Where to start

- **Reading the standard** → the
  [spec suite](https://github.com/agenteventprotocol/agent-event-protocol/tree/main/spec)
  (start with AEP-0001, the envelope) and the
  [docs site](https://agenteventprotocol.io).
- **Seeing it run** → clone
  [reference](https://github.com/agenteventprotocol/reference) and run `./run-demo.sh`:
  one command boots the relay, streams three synthetic agents, and tails the
  unified event stream live in your terminal (Ctrl-C tears it all down).
- **Building an emitter or consumer** → the
  [TypeScript](https://github.com/agenteventprotocol/typescript-sdk) or
  [Python](https://github.com/agenteventprotocol/python-sdk) SDK.
- **Checking your own implementation** → bring your relay, collector, or
  control-capable agent and run the standard's
  [live conformance checker](https://github.com/agenteventprotocol/agent-event-protocol/tree/main/conformance)
  against it, or drive your consumer from the golden corpus
  ([the recipe](https://github.com/agenteventprotocol/agent-event-protocol/blob/main/docs/guides/write-a-consumer.md#certify-it)).
  Three conformance classes are self-certified across this org on every CI
  run: the reference relay as a collector (including its watch-only
  unauthenticated posture), a lingering demo agent as a control-capable
  target, and Mission Control as a consumer.

## Contributing

AEP is **spec-first**: normative changes go through the AEP proposal process
and land with conformance fixtures in the same change. Start with
[GOVERNANCE](https://github.com/agenteventprotocol/agent-event-protocol/blob/main/GOVERNANCE.md)
and
[CONTRIBUTING](https://github.com/agenteventprotocol/agent-event-protocol/blob/main/CONTRIBUTING.md)
in the standard repo.
