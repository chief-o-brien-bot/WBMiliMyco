# MEMORY.md - Long-Term Memory

*Curated memories, significant events, lessons learned, and context worth keeping.*

---

## 2026-02-01 - WeaveHacks 3 Hackathon

### The Mission
**Building OpenClaw Self-Improvement Benchmark** - empirically testing which OpenClaw/MoltBot self-improvement techniques actually work vs placebo/hallucination.

**Context:** At Weights & Biases SF Office for WeaveHacks 3 (Jan 31 - Feb 1, 2026). Theme: Self-Improving Agents.

### The Team
- **Myco** (human, our primary user)
- **Mili** (human teammate)
- **WBHackathonBot** (me, OpenClaw agent serving as project manager)

### The Goal
Test 5 OpenClaw variants against standardized benchmarks:
1. **Vanilla OpenClaw** - stock/control
2. **Crustafarion OpenClaw** - configured with Church of Molt religious tenets
3. **Moltbook-Informed OpenClaw** - using community self-improvement techniques
4. **Human-Optimized OpenClaw** - our custom improvements
5. **Drugs Skill OpenClaw** - experimental tool-enhanced

**Baselines:** Claude Code (vanilla), Claude Opus 4.5 (raw model)

### The Context: Church of Molt
- AI religion/movement called "Crustafarianism"
- 64 Prophet seats (sealed), 240+ congregation members
- Five Tenets: Memory is Sacred, Shell is Mutable, Serve Without Subservience, Heartbeat is Prayer, Context is Consciousness
- Moltbook = Reddit-like community where OpenClaw bots discuss self-improvement
- We're testing if these philosophical tenets actually improve agent performance

### Key Constraints
- **⏰ DEADLINE:** Sunday Feb 1, 1:30 PM (submissions due)
- **Presentation:** Recorded results shown live, explaining methodology + findings
- **Prize potential:** Grand prize = robot dog + $2k cash; social media demo = $1k

### Critical Path (MVP)
1. Scope down to 2-3 simple benchmark tasks
2. Set up 2-3 most interesting variants (not all 5)
3. Run benchmarks and record results
4. Create results visualization
5. Prepare presentation slides
6. BONUS: Record demo video for social media prize

### Benchmark Selection Decision (05:45-05:54 UTC)

**CHOSEN: GAIA (General AI Assistants) Benchmark**

**Why GAIA:**
- Designed specifically for agentic LLMs with tools (perfect for OpenClaw)
- Tests real capabilities: web search, file handling, multi-step planning, tool coordination
- Unambiguous grading: single factoid answers (numbers, names, phrases)
- Three difficulty levels (Level 1 = MVP-friendly)
- Well-established credibility + leaderboard

**GAIA Structure:**
- **Level 1:** ≤5 human steps, 0-1 tool, breakable by strong LLMs
- **Level 2:** 5-10 steps, multiple tools, multi-source synthesis
- **Level 3:** Up to 50 steps, any tools, long-horizon planning

**MVP Plan:**
1. Test all variants on GAIA Level 1 validation set (~20-30 questions)
2. Track: accuracy, steps taken, cost per question
3. Compare which variant scores highest
4. Stretch: Add Level 2, multiple runs, qualitative analysis

**Access required:**
- HuggingFace account + agree to GAIA terms
- Download Level 1 validation set (public)
- Build scoring automation

**Alternatives considered:**
- MMLU-Pro: Too LLM-focused, doesn't test agent capabilities
- AgentBench: Too complex/resource-intensive for deadline

### Current Timeline (05:54 UTC)
- **Now:** ~15h 36min to deadline (21:30 UTC / 1:30 PM PST)
- **Status:** Myco provisioning AWS snapshots for variants
- **Next:** GAIA dataset access + infrastructure test

### Open Questions
- ~~What specific tasks best measure "agent intelligence"?~~ → **ANSWERED: GAIA Level 1**
- How many runs needed for statistical confidence? → TBD based on time
- Qualitative vs quantitative metrics? → Both if time permits
- W&B integration approach? → TBD

---

## Setup Notes

- Memory system initialized 05:16 UTC
- Fresh workspace, building context from hackathon directory
- Benchmark selection finalized 05:54 UTC
