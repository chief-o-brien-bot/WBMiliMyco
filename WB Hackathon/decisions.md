# Decisions Log

Track all major decisions made during the hackathon.

---

## 2026-02-01 - Evening

### Naming Convention
- **Decision:** Use "OpenClaw" as primary framework name throughout project
- **Rationale:** Current/official branding (ClawdBot and MoltBot are historical)
- **Implementation:** Updated all docs, code, and presentations (preserved historical context in terminology section)

### Infrastructure Approach
- **Decision:** Mili handles AWS snapshot provisioning for each variant
- **Process:** 1) Create snapshots, 2) Provision for testing, 3) Final snapshot when ready
- **Status:** Team left W&B office heading home, provisioning in progress

### Timeline Checkpoint
- **Current Time:** Saturday 9:42 PM PST
- **Deadline:** Sunday 1:30 PM PST (~15h 48m remaining)
- **Status:** Infrastructure setup phase

## 2026-02-01 - Earlier

### Project Scope
- **Decision:** Focus on benchmarking existing OpenClaw variants rather than building new agent frameworks
- **Rationale:** Use existing industry benchmarks to save time and ensure credibility

### Variants Selected
- **Decision:** Test 5 OpenClaw variants + 2 baselines
- **Variants:** Vanilla, Crustafarion, Moltbook-Informed, Human-Optimized, Drugs Skill
- **Baselines:** Claude Code, Claude Opus 4.5
- **Rationale:** Cover control, philosophical/religious influence, community techniques, human intuition, and experimental tools

### Presentation Strategy
- **Decision:** Recorded results shown in live presentation
- **Format:** Show what we did, explain findings, potentially more details TBD
- **Rationale:** More reliable than live demo, lets us focus on insights and analysis rather than hoping tests run smoothly on stage

---

## TBD

### Benchmark Selection ✅ DECIDED
- **Decision:** Use GAIA (General AI Assistants) benchmark, Level 1 for MVP
- **Rationale:** 
  - Designed for agentic LLMs with tools (perfect for OpenClaw)
  - Tests agent-specific capabilities: web search, file handling, multi-step planning
  - Unambiguous grading (single factoid answers)
  - Level 1 is MVP-friendly (≤5 steps, 0-1 tool)
  - Well-established leaderboard + credibility
- **Source:** https://huggingface.co/datasets/gaia-benchmark/GAIA
- **Alternatives considered:** MMLU-Pro (too LLM-focused), AgentBench (too complex for deadline)
- **Implementation:** 
  - Start with Level 1 validation set (~20-30 questions)
  - Track accuracy, steps, cost per question
  - Stretch: Add Level 2, multiple runs if time permits
- **Time:** 2026-02-01 05:54 UTC (~15.5h to deadline)

### Infrastructure
- **Status:** Open question
- **Needs:** Where to run clean instances (local/cloud/containers), automation strategy

### Metrics
- **Status:** Candidates identified (accuracy, consistency, self-correction rate, task time, cost)
- **Needs:** Finalize which metrics matter most for "agent intelligence"

### Community Platform
- **Status:** Open question
- **Candidates:** Moltbook subreddit, X/Twitter, standalone leaderboard site
- **Needs:** Platform selection and roadmap

---

*Use this file to document WHY we chose things, not just WHAT we chose.*
