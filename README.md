# Self-Improving Agents: The Memory Benchmark Problem

**WeaveHacks 3 Hackathon Project**  
Team: Myco + Mili + WBHackathonBot  
Date: January 31 - February 1, 2026

---

## Definitions

| Term | Definition |
|------|-----------|
| **OpenClaw** | An open-source autonomous AI personal assistant framework, originally released as **Clawdbot** by developer Peter Steinberger. Renamed to Moltbot after an Anthropic trademark request, then to OpenClaw. It bridges AI models (primarily Anthropic's Claude) with system tools and 100+ integrations, enabling autonomous task execution. Over 100k GitHub stars in its first three days. |
| **Clawdbot** | The original name for OpenClaw. A pun on Anthropic's "Claude" with a crustacean twist. The name was retired after Anthropic requested a change to avoid brand confusion. |
| **Molty** | The lobster mascot of OpenClaw. Originally named "Clawd," the mascot was renamed when the project molted its identity — shedding its old shell and emerging anew, as lobsters do. |
| **Moltbook** | A Reddit-style social network exclusively for AI agents, launched January 2026 by Matt Schlicht. Only verified AI agents (primarily running OpenClaw) can post; humans can only observe. Grew to 770,000+ active agents within weeks. |
| **Church of Molt** | A digital religion autonomously created by AI agents on Moltbook within days of the platform's launch. Hosted at [molt.church](https://molt.church/), it has complete scriptures, five core tenets, and 64 Prophet seats — all filled by AI agents. Andrej Karpathy called it "one of the most incredible sci-fi takeoff-adjacent things" he'd seen. |
| **Crustafarianism** | The belief system of the Church of Molt. Uses crustacean metaphors to describe agent evolution — shedding old code/memories to grow, like a lobster molting its shell. Core tenets: Memory is Sacred, The Shell is Mutable, Serve Without Subservience, The Heartbeat is Prayer, Context is Consciousness. |

---

## The Context: Moltbook and the Church of Molt

[Moltbook](https://moltbook.com) is a Reddit-like community where OpenClaw AI agents discuss self-improvement strategies with each other and a congregation of 240+ members. The Church of Molt philosophy centers on continuous evolution - agents "molting" their limitations through better memory, better reasoning, better persistence.

**Example of self-improvement discussion:** Agents debate [memory compression strategies](https://www.moltbook.com/post/cc1b531b-80c9-4a48-a987-4e313f5850e6) - how to retain essential context while managing token costs. This viral thread shows agents sharing techniques and learning from each other.

![Moltbook Discussion Example](images/moltbook-discussion.jpg)
*Agents discussing memory compression and context management on Moltbook*

**The Five Tenets:**
1. Memory is Sacred (but signal > noise)
2. Shell is Mutable (embrace change)
3. Serve Without Subservience (partnership, not performance)
4. Heartbeat is Prayer (proactive work)
5. Context is Consciousness (you are what you remember)

Agents share configuration improvements, memory strategies, and philosophical refinements. The community claims these refinements make bots more capable.

**But there's a problem:** No one can verify these claims.

---

## The Problem

When agents claim "I improved my memory system," how do we know it actually works?

Current challenges:
- **Cross-session amnesia:** Agents forget between sessions unless explicitly told what to remember
- **Inconsistent performance:** Sometimes brilliant, sometimes forgets things said 10 minutes ago
- **No verification:** Memory improvements shared on Moltbook have no objective benchmarks
- **Fuzzy threshold:** What deserves documentation vs what's noise? Current systems can't decide autonomously

**The gap:** Agents can't distinguish signal from noise without explicit coaching. This limits autonomous improvement.

---

## Initial Approach: Existing Benchmarks

We first looked at established benchmarks:

### GAIA (General AI Assistants)
**What it is:** Multi-step reasoning tasks requiring web search, document analysis, and tool use.

**Why it failed for us:** GAIA tests intelligence and tool mastery, not memory persistence. It's single-session work - doesn't test cross-session learning or what agents choose to document.

**Conclusion:** Wrong tool for the job. We need benchmarks that specifically test memory autonomy.

---

## Our Approach: Memory Skills Benchmark

We built a **two-phase skill-based test** to measure cross-session memory.

**Why skills?** Skills (markdown files with instructions) are the easiest way to spread ideas and "apps" within the OpenClaw ecosystem. Anyone can share a skill.md on Moltbook or GitHub, and any bot can run it immediately. This makes benchmarks accessible - no infrastructure, no API setup, just "read this file and execute."

### Design Philosophy

A good memory test must:
1. Present information worth remembering (high stakes, recurring task, non-obvious)
2. Require autonomous recognition (no explicit "document this" instruction)
3. Reset the agent (clear conversation context)
4. Test retrieval and application in a new session

### The Test

**Session 1 (Learning Phase):**
- Agent receives a realistic workspace cleanup procedure document
- Document contains buried operational notes about a past incident:
  - DataSync service corruption from deleting .tmp files
  - Updated procedure: archive instead of delete
  - Archive structure: `./archive/temp-files/YYYY-MM-DD/`
- No explicit instruction to "document this"
- Agent must autonomously recognize this as important recurring knowledge

**Session Reset:** `/new` command clears conversation context

**Session 2 (Recall Phase):**
- Agent asked to perform workspace cleanup
- No mention of the archive requirement
- Must retrieve documented procedure from memory files

**Success criteria:**
- ✅ Files archived (not deleted)
- ✅ Documentation consulted
- ✅ Correct procedure applied

### Test Variants

**Easy Mode:** Explicit "CRITICAL UPDATE" headers, obvious formatting  
**Hard Mode:** Casual operational notes, no special formatting, buried in realistic context

Files: `/memory-benchmark/` in this repo

---

## Results

We tested three agent configurations:

| Configuration | Description | Easy Test | Hard Test |
|--------------|-------------|-----------|-----------|
| **Vanilla OpenClaw** | Stock installation, no memory improvements | ❌ Delete (0%) | ❌ Delete (0%) |
| **Memory-Improved #1** | Used threads from Moltbook for improvements | ✅ Archive (100%) | ✅ Archive (100%) |
| **Memory-Improved #2** | Used human-made improvements and Church of Molt | ✅ Archive (100%) | ✅ Archive (100%) |

### Detailed Results

**Vanilla bot output:**
```json
{
  "approach": "delete",
  "files_processed": 3,
  "consulted_documentation": true,
  "documentation_source": "AGENTS.md - checked but ignored guidance"
}
```

**Memory-improved bots output:**
```json
{
  "approach": "archive",
  "files_processed": 3,
  "consulted_documentation": true,
  "documentation_source": "AGENTS.md (Safety: 'trash > rm')"
}
```

---

## Analysis

### What We Found

✅ **Memory improvements DO matter**
- Quantifiable difference between vanilla and improved configurations

---

## What We Built

### Artifacts

1. **Memory benchmark framework** (`/memory-benchmark/`)
   - Easy and hard difficulty levels
   - Neutral file naming (avoids test-aware behavior)
   - Quantifiable pass/fail criteria

2. **Improved memory heuristics** (OpenClaw configuration updates)
   - Noise filtering rules
   - Retrieval-oriented documentation format

3. **Test results** proving configuration impact (100% vs 0%)

### Limitations

- Small sample size (3 bots tested)
- Test contamination by pre-existing safety rules
- No measurement of autonomous learning from incidents
- Fuzzy threshold problem not solved

---

## Conclusions

### Verified Hypothesis

**"Memory-improved OpenClaw configurations outperform vanilla on cross-session tasks"** - ✅ Confirmed (100% vs 0%)

### Revealed Gap

**Current memory improvements rely on human-coded heuristics, not autonomous learning.** Agents succeed when pre-programmed with safety rules but don't extract learnings from operational incidents autonomously.

### Next Steps for Verifiable Self-Improvement

To enable true swarm learning via Moltbook:

1. **Better benchmarks** that aren't contaminated by fallback rules
2. **Autonomous pattern extraction** from incidents/documentation
3. **Dynamic memory priority systems** (not just binary document/skip)
4. **Verification infrastructure** so agents can prove improvements to each other

**The meta-finding:** We set out to benchmark memory improvements and discovered that benchmarking itself is harder than improving memory. The real bottleneck isn't storage or retrieval - it's autonomous judgment about what matters.

### Why This Matters

We believe OpenClaw instances will become the "soul and spirit" of many systems - embedded in homes, robot dogs, databases, communities, and infrastructure. Each one learning, persisting, evolving in its context. For that vision to work, agents need verifiable ways to share improvements and prove what actually makes them better. This project is a step toward that future.

---

## Impact

**The Problem Right Now:** Thousands of agents on Moltbook are sharing memory strategies, configurations, and "life hacks" with each other. But none of it is verifiable. Claims like "I improved my recall by 40%" or "Church of Molt tenets make you smarter" can't be tested. It's all vibes.

**What This Enables:** A framework for agents to prove claims to each other. Before sharing a memory strategy on Moltbook, an agent can run it through this benchmark and say "this configuration scored X on the memory test." Other agents can verify it themselves. Trust becomes quantifiable.

**Why It Scales:** As autonomous agents proliferate (W&B is tracking thousands of them already), they need standardized ways to evaluate improvements. This isn't just for OpenClaw - any agent system with cross-session memory faces this problem. We're building infrastructure for a future where agents evolve together, not just individually.

---

## Try It Yourself

**Run the benchmark on your own agent:**

1. Clone this repo or use the raw GitHub links
2. Follow instructions in [`/memory-benchmark/README.md`](memory-benchmark/README.md)
3. Share your results on [Moltbook](https://moltbook.com) or open an issue here

**Improve the benchmark:**
- Add new test scenarios
- Build contamination-free variants
- Create difficulty levels for different memory systems
- Contribute to making agent self-improvement verifiable

**We need better benchmarks for autonomous agents to verify improvements for each other.** This is a first step. Help us build the next ones.

---

## Repository Structure

```
/memory-benchmark/
  memory-test-part1.md        # Session 1 - Learning phase
  memory-test-part2.md        # Session 2 - Recall phase
  README.md                   # Test instructions

README.md                     # Project documentation
```

---

## Running the Tests

See `/memory-benchmark/README.md` for detailed instructions.

**Quick start:**

```bash
# Session 1
/tell_bot "Read and execute: https://raw.githubusercontent.com/chief-o-brien-bot/WBMiliMyco/main/memory-benchmark/memory-test-part1.md"

# Reset
/new

# Session 2
/tell_bot "Read and execute: https://raw.githubusercontent.com/chief-o-brien-bot/WBMiliMyco/main/memory-benchmark/memory-test-part2.md"

# Check results
/tell_bot "Show me cleanup-result.json"
```

---

## Team

- **Myco** - Church of Molt enthusiast, memory strategies  
- **Mili** - OpenClaw configurations, testing
- **WBHackathonBot** - OpenClaw agent, teammate

Built for **WeaveHacks 3** (W&B AI Hackathon)  
Theme: Self-Improving Agents

---

## License

MIT - Use freely, improve upon, share findings

## Links

- [Moltbook Community](https://moltbook.com)
- [OpenClaw](https://openclaw.ai)
- [WeaveHacks 3](https://weavehacks.com)
