# 0001: Off-the-shelf hardware only - no custom PCB or CAD

**Status:** Accepted

## Context
Designing our own circuit board or 3D-modeling our own parts both take a
lot of time: drawing the circuit, laying it out, ordering it, waiting for
it to arrive, fixing what does not work. For a final-year project with a
fixed deadline and two of us, that time is better spent on the parts that
are actually new - the autonomy software, and making sure the whole thing
flies reliably.

## Decision
Build the drone entirely from bought parts - flight controller, ESCs,
motors, frame, battery, sensors. We are not designing or ordering a custom
circuit board. We are not designing or printing custom structural parts.
Any 3D-printed brackets we use are simple, off-the-shelf, or lightly
adjusted designs, not from-scratch engineering.

## Consequences
- The hardware work becomes about picking the right parts and wiring them
  together well, not designing them. components/ and
  2-architecture/interface-control-documents.md matter more because of this.
- 4-integration-design/ replaces what would otherwise be a circuit-design
  stage. It is about wiring, mounting, and settings instead.
- We get to a flying drone faster, but have less custom hardware
  engineering to show. Worth saying plainly in the report so it reads as a
  choice, not a gap.
- If we ever hit something no bought part can do, revisit this decision
  instead of quietly working around it.
