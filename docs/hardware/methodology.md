# How We Work on the Hardware

This is the plan for how we build the physical drone - the frame, motors, flight controller, wiring, all of it. Read this once, then use the folders as you go. Every file in the tree explains itself at the top, and README.md has the quick index of what's where.

## The big idea

Figure out WHAT the drone needs to do before deciding HOW. If you start by picking cool parts first, you often end up building the wrong thing, or realizing halfway through that a part doesn't actually fit what you need.

So: requirements first. Then the big picture - which parts, how they connect. Then the details - wiring, settings. Then building and testing.

## The order, and why

1. **0-framing** - Write down what this project actually is, before anything else.
2. **1-requirements** - What must the drone do, and how well? No parts picked yet.
3. **2-architecture** - Now the big decisions: which parts, roughly how they connect. Every real decision gets a short written note (an ADR), so we remember WHY later, not just WHAT.
4. **3-high-level-design** - A rough plan for power and where things physically sit.
5. **4-integration-design** - Since we're buying parts instead of designing our own, this step is the wiring plan, the mounting plan, and the flight-controller settings.
6. **5-integration-and-verification** - Power it on safely, test on the bench, then test flights, smallest first.
7. **6-assembly** - The final parts list and the build instructions.

Three things run alongside ALL of these steps, the whole time, not just at the end:

- **Safety** (`cross-cutting/safety-and-compliance/`) - what could go wrong, and what happens if it does.
- **Keeping track** (`cross-cutting/traceability/`) - does every requirement actually get built and tested?
- **Test planning** (`cross-cutting/verification/`) - decide how you'll test things early, even though the actual testing happens later.

## Why no custom circuit board or 3D-modeled parts

We decided to build this from bought parts only - see the first decision file, `2-architecture/adr/0001-off-the-shelf-hardware.md`, for the full reasoning. Short version: designing our own board or parts takes a lot of time we'd rather spend on the AI/autonomy side and on making sure everything actually works together. Picking the right parts and integrating them well is still real engineering - it's just a different kind of work than designing a board from scratch.

## One thing worth understanding: it's the same drone, described more precisely each time

Take one part of the drone - say, a single motor and its ESC (the small controller box that drives it). You describe it slightly differently at each stage, and each time you add more detail:

- In requirements, it's just a number: this motor needs to produce enough thrust to lift its share of the drone.
- In architecture, it's a box on a diagram: this motor connects to this ESC, which connects to the flight controller.
- In wiring, it's exact pins and wires: this wire, this connector, this pin.
- In the parts list, it's a real product: a specific motor and ESC, by name and price.
- In the test report, it's a measurement: we tested it, here's what it actually produced.

Nothing new gets invented at each step - the later steps just make the earlier ones more exact. That's the whole point of doing it in order: skip ahead and you end up guessing at things that weren't decided yet.

## A simple rule for splitting things into parts

When deciding where one subsystem ends and another begins, use one rule: things that change for the same reason go together, things that change for different reasons go apart. The power wiring and the frame are separate concerns, because you'll change them for completely different reasons - so keep the connection between them small and clearly written down (that's what the interface control documents are for).

A quick check for any subsystem: can you explain what it does in one sentence? Can you test it on its own, off the drone? Can you swap it out without having to redo everything else? If not, the boundary is probably in the wrong place.

## If you want this to sound official for the report

This isn't a made-up process - it follows the same order that real engineering standards use for building physical systems. Worth citing if your report wants to show the process is grounded in something real:

- **ISO/IEC/IEEE 15288:2023** - the standard for how systems, not just software, get built, step by step.
- **ISO/IEC/IEEE 29148:2018** - the standard specifically about writing good requirements.
- **NASA Systems Engineering Handbook** (NASA/SP-2016-6105) - a very readable, practical version of the same idea, built around something called the "Vee model."
- **IEC 60812:2018** - the standard behind the failure-modes exercise (`cross-cutting/safety-and-compliance/failure-modes-and-effects.md`).
- **ASTM F2910 / F3298** - design and construction standards specifically for small drones, from ASTM Committee F38. Worth double-checking the current wording on astm.org before citing - the exact scope of these has shifted across revisions.
- **14 CFR Part 89 (Remote ID) and Part 107** - the actual US flying rules, if relevant to where you're flying and testing.
