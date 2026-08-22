# Software Docs

This is where we write down the plan and the decisions behind `Brain/` - not the code itself, but the thinking behind it. Read **[methodology.md](methodology.md)** once for the why. This page is the quick index of what's where.

## What every file is for

| File | What it's for |
|---|---|
| `0-framing/vision-and-scope.md` | What the software must do, written first |
| `0-framing/roadmap.md` | Rough timeline / milestones |
| `1-problem-space/domain-model.md` | Plain-word definitions of the important "things" |
| `1-problem-space/use-cases.md` | What the software must do, from the outside |
| `1-problem-space/nfr.md` | How fast / reliable it must be |
| `1-problem-space/requirements-spec.md` | The full numbered requirements list |
| `1-problem-space/edge-case-research.md` | Weird situations to plan for ahead of time |
| `2-architecture/adr/0001-example-decision.md` | Template for recording a real decision |
| `2-architecture/c4-context.md` | The software as one box, and what it talks to |
| `2-architecture/c4-container.md` | The big pieces inside the software |
| `3-high-level-design/aggregate-model.md` | Main objects/classes and how they relate |
| `3-high-level-design/component-diagram.md` | How containers break into smaller pieces |
| `4-detailed-design/lifecycles.md` | Stages something goes through, e.g. a Mission |
| `4-detailed-design/sequence-flows.md` | Step-by-step for one specific scenario |
| `4-detailed-design/erd.md` | What data gets stored and how it connects |
| `4-detailed-design/api-contract.md` | The exact interface other code calls into |
| `cross-cutting/security/threat-model.md` | How someone could mess with it, and the fix |
| `cross-cutting/traceability/rtm.md` | Checklist linking requirements to tests |
| `cross-cutting/testing/test-strategy.md` | How we plan to test, decided early |
| `5-delivery/build-plan.md` | The order we're building things in |
| `5-delivery/ci-cd-and-ops.md` | Automatic checks, and keeping an eye on it once running |

## Status

Nothing here is built yet. Check things off as you go:

- [ ] `0-framing/vision-and-scope.md`
- [ ] `1-problem-space/`
- [ ] `2-architecture/` (first real decisions)
- [ ] `3-high-level-design/`
- [ ] `4-detailed-design/`
- [ ] `cross-cutting/` (at least a first pass on security)
- [ ] `5-delivery/`

## A couple of habits worth keeping

- Made a real architectural decision? Write a short ADR in `2-architecture/adr/`. Doesn't need to be long - what we decided, and why.
- Added a requirement? Add it to `1-problem-space/requirements-spec.md`, then link it in `cross-cutting/traceability/rtm.md` once it's built and tested.
