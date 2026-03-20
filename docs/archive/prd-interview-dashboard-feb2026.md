# Interview Intelligence Dashboard — PRD

## 1. Problem & Why Now

I have a working interview prep system built on markdown files and Claude skills. It generates structured data after every interview — debriefs with scored dimensions, question patterns across companies, story deployment tracking, behavioral and technical gap rankings, and company-specific prep documents.

The system works. It's helped me across 10+ real interviews and I have confidence in the framework. But I've hit a ceiling.

**The core problem is that the data is relational but the storage is flat.** Stories connect to questions connect to companies connect to gaps. Those connections only exist in my head and in Claude re-reading everything each session.

Two specific pain points:

**Pre-interview prep is scattered.** When I have an interview coming up, I'm bouncing between 5-6 files — company overview, job description, prior debriefs, gap analysis, master playbook, story bank — trying to synthesize everything into "what do I need to nail in this specific interview." The information exists, it's just spread across too many places. I spend 10 minutes hunting through files in Obsidian and still don't feel fully prepared.

**Ongoing improvement has no feedback loop I can see.** Between interviews, there's no single view that says "here are the 3 things you're working on, here's your progress, here's what to practice this week." The gap analysis file tracks it, but debriefs generate insights that disappear into files. I can't see whether an issue I've been flagged on 6 times is getting better or worse. I can't see at a glance which stories are overused or which questions keep coming up.

**Why now:** The system got me this far but it's plateauing. The data is there, the framework is there, but the format is limiting how much value I can extract. I'm not getting the compounding benefit because I can't see the patterns.

---

## 2. One-Sentence Solution

This is an interview training system that learns from every interview you do — practice or real — and uses your accumulated performance data to make you sharper for each next one.

---

## 3. Success Criteria

- [ ] Pre-interview prep goes from a scattered 10-minute file hunt to a focused 3-5 minute dashboard review — and I feel more prepared with less time because everything is on one screen
- [ ] I never have to open Obsidian or dig through markdown files to prep for an interview — the dashboard is the single source
- [ ] Post-interview, the debrief insights visually connect to my overall trends — I can see "this issue has appeared 6 times and here's the trajectory" or "this gap is now resolved"
- [ ] After every debrief, I can see exactly how it changed my improvement priorities — what moved up, what moved down, what got resolved

---

## 4. User Flow

### Sunday Night — Weekly Review
1. Open dashboard
2. See interview pipeline — all active companies, what stage, what's coming this week
3. See improvement tracker — behavioral and technical gaps ranked by priority, with trends
4. Click into any upcoming interview to see its prep status and briefing page

### Night Before Interview — Prep
1. Click into the specific interview (e.g., "Liberate — Round 2 — March 5")
2. See the single-screen briefing:
   - Job description
   - Interviewer name, role, and background
   - Company context (what matters for this interview)
   - Questions asked in previous rounds at this company
   - Predicted questions for this round type and interviewer
   - Suggested answers with mapped stories
   - Active issues to watch from improvement tracker
3. Practice against predicted questions (v2: in-app mock mode)
4. Close laptop, feel ready

### After Interview — Debrief
1. Upload or paste the interview transcript
2. See the generated debrief — scores across dimensions, what went well, what didn't, why
3. See the "what changed" summary — how this debrief updated improvement priorities, what moved up/down/resolved, new insights
4. Everything saved under that company for reference before the next round

---

## 5. Core Features (v1)

### 5.1 Interview Pipeline Board
- **Trigger:** Open the dashboard
- **Behavior:** Shows all active companies with their current stage, upcoming interview dates, and prep status
- **Output:** A board view where each company is a card showing stage, next interview date, and whether a prep doc exists

### 5.2 Single-Screen Interview Briefing
- **Trigger:** Click on a specific interview from the pipeline
- **Behavior:** Pulls together JD, interviewer info, company context, previous round history, predicted questions, suggested answers, and active improvement issues into one view
- **Output:** A single page with all prep material — no file-hopping

### 5.3 Transcript Upload & Debrief Display
- **Trigger:** Click "Add Debrief" on a specific interview round
- **Behavior:** User pastes transcript or uploads file. System stores it and displays the structured debrief (generated externally via Claude skill in v1, via Claude API in v1.5)
- **Output:** Scored debrief with dimension ratings, strengths, improvements, interviewer signals

### 5.4 Post-Debrief "What Changed" Summary
- **Trigger:** After a new debrief is added
- **Behavior:** Compares current improvement tracker state to previous state. Identifies what moved up, what moved down, what's new, what's resolved
- **Output:** A before/after snapshot showing exactly how this interview changed the bigger picture

### 5.5 Improvement Tracker with Trends
- **Trigger:** Accessible from dashboard home and from post-debrief view
- **Behavior:** Shows behavioral and technical gaps ranked by priority (frequency x impact), with trend lines over time showing whether each issue is improving, stagnating, or getting worse
- **Output:** Ranked list with visual trends — not just a snapshot, but a trajectory

### 5.6 Story Bank View
- **Trigger:** Accessible from navigation
- **Behavior:** Shows all stories with deployment history — where used, how many times, follow-up signals, health status
- **Output:** Filterable table/cards showing story health at a glance — which are strong, which are overused, which are untested

### 5.7 Question Bank View
- **Trigger:** Accessible from navigation
- **Behavior:** Shows every question asked across all companies, filterable by stage type, category, company, and frequency
- **Output:** Filterable, searchable view that answers "what do HMs always ask?" or "what came up at Chime?"

### 5.8 Markdown Data Import
- **Trigger:** Initial setup / import function
- **Behavior:** Parses existing markdown files from personal-os (story bank, question bank, debriefs, gap analysis, company prep docs) and populates the database
- **Output:** Dashboard populated with all existing interview data from day one — not starting empty

---

## 6. What We Are NOT Building

1. **Not a coaching chatbot** — The dashboard doesn't give advice or have conversations. It displays and organizes data. The Claude skill handles coaching.
2. **Not a mock interview tool (v1)** — Practice mode is v2. V1 shows predicted questions and suggested answers, but actual mock/scoring stays in Claude.
3. **Not a networking CRM (v1)** — Outreach tracking, contact management, follow-up cadence are all v2.
4. **Not a calendar app** — No Google Calendar integration in v1. Interview dates are entered manually.
5. **Not multi-user (v1)** — No auth, no onboarding, no "create an account." V1 is Michael's data, Michael's dashboard. Data model supports multi-user later.
6. **Not a resume or LinkedIn tool** — No resume review, no LinkedIn optimization. That stays in the skill.
7. **Not a job board or job search engine** — You're not searching for jobs here. You're tracking the ones already in your pipeline.

---

## 7. Technical Decisions

### Stack
- **Framework:** Next.js (React + TypeScript)
- **Database:** Supabase (Postgres)
- **Hosting:** Vercel (free tier)
- **AI Processing (v1):** None — debriefs generated via Claude skill, imported to dashboard
- **AI Processing (v1.5):** Claude API for in-app transcript processing

### Architecture Rationale
- Next.js + Vercel = one-click deploys, free hosting, industry-standard stack
- Supabase = free Postgres with built-in auth (ready for multi-user in v2), API out of the box
- Starting without Claude API keeps v1 free and ships faster
- Data model designed from day one to support the agentic layer (Phase 4)

### Open Source
- Public GitHub repo from day one
- MIT license
- Code visible for interviews and community contributions

---

## 8. Implementation Phases

### Phase 1: Foundation (Sessions 1-2)
- Project setup (Next.js, Supabase, Vercel deployment)
- Database schema design — companies, interviews, stories, questions, debriefs, gaps
- Markdown data import — parse existing personal-os files into the database
- **Milestone:** Live URL with data populated

### Phase 2: Core Dashboard (Sessions 3-5)
- Interview pipeline board — companies, stages, upcoming interviews
- Single-screen interview briefing — the one-page prep view
- Story bank and question bank views with filtering
- **Milestone:** Can prep for an interview using only the dashboard

### Phase 3: Debrief & Tracking (Sessions 6-8)
- Transcript/debrief upload and display
- Post-debrief "what changed" summary
- Improvement tracker with trend visualization
- **Milestone:** Full interview lifecycle supported — prep, interview, debrief, track

### Phase 4: Agents (Future)
- **Prep Agent** — auto-generates briefing when interview is added to pipeline (reads question bank, maps stories, checks gap analysis, researches company/interviewer)
- **Debrief Agent** — processes transcript, scores answers, updates improvement tracker, promotes recurring questions, updates story deployment counts
- **Proactive Coach Agent** — runs on schedule, checks for interviews without prep, stale pipeline, overused stories, emerging patterns
- Build simple first (Vercel cron + Claude API), optionally refactor to agent framework (Claude Agent SDK or LangGraph) for learning

### Skill-to-Agent Mapping (Reference for Phase 4)

The existing Claude skills already contain the agent logic. Phase 4 extracts this into autonomous agents:

| Current Skill Trigger | Future Agent | What It Reads | What It Decides | What It Outputs |
|---|---|---|---|---|
| "New interview: [Company] - [Role] - [Round] - [Date]" | Prep Agent | Question bank, story bank, gap analysis, company data, web (company + interviewer research) | Which questions are likely, which stories map best, which gaps to watch | Complete briefing page written to dashboard |
| "Here's the transcript from my [Company] interview" | Debrief Agent | Transcript, historical scores, improvement tracker, question bank, story bank | Dimension scores, what changed vs. prior trends, whether questions should be promoted, story deployment updates | Debrief + "what changed" summary + updated tracker |
| (No current trigger — manual Sunday check) | Proactive Coach | Pipeline data, improvement tracker, story deployment counts, interview dates | Whether prep is missing, pipeline is stalling, stories are overused, patterns are emerging | Alerts and recommendations surfaced on dashboard |

### V2 Feature Parking Lot
- Google Calendar integration
- Networking CRM and outreach pipeline
- In-app mock interview mode with scoring
- Multi-user auth and onboarding
- Resume and LinkedIn tools
- Native mobile app
- Agent framework refactor (Claude Agent SDK / LangGraph)

---

## 9. Boundaries (for AI Coding Agent)

When building this project with Claude Code:

**Always OK:**
- Edit files within the interview-dashboard project
- Run dev server, tests, builds
- Deploy to Vercel
- Create new components and pages

**Ask first:**
- Changes to the database schema after initial setup
- Adding new dependencies
- Any changes to personal-os-main files
- Deploying to production after Phase 1

**Never:**
- Modify or delete existing personal-os markdown files during import
- Commit API keys, secrets, or credentials
- Add authentication/auth flows (v2)
- Add payment or billing features
- Push to main without confirmation

---

## 10. Open Questions

1. **Data model design** — Exact database schema (tables, relationships, indexes) to be defined in Phase 1. Must support the agentic layer from day one.
2. **Markdown import fidelity** — How much nuance survives import? Gap analysis priority rankings, story deployment history, question cross-references — needs testing.
3. **Dashboard-to-skill handoff** — In v1, debriefs are generated in Claude Code. How does that data get into the dashboard? Manual paste? File upload? Import button? To be decided.
4. **Auth architecture** — When going multi-user (v2), what auth method? Supabase has built-in options (email/password, Google OAuth). Decision deferred but shapes some v1 schema choices.
5. **Agent triggers** — What triggers agents in Phase 4? Database webhooks? Button clicks? Cron checking for new entries? To be decided when we get there.
6. **Mobile experience** — Responsive web app works on phone by default (no native app needed). Revisit if push notifications or offline access become important.
7. **Claude API integration timing** — When to add in-app transcript processing vs. keeping it in the skill. Depends on how friction-free the manual handoff feels in practice.

---

## Appendix: Why This Project

This project serves three purposes:

1. **Immediately useful** — Makes my active job search more effective by surfacing patterns and reducing prep friction
2. **Interview artifact** — "I built an interview intelligence dashboard with a data layer designed to support autonomous agents" is a strong answer at Anthropic, OpenAI, or any AI company
3. **Learning vehicle** — First real build using AI coding tools, progressing from dashboard to agentic workflows (Level 2 → Level 4-5)

---

**Author:** Michael Bachar
**Date:** February 28, 2026
**Status:** Draft — Ready for Review
