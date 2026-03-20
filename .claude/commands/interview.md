# /interview

Interview the user to gather everything needed to write INITIAL.md. Ask structured questions one at a time using AskUserQuestion. Then generate a completed INITIAL.md from the answers.

## Usage
```
/interview
```

## When to Use

`/interview` is the entry point for specifying any feature. Run it when you're ready to define what you're building.

**Not sure if you're ready? Run `/scope` first.** It asks 5 quick questions and tells you whether to go straight to `/interview` (simple path) or do brainstorm/research first (complicated path).

## Instructions for Claude

### Phase 1 — Read Context First

Before asking any questions:
1. Read `CLAUDE.md` — understand the project, stack, autonomy rules
2. Read `tasks/todo.md` — understand what's already built or in progress
3. Read `tasks/lessons.md` — understand known constraints and patterns
4. Scan `PRPs/` — understand what has already been specified and built
5. Scan `examples/` — understand what patterns exist

This prevents asking questions whose answers are already clear from context.

### Phase 2 — Interview (one question at a time)

**Routing signals — watch for these during the interview:**

If the user says "I'm not sure what I want" or "I haven't fully figured this out yet" or gives vague/contradictory answers to the core feature question:
→ **Pause the interview.** Say: "This signals you'd benefit from `/ce:brainstorm` first. It helps clarify what you're building before we specify it. Come back to `/interview` when you have a clearer direction."

If the user says "I'm not sure how this connects to what's already built" or "I don't know if there's already a table/service for this" or can't answer data/integration questions confidently:
→ **Pause the interview.** Say: "This signals you'd benefit from `/research [area]` first. It deep-reads the relevant codebase so you can answer these questions accurately. Come back to `/interview` after reviewing the research."

Do not force the interview to completion if the user is clearly missing context. The interview works best when the user has clarity — routing them to the right pre-step is more valuable than producing a vague INITIAL.md.



Ask questions using AskUserQuestion. One at a time. Wait for the answer before asking the next. Do not dump a list of questions.

Cover these areas in this order:

**1. The core feature**
- What are we building? Describe it in one sentence.
- What triggers it — user action, agent event, cron, API call?
- What does success look like? What's the output or state change?

**2. The user/agent experience**
- Who uses this or what system calls it?
- Walk me through the happy path step by step.
- What does the user/system see or receive at the end?

**3. Scope boundaries**
- What is explicitly NOT part of this feature?
- Is there a v2 version of this that we're deferring? What's deferred?

**4. Data and integrations**
- What data does this read from? (tables, files, external APIs)
- What data does this write or update?
- Does this touch the database schema, or work with existing tables?

**5. Edge cases and errors**
- What should happen if the input is missing or invalid?
- What's the failure mode? Should it fail silently, loudly, or retry?
- Any rate limits, cost implications, or performance constraints?

**6. Examples and patterns**
- Is there anything already built in this project that this should look like?
- Any external examples, open source repos, or docs that show the pattern?

**7. Constraints**
- Anything I must not do in this implementation?
- Any dependencies that need to exist first?
- Any decisions already made that I should not revisit?

Stop when you have enough to write a complete INITIAL.md. You do not need to ask every question if earlier answers make later ones obvious.

### Phase 3 — Generate INITIAL.md

Write the completed `INITIAL.md` using the answers. Follow the four-section format exactly:

```markdown
## FEATURE
[Detailed description based on answers — specific, not vague]

## EXAMPLES
[Specific references to examples/ folder or external patterns mentioned]

## DOCUMENTATION
[URLs from the answers, plus any obvious official docs for the stack]

## OTHER CONSIDERATIONS
[Constraints, edge cases, what not to build, dependencies — all from answers]
```

### Phase 4 — Confirm

After writing INITIAL.md, show a brief summary:
```
INITIAL.md is written. Here's what I captured:
- Feature: [one line]
- Triggers: [one line]
- Key constraints: [bullet list]
- Deferred to v2: [if anything]

Does this match what you had in mind, or anything to adjust before we generate the PRP?
```

Wait for confirmation before proceeding to `/generate-prp`.
