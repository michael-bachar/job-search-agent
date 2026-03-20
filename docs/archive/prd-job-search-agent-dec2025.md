# Job Search Agent - Product Brief

**Product Manager:** Michael Bachar  
**Version:** 1.0  
**Date:** December 7, 2025  
**Status:** 🟡 Spec Phase (Not Yet Built)

---

## 🎯 PROBLEM STATEMENT

### **What Problem Are We Solving?**

[DISCUSS TOGETHER: What's most painful about your job search right now?]

**Hypothesis:**
- Finding relevant AI PM jobs is time-consuming (2-3 hours/week browsing)
- Hard to know which roles are good fits (apply to 50 roles, only 5 are actually relevant)
- Company research is tedious (visiting 20 career pages, reading about each company)
- Tracking applications is messy (spreadsheets, forgetting which roles you applied to)

**Current Workflow:**
```
[FILL IN: What do you do today to find and apply for jobs?]

Example:
1. Browse LinkedIn Jobs for "AI Product Manager"
2. Click through 20-30 postings
3. Read each job description
4. Manually assess fit
5. Research company on Google
6. Copy-paste to spreadsheet
7. Apply if good fit

Time: 3-4 hours/week
```

**Pain Points:**
- [ ] Finding jobs (too manual)
- [ ] Scoring fit (not sure which to prioritize)
- [ ] Tracking applications (messy spreadsheet)
- [ ] Company research (time-consuming)
- [ ] Other: _______________

---

## 👤 USER (YOU)

**Who:** Michael Bachar, applying for AI PM roles

**Goals:**
1. Find 30+ relevant AI PM roles in next 2 weeks
2. Apply to high-fit roles first (prioritization)
3. Track applications without mess
4. Save 2-3 hours/week on job search

**Technical Comfort:**
- Can run Python scripts
- Comfortable with terminal
- Has API keys (OpenAI, Tavily)
- Wants something practical, not a toy

**Constraints:**
- Time: 15-20 hours/week for job search (can't spend all day browsing jobs)
- Budget: <$10/month on API costs
- Stealth mode: Can't let current employer know (no public LinkedIn scraping)

---

## 💡 PROPOSED SOLUTION

### **Product Vision:**

An AI agent that automates the tedious parts of job searching (finding roles, scoring fit, researching companies), so you can focus on high-value activities (networking, applications, interviews).

### **Core Capabilities:**

**MVP (Must-Have)**:
- [ ] Searches for AI PM jobs at target companies
- [ ] Scores each job against your resume (0-100)
- [ ] Researches companies (funding, AI focus, size)
- [ ] Exports to CSV for tracking
- [ ] Runs on-demand (you trigger it)

**V2 (Nice-to-Have)**:
- [ ] Filters out poor fits (PhD required, wrong location)
- [ ] Generates custom cover letter drafts
- [ ] Tracks which jobs you've applied to
- [ ] Alerts you to new postings at target companies

**V3 (Future)**:
- [ ] Automated daily runs
- [ ] Email digest of top 10 new roles
- [ ] Integration with application tracker

---

## 🛠️ TECHNICAL ARCHITECTURE

### **Platform Options (We Need to Decide):**

#### **Option 1: Build in Cursor (Local Python)** ⭐

**Pros:**
- ✅ Full control (no platform limitations)
- ✅ Free to run (only pay for API calls)
- ✅ Can iterate fast (Cursor Composer + AI assistance)
- ✅ Works offline (no internet dependency beyond API calls)
- ✅ Secure (runs locally, no data leaving your machine)

**Cons:**
- ❌ Need to set up environment (venv, dependencies)
- ❌ Terminal-based (no UI unless we build Streamlit)
- ❌ You need to run it manually

**Best for:** Full customization, learning how agents work, portfolio project

---

#### **Option 2: Google AI Studio / Vertex AI**

**Pros:**
- ✅ No setup required (cloud-based)
- ✅ UI for testing agents
- ✅ Built-in tools and integrations
- ✅ Can schedule runs (automated)

**Cons:**
- ❌ Limited control (bound by platform capabilities)
- ❌ Costs more (Vertex AI pricing)
- ❌ Less impressive as portfolio project (no code to show)
- ❌ Harder to customize

**Best for:** Quick prototyping, no-code preference

---

#### **Option 3: Replit (Cloud IDE)**

**Pros:**
- ✅ Run from anywhere (cloud-based)
- ✅ Easy to share (public URL)
- ✅ Built-in deployment
- ✅ Collaborative (can work with others)

**Cons:**
- ❌ Free tier is limited (slow)
- ❌ Need to keep Replit tab open for scheduled runs
- ❌ API keys stored in cloud (slightly less secure)

**Best for:** Quick iteration, sharing with others

---

#### **Option 4: LangChain Studio / LangServe**

**Pros:**
- ✅ Built for LangChain agents (native support)
- ✅ Easy deployment (LangServe for API)
- ✅ Observability built-in (LangSmith tracing)

**Cons:**
- ❌ Newer platform (less mature)
- ❌ Still need to code locally first

**Best for:** If you're already using LangChain heavily

---

#### **Option 5: No-Code Agent Builders** (Relevance AI, LangFlow, etc.)

**Pros:**
- ✅ Visual builder (drag-and-drop)
- ✅ Fast to prototype (1-2 hours)
- ✅ No coding required

**Cons:**
- ❌ Less impressive for portfolio (not coding)
- ❌ Limited customization
- ❌ Doesn't teach you how agents work
- ❌ Platform lock-in

**Best for:** Quick prototype to validate idea, not for portfolio

---

## **📊 Platform Comparison**

| Platform | Time to Build | Control | Portfolio Value | Learning | Cost |
|----------|---------------|---------|-----------------|----------|------|
| **Cursor (Local)** | 8-10 hrs | ✅ Full | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | $ (API only) |
| **Google AI Studio** | 2-3 hrs | ⚠️ Limited | ⭐⭐ | ⭐⭐⭐ | $$ |
| **Replit** | 6-8 hrs | ✅ Good | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | $ (free tier OK) |
| **LangChain Studio** | 6-8 hrs | ✅ Good | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | $ (API only) |
| **No-Code** | 2-3 hrs | ❌ Low | ⭐ | ⭐⭐ | $$ (platform fees) |

---

## **🎯 My Recommendation: Cursor (Local Python)**

**Why:**
1. ✅ **Best for portfolio** - You can show real code on GitHub
2. ✅ **Best for learning** - You'll understand how agents work
3. ✅ **Most flexible** - Full control, can customize everything
4. ✅ **You already have setup** - From Research Agent work
5. ✅ **Cheap** - Only pay for API calls (~$2-5 total)

**Trade-off**: Takes 8-10 hours vs 2-3 hours for no-code. But those extra hours give you:
- Real code for GitHub
- Deep understanding of agents
- Interview stories ("I built X, here's how I solved Y")

---

## **📝 Let's Build the Product Brief Together**

I'll create a structured PRD and we'll fill it in together. Then we'll decide on architecture.

<function_calls>
<invoke name="write">
<parameter name="contents"># Job Search Agent - Product Requirements Document (PRD)

**Product Manager:** Michael Bachar  
**Version:** 1.0 - MVP Spec  
**Date:** December 7, 2025  
**Status:** 🟡 Spec Phase → Next: Build Phase

---

## 📋 DOCUMENT SECTIONS

1. [Problem & Opportunity](#problem--opportunity)
2. [User & Use Cases](#user--use-cases)
3. [Solution Overview](#solution-overview)
4. [Functional Requirements](#functional-requirements)
5. [Technical Architecture](#technical-architecture)
6. [Success Metrics](#success-metrics)
7. [Open Questions](#open-questions)

---

## 🎯 PROBLEM & OPPORTUNITY

### **Problem Statement**

**Current pain**: [DISCUSS: What's most painful about finding/applying for jobs?]

Finding and applying for AI PM jobs is time-consuming and inefficient:
- Browsing job boards takes 2-3 hours/week
- Hard to prioritize which roles to apply to first
- Company research is tedious (visiting 20 career pages)
- Tracking applications in spreadsheets is messy
- Not sure if a role is a good fit until you read the full description

### **Opportunity**

**What if an AI agent could**:
- Automatically find AI PM jobs at target companies
- Score each job against your resume (so you know which to prioritize)
- Research companies (so you understand context)
- Export everything to a clean CSV (so tracking is easy)

**Time savings**: 2-3 hours/week → 30 minutes/week

**Better outcomes**: Apply to higher-fit roles (less spray-and-pray)

### **Why This Matters**

**Short-term (next 8 weeks)**: Helps you apply to 30+ roles efficiently

**Medium-term (portfolio)**: Demonstrates you can build practical AI agents that solve real problems

**Long-term (learning)**: Teaches you multi-tool agent orchestration, which is valuable for AI PM role

---

## 👤 USER & USE CASES

### **Primary User**

**Who:** You (Michael Bachar)

**Context:**
- Currently: Senior PM at OnePay
- Goal: Land AI PM role in 8 weeks
- Time: 15-20 hours/week for job search
- Target: 30-35 applications in 8 weeks

**Needs:**
- Find relevant AI PM jobs (not generic PM roles)
- Understand which roles are best fit (prioritization)
- Track applications without mess
- Save time on tedious tasks (searching, researching)

### **Use Cases**

**Use Case 1: Weekly Job Discovery**
```
Scenario: It's Sunday morning, Michael wants to find new AI PM jobs posted this week

1. Michael runs: python main.py --companies companies.txt
2. Agent searches career pages for 20 companies
3. Agent finds 15 new AI PM postings
4. Agent scores each against Michael's resume
5. Agent exports to CSV: job_search_results_2025_12_08.csv
6. Michael opens CSV, sees top 5 roles (score > 80)
7. Michael applies to top 5 roles (1 hour)

Time saved: 2 hours of browsing → 5 minutes running agent
```

**Use Case 2: Deep-Dive on Specific Company**
```
Scenario: Michael got a referral at Anthropic, wants to find ALL open AI PM roles there

1. Michael runs: python main.py --company "Anthropic" --deep-search
2. Agent finds 3 AI PM roles at Anthropic
3. Agent scores each, researches team structure
4. Agent outputs: Which role fits best + why
5. Michael applies to the top-scored role

Time saved: 1 hour → 5 minutes
```

**Use Case 3: Company Research**
```
Scenario: Michael has a coffee chat with someone at Perplexity, wants context

1. Michael runs: python research.py --company "Perplexity"
2. Agent searches: Recent funding, AI products, team size, culture
3. Agent outputs: 1-page company brief
4. Michael uses this to prepare thoughtful questions

Time saved: 30 min → 2 minutes
```

---

## 💡 SOLUTION OVERVIEW

### **What We're Building**

**Product Name:** AI Job Search Agent (or "JobScout AI" or "AI PM Finder" - decide later)

**One-Line Description:**
An autonomous AI agent that finds, scores, and researches AI PM job opportunities based on your resume and target companies.

### **Key Features (MVP)**

1. **Automated Job Search**
   - Input: List of 20 target companies
   - Output: All open AI PM roles at those companies
   - Method: Web search via Tavily (no LinkedIn scraping)

2. **Intelligent Fit Scoring**
   - Input: Job description + your resume
   - Output: 0-100 fit score + reasoning
   - Method: LLM analyzes job requirements vs. your experience

3. **Company Research**
   - Input: Company name
   - Output: Funding, AI products, team size, recent news
   - Method: Web search + synthesis

4. **CSV Export**
   - Output: Structured spreadsheet with all findings
   - Columns: Company, Role, Fit Score, Why Good Fit, Required Skills, Job URL, Date
   - Sorted by fit score (highest first)

### **What We're NOT Building (Out of Scope for MVP)**

❌ LinkedIn scraping (against ToS, complex, risky)  
❌ Automated applications (you still apply manually)  
❌ Email notifications (you check CSV manually)  
❌ Integration with ATS systems (too complex)  
❌ Cover letter generation (defer to V2)  
❌ Scheduled runs (you run manually on-demand)  

---

## 📋 FUNCTIONAL REQUIREMENTS

### **Requirement 1: Job Search**

**As a user**, I want to search for AI PM jobs at my target companies, so that I don't have to manually visit 20 career pages.

**Acceptance Criteria:**
- [ ] Given a list of companies (companies.txt), agent searches each company's career page
- [ ] Agent finds all roles with keywords: "AI Product Manager", "ML Product Manager", "GenAI PM"
- [ ] Agent extracts: Job title, location, job URL, posting date (if available)
- [ ] Agent handles errors gracefully (if company site is down, continues with others)
- [ ] Search completes in < 5 minutes for 20 companies

**Answered Questions:**
- [x] **How do we handle companies with no open AI PM roles?** → Include in CSV with "No AI PM openings found" in Role Title column, score = 0
- [x] **Do we search only career pages, or also general web?** → General web search (Tavily handles this). Search: "AI Product Manager jobs at [Company] site:[company].com"
- [x] **What if job title doesn't say "AI PM" but description is AI-focused?** → Scorer evaluates description content, not just title. "Product Manager, ML Infra" could score 70+ if description mentions LLMs/RAG

---

### **Requirement 2: Fit Scoring**

**As a user**, I want each job scored against my resume (0-100), so that I can prioritize which roles to apply to first.

**Acceptance Criteria:**
- [ ] Given a job description + my resume, agent outputs score (0-100)
- [ ] Agent explains reasoning (2-3 sentences): "Why this score?"
- [ ] Scoring considers:
  - Title match (is it AI PM or generic PM?)
  - Required skills (RAG, LLM, evaluation frameworks, etc.)
  - Required experience (years, industries)
  - Location (remote-friendly? onsite?)
  - Company stage (startup vs big tech)
- [ ] Scoring is consistent (running twice on same job gives same score ±5 points)

**Scoring Rubric** (To Discuss):
```
Title match: ___ points (out of 100)
Required skills match: ___ points
Experience level match: ___ points
Location match: ___ points
Company stage match: ___ points
AI focus: ___ points

Total: 100 points
```

**Answered Questions:**
- [x] **What's a "good" score?** → > 80 = apply immediately, 60-80 = review carefully, 40-60 = borderline, < 40 = skip
- [x] **Do we weight certain criteria higher?** → Yes (see scoring rubric in Finalized Specs section). Skills (30%) and title (25%) weighted highest because they're most predictive of fit.
- [x] **How do we handle missing information in job description?** → Default to neutral/conservative score. If experience not mentioned, assume mid-level (5-7 years). If location not mentioned, assume "Unknown" and score = 50/100 for location component.

---

### **Requirement 3: Company Research**

**As a user**, I want context on each company (funding, AI products, size), so that I can prepare for coffee chats and tailor applications.

**Acceptance Criteria:**
- [ ] For each company with open role, agent searches for:
  - Recent funding (Series A/B/C, amount, date)
  - AI products/focus (what do they build?)
  - Team size (estimated employees)
  - Recent news (last 30 days)
- [ ] Research is concise (2-3 sentences per company)
- [ ] Research is included in CSV output

**Answered Questions:**
- [x] **How deep should research go?** → 1-2 Tavily searches per company (keep it lightweight for MVP). Search: "[Company] funding AI products" and parse top 3 results.
- [x] **Do we cache research?** → Yes for MVP session (store in memory dict), but don't persist to disk. Each run is fresh. V2 can add persistent cache.
- [x] **What if company info is scarce?** → Note "Limited public info available" and include what we can find (even if just company website description).

---

### **Requirement 4: CSV Export**

**As a user**, I want results in a clean CSV, so that I can easily track and prioritize applications.

**Acceptance Criteria:**
- [ ] Agent exports to CSV with columns:
  - Company
  - Role Title
  - Fit Score (0-100)
  - Why Good Fit (2-3 sentence reasoning)
  - Required Skills Match (which skills from my resume align)
  - Location
  - Job URL (clickable)
  - Company Research (brief summary)
  - Date Found
- [ ] CSV is sorted by Fit Score (highest first)
- [ ] CSV file named with timestamp: job_search_YYYY_MM_DD.csv
- [ ] Easy to open in Google Sheets or Excel

**Answered Questions:**
- [x] **Multiple CSVs or single master?** → Multiple CSVs (one per run) with timestamp: `job_search_YYYY_MM_DD_HHMM.csv`. Allows tracking over time ("which new jobs appeared this week?").
- [x] **Track "applied" status in CSV?** → Not in MVP. Export includes empty "Applied" column you can manually update in Google Sheets if desired.
- [x] **Include jobs with score < 40?** → Yes, include all jobs found. You might want to see what was filtered out. Just sort by score so low-scoring jobs are at bottom.

---

## 🏗️ TECHNICAL ARCHITECTURE

### **Architecture Decision: Where to Build?**

**NEED TO DECIDE:** Local Python vs Cloud Platform

**Recommendation:** Local Python in Cursor

**Why:**
- Best for portfolio (real code to show)
- Best for learning (understand agent internals)
- Most flexible (full control)
- Cheapest (only API costs)

**Alternative considered:**
- Google AI Studio: Faster to prototype, but less impressive
- Replit: Good for sharing, but similar to local
- No-code: Too limiting for this use case

---

### **Tech Stack (If Building Locally)**

**Core:**
- Python 3.11
- LangChain (agent orchestration)
- OpenAI GPT-4o-mini (cheaper, good enough for this)
- Tavily API (web search)
- pandas (CSV export)

**Agent Pattern:**
- ReAct (reasoning + acting)
- Tools: web_search, score_fit, research_company, export_csv

**Project Structure:**
```
job-search-agent/
├── main.py              # CLI entry point
├── agent.py             # Agent orchestration
├── tools/
│   ├── job_search.py    # Searches career pages
│   ├── scorer.py        # Scores job fit
│   ├── company_research.py  # Researches companies
│   └── csv_export.py    # Exports to CSV
├── prompts/
│   ├── system_prompt.txt     # Agent instructions
│   └── scorer_prompt.txt     # Scoring rubric
├── config.py            # Settings
├── resume.txt           # Your resume (for scoring)
├── companies.txt        # List of 20 companies
├── outputs/             # CSV files
├── requirements.txt
├── .env                 # API keys
├── .gitignore
└── README.md
```

---

### **Agent Workflow**

```
1. User runs: python main.py

2. Agent reads:
   - companies.txt (20 target companies)
   - resume.txt (your resume)
   
3. For each company:
   a. Tool: web_search("AI Product Manager jobs at [Company]")
   b. Extract: Job title, URL, description
   c. Tool: score_fit(job_description, resume) → 0-100 score
   d. Tool: research_company(company) → funding, AI focus, size
   
4. Agent compiles results

5. Tool: export_csv(results) → job_search_YYYY_MM_DD.csv

6. Agent outputs: "Found 15 jobs. Top 5 scores: [list]. CSV saved to outputs/"
```

---

### **Alternative: Simpler First Version**

**If 8-10 hours is too much right now**, we could build a **2-hour version**:

**Ultra-Simple Agent:**
- Input: You paste job URLs (you found them manually)
- Agent: Scores each + explains why
- Output: Ranked list with recommendations

**Later upgrade** (Week 3-4): Add job search capability

---

## ✅ SUCCESS METRICS

### **Product Success:**
- [ ] Finds 30+ relevant AI PM roles across 20 companies
- [ ] Scoring is accurate (manually verify top 10 → 8+ are actually good fits)
- [ ] Saves 2+ hours/week on job search
- [ ] You actually USE it (not just build it)

### **Technical Success:**
- [ ] Agent runs without errors
- [ ] Completes search in < 5 minutes
- [ ] CSV is clean and usable
- [ ] Code is documented and on GitHub

### **Portfolio Success:**
- [ ] Comprehensive README with architecture
- [ ] Demo video showing workflow
- [ ] Can explain in interviews: "I built this because..."
- [ ] Shows practical problem-solving (not just technical exercise)

---

## ❓ OPEN QUESTIONS (Let's Discuss)

### **Product Questions:**

**Q1: What's your BIGGEST pain point right now?**
- [ ] A) Finding jobs (too manual)
- [ ] B) Scoring fit (not sure which to prioritize)
- [ ] C) Tracking applications (messy)
- [ ] D) Company research (time-consuming)

**Answer:** ____________

**Q2: How often would you run this agent?**
- [ ] A) Daily (check for new jobs every day)
- [ ] B) Weekly (Sunday job search routine)
- [ ] C) On-demand (when I have time)

**Answer:** ____________

**Q3: What's a "good fit" score threshold?**
- [ ] > 80 = Apply immediately
- [ ] 60-80 = Review carefully, maybe apply
- [ ] < 60 = Skip

**Answer:** ____________

---

### **Technical Questions:**

**Q4: Where do you want to build this?**
- [ ] A) Local Python in Cursor (8-10 hours, best for portfolio)
- [ ] B) Google AI Studio (2-3 hours, faster prototype)
- [ ] C) Replit (6-8 hours, can share easily)

**Answer:** ____________

**Q5: Do you want a UI or CLI?**
- [ ] A) CLI only (terminal, faster to build)
- [ ] B) Streamlit UI (browser-based, nicer UX)
- [ ] C) CLI for MVP, UI later

**Answer:** ____________

**Q6: How do you want to provide input?**
- [ ] A) Text file with company list (companies.txt)
- [ ] B) Interactive prompt (agent asks "which companies?")
- [ ] C) Config file (config.json with companies + preferences)

**Answer:** ____________

---

### **Scope Questions:**

**Q7: MVP vs Full Version?**

**Option A - Ultra-Simple (2-3 hours)**:
- You find jobs manually (LinkedIn, career pages)
- You paste URLs to agent
- Agent scores + explains fit
- Agent exports to CSV

**Option B - MVP (8-10 hours)** ⭐:
- Agent searches for jobs (Tavily)
- Agent scores fit
- Agent researches companies
- Agent exports to CSV
- You run manually when you want

**Option C - Full Version (15-20 hours)**:
- Everything in Option B, plus:
- Agent runs daily automatically
- Agent sends email digest
- Agent generates cover letter drafts
- Agent tracks application status

**Which version do you want?** ____________

---

## 🚀 NEXT STEPS

### **Before We Build:**

1. **Answer Open Questions** (above)
2. **Finalize scope** (MVP vs Ultra-Simple vs Full)
3. **Choose platform** (Local Cursor vs other)
4. **Review architecture** (make sure it makes sense)

### **Build Phase:**

5. **Set up project** (30 min)
6. **Use Cursor Composer** (30 min - generates scaffold)
7. **Test & iterate** (4-8 hours)
8. **Polish & document** (2-3 hours)
9. **Ship to GitHub** (30 min)

---

## 📝 DISCUSSION NOTES & DECISIONS

**Session Date:** December 6, 2025

### **DECISIONS MADE:**

**What pain point matters most?**
```
A) Finding jobs + B) Scoring fit (Combined)

Reasoning: You have 20 target companies already identified. The manual process is:
- Visiting 20 career pages weekly
- Reading through dozens of job descriptions
- Manually assessing "is this AI PM or generic PM?"
- Not sure which roles to prioritize

An agent that finds AND scores jobs would save the most time.
```

**What's your time budget?**
```
Option B - MVP (8-10 hours) ⭐

Reasoning:
- Ultra-simple (2-3 hours) doesn't showcase agent capabilities for portfolio
- Full version (15-20 hours) is too much right now with job search starting
- MVP hits sweet spot: portfolio-worthy, practical utility, reasonable time investment
- Can iterate to v2 after it proves useful
```

**Platform preference?**
```
A) Local Python in Cursor ⭐

Reasoning:
- Best for portfolio (real code to show on GitHub)
- You already have the environment set up
- Full control and customization
- Can use Cursor Composer to accelerate development
- Only pay for API calls (~$2-5 for MVP testing)
- Shows technical depth in interviews
```

**MVP scope?**
```
Option B - MVP (Job Search + Scoring + Research + CSV Export)

Core features:
1. Automated job search across 20 target companies
2. AI-powered fit scoring (0-100) based on your resume
3. Basic company research (funding, AI focus, team size)
4. CSV export sorted by fit score
5. Manual runs (you trigger weekly)

NOT included in MVP:
- Automated daily runs (add later)
- Email notifications (add later)
- Cover letter generation (v2 feature)
- Application tracking (manual for now)
- LinkedIn scraping (too risky)
```

**When do you want to build this?**
```
Week 1-2 (Next two weekends)

Timeline:
- Weekend 1 (Dec 7-8): Project setup + core agent scaffolding (4-5 hours)
- Week 1 evenings: Build job search tool + test (2-3 hours)
- Weekend 2 (Dec 14-15): Build scorer + company research + CSV export (3-4 hours)
- Week 2 evenings: Testing + polish + README (1-2 hours)

Total: ~10-12 hours over 2 weeks
Start using it: Week 3 (Dec 16+)
```

---

## ✅ FINALIZED SPECIFICATIONS

### **Agent Pattern: ReAct** ✅

**Why ReAct over other patterns:**
- **Dynamic workflow**: Don't know upfront how many jobs exist at each company
- **Adaptive reasoning**: Agent discovers patterns (e.g., "This company has 3 AI PM roles but only 1 is remote-friendly")
- **Exploratory task**: Each search result informs next steps
- **Simple to implement**: No need for complex Plan-and-Execute for MVP

**Agent Flow:**
```
User runs: python main.py --companies companies.txt

Agent (ReAct loop):
1. Reason: "I need to search for AI PM jobs at Company 1"
2. Act: web_search("AI Product Manager jobs at Anthropic")
3. Observe: Found 2 job postings
4. Reason: "I should extract details from each posting"
5. Act: extract_job_details(url_1)
6. Observe: Got title, description, requirements, URL
7. Reason: "I should score this against the resume"
8. Act: score_fit(job_description, resume)
9. Observe: Score = 85, reasoning = "Strong match on RAG experience"
10. Reason: "I should get company context"
11. Act: research_company("Anthropic")
12. Observe: Got funding, AI focus, team size
13. Reason: "Move to next company"
14. Loop continues for all 20 companies...
15. Generate: CSV with all results sorted by score
```

---

### **Tech Stack (Final)**

```
Core:
- Python 3.11+
- LangChain (agent orchestration)
- OpenAI GPT-4o-mini (cost-effective, good for this task)
- Tavily API (web search)
- pandas (CSV export)
- python-dotenv (environment variables)

Agent Pattern:
- ReAct (reasoning + acting)

Tools:
1. web_search (Tavily) - Find job postings
2. extract_job_details (parsing) - Parse job page
3. score_fit (LLM) - Score against resume
4. research_company (Tavily + LLM) - Company context
5. export_csv (pandas) - Output results
```

---

### **Project Structure (Final)**

```
job-search-agent/
├── main.py                    # CLI entry point
├── agent.py                   # ReAct agent orchestration
├── tools/
│   ├── __init__.py
│   ├── job_search.py         # Searches for jobs (Tavily)
│   ├── job_parser.py         # Extracts job details
│   ├── scorer.py             # Scores job fit
│   ├── company_research.py   # Researches companies
│   └── csv_exporter.py       # Exports to CSV
├── prompts/
│   ├── system_prompt.txt     # Agent instructions
│   ├── scorer_prompt.txt     # Scoring rubric
│   └── research_prompt.txt   # Company research template
├── data/
│   ├── resume.txt            # Your resume (for scoring)
│   └── companies.txt         # 20 target companies
├── outputs/                  # CSV files go here
│   └── .gitkeep
├── tests/
│   ├── __init__.py
│   └── test_tools.py         # Unit tests
├── config.py                 # Settings (max iterations, model, etc.)
├── requirements.txt
├── .env.example              # Template for API keys
├── .env                      # API keys (gitignored)
├── .gitignore
└── README.md                 # Portfolio documentation
```

---

### **Scoring Rubric (Final)**

**Total: 100 points**

```python
scoring_criteria = {
    "title_match": {
        "weight": 25,
        "description": "Is this explicitly an AI/ML PM role?",
        "examples": {
            100: "AI Product Manager, ML PM, GenAI PM",
            75: "Product Manager (AI team)",
            50: "Product Manager with AI mentioned",
            25: "Product Manager (no AI mention)"
        }
    },
    "required_skills_match": {
        "weight": 30,
        "description": "Match on: RAG, LLMs, prompt engineering, evaluation, agents",
        "calculation": "(matched_skills / total_required_skills) * 30"
    },
    "experience_level": {
        "weight": 20,
        "description": "Does YOE requirement match?",
        "examples": {
            100: "5-7 years (perfect match)",
            75: "4-6 years or 6-8 years (close)",
            50: "3-5 years (stretch but possible)",
            25: "8+ years (too senior)"
        }
    },
    "location_match": {
        "weight": 15,
        "description": "Remote-friendly? Location ok?",
        "examples": {
            100: "Remote or NYC",
            75: "Hybrid NYC",
            50: "SF (would need to relocate)",
            25: "Onsite-only non-NYC"
        }
    },
    "company_stage_ai_focus": {
        "weight": 10,
        "description": "AI-first company? Big tech AI team?",
        "examples": {
            100: "AI-first company (Anthropic, OpenAI)",
            75: "Big tech AI team (Google Gemini)",
            50: "Tech company adding AI",
            25: "Non-tech with AI initiative"
        }
    }
}

# Thresholds:
# > 80 = Apply immediately (high fit)
# 60-80 = Review carefully, probably apply
# 40-60 = Borderline, only if few other options
# < 40 = Skip (poor fit)
```

---

### **Input Files**

**`data/companies.txt`** (20 target companies):
```
Anthropic
OpenAI
Perplexity
Cohere
Mistral AI
Google
Microsoft
Meta
AWS
Salesforce
LangChain
LlamaIndex
Pinecone
Weaviate
Weights & Biases
Stripe
Plaid
Brex
Ramp
Mercury
```

**`data/resume.txt`** (Key points for scoring):
```
Michael Bachar
AI Product Manager

EXPERIENCE:
- OnePay: Built production RAG chatbot, 14K queries/day, 85% accuracy
- Reduced hallucination rate from 20% to 10%
- Multi-stage LLM orchestration with tool calling
- Evaluation frameworks (LLM-as-judge, regression testing)
- AWS Bedrock, LangChain, LanceDB vector search
- Prompt engineering, retrieval optimization

SKILLS:
- GenAI/LLM product management
- RAG architecture
- AI agents & tool calling
- Evaluation frameworks
- Production AI systems
- Fintech/payments domain
- 6+ years PM experience

LOOKING FOR:
- AI Product Manager roles
- Remote or NYC
- AI-first companies or big tech AI teams
```

---

### **CLI Usage (Final)**

```bash
# Basic usage (search all companies)
python main.py

# Search specific companies
python main.py --companies "Anthropic,OpenAI,Perplexity"

# Deep search (more thorough, slower)
python main.py --deep-search

# Custom output path
python main.py --output outputs/jobs_dec_6.csv

# Verbose logging
python main.py --verbose
```

---

### **Output CSV Format**

```csv
Company,Role Title,Fit Score,Why Good Fit,Required Skills Match,Missing Skills,Location,Remote,Job URL,Company Research,Date Found
Anthropic,AI Product Manager,92,"Strong match: Production RAG experience, evaluation frameworks, AI safety focus aligns","RAG (✓), LLM orchestration (✓), Evaluation (✓), Prompt engineering (✓)","PhD in ML (optional)","San Francisco, CA",Yes,https://anthropic.com/careers/...,Series C funded ($450M), AI safety focus, 150 employees, Building Claude,2025-12-06
OpenAI,Product Manager - ChatGPT,88,"Excellent fit: Uses GPT-4 at OnePay, production LLM experience, scaling chatbots","LLM APIs (✓), Production scaling (✓), User research (✓)","Deep RL knowledge (nice-to-have)","San Francisco, CA",Hybrid,https://openai.com/careers/...,Series C+ funded, Industry leader, ChatGPT/GPT-4 products, 500+ employees,2025-12-06
[... more rows ...]
```

---

## ✅ SUCCESS METRICS (FINAL)

### **MVP Success (Week 3)**
- [ ] Agent runs without errors on 20 companies
- [ ] Finds 15+ relevant AI PM roles
- [ ] Scoring accuracy: 80%+ (manually verify top 10 scores)
- [ ] CSV is clean, sortable, and useful
- [ ] Saves 2+ hours vs manual search

### **Portfolio Success (Week 4-6)**
- [ ] Comprehensive README with architecture diagram
- [ ] Code on GitHub (public repo)
- [ ] Demo video showing agent in action
- [ ] Can explain in interviews: "I built this because I needed it"

### **Job Search Success (Week 3-8)**
- [ ] You actually USE it weekly
- [ ] Apply to 5-10 jobs per week from results
- [ ] Helps prioritize high-fit roles
- [ ] Saves time for networking/interviews

---

## 🚀 NEXT STEPS - BUILD PHASE

### **This Weekend (Dec 7-8): Project Setup**

**Saturday Morning (2-3 hours):**
1. Create project structure (30 min)
2. Set up virtual environment + dependencies (30 min)
3. Create `.env` with API keys (15 min)
4. Build basic ReAct agent scaffold (45 min)
5. Test with simple tool (30 min)

**Sunday Morning (2 hours):**
6. Build job search tool (Tavily integration)
7. Test on 3 companies
8. Verify results

### **Week 1 Evenings (2-3 hours total):**
9. Build job parser tool
10. Build scorer tool with rubric
11. Test scoring on 5 sample jobs

### **Weekend 2 (Dec 14-15): Core Features**

**Saturday (3-4 hours):**
12. Build company research tool
13. Build CSV exporter
14. End-to-end test on 5 companies

**Sunday (2-3 hours):**
15. Run on all 20 companies
16. Debug issues
17. Polish output format

### **Week 2 Evenings (1-2 hours):**
18. Write comprehensive README
19. Add architecture diagram
20. Create demo video or screenshots
21. Push to GitHub

### **Week 3 (Dec 16+): USE IT**
22. Run agent weekly (Sunday mornings)
23. Apply to top-scored roles
24. Track which roles you apply to
25. Iterate based on feedback

---

## 🎯 WHERE TO BUILD

**Decision: Local Python in Cursor** ✅

### **Setup Steps:**

```bash
# 1. Create project directory
cd ~/Desktop
mkdir job-search-agent
cd job-search-agent

# 2. Create virtual environment
python3 -m venv venv
source venv/bin/activate  # On macOS/Linux

# 3. Install dependencies
pip install langchain langchain-openai tavily-python pandas python-dotenv

# 4. Create .env file
echo "OPENAI_API_KEY=your_key_here" > .env
echo "TAVILY_API_KEY=your_key_here" >> .env

# 5. Open in Cursor
cursor .
```

### **Use Cursor Composer to Accelerate:**

**Prompt for Cursor Composer:**
```
Build a ReAct agent for job search automation:

1. Agent searches for AI PM jobs at target companies using Tavily
2. Agent scores each job against my resume (0-100)
3. Agent researches companies (funding, AI focus)
4. Agent exports to CSV sorted by fit score

Tech stack: Python, LangChain, OpenAI GPT-4o-mini, Tavily, pandas

Project structure:
- main.py (CLI)
- agent.py (ReAct orchestration)
- tools/ (job_search, scorer, company_research, csv_exporter)
- prompts/ (system_prompt, scorer_prompt)
- data/ (resume.txt, companies.txt)

Use the scoring rubric in the PRD (title match 25pts, skills 30pts, experience 20pts, location 15pts, company 10pts).

Implement ReAct pattern: Reason → Act → Observe → Repeat.
```

---

## 📋 ANSWERED OPEN QUESTIONS

### **Q1: What's your BIGGEST pain point?**
**Answer:** A + B (Finding jobs + Scoring fit)

### **Q2: How often would you run this agent?**
**Answer:** B (Weekly - Sunday job search routine)

### **Q3: What's a "good fit" score threshold?**
**Answer:**
- \> 80 = Apply immediately
- 60-80 = Review carefully, probably apply
- 40-60 = Borderline
- < 40 = Skip

### **Q4: Where do you want to build this?**
**Answer:** A (Local Python in Cursor)

### **Q5: Do you want a UI or CLI?**
**Answer:** A (CLI only for MVP, maybe Streamlit UI later)

### **Q6: How do you want to provide input?**
**Answer:** A (Text file with company list - companies.txt)

### **Q7: MVP vs Full Version?**
**Answer:** Option B - MVP (8-10 hours)

---

## ✅ FINAL PRD APPROVED

**Status:** 🟢 Ready to Build  
**Next Action:** Set up project structure this weekend  
**Timeline:** 2 weeks to MVP  
**Start Date:** December 7, 2025  
**Target Completion:** December 20, 2025

**Let's build this!** 🚀

