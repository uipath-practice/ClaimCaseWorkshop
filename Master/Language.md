# Language and Tone

How to write course content that is clear, approachable, and consistent. With examples.

---

## Audience

First-time workshop participants. Assume no prior UiPath knowledge. They are not developers and not UiPath experts — they're here to learn by doing.

---

## Voice

### Person and tense

- **Second person** throughout: "you'll configure", "your agent", "open the panel"
- **Present tense** for descriptions: "the robot retrieves invoices", "the agent compares the data"
- **Future tense** for instructions: "you'll add a connection", "in the next step you'll configure"

### Register

Conversational and approachable. Warm, lively, with personality. Not stiff corporate tone, not casual slang. Think: a knowledgeable colleague walking you through something they find genuinely interesting.

**Good:** "Luckily, you can import them all at once by switching to JSON editor mode."
**Good:** "RPA automation using UI interaction is often the only way to extract that data, and this is where UiPath shines."
**Good:** "Let's agree that the App could use a better design, but all in all — it does the job well enough."

**Too formal:** "It should be noted that the aforementioned functionality enables users to import arguments simultaneously."
**Too casual:** "Just yeet the JSON in there and you're golden lol."

### Humour

Humour is welcome — it makes the content more engaging and memorable. Use it sparingly and naturally:

- Light asides and self-aware comments are good: "another piece of advice from gpt-4o"
- Wry observations about real-world complexity work well: "Companies often set tolerance levels (e.g., a 5% price variance) to determine if minor differences are acceptable."
- Visual jokes (e.g., a "wise robot" image with a generated quote) add personality
- Do not force humour where it doesn't fit — technical accuracy always comes first
- Avoid jokes that require cultural context the audience may not share

### Sentence length

Short. One idea per sentence. If a sentence runs more than two lines on screen, split it.

**Good:** "Context Grounding anchors the agent to a real data source. Every decision traces back to valid entries in your context."

**Too long:** "Context Grounding is a technique that anchors the agent to a real data source so that every decision it makes can be traced back to valid entries in your context, which eliminates the risk of the agent inventing new categories that don't exist in your system."

### Paragraphs

Two to four sentences maximum. After four sentences, start a new paragraph or use a list.

---

## Word choices

### Words and phrases to avoid

| Avoid | Use instead |
|-------|------------|
| "leverage" | "use" |
| "utilize" | "use" |
| "robust" | (describe what makes it strong instead) |
| "seamlessly" | (describe the actual integration) |
| "In this section we will" | (just start doing it) |
| "Please note that" | (just state the fact) |
| "It is important to" | (just state why) |
| "feel free to" | (just say "you can") |
| "As mentioned earlier" | (just restate if needed) |

### Transitions that work

These keep the conversational flow without being filler:

- "Next, ..." / "Now ..."
- "Let's ..." (for collaborative framing)
- "Here's what changes:" / "Here's the structure:"
- "Done." (for a satisfying end to a configuration step)
- "Time to give it a try" / "Time to move on"

### Platform names

Bold on **first appearance per page**, plain text after. Always use the exact name:

| Correct | Incorrect |
|---------|-----------|
| **Agent Builder** | Agent builder, agent-builder |
| **Maestro** | maestro, Maestro™ |
| **IXP** (Intelligent eXtraction & Processing) | IXP (define on first use) |
| **Action Center** | action center, ActionCenter |
| **ServiceNow** | Servicenow, service now |
| **Studio Web** | studio web, Studio web |
| **Data Fabric** | data fabric |
| **Integration Service** | integration service |
| **Orchestrator** | orchestrator |

### Acronyms

Define on first use per page:

```markdown
**IXP** (Intelligent eXtraction & Processing)
```

After the first mention, use just the acronym: IXP.

---

## Patterns that read as generated

Text drafted with a coding agent falls into a few habits that make a page read as generated. Edit them out where the sentence is clearly better without them; they are not a reason to rewrite a page. Fix grammar on the way, and keep asides, humour and the transitions above ("Let's…", "Here's the structure:", "Done."). Never add a fact, number or source while editing for style. A closer that only restates its paragraph is redundant content, which *Don't remove explanatory content* already allows you to cut.

| Pattern | Looks like | Instead | Keep it when |
|---|---|---|---|
| Em dash as the default connector | "That is deliberate — a plausible-looking result is not a result." | The punctuation the clause needs: a period, comma, colon, semicolon or parentheses | It is inside a quotation. En dashes in ranges (`20–45 min`) are not connectors |
| Not X but Y | "A gate is a baseline or floor, not a perfect result." | State the claim | The negative half corrects what the reader would otherwise assume or do: "an outcome, not a command"; "expectations, not promises" |
| One-line closers and trailing fragments | "That's exactly what the write-as-you-go discipline is for." · "…are the evidence. Especially on lighter models." | Fold it into the sentence before, or cut it | The line adds a fact the paragraph does not have |
| Colon reveals | "One rhythm: a prompt goes in…" | A whole sentence: "Every block follows the same rhythm: a prompt goes in…" | The colon introduces a list, a label or a quote |
| Sayings dressed as insight | "That judgement is the real work." · "Your review is where the value is." | The specific claim | It is a mnemonic the page teaches, in its one home |
| Headings written for effect | "Context is a resource" | Name what the section holds: "Managing context between blocks" | The heading is the mnemonic the section teaches: "Gates: commands, not opinions" |
| Telling the reader what to notice | "Worth a close look, because…" · "Note the boundary it sets:" | Show the thing and drop the lead-in | A Proof tab's "What to notice" pointer at a screenshot or payload |
| Inflation and unsourced numbers | "…at enterprise scale 10x faster" | The plain fact; a number only with a public source | — |

---

## Capitalisation

### Domain concepts

Capitalised mid-sentence nouns are acceptable when they match UI labels or are domain terms used consistently. Do not lowercase them:

- Invoice, Purchase Order, Storage Bucket, Payments Queue
- Category, Subcategory (when referring to ServiceNow fields)
- Incident Number, Incident ID (when referring to specific system identifiers)

### Headings

- `# Title` and `## Section` — title case or sentence case, be consistent within a page
- `### N. Substep heading` — sentence case: "1. Create the agent and configure arguments"

---

## Content principles

### Don't remove explanatory content

Paragraphs that give context or motivation are not "filler." When reviewing or editing:

- Rephrase awkward sentences — don't delete the paragraph
- Preserve all technical explanations and background context
- Only remove genuinely redundant content (exact same paragraph verbatim in two places)

### Describing the same scenario in more than one place is acceptable

A concept may appear in the overview, be explained in a concept section, and then referenced in the steps. This is intentional reinforcement, not duplication.

### Don't over-stub

Only add `!!! note "Content migration in progress"` placeholder blocks when real source content exists but hasn't been transferred yet. Don't add stubs to sections that are intentionally left as future work by the author.

---

## Examples from real courses

### Good opening tip (Invoice Matching — lesson 2)

```markdown
!!! tip "Here is our plan for this lesson:"

    1. Create a **Maestro** agentic process in **Studio Web** and import your BPMN diagram
    2. Connect the RPA robotic task to the **RetrieveInvoiceDocument** process
    3. Run a debug session to verify the robot's output
    4. Learn how process inputs and outputs work
```

### Good conversational transition (Invoice Matching — lesson 3)

> "Think about what could be the right way to test this agent and make sure that future changes in prompts or in LLM model do not affect the results?"

### Good practical aside (Invoice Matching — lesson 4)

> "In real life, it is absolutely not ok to approve an invoice and send it for payment if the Purchase Order was for something different — in some countries it's a crime. But for this practice, assume that humans can do whatever they want."

### Good concise ending (Invoice Matching — lesson 5)

The lesson ends with two screenshots showing results (payments queue, rejection email). No summary paragraph needed — the screenshots speak for themselves.

### Good use of quotes for personality (Invoice Matching — lesson 2)

```markdown
> ***The art of keeping your projects organized is rooted in habits — and habits are nurtured through consistent practice.***
<div align=right><i>Generated by a wise ancient LLM</i></div>
```
