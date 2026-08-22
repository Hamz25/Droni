# Hardware Docs

This is where we write down the plan and the decisions for the physical drone - not the parts themselves (those live in `Body/`), but the thinking behind them. Read **[methodology.md](methodology.md)** once for the why. This page is the quick index of what's where.

## What every file is for

| File | What it's for |
|---|---|
| `components/flight-controllers.md` | Comparing flight controller options before buying |
| `components/motors-and-escs.md` | Comparing motor and ESC options |
| `components/batteries.md` | Comparing battery options |
| `components/sensors-and-payload.md` | Comparing sensors / extra equipment |
| `components/frame-and-propellers.md` | Comparing frame and propeller options |
| `0-framing/vision-and-scope.md` | What this project is and isn't, written first |
| `0-framing/roadmap.md` | Rough timeline / milestones |
| `1-requirements/mission-requirements.md` | What the drone must do - range, endurance, payload |
| `1-requirements/functional-requirements.md` | Specific must-do statements |
| `1-requirements/nfr.md` | How well it must do it - weight, wind, cost, range |
| `2-architecture/adr/0001-off-the-shelf-hardware.md` | Why we're not building custom boards or parts |
| `2-architecture/system-block-diagram.md` | Big-picture map of the parts and how they connect |
| `2-architecture/interface-control-documents.md` | Exact wiring / voltage / plug for each connection |
| `3-high-level-design/power-budget.md` | Does the battery supply enough power for everything |
| `3-high-level-design/mechanical-layout.md` | Rough placement of parts, plus a running weight total |
| `4-integration-design/wiring-diagram.md` | The actual pin-by-pin wiring plan |
| `4-integration-design/mounting-plan.md` | How parts are physically attached |
| `4-integration-design/configuration.md` | Flight-controller software settings |
| `4-integration-design/hardware-software-interface.md` | The agreement between hardware and `Brain/` |
| `cross-cutting/safety-and-compliance/regulatory-requirements.md` | Rules we have to follow |
| `cross-cutting/safety-and-compliance/failure-modes-and-effects.md` | What could break, and what we'd do about it |
| `cross-cutting/safety-and-compliance/safety-case.md` | Safety features actually built and tested |
| `cross-cutting/traceability/requirements-traceability-matrix.md` | Checklist linking requirements to tests |
| `cross-cutting/verification/test-and-verification-plan.md` | How we plan to test, decided early |
| `5-integration-and-verification/bring-up-procedures.md` | Steps for powering on safely |
| `5-integration-and-verification/bench-test-plan.md` | Tests done without flying |
| `5-integration-and-verification/flight-test-plan.md` | The real flight test steps |
| `5-integration-and-verification/test-reports/` | Dated write-ups of each real test |
| `6-assembly/bill-of-materials.md` | Final parts list, with prices and links |
| `6-assembly/assembly-instructions.md` | Step-by-step build guide |
| `6-assembly/maintenance-and-logistics.md` | Keeping it working - spares, pre-flight checks |

## Status

Nothing here is built yet. Check things off as you go:

- [ ] `0-framing/vision-and-scope.md`
- [ ] `1-requirements/`
- [ ] `2-architecture/` (first real decisions)
- [ ] `3-high-level-design/`
- [ ] `4-integration-design/`
- [ ] `cross-cutting/safety-and-compliance/` (at least the failure list)
- [ ] `5-integration-and-verification/` (bring-up)
- [ ] `6-assembly/bill-of-materials.md`

## A couple of habits worth keeping

- Picked a part or made a real decision? Write a short ADR in `2-architecture/adr/`. Doesn't need to be long - what we decided, and why.
- About to fly for real? Check `cross-cutting/safety-and-compliance/failure-modes-and-effects.md` first, not after.
