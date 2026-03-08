# Job Search OS

A multi-agent system that automates the operational overhead of a job search — so you spend time on conversations and interviews, not tracking and research.

---

## Why I Built This

Managing a job search at scale means constantly context-switching between researching companies, drafting personalized outreach, tracking pipeline status, and prepping for interviews. Each task is repetitive and time-consuming individually. Together they create enough friction that things fall through the cracks.

This system delegates the operational work to agents, each specialized for a specific task, coordinating to keep the pipeline moving.

---

## What It Does

| Agent | Responsibility |
|-------|---------------|
| **Research Agent** | Given a company name, builds a brief: product, AI stack, recent news, open roles, relevant people |
| **Outreach Agent** | Drafts personalized networking messages based on research + recipient profile |
| **Pipeline Agent** | Tracks application status, flags stale processes, surfaces what needs follow-up |
| **Interview Prep Agent** | Given a company + role, generates likely questions and pulls relevant stories |
| **Eval Agent** | Reviews interview answers (via transcript), scores them, identifies gaps |

---

## Architecture Decisions

**Why multi-agent instead of one agent?**
Each task has different latency requirements and failure modes. Research is slow and I/O-bound — it can run in parallel for 5 companies simultaneously. Outreach drafting is fast but quality-sensitive and needs human approval before sending. Separating them means failures in research don't block outreach, and I can evaluate each agent independently.

**Why human-in-the-loop on outreach?**
Personalized messages sent without review would damage relationships if wrong. The agent drafts, I approve, then it sends. Guardrail by design, not as an afterthought.

**Memory strategy**
Pipeline state is persisted to a local JSON store between sessions. Research results are cached to avoid redundant API calls. Interview transcripts are stored and indexed for retrieval when prepping for follow-up rounds.

---

## Project Structure

```
job-search-agent/
├── src/
│   ├── agents/          # Individual agent implementations
│   ├── tools/           # Tool definitions (web search, file I/O, etc.)
│   ├── memory/          # State persistence layer
│   └── orchestrator.py  # Coordinates agents and manages workflow
├── evals/
│   ├── test_cases/      # Input/output pairs for each agent
│   └── results/         # Eval run outputs with pass rates
├── docs/
│   └── architecture.md  # Detailed design decisions
├── .env.example         # Required environment variables
└── requirements.txt
```

---

## Concepts Demonstrated

- Agentic loop with tool calling
- Multi-agent orchestration (parallel + sequential)
- Persistent memory across sessions
- Human-in-the-loop for high-stakes actions
- Evaluation framework for non-deterministic outputs

---

## Status

**In progress.** Building agent by agent, starting with Research. Each milestone is committed as it works — evals first, then implementation.

---

## What I'd Do Differently at Scale

*(This section gets updated as I hit real failure modes during building)*
