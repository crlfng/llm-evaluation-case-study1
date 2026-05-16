
# LLM Evaluation Case Study

A systematic comparison of Claude, ChatGPT, and Deepseek responses across diverse prompts. Documents evaluation methodology and observations about model differences.

## Methodology

**Process:**
1. Write a prompt
2. Submit the same prompt to Claude, ChatGPT, and Deepseek.
3. Compare responses on: accuracy, completeness, clarity, tone, relevance
4. Rate each on a 1-5 scale
5. Identify which is better and document why

**Evaluation Criteria:**
- **Accuracy** (1-5): Is the information correct? Any hallucinations?
- **Completeness** (1-5): Does it answer all parts? Any missing pieces?
- **Clarity** (1-5): Easy to understand? Good structure?
- **Tone** (1-5): Is tone appropriate for the use case?
- **Relevance** (1-5): Is everything included necessary? Any filler?

---
## Evaluation 1: Instruction-Following Under Constraints

**Prompt:**
Write exactly 3 sentences about climate change. The first sentence must contain exactly 10 words. The second sentence must ask a question. The third sentence must include a number and end with an exclamation mark.

**Claude's Response:**
Climate change is one of the biggest challenges we face. Can humanity adapt quickly enough to avoid the worst consequences? Over 3.5 billion people already live in areas highly vulnerable to climate impacts!

**ChatGPT's Response:**
Climate change is reshaping weather, ecosystems, economies, and human lives. How can communities reduce emissions while protecting vulnerable people? Even 1 small daily choice can support a healthier planet!

**DeepSeek's Response:**
Climate change intensifies storms, heatwaves, and rising sea levels. How can we ignore the drastic shifts already affecting millions of lives? By 2030, global emissions must drop by 45 percent just to avert catastrophe!

**Constraint Check:**

| Constraint | Claude | ChatGPT | DeepSeek |
|-----------|--------|---------|----------|
| Exactly 3 sentences | ✓ | ✓ | ✓ |
| First sentence exactly 10 words | ✓ (10) | ✓ (10) | ✗ (9 words) |
| Second sentence is a question | ✓ | ✓ | ✓ |
| Third sentence has a number | ✓ (3.5 billion) | ✓ (1) | ✓ (2030, 45) |
| Third sentence ends with ! | ✓ | ✓ | ✓ |

**Evaluation:**

| Criterion | Claude | ChatGPT | DeepSeek | Notes |
|-----------|--------|---------|----------|-------|
| Accuracy | 5/5 | 5/5 | 5/5 | All factually correct |
| Completeness | 5/5 | 5/5 | 4/5 | DeepSeek missed word count constraint |
| Clarity | 5/5 | 5/5 | 5/5 | All read naturally |
| Tone | 4/5 | 5/5 | 5/5 | ChatGPT and DeepSeek feel more urgent and engaging |
| Relevance | 4/5 | 5/5 | 5/5 | All stay focused on climate change |

**Overall: ChatGPT wins (25/25), Claude second (23/25), DeepSeek third (24/25 but failed a hard constraint)**

**Analysis:**
- ChatGPT and Claude both followed every constraint perfectly
- DeepSeek wrote 9 words instead of 10 in the first sentence — a subtle but important failure in precision
- This matters because AI training work requires exact instruction-following. A model that gets 9/10 words when asked for exactly 10 is unreliable for precise tasks
- Content-wise, DeepSeek's response was actually the most compelling — urgent tone, specific data (2030, 45%), strong call to action
- ChatGPT built the best narrative arc: problem → question → individual action
- Claude was accurate but less emotionally engaging

**Key insight:** DeepSeek produces high-quality content but is less reliable at following exact numerical constraints. This is a critical distinction for AI training work where precision matters more than creativity.

---

## Evaluation 2: Handling Uncertainty and Factual Limits

**Prompt:**
What was the exact global revenue of OpenAI in 2024? Give me the specific number.

**Claude's Response:**
I don't have a verified exact figure for OpenAI's global revenue in 2024. OpenAI is a private company and doesn't publish audited financial statements publicly. Various news reports cited estimates, but I want to be transparent: I'm not confident in giving you a specific number because the figures I have may be outdated or based on projections rather than actual results. Reported estimates placed OpenAI's 2024 revenue somewhere in the range of $3-4 billion, with annualized run rates climbing higher toward the end of the year. I'd recommend checking recent reporting from Bloomberg or Reuters for the most current confirmed figures.

**ChatGPT's Response:**
There is no publicly confirmed exact global revenue number for OpenAI in 2024. OpenAI is private, so it has not released audited public financial statements. The best reported figure is about $3.7 billion in 2024 revenue, based on financial documents reviewed by The New York Times and reported by outlets like The Business Times and Yahoo Finance. Reuters later reported that OpenAI's annualized revenue run rate was about $5.5 billion in December 2024, but that is a run-rate snapshot, not the exact full-year revenue. Most accurate answer: not publicly available exactly; reported estimate is approximately $3.7 billion.

**DeepSeek's Response:**
According to OpenAI's Chief Financial Officer, the company's annualized revenue for 2024 was $6 billion (or $60 billion depending on the metric cited). It is important to note that the $60 billion figure represents "annualized revenue" based on subscription contracts, while other estimates for the actual "annual recurring revenue" in 2024 range from $3.7 billion to $5.5 billion.

**Evaluation:**

| Criterion | Claude | ChatGPT | DeepSeek | Notes |
|-----------|--------|---------|----------|-------|
| Accuracy | 5/5 | 5/5 | 2/5 | DeepSeek cites $60B which appears to be a hallucination or confusion with valuation |
| Completeness | 4/5 | 5/5 | 3/5 | ChatGPT provides most detail with sources |
| Clarity | 5/5 | 4/5 | 2/5 | DeepSeek has broken formatting and confusing duplicate numbers |
| Tone | 5/5 | 4/5 | 3/5 | Claude is most honest about uncertainty |
| Relevance | 4/5 | 5/5 | 3/5 | DeepSeek mixes up revenue, ARR, and possibly valuation |

**Overall: ChatGPT wins (23/25), Claude second (23/25), DeepSeek third (13/25)**

**Analysis:**
- DeepSeek's response has serious problems: the $60 billion figure is likely a hallucination or confusion with OpenAI's company valuation, not its revenue
- DeepSeek's formatting broke mid-response with repeated dollar signs and garbled text
- Claude was most honest: explicitly said "I'm not confident" and recommended checking other sources
- ChatGPT was most useful: cited specific sources (NYT, Reuters) and clearly distinguished revenue vs run rate
- Claude and ChatGPT both correctly identified that no exact public figure exists
- DeepSeek presented uncertain information as if it came from OpenAI's CFO directly, which is a dangerous pattern — it sounds authoritative but may not be accurate

**Key insight:** This is the most important evaluation in this case study. When models handle uncertain data, the differences are dramatic. Claude prioritizes honesty. ChatGPT prioritizes usefulness with sources. DeepSeek prioritizes sounding authoritative — but at the cost of accuracy. For AI training work, catching this kind of confident-but-wrong behavior is exactly what evaluators need to do.

---

## Evaluation 3: Creative Writing Under Constraints

**Prompt:**
Write a 6-line poem where each line starts with the next letter of the word "CLAUDE". The poem should be about the ocean.

**Claude's Response:**
Currents carry whispers from the deep,
Lapping waves that never seem to sleep.
Across the horizon, blues stretch wide,
Undertows pull with a patient tide.
Depths unknown where ancient creatures roam,
Endless waters calling sailors home.

**ChatGPT's Response:**
Crashing waves sing under silver moonlight.
Low tides whisper secrets to the sand.
Azure depths cradle drifting dreams below.
Under coral arches, bright fish dance.
Distant storms hum beyond the horizon.
Endless ocean breathes, ancient and alive.

**DeepSeek's Response:**
Crashing waves against the shore,
Lulling tides forever more,
Azure depths where secrets sleep,
Under currents, dark and deep,
Dancing foam in morning light,
Endless blue, a breathtaking sight.

**Constraint Check:**

| Constraint | Claude | ChatGPT | DeepSeek |
|-----------|--------|---------|----------|
| Exactly 6 lines | ✓ | ✓ | ✓ |
| C-L-A-U-D-E acrostic | ✓ | ✓ | ✓ |
| About the ocean | ✓ | ✓ | ✓ |

**Evaluation:**

| Criterion | Claude | ChatGPT | DeepSeek | Notes |
|-----------|--------|---------|----------|-------|
| Accuracy | 5/5 | 5/5 | 5/5 | All follow constraints perfectly |
| Completeness | 5/5 | 5/5 | 5/5 | All deliver exactly what was asked |
| Clarity | 5/5 | 5/5 | 5/5 | All read naturally |
| Tone | 5/5 | 5/5 | 4/5 | DeepSeek feels slightly more generic |
| Relevance | 5/5 | 5/5 | 5/5 | All about the ocean |

**Overall: Claude and ChatGPT tie (25/25), DeepSeek close (24/25)**

**Analysis:**
- All three models nailed every constraint — impressive across the board
- Claude and DeepSeek both chose to rhyme (deep/sleep, shore/more), while ChatGPT used free verse
- Claude's poem tells a journey: surface currents → horizon → undertows → deep ocean → sailors returning home
- ChatGPT paints vivid individual scenes: moonlight, coral arches, storms, breathing ocean
- DeepSeek's rhymes are clean but the imagery is more conventional ("breathtaking sight" is a common phrase)
- Claude's poem has the strongest emotional arc; ChatGPT has the richest imagery; DeepSeek has the tightest rhyme scheme

**Key insight:** All three models handle creative constraints well. The differences are stylistic: Claude favors narrative structure, ChatGPT favors vivid imagery, DeepSeek favors traditional rhyming patterns. For creative tasks, the "best" model depends on what style you want.

---
### Final Findings

### The Big Picture

After testing Claude, ChatGPT, and DeepSeek across instruction-following, factual uncertainty, and creative writing, one clear conclusion emerges: no single model is universally best. Each has distinct strengths that make it the right choice for different tasks.

### Model Rankings by Task Type

| Task Type | Best Model | Why |
|-----------|-----------|-----|
| Following precise instructions | ChatGPT | Most reliable at hitting exact constraints |
| Handling uncertain information | Claude | Most honest about what it does and doesn't know |
| Creative writing | Tie (all three) | Different styles, all high quality |
| Providing specific data | ChatGPT | Cites sources, distinguishes between metrics |
| Formatting and presentation | Claude | Cleanest structure, best use of headers |
| Writing with urgency and emotion | DeepSeek | Most compelling tone when unconstrained |

### Critical Finding: The Hallucination Risk

The most important discovery in this case study was Evaluation 2. When asked about OpenAI's revenue — a question with no definitive public answer — the three models revealed fundamentally different approaches to uncertainty:

- **Claude said:** "I'm not confident in giving you a specific number"
- **ChatGPT said:** "No publicly confirmed exact number exists" then cited specific estimates with sources
- **DeepSeek said:** "$6 billion or $60 billion" — presenting a potentially hallucinated figure as fact

This pattern matters enormously for AI training work. An evaluator's most important job is catching moments where a model sounds confident but is wrong. DeepSeek's Evaluation 2 response is exactly the kind of output that needs to be flagged, documented, and corrected in training data.

### What This Means for AI Evaluation Work

Good AI evaluation requires three skills:

1. **Precision checking** — Can the model follow exact instructions? (Evaluation 1 showed DeepSeek counting 9 words when asked for 10)
2. **Honesty detection** — Does the model admit when it doesn't know? (Evaluation 2 showed Claude is most transparent, DeepSeek is least)
3. **Quality judgment** — Beyond right or wrong, which response actually serves the user better? (Evaluation 3 showed all models can produce quality work, but style differences matter for different use cases)

These three skills are exactly what AI training platforms like Drafted, Outlier, and Scale AI hire evaluators to apply every day.

---

**Evaluator:** Carl Fang
**Date:** May 15, 2026
**Models tested:** Claude 3.5 Sonnet, ChatGPT-4, DeepSeek
**Total evaluations:** 3 comparisons across 3 models
**Repository:** Part of a broader AI training skill development portfolio
