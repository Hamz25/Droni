# How We Work on the Software

This is the plan for how the AI/autonomy code (`Brain/`) gets built. Read this once, then use the folders as you go. Every file in the tree explains itself at the top, and README.md has the quick index of what's where.

## The big idea

Figure out WHAT the software needs to do before deciding HOW to build it. Jumping straight to code, before writing down what it actually needs to handle, is how you end up rewriting things twice.

## The order, and why

1. **0-framing** - What is this software for, written first.
2. **1-problem-space** - What must it do, in plain words, before any code.
3. **2-architecture** - The big decisions: how the software splits into major pieces, and why. Every real decision gets a short written note (an ADR).
4. **3-high-level-design** - The main objects in the code and how they relate.
5. **4-detailed-design** - The exact behaviour: what happens, step by step, in what order, for each scenario.
6. **5-delivery** - Actually building it, plus how it gets tested and watched once running.

Three things run alongside ALL of these, the whole time, not just at the end:

- **Security** (`cross-cutting/security/`) - how someone could mess with it, and what we're doing about it.
- **Keeping track** (`cross-cutting/traceability/`) - does every requirement actually get built and tested?
- **Test planning** (`cross-cutting/testing/`) - decide how you'll test early, even though most testing happens later.

## One thing worth understanding: it's the same idea, described more precisely each time

Take one thing in the software - say, a "Mission." You describe it slightly differently at each stage, more precisely each time:

- In the problem space, it's just a definition: a Mission is a sequence of waypoints the drone flies through.
- In the high-level design, it's a class: Mission has a list of Waypoints and a status.
- In detailed design, it's a set of stages: Planned, Active, Completed, Cancelled, and exactly what causes each switch.
- In the data model, it's a table: `mission(id, status, created_at, ...)`.

Nothing new gets invented at each step - the later steps just make the earlier ones more exact. That's why the order matters: draw the detailed behaviour before the class exists, and you're describing something that isn't fully defined yet.

## A simple rule for splitting code into pieces

When deciding where one module ends and another begins, use one rule: things that change for the same reason go together, things that change for different reasons go apart. The code that talks to the database should be separate from the code that decides flight logic, because you'll change them for completely different reasons.

A quick check for any file or module: can you explain what it does in one sentence? Can you change what's inside it without touching five other files? Can you understand it without opening everything it's connected to? If not, the boundary is probably in the wrong place - move things around until the answer is yes.

## If you want this to sound official for the report

This isn't a made-up process - it follows the same order used across real software engineering standards:

- **SWEBOK v4** - the IEEE's guide to how software engineering actually works, covering requirements, design, testing, and more.
- **ISO/IEC/IEEE 29148:2018** - the standard specifically about writing good requirements.
- **ISO/IEC/IEEE 29119-3:2021** - the standard for test documentation.
- **Domain-Driven Design** (Eric Evans) - where the "plain words first" idea for the domain model comes from.
- **The C4 model** (Simon Brown) - the diagram style used in `2-architecture/`.
- **Architecture Decision Records** (Michael Nygard) - the short why-we-decided-this format used for ADRs.
