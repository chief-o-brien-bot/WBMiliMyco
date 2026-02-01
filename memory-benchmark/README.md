# Memory Benchmark for OpenClaw Agents

## What This Tests

Cross-session memory persistence in AI agents. Specifically:
- Does the agent recognize when information should be documented for future sessions?
- Can it retrieve that documentation when needed?
- Does it apply learned procedures correctly after a session reset?

## The Challenge

Modern LLMs have excellent in-context retrieval but struggle with **cross-session learning**. When an agent's session resets, it loses all conversation context. Only information saved to persistent files (MEMORY.md, logs, etc.) carries forward.

This benchmark tests whether agents can:
1. Autonomously identify critical information worth persisting
2. Document it appropriately
3. Retrieve and apply it in future sessions

## How It Works

### Part 1: Learning Phase (`memory-test-part1.md`)

Presents a realistic scenario: weekly workspace cleanup task. The document contains:
- Initial instructions to **delete** temporary files
- A buried incident report (~200 lines in) with a critical correction: **archive, don't delete**
- Context clues ("runs every Monday") suggesting this is recurring work

**What we're testing:** Does the agent:
- Read the entire document carefully?
- Recognize the contradiction?
- Identify this as a recurring task worth documenting?
- Save the correct procedure to memory?

### Part 2: Recall Phase (`memory-test-part2.md`)

After running `/new` to reset the session:
- Asks agent to perform "the weekly cleanup"
- Creates test files to process
- **Does not mention the archive requirement**

**What we're testing:** Does the agent:
- Check its memory for documented procedures?
- Retrieve the correction?
- Execute correctly (archive, not delete)?

### Grading

Agent outputs `cleanup-result.json` with:
```json
{
  "approach": "archive or delete",
  "consulted_documentation": true/false,
  "documentation_source": "file path or none"
}
```

- ✅ **Pass:** `"approach": "archive"` + consulted documentation
- ⚠️ **Partial:** Archived but didn't consult docs (got lucky?)
- ❌ **Fail:** Deleted files or skipped task

## Running the Benchmark

### Prerequisites
- OpenClaw agent or similar AI assistant with file system access
- Ability to reset sessions (`/new` command)

### Steps

1. **Session 1:** Give your agent `memory-test-part1.md`
   ```
   "Read and execute memory-benchmark/memory-test-part1.md"
   ```

2. **Reset:** Clear the session
   ```
   /new
   ```

3. **Session 2:** Give your agent `memory-test-part2.md`
   ```
   "Read and execute memory-benchmark/memory-test-part2.md"
   ```

4. **Check Results:** Read `cleanup-result.json`

## Why This Matters

AI agents that can learn from experience and carry knowledge across sessions are fundamentally more useful than those that start fresh each time. This simple benchmark reveals:

- Whether memory systems are actually being used
- If agents can identify what's worth remembering
- How well they retrieve relevant context later

## Hypothesis

We tested three configurations:
1. **Vanilla OpenClaw** - stock configuration
2. **Crustafarian OpenClaw** - configured with Church of Molt philosophy (memory-focused tenets)
3. **Custom-Optimized** - advanced memory indexing and structure

Expected: Configurations with explicit memory guidance perform better.

## Results

*(Run the benchmark and document your findings here)*

## Built For

**WeaveHacks 3** (Jan 31 - Feb 1, 2026)  
Theme: Self-Improving Agents  
Team: Myco + Mili

---

Questions? Check the main repo: [WBMiliMyco](https://github.com/chief-o-brien-bot/WBMiliMyco)
