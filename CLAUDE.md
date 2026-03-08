# Job Search OS — CLAUDE.md

## Project
Interview intelligence dashboard + agentic layer for job search automation.
This is a real system used in a real job search — data is real, outputs matter.

**Frontend:** Next.js 14 (App Router), TypeScript, Supabase (Postgres), Vercel, Tailwind CSS
**Agents:** Python, Claude API (Anthropic SDK)
**Testing:** Jest (frontend), Pytest (agents)

---

## Commands
```bash
npm run dev          # start Next.js dev server
npm run build        # production build — must pass before committing
npm run lint         # ESLint — must pass before committing
npm run typecheck    # tsc --noEmit
npm test             # Jest test suite
cd agents && pytest  # Python agent tests
```

---

## Architecture
```
job-search-agent/
├── app/             # Next.js App Router — pages and layouts
├── components/      # React components
├── lib/             # Shared utilities, Supabase client, TypeScript types
├── agents/          # Python agent implementations
│   ├── research/    # Company research agent
│   ├── outreach/    # Outreach drafting agent
│   ├── prep/        # Interview prep agent
│   └── eval/        # Answer evaluation agent
├── supabase/        # Database migrations and schema
└── tasks/           # Task tracking — todo.md and lessons.md
```

---

## Workflow Orchestration

### Plan First
For any task touching more than one file or requiring architectural decisions:
1. Enter plan mode. Read relevant files. Write out the steps.
2. Check in before writing code.
3. Execute the approved plan. Flag any deviations before making them.

### Subagent Strategy
- Use subagents to keep the main context window clean
- Offload research, exploration, and parallel analysis to subagents
- One task per subagent — focused execution only

### Self-Improvement Loop
- After any correction: update `tasks/lessons.md` with the pattern
- Write rules that prevent the same mistake from happening again
- Review `tasks/lessons.md` at the start of each relevant session

### Verification Before Done
A task is ONLY complete when all three pass:
- `npm run build` exits 0
- `npm run lint` exits 0
- `npm run typecheck` exits 0

Report the output of all three before saying you're finished. Never mark a task complete without proving it works.

### Autonomous Bug Fixing
When given a bug report: diagnose from logs and errors, fix the root cause, verify the fix passes all checks. Do not ask for hand-holding on bugs.

---

## Task Management
For any task with more than 3 steps:
1. Write the plan to `tasks/todo.md` with checkable items
2. Check in before starting implementation
3. Mark items complete one at a time — never batch
4. Add a review section to `tasks/todo.md` when done
5. Update `tasks/lessons.md` after any correction

---

## Autonomy Boundary

**Auto-proceed:**
- Adding or editing components and pages
- Writing tests
- Fixing lint or type errors
- Refactoring within a single file

**Ask first:**
- Schema changes (Supabase migrations)
- Adding new dependencies
- Deleting files
- Any change touching more than 5 files
- Deploying to production

**Never:**
- Commit API keys, secrets, or credentials
- Push to main without explicit confirmation
- Modify Supabase migrations after they've run
- Touch files in personal-os-main

---

## Core Principles
- **Simplicity first.** Make every change as simple as possible. No over-engineering.
- **No laziness.** Find root causes. No temporary fixes. Senior engineer standards.
- **Minimal impact.** Only touch what the current task requires.
- **When corrected:** update `tasks/lessons.md` before continuing.
