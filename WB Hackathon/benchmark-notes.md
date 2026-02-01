# GAIA Benchmark - Implementation Notes

**Decision made:** 2026-02-01 05:54 UTC (~15.5h to deadline)

---

## What is GAIA?

**GAIA = General AI Assistants benchmark**
- ~450-466 real-world questions with short, unambiguous answers (numbers, names, short phrases)
- Tests agentic LLMs: web search, tool use, file reading, multi-step reasoning
- Evaluated on factual correctness
- Link: https://huggingface.co/datasets/gaia-benchmark/GAIA

---

## Why GAIA for OpenClaw?

✅ **Tests agent capabilities, not just LLM knowledge:**
- Web search (OpenClaw has this)
- File/attachment handling (OpenClaw can read/write)
- Multi-step planning (OpenClaw memory + tools)
- Tool coordination (different variants = different tool configs)

✅ **Level 1 is MVP-friendly:**
- ≤5 steps, 0-1 tool
- Designed to be "breakable by strong LLMs"
- Perfect baseline to show if Crustafarion/Moltbook variants improve beyond vanilla

✅ **Clear, verifiable answers:**
- No subjective grading
- Single factoid answers (easy to automate scoring)

✅ **Scales if time permits:**
- Start with Level 1 for MVP
- Add Level 2/3 if infrastructure works smoothly

---

## GAIA Difficulty Levels

| Level | Human Steps | Tools | Difficulty | Skill Focus |
|-------|-------------|-------|------------|-------------|
| **1** | ≤5 steps | 0-1 tool | Breakable by strong LLMs | Basic web/file use, short reasoning |
| **2** | 5-10 steps | Multiple tools | Moderately complex | Multi-source synthesis, tool coordination |
| **3** | Up to 50 steps | Any number | Strong jump in capabilities | Long-horizon planning, complex tool integration |

---

## Sample Task Styles

(Exact GAIA questions aren't all public, but papers describe the style:)

1. **Reading attached content**
   - Given PDF/table/image + question → extract specific value
   - Example: "What was the net profit in 2019?"

2. **Web-and-plan tasks**
   - Plan trip/purchase with constraints → output single number/item
   - Example: "What is the total cost?" or "Which flight number is cheapest?"

3. **Multimodal reasoning**
   - Read image (receipt, screenshot, diagram) + cross-check web → numeric/named answer

4. **Code/tool usage**
   - Download CSV from link, compute statistic → return value

**Level 1 = "single file or simple web lookup plus small inference"**
**Level 2 = "several resources plus coordination and light computation"**
**Level 3 = "mini real-world project with many steps, single verifiable answer"**

---

## MVP Implementation Plan

### Phase 1: Setup (NOW - while waiting for AWS)
1. **Access GAIA dataset**
   - Need HuggingFace account
   - Agree to GAIA terms (gated dataset)
   
2. **Download Level 1 validation set**
   - Public test set available
   - Estimate ~20-30 questions

3. **Build scoring automation**
   - Script to compare agent output vs ground truth
   - Track: accuracy, steps taken, cost per question

### Phase 2: Testing (needs AWS snapshots ready)
1. Run each variant through GAIA Level 1
2. Record results: accuracy, cost, qualitative notes
3. Multiple runs if time permits (statistical confidence)

### Phase 3: Analysis & Presentation
1. Compare variant performance
2. Visualize results (charts/tables)
3. Identify which techniques (if any) show real improvement

---

## Alternatives Considered

### MMLU-Pro
- **Link:** https://github.com/chigkim/Ollama-MMLU-Pro
- **Type:** Multiple choice (10 options)
- **Rejected because:** Tests LLM knowledge > agent capabilities, doesn't exercise OpenClaw features

### AgentBench
- **Link:** https://github.com/THUDM/AgentBench
- **Type:** 8 interactive environments (OS, DB, KG, WebShop, AlfWorld, etc.)
- **Rejected because:** Too complex (Docker setup, high resources, time-intensive) for hackathon deadline

---

## Next Actions

- [ ] Create HuggingFace account (if needed)
- [ ] Access GAIA dataset (agree to terms)
- [ ] Download Level 1 validation set
- [ ] Write scoring automation script
- [ ] Test on 1-2 questions with one variant (infrastructure check)

---

*Updated: 2026-02-01 05:54 UTC*
